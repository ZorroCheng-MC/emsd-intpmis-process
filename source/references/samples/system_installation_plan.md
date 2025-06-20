---
sip_i1.md
---
![BDlogo](media/image1.jpg)

# SYSTEM INSTALLATION PLAN

**FOR**

**COMBINED SYSTEM DEVELOPMENT SERVICES**

**FOR**

**LICENSING SELF-CERTIFICATION PORTAL**

**OF**

**BUILDINGS DEPARTMENT**

**Version: 0.1**

? The Government of the Hong Kong Special Administrative Region
The contents of this document remain the property of and may not be reproduced in whole or in part without the express permission of the Government of the HKSAR.

|-------------|-------------------------------------| N/A |---|---| N/A | Copy No.    | Holder                              | N/A |---|---| N/A | 2           | Master Concept (Hong Kong) Limited (MC) | N/A |---|---| N/A |------------------|------------------------|----------------|------------|-----------|-----------| N/A |---|---|---|---|---|---| N/A | Change Number    | Revision Description   | Pages Affected | Revision / | Date      | Approval  | N/A |                  | N/A | Version        | Number     | N/A |           | N/A |---|---|---|---|---|---| N/A | 1                | 1st draft             | All            | 0.1        | 16/01/225 | N/A |
|---|---|---|---|---|---|
# TABLE OF CONTENTS

