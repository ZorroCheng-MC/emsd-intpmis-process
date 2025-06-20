# SYSTEM INSTALLATION PLAN

**FOR**

**[PROJECT_NAME]**

**OF**

**[DEPARTMENT_NAME]**

**Version: [VERSION]**

**[DATE]**

![Logo](media/image1.jpg)

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

This document also incorporates information from the System/Operation & User Manual and the User Requirement Specification to provide a comprehensive overview of the system.  The system is named **Development of I&T Project Management Information System (INTPMIS)**.

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
# INTPMIS System Overview (From URS)

The proposed INTPMIS will address the problems of the current system.
Thus, the proposed INTPMIS offers a variety of enhanced aspects as
following:

- **Working environment:** An easy-to-use web portal, UI and forms for admin and users to login and modify individual database entries will be developed. Users are allowed to co-editing of database entries simultaneously and in real-time.

- **Data management:** The I&T project's information includes E & M InnoPortal and other I&T projects that will be stored in the MySQL database of INTPMIS. The data includes text ,data ,report and attachment in the form of PDF, Microsoft Word and JPEG, PNG etc. Users can access the data in the INTPMIS web portal. Moreover, it migrates existing I&T project information by interface with other systems and from Excel tables.

- **Data analysis:** The reports and statistics will be generated by the system to show the facts and trend of I&T development. Also, users can customize the reports. Filtering and Sorting record functions will be added to the system. Users can export the data to Excel reports.

- **Workflow:** When creating a new project, users do not need to enter the data manually. The system will automatically get the data from different tables. It avoids data loss and increases accuracy.

# INTPMIS System Architecture (From SM)

![](media/image54.jpg){width="3.78125in" height="4.447916666666667in"}

The proposed INTPMIS is a web-based application which is built using
Node.js, Vue.js, and MySQL. INTPMIS is designed for bridging the
information and collaboration between different users. It interfaces
with the online platform E&M InnoPortal to obtain relevant project

data, such as the wish table, project table, and solution table, stored
in INTPMIS MySQL database. Users are allowed to fill information and
match records via the web user interface which is built by Vue.js. The
key features of the system are record searching, record filtering, and
report generation.

**Selected Technical System Option**

Node.js and MySQL are applied for the backend of the system when the
Vue.js is the frontend of the system.

Node.js is an open source, cross-platform runtime environment for
developing server-side and networking applications. Node.js applications
are written in JavaScript, and can be run within the Node.js runtime on
OS X, Microsoft Windows, and Linux.

Node.js also provides a rich library of various JavaScript modules which
simplifies the development of web applications using Node.js to a great
extent.

MySQL is an open source relational database management system. It is
based on the structure query language (SQL), which is used for adding,
removing, and modifying information in the database.

Vue.js is a library for building interactive web interfaces. The goal of
Vue.js is to provide the benefits of reactive data binding and
composable view components with an API that is as simple as possible.

# INTPMIS Functional Requirements (From URS)

*List of Functional Requirements:*

| N/A |                          | N/A |          | N/A |-------------|--------------------------|--------------|----------| N/A |---|---|---|---| N/A | Req. ID     | Requirement Title        | Target Users | Priority | N/A |---|---|---|---| N/A | REQ-SYS-001 | Login                    | Users        | MUST     | N/A |---|---|---|---| N/A | REQ-SYS-002 | Project List             | Users        | MUST     | N/A |---|---|---|---| N/A | REQ-SYS-003 | Create a Project         | Users        | MUST     | N/A |---|---|---|---| N/A | REQ-SYS-004 | View or Edit a Project   | Users        | MUST     | N/A |---|---|---|---| N/A | REQ-SYS-005 | Wish List                | Users        | MUST     | N/A |---|---|---|---| N/A | REQ-SYS-006 | View or Edit a Wish      | Users        | MUST     | N/A |---|---|---|---| N/A | REQ-SYS-007 | Solution List            | Users        | MUST     | N/A |---|---|---|---| N/A | REQ-SYS-008 | View and Edit a Solution | Users        | MUST     | N/A |---|---|---|---| N/A | REQ-SYS-009 | Report List              | Users        | MUST     | N/A |---|---|---|---| N/A | REQ-SYS-010 | View Report              | Users        | MUST     | N/A |---|---|---|---| N/A | REQ-SYS-011 | Log List                 | Users        | MUST     | N/A |---|---|---|---| N/A | REQ-SYS-012 | View Log List            | Users        | MUST     | N/A |---|---|---|---| N/A | REQ-SYS-013 | Upload File              | Users        | MUST     | N/A |---|---|---|---|
# INTPMIS Non-Functional Requirements (From URS)

