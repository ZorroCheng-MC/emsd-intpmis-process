![EMSDlogo](media/image1.jpg)

# SYSTEM INSTALLATION PLAN

**FOR**

**I&T PROJECT MANAGEMENT INFORMATION SYSTEM**

**INTPMIS**

**OF**

**ELECTRICAL AND MECHANICAL SERVICES DEPARTMENT**

**Version: 0.1**

**Jan 2025**

? The Government of the Hong Kong Special Administrative Region

The contents of this document remain the property of and may not be reproduced in whole or in part without the express permission of the Government of the HKSAR.

| Distribution | N/A |
|-------------|-------------------------------------| N/A |---|---| N/A | Copy No.    | Holder                              | N/A |---|---| N/A | 1           | Electrical and Mechanical Services Department (EMSD) | N/A |---|---| N/A | 2           | Master Concept (Hong Kong) Limited (MC) | N/A |---|---| N/A | Amendment History | N/A |                | N/A |           | N/A |
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

Below is a logical network diagram in 1/F West Kowloon Government Office for production and UAT site.

[DIAGRAM HERE]

The network will be separated into three zones: DMZ, trusted zone, and storage network.

A two-tier firewall setup will be used to form the trusted zone and DMZ. Incoming network traffic to the system must go through the DMZ before entering the trusted zone.

To utilize hardware resources more effectively, servers listed in section [1.3.3], except the backup server, will be set up in the form of virtual machines (VM) and consolidated into DMZ VM host servers and trusted zone VM host servers for each physical site. Two VM host servers will be built in each zone for the purpose of high availability.

Similarly, storage needed by all servers will be consolidated and provided by SAN storage. A dedicated network will be set up and interconnected with the VM host servers. The backup server will also exist in this storage-dedicated network to carry out backup tasks of VM host servers in DMZ and trusted zone.

The diagram below illustrates the physical setup.

## Hardware Specification

Production and UAT environment:

List of machines and virtual machines:

| Hostname (Physical Machine) | Hostname (Virtual Machine) | Purpose | IP | N/A |---------------------------|---------------------------|---------|-----| N/A |---|---|---|---| N/A | prd-intpmis-db-01 | prd-intpmis-mysql-01 | MySQL Database Server | 192.168.10.50 | N/A |---|---|---|---| N/A | prd-intpmis-app-01 | prd-intpmis-node-01 | Node.js Backend Server | 192.168.10.51 | N/A |---|---|---|---| N/A | prd-intpmis-web-01 | prd-intpmis-vue-01 | Vue.js Frontend Server | 192.168.10.52 | N/A |---|---|---|---|
DR environment:

List of machines and virtual machines:

| Hostname (Physical Machine) | Hostname (Virtual Machine) | Purpose | IP | N/A |---------------------------|---------------------------|---------|-----| N/A |---|---|---|---| N/A | dr-intpmis-db-01 | dr-intpmis-mysql-01 | MySQL Database Server | 192.168.20.50 | N/A |---|---|---|---| N/A | dr-intpmis-app-01 | dr-intpmis-node-01 | Node.js Backend Server | 192.168.20.51 | N/A |---|---|---|---| N/A | dr-intpmis-web-01 | dr-intpmis-vue-01 | Vue.js Frontend Server | 192.168.20.52 | N/A |---|---|---|---|
## Software Specification

| Machine | Hostname | Software Requirement | N/A |---------|----------|---------------------| N/A |---|---|---| N/A | MySQL Database Server | prd-intpmis-mysql-01 | MySQL 8.0.35 | N/A |---|---|---| N/A | Node.js Backend Server | prd-intpmis-node-01 | Node.js 20.11.1, PM2 5.3.0 | N/A |---|---|---| N/A | Vue.js Frontend Server | prd-intpmis-vue-01 | Nginx 1.24.0, Vue.js 3.4.0 | N/A |---|---|---|
Development Frameworks:

| Framework | Version | N/A |-----------|---------| N/A |---|---| N/A | Vue.js (frontend) | 3.4.0 | N/A |---|---| N/A | Node.js (backend) | 20.11.1 | N/A |---|---| N/A | MySQL (database) | 8.0.35 | N/A |---|---|
# Application Deployment Procedure for Production

## Database Server

To install database server, follow these steps:

