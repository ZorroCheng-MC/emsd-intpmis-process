---
sip_i1.md:

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
sm_i1.md:

reproduced in whole or in part without the express permission of the

|-------------|------------------------------| N/A |---|---| N/A | Copy No.    | Holder                       | N/A |             | Master Concept (Hong Kong) Limited (MC) | N/A |---|---| N/A |----------|------------------------------|-------------|----------|------------| N/A |---|---|---|---|---| N/A | Change Number     | Revision Description | Pages Affected on Respective Version | Revision / Version Number | Date       | N/A |---|---|---|---|---| N/A | 2                 | 2<sup>nd</sup> draft | All                                  | 0.2                       | 19/11/2024 | N/A |---|---|---|---|---|
[6.1.4 Database Configuration 39](#_heading=h.34g0dwd)
[6.1.5 Detailed Server and Network Configurations

[7.2 Inventory of System Software and Software Package

[8.3.3 System Security 52](#system-security)
[8.3.4 Physical Security 53](#physical-security)
[8.3.5 Password and Group Control 53](#password-and-group-control)
[8.3.6 Control Procedure of Application User Account and Production
53](#control-procedure-of-application-user-account-and-production-support-account)
[8.4 Change Control 54](#_heading=h.3mzq4wv)
[8.5 Disaster Recovery 54](#_heading=h.2250f4o)
[8.6 Database Backup Strategy 54](#_heading=h.haapch)
[8.6.1 SQL Database Backup 54](#sql-database-backup)
[8.6.2 Recovery 54](#recovery)
[8.6.3 Backup Schedule 55](#backup-schedule)
[9. Database Administration 57](#database-administration)
[9.1 Clean Database Transaction Logs 57](#_heading=h.upglbi)
[9.2 Database Backup 60](#_heading=h.3ep43zb)
[9.3 System Constraints and Limitations 62](#bookmark=id.1hmsyys)

**Purpose**
The objective of this document is to provide an overview of the system
procedure, computer operation procedure, etc. Reader interested in
Program Manual, etc.).
The major readers of System Manual are the staff responsible for

hardware configurations for LSCP, and shows the system environment
information and backup services.
In addition, some major system parameters, system configuration files

maintaining the application system. Readers interested in specific area
etc.).

**Reference and Convention**
## 4.1 Definitions
None.
## 4.2 Conventions
The following acronyms are used in the text of this document:
|**Abbreviation**|**Description**| N/A |---|---| N/A |---|---| N/A |BD|Buildings Department| N/A |---|---| N/A |LSCP|Licensing Self-Certification Portal| N/A |---|---| N/A |DMZ|Demilitarized Zone| N/A |---|---| N/A |SAN|Storage Area Network| N/A |---|---| N/A |VM|Virtual Machine| N/A |---|---| N/A |ITU|Information Technology Unit| N/A |---|---| N/A |WKGO|West Kowloon Government Offices| N/A |---|---|
**System Summary**
## 5.1 Objective
The users of the LSCP can be classified into two categories:
- BD Officers
- Public users involved in site inspection and site monitoring
The primary objective of LSCP is to provide an electronic platform for
review the inspection and monitoring records.
## 5.2 System Architecture
This is an overview of the system structure of LSCP in the Production

Production site and UAT site in another perspective.
![System Architecture](media/image3.png)
The system is holding on two datacenters: On-premise (WKGO) and

separate into 3 subnets. There are Production, UAT and DEV for internal

increased security and share the incoming requests to the frontend web

Trusted Zone and Gnet DMZ (gDMZ).
Both iDMZ and gDMZ contain a reverse proxy server and a Web Application
access.
External users (i.e. public users) access the system from the internet
the Application Server through the reverse proxy server. The Application

requests to the Web Servers in the Trusted Zone. The web application,
written in nodeJS that in turns perform CRUD on the Database Servers,
perform logic computing, and return result to the External Web Servers

internal BDSCS application from BD intranet, would connect to the BD Web
BD Web Servers perform the same function as the External Web Servers and
Departmental Portal.
Finally, there are some more servers in the Trusted Zone to support

servers
- File Server to store the temporary and permanent files
- Database Server that hosts Microsoft SQL server to store all the

servers
- Backup Server to keep snapshots of the database
Below are further details of each of the system components in the BDSCS:
<u>External Application Server</u>
The external application servers serve the static web contents in form
Internet Information Services (IIS), and also proxy the backend APIs

under the React framework. After compiling the JavaScript project, the
with rewrite rules to proxy the backend APIs.
<u>External Web Server</u>
The external web server, in this context, refers to a server that hosts
performing database operations. In the case of IIS (Internet Information
ExpressJS represents the framework used for developing the backend

handles various tasks, including interacting with databases, executing
intermediary between the frontend (such as a mobile or web application)

receives the request and passes it to the appropriate ExpressJS code for
which may involve querying the database, executing business rules, or
API generates a response that is sent back to the client application

It is using the same technology stack as Extra Application Server but
internal BD users only
<u>Database Management Servers</u>
Both the internal and external BDSCS applications are built on the

primarily on providing a secure and convenient login mechanism and
Smart authentication module. Users can utilize iAM Smart to log in to
their digital identity.
<u>Departmental Portal</u>
The Departmental Portal is a web service of BD to pass BD user?s
LSCP website through the Departmental Portal, the user ID will be
from the user. This login method only available inside BD?s network.
<u>SMTPX</u>
The notification module in BDSCS would send login one-time password
CIS.
<u>MWMS</u>
MWMS would provide data of AP/RSE/RGE/AS acknowledged by BD. Snapshots
internal and external BDSCS applications would intake this data by

latest copy of the BCIS database would be synced to BDSCS through SQL
internal portals for address selection, folio management, and case
through a SQL stored procedure.
This is an overview of the system structure of Pilot CDPSS in Disaster

|---------------|---------------------------------------------------------| N/A |---|---| N/A | UF-WEB-001-1  | Public User Authentication with Password                | N/A |---|---| N/A | UF-WEB-001-3  | Single User Session                                     | N/A |---|---| N/A | UF-WEB-001-5  | Public User Authentication with iAM Smart               | N/A |---|---| N/A | UF-WEB-001-7  | Change Password                                         | N/A |---|---| N/A | UF-WEB-001-9  | User Account Confirmation                               | N/A |---|---| N/A | UF-WEB-001-11 | User Account Detail Management                          | N/A |---|---| N/A | UF-WEB-001-13 | Public User Accounts Management                         | N/A |---|---| N/A | UF-WEB-001-15 | Public User Account Password Policy                     | N/A |---|---| N/A | UF-WEB-002-2  | Request TCP acceptance                                  | N/A |---|---| N/A | UF-WEB-002-4  | Unassign TCPs                                           | N/A |---|---| N/A | UF-WEB-002-6  | Temporary replacement of TCP                            | N/A |---|---| N/A | UF-WEB-002-8  | Notification of Head of Stream resignation              | N/A |---|---| N/A | UF-WEB-003-2  | Listing out responsible Site-Monitoring Schemes         | N/A |---|---| N/A | UF-WEB-004-2  | Search responsible Site Project                         | N/A |---|---| N/A | UF-WEB-004-4  | Edit and update Site Project Detail                     | N/A |---|---| N/A | UF-WEB-004-6  | View Site Project Detail                                | N/A |---|---| N/A | UF-WEB-004-8  | Supervision Plan Detail Management                      | N/A |---|---|
**Computer Hardware Configuration**
### Hardware Components
The Configuration of Physical Server in Production
|**Type**|**Model**|**Host Name**|**IP**|**Serial No.**|**Disk Configuration**| N/A |---|---|---|---|---|---| N/A |---|---|---|---|---|---| N/A |Server|Dell PowerEdge R750|prd-scs-admin-server-02|192.168.10.23, 10.5.161.207|D646RX3|RAID-5| N/A |---|---|---|---|---|---| N/A |SAN Switch|Dell DS6610B|N/A|192.168.10.16|FRC1924T0CC|N/A| N/A |---|---|---|---|---|---| N/A |SAN Storage|Dell PowerStore 500T|N/A|192.168.10.26, 192.168.10.27, 192.168.10.28, 192.168.10.29|HV1NBX3|N/A| N/A |---|---|---|---|---|---| N/A |Backup Appliance|Dell DataDomain 3300|N/A|192.168.10.20|17XMBX3|15TB| N/A |---|---|---|---|---|---| N/A |Tape Library|Dell ML3|N/A|192.168.10.20|3555L3A7801YY0|35 slots| N/A |---|---|---|---|---|---| N/A |Firewall|Palo Alto PA-850|PA-850-SCSSec|192.168.10.13, 10.5.161.220|11901063049|N/A| N/A |---|---|---|---|---|---| N/A |Switch|Cisco Catalyst|N/A|192.168.10.14|N/A|N/A| N/A |---|---|---|---|---|---| N/A |KVM|Cyber View|N/A|N/A|N/A|N/A| N/A |---|---|---|---|---|---| N/A |UPS|Vertiv? Liebert? GXT5 3000|N/A|192.168.11.21|2102311887222A010004|N/A| N/A |---|---|---|---|---|---|
Hardware Components of Production Servers
|Hardware Component|Qty| N/A |---|---| N/A |---|---| N/A |ESXi Hypervisor Server (Dell PowerEdge R750)|2| N/A |---|---| N/A |Intel(R) Xeon(R) Gold 6326 CPU @ 2.90GHz|1| N/A |---|---| N/A |32GB DDR4 Synchronous Registered (Buffered)|8| N/A |---|---| N/A |1.2TB SAS HDD|3| N/A |---|---| N/A |ESXi 8.0.3|1| N/A |---|---| N/A |NAS (Dell PowerEdge R750)|4| N/A |---|---| N/A |SAN Switch (Dell DS6610B)|6| N/A |---|---| N/A |SAN Storage (Dell PowerStore 500T)|6| N/A |---|---| N/A |Backup Appliance (Dell DataDomain DD3300)|8| N/A |---|---| N/A |Tape Library (DELL ML3)|9| N/A |---|---| N/A |Firewall (Palo Alto PA 850)|11| N/A |---|---| N/A |Switch (Cisco ???)|11| N/A |---|---| N/A |KVM (CyberView)|13| N/A |---|---| N/A |UPS (Vertiv? Liebert? GXT5 3000)|13| N/A |---|---|
Partition Configuration of Production Servers
|Host Name|Drive|Capacity|Description| N/A |---|---|---|---| N/A |---|---|---|---| N/A |prd-scs-admin-server-01|local|2.4TB|VMware ESXi Operating system| N/A |---|---|---|---| N/A |PS500T-Cluster1|VM_Volume01|20TB|Shared pool of storage space| N/A |---|---|---|---| N/A |prd-scs-nas|C:|???|OS| N/A |---|---|---|---|
The Configuration of Physical Server in DR Site
|**Type**|**Model**|**Host Name**|**IP**|**Serial No.**|**Disk Configuration**| N/A |---|---|---|---|---|---| N/A |---|---|---|---|---|---| N/A |Server|Dell PowerEdge R750|dr-scs-admin-server-01|192.168.20.17, 10.5.174.216|G646RX3|RAID-5| N/A |---|---|---|---|---|---| N/A |SAN Switch|Dell DS6610B|N/A|192.168.20.14|FRC1924T0CE|N/A| N/A |---|---|---|---|---|---| N/A |Firewall|Palo Alto PA-850|PA-850-SCSDR|192.168.20.12, 10.5.174.215|011901063069|N/A| N/A |---|---|---|---|---|---| N/A |UPS|Vertiv? Liebert? GXT5 3000|N/A|192.168.20.11|2102311887222A01000A|N/A| N/A |---|---|---|---|---|---|
Hardware Components of Disaster Recovery Servers
|Hardware Component|Qty| N/A |---|---| N/A |---|---| N/A |ESXi Hypervisor Server (Dell PowerEdge R750)|2| N/A |---|---| N/A |SAN Switch (Dell DS6610B)|4| N/A |---|---| N/A |SAN Storage (Dell PowerStore 500T)|5| N/A |---|---| N/A |Firewall (Palo Alto PA 850)|7| N/A |---|---| N/A |KVM|7| N/A |---|---| N/A |UPS (Vertiv? Liebert? GXT5 3000)|7| N/A |---|---|
Partition Configuration of DR Servers
|Host Name|Drive|Capacity|Description| N/A |---|---|---|---| N/A |---|---|---|---| N/A |PS500T-Cluster2|VM Volume01|20TB|Shared pool of storage space| N/A |---|---|---|---|
### Guest Servers Components
Production guest servers
|Host Name|RAM (GB)|Disk (GB)|IP Addresses|Host Server / Zone| N/A |---|---|---|---|---| N/A |---|---|---|---|---| N/A |prd-scs-backup-01|16|1.33TB|10.5.161.210|prd-scs-admin-server-01| N/A |---|---|---|---|---| N/A |prd-scs-kiwi-01|24|1TB|10.5.161.211|prd-scs-admin-server-01| N/A |---|---|---|---|---| N/A |prd-scs-api-01|4|300+|192.168.12.11|prd-scs-admin-server-01| N/A |---|---|---|---|---| N/A |prd-scs-frontend-01|4|300+|192.168.12.12|prd-scs-admin-server-01| N/A |---|---|---|---|---| N/A |prd-scs-backend-01|4|300+|192.168.12.13|prd-scs-admin-server-01| N/A |---|---|---|---|---| N/A |prd-scs-db-01|8|100+|192.168.12.14|prd-scs-admin-server-01| N/A |---|---|---|---|---| N/A |prd-scs-file-01|2|100+|192.168.12.20|prd-scs-admin-server-01| N/A |---|---|---|---|---| N/A |scspwi|8|192.168.0.6+|GCIS iDMZ| N/A |---|---|---|---| N/A |scspwg|8|192.168.4.6+|GCIS gDMZ| N/A |---|---|---|---| N/A |scspdb|16|200+|GCIS Trust Zone| N/A |---|---|---|---| N/A |scspbk2|16|1TB+|GCIS Trust Zone| N/A |---|---|---|---|
UAT guest servers
|Host Name|RAM (GB)|Disk (GB)|IP Addresses|Host Server / Zone| N/A |---|---|---|---|---| N/A |---|---|---|---|---| N/A |uat-scs-db-01|4|192.168.13.13|prd-scs-admin-server-01| N/A |---|---|---|---| N/A |uat-scs-file-01|2|100+|192.168.13.15|prd-scs-admin-server-01| N/A |---|---|---|---|---| N/A |scsuwi|8|192.168.0.7+|GCIS iDMZ| N/A |---|---|---|---| N/A |scsuwg|8|192.168.4.7+|GCIS gDMZ| N/A |---|---|---|---| N/A |scsudb|16|100+|GCIS Trust Zone| N/A |---|---|---|---|
Dev guest servers
|Role|Host Name|vCPU|RAM (GB)|Disk (GB)|Data Center| N/A |---|---|---|---|---|---| N/A |---|---|---|---|---|---| N/A |API|dev-scs-api-01|4|N/A|N/A|prd-scs-admin-server-01| N/A |---|---|---|---|---|---| N/A |Frontend|dev-scs-frontend-01|4|N/A|N/A|prd-scs-admin-server-01| N/A |---|---|---|---|---|---| N/A |Backend|dev-scs-backend-01|4|N/A|N/A|prd-scs-admin-server-01| N/A |---|---|---|---|---|---|
Disaster Recovery guest servers
|Host Name|RAM (GB)|Disk (GB)|IP Addresses|Host Server / Zone| N/A |---|---|---|---|---| N/A |---|---|---|---|---| N/A |dr-scs-backup-01|16|1.33TB|10.5.174.225|dr-scs-admin-server-01| N/A |---|---|---|---|---| N/A |dr-scs-kiwi-01|24|1TB|10.5.161.224|dr-scs-admin-server-01| N/A |---|---|---|---|---| N/A |dr-scs-api-01|8|N/A|192.168.22.11|dr-scs-admin-server-01| N/A |---|---|---|---|---| N/A |dr-scs-frontend-01|8|N/A|192.168.22.12|dr-scs-admin-server-01| N/A |---|---|---|---|---| N/A |dr-scs-backend-01|8|N/A|192.168.22.13|dr-scs-admin-server-01| N/A |---|---|---|---|---| N/A |dr-scs-db-01|2|90+|192.168.22.14|dr-scs-admin-server-01| N/A |---|---|---|---|---| N/A |dr-scs-file-01|2|90+|192.168.22.16|dr-scs-admin-server-01| N/A |---|---|---|---|---| N/A |scspwi|8|192.168.0.6+|GCIS iDMZ| N/A |---|---|---|---| N/A |scspwg|8|192.168.4.6+|GCIS gDMZ| N/A |---|---|---|---| N/A |scspdb|16|200+|GCIS Trust Zone| N/A |---|---|---|---| N/A |scspbk2|16|1TB+|GCIS Trust Zone| N/A |---|---|---|---|
### Gateway and SMTPX Configuration
SMTPX
|Parameter|Value| N/A |---|---| N/A |---|---| N/A |SMTPX Hostname|smtpx.cis.hksarg| N/A |---|---| N/A |IP Addresses|10.106.5.103, 10.106.105.103| N/A |---|---| N/A |Port|587| N/A |---|---| N/A |Allowed IP Range|(B/Ds' IP address within GNET)| N/A |---|---| N/A |Authentication|By e-Certificate issued from Hong Kong Post or the Government| N/A |---|---| N/A |Connection encryption|TLS| N/A |---|---|
WKGO Production Network Gateway
|Gateway|Subnet|IP Range|vlan / Zone| N/A |---|---|---|---| N/A |---|---|---|---| N/A |192.168.11.1|255.255.255.0|192.168.11.1-254|Replication / Backup| N/A |---|---|---|---| N/A |192.168.13.1|255.255.255.0|192.168.13.1-254|UAT| N/A |---|---|---|---| N/A |10.5.161.1|255.255.255.0|10.5.161.205-235|BD Network| N/A |---|---|---|---|
AIA DR Network Gateway
|Gateway|Subnet|IP Range|vlan / Zone| N/A |---|---|---|---| N/A |---|---|---|---| N/A |192.168.21.1|255.255.255.0|192.168.21.1-254|Replication / Backup| N/A |---|---|---|---| N/A |10.5.174.1|255.255.255.0|10.5.174.215-234|BD Network| N/A |---|---|---|---|
Database Configuration
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
```

Okay, I've reviewed the provided documents and will summarize the information related to your questions.

**1. External Firewall**

*   **BD CDPSS - Prod Installation & Operation Manual (network) v1.0 Section 1:**  This section should contain the details about the external firewall configuration.  You'll need to refer to the document itself to get the specifics.
*   **BD - VM & Network Upgrade for CDPSS Site Infra Configuration Information - 20230427_v0.1 tab - Prod - FW port, Prod - FW VIP policy, DR - FW port, DR - FW VIP policy:** This spreadsheet provides specific port and VIP policy information for both Production and DR external firewalls.  You'll need to consult the spreadsheet to see the exact rules.

**2. Internal Firewall**

*   **BD CDPSS - Prod Installation & Operation Manual (network) v1.0 Section 2:** This section should contain the details about the internal firewall configuration.  You'll need to refer to the document itself to get the specifics.
*   **BD - VM & Network Upgrade for CDPSS Site Infra Configuration Information - 20230427_v0.1 tab - Prod - FW port, Prod - FW VIP policy, DR - FW port, DR - FW VIP policy:** This spreadsheet provides specific port and VIP policy information for both Production and DR internal firewalls.  You'll need to consult the spreadsheet to see the exact rules.

**3. Windows NLB**

*   **BD CDPSS - Prod Installation & Operation Manual (network) v1.0 Section 3:** This section should contain the details about the Windows NLB configuration.  You'll need to refer to the document itself to get the specifics.

**4. Switches - Prod DMZ Port**

The image you provided shows the network diagram for the Prod DMZ switch ports.  You'll need to refer to the image itself to get the specifics.

**5. Switches - Prod INT SW Port**

The image you provided shows the network diagram for the Prod INT switch ports.  You'll need to refer to the image itself to get the specifics.

**6. Switches ? DR DMZ SW Port**

The image you provided shows the network diagram for the DR DMZ switch ports.  You'll need to refer to the image itself to get the specifics.

**7. Switches ? DR INT SW Port**

The image you provided shows the network diagram for the DR INT switch ports.  You'll need to refer to the image itself to get the specifics.

**8. Software Inventories**

The document provides detailed software inventories for the following environments:

*   Production Environment ? WKGO
*   UAT Environment ? WKGO
*   DEV Environment ? WKGO
*   Production Environment ? GCIS P1
*   UAT Environment ? GCIS T1
*   DEV Environment ? GCIS T1
*   DR Environment ? AIA
*   Production Environment (Replicate from P1)? GCIS P2

The tables list the Machine, Hostname, and Software installed on each server in each environment.  Refer to the document for the specific details.

**9. Security and Backup**

*   **System Control:**  Authentication for BD staff is via OSDP (preferred) or username/password + OTP. External users are authenticated via OTP sent via email. Password complexity follows IT Security Guidelines.
*   **Backup:**
    *   Production, UAT, and DEV (WKGO) and DR (AIA) are backed up by prd-scs-backup-01 and dr-scs-backup-01.
    *   Daily VM image backups are stored in backup storage, weekly to tape, and daily copy to AIA.
    *   Database servers perform local backups, which are then backed up by the backup server and copied to AIA.
    *   GCIS P1 production is backed up by GCIS-provided services with offsite copy and replication to DR GCIS P2.
    *   GCIS P1 production database server performs local backups, also backed up by Veeam (scspbk2).
    *   GCIS UAT and DEV are backed up by GCIS-provided services.
*   **Security:** The system conforms to BD and DPO security policies.
    *   Data transmission is encrypted via HTTPS over TLS.  Certificates are used (ISCCA for internal, HK Post for public).
    *   Production data is stored in SAN storage; DR data is stored in local server storage. Both use RAID mirroring and encryption.
    *   Regular OS and software patches are applied.
    *   Antivirus clients are installed on all servers, managed by a virtualized Antivirus Management server.
    *   Physical security measures are in place in server rooms.
    *   Password control is enforced.
    *   User access is limited based on role.
*   **Change Control:** GIT repository with version control is used for program source code management.
*   **Disaster Recovery:**
    *   **GCIS:** Automatic failover to GCIS Prod 2. Daily database backups.
    *   **BDSCS External (On-Prem):** NGINX load balancing. Scheduled database backup. VM replication to DR.
*   **Database Backup Strategy:**
    *   Full database export backups are performed daily at 18:45 on database servers.
    *   Recovery procedures are outlined for various failure scenarios, with estimated downtime.
    *   Backup schedules are provided.

**10. Database Administration**

*   Instructions are provided for cleaning database transaction logs and performing database backups using SQL Server Management Studio (SSMS).

**11. System Constraints and Limitations**

*   URL path length limit: 250 characters
*   Restricted characters for files/folders: ~, #, %, & , \*, {, }, \\ :, \<, \>, ?, /, \|, ?

**12. Log Management**

*   Logs should include various activities (login attempts, unauthorized access, etc.).
*   Logs should be retained for 180 days, centralized, and managed by a Syslog server.
*   Logs should be reviewed regularly.
*   Logs should not be used to profile users without proper authorization.

**User Requirements Specifications (URS)**

The URS document outlines the user, functional, non-functional, and technical requirements for the Self-Certification System. It covers various aspects, including:

*   System Overview
*   Future Business Processes
*   Functional Requirements (User Registration, Login, e-submission, e-processing, etc.)
*   Non-Functional Requirements (SMS Alert, Email Notification, Security, Interfaces, etc.)
*   Technical Requirements (24x7 availability, Cloud integration, Input Validation, Backup and Recovery, etc.)

To get the specific details about each of these areas, you'll need to refer to the attached documents.


Okay, I've analyzed the provided text and extracted the technical requirements (TR) from the document. Here's a list of those requirements, along with their associated information:

**Technical Requirements**

*   **REQ-TR-27 Scalable system frame design**
    *   Page: 69

*   **REQ-TR-28 Data exchange with other system securely**
    *   Page: 70

*   **REQ-TR-29 Security measurement**
    *   Page: 70

*   **REQ-TR-30 Help check email notification**
    *   Page: 70

*   **REQ-TR-31 Email notification for all batch jobs**
    *   Page: 71

*   **REQ-TR-32 Conform to the Interoperability Framework**
    *   Page: 71

*   **REQ-TR-33 Manage System Parameters**
    *   Page: 71

*   **REQ-TR-34 Allow System Access by EDB and SWD**
    *   Page: 72

*   **REQ-TR-35 Independent System (Not depended on other BD system)**
    *   Page: 72

*   **REQ-TR-36 Logout automatically for inactive for 30 minutes**
    *   Page: 73

*   **REQ-TR-37 Centralized log management**
    *   Page: 73

*   **REQ-TR-38 Handle around 300 user accounts of EDB and SWD for Single Sign On**
    *   Page: 73

*   **REQ-TR-39 Paper Less**
    *   Page: 74

*   **REQ-TR-40 PDF template and mapping field for letter generation**
    *   Page: 74

**Important Considerations:**

*   **Context is Key:**  Without the full document, it's impossible to provide detailed explanations of each requirement.  The surrounding text would give the specific meaning and constraints for each.
*   **Further Analysis Needed:**  Each of these "Technical Requirements" would need to be broken down into more specific, testable criteria during the system design phase.

I hope this is helpful!


# System Installation Plan Document

This document consolidates the information provided in the various sections to create a comprehensive System Installation Plan.

## 1. Introduction

This document outlines the requirements, constraints, and technical specifications for the installation and deployment of the new system (SCS - details not fully specified in the provided document, but assumed to be the system being described). The system aims to enhance efficiency and security in handling building-related processes.

## 2. Functional Requirements

The system must fulfill the following functional requirements:

*   **REQ-SR-05 System Control:** Secure access to the system using firewalls, network controls, and physical access controls.
*   **REQ-IR-01 Interface with BCIS:**
    *   Receive master data from BCIS for case creation.
    *   Send application data to BCIS for case creation (batch).
    *   Update application data in BCIS.
    *   Provide a reference link between SCS and BCIS.
    *   Transfer data from SCS to BCIS for statistical reporting.
    *   Select block for creating new address in BCIS via to-do-list and email.
    *   Handle 12 and 13 file Licensing cases in SCS instead of BCIS.
    *   Map BCIS users (username, post, file reference, DP login ID, case officer).
    *   Include Licensing nature Enquire.
    *   Link to DV tables of BCIS.
    *   Conduct a detailed study for easy retrieval of records from SCS by comparing data storage against a reference link from the two systems of SCS and BCIS, and determine a solution most suited to user requirements.
*   **REQ-IR-02 Interface with BD Website:** Display a list of Pre-accepted Proprietary Temporary structure data on the BD website.
*   **REQ-IR-03 Interface with Minor Works:**
    *   Provide an sFTP upload account to MWMS 2.0 for AP/RSE data collection (User Name, Registration Number, HKID, Expiry Date, etc.).
    *   Set up an sFTP server to receive AP/RSE data and update the database.
    *   Provide a Departmental Portal link to redirect to CRM of MWMS for detailed AP/RSE information.
*   **REQ-IR-04 Interface with ESH:** Provide case information and hyperlinks from SCS to ESH and vice versa.
*   **REQ-IR-05 Interface with ERKS:** Import e-Certificates, e-notices, reply letters, and other documents into the ERKS system for record keeping.
*   **REQ-IR-06 Interface with BRAVO:** Redirect to BRAVO using a specified URL, passing parameters such as CASE_NUMBER, YEAR, BLOCK_ID, SEARCH_TYPE, SUBJECT_CODE, and SPECIAL_CAT.

## 3. Technical Requirements

The system must meet the following technical requirements:

*   **REQ-TR-01:** 24x7 Internet and Intranet availability.
*   **REQ-TR-02:** Integrated Cloud GCIS and On-Premises deployment. Front-end in GCIS, back-end on-premises.
*   **REQ-TR-03:** Input Validation to prevent security attacks (SQL Injection, DDOS). CAPTCHA implementation.
*   **REQ-TR-04:** Record Relocation from GCIS to On-Premises functionality.
*   **REQ-TR-05:** High Availability (active-active application server, DR capability).
*   **REQ-TR-06:** Monitoring and Alert Generation (log server, email alerts, security audit logs for 12 months).
*   **REQ-TR-07:** DR Drill testing (Recovery Time Objective RTO is 1 day).
*   **REQ-TR-08:** UTF-8, Unicode, or HKSCS support.
*   **REQ-TR-09:** System Logging (record all functions, tasks, processes, and user actions for at least 12 months).
*   **REQ-TR-10:** High Configurable design (avoid hard coding).
*   **REQ-TR-11:** Backup and Recovery:
    *   Incremental backup daily.
    *   Full backup weekly.
    *   Full backups retained for 6 months.
    *   Archive outdated information, when required but no more than twice per year.
*   **REQ-TR-12:** Operation System and Browser Compatibility (see table below).
*   **REQ-TR-13:** Review and Update User Privilege functionality.
*   **REQ-TR-14:** Health Check functionality (hyperlink for System Administration).
*   **REQ-TR-15:** Encryption on All Communications (HTTPS).
*   **REQ-TR-16:** Version Control for application.
*   **REQ-TR-17:** Monthly Usage Statistics and Ad-hoc Statistics:
    *   Allow data administrator to run ?Select? SQL statement through the application website. Results shall be exportable as CSV excel file. (e.g. No contain HKID )
    *   Appendix 4 - Utilisation Survey
    *   Active and Inactive User Account Report by selection date and time
*   **REQ-TR-18:** Check-in and Check-out (Not applicable).
*   **REQ-TR-19:** Language Support (EN/TC/SC).
*   **REQ-TR-20:** System Performance monitoring.
*   **REQ-TR-21:** Reports and statistics for monitor system performance.
*   **REQ-TR-22:** Ad-hoc and periodic updates on the contents. Develop an automatic function to delete the records by customization.
*   **REQ-TR-23:** Provide refined Login & Authentication / FULL Audit features.
*   **REQ-TR-24:** Login user account login by user ID and password.
*   **REQ-TR-25:** Version control of source code.
*   **REQ-TR-26:** System log tracking.
*   **REQ-TR-27:** Scalable system frame design.
*   **REQ-TR-28:** Data exchange with other system securely.
*   **REQ-TR-29:** Security measurement.
*   **REQ-TR-30:** Help check email notification.
*   **REQ-TR-31:** Email notification for all batch jobs.
*   **REQ-TR-32:** Conform to the Interoperability Framework.
*   **REQ-TR-33:** Manage System Parameters.
*   **REQ-TR-34:** Allow System Access by EBD and SWD.
*   **REQ-TR-35:** Independent System (Not dependent on other BD systems).
*   **REQ-TR-36:** Logout automatically for inactive for 30 minutes.
*   **REQ-TR-37:** Centralized log Management.
*   **REQ-TR-38:** Handle around 300 user accounts of EDB and SWD for single sign on.
*   **REQ-TR-39:** Paper Less.
*   **REQ-TR-40:** PDF template and mapping field for letter generation.

### 3.1. Operation System and Browser Compatibility

| **Operating System Browser** | **Microsoft Windows 8.1** | **Microsoft Windows 10 and 11** | **Mac OS X** | **Linux** | **iOS** | **Android** | N/A | :--------------------------- | :------------------------ | :------------------------------ | :----------- | :-------- | :------ | :-------- | N/A |---|---|---|---|---|---|---| N/A | **Microsoft Edge**           | Not applicable            | **Yes**                         | Not applicable | Not applicable | Not applicable | Not applicable | N/A |---|---|---|---|---|---|---| N/A | **Safari**                   | Not applicable            | Not applicable                  | **Yes**      | Not applicable | **Yes** | Not applicable | N/A |---|---|---|---|---|---|---| N/A | **Mozilla Firefox**          | **Yes**                   | **Yes**                         | **Yes**      | **Yes**   | **Yes** | **Yes**   | N/A |---|---|---|---|---|---|---| N/A | **Google Chrome**            | **Yes**                   | **Yes**                         | **Yes**      | **Yes**   | **Yes** | **Yes**   | N/A |---|---|---|---|---|---|---|
## 4. Constraints

*   **Complexity of Address Identification:** Case creation may be passed to BCIS due to address identification complexities.
*   **Signature of AP/RSE:** Handwriting signatures on postal applications need manual verification by Registry.

## 5. Security Requirements

The system must adhere to the following security requirements (Appendix 4):

*   **Network Security Controls:**
    *   Disable unnecessary services on network devices.
    *   Restrict access to administrative consoles.
    *   Segregate networks for critical and normal services.
    *   Review and remove obsolete firewall rules.
    *   Review DDoS response plans.
    *   Check CDN configurations.
*   **Endpoint Protection:**
    *   Install and maintain active anti-malware software.
    *   Apply the latest security patches.
*   **Access Controls:**
    *   Review and remove obsolete user accounts.
    *   Verify proper configuration of multi-factor authentication (MFA).
    *   Carefully review the user privileges and activities so as to identify and cease suspicious users from gaining unauthorised access.? Management may tighten user privilege and grant permissions only when strictly necessary.
    *   Enforce a strong password policy.
*   **Logging and Monitoring:**
    *   Retain sufficient logs (email and internet access logs for at least six months).
    *   Properly configure security solutions (IDPS, WAF).
    *   Regularly check log records.
    *   Allocate sufficient manpower and resources for monitoring and responding to potential cyber attacks.
*   **Backup:**
    *   Ensure reliable and secure data and system backups.
    *   Perform restoration tests.
    *   Maintain multiple generations of offline backups.
*   **Incident Response:**
    *   Keep incident response procedures up to date.
    *   Ensure the escalated incident response plan covers web defacement apart from typical cyber attacks.?
    *   Review the inventory list of the IT systems, important assets and keys for effective monitoring and resources management in emergency situations is up to date

## 6. Deployment Architecture

The system will follow a 3-Tier architecture (Appendix 1):

*   **Presentation Tier:** GCIS Cloud (AP/RSE front-end).
*   **Application Tier:** GCIS Cloud and On-Premises.
*   **Data Tier:** GCIS Cloud and On-Premises.

## 7. Integration Points

The system integrates with the following external systems:

*   BCIS
*   BD Website
*   Minor Works (MWMS 2.0)
*   ESH
*   ERKS
*   BRAVO

## 8. Utilisation Reporting

The system will provide monthly usage statistics and ad-hoc reporting capabilities (Appendix 5).

## 9. Appendices

*   Appendix 1 ? 3-Tier BSR System (Diagram)
*   Appendix 2 ? Sample of School and CCC Certificates and Notices (Documents)
*   Appendix 3 ? Sample of Letter of Requirement (LoR) (Document)
*   Appendix 4 ? Information Security Requirement (Table)
*   Appendix 5 ? Sample of Utilisation Report (Image)

## 10. Conclusion

This document provides a comprehensive overview of the system installation plan. Adherence to these requirements and constraints will ensure a successful deployment and operation of the system.