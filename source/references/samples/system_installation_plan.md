![{{DEPARTMENT_LOGO}}](media/image1.jpg)

# SYSTEM INSTALLATION PLAN

**FOR**

**{{PROJECT_FULL_NAME}}**

**{{PROJECT_SHORT_NAME}}**

**OF**

**{{DEPARTMENT_NAME}}**

**Version: 0.1**

**Jan 2025**

? The Government of the Hong Kong Special Administrative Region

The contents of this document remain the property of and may not be reproduced in whole or in part without the express permission of the Government of the HKSAR.

| Distribution | N/A |
|-------------|-------------------------------------| N/A |---|---| N/A | Copy No.    | Holder                              | N/A |---|---| N/A | 1           | {{DEPARTMENT_NAME}} | N/A |---|---| N/A | 2           | Master Concept (Hong Kong) Limited (MC) | N/A |---|---| N/A | Amendment History | N/A |                | N/A |           | N/A |
|------------------|------------------------|----------------|------------|-----------|-----------| N/A |---|---|---|---|---|---| N/A | Change Number    | Revision Description   | Pages Affected | Revision / | Date      | Approval  | N/A |                  | N/A | on Respective  | Version    | N/A | Reference | N/A |                  | N/A | Version        | Number     | N/A |           | N/A |---|---|---|---|---|---| N/A | 1                | 1st draft             | All            | 0.1        | 16/01/225 | N/A |
|---|---|---|---|---|---|
# TABLE OF CONTENTS