*List of Non-Functional Requirements*

| N/A |                              | N/A |                  | N/A |
|-------------|------------------------------|----------------------------|------------------|--------------| N/A |---|---|---|---|---| N/A | **Req. ID** | **Category**                 | **Requirement Title**      | **Target Users** | **Priority** | N/A |---|---|---|---|---| N/A | REQ-SR-001  | System Requirements          | Response Time              | User             | M            | N/A |---|---|---|---|---| N/A | REQ-SR-002  | System Requirements          | Service Time               | User             | M            | N/A |---|---|---|---|---| N/A | REQ-SR-003  | System Requirements          | Export                     | User             | M            | N/A |---|---|---|---|---| N/A | REQ-SR-004  | System Requirements          | Scalability                | User             | M            | N/A |---|---|---|---|---| N/A | REQ-SR-005  | System Requirements          | System Performance         | User             | M            | N/A |---|---|---|---|---| N/A | REQ-UR-001  | User Requirements            | User Interface Requirement | User             | M            | N/A |---|---|---|---|---| N/A | REQ-SCR-001 | System Controls Requirements | Function Access Rights     | User             | M            | N/A |---|---|---|---|---| N/A | REQ-SCR-002 | System Controls Requirements | Access to Data             | User             | M            | N/A |---|---|---|---|---| N/A | REQ-SCR-003 | System Controls Requirements | System Backup              | User             | M            | N/A |---|---|---|---|---|
# INTPMIS Technical Requirements (From URS)

*List of Technical Requirements:*

| N/A |                                     | N/A |                                         | N/A |------------|-------------------------------------|----------|-----------------------------------------| N/A |---|---|---|---| N/A | Req. ID    | Requirement Title                   | Priority | Category                                | N/A |---|---|---|---| N/A | TR-SBR-001 | Server House Keeping                | M        | System Backup and Recovery Requirements | N/A |---|---|---|---| N/A | TR-SBR-002 | Backup, Recovery and System Archive | M        | System Backup and Recovery Requirements | N/A |---|---|---|---| N/A | TR-DRR-001 | System disaster recovery            | M        | Disaster Recovery Requirements          | N/A |---|---|---|---|
# INTPMIS User Interface (From URS & SM)

*Login page*

![](media/image13.png)
![](media/image1.png)

*Project Management- Create*

![](media/image22.jpg)
![](media/image8.png)
![](media/image2.jpg)
![](media/image3.png)
![](media/image4.png)
![](media/image5.png)
![](media/image6.png)
![](media/image7.png)

*Project Management- Edit*

![](media/image29.jpg)
![](media/image26.png)
![](media/image24.png)
![](media/image23.png)
![](media/image8.jpg)
![](media/image9.png)
![](media/image10.png)
![](media/image11.jpg)

*Project Management- View*

![](media/image12.jpg)

*Wish Management- Edit*

![](media/image39.png)
![](media/image24.png)
![](media/image11.png)
![](media/image13.jpg)
![](media/image14.png)

*Wish Management- View*

![](media/image34.jpg)
![](media/image15.jpg)

*Solution Management- Edit*

![](media/image18.png)
![](media/image24.png)
![](media/image27.png)
![](media/image16.jpg)
![](media/image17.png)

*Solution Management- View*

![](media/image32.jpg)
![](media/image18.jpg)

*Report Management- View*

