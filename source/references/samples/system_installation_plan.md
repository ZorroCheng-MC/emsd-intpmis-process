![Logo](media/image1.jpg)

# SYSTEM INSTALLATION PLAN

**FOR**

**[PROJECT_NAME]**

**OF**

**[DEPARTMENT_NAME]**

**Version: [VERSION]**

**[DATE]**

? The Government of the Hong Kong Special Administrative Region

The contents of this document remain the property of and may not be reproduced in whole or in part without the express permission of the Government of the HKSAR.

| Distribution | N/A |
|-------------|-------------------------------------| N/A |---|---| N/A | Copy No.    | Holder                              | N/A |---|---| N/A | 1           | [DEPARTMENT_NAME]                   | N/A |---|---| N/A | 2           | Master Concept (Hong Kong) Limited (MC) | N/A |---|---| N/A | Amendment History | N/A |                | N/A |           | N/A |
|------------------|------------------------|----------------|------------|-----------|-----------| N/A |---|---|---|---|---|---| N/A | Change Number    | Revision Description   | Pages Affected | Revision / | Date      | Approval  | N/A |                  | N/A | on Respective  | Version    | N/A | Reference | N/A |                  | N/A | Version        | Number     | N/A |           | N/A |---|---|---|---|---|---| N/A | 1                | 1st draft             | All            | [VERSION]  | [DATE]    | N/A |
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

The System Installation plan describes the procedure and schedule for deploying the application in the production environment, including the main components of the system:

- Database Server
- Backend Server
- Frontend and Web Portal Server

# Project Environment Description

## Network Diagram

[NETWORK_DIAGRAM_DESCRIPTION]

[DIAGRAM HERE]

[NETWORK_ARCHITECTURE_DESCRIPTION]

## Hardware Specification

Production and UAT environment:

List of machines and virtual machines:

| Hostname (Physical Machine) | Hostname (Virtual Machine) | Purpose | IP | N/A |---------------------------|---------------------------|---------|-----| N/A |---|---|---|---| N/A | [HARDWARE_SPECIFICATIONS] | [HARDWARE_SPECIFICATIONS] | [HARDWARE_SPECIFICATIONS] | [HARDWARE_SPECIFICATIONS] | N/A |---|---|---|---|
DR environment:

List of machines and virtual machines:

| Hostname (Physical Machine) | Hostname (Virtual Machine) | Purpose | IP | N/A |---------------------------|---------------------------|---------|-----| N/A |---|---|---|---| N/A | [DR_HARDWARE_SPECIFICATIONS] | [DR_HARDWARE_SPECIFICATIONS] | [DR_HARDWARE_SPECIFICATIONS] | [DR_HARDWARE_SPECIFICATIONS] | N/A |---|---|---|---|
## Software Specification

| Machine | Hostname | Software Requirement | N/A |---------|----------|---------------------| N/A |---|---|---| N/A | [SOFTWARE_SPECIFICATIONS] | [SOFTWARE_SPECIFICATIONS] | [SOFTWARE_SPECIFICATIONS] | N/A |---|---|---|
Development Frameworks:

| Framework | Version | N/A |-----------|---------| N/A |---|---| N/A | [FRAMEWORK_SPECIFICATIONS] | [FRAMEWORK_SPECIFICATIONS] | N/A |---|---|
# Application Deployment Procedure for Production

## Database Server

[DATABASE_INSTALLATION_PROCEDURES]

## Backend Servers

[BACKEND_INSTALLATION_PROCEDURES]

## Frontend Servers

[FRONTEND_INSTALLATION_PROCEDURES]

### sFTP Server Setup

[SFTP_INSTALLATION_PROCEDURES]

# System Installation Schedule and Result

## System Installation Schedule

The following table summarises the testing schedule:

| Pre-Requisite | Start Date | End Date | Start time | End Time | N/A |---------------|------------|----------|------------|----------| N/A |---|---|---|---|---| N/A | [INSTALLATION_SCHEDULE] | [INSTALLATION_SCHEDULE] | [INSTALLATION_SCHEDULE] | [INSTALLATION_SCHEDULE] | [INSTALLATION_SCHEDULE] | N/A |---|---|---|---|---|
## System Installation Result

The following table summarises the actual system installation schedule:

