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

Okay, I've analyzed the provided text. Here's a breakdown of the key information, focusing on the user manual aspects and the system requirements:

**1.  Report Descriptions:**

The document details seven reports within the INTPMIS system:

*   **Trend of I&T Wishes, Solutions, and Matched Trial Projects Report:** Shows monthly trends of wishes, solutions, and matched projects.  Users can select the month.
*   **Summary of I&T Wishes Report:**  Summarizes wishes by division, including wishes from departments outside EMSD.
*   **Distribution of I&T Solutions by Technology Report:**  Groups and counts solutions based on the technologies used.
*   **Cash flow for Matched Trial Projects on E&M InnoPortal Report:** Shows the total cash flow of matched projects by division per year.
*   **Statistics on I&T Projects Report:** Counts projects by division, categorized by "complete" or "in-progress" status.  Includes "Show All" and "Filter 0 items" buttons.
*   **Statistics Technology on I&T Projects Report:**  Counts and calculates the percentage of technologies used in projects.
*   **Expenditure on I&T Projects Report:**  Sums actual and projected project expenditures for the year, broken down by division.

**2. User Procedures and Operation Manual:**

*   **Login:**
    *   **SSO Login:** Uses EMSD Active Directory and LDAP API.
    *   **Username Login:** Requires email address and password.  Provides error handling for failed logins.
*   **Project Management:**
    *   **Browsing Project List:**
        *   "View" option to see project details.
        *   Filtering by inputting values and selecting records per page.
        *   Search functionality with criteria selection.
        *   Exporting options: "Export Records" (searched records) and "Export All Records" (all records) to CSV.
    *   **Creating a Project:**
        *   Click "Create" button.
        *   Required fields must be filled.
        *   Error messages for invalid or missing input.
        *   Successful creation message with project number.
    *   **Editing a Project:**
        *   Click "Edit" button and edit icon.
        *   Allows modifying project information.
        *   "Save All" button to save changes.
        *   Error handling for invalid input.
        *   Success message upon saving.
*   **Wish List Management:**
    *   **Browsing Wish List:**
        *   "View" option to see wish details.
        *   Search functionality with criteria selection.
        *   Filtering by inputting values and selecting records per page.
        *   Exporting options: "Export Records" (searched records) and "Export All Records" (all records) to CSV.
    *   **Editing a Wish:**
        *   Input values to edit.
        *   "Save All" button.
        *   Error handling for invalid input.
        *   Success message upon saving.
*   **Solution List Management:**
    *   **Browsing Solution List:**
        *   "View" option to see solution details.
        *   Search functionality with criteria selection.
        *   Filtering by inputting values and selecting records per page.
        *   Exporting options: "Export Records" (searched records) and "Export All Records" (all records) to CSV.
    *   **Editing a Solution:**
        *   Input values to edit.
        *   "Save All" button.
        *   Error handling for invalid input.
        *   Success message upon saving.

**3. Administrator Procedures and Operation Manual:**

*   **Project Management (Admin):**
    *   **Editing a Project:** Admins have access to edit more fields than regular users (e.g., "Date of Uploading Interim Evaluation Report").
*   **Log List:**
    *   **Browsing Log List:**
        *   Select log type.
        *   View log details using the "+" button.
        *   Export logs to CSV.
    *   **Cancel Reminder:**
        *   Cancel reminders for individual logs or batch cancel selected logs.
*   **Search Function:**
    *   Allows searching projects, wishes, or solutions based on field criteria.
    *   Report search allows selecting a month to filter data.
*   **Export Function:**
    *   Exports records to CSV.
*   **Printing Report Function:**
    *   Allows printing reports via a print button.
*   **Create Project:**
    *   Details all the fields required for creating a project, including input types, requirements, and remarks.
*   **Logging:**
    *   Details the logging functionality and how to manage log records.

**4. User Requirement Specification (URS):**

*   **Proposed System Overview:**
    *   Easy-to-use web portal.
    *   Co-editing of database entries.
    *   MySQL database for I&T project information.
    *   Data analysis and customizable reports.
    *   Workflow automation.
*   **Future Business Processes:**
    *   Lists business processes such as User Login, View Project List, Create Project, View and Edit Project, View Wish List, View and Edit Wish, View Solution List, View and Edit Solution, View Report List, View Report, View Log List, and Upload File.
*   **UI & UX Design:**
    *   Provides screenshots of various UI elements, including login page, project management pages, wish management pages, solution management pages, report management pages, and log management pages.
