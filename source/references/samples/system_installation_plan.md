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

## 1. System Overview

The INTPMIS is a web-based system designed to manage I&T projects, wishes, and solutions within EMSD. It aims to address the limitations of the current system by providing enhanced features for data management, analysis, and workflow. Key features include:

*   **User-friendly Web Portal:** An intuitive web interface for administrators and users to access and modify database entries.
*   **Data Management:** Storage of I&T project information (including E&M InnoPortal projects), wishes, and solutions in a MySQL database. Support for various data types, including text, dates, reports, and attachments (PDF, Microsoft Word, JPEG, PNG, etc.).
*   **Data Analysis:** Generation of reports and statistics to track I&T development trends. Customizable reports with filtering and sorting capabilities. Data export to Excel format.
*   **Workflow Automation:** Automated data retrieval from different tables during project creation, reducing manual data entry and improving accuracy.
*   **Logging:** Comprehensive logging of user actions and system events for auditing and troubleshooting.

## 2. System Requirements

### 2.1 Functional Requirements

The system must fulfill the following functional requirements:

*   **REQ-SYS-001: Login:** Secure user authentication via Windows Active Directory single sign-on. Support for existing user permission matrix mapping. Handling of "Acting" roles based on LDAP login details.
*   **REQ-SYS-002: Project List:** Ability to search, sort, and filter projects. Export project list to CSV format. Configure filtering and sorting criteria. View and edit project details.
*   **REQ-SYS-003: Create a Project:** Functionality to create new projects with required data fields.
*   **REQ-SYS-004: View and Edit a Project:** Support read-only and edit modes based on user permissions and project stage.
*   **REQ-SYS-005: Wish List:** Ability to search, sort, and filter wishes. Export wish list to CSV format. Configure filtering and sorting criteria. View and edit wish details.
*   **REQ-SYS-006: View or Edit a Wish:** Support read-only and edit modes based on user permissions.
*   **REQ-SYS-007: Solution List:** Ability to search, sort, and filter solutions. Export solution list to CSV format. Configure filtering and sorting criteria. View and edit solution details.
*   **REQ-SYS-008: View and Edit a Solution:** Support read-only and edit modes based on user permissions.
*   **REQ-SYS-009: Report List:** Ability to sort and filter reports. Export report list to CSV format. Configure filtering and sorting criteria.
*   **REQ-SYS-010: View Report:** Support read-only mode for report viewing.
*   **REQ-SYS-011: Log List:** Ability to sort and filter logs. Export log list to CSV format. Configure filtering and sorting criteria. View log details.
*   **REQ-SYS-012: View Log List:** Support read-only mode for log viewing.
*   **REQ-SYS-013: Upload Files:** Ability to upload files in various formats (PDF, JPEG, DOCX, XLS). Support file replacement and deletion.

### 2.2 Non-Functional Requirements

The system must meet the following non-functional requirements:

*   **REQ-SR-001: Response Time:** 95% of predefined queries should respond within 5 seconds.
*   **REQ-SR-002: Service Time:** System availability from 08:00 to 20:00 daily (with potential for late-night access). Achieve 99.0% availability (unscheduled downtime not exceeding 7.2 minutes per day or 1.83 days per year).
*   **REQ-SR-003: Export:** Ability to export data in easy-readable formats like Excel.
*   **REQ-SR-004: Scalability:** Provide scalability options for future system expansion.
*   **REQ-SR-005: System Performance:** Technically sound architecture to meet response time and performance levels.
*   **REQ-UR-001: User Interface Requirement:** User-friendly interface consistent with web-based applications. Responsive web design for different screen sizes. Functionality in multiple browsers (Internet Explorer, Chrome).
*   **REQ-SCR-001: Function Access Rights:** Define user access rights based on roles and user levels.
*   **REQ-SCR-002: Access to Data:** Define access rights for users to access specific data, with conditional access and monitoring capabilities.
*   **REQ-SCR-003: System Backup:** Meet general backup requirements for data, system, and audit logging information.

### 2.3 Technical Requirements

The system must adhere to the following technical requirements:

*   **TR-SBR-001: Server House Keeping:** Archive system logs to backup tape weekly.
*   **TR-SBR-002: Backup, Recovery and System Archive:** Daily backup, weekly system backup, two generations of off-site system backup, system activity logs and reports.
*   **TR-DRR-001: System Disaster Recovery:** Participate in disaster recovery activities, coordinate with users, and resume the system from the disaster recovery site.

## 3. Installation Procedures

The installation process involves several key steps:

1.  **Environment Setup:**
    *   Install and configure the necessary operating system, web server, database server (MySQL), and other required software components.
    *   Ensure the server meets the hardware requirements for the system.
2.  **Database Setup:**
    *   Create the MySQL database for INTPMIS.
    *   Import the database schema and initial data.