| Pre-Requisite | Actual Start Date | Actual End Date | Actual Start time | Actual End Time | Status/Result | N/A |---------------|-------------------|-----------------|-------------------|-----------------|---------------| N/A |---|---|---|---|---|---| N/A | [INSTALLATION_RESULTS] | [INSTALLATION_RESULTS] | [INSTALLATION_RESULTS] | [INSTALLATION_RESULTS] | [INSTALLATION_RESULTS] | [INSTALLATION_RESULTS] | N/A |---|---|---|---|---|---|
<<End of Document>>
```

# System Installation Plan for I&T Project Management Information System (INTPMIS)

This document outlines the system installation plan for the I&T Project Management Information System (INTPMIS) developed for the Electrical and Mechanical Services Department (EMSD). It consolidates information from the provided User Requirement Specification (URS) and other documentation to provide a comprehensive overview of the installation process, requirements, and procedures.

## 1. Introduction

The INTPMIS aims to address the limitations of the current system by providing a user-friendly web portal for managing I&T projects, wishes, and solutions.  It includes features for data management, analysis, and reporting, improving efficiency and accuracy in tracking and managing I&T initiatives.

## 2. System Overview

The INTPMIS is a web-based application built on a MySQL database. It stores information related to E&M InnoPortal and other I&T projects, including text, data, reports, and attachments (PDF, Microsoft Word, JPEG, PNG, etc.).  The system provides a centralized platform for users to access, manage, and analyze I&T project data.

## 3. Installation Prerequisites

Before installing the INTPMIS, ensure the following prerequisites are met:

*   **Hardware Requirements:**  (Specific hardware requirements are not detailed in the provided documents.  This section needs to be populated with details from the system architecture and design documents.)
*   **Software Requirements:**
    *   Web Server (e.g., Apache, Nginx)
    *   MySQL Database Server
    *   Operating System (Specify supported OS versions)
    *   PHP (Specify required version)
    *   Web Browsers: Internet Explorer, Chrome (with Apollo support version)
*   **Network Requirements:**  (Specify network connectivity requirements, including firewall rules and port configurations.)
*   **User Accounts:**  Active Directory accounts for user authentication.
*   **Permissions:** Appropriate file system and database permissions for the INTPMIS application.

## 4. Installation Steps

The following steps outline the installation process for the INTPMIS:

1.  **Server Setup:**
    *   Install and configure the web server (e.g., Apache, Nginx).
    *   Install and configure the MySQL database server.
    *   Ensure PHP is installed and configured correctly with the necessary extensions for database connectivity.

2.  **Database Setup:**
    *   Create a MySQL database for INTPMIS.
    *   Import the database schema and initial data. (This assumes a database dump file is available.)

3.  **Application Deployment:**
    *   Deploy the INTPMIS application files to the web server's document root.
    *   Configure the application to connect to the MySQL database.  This typically involves updating configuration files with database credentials.

4.  **User Authentication Configuration:**
    *   Configure the application to use Windows Active Directory for single sign-on.
    *   Map existing user permission matrix to the INTPMIS roles and permissions.

5.  **Testing:**
    *   Verify that the application is accessible through a web browser.
    *   Test user login and authentication.
    *   Test basic functionality, such as creating, viewing, and editing projects, wishes, and solutions.
    *   Test reporting and data export features.

## 5. Post-Installation Configuration

After the initial installation, the following configurations need to be performed:

*   **User Role and Permission Configuration:**  Define user roles and permissions based on the existing permission matrix.
*   **Filtering and Sorting Criteria Configuration:** Configure the default filtering and sorting criteria for project, wish, and solution lists.
*   **Backup Configuration:** Configure daily and weekly system backups, including off-site storage.
*   **Logging Configuration:**  Configure system activity logs and reports.

## 6. System Backup and Recovery

*   **Backup Schedule:** Daily and weekly system backups.
*   **Backup Storage:** Two generations of system backups stored off-site.
*   **Backup Content:** Data, system files, and audit logging information.
*   **Recovery Procedures:**  Detailed procedures for restoring the system from backup in case of data loss or system failure.

## 7. Disaster Recovery

*   **Disaster Recovery Plan:**  A comprehensive plan for recovering the system in the event of a disaster.
*   **Disaster Recovery Site:**  A designated location for restoring the system in case of a disaster.
*   **Disaster Recovery Activities:**  Procedures for participating in disaster recovery activities, coordinating with users, and resuming the system from the disaster recovery site to the normal production environment.

## 8. User Training and Documentation

*   **Training Courses:** Provide training courses for users on how to use the INTPMIS.
*   **User Experience Sessions:** Conduct user experience sessions to gather feedback and improve the system.
*   **Program Manual:**  Develop a program manual including a workflow manual.
*   **System Manual:**  Create a system manual for administrators and technical staff.
*   **User Procedures Manual:**  Develop a user procedures manual for end-users.

## 9. System Functions

The INTPMIS provides the following system functions:

*   **Information Viewing:**
    *   View Project List and Detail
    *   View Wish List and Detail
    *   View Solution List and Detail
    *   View Report List and Detail
    *   View Log List and Detail
*   **Content Management:**
    *   Create a Project
    *   Edit a Project
    *   Edit a Wish
    *   Edit a Solution
    *   Cancel Reminder for Log
*   **Information Retrieval:**
    *   Search Projects
    *   Search Wishes
    *   Search Solutions
    *   Filter Projects
    *   Filter Wishes
    *   Filter Solutions
*   **Workflow Application:**
    *   Export Projects
    *   Export Wishes
    *   Export Solutions
    *   Export Report
*   **File Management:**
    *   Upload Files

## 10. Functional Requirements

The INTPMIS must meet the following functional requirements:

*   **REQ-SYS-001 - Login:** Support single sign-on through Windows Active Directory.
*   **REQ-SYS-002 - Project List:** Allow users to search, sort, filter, and export projects.
*   **REQ-SYS-003 - Create a Project:** Allow users to create new projects.
*   **REQ-SYS-004 - View and Edit a Project:** Support read-only and edit modes based on user permissions.
*   **REQ-SYS-005 - Wish List:** Allow users to search, sort, filter, and export wishes.
*   **REQ-SYS-006 - View and Edit a Wish:** Support read-only and edit modes based on user permissions.
*   **REQ-SYS-007 - Solution List:** Allow users to search, sort, filter, and export solutions.
*   **REQ-SYS-008 - View and Edit a Solution:** Support read-only and edit modes based on user permissions.
*   **REQ-SYS-009 - Report List:** Allow users to search, sort, filter, and export reports.
*   **REQ-SYS-010 - View Report:** Support read-only mode for reports.
*   **REQ-SYS-011 - Log List:** Allow users to search, sort, filter, and export logs.
*   **REQ-SYS-012 - View Log List:** Support read-only mode for logs.
*   **REQ-SYS-013 - Upload Files:** Allow users to upload files in various formats.

## 11. Non-Functional Requirements

The INTPMIS must meet the following non-functional requirements:

*   **REQ-SR-001 - Response Time:** 95% of predefined queries should respond within 5 seconds.
*   **REQ-SR-002 - Service Time:** System availability of 99.0% between 08:00 and 20:00 daily.
*   **REQ-SR-003 - Export:** Allow data to be exported in Excel format.
*   **REQ-SR-004 - Scalability:** Provide scalability options for future system expansion.
*   **REQ-SR-005 - System Performance:** Provide a technically sound architecture to meet performance requirements.
*   **REQ-UR-001 - User Interface Requirement:** User-friendly interface consistent with web-based applications, responsive design, and compatibility with multiple browsers.
*   **REQ-SCR-001 - Function Access Rights:** Define user access rights based on roles and user levels.
*   **REQ-SCR-002 - Access to Data:** Define access rights for users to access particular data.
*   **REQ-SCR-003 - System Backup:** Meet general backup requirements for data, system, and audit logging information.

## 12. Technical Requirements

The INTPMIS must meet the following technical requirements:

*   **TR-SBR-001 - Server House Keeping:** Archive system logs to backup tape weekly.
*   **TR-SBR-002 - Backup, Recovery and System Archive:** Provide daily backup, weekly system backup, 2 generations of off-site backup, and system activity logs.
*   **TR-DRR-001 - System Disaster Recovery:** Participate in disaster recovery activities and resume the system from the disaster recovery site.

## 13. Administrator Procedures and Operation Manual

(This section summarizes key administrator tasks based on the provided documentation.)

*   **Project Management:**
    *   Administrators (Role 6) have extended editing capabilities for project information, including fields like "Date of Uploading Interim Evaluation Report."
*   **Log Management:**
    *   Administrators can view and export log records for reports, wishes, and solutions.
    *   Administrators can cancel reminders for log records.
*   **Logging:**
    *   The system automatically creates log records when objects (projects, wishes, solutions) are created or edited.
    *   Log records include a reminder field to indicate new or unchecked records.

## 14. Known Issues and Workarounds

(This section should be populated with any known issues and their corresponding workarounds.)

## 15. Contact Information

(Provide contact information for the system administrator and support team.)

## 16. Appendix

(Include any relevant appendices, such as configuration files, database schemas, and user manuals.)

**Note:** This document is based on the provided information and may require further details and refinements based on the actual system implementation and deployment environment.  Specifically, the hardware requirements and detailed configuration steps need to be added based on the system architecture and design documents.