[1. Introduction](#introduction)

[2. Project Environment Description](#project-environment-description)
- [2.1 Network Diagram](#network-diagram)
- [2.2 Hardware Specification](#hardware-specification)
- [2.3 Software Specification](#software-specification)

[3. Application Deployment Procedure for Production](#application-deployment-procedure-for-production)
- [3.1 Database Server](#database-server)
- [3.2 Backend Servers](#backend-servers)
- [3.3 Frontend Servers](#frontend-servers)
  - [3.3.1 sFTP Server Setup](#sftp-server-setup)

[4. System Installation Schedule and Result](#system-installation-schedule-and-result)
- [4.1 System Installation Schedule](#system-installation-schedule)
- [4.2 System Installation Result](#system-installation-result)

# Introduction

The System Installation plan describes the procedure and schedule for deploying the application in the production environment, including 3 parts of the system:

- Database Server
- Backend Server
- Frontend and Web Portal Server

# Project Environment Description

## Network Diagram

Below is a logical network diagram in {{LOCATION}} for production and UAT site.

[DIAGRAM HERE]

The network will be separated into three zones: DMZ, trusted zone, and storage network.

A two-tier firewall setup will be used to form the trusted zone and DMZ. Incoming network traffic to the system must go through the DMZ before entering the trusted zone.

To utilize hardware resources more effectively, servers listed in section [1.3.3], except the backup server, will be set up in the form of virtual machines (VM) and consolidated into DMZ VM host servers and trusted zone VM host servers for each physical site. Two VM host servers will be built in each zone for the purpose of high availability.

Similarly, storage needed by all servers will be consolidated and provided by SAN storage. A dedicated network will be set up and interconnected with the VM host servers. The backup server will also exist in this storage-dedicated network to carry out backup tasks of VM host servers in DMZ and trusted zone.

The diagram below illustrates the physical setup.

## Hardware Specification

Production and UAT environment:

List of machines and virtual machines:

| Hostname (Physical Machine) | Hostname (Virtual Machine) | Purpose | IP | N/A |---------------------------|---------------------------|---------|-----| N/A |---|---|---|---| N/A | {{PRD_DB_PHYSICAL}} | {{PRD_DB_VIRTUAL}} | {{DATABASE_TYPE}} Database Server | {{PRD_DB_IP}} | N/A |---|---|---|---| N/A | {{PRD_APP_PHYSICAL}} | {{PRD_APP_VIRTUAL}} | {{BACKEND_TYPE}} Backend Server | {{PRD_APP_IP}} | N/A |---|---|---|---| N/A | {{PRD_WEB_PHYSICAL}} | {{PRD_WEB_VIRTUAL}} | {{FRONTEND_TYPE}} Frontend Server | {{PRD_WEB_IP}} | N/A |---|---|---|---|
DR environment:

List of machines and virtual machines:

| Hostname (Physical Machine) | Hostname (Virtual Machine) | Purpose | IP | N/A |---------------------------|---------------------------|---------|-----| N/A |---|---|---|---| N/A | {{DR_DB_PHYSICAL}} | {{DR_DB_VIRTUAL}} | {{DATABASE_TYPE}} Database Server | {{DR_DB_IP}} | N/A |---|---|---|---| N/A | {{DR_APP_PHYSICAL}} | {{DR_APP_VIRTUAL}} | {{BACKEND_TYPE}} Backend Server | {{DR_APP_IP}} | N/A |---|---|---|---| N/A | {{DR_WEB_PHYSICAL}} | {{DR_WEB_VIRTUAL}} | {{FRONTEND_TYPE}} Frontend Server | {{DR_WEB_IP}} | N/A |---|---|---|---|
## Software Specification

| Machine | Hostname | Software Requirement | N/A |---------|----------|---------------------| N/A |---|---|---| N/A | {{DATABASE_TYPE}} Database Server | {{PRD_DB_VIRTUAL}} | {{DATABASE_TYPE}} {{DATABASE_VERSION}} | N/A |---|---|---| N/A | {{BACKEND_TYPE}} Backend Server | {{PRD_APP_VIRTUAL}} | {{BACKEND_TYPE}} {{BACKEND_VERSION}}, {{PROCESS_MANAGER}} {{PM_VERSION}} | N/A |---|---|---| N/A | {{FRONTEND_TYPE}} Frontend Server | {{PRD_WEB_VIRTUAL}} | {{WEB_SERVER}} {{WEB_SERVER_VERSION}}, {{FRONTEND_TYPE}} {{FRONTEND_VERSION}} | N/A |---|---|---|
Development Frameworks:

| Framework | Version | N/A |-----------|---------| N/A |---|---| N/A | {{FRONTEND_TYPE}} (frontend) | {{FRONTEND_VERSION}} | N/A |---|---| N/A | {{BACKEND_TYPE}} (backend) | {{BACKEND_VERSION}} | N/A |---|---| N/A | {{DATABASE_TYPE}} (database) | {{DATABASE_VERSION}} | N/A |---|---|
# Application Deployment Procedure for Production

## Database Server

To install database server, follow these steps:

1. Remote login to {{PRD_DB_VIRTUAL}}
2. Install {{DATABASE_TYPE}} Server {{DATABASE_VERSION}}
3. Install {{DATABASE_TYPE}} {{DATABASE_MANAGEMENT_TOOL}} {{DB_TOOL_VERSION}}
4. Configure {{DATABASE_TYPE}} Server with:
   - Authentication: {{DB_AUTH_METHOD}}
   - Enable networking on port {{DB_PORT}}
   - Configure firewall to allow {{DATABASE_TYPE}} port (default {{DB_PORT}})
   - Set up SSL/TLS encryption
5. Create database {{DATABASE_NAME}} with:
   - Character set: {{DB_CHARSET}}
   - Collation: {{DB_COLLATION}}
   - Initial size: {{DB_INITIAL_SIZE}}
6. Configure database backup schedule:
   - Daily incremental backup at {{DAILY_BACKUP_TIME}}
   - Weekly full backup on {{WEEKLY_BACKUP_DAY}} at {{WEEKLY_BACKUP_TIME}}
7. Configure database maintenance plan:
   - Weekly {{DB_MAINTENANCE_TASK}}
   - Daily statistics update
8. Configure database monitoring and alerts:
   - Space usage alerts at 85% and 95%
   - Performance alerts for slow queries
   - Connection limit alerts

## Backend Servers

1. Remote login into {{PRD_APP_VIRTUAL}}
2. Install prerequisites:
   - {{OS_TYPE}} updates
   - {{BACKEND_TYPE}} {{BACKEND_VERSION}}
   - {{PROCESS_MANAGER}} {{PM_VERSION}} (Process Manager)
   - Git for deployment
3. Install backend application:
   - Deploy {{BACKEND_TYPE}} API application files to {{BACKEND_DEPLOY_PATH}}
   - Configure {{PROCESS_MANAGER}} ecosystem file:
     - Environment: production
     - Instances: cluster mode ({{CLUSTER_INSTANCES}} instances)
     - Memory limit: {{MEMORY_LIMIT}} per instance
4. Configure application settings:
   - Update {{CONFIG_FILE}} with production values
   - Configure {{DATABASE_TYPE}} connection strings
   - Set up logging paths ({{LOG_PATH}})
5. Configure system services:
   - Set up {{PROCESS_MANAGER}} as system service
   - Configure log rotation
   - Set up service recovery options
6. Configure SSL certificates:
   - Install SSL certificate for HTTPS
   - Configure reverse proxy ({{WEB_SERVER}})
7. Configure {{WEB_SERVER}} reverse proxy:
   - Create virtual host configuration
   - Configure load balancing
   - Set up compression and caching rules

## Frontend Servers

1. Remote login into {{PRD_WEB_VIRTUAL}}
2. Install prerequisites:
   - {{OS_TYPE}} updates
   - {{WEB_SERVER}} {{WEB_SERVER_VERSION}}
   - {{BACKEND_TYPE}} {{BACKEND_VERSION}} (for build process)
   - Git for deployment
3. Install frontend application:
   - Deploy {{FRONTEND_TYPE}} application files to {{FRONTEND_DEPLOY_PATH}}
   - Build production assets using npm run build
   - Configure static file serving
   - Set up compression for static files
4. Configure {{WEB_SERVER}}:
   - Create virtual host configuration
   - Configure SSL certificates
   - Set up URL rewrite rules for SPA routing
   - Configure CORS headers
   - Set up gzip compression
5. Configure monitoring:
   - Set up {{WEB_SERVER}} access and error logging
   - Configure health check endpoints
   - Set up performance monitoring
   - Configure log rotation

### sFTP Server Setup

1. Install OpenSSH server in {{OS_TYPE}}:
   - Update package repository: {{PACKAGE_UPDATE_CMD}}
   - Install OpenSSH server: {{SSH_INSTALL_CMD}}
   - Enable SSH service: {{SSH_ENABLE_CMD}}
2. Configure OpenSSH server:
   - Create dedicated service account for {{PROJECT_SHORT_NAME}}
   - Configure authentication methods in /etc/ssh/sshd_config
   - Set up SFTP chroot directory: {{SFTP_ROOT_DIR}}
3. Configure firewall:
   - Allow inbound port 22 (SSH): {{FIREWALL_SSH_CMD}}
   - Restrict access to specific IP ranges
   - Configure fail2ban for intrusion prevention
4. Set up user accounts:
   - Create SFTP users for {{PROJECT_SHORT_NAME}} file transfers
   - Configure user permissions and directory access
   - Set up public key authentication
5. Configure logging and monitoring:
   - Enable detailed SSH logging in {{SSH_LOG_PATH}}
   - Set up log rotation with logrotate
   - Configure alerts for failed login attempts

# System Installation Schedule and Result

## System Installation Schedule

The following table summarises the testing schedule:

| Pre-Requisite | Start Date | End Date | Start time | End Time | N/A |---------------|------------|----------|------------|----------| N/A |---|---|---|---|---| N/A | Database Server Installation (Production and DR) | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Backend Server Installation (Production and DR) | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Frontend Server Installation (Production and DR) | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Functionality test (VM & Networking) | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Database setup | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Deployment for 1st version of frontend server | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Deployment for 1st version of backend server | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Application Health Check | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Deployment for Latest Mobile Application | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Final Check Production Web Server | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Final Check Production Database Server | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Final Check DR Web & Database server | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Final Check {{WEB_SERVER}} & Framework | N/A |  | N/A |  | N/A |---|---|---|---|---|
## System Installation Result

The following table summarises the actual system installation schedule:

| Pre-Requisite | Actual Start Date | Actual End Date | Actual Start time | Actual End Time | Status/Result | N/A |---------------|-------------------|-----------------|-------------------|-----------------|---------------| N/A |---|---|---|---|---|---| N/A | Database Server Installation (Production, UAT and DR) | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Backend Server Installation (Production, UAT and DR) | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Frontend Server Installation (Production, UAT and DR) | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Functionality test (VM & Networking) | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Database setup | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Deployment for 1st version of frontend server | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Deployment for 1st version of backend server | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Application Health Check | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Deployment for Latest Mobile Application | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Final Check Production Web Server | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Final Check Production Database Server | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Final Check DR Web & DB server | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Final Check {{WEB_SERVER}} & Framework | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---|
<<End of Document>>
```

Okay, I've analyzed the provided text. Here's a breakdown of the document and a summary of its key points:

**Overall Document Purpose:**

This document appears to be a combination of a user manual/guide for an "I&T Project Management Information System (INTPMIS)" and a User Requirements Specification (URS) for the system's development.  It's designed for the Electrical and Mechanical Services Department (EMSD) in Hong Kong.

**Key Sections and Their Content:**

1.  **Report Descriptions:**
    *   This section describes the various reports available within the INTPMIS system.  It outlines the purpose of each report, the data it presents, and how users can interact with it (e.g., filtering, viewing trends).
    *   The reports cover areas like:
        *   Trends of I&T Wishes, Solutions, and Matched Trial Projects
        *   Summary of I&T Wishes
        *   Distribution of I&T Solutions by Technology
        *   Cash Flow for Matched Trial Projects
        *   Statistics on I&T Projects
        *   Statistics Technology on I&T Projects
        *   Expenditure on I&T Projects

2.  **User Procedures and Operation Manual:**
    *   This is a step-by-step guide for users on how to use the INTPMIS system.  It covers:
        *   **Login:** Instructions for both SSO (Single Sign-On) and username/password login.
        *   **Project Management:**
            *   Browsing Project List (viewing, filtering, searching, exporting)
            *   Creating a Project
            *   Editing a Project
        *   **Wish List Management:**
            *   Browsing Wish List (viewing, searching, filtering, exporting)
            *   Editing a Wish
        *   **Solution List Management:**
            *   Browsing Solution List (viewing, searching, filtering, exporting)
            *   Editing a Solution

3.  **Administrator Procedures and Operation Manual:**
    *   This section outlines specific procedures and functionalities available to administrators within the INTPMIS system.
        *   **Project Management:**
            *   Editing a Project (with more fields accessible to administrators)
        *   **Log List:**
            *   Browsing Log List (viewing, exporting, canceling reminders)

4.  **Additional Functionality Descriptions:**
    *   **Search Function:**  Details how users can search for projects, wishes, or solutions using specific criteria.
    *   **Export Function:** Explains how users can export data from tables into CSV files.
    *   **Printing Report Function:** Describes how users can print reports.
    *   **Create Project:**  A detailed table listing the fields required when creating a new project, including input types, requirements, and remarks.
    *   **Logging:**  Explains the logging functionality for tracking changes to reports, wishes, and solutions.

5.  **User Requirement Specification (URS):**
    *   This section outlines the requirements for the development of the INTPMIS system.
        *   **Proposed System Overview:** Describes the enhanced aspects of the proposed INTPMIS system, including working environment, data management, data analysis, and workflow.
        *   **Future Business Process:** Lists the future business processes that the system will support.
        *   **UI & UX Design:** Shows screenshots of the user interface design for various pages in the system.
        *   **Functional Requirements:** Lists the functional requirements for the system, including login, project list, create a project, view or edit a project, wish list, view or edit a wish, solution list, view and edit a solution, report list, view report, log list, view log list, and upload files.
        *   **Non-functional Requirements:** Lists the non-functional requirements for the system, including response time, service time, export, scalability, system performance, user interface requirement, function access rights, access to data, and system backup.

**Key Takeaways:**

*   **Comprehensive System:** INTPMIS is designed to be a comprehensive system for managing I&T projects, wishes, and solutions within EMSD.
*   **User-Friendly:** The system emphasizes a user-friendly interface with features like filtering, searching, and exporting data.
*   **Role-Based Access:** The system has different functionalities and access levels for regular users and administrators.
*   **Logging and Auditing:** The system includes logging functionality to track changes and ensure accountability.
*   **Detailed Requirements:** The URS section provides a detailed specification of the system's functional and non-functional requirements.

Let me know if you have any specific questions about the document or if you'd like me to elaborate on any particular section.


# System Installation Plan

This document outlines the system installation plan based on the provided requirements and specifications. It covers functional and technical requirements, focusing on system controls, backup, recovery, and disaster recovery.

## 1. Introduction

This plan details the steps required to install and configure the system, ensuring it meets the defined functional and non-functional requirements. It addresses access control, data backup, recovery procedures, and disaster recovery preparedness.

## 2. Requirements Summary

This section summarizes the key requirements driving the system installation.

### 2.1 Functional Requirements

Based on the System Specification, the system provides the following functions:

*   **Information Viewing:**
    *   View Project List and Detail
    *   View Wish List and Detail
    *   View Solution List and Detail
    *   View Report List and Detail
    *   View Log List and Detail
    *   Search Projects
    *   Filter Projects
    *   Search Wishes
    *   Filter Wishes
    *   Search Solutions
    *   Filter Solutions
*   **Content Management:**
    *   Create a Project
    *   Edit a Project
    *   Edit a Wish
    *   Edit a Solution
    *   Cancel Reminder for Log
*   **Workflow Application:**
    *   Export Projects
    *   Export Wishes
    *   Export Solutions
    *   Export Report

### 2.2 Non-Functional Requirements

*   **REQ-SCR-002: Access to Data**
    *   Define access rights for users to access particular data and also on a conditional basis.
    *   Define access monitoring for the selected data.
*   **REQ-SCR-003: System Backup**
    *   Meet general backup requirements including data and system; and all audit logging information.

### 2.3 Technical Requirements

*   **TR-SBR-001: Server House Keeping**
    *   System logs must be archived to backup tape weekly.
*   **TR-SBR-002: Backup, Recovery and System Archive**
    *   Provide daily backup
    *   Provide weekly system backup
    *   Provide 2 generations of system backup stored off-site
    *   Provide system activity logs and reports
*   **TR-DRR-001: System Disaster Recovery**
    *   Participate in the disaster recovery activities and complete all activities assigned following the procedures in the disaster recovery plan.
    *   Co-ordinate with new system user to participate in the disaster recovery activities.
    *   Resume the whole system from disaster recovery site to normal production environment.

## 3. Installation Steps

This section outlines the high-level steps for installing the system.  Specific details will depend on the chosen technology stack.

1.  **Environment Setup:**
    *   Provision servers (development, testing, production, disaster recovery).
    *   Install operating systems and necessary software (databases, application servers, etc.).
    *   Configure network settings and security.

2.  **Application Deployment:**
    *   Deploy the application code to the application server.
    *   Configure the application to connect to the database.
    *   Configure access control mechanisms based on REQ-SCR-002.

3.  **Database Setup:**
    *   Create the necessary database schemas and tables.
    *   Populate the database with initial data (if required).

4.  **Backup and Recovery Configuration:**
    *   Implement daily and weekly backup procedures as per TR-SBR-002.
    *   Configure off-site storage for two generations of system backups as per TR-SBR-002.
    *   Implement system activity logging and reporting as per TR-SBR-002.
    *   Configure system log archiving to backup tape weekly as per TR-SBR-001.

5.  **Disaster Recovery Setup:**
    *   Establish a disaster recovery site.
    *   Implement replication or backup mechanisms to ensure data is available at the disaster recovery site.
    *   Develop and document a disaster recovery plan.
    *   Conduct regular disaster recovery drills as per TR-DRR-001.

6.  **Testing:**
    *   Conduct thorough testing of all system functions.
    *   Test access control mechanisms.
    *   Test backup and recovery procedures.
    *   Test disaster recovery procedures.

7.  **Monitoring:**
    *   Implement system monitoring tools to track performance and identify potential issues.
    *   Monitor access logs as per REQ-SCR-002.

8.  **Documentation:**
    *   Document all installation and configuration steps.
    *   Document backup and recovery procedures.
    *   Document disaster recovery plan.
    *   Document access control policies.

## 4. Roles and Responsibilities

This section defines the roles and responsibilities for the system installation.

*   **System Administrator:** Responsible for server provisioning, operating system installation, network configuration, and security.
*   **Database Administrator:** Responsible for database setup, configuration, backup, and recovery.
*   **Application Developer:** Responsible for application deployment, configuration, and testing.
*   **Security Administrator:** Responsible for access control configuration and monitoring.
*   **Disaster Recovery Team:** Responsible for developing and executing the disaster recovery plan.

## 5. Timeline

A detailed timeline for the system installation will be developed based on the complexity of the system and the availability of resources.

## 6. Risk Assessment

This section identifies potential risks associated with the system installation and mitigation strategies.

*   **Risk:** Data loss due to hardware failure.
    *   **Mitigation:** Implement redundant storage and regular backups.
*   **Risk:** System downtime due to a disaster.
    *   **Mitigation:** Implement a disaster recovery plan and conduct regular drills.
*   **Risk:** Unauthorized access to data.
    *   **Mitigation:** Implement strong access control policies and monitor access logs.

## 7. Conclusion

This System Installation Plan provides a framework for installing and configuring the system to meet the defined requirements.  Regular review and updates to this plan are essential to ensure its continued effectiveness.