[2. Project Environment Description](#project-environment-description)
- [2.2 Hardware Specification](#hardware-specification)
- [2.3 Software Specification](#software-specification)
[3. Application Deployment Procedure for Production](#application-deployment-procedure-for-production)
- [3.1 Database Server](#database-server)
- [3.3 Frontend Servers](#frontend-servers)
  - [3.3.1 sFTP Server Setup](#sftp-server-setup)
[4. System Installation Schedule and Result](#system-installation-schedule-and-result)
- [4.1 System Installation Schedule](#system-installation-schedule)

# Introduction
The System Installation plan describes the procedure and schedule for deploying the application in the production environment, including 3 parts of the system:

- Backend Server
- Frontend and Web Portal Server

# Project Environment Description

Below is a logical network diagram in 1/F West Kowloon Government Office for production and UAT site.
[DIAGRAM HERE]

A two-tier firewall setup will be used to form the trusted zone and DMZ. Incoming network traffic to the system must go through the DMZ before entering the trusted zone.
To utilize hardware resources more effectively, servers listed in section [1.3.3], except the backup server, will be set up in the form of virtual machines (VM) and consolidated into DMZ VM host servers and trusted zone VM host servers for each physical site. Two VM host servers will be built in each zone for the purpose of high availability.

The diagram below illustrates the physical setup.

## Hardware Specification

List of machines and virtual machines:

| Hostname (Physical Machine) | Hostname (Virtual Machine) | Purpose | IP | N/A |---------------------------|---------------------------|---------|-----| N/A |---|---|---|---|
List of machines and virtual machines:

| Hostname (Physical Machine) | Hostname (Virtual Machine) | Purpose | IP | N/A |---------------------------|---------------------------|---------|-----| N/A |---|---|---|---| N/A | Machine | Hostname | Software Requirement | N/A |---|---|---| N/A | vCenter Server | prd-scs-vcenter-01 | vCenter 8.0.3 Build 24322831 | N/A |---|---|---|
Development Frameworks:

|-----------|---------| N/A |---|---| N/A | React (frontend) | 18.2.0 | N/A |---|---|
# Application Deployment Procedure for Production

## Database Server

1. Remote login to PRD-DB-01
3. Install Microsoft SQL Server Management Studio 19.1
4. Configure SQL Server with:
   - Enable TCP/IP protocol
   - Configure firewall to allow SQL Server port (default 1433)
   - Initial size: 100GB
   - Autogrowth: 1GB
6. Configure database backup schedule:
   - Daily incremental backup at 00:00
7. Configure database maintenance plan:
   - Weekly index rebuild
8. Configure database monitoring and alerts:
   - Space usage alerts at 85% and 95%
   - Failed job alerts

1. Remote login into PRD-WEBAPP-01 and PRD-WEBAPP-02
   - Windows Server 2022 updates
   - .NET 6.0 Runtime
3. Install backend application:
   - Deploy API application files to C:\inetpub\wwwroot\lscp-api
     - .NET CLR Version: .NET CLR v4.0
     - Managed Pipeline Mode: Integrated
4. Configure application settings:
   - Update appsettings.json with production values
   - Set up logging paths
5. Configure Windows services:
   - Set up Windows service recovery options
6. Configure SSL certificates:
   - Bind certificate to HTTPS port
7. Configure IIS:
   - Configure URL bindings
   - Set up compression and caching rules

## Frontend Servers

2. Install prerequisites:
   - IIS 10.0.20348.1
   - Application Request Routing
3. Install frontend application:
   - Configure static file caching
   - Set up compression for static files
   - Create website with appropriate bindings
   - Configure SSL certificates
   - Configure CORS if needed
5. Configure monitoring:
   - Configure health check endpoints
   - Set up performance monitoring

### sFTP Server Setup

   - Go to Apps & Features
   - Click "Optional Features"
   - Check "OpenSSH Server"
2. Configure OpenSSH server:
   - Configure authentication methods
   - Set up SFTP chroot directory
   - Allow inbound port 22 (SSH)
   - Restrict access to specific IP ranges
   - Create SFTP users
   - Configure user permissions
5. Configure logging and monitoring:
   - Enable detailed logging
   - Configure alerts for failed login attempts

## System Installation Schedule

The following table summarises the testing schedule:

|---------------|------------|----------|------------|----------| N/A |---|---|---|---|---| N/A | Database Server Installation (Production and DR) | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Frontend Server Installation (Production and DR) | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Functionality test (VM & Networking) | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Deployment for 1st version of frontend server | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Deployment for 1st version of backend server | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Deployment for Latest Mobile Application | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Final Check Production Web Server | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Final Check DR Web & Database server | N/A |  | N/A |  | N/A |---|---|---|---|---| N/A | Final Check IIS & Framework | N/A |  | N/A |  | N/A |---|---|---|---|---|
## System Installation Result

| Pre-Requisite | Actual Start Date | Actual End Date | Actual Start time | Actual End Time | Status/Result | N/A |---|---|---|---|---|---| N/A | Database Server Installation (Production, UAT and DR) | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Backend Server Installation (Production, UAT and DR) | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Functionality test (VM & Networking) | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Database setup | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Deployment for 1st version of backend server | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Application Health Check | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Final Check Production Web Server | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Final Check Production Database Server | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---| N/A | Final Check IIS & Framework | N/A |  | N/A |  | N/A |
|---|---|---|---|---|---|
---
sm_i1.md
---

reproduced in whole or in part without the express permission of the

|-------------|------------------------------| N/A |---|---| N/A | Copy No.    | Holder                       | N/A |---|---| N/A | 2           | Master Concept (Hong Kong) Limited (MC) | N/A |---|---| N/A |----------|------------------------------|-------------|----------|------------| N/A |---|---|---|---|---| N/A | Change Number     | Revision Description | Revision / Version Number | Date       | N/A |---|---|---|---| N/A | 2                 | 2nd draft | 0.2                       | 19/11/2024 | N/A |---|---|---|---|
# TABLE OF CONTENTS

[5. System Overview](#system-overview)
- [5.2 System Architecture](#system-architecture)
[6. System Environment](#system-environment)
- [6.1 Computer Hardware](#computer-hardware)
  - [6.1.4 Database Configuration](#database-configuration)
[8. Security Considerations](#security-considerations)
- [8.6 Database Backup Strategy](#database-backup-strategy)
[9. Database Administration](#database-administration)

# 1. Purpose
The objective of this document is to provide an overview of the system procedure, computer operation procedure, etc.

# 4. Reference and Convention
## 4.1 Definitions
None.
## 4.2 Conventions
The following acronyms are used in the text of this document:
|Abbreviation|Description| N/A |---|---| N/A |---|---| N/A |BD|Buildings Department| N/A |---|---| N/A |LSCP|Licensing Self-Certification Portal| N/A |---|---| N/A |DMZ|Demilitarized Zone| N/A |---|---| N/A |SAN|Storage Area Network| N/A |---|---| N/A |VM|Virtual Machine| N/A |---|---| N/A |ITU|Information Technology Unit| N/A |---|---| N/A |WKGO|West Kowloon Government Offices| N/A |---|---|
# 5. System Overview
## 5.1 Objective
The users of the LSCP can be classified into two categories:
- BD Officers
- Public users involved in site inspection and site monitoring

The primary objective of LSCP is to provide an electronic platform for review the inspection and monitoring records.

## 5.2 System Architecture
This is an overview of the system structure of LSCP in the Production site and UAT site in another perspective.

The system is holding on two datacenters: On-premise (WKGO) and separate into 3 subnets. There are Production, UAT and DEV for internal increased security and share the incoming requests to the frontend web Trusted Zone and Gnet DMZ (gDMZ).

Both iDMZ and gDMZ contain a reverse proxy server and a Web Application access. External users (i.e. public users) access the system from the internet the Application Server through the reverse proxy server. The Application requests to the Web Servers in the Trusted Zone. The web application, written in nodeJS that in turns perform CRUD on the Database Servers, perform logic computing, and return result to the External Web Servers internal BDSCS application from BD intranet, would connect to the BD Web BD Web Servers perform the same function as the External Web Servers and Departmental Portal. Finally, there are some more servers in the Trusted Zone to support servers

- File Server to store the temporary and permanent files
- Database Server that hosts Microsoft SQL server to store all the servers
- Backup Server to keep snapshots of the database

Below are further details of each of the system components in the BDSCS:
External Application Server
The external application servers serve the static web contents in form Internet Information Services (IIS), and also proxy the backend APIs under the React framework. After compiling the JavaScript project, the with rewrite rules to proxy the backend APIs.

External Web Server
The external web server, in this context, refers to a server that hosts performing database operations. In the case of IIS (Internet Information ExpressJS represents the framework used for developing the backend handles various tasks, including interacting with databases, executing intermediary between the frontend (such as a mobile or web application) receives the request and passes it to the appropriate ExpressJS code for which may involve querying the database, executing business rules, or API generates a response that is sent back to the client application

It is using the same technology stack as Extra Application Server but internal BD users only

Database Management Servers
Both the internal and external BDSCS applications are built on the primarily on providing a secure and convenient login mechanism and Smart authentication module. Users can utilize iAM Smart to log in to their digital identity.

Departmental Portal
The Departmental Portal is a web service of BD to pass BD user?s LSCP website through the Departmental Portal, the user ID will be from the user. This login method only available inside BD?s network.

SMTPX
The notification module in BDSCS would send login one-time password CIS.

MWMS
MWMS would provide data of AP/RSE/RGE/AS acknowledged by BD. Snapshots internal and external BDSCS applications would intake this data by latest copy of the BCIS database would be synced to BDSCS through SQL internal portals for address selection, folio management, and case through a SQL stored procedure.

This is an overview of the system structure of Pilot CDPSS in Disaster

|---------------|---------------------------------------------------------| N/A |---|---| N/A | UF-WEB-001-1  | Public User Authentication with Password                | N/A |---|---| N/A | UF-WEB-001-3  | Single User Session                                     | N/A |---|---| N/A | UF-WEB-001-5  | Public User Authentication with iAM Smart               | N/A |---|---| N/A | UF-WEB-001-7  | Change Password                                         | N/A |---|---| N/A | UF-WEB-001-9  | User Account Confirmation                               | N/A |---|---| N/A | UF-WEB-001-11 | User Account Detail Management                          | N/A |---|---| N/A | UF-WEB-001-13 | Public User Accounts Management                         | N/A |---|---| N/A | UF-WEB-001-15 | Public User Account Password Policy                     | N/A |---|---| N/A | UF-WEB-002-2  | Request TCP acceptance                                  | N/A |---|---| N/A | UF-WEB-002-4  | Unassign TCPs                                           | N/A |---|---| N/A | UF-WEB-002-6  | Temporary replacement of TCP                            | N/A |---|---| N/A | UF-WEB-002-8  | Notification of Head of Stream resignation              | N/A |---|---| N/A | UF-WEB-003-2  | Listing out responsible Site-Monitoring Schemes         | N/A |---|---| N/A | UF-WEB-004-2  | Search responsible Site Project                         | N/A |---|---| N/A | UF-WEB-004-4  | Edit and update Site Project Detail                     | N/A |---|---| N/A | UF-WEB-004-6  | View Site Project Detail                                | N/A |---|---| N/A | UF-WEB-004-8  | Supervision Plan Detail Management                      | N/A |---|---|
# 6. System Environment
## 6.1 Computer Hardware
### Hardware Components
The Configuration of Physical Server in Production
| N/A |                         | N/A |                | N/A |
|---|---|---|---|---| N/A | **Model**                  | **Host Name**           | **IP**                      | **Serial No.** | **Disk Configuration** | N/A |---|---|---|---|---| N/A | Dell PowerEdge R750 Server | prd-scs-admin-server-02 | 192.168.10.23, 10.5.161.207 | D646RX3        | RAID-5                 | N/A |---|---|---|---|---| N/A |----------------|---------------|--------------|--------------|---------------| N/A |---|---|---|---|---| N/A | SAN Switch  | Dell DS6610B         | FRC1924T0CC    | N/A                   | 192.168.10.16                                              | N/A |---|---|---|---|---| N/A | SAN Storage | Dell PowerStore 500T | HV1NBX3        | 11                    | 192.168.10.26, 192.168.10.27, 192.168.10.28, 192.168.10.29 | N/A |---|---|---|---|---|
The Configuration of Backup storage in Production
| **Type**         | **Model**            | **Serial No.** | **Volume Size** | **IP Address** | N/A |---|---|---|---|---| N/A | Backup Appliance | Dell DataDomain 3300 | 17XMBX3        | 15TB            | 192.168.10.20  | N/A |---|---|---|---|---|
The Configuration of Tape Library in Production
| **Type**     | **Model** | **Serial No.** | **No. of slots** | **IP Address** | N/A |---|---|---|---|---| N/A | Tape Library | Dell ML3  | 3555L3A7801YY0 | 35               | 192.168.10.20  | N/A |---|---|---|---|---|
The Configuration of Firewalls in Production
| N/A |                 | N/A |                  | N/A |
|---|---|---|---|---| N/A | **Host Name** | **Internal IP** | **External IP** | **Model**        | **Serial No.** | N/A |---|---|---|---|---| N/A | PA-850-SCSSec | 192.168.10.13   | 10.5.161.220    | Palo Alto PA-850 | 11901063049    | N/A |---|---|---|---|---|
The Configuration of switches in Production
| **Host Name** | **Internal IP** | **Model** | **Serial No.** | N/A |               | 192.168.10.14   | Catalyst  | N/A |
|---|---|---|---| N/A |------------|----------------| N/A |---|---| N/A | Cyber View | N/A |
|---|---|
The Configuration of UPS in Production
| N/A |                      | N/A |
|---|---|---| N/A | **Model**                  | **Serial No.**       | **IP Address** | N/A |---|---|---| N/A | Vertiv? Liebert? GXT5 3000 | 2102311887222A010004 | 192.168.11.21  | N/A |---|---|---|
Hardware Components of Production Servers
|Hardware Component|Qty| N/A |---|---| N/A |---|---| N/A |ESXi Hypervisor Server|2| N/A |---|---| N/A |Dell PowerEdge R750|1| N/A |---|---| N/A |Intel(R) Xeon(R) Gold 6326 CPU @ 2.90GHz|1| N/A |---|---| N/A |32GB DDR4 Synchronous Registered (Buffered)|8| N/A |---|---| N/A |1.2TB SAS HDD|3| N/A |---|---| N/A |ESXi 8.0.3|1| N/A |---|---| N/A |NAS|4| N/A |---|---| N/A |Dell PowerEdge R750|1| N/A |---|---| N/A |SAN Switch|6| N/A |---|---| N/A |Dell DS6610B|1| N/A |---|---| N/A |SAN Storage|6| N/A |---|---| N/A |Dell PowerStore 500T|1| N/A |---|---| N/A |Backup Appliance|8| N/A |---|---| N/A |Dell DataDomain DD3300|1| N/A |---|---| N/A |Tape Library|9| N/A |---|---| N/A |DELL ML3|1| N/A |---|---| N/A |Firewall|11| N/A |---|---| N/A |Palo Alto PA 850|1| N/A |---|---| N/A |Switch|11| N/A |---|---| N/A |Cisco ???|1| N/A |---|---| N/A |KVM|13| N/A |---|---| N/A |CyberView|1| N/A |---|---| N/A |UPS|13| N/A |---|---| N/A |Vertiv? Liebert? GXT5 3000|1| N/A |---|---|
Partition Configuration of Production Servers
| **Host Name**           | **Drive**       | **Capacity** | **Description**              | N/A |---|---|---|---| N/A | prd-scs-admin-server-01 | local           | 2.4TB        | VMware?ESXi Operating system | N/A |---|---|---|---| N/A | PS500T-Cluster1         | VM_Volume01     | 20TB         | Shared pool of storage space | N/A |---|---|---|---|
The Configuration of Physical Server in DR Site
|---------------|-------------|----------------|---------------|--------------| N/A |---|---|---|---|---| N/A | Dell PowerEdge R750Server | dr-scs-admin-server-01 | 192.168.20.17, 10.5.174.216 | G646RX3        | RAID-5                 | N/A |---|---|---|---|---| N/A |----------------|---------------|--------------|--------------|---------------| N/A |---|---|---|---|---| N/A | SAN Switch  | Dell DS6610B         | FRC1924T0CE    | N/A                   | 192.168.20.14                                              | N/A |---|---|---|---|---| N/A |----------------|---------------|--------------|--------------|---------------| N/A |---|---|---|---|---| N/A |---------------|-------------|-------------|----------------|-----------------| N/A |---|---|---|---|---| N/A | PA-850-SCSDR  | 192.168.20.12   | 10.5.174.215    | Palo Alto PA-850 | 011901063069   | N/A |---|---|---|---|---|
The Configuration of Switches in DR Site
| N/A |                 | N/A |                | N/A |---|---|---|---| N/A | **Host Name** | **Internal IP** | **Model**    | **Serial No.** | N/A |---|---|---|---| N/A |----------------------------|----------------------|----------------| N/A |---|---|---| N/A | Vertiv? Liebert? GXT5 3000 | 2102311887222A01000A | 192.168.20.11  | N/A |---|---|---|
Hardware Components of Disaster Recovery Servers
|Hardware Component|Qty| N/A |---|---| N/A |---|---| N/A |ESXi Hypervisor Server|2| N/A |---|---| N/A |Dell PowerEdge R750|1| N/A |---|---| N/A |Intel(R) Xeon(R) Gold 6326 CPU @ 2.90GHz|1| N/A |---|---| N/A |32GB DDR4 Synchronous Registered (Buffered)|8| N/A |---|---| N/A |1.2TB SAS HDD|3| N/A |---|---| N/A |ESXi 8.0.3|1| N/A |---|---| N/A |SAN Switch|4| N/A |---|---| N/A |Dell DS6610B|1| N/A |---|---| N/A |SAN Storage|4| N/A |---|---| N/A |3.8TB NVME SSD|1| N/A |---|---| N/A |Firewall|5| N/A |---|---| N/A |Palo Alto PA 850|1| N/A |---|---| N/A |KVM|7| N/A |---|---| N/A |UPS|7| N/A |---|---| N/A |Vertiv? Liebert? GXT5 3000|1| N/A |---|---|
Partition Configuration of DR Servers
| N/A |             | N/A |                              | N/A |---|---|---|---| N/A | **Host Name**          | **Drive**   | **Capacity** | **Description**              | N/A |---|---|---|---| N/A | PS500T-Cluster2        | VM Volume01 | 20TB         | Shared pool of storage space | N/A |---|---|---|---|
### Guest Servers Components

Production guest servers
|Host Name|RAM|Disk|IP Addresses|Host Server / Zone| N/A |---|---|---|---|---| N/A |---|---|---|---|---| N/A |prd-scs-backup-01|16|1.33TB|10.5.161.210|prd-scs-admin-server-01| N/A |---|---|---|---|---| N/A |prd-scs-api-01|4|100+|192.168.12.11|prd-scs-admin-server-01| N/A |---|---|---|---|---| N/A |prd-scs-frontend-01|4|100+|192.168.12.12|prd-scs-admin-server-01| N/A |---|---|---|---|---| N/A |prd-scs-backend-01|4|100+|192.168.12.13|prd-scs-admin-server-01| N/A |---|---|---|---|---| N/A |prd-scs-db-02|16|500|192.168.12.14|prd-scs-admin-server-02| N/A |---|---|---|---|---| N/A |scspwi|8|100+|192.168.0.6|GCIS iDMZ| N/A |---|---|---|---|---| N/A |scspwg|8|100+|192.168.4.6|GCIS gDMZ| N/A |---|---|---|---|---| N/A |scspdb|16|200|192.168.8.7|GCIS Trust Zone| N/A |---|---|---|---|---| N/A |scspbk2|16|1TB|192.168.8.7|GCIS Trust Zone| N/A |---|---|---|---|---|
UAT guest servers
|Host Name|RAM|Disk|IP Addresses|Host Server / Zone| N/A |---|---|---|---|---| N/A |---|---|---|---|---| N/A |uat-scs-db-01|4|100+|192.168.13.13|prd-scs-admin-server-01| N/A |---|---|---|---|---| N/A |uat-scs-proxy|2|100|10.5.161.224|prd-scs-admin-server-01| N/A |---|---|---|---|---| N/A |scsuwi|8|100+|192.168.0.7|GCIS iDMZ| N/A |---|---|---|---|---| N/A |scsuwg|8|100+|192.168.4.7|GCIS gDMZ| N/A |---|---|---|---|---| N/A |scsudb|16|100|192.168.8.10|GCIS Trust Zone| N/A |---|---|---|---|---|
Dev guest servers
|Role|vCPU|RAM|Disk|IP Addresses|Data Center| N/A |---|---|---|---|---|---| N/A |---|---|---|---|---|---| N/A |dev-scs-api-01|4|100+|192.168.14.10|prd-scs-admin-server-01|WKGO| N/A |---|---|---|---|---|---| N/A |dev-scs-frontend-01|4|100+|192.168.14.11|prd-scs-admin-server-01|WKGO| N/A |---|---|---|---|---|---| N/A |dev-scs-backend-01|4|100+|192.168.14.12|prd-scs-admin-server-01|WKGO| N/A |---|---|---|---|---|---| N/A |scsdad|16|200|192.168.8.8|GCIS Trust Zone| N/A |---|---|---|---|---|
Disaster Recovery guest servers
|Host Name|RAM|Disk|IP Addresses|Host Server / Zone| N/A |---|---|---|---|---| N/A |---|---|---|---|---| N/A |dr-scs-backup-01|16|1.33TB|10.5.174.225|dr-scs-admin-server-01| N/A |---|---|---|---|---| N/A |dr-scs-api-01|8|100+|192.168.22.11|dr-scs-admin-server-01| N/A |---|---|---|---|---| N/A |dr-scs-frontend-01|8|100+|192.168.22.12|dr-scs-admin-server-01| N/A |---|---|---|---|---| N/A |dr-scs-backend-01|8|100+|192.168.22.13|dr-scs-admin-server-01| N/A |---|---|---|---|---| N/A |scspwi|8|100+|192.168.0.6|GCIS iDMZ| N/A |---|---|---|---|---| N/A |scspwg|8|100+|192.168.4.6|GCIS gDMZ| N/A |---|---|---|---|---| N/A |scspdb|16|200|192.168.8.7|GCIS Trust Zone| N/A |---|---|---|---|---| N/A |scspbk2|16|1TB|192.168.8.7|GCIS Trust Zone| N/A |---|---|---|---|---|
### Gateway and SMTPX Configuration

SMTPX
|Item|Value| N/A |---|---| N/A |---|---| N/A |SMTPX Hostname|smtpx.cis.hksarg| N/A |---|---| N/A |IP Addresses|10.106.5.103, 10.106.105.103| N/A |---|---| N/A |Port|587| N/A |---|---| N/A |Allowed IP Ranges|(B/Ds' IP address within GNET)| N/A |---|---| N/A |Authentication|By e-Certificate issued from Hong Kong Post or the Government| N/A |---|---| N/A |Connection encryption|TLS| N/A |---|---|
WKGO Production Network Gateway
|Gateway|Subnet|IP Range|vlan / Zone| N/A |---|---|---|---| N/A |---|---|---|---| N/A |192.168.11.1|255.255.255.0|192.168.11.1-254|Replication / Backup| N/A |---|---|---|---| N/A |192.168.13.1|255.255.255.0|192.168.13.1-254|UAT| N/A |---|---|---|---| N/A |10.5.161.1|255.255.255.0|10.5.161.205-235|BD Network| N/A |---|---|---|---|
AIA DR Network Gateway
|Gateway|Subnet|IP Range|vlan / Zone| N/A |---|---|---|---| N/A |---|---|---|---| N/A |192.168.21.1|255.255.255.0|192.168.21.1-254|Replication / Backup| N/A |---|---|---|---| N/A |10.5.174.1|255.255.255.0|10.5.174.215-234|BD Network| N/A |---|---|---|---|
### Database Configuration

WKGO Production:
- prd-scs-db-01 192.168.12.14 (Primary)
- prd-scs-db-02 192.168.12.19 (Secondary)
WKGO UAT:
- uat-scs-db-01 192.168.13.13
WKGO DEV:
- dev-scs-db-01 192.168.14.13
AIA DR:
- dr-scs-db-01 192.168.22.14
GCIS P1:
- scspdb 192.168.8.7
GCIS UAT:
- scsudb 192.168.8.10
GCIS DEV:
- scsddb 192.168.8.8
GCIS P2 DR:
- scspdb 192.168.8.7

# 8. Security Considerations
## 8.6 Database Backup Strategy
### 8.6.1 SQL Database Backup
### 8.6.2 Recovery
### 8.6.3 Backup Schedule

# 9. Database Administration
```

Okay, I'll summarize the information about the network and security components based on the provided documents.

**1. External Firewall**

*   **BD CDPSS - Prod Installation & Operation Manual (network) v1.0 Section 1:**  This section should contain the details of the external firewall configuration.  You'll need to refer to the document itself to get the specifics.
*   **BD - VM & Network Upgrade for CDPSS Site Infra Configuration Information - 20230427_v0.1:**  This document (specifically the "Prod - FW port" and "Prod - FW VIP policy" tabs) will contain the specific port and VIP policy configurations for the Production external firewall.  The "DR - FW port" and "DR - FW VIP policy" tabs will contain the same information for the Disaster Recovery environment.  You'll need to consult the spreadsheet to get the exact details.

**2. Internal Firewall**

*   **BD CDPSS - Prod Installation & Operation Manual (network) v1.0 Section 2:** This section should contain the details of the internal firewall configuration. You'll need to refer to the document itself to get the specifics.
*   **BD - VM & Network Upgrade for CDPSS Site Infra Configuration Information - 20230427_v0.1:** This document (specifically the "Prod - FW port" and "Prod - FW VIP policy" tabs) will contain the specific port and VIP policy configurations for the Production internal firewall. The "DR - FW port" and "DR - FW VIP policy" tabs will contain the same information for the Disaster Recovery environment. You'll need to consult the spreadsheet to get the exact details.

**3. Windows NLB**

*   **BD CDPSS - Prod Installation & Operation Manual (network) v1.0 Section 3:**  This section should contain the details of the Windows Network Load Balancer configuration. You'll need to refer to the document itself to get the specifics.

**4. Switches - Prod DMZ Port**

*   The provided image shows a diagram of the Prod DMZ switch port configuration.  You'll need to visually inspect the diagram to understand the port assignments and connections.

**5. Switches - Prod INT SW Port**

*   The provided image shows a diagram of the Prod Internal switch port configuration.  You'll need to visually inspect the diagram to understand the port assignments and connections.

**6. Switches ? DR DMZ SW Port**

*   The provided image shows a diagram of the DR DMZ switch port configuration.  You'll need to visually inspect the diagram to understand the port assignments and connections.

**7. Switches ? DR INT SW Port**

*   The provided image shows a diagram of the DR Internal switch port configuration.  You'll need to visually inspect the diagram to understand the port assignments and connections.

**8. Security and Backup (From the "BD CDPSS - Prod Installation & Operation Manual (network) v1.0" document)**

*   **System Control:**  Authentication is primarily through OSDP for BD staff.  If OSDP is unavailable, the LSCP authenticates users with username/password + one-time password. External users are authenticated by OTP sent via email. Password complexity follows the latest IT Security Guidelines.
*   **Backup:**
    *   Production, UAT, and DEV environments on WKGO and DR on AIA are backed up by dedicated backup servers.
    *   Daily VM image backups are stored in backup storage, weekly to tape, and daily copies to AIA.
    *   Database servers perform local database backups, which are then backed up by the backup server and copied to AIA.
    *   Production environments on GCIS P1 are backed up by GCIS-provided backup services with offsite copies and replication to DR GCIS P2.
    *   UAT and DEV environments on GCIS are backed up by GCIS-provided backup services.
*   **Security:**
    *   The system conforms to security policies, guidelines, and regulations set by the Buildings Department and DPO.
    *   **Data Transmission Security:** Data is classified as "Restricted" and transmitted over HTTPS/TLS. Certificates are used (OGCIO's ISCCA for internal, HK Post for public-facing, self-generated for availability groups, and iAM Smart certs).
    *   **Data Storage and Auditing Security:** Production data is stored in SAN storage, DR data in local server storage. Both use RAID mirroring. All data is encrypted and has audit trails.
    *   **System Security:** Regular service pack and patch updates are performed. All servers have antivirus clients managed by a virtualized Antivirus Management server.
    *   **Physical Security:** Servers are located in server rooms compliant with IT Security Guidelines and Data Centre Site Preparation Guidelines.
    *   **Password and Group Control:** Password control is in place (DP for BD users, OTP via Authenticator for internet access, OTP via email for public users, iAM Smart app login). User access is limited by user group assignments.
    *   **Control Procedure of Application User Account and Production Support Account:** New users must register. External users use OTP for secure login. Application Maintenance Team requires System Maintenance Committee approval for production server access, with ITU monitoring.
*   **Change Control:** Program source is maintained by the Application Maintenance Team using GIT repository with version control.
*   **Disaster Recovery:**
    *   **GCIS:** Automatic failover to GCIS Prod 2 using VM Site Recovery Manager. Daily database backups to the backup server.
    *   **BDSCS External (On-Prem):** NGINX reverse proxy/load balancer. Scheduled database backup. VM replication to DR environment using VEEAM.
*   **Database Backup Strategy:**
    *   Daily full export backup of the database is performed.
    *   Recovery procedures are outlined for various failure scenarios.
    *   Backup schedules are provided.

**9. Log Management**

*   The document outlines the activities that should be logged (login attempts, unauthorized access, etc.).
*   Logs are retained for 180 days and managed by a Syslog server.
*   Logs are reviewed regularly.
*   Logs are not used to profile users unless related to a necessary audit activity.

**Important Considerations:**

*   **Consult the Documents:** This summary is based on the provided text. You *must* refer to the actual documents (especially the spreadsheet) for the complete and accurate configuration details.
*   **Diagrams:** The switch port diagrams are crucial for understanding the network topology.
*   **Security Policies:** Ensure all configurations adhere to the organization's security policies and best practices.
*   **Testing:**  Thoroughly test all configurations, especially failover and disaster recovery procedures.

This should give you a good starting point for understanding the network and security setup. Remember to consult the original documents for the definitive information.


Okay, I've analyzed the provided text and extracted the following information. This is a structured summary of the requirements for the Self-Certification System (SCS) project.

**I. Functional Requirements Summary**

This section summarizes the key functional requirements, grouped by category.

*   **General Requirements (REQ-GR):**
    *   **REQ-GR-07:** Single Sign-On (SSO) for BD, EDB, and SWD users via their respective OSDPs.
    *   **REQ-GR-08:** Preview uploaded documents (PDF, JPEG, PNG, TIFF).
    *   **REQ-GR-09:** Print documents (application forms, plans, reports, letters, certificates, etc.) for BD users.
    *   **REQ-GR-10:** Upload documents with virus scanning.  PDF plans must be flattened, digitally signed (Hong Kong Post or iAM Smart), and within size limits.
    *   **REQ-GR-11:** Generate management statistics and reports (received, replied, outstanding, overdue, audit cases, submission types, PTS cases, performance reports).
    *   **REQ-GR-12:** e-Submission capabilities, including mobile-friendliness, field validations, conditional display, form pre-filling (iAM Smart), digital signatures (iAM Smart, HK Post, Digi-Sign), saving drafts, photo compression, version control, attachment handling, PDF generation, Excel template preparation, data encryption, and saving draft applications in GCIS for two weeks.
    *   **REQ-GR-13:** e-Processing of applications via workflows.
    *   **REQ-GR-14:** e-Tracking of applications.
    *   **REQ-GR-15:** Centralized data repository for applications and supporting documents.
    *   **REQ-GR-16:** Search and Capture functionality.
    *   **REQ-GR-17:** Handle new applications.
    *   **REQ-GR-18:** Handle alteration applications.
    *   **REQ-GR-19:** Handle Self-Certification Submissions.
    *   **REQ-GR-20:** Handle Periodic Inspections for CCC.
    *   **REQ-GR-21:** Handle PTS for TPPE.
    *   **REQ-GR-22:** Data repository.
    *   **REQ-GR-23:** Easy retrieval of records.
    *   **REQ-GR-24:** User and Delegation Administration.
    *   **REQ-GR-25:** Generate Application Number.
    *   **REQ-GR-26:** Withdraw Application.

*   **Workflow Requirements (REQ-WR):**
    *   **REQ-WR-01:** Input application data (Registry), including structural address with autocomplete.
    *   **REQ-WR-02:** Create Structural Information Report (TO).
    *   **REQ-WR-03:** Provide Comment via SSE.
    *   **REQ-WR-04:** Perform Site Inspection (SO), record data, retrieve plans from BRAVO, prepare inspection report, annotate PDF plans, and upload site photos.
    *   **REQ-WR-05:** Building Safety Requirements Check (BS) using the 3-tier BSR system.
    *   **REQ-WR-06:** Generate Reply Letter, e-Certificates, and e-Notices (BS/SBS), digitally signed.
    *   **REQ-WR-07:** Generate Letter of Requirement (LoR) (BS/SBS).
    *   **REQ-WR-08:** Endorse Application (SBS).
    *   **REQ-WR-09:** Endorse Objection (CBS).
    *   **REQ-WR-10:** AP/RSE Verification against MWMS 2.0 data (name, registration number/status, HKID, expiry date, signature).
    *   **REQ-WR-11:** Check Essential Documents (SO/BS).
    *   **REQ-WR-12:** Digital Signing of documents (Applicant/AP/RSE using Hong Kong Post e-cert or iAM Smart+; BD using BD certificate).
    *   **REQ-WR-13:** Random Audit Check (BS, 60% probability, configurable).
    *   **REQ-WR-14:** Outstanding Application Alert (email notification to officers).
    *   **REQ-WR-15:** Input Application Form.
    *   **REQ-WR-16:** Input memo data.
    *   **REQ-WR-17:** Search Case Information.

*   **Form Requirements (REQ-FRM):**
    *   **REQ-FRM-1:** Verify certificate against the copy from Hong Kong Post and DigiSign.
    *   **REQ-FRM-2:** Route form to corresponding user.
    *   **REQ-FRM-3:** Encrypt restricted data in the form.
    *   **REQ-FRM-4:** Submit public form via online.
    *   **REQ-FRM-5:** Extract data from form.
    *   **REQ-FRM-6:** Store the extracted data in the database.
    *   **REQ-FRM-7:** Search function for all record.
    *   **REQ-FRM-8:** Auto-reply to acknowledge receiving the form.
    *   **REQ-FRM-9:** Maintenance function of the form.
    *   **REQ-FRM-10:** Resubmit the form data.
    *   **REQ-FRM-11:** Update of the disclaimer of the forms.
    *   **REQ-FRM-12:** Handle eform and Hardcopy form.

*   **Form Processing Requirements (REQ-PRO):**
    *   **REQ-PRO-1:** Verify CRM certification record.
    *   **REQ-PRO-2:** Reassign Case to other officer.
    *   **REQ-PRO-3:** Form status query.
    *   **REQ-PRO-4:** Automatically Bring up Outstanding Cases.
    *   **REQ-PRO-5:** To Do List.
    *   **REQ-PRO-6:** Case History Summary.
    *   **REQ-PRO-7:** Mark Notes and remark for internal use.
    *   **REQ-PRO-8:** Re-direct to BCIS for case checking.
    *   **REQ-PRO-9:** Handle upload soft-copy.
    *   **REQ-PRO-10:** Export outstanding case.
    *   **REQ-PRO-11:** Handle referral Case.

**II. Non-Functional Requirements Summary**

*   **Communication Requirements (REQ-CR):**
    *   **REQ-CR-01:** SMS Alerts (form submission acknowledgement, LoR notification, Certificate/Notice notification).
    *   **REQ-CR-02:** Email Notifications (same as SMS, plus reminder for outstanding audit cases).
    *   **REQ-CR-03:** Fax Copy of LoR, Certificates, and Notice.

*   **Webpage Requirements (REQ-UR):**
    *   **REQ-UR-01:** Common Look & Feel (CLF) compliance, mobile-friendly, responsive design, HTML5 standard.
    *   **REQ-UR-02:** W3C WCAG 2.1 Level AA compliance (code scanning, visual review, assistive technology testing, human testing).
    *   **REQ-UR-03:** Privacy Disclaimer.
    *   **REQ-UR-04:** Assistive Technology Testing.

*   **Security Requirements (REQ-SR):**
    *   **REQ-SR-01:** Security Risk Assessment Audit (SRAA).
    *   **REQ-SR-02:** Privacy Impact Assessment (PIA) and Privacy Compliance Audit (PCA).
    *   **REQ-SR-03:** Encryption and Decryption of Classified Data (AES 256bit or SHA-256).
    *   **REQ-SR-04:** System Audit (logging important events).
    *   **REQ-SR-05:** System Control.

*   **Interface Requirements (REQ-IR):**
    *   **REQ-IR-01:** Interface with BCIS.
    *   **REQ-IR-02:** Interface with BD Website.
    *   **REQ-IR-03:** Interface with Minor Works.
    *   **REQ-IR-04:** Interface with ESH.
    *   **REQ-IR-05:** Interface with ERKS.
    *   **REQ-IR-06:** Interface with BRAVO.

**III. Key Observations and Potential Questions**

*   **Heavy Reliance on e-Submission:** The system heavily favors e-submission, with many requirements focused on digital signatures, document uploads, and online forms.
*   **Integration is Crucial:**  The system needs to integrate with several external systems (BCIS, BD Website, Minor Works, ESH, ERKS, BRAVO, MWMS 2.0).  The success of the project depends on the smooth and reliable operation of these interfaces.
*   **Security and Privacy are Paramount:**  The requirements emphasize security and privacy, with SRAA, PIA, PCA, and encryption of classified data.
*   **Accessibility is Important:**  The system must be accessible to users with disabilities, complying with W3C WCAG 2.1 Level AA.
*   **Workflow Automation:** The system aims to automate many processes through workflows, requiring careful design and implementation.

This summary should provide a good overview of the requirements for the SCS project. Let me know if you have any specific questions or need further clarification on any of these points.


# System Installation Plan - SCS (Simplified Case System)

This document outlines the system installation plan for the Simplified Case System (SCS), encompassing functional, technical, and security requirements, along with constraints and appendices for reference.

## 1. Introduction

This document details the requirements, constraints, and technical specifications for the installation of the Simplified Case System (SCS). SCS aims to streamline case management processes and integrate with various external systems.

## 2. Functional Requirements

### 2.1. REQ-SR-05 System Control

*   **Priority:** High
*   **Description:** Security controls for system access using Firewall, network control, physical access control, etc.
*   **Frequency of Use:** Ad-hoc

### 2.2. Interface Requirements

*   All interface requirements are considered **High** priority and used **Ad-hoc**.

    *   **REQ-IR-01 Interface with BCIS (Building Control Information System)**
        *   Receive master data from BCIS for case creation.
        *   Send application data to BCIS for case creation (batch, using stored procedures).
        *   Update application data in BCIS (using stored procedures).
        *   Provide a reference link between SCS and BCIS.
        *   Transfer data from SCS to BCIS for statistical reporting.
        *   Select block for new address creation in BCIS via to-do-list and email.
        *   Handle 12 and 13 file Licensing cases in SCS instead of BCIS.
        *   Map BCIS users (username, post, file reference, DP login ID, case officer).
        *   Include Licensing nature Enquire.
        *   Link to DV tables of BCIS.
        *   Conduct a detailed study for easy retrieval of records from SCS by comparing data storage against a reference link from the two systems of SCS and BCIS, and determine a solution most suited to user requirements.
    *   **REQ-IR-02 Interface with BD Website**
        *   Display a list of Pre-accepted Proprietary Temporary structure data on the BD website.
    *   **REQ-IR-03 Interface with Minor Works (MWMS 2.0)**
        *   Provide sFTP upload account to MWMS 2.0 for AP/RSE data (User Name, Registration Number, HKID, Expiry Date, etc.) on a daily basis.
        *   SCS will set up an sFTP server to receive AP/RSE data and update the database.
        *   Provide a Departmental Portal link to redirect to CRM of MWMS for detailed AP/RSE information.
    *   **REQ-IR-04 Interface with ESH**
        *   Provide case information and hyperlinks from SCS to ESH to view related case information and redirect to SCS.
    *   **REQ-IR-05 Interface with ERKS**
        *   Import e-Certificates, e-notices, reply letters, and other documents into ERKS for record keeping. Detailed interface specification and implementation will be done in SM&S stage.
    *   **REQ-IR-06 Interface with BRAVO**
        *   Redirect to BRAVO using `<https://dp2.bd.hksarg/bravo/intranetSignOn>`.
        *   Redirect to BRAVO through a URL call with specified parameters:
            *   `https://dp2.bd.hksarg/bravo/BuildingSearchRedirection?CASE_NUMBER=<CASE_NUMBER>&YEAR=<YEAR>`
            *   `https://dp2.bd.hksarg/bravo/BuildingSearchRedirection?BLOCK_ID=<BLOCK_ID>`
            *   `https://dp2.bd.hksarg/bravo/BuildingSearchRedirection?SEARCH_TYPE=<SEARCH_TYPE>&SUBJECT_CODE=<SUBJECT_CODE>&CASE_NUMBER=<CASE_NUMBER>&YEAR=<YEAR>&SPECIAL_CAT=<SPECIAL_CAT>`

## 3. Technical Requirements

All technical requirements are targeted towards **System Admin** and are of **High** priority unless otherwise specified.

| Req. ID   | Requirement Name                               | Priority | N/A | :-------- | :--------------------------------------------- | :------- | N/A |---|---|---| N/A | REQ-TR-01 | 24x7 Internet and Intranet                     | H        | N/A |---|---|---| N/A | REQ-TR-02 | Integrated Cloud GCIS and On Premises          | H        | N/A |---|---|---| N/A | REQ-TR-03 | Input Validation                               | H        | N/A |---|---|---| N/A | REQ-TR-04 | Record Relocation from GCIS to On Premises     | H        | N/A |---|---|---| N/A | REQ-TR-05 | High Availability                              | H        | N/A |---|---|---| N/A | REQ-TR-06 | Monitoring and Alert Generation                | H        | N/A |---|---|---| N/A | REQ-TR-07 | DR Drill                                       | H        | N/A |---|---|---| N/A | REQ-TR-08 | UTF-8, Unicode or HKSCS                        | H        | N/A |---|---|---| N/A | REQ-TR-09 | System Logging                                 | H        | N/A |---|---|---| N/A | REQ-TR-10 | High Configurable                              | H        | N/A |---|---|---| N/A | REQ-TR-11 | Backup and Recovery                            | H        | N/A |---|---|---| N/A | REQ-TR-12 | Operation System and Browser Compatibility     | H        | N/A |---|---|---| N/A | REQ-TR-13 | Review and Update privilege                    | H        | N/A |---|---|---| N/A | REQ-TR-14 | Health Check                                   | H        | N/A |---|---|---| N/A | REQ-TR-15 | Encryption on All Communications              | H        | N/A |---|---|---| N/A | REQ-TR-16 | Version Control for application                | NA       | N/A |---|---|---| N/A | REQ-TR-17 | Monthly Usage Statistics and Ad-hoc Statistics | H        | N/A |---|---|---| N/A | REQ-TR-18 | Check-in and Check-out                         | NA       | N/A |---|---|---| N/A | REQ-TR-19 | Language support (EN/TC/SC)                    | H        | N/A |---|---|---| N/A | REQ-TR-20 | System Performance                             | H        | N/A |---|---|---| N/A | REQ-TR-21 | Reports and statistics for monitor system performance | H        | N/A |---|---|---| N/A | REQ-TR-22 | Ad-hoc and periodic updates on the contents     | H        | N/A |---|---|---| N/A | REQ-TR-23 | Provide refined Login & Authentication / FULL Audit features | H        | N/A |---|---|---| N/A | REQ-TR-24 | Login user account login by user ID and password | H        | N/A |---|---|---| N/A | REQ-TR-25 | Version control of source code                 | H        | N/A |---|---|---| N/A | REQ-TR-26 | System log tracking                            | H        | N/A |---|---|---| N/A | REQ-TR-27 | Scalable system frame design                   | H        | N/A |---|---|---| N/A | REQ-TR-28 | Data exchange with other system securely       | H        | N/A |---|---|---| N/A | REQ-TR-29 | Security measurement                           | H        | N/A |---|---|---| N/A | REQ-TR-30 | Help check email notification                  | H        | N/A |---|---|---| N/A | REQ-TR-31 | Email notification for all batch jobs          | H        | N/A |---|---|---| N/A | REQ-TR-32 | Conform to the Interoperability Framework      | H        | N/A |---|---|---| N/A | REQ-TR-33 | Manage System Parameters                       | H        | N/A |---|---|---| N/A | REQ-TR-34 | Allow System Access by EDB and SWD             | H        | N/A |---|---|---| N/A | REQ-TR-35 | Independent System (Not depended on other BD system) | H        | N/A |---|---|---| N/A | REQ-TR-36 | Logout automatically for inactive for 30 minutes | H        | N/A |---|---|---| N/A | REQ-TR-37 | Centralized log management                     | H        | N/A |---|---|---| N/A | REQ-TR-38 | Handle around 300 user accounts of EDB and SWD for Single Sign On | H        | N/A |---|---|---| N/A | REQ-TR-39 | Paper Less                                     | H        | N/A |---|---|---| N/A | REQ-TR-40 | PDF template and mapping field for letter generation | H        | N/A |---|---|---|
### 3.1. Detailed Technical Requirements

*   **REQ-TR-01: 24x7 Internet and Intranet:**  The system must be accessible 24/7 via the internet for AP/RSE and via Intranet/GNET for BD users, maintaining high availability except during maintenance.
*   **REQ-TR-02: Integrated Cloud GCIS and On Premises:** The system will integrate GCIS (Cloud) and on-premises BD infrastructure. Front-end functions for AP/RSE will be in GCIS, while back-end functions for BD users will be on-premises.
*   **REQ-TR-03: Input Validation:**  All data input must be validated to prevent security attacks (e.g., SQL Injection). CAPTCHA will be implemented for form submission to prevent DDOS attacks.
*   **REQ-TR-04: Record Relocation from GCIS to On Premises:** Functionality to relocate records from GCIS to on-premises storage.
*   **REQ-TR-05: High Availability:**  The system should maintain high availability with active-active application servers and DR capability.
*   **REQ-TR-06: Monitoring and Alert Generation:**  A log server will monitor server health and alert administrators via email in critical situations. Security audit logs will be kept for 12 months.
*   **REQ-TR-07: DR Drill:**  Disaster Recovery drills will be conducted to test procedures. Recovery Time Objective (RTO) is 1 day.
*   **REQ-TR-08: UTF-8, Unicode or HKSCS:**  The system must support UTF-8, Unicode, or ISO10646 Standard and Hong Kong Supplementary Character Set (HKSCS) coded in ISO10646.
*   **REQ-TR-09: System Logging:**  Record and track all functions, tasks, processes, and user actions. System logs, user activity logs, and transaction logs should be kept for at least 12 months.
*   **REQ-TR-10: High Configurable:**  The system should be highly configurable in coding, avoiding hard coding where possible.
*   **REQ-TR-11: Backup and Recovery:**
    *   Incremental backup daily.
    *   Full backup weekly.
    *   Full backups kept for 6 months.
    *   Archive outdated information when required, but no more than twice per year.
*   **REQ-TR-12: Operation System and Browser Compatibility:**  Support the following OS/Browser combinations:

    | Operating System / Browser | Microsoft Windows 8.1 | Microsoft Windows 10 and 11 | Mac OS X | Linux | iOS | Android | N/A |---|---|---|---|---|---|---| N/A | :------------------------- | :-------------------- | :-------------------------- | :------- | :---- | :-- | :------ | N/A |---|---|---|---|---|---|---| N/A | Microsoft Edge             | Not applicable        | Yes                         | Not applicable | Not applicable | Not applicable | Not applicable | N/A |---|---|---|---|---|---|---| N/A | Safari                     | Not applicable        | Not applicable              | Yes      | Not applicable | Yes | Not applicable | N/A |---|---|---|---|---|---|---| N/A | Mozilla Firefox            | Yes                   | Yes                         | Yes      | Yes   | Yes | Yes     | N/A |---|---|---|---|---|---|---| N/A | Google Chrome              | Yes                   | Yes                         | Yes      | Yes   | Yes | Yes     | N/A |---|---|---|---|---|---|---|
*   **REQ-TR-13: Review and Update Privilege:**  Function to review and update user privileges.
*   **REQ-TR-14: Health Check:**  Function to perform system health checks. A hyperlink will be provided to System Administration.
*   **REQ-TR-15: Encryption on All Communications:**  Communication and data transfer between client and server or server to server will be encrypted using HTTPS.
*   **REQ-TR-16: Version Control for application:** Programming versioning shall be maintained.
*   **REQ-TR-17: Monthly Usage Statistics and Ad-hoc Statistics:**
    1.  Allow data administrator to run ?Select? SQL statement through the application website. Results shall be exportable as CSV excel file. (e.g. No contain HKID )
    2.  Appendix 4 - Utilisation Survey
    3.  Active and Inactive User Account Report by selection date and time
*   **REQ-TR-18: Check-in and Check-out:** The system shall able to check-in or check-out documents in order to prevent duplicate update on same document.
*   **REQ-TR-19: Language Support (EN/TC/SC):**  Web pages in English, Traditional Chinese, and Simplified Chinese.
*   **REQ-TR-20: System Performance:**  Periodically monitor system performance to identify bottlenecks.
*   **REQ-TR-21: Reports and statistics for monitor system performance:** The reports and statistics of system performance can be generated using system monitoring tool.
*   **REQ-TR-22: Ad-hoc and periodic updates on the contents:** The system allows authorized BD users to edit the case information. Develop an automatic function to delete the records by customization
*   **REQ-TR-23: Provide refined Login & Authentication / FULL Audit features:** The Login information will be record in audit and stored in database.
*   **REQ-TR-24: Login user account login by user ID and password:** In case the OSDP is malfunctioned, the system provide another interface for BD/EDB/SWD users to login the system using username and password.
*   **REQ-TR-25: Version control of source code:** The source code of the system will be kept in Version Control System and providing versioning support.
*   **REQ-TR-26: System log tracking:** The system provides logging to file for all functions and events.
*   **REQ-TR-27: Scalable system frame design:** The system provides High Availability (HA) in the system design so that to minimize single point of failure. Also, it can increase the HA by adding extra nodes whenever it needs.
*   **REQ-TR-28: Data exchange with other system securely:** The system will connect other system using secure method such as HTTPS if it is applicable.
*   **REQ-TR-29: Security measurement:** The system will be designed with security in first priority and security control will be added in different layers such as application, network, database?etc.
*   **REQ-TR-30: Help check email notification:** The system will send email notification using internal BD email server and external GCIS email server. The email server should be monitored by system administrator.
*   **REQ-TR-31: Email notification for all batch jobs:** Once the batch job is finished, an email notification will be sent to system administrator.
*   **REQ-TR-32: Conform to the Interoperability Framework:** The system is designed and developed using standard and well-design application framework i.e. .Net 6
*   **REQ-TR-33: Manage System Parameters:** The system parameters will be placed in configuration file and will not hardcode in the coding.
*   **REQ-TR-34: Allow System Access by EDB and SWD:** The EDB/SWD users are required to login their OSDP and access SCS. The user authorization control will be maintained in SCS.
*   **REQ-TR-35: Independent System (Not depended on other BD system):** The system is designed to separate the front-end program for applicant/AP/RSE and the back-end program for internal BD users. Also, the system will be run independently no matter there were down time of other system, except BCIS.
*   **REQ-TR-36: Logout automatically for inactive for 30 minutes:** For SSO users, the logout will be done on ODSP. For special case i.e. login using username and password, the system will terminate the session after a certain time such as 30 mins.
*   **REQ-TR-37: Centralized log management:** The log files will be stored in centralized folder if it is applicable
*   **REQ-TR-38: Handle around 300 user accounts of EDB and SWD for Single Sign On:** The system will be tested to handle concurrent users to access SCS. In case there is any bottleneck in hardware level, it can increase the throughput by adding more nodes.
*   **REQ-TR-39: Paper Less:** The system will generate and save different documents in the system and BD users will keep the documents in hard copy of the filing system.
*   **REQ-TR-40: PDF template and mapping field for letter generation:** The generated documents will be in PDF format.

## 4. Constraints

*   **Complexity of Address Identification:** Case creation may be passed to BCIS due to address identification complexity. Data will be sent back to SCS for workflow processing after creation in BCIS.
*   **Signature of AP/RSE:** Hand-written signatures on applications sent by post need to be verified by Registry personnel.

## 5. Appendices

*   **Appendix 1:** 3-Tier BSR System Diagram (Refer to original document).
*   **Appendix 2:** Sample of School and CCC Certificates and Notices (Refer to original document).
*   **Appendix 3:** Sample of Letter of Requirement (LoR) (Refer to original document).
*   **Appendix 4:** Information Security Requirement

    | #  | Item                                                                                                                                                                                                                                            | N/A |---|---| N/A | :--- | :---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | N/A |---|---| N/A | **Network security controls** | N/A |
|---|---| N/A | 1  | Ensure all unnecessary services are disabled in the network devices (e.g. unnecessary ping traffic and requests from unauthorised network ports)                                                                                                | N/A |---|---| N/A | 2  | Ensure administrative consoles are not Internet-accessible and/or can only be accessible from trusted addresses.                                                                                                                                | N/A |---|---| N/A | 3  | Ensure networks are properly segregated so that critical and normal services can utilise different network connections.                                                                                                                         | N/A |---|---| N/A | 4  | Review firewall rules, intrusion detection and protection systems and remove obsolete rules or established connections, especially for temporary rules that may have been left beyond their expected lifetime.                                  | N/A |---|---| N/A | 5  | Review DDoS response plans including roles and responsibilities for various stakeholders (e.g. ISP and anti-DDoS service providers), internal procedures and escalation protocols etc.                                                          | N/A |---|---| N/A | 6  | Check that networks protected by a content delivery network (CDN) solution only allow incoming traffic from the specific source IP addresses of the CDN and the original Internet-facing IP addresses are not disclosed to unauthorised parties | N/A |---|---| N/A | **Endpoint protection** | N/A |
|---|---| N/A | 7  | Ensure anti-malware software is installed and confirm that it is active on all systems and that signatures are updating correctly.                                                                                                              | N/A |---|---| N/A | 8  | Ensure the latest security patches are applied to the operating systems and applications, in particular for Internet-facing systems and websites.                                                                                               | N/A |---|---| N/A | **Access controls** | N/A |
|---|---| N/A | 9  | Review user accounts and remove any obsolete accounts. If multi-factor authentication (MFA) is enabled, check if it is properly configured.                                                                                                     | N/A |---|---| N/A | 10 | Carefully review the user privileges and activities so as to identify and cease suspicious users from gaining unauthorised access.? Management may tighten user privilege and grant permissions only when strictly necessary.                   | N/A |---|---| N/A | 11 | Ensure strong password policy is adopted, in particular for all mission ciritical sytems and information systems containing classified data.                                                                                                    | N/A |---|---| N/A | **Logging and monitoring** | N/A |
|---|---| N/A | 12 | Review the existing logging mechianism to ensure sufficient logs are retained.? For email systems and internet access service, ensure that your logs are kept for at least six months.?                                                         | N/A |---|---| N/A | 13 | Ensure all security solutions including intrusion detection/prevention system (IDPS) and web application firewall (WAF), are properly configured for identifying and reporting any suspicious activities.                                       | N/A |---|---| N/A | 14 | Ensure log records are in place with regular checking, especially for alerts generated by anti-malware and security solutions.??                                                                                                                | N/A |---|---| N/A | 15 | Allocate sufficient manpower and resources for monitoring and responding to potential cyber attacks.                                                                                                                                            | N/A |---|---| N/A | **Backup** | N/A |
|---|---| N/A | 16 | Ensure backups of data and systems are reliable and secure.? Perform restoration tests from your backups to assure speedy system recovery.??                                                                                                    | N/A |---|---| N/A | 17 | Ensure multiple generations of offline backups are maintained and detached from the network and system.                                                                                                                                         | N/A |---|---| N/A | **Incident response** | N/A |
|---|---| N/A | 18 | Review the existing incident response procedure is up to date and confirm that escalation routes and contact details are all up to date.                                                                                                        | N/A |---|---| N/A | 19 | Ensure the escalated incident response plan covers web defacement apart from typical cyber attacks.?                                                                                                                                            | N/A |---|---| N/A | 20 | Review the inventory list of the IT systems, important assets and keys for effective monitoring and resources management in emergency situations is up to date                                                                                  | N/A |---|---|
*   **Appendix 5:** Sample of Utilisation Report (Refer to original document).

## 6. Conclusion

This document provides a comprehensive overview of the requirements and constraints for the SCS installation. Adherence to these guidelines will ensure a successful and secure implementation.