3.  **Application Deployment:**
    *   Deploy the INTPMIS application files to the web server.
    *   Configure the application to connect to the MySQL database.
4.  **User Authentication Configuration:**
    *   Configure single sign-on integration with Windows Active Directory.
    *   Map existing user permissions to the INTPMIS roles.
5.  **Data Migration:**
    *   Migrate existing I&T project information from other systems and Excel tables to the INTPMIS database.
6.  **Testing:**
    *   Conduct thorough testing of all system functionalities, including login, project management, wish management, solution management, reporting, and logging.
    *   Verify that the system meets the performance and security requirements.
7.  **User Training:**
    *   Provide training courses and user experience sessions for EMSD staff on how to use the INTPMIS.
    *   Develop user manuals, including workflow manuals and user procedures manuals.
8.  **Deployment:**
    *   Deploy the INTPMIS to the production environment.
    *   Monitor the system performance and stability after deployment.

## 4. User Procedures and Operation Manual

The INTPMIS provides different functionalities for various user roles. Key procedures include:

### 4.1 Project Management

*   **Browsing Project List:**
    *   Click "View" under "Project Management" to view the project list.
    *   Use the search function to find specific projects based on criteria like project title, client department, etc.
    *   Use the filter function to narrow down the project list based on input values and display number of records per page.
    *   Click "X" to redirect to the project view page.
*   **Creating a Project:**
    *   Refer to the "Create Project" table in the documentation for required fields and input types.
    *   Note the dependencies between fields (e.g., hiding/showing fields based on selections).
*   **Editing a Project:**
    *   Click "Edit" under "Project Management."
    *   Click the edit icon to modify the project details.
    *   Update information, select completed status, input values, or empty input fields.
    *   Click "Save All" to save the changes.
    *   Handle invalid input errors and successful save messages.
    *   Admin users (Role 6) have access to edit more fields, such as the "Date of Uploading Interim Evaluation Report."

### 4.2 Wish List Management

*   **Browsing Wish List:**
    *   Click "View" under "Wish Management" to view the wish list.
    *   Scroll the bottom bar to view details of the wish.
    *   Use the search function to find specific wishes based on criteria.
    *   Use the filter function to narrow down the wish list.
    *   Export wishes using "Export Records" (searched records) or "Export All Records" (all records).
*   **Editing a Wish:**
    *   Input values to edit the wish details.
    *   Click "Save All" to save the changes.
    *   Handle invalid input errors and successful edit messages.

### 4.3 Solution List Management

*   **Browsing Solution List:**
    *   Click "View" under "Solution Management" to view the solution list.
    *   Scroll the bottom bar to view details of the solution.
    *   Use the search function to find specific solutions based on criteria.
    *   Use the filter function to narrow down the solution list.
    *   Export solutions using "Export Records" (searched records) or "Export All Records" (all records).
*   **Editing a Solution:**
    *   Input values to edit the solution details.
    *   Click "Save All" to save the changes.
    *   Handle invalid input errors and successful edit messages.

### 4.4 Report Management

*   **Browsing Report List:**
    *   View the report list and details.
    *   Use the search function to find specific reports.
*   **Viewing a Report:**
    *   Select a month to automatically assign start and end dates.
    *   Click "Confirm" to display the report data within the selected month.
*   **Printing a Report:**
    *   Click the "Print" button to generate a preview page for printing.

### 4.5 Log Management

*   **Browsing Log List:**
    *   Select the tag type of log (report, wish, solution).
    *   View log records in the list.
    *   Click "+" to view log details.
    *   Export records to a CSV file using "Export Records."
*   **Canceling Reminders:**
    *   Click the checked button to cancel the reminder for a specific record.
    *   Select multiple records and click "Batch Checked" to cancel reminders for selected records.

## 5. Administrator Procedures

Administrators have additional responsibilities, including:

*   **Project Editing:** Access to edit more project fields, such as "Date of Uploading Interim Evaluation Report."
*   **Log Management:** Monitoring and managing log records, canceling reminders, and exporting logs.

## 6. Search and Export Functions

*   **Search Function:** Allows users to search for projects, wishes, or solutions by selecting specific search criteria (fields of the object).
*   **Export Function:** Allows users to export all records after a search to a CSV file.

## 7. Training and Documentation

*   **Training Courses and User Experience Sessions:** Provide training to users on the system's functionalities.
*   **Program Manual:** Includes a workflow manual to guide users through the system's processes.
*   **System Manual:** Provides technical details about the system's architecture and configuration.
*   **User Procedures Manual:** Outlines step-by-step instructions for performing various tasks within the system.

## 8. Logging

The system logs all user actions and system events.  After a user creates or edits an object, the system creates a log record.  Users can check log records and cancel reminders for specific records.

This document provides a comprehensive overview of the INTPMIS installation plan.  Adherence to these procedures will ensure a successful and efficient deployment of the system.