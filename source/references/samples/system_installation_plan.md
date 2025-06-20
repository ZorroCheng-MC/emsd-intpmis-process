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

Okay, I've analyzed the provided text and extracted the key information. Here's a summary of the INTPMIS system, focusing on its reports, user procedures, administrator procedures, and the User Requirement Specification:

**I. System Overview**

The INTPMIS (I&T Project Management Information System) is designed for the Electrical and Mechanical Services Department (EMSD). It aims to improve upon the current system by providing:

*   An easy-to-use web portal.
*   Enhanced data management.
*   Data analysis and reporting capabilities.
*   Workflow automation.

**II. Reports**

The system includes seven different reports to analyze and show the results of projects, wishes, and solutions. These reports include:

1.  **Trend of I&T Wishes, Solutions, and Matched Trial Projects Report:** Shows the number of wishes, solutions, and matched projects over time (monthly).
2.  **Summary of I&T Wishes Report:** Shows the number of wishes belonging to different divisions.
3.  **Distribution of I&T Solutions by Technology Report:** Groups and counts the number of solutions using specific technologies.
4.  **Cash flow for Matched Trial Projects on E&M InnoPortal Report:** Shows the total cash flow of matched projects for each division in a year.
5.  **Statistics on I&T Projects Report:** Counts projects by division and status (complete or in-progress).  Includes "Show All" and "Filter 0 items" buttons.
6.  **Statistics Technology on I&T Projects Report:** Counts and calculates the percentage of technologies used in projects.
7.  **Expenditure on I&T Projects Report:** Sums the actual and projected expenditures of projects in a year, broken down by division.

**Common Report Features:**

*   **Search Function:** Allows users to filter reports by month.
*   **Export Function:** Allows users to export all records after a search to a CSV file.
*   **Printing Report Function:** Allows users to print all reports by clicking the "Print" button.

**III. User Procedures**

The user procedures cover the following areas:

*   **Login:**
    *   Supports SSO (Single Sign-On) via EMSD Active Directory.
    *   Offers username/password login as an alternative.
*   **Project Management:**
    *   Browsing Project List: Includes viewing, filtering, searching, and exporting projects.
    *   Creating a Project: Details the required fields and validation.
    *   Editing a Project: Allows users to modify project information.
*   **Wish List Management:**
    *   Browsing Wish List: Includes viewing, searching, filtering, and exporting wishes.
    *   Editing a Wish: Allows users to modify wish information.
*   **Solution List Management:**
    *   Browsing Solution List: Includes viewing, searching, filtering, and exporting solutions.
    *   Editing a Solution: Allows users to modify solution information.

**IV. Administrator Procedures**

The administrator procedures cover:

*   **Project Management:**
    *   Editing a Project: Administrators have access to more fields than regular users.
*   **Log List:**
    *   Browsing Log List: Includes viewing, exporting, and canceling reminders related to log entries.

**V. User Requirement Specification (URS)**

The URS document outlines the user requirements for the INTPMIS system. Key aspects include:

*   **Proposed System Overview:**  Details the goals of the new system.
*   **Future Business Processes:** Lists the key business processes supported by the system (e.g., User Login, View Project List, Create Project).
*   **UI & UX Design:** Provides mockups of key screens (Login, Project Management, Wish Management, Solution Management, Report Management, Log Management).
*   **Functional Requirements:** Lists the functional requirements (REQ-SYS-XXX) with details on priority, description, frequency of use, acceptance criteria, and related business processes.  Examples include:
    *   Login
    *   Project List
    *   Create a Project
    *   View or Edit a Project
    *   Wish List
    *   View or Edit a Wish
    *   Solution List
    *   View and Edit a Solution
    *   Report List
    *   View Report
    *   Log List
    *   View Log List
    *   Upload File
*   **Non-Functional Requirements:** Lists the non-functional requirements (REQ-SR/UR/SCR-XXX) with details on priority and description.  Examples include:
    *   Response Time
    *   Service Time
    *   Export
    *   Scalability
    *   System Performance
    *   User Interface Requirement
    *   Function Access Rights
    *   Access to Data
    *   System Backup

