![{{DEPARTMENT_LOGO}}](media/image1.jpg)

# SYSTEM INSTALLATION PLAN

**FOR**

**{{PROJECT_FULL_NAME}}**

**{{PROJECT_SHORT_NAME}}**

**OF**

**{{DEPARTMENT_NAME}}**

**Version: 0.1**

**Jan 2025**

© The Government of the Hong Kong Special Administrative Region

The contents of this document remain the property of and may not be reproduced in whole or in part without the express permission of the Government of the HKSAR.

| Distribution |                                     |
|-------------|-------------------------------------|
| Copy No.    | Holder                              |
| 1           | {{DEPARTMENT_NAME}} |
| 2           | Master Concept (Hong Kong) Limited (MC) |

| Amendment History |                       |                |            |           |           |
|------------------|------------------------|----------------|------------|-----------|-----------|
| Change Number    | Revision Description   | Pages Affected | Revision / | Date      | Approval  |
|                  |                       | on Respective  | Version    |           | Reference |
|                  |                       | Version        | Number     |           |           |
| 1                | 1st draft             | All            | 0.1        | 16/01/225 |           |

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

| Hostname (Physical Machine) | Hostname (Virtual Machine) | Purpose | IP |
|---------------------------|---------------------------|---------|-----|
| {{PRD_DB_PHYSICAL}} | {{PRD_DB_VIRTUAL}} | {{DATABASE_TYPE}} Database Server | {{PRD_DB_IP}} |
| {{PRD_APP_PHYSICAL}} | {{PRD_APP_VIRTUAL}} | {{BACKEND_TYPE}} Backend Server | {{PRD_APP_IP}} |
| {{PRD_WEB_PHYSICAL}} | {{PRD_WEB_VIRTUAL}} | {{FRONTEND_TYPE}} Frontend Server | {{PRD_WEB_IP}} |


DR environment:

List of machines and virtual machines:

| Hostname (Physical Machine) | Hostname (Virtual Machine) | Purpose | IP |
|---------------------------|---------------------------|---------|-----|
| {{DR_DB_PHYSICAL}} | {{DR_DB_VIRTUAL}} | {{DATABASE_TYPE}} Database Server | {{DR_DB_IP}} |
| {{DR_APP_PHYSICAL}} | {{DR_APP_VIRTUAL}} | {{BACKEND_TYPE}} Backend Server | {{DR_APP_IP}} |
| {{DR_WEB_PHYSICAL}} | {{DR_WEB_VIRTUAL}} | {{FRONTEND_TYPE}} Frontend Server | {{DR_WEB_IP}} |


## Software Specification

| Machine | Hostname | Software Requirement |
|---------|----------|---------------------|
| {{DATABASE_TYPE}} Database Server | {{PRD_DB_VIRTUAL}} | {{DATABASE_TYPE}} {{DATABASE_VERSION}} |
| {{BACKEND_TYPE}} Backend Server | {{PRD_APP_VIRTUAL}} | {{BACKEND_TYPE}} {{BACKEND_VERSION}}, {{PROCESS_MANAGER}} {{PM_VERSION}} |
| {{FRONTEND_TYPE}} Frontend Server | {{PRD_WEB_VIRTUAL}} | {{WEB_SERVER}} {{WEB_SERVER_VERSION}}, {{FRONTEND_TYPE}} {{FRONTEND_VERSION}} |


Development Frameworks:

| Framework | Version |
|-----------|---------|
| {{FRONTEND_TYPE}} (frontend) | {{FRONTEND_VERSION}} |
| {{BACKEND_TYPE}} (backend) | {{BACKEND_VERSION}} |
| {{DATABASE_TYPE}} (database) | {{DATABASE_VERSION}} |


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

| Pre-Requisite | Start Date | End Date | Start time | End Time |
|---------------|------------|----------|------------|----------|
| Database Server Installation (Production and DR) |  |  |  |  |
| Backend Server Installation (Production and DR) |  |  |  |  |
| Frontend Server Installation (Production and DR) |  |  |  |  |
| Functionality test (VM & Networking) |  |  |  |  |
| Database setup |  |  |  |  |
| Deployment for 1st version of frontend server |  |  |  |  |
| Deployment for 1st version of backend server |  |  |  |  |
| Application Health Check |  |  |  |  |
| Deployment for Latest Mobile Application |  |  |  |  |
| Final Check Production Web Server |  |  |  |  |
| Final Check Production Database Server |  |  |  |  |
| Final Check DR Web & Database server |  |  |  |  |
| Final Check {{WEB_SERVER}} & Framework |  |  |  |  |

## System Installation Result

The following table summarises the actual system installation schedule:

| Pre-Requisite | Actual Start Date | Actual End Date | Actual Start time | Actual End Time | Status/Result |
|---------------|-------------------|-----------------|-------------------|-----------------|---------------|
| Database Server Installation (Production, UAT and DR) |  |  |  |  |  |
| Backend Server Installation (Production, UAT and DR) |  |  |  |  |  |
| Frontend Server Installation (Production, UAT and DR) |  |  |  |  |  |
| Functionality test (VM & Networking) |  |  |  |  |  |
| Database setup |  |  |  |  |  |
| Deployment for 1st version of frontend server |  |  |  |  |  |
| Deployment for 1st version of backend server |  |  |  |  |  |
| Application Health Check |  |  |  |  |  |
| Deployment for Latest Mobile Application |  |  |  |  |  |
| Final Check Production Web Server |  |  |  |  |  |
| Final Check Production Database Server |  |  |  |  |  |
| Final Check DR Web & DB server |  |  |  |  |  |
| Final Check {{WEB_SERVER}} & Framework |  |  |  |  |  |

<<End of Document>>