*   **Functional Requirements:**
    *   Lists functional requirements such as Login, Project List, Create a Project, View or Edit a Project, Wish List, View or Edit a Wish, Solution List, View and Edit a Solution, Report List, View Report, Log List, View Log List, and Upload File.
*   **Non-functional Requirements:**
    *   Lists non-functional requirements such as Response Time, Service Time, Export, Scalability, System Performance, User Interface Requirement, Function Access Rights, Access to Data, and System Backup.

**Key Takeaways and Potential Improvements:**

*   **Comprehensive Documentation:** The document provides a good level of detail for a user manual and system specification.
*   **Visual Aids:** The inclusion of screenshots is very helpful for understanding the UI.
*   **Clarity:** Some sections could benefit from clearer language and more concise explanations.
*   **Target Audience:**  Consider tailoring the language to the specific user roles (e.g., a separate section for administrators with more technical details).
*   **Navigation:**  A table of contents with hyperlinks would make it easier to navigate the document.
*   **Error Handling:**  Expand on the error handling sections to provide more specific examples of error messages and how to resolve them.
*   **Workflow Diagrams:**  Consider adding workflow diagrams to visually represent the key business processes.
*   **Accessibility:** Ensure the document is accessible to users with disabilities (e.g., using alt text for images, providing sufficient color contrast).
*   **Training:**  The document mentions training courses and user experience sessions.  It would be helpful to include information about how to access these resources.

This analysis should give you a good understanding of the document's content and potential areas for improvement.


# System Installation Plan Requirements

This document outlines the system requirements, focusing on system controls, backup and recovery, and disaster recovery. It also includes a list of system functions.

## 1. System Controls Requirements

### REQ-SCR-002: Access Monitoring

*   **Requirement ID:** REQ-SCR-002
*   **Category:** System Controls Requirements
*   **Non-functional Requirement Description:**
    1.  Able to define access monitoring for selected data on a conditional basis.
    2.  Able to define access monitoring for the selected data.

### REQ-SCR-003: System Backup

*   **Category:** System Controls Requirements
*   **Requirement Title:** System Backup
*   **Non-functional Requirement Description:** Able to meet general backup requirements including data and system; and all audit logging information.

## 2. System Backup and Recovery Requirements

### Technical Requirements

*   **TR-SBR-001: Server House Keeping**
    *   **Priority:** M (Mandatory)
    *   **Technical Requirement Description:** System logs must be archived to backup tape weekly.

*   **TR-SBR-002: Backup, Recovery and System Archive**
    *   **Priority:** M (Mandatory)
    *   **Technical Requirement Description:**
        1.  Provide weekly system backup
        2.  Provide 2 generations of system backup stored off-site

## 3. System Disaster Recovery Requirements

### Technical Requirements

*   **TR-DRR-001: System Disaster Recovery**
    *   **Priority:** M (Mandatory)
    *   **Technical Requirement Description:**
        1.  System administrator must be assigned disaster recovery activities following the procedures in the disaster recovery plan.
        2.  System administrator must be able to perform system recovery activities.
        3.  Resume the whole system from disaster recovery site to normal.

## 4. System Functions

The following table outlines key system functions, categorized by their purpose.

| Item | Category             | System Function               | N/A |------|----------------------|-------------------------------| N/A |---|---|---| N/A | 1    | Information Viewing  | View Project List and Detail  | N/A |---|---|---| N/A | 3    | Content Management   | Edit a Project                | N/A |---|---|---| N/A | 4    | Information Viewing  | Search Projects               | N/A |---|---|---| N/A | 6    | Workflow Application | Export Projects               | N/A |---|---|---| N/A | 7    | Information Viewing  | View Wish List and Detail     | N/A |---|---|---| N/A | 9    | Information Viewing  | Search Wishes                 | N/A |---|---|---| N/A | 10   | Information Viewing  | Filter Wishes                 | N/A |---|---|---| N/A | 12   | Information Viewing  | View Solution List and Detail | N/A |---|---|---| N/A | 13   | Content Management   | Edit a Solution               | N/A |---|---|---| N/A | 15   | Information Viewing  | Filter Solutions              | N/A |---|---|---| N/A | 16   | Workflow Application | Export Solutions              | N/A |---|---|---| N/A | 18   | Workflow Application | Export Report                 | N/A |---|---|---| N/A | 19   | Information Viewing  | View Log List and Detail      |