![](media/image56.jpg)
![](media/image45.png)
![](media/image57.png)
![](media/image49.png)
![](media/image50.png)
![](media/image47.png)
![](media/image55.png)
![](media/image4.png)
![](media/image53.png)
![](media/image7.png)
![](media/image16.png)
![](media/image6.png)
![](media/image19.jpg)
![](media/image20.png)
![](media/image21.png)
![](media/image22.png)
![](media/image23.png)

*Log Management- View*

![](media/image19.png)
![](media/image17.png)
![](media/image24.jpg)

# INTPMIS API Integration (From SM)

The system needed to integrate to the InnoPortal CMS by API provided by
InnoPortal CMS side. They were list below:

### Solution import

Post
[[http://intpmis/api/vi/data/import-solution]{.underline}](http://intpmis/api/vi/data/import-solution)

Description : This api allow InnoPortal CMS call to import solution

| Key                        | Type    | Required | N/A |----------------------------|---------|----------| N/A |---|---|---| N/A | **soln_id**                | ?string | ?true    | N/A |---|---|---| N/A | **cms_id**                 | ?string | ?false   | N/A |---|---|---| N/A | **cms_expiry_date**        | ?string | ?false   | N/A |---|---|---| N/A | **soln_title**             | ?string | ?false   | N/A |---|---|---| N/A | **soln_cat_tech**          | ?string | ?false   | N/A |---|---|---| N/A | **soln_cat_app**           | ?string | ?false   | N/A |---|---|---| N/A | **innoportal_upload_date** | ?string | ?false   | N/A |---|---|---| N/A | **int_soln_provider**      | ?string | ?false   | N/A |---|---|---| N/A | **int_soln_provider_type** | ?string | ?false   | N/A |---|---|---| N/A | **is_moc_partner**         | ?string | ?false   | N/A |---|---|---| N/A | **moc_partner**            | ?string | ?false   | N/A |---|---|---| N/A | **geog_location**          | ?string | ?false   | N/A |---|---|---| N/A | **soln_contact_name**      | ?string | ?false   | N/A |---|---|---| N/A | **soln_contact_title**     | ?string | ?false   | N/A |---|---|---| N/A | **soln_contact_tel**       | ?string | ?false   | N/A |---|---|---| N/A | **soln_contact_email**     | ?string | ?false   | N/A |---|---|---| N/A | **soln_contact_address**   | ?string | ?false   | N/A |---|---|---| N/A | **if_targetted_wish**      | ?string | ?false   | N/A |---|---|---| N/A | **target_wish**            | ?string | ?false   | N/A |---|---|---| N/A | **is_iirc**                | ?string | ?false   | N/A |---|---|---| N/A | **iirc_bulletin_no**       | ?string | ?false   | N/A |---|---|---| N/A | **iirc_review_date**       | ?string | ?false   | N/A |---|---|---| N/A | **iirc_endorse_date**      | ?string | ?false   | N/A |---|---|---| N/A | **is_intac**               | ?string | ?false   | N/A |---|---|---| N/A | **intac_review_date**      | ?string | ?false   | N/A |---|---|---| N/A | **intac_endorse_date**     | ?string | ?false   | N/A |---|---|---| N/A | **tech_feasible**          | ?string | ?false   | N/A |---|---|---| N/A | **remarks**                | ?string | ?false   | N/A |---|---|---| N/A | **last_modified_by**       | ?string | ?false   | N/A |---|---|---| N/A | **last_modified_at**       | ?string | ?false   | N/A |---|---|---| N/A | **matched**                | ?string | ?false   | N/A |---|---|---| N/A | **created_by**             | ?string | ?false   | N/A |---|---|---| N/A | **created_at**             | ?string | ?false   | N/A |---|---|---|
Response code :

| Response code | Description             | N/A |---------------|-------------------------| N/A |---|---| N/A | 200           | Import solution success | N/A |---|---| N/A | 400           | Import solution fail    | N/A |---|---|
### Wish import

Post
[[http://intpmis/api/vi/data/import-wish]{.underline}](http://intpmis/api/vi/data/import-wish)

Description : This api allow InnoPortal CMS call to import wish

| Key                              | Type    | Required | N/A |----------------------------------|---------|----------| N/A |---|---|---| N/A | wish_id                          | ?string | ?true    | N/A |---|---|---| N/A | cms_id                           | ?string | ?false   | N/A |---|---|---| N/A | cms_expiry_date                  | ?string | ?false   | N/A |---|---|---| N/A | wish_title                       | ?string | ?false   | N/A |---|---|---| N/A | wish_cat_smart                   | ?string | ?false   | N/A |---|---|---| N/A | wish_cat_tech                    | ?string | ?false   | N/A |---|---|---| N/A | wish_cat_app                     | ?string | ?false   | N/A |---|---|---| N/A | innoportal_upload_date           | ?string | ?false   | N/A |---|---|---| N/A | type_of_organization             | ?string | ?false   | N/A |---|---|---| N/A | wish_client_dept                 | ?string | ?false   | N/A |---|---|---| N/A | proposing_emsd_arm               | ?string | ?false   | N/A |---|---|---| N/A | proposing_emsd_branch            | ?string | ?false   | N/A |---|---|---| N/A | proposing_emsd_div               | ?string | ?false   | N/A |---|---|---| N/A | proposing_emsd_sub_div           | ?string | ?false   | N/A |---|---|---| N/A | support_emsd_div                 | ?string | ?false   | N/A |---|---|---| N/A | wish_emsd_contact_name_eng       | ?string | ?false   | N/A |---|---|---| N/A | wish_emsd_contact_name_chi       | ?string | ?false   | N/A |---|---|---| N/A | wish_emsd_contact_post_short     | ?string | ?false   | N/A |---|---|---| N/A | wish_emsd_contact_post_eng       | ?string | ?false   | N/A |---|---|---| N/A | wish_emsd_contact_post_chi       | ?string | ?false   | N/A |---|---|---| N/A | wish_emsd_contact_email          | ?string | ?false   | N/A |---|---|---| N/A | wish_emsd_contact_tel            | ?string | ?false   | N/A |---|---|---| N/A | is_innoteam                      | ?string | ?false   | N/A |---|---|---| N/A | innoteam_round                   | ?string | ?false   | N/A |---|---|---| N/A | int_challenge_no                 | ?string | ?false   | N/A |---|---|---| N/A | int_challenge_title              | ?string | ?false   | N/A |---|---|---| N/A | is_iirc                          | ?string | ?false   | N/A |---|---|---| N/A | iirc_bulletin_no                 | ?string | ?false   | N/A |---|---|---| N/A | iirc_review_date                 | ?string | ?false   | N/A |---|---|---| N/A | iirc_endorse_date                | ?string | ?false   | N/A |---|---|---| N/A | is_intac                         | ?string | ?false   | N/A |---|---|---| N/A | iirc_deadline                    | ?string | ?false   | N/A |---|---|---| N/A | iirc_soln                        | ?string | ?false   | N/A |---|---|---| N/A | intac_review_date                | ?string | ?false   | N/A |---|---|---| N/A | intac_endorse_date               | ?string | ?false   | N/A |---|---|---| N/A | active_for_proposal              | ?string | ?false   | N/A |---|---|---| N/A | remarks                          | ?string | ?false   | N/A |---|---|---| N/A | last_modified_by                 | ?string | ?false   | N/A |---|---|---| N/A | last_modified_at                 | ?string | ?false   | N/A |---|---|---| N/A | matched                          | ?string | ?false   | N/A |---|---|---| N/A | created_by                       | ?string | ?false   | N/A |---|---|---| N/A | created_at                       | ?string | ?false   | N/A |---|---|---| N/A | wish_emsd_contact_tel_2          | ?string | ?false   | N/A |---|---|---| N/A | wish_emsd_contact_post_title_eng | ?string | ?false   | N/A |---|---|---| N/A | wish_emsd_contact_post_title_chi | ?string | ?false   | N/A |---|---|---|
Response code :

| Response code | Description         | N/A |---------------|---------------------| N/A |---|---| N/A | 200           | Import wish success | N/A |---|---| N/A | 400           | Import wish fail    | N/A |---|---|
<<End of Document>>