**Key Takeaways:**

*   INTPMIS is a comprehensive system designed to manage I&T projects, wishes, and solutions within EMSD.
*   It provides robust reporting and analysis capabilities.
*   User procedures are well-documented.
*   The URS document provides a detailed specification of the system's requirements.

Let me know if you'd like me to elaborate on any specific aspect of the system!


# System Installation Plan

This document outlines the system installation plan based on the provided requirements and specifications. It covers functional and technical requirements, focusing on system controls, backup and recovery, and disaster recovery.

## 1. Introduction

This plan details the steps required to successfully install and configure the system, ensuring it meets the defined requirements for data access, backup, recovery, and disaster recovery.

## 2. Requirements Summary

This section summarizes the key requirements driving the system installation.

### 2.1 Functional Requirements

*   **REQ-SCR-002: Access to Data:**  The system must allow for defining access rights for users to specific data, conditionally. It must also support access monitoring for selected data.
*   **REQ-SCR-003: System Backup:** The system must meet general backup requirements, including data, system, and all audit logging information.

### 2.2 Technical Requirements

*   **TR-SBR-001: Server House Keeping:** System logs must be archived to backup tape weekly.
*   **TR-SBR-002: Backup, Recovery and System Archive:**
    *   Provide daily backup.
    *   Provide weekly system backup.
    *   Provide 2 generations of system backup stored off-site.
    *   Provide system activity logs and reports.
*   **TR-DRR-001: System Disaster Recovery:**
    *   Participate in disaster recovery activities and complete assigned tasks following the disaster recovery plan.
    *   Coordinate with new system users to participate in disaster recovery activities.
    *   Resume the entire system from the disaster recovery site to the normal production environment.

## 3. System Specification

The system provides the following functions, categorized as follows:

| Item | Category             | System Functions              | N/A |------|----------------------|-------------------------------| N/A |---|---|---| N/A | 1    | Information Viewing  | View Project List and Detail  | N/A |---|---|---| N/A | 2    | Content Management   | Create a Project              | N/A |---|---|---| N/A | 3    | Content Management   | Edit a Project                | N/A |---|---|---| N/A | 4    | Information Viewing  | Search Projects               | N/A |---|---|---| N/A | 5    | Information Viewing  | Filter Projects               | N/A |---|---|---| N/A | 6    | Workflow Application | Export Projects               | N/A |---|---|---| N/A | 7    | Information Viewing  | View Wish List and Detail     | N/A |---|---|---| N/A | 8    | Content Management   | Edit a Wish                   | N/A |---|---|---| N/A | 9    | Information Viewing  | Search Wishes                 | N/A |---|---|---| N/A | 10   | Information Viewing  | Filter Wishes                 | N/A |---|---|---| N/A | 11   | Workflow Application | Export Wishes                 | N/A |---|---|---| N/A | 12   | Information Viewing  | View Solution List and Detail | N/A |---|---|---| N/A | 13   | Content Management   | Edit a Solution               | N/A |---|---|---| N/A | 14   | Information Viewing  | Search Solutions              | N/A |---|---|---| N/A | 15   | Information Viewing  | Filter Solutions              | N/A |---|---|---| N/A | 16   | Workflow Application | Export Solutions              | N/A |---|---|---| N/A | 17   | Information Viewing  | View Report List and Detail   | N/A |---|---|---| N/A | 18   | Workflow Application | Export Report                 | N/A |---|---|---| N/A | 19   | Information Viewing  | View Log List and Detail      | N/A |---|---|---| N/A | 20   | Content Management   | Cancel Reminder for Log       | N/A |---|---|---|
## 4. Installation Steps

This section outlines the high-level steps for installing the system.  Specific details for each step will be documented in separate, more detailed procedures.

1.  **Environment Preparation:**
    *   Provision necessary hardware and software infrastructure (servers, databases, operating systems, etc.).
    *   Configure network connectivity.
    *   Install and configure any prerequisite software.
2.  **Software Installation:**
    *   Install the system software components.
    *   Configure the system based on the system specifications.