1. Remote login to prd-intpmis-mysql-01
2. Install MySQL Server 8.0.35
3. Install MySQL Workbench 8.0.35
4. Configure MySQL Server with:
   - Authentication: mysql_native_password
   - Enable networking on port 3306
   - Configure firewall to allow MySQL port (default 3306)
   - Set up SSL/TLS encryption
5. Create database INTPMIS_DB with:
   - Character set: utf8mb4
   - Collation: utf8mb4_unicode_ci
   - Initial size: 50GB
6. Configure database backup schedule:
   - Daily incremental backup at 02:00
   - Weekly full backup on Sunday at 01:00
7. Configure database maintenance plan:
   - Weekly table optimization
   - Daily statistics update
8. Configure database monitoring and alerts:
   - Space usage alerts at 85% and 95%
   - Performance alerts for slow queries
   - Connection limit alerts

## Backend Servers

1. Remote login into prd-intpmis-node-01
2. Install prerequisites:
   - Ubuntu Server 22.04 LTS updates
   - Node.js 20.11.1
   - PM2 5.3.0 (Process Manager)
   - Git for deployment
3. Install backend application:
   - Deploy Node.js API application files to /opt/intpmis/api
   - Configure PM2 ecosystem file:
     - Environment: production
     - Instances: cluster mode (4 instances)
     - Memory limit: 512MB per instance
4. Configure application settings:
   - Update config/production.json with production values
   - Configure MySQL connection strings
   - Set up logging paths (/var/log/intpmis)
5. Configure system services:
   - Set up PM2 as system service
   - Configure log rotation
   - Set up service recovery options
6. Configure SSL certificates:
   - Install SSL certificate for HTTPS
   - Configure reverse proxy (Nginx)
7. Configure Nginx reverse proxy:
   - Create virtual host configuration
   - Configure load balancing
   - Set up compression and caching rules

## Frontend Servers

1. Remote login into prd-intpmis-vue-01
2. Install prerequisites:
   - Ubuntu Server 22.04 LTS updates
   - Nginx 1.24.0
   - Node.js 20.11.1 (for build process)
   - Git for deployment
3. Install frontend application:
   - Deploy Vue.js application files to /var/www/intpmis-web
   - Build production assets using npm run build
   - Configure static file serving
   - Set up compression for static files
4. Configure Nginx:
   - Create virtual host configuration
   - Configure SSL certificates
   - Set up URL rewrite rules for SPA routing
   - Configure CORS headers
   - Set up gzip compression
5. Configure monitoring:
   - Set up Nginx access and error logging
   - Configure health check endpoints
   - Set up performance monitoring
   - Configure log rotation

### sFTP Server Setup

1. Install OpenSSH server in Ubuntu Server:
   - Update package repository: sudo apt update
   - Install OpenSSH server: sudo apt install openssh-server
   - Enable SSH service: sudo systemctl enable ssh
2. Configure OpenSSH server:
   - Create dedicated service account for INTPMIS
   - Configure authentication methods in /etc/ssh/sshd_config
   - Set up SFTP chroot directory: /var/sftp/intpmis
3. Configure firewall:
   - Allow inbound port 22 (SSH): sudo ufw allow 22
   - Restrict access to specific IP ranges
   - Configure fail2ban for intrusion prevention
4. Set up user accounts:
   - Create SFTP users for INTPMIS file transfers
   - Configure user permissions and directory access
   - Set up public key authentication
5. Configure logging and monitoring:
   - Enable detailed SSH logging in /var/log/auth.log
   - Set up log rotation with logrotate
   - Configure alerts for failed login attempts

# System Installation Schedule and Result

## System Installation Schedule

The following table summarises the testing schedule:

