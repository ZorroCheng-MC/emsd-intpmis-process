![Logo](media/image1.jpg)

# SYSTEM INSTALLATION PLAN

**FOR**

**[PROJECT_NAME]**

**OF**

**[DEPARTMENT_NAME]**

**Version: [VERSION]**

**[DATE]**

© The Government of the Hong Kong Special Administrative Region

The contents of this document remain the property of and may not be reproduced in whole or in part without the express permission of the Government of the HKSAR.

| Distribution |                                     |
|-------------|-------------------------------------|
| Copy No.    | Holder                              |
| 1           | [DEPARTMENT_NAME]                   |
| 2           | Master Concept (Hong Kong) Limited (MC) |

| Amendment History |                       |                |            |           |           |
|------------------|------------------------|----------------|------------|-----------|-----------|
| Change Number    | Revision Description   | Pages Affected | Revision / | Date      | Approval  |
|                  |                       | on Respective  | Version    |           | Reference |
|                  |                       | Version        | Number     |           |           |
| 1                | 1st draft             | All            | [VERSION]  | [DATE]    |           |

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

| Hostname (Physical Machine) | Hostname (Virtual Machine) | Purpose | IP |
|---------------------------|---------------------------|---------|-----|
| [HARDWARE_SPECIFICATIONS] | [HARDWARE_SPECIFICATIONS] | [HARDWARE_SPECIFICATIONS] | [HARDWARE_SPECIFICATIONS] |

DR environment:

List of machines and virtual machines:

| Hostname (Physical Machine) | Hostname (Virtual Machine) | Purpose | IP |
|---------------------------|---------------------------|---------|-----|
| [DR_HARDWARE_SPECIFICATIONS] | [DR_HARDWARE_SPECIFICATIONS] | [DR_HARDWARE_SPECIFICATIONS] | [DR_HARDWARE_SPECIFICATIONS] |

## Software Specification

| Machine | Hostname | Software Requirement |
|---------|----------|---------------------|
| [SOFTWARE_SPECIFICATIONS] | [SOFTWARE_SPECIFICATIONS] | [SOFTWARE_SPECIFICATIONS] |

Development Frameworks:

| Framework | Version |
|-----------|---------|
| [FRAMEWORK_SPECIFICATIONS] | [FRAMEWORK_SPECIFICATIONS] |

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

| Pre-Requisite | Start Date | End Date | Start time | End Time |
|---------------|------------|----------|------------|----------|
| [INSTALLATION_SCHEDULE] | [INSTALLATION_SCHEDULE] | [INSTALLATION_SCHEDULE] | [INSTALLATION_SCHEDULE] | [INSTALLATION_SCHEDULE] |

## System Installation Result

The following table summarises the actual system installation schedule:

| Pre-Requisite | Actual Start Date | Actual End Date | Actual Start time | Actual End Time | Status/Result |
|---------------|-------------------|-----------------|-------------------|-----------------|---------------|
| [INSTALLATION_RESULTS] | [INSTALLATION_RESULTS] | [INSTALLATION_RESULTS] | [INSTALLATION_RESULTS] | [INSTALLATION_RESULTS] | [INSTALLATION_RESULTS] |

<<End of Document>>