3.  **Data Migration (if applicable):**
    *   Migrate existing data to the new system.
    *   Verify data integrity after migration.
4.  **Access Control Configuration:**
    *   Implement access control mechanisms based on REQ-SCR-002.
    *   Define user roles and permissions.
    *   Configure access monitoring.
5.  **Backup and Recovery Configuration:**
    *   Configure daily and weekly backups as per TR-SBR-002.
    *   Configure off-site storage for backup generations.
    *   Implement system activity logging and reporting.
    *   Configure weekly system log archiving to backup tape as per TR-SBR-001.
6.  **Disaster Recovery Setup:**
    *   Establish a disaster recovery site.
    *   Develop and document a disaster recovery plan.
    *   Configure replication or other mechanisms for data and system recovery.
7.  **Testing:**
    *   Conduct thorough testing of all system functions.
    *   Test access control mechanisms.
    *   Perform backup and recovery testing.
    *   Conduct disaster recovery drills.
8.  **User Training:**
    *   Provide training to users on the new system.
    *   Include training on disaster recovery procedures.
9.  **Go-Live:**
    *   Deploy the system to the production environment.
    *   Monitor system performance and stability.
10. **Post-Installation Support:**
    *   Provide ongoing support and maintenance.
    *   Address any issues or bugs that arise.

## 5. Backup and Recovery Plan

This section details the backup and recovery procedures.

*   **Backup Schedule:**
    *   Daily backups of critical data.
    *   Weekly full system backups.
    *   Weekly archiving of system logs to backup tape.
*   **Backup Storage:**
    *   On-site storage for recent backups.
    *   Off-site storage for two generations of system backups.
*   **Recovery Procedures:**
    *   Documented procedures for restoring data and systems from backups.
    *   Regular testing of recovery procedures.

## 6. Disaster Recovery Plan

This section outlines the disaster recovery plan.

*   **Disaster Recovery Site:**
    *   A designated location for recovering the system in the event of a disaster.
*   **Recovery Time Objective (RTO):**
    *   The target time for restoring the system after a disaster.  (This should be defined based on business needs, but is not specified in the provided documents).
*   **Recovery Point Objective (RPO):**
    *   The acceptable amount of data loss in the event of a disaster. (This should be defined based on business needs, but is not specified in the provided documents).
*   **Disaster Recovery Procedures:**
    *   Detailed steps for activating the disaster recovery site.
    *   Procedures for restoring data and systems.
    *   Communication plan for notifying stakeholders.
*   **Testing:**
    *   Regular disaster recovery drills to test the plan and ensure its effectiveness.

## 7. Roles and Responsibilities

*   **System Administrator:** Responsible for installing, configuring, and maintaining the system.
*   **Database Administrator:** Responsible for managing the database and ensuring data integrity.
*   **Security Administrator:** Responsible for implementing and managing access control.
*   **Backup Administrator:** Responsible for configuring and monitoring backups.
*   **Disaster Recovery Coordinator:** Responsible for developing and maintaining the disaster recovery plan.
*   **Users:** Responsible for participating in disaster recovery activities as needed.

## 8. Risk Assessment

*   **Data Loss:**  Inadequate backup procedures could lead to data loss.
*   **System Downtime:**  Hardware or software failures could cause system downtime.
*   **Security Breaches:**  Unauthorized access could compromise data security.
*   **Disaster Events:**  Natural disasters or other events could disrupt system operations.

## 9. Mitigation Strategies

*   Implement robust backup and recovery procedures.
*   Implement redundant hardware and software components.
*   Implement strong access control mechanisms.
*   Develop and test a comprehensive disaster recovery plan.

## 10.  Priority

All requirements listed have a priority of "M" (Medium).  This indicates that while important, they may not be critical for initial launch but should be addressed in a timely manner.  A more detailed prioritization exercise should be conducted to determine which requirements are most critical for the initial installation and subsequent phases.

## 11.  Future Considerations

*   Regularly review and update the installation plan, backup and recovery plan, and disaster recovery plan.
*   Implement automated monitoring and alerting for system performance and security.
*   Consider cloud-based solutions for backup and disaster recovery.
*   Implement a formal change management process.