| Pre-Requisite | Start Date | End Date | Start time | End Time | N/A |---------------|------------|----------|------------|----------| N/A |---|---|---|---|---| N/A | Database Server Installation (Production and DR) | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Backend Server Installation (Production and DR) | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Frontend Server Installation (Production and DR) | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Functionality test (VM & Networking) | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Database setup | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Deployment for 1st version of frontend server | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Deployment for 1st version of backend server | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Application Health Check | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Deployment for Latest Mobile Application | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Final Check Production Web Server | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Final Check Production Database Server | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Final Check DR Web & Database server | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Final Check IIS & Framework | N/A |  | N/A |  | N/A |---|---|---|---|---|
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
|---|---|---|---|---|---| N/A | Final Check IIS & Framework | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---|
<<End of Document>>
```

Okay, I've analyzed the provided text. Here's a breakdown of the document and a summary of its key points:

**Overall Document Purpose:**

This document is a combination of a user manual for an "I&T Project Management Information System" (INTPMIS) and a User Requirement Specification (URS) for its development.  It describes the system's features, how users interact with it, and the requirements that guided its creation.

**Part 1: User Manual**

This section provides instructions on how to use the INTPMIS system. It covers the following:

*   **Reports:** Describes the different types of reports available in the system, including:
    *   Trend of I&T Wishes, Solutions, and Matched Trial Projects Report
    *   Summary of I&T Wishes Report
    *   Distribution of I&T Solutions by Technology Report
    *   Cash flow for Matched Trial Projects on E&M InnoPortal Report
    *   Statistics on I&T Projects Report
    *   Statistics Technology on I&T Projects Report
    *   Expenditure on I&T Projects Report
*   **User Procedures:**
    *   **Login:** Explains how to log in to the system using SSO or username/password.
    *   **Project Management:** Covers browsing, creating, and editing projects.
    *   **Wish List Management:** Covers browsing and editing wish lists.
    *   **Solution List Management:** Covers browsing and editing solution lists.
*   **Administrator Procedures:**
    *   **Project Management (Admin):**  Highlights the additional fields an administrator can edit in a project.
    *   **Log List Management:** Explains how to view and export logs, and cancel reminders.
*   **Other Functions:**
    *   **Search Function:** Describes how to search for projects, wishes, or solutions using specific criteria.
    *   **Export Function:** Explains how to export records to a CSV file.
    *   **Printing Report Function:** Explains how to print reports.
    *   **Create Project:** Details the fields required when creating a new project.
    *   **Logging:** Explains how to check log records and cancel reminders.

**Part 2: User Requirement Specification (URS)**

This section outlines the requirements for the development of the INTPMIS system. It includes:

*   **Proposed System Overview:** Describes the enhanced aspects of the proposed system, including working environment, data management, data analysis, and workflow.
*   **Future Business Process:** Lists the future business processes that the system will support, such as user login, viewing project lists, creating projects, and viewing reports.
*   **UI & UX Design:** Provides screenshots and descriptions of the user interface for various parts of the system, including the login page, project management, wish management, solution management, report management, and log management.
*   **Functional Requirements:** Lists the functional requirements of the system, such as login, project list, create a project, view or edit a project, wish list, view or edit a wish, solution list, view and edit a solution, report list, view report, log list, view log list, and upload files.
*   **Non-functional Requirements:** Lists the non-functional requirements of the system, such as response time, service time, export, scalability, system performance, user interface requirement, function access rights, access to data, and system backup.

**Key Takeaways:**

*   **Comprehensive System:** INTPMIS is designed to manage I&T projects, wishes, and solutions within the Electrical and Mechanical Services Department (EMSD).
*   **User-Friendly:** The system aims to be user-friendly with a web-based interface and features like search, filtering, and export.
*   **Role-Based Access:**  Different user roles (e.g., regular users, administrators) have different levels of access and functionality.
*   **Reporting and Analysis:**  The system provides various reports to analyze I&T trends and project performance.
*   **Detailed Requirements:** The URS section provides a detailed specification of the system's functional and non-functional requirements.

In summary, this document serves as both a user guide and a development specification for the INTPMIS system, providing a comprehensive overview of its features, functionality, and requirements.


# System Installation Plan

This document outlines the system installation plan based on the provided requirements and specifications. It covers functional and technical requirements, system specifications, and backup/recovery considerations.

## 1. Introduction

This plan details the steps required to install and configure the system, ensuring it meets the defined functional and non-functional requirements. It also addresses backup and recovery procedures to maintain data integrity and system availability.

## 2. Requirements Summary

This section summarizes the key requirements driving the system installation.

### 2.1 Functional Requirements

*   **REQ-SCR-002: Access to Data:**
    *   Define access rights for users to access particular data on a conditional basis.
    *   Define access monitoring for selected data.

*   **REQ-SCR-003: System Backup:**
    *   Meet general backup requirements including data and system.
    *   Backup all audit logging information.

### 2.2 Technical Requirements

*   **TR-SBR-001: Server House Keeping:**
    *   System logs must be archived to backup tape weekly.

*   **TR-SBR-002: Backup, Recovery and System Archive:**
    *   Provide daily backup.
    *   Provide weekly system backup.
    *   Provide 2 generations of system backup stored off-site.
    *   Provide system activity logs and reports.

*   **TR-DRR-001: System Disaster Recovery:**
    *   Participate in disaster recovery activities and complete assigned tasks following the disaster recovery plan.
    *   Coordinate with new system users to participate in disaster recovery activities.
    *   Resume the whole system from the disaster recovery site to the normal production environment.

## 3. System Specifications

The system provides the following functions:

*   **Information Viewing:**
    *   View Project List and Detail
    *   View Wish List and Detail
    *   View Solution List and Detail
    *   View Report List and Detail
    *   View Log List and Detail
    *   Search Projects
    *   Search Wishes
    *   Search Solutions
    *   Filter Projects
    *   Filter Wishes
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

## 4. Installation Steps

This section outlines the steps required to install the system.  Specific steps will vary depending on the chosen technology stack and deployment environment.

1.  **Environment Setup:**
    *   Provision necessary hardware and software resources (servers, databases, etc.).
    *   Configure network settings and security policies.
    *   Install operating system and required dependencies.

2.  **Software Installation:**
    *   Install the system software components.
    *   Configure the system based on the defined requirements.

3.  **Database Setup:**
    *   Create and configure the database.
    *   Import initial data (if applicable).

4.  **Security Configuration:**
    *   Implement access control mechanisms based on REQ-SCR-002.
    *   Configure user authentication and authorization.
    *   Implement data encryption (if required).

5.  **Backup and Recovery Configuration:**
    *   Configure daily and weekly backups as per TR-SBR-002.
    *   Set up off-site storage for backups (2 generations).
    *   Configure system activity logs and reports.
    *   Configure system log archiving to backup tape weekly (TR-SBR-001).

6.  **Testing:**
    *   Perform functional testing to ensure all system functions are working as expected.
    *   Perform performance testing to ensure the system meets performance requirements.
    *   Perform security testing to identify and address any security vulnerabilities.
    *   Test the backup and recovery procedures.

7.  **Deployment:**
    *   Deploy the system to the production environment.
    *   Monitor the system performance and stability.

## 5. Backup and Recovery Plan

This section details the backup and recovery procedures to ensure data integrity and system availability.

### 5.1 Backup Procedures

*   **Daily Backup:** Perform a daily backup of the database and critical system files.
*   **Weekly Backup:** Perform a full weekly backup of the entire system, including the operating system, applications, and data.
*   **Off-site Storage:** Store two generations of weekly backups off-site for disaster recovery purposes.
*   **Log Archiving:** Archive system logs to backup tape weekly.

### 5.2 Recovery Procedures

*   **Data Recovery:** In the event of data loss, restore the database from the most recent backup.
*   **System Recovery:** In the event of a system failure, restore the system from the most recent full backup.
*   **Disaster Recovery:** In the event of a disaster, restore the system from the off-site backups at the disaster recovery site.  Follow the procedures outlined in the disaster recovery plan, as per TR-DRR-001.

## 6. Security Considerations

*   Implement strong passwords and multi-factor authentication.
*   Regularly update security patches and software versions.
*   Monitor system logs for suspicious activity.
*   Restrict access to sensitive data and system resources.
*   Conduct regular security audits.

## 7. Roles and Responsibilities

This section defines the roles and responsibilities of the individuals involved in the system installation.

*   **System Administrator:** Responsible for installing and configuring the system, managing backups, and ensuring system security.
*   **Database Administrator:** Responsible for managing the database, including backups and recovery.
*   **Security Administrator:** Responsible for implementing and maintaining security policies.
*   **Application Developer:** Responsible for developing and maintaining the system software.
*   **Project Manager:** Responsible for overseeing the entire installation process and ensuring that it is completed on time and within budget.

## 8.  Contingency Plan

*   **Rollback Plan:** In case of a failed installation, a rollback plan should be in place to revert the system to its previous state.  This includes having backups of the previous system configuration and data.
*   **Escalation Procedures:**  Clearly defined escalation procedures should be in place to address any issues that arise during the installation process.

## 9.  Conclusion

This System Installation Plan provides a framework for successfully installing and configuring the system. By following the steps outlined in this plan, the system can be deployed in a secure and reliable manner, meeting the defined functional and technical requirements.  Regular review and updates to this plan are recommended to ensure its continued relevance and effectiveness.