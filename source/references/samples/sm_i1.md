**SYSTEM / OPERATION & USER MANUAL**

**FOR**

**Development of I&T Project**

**Management Information System (INTPMIS)**

**OF**

**Electrical and Mechanical Services Department**

Version: 0.1

**August 2020**

© The Government of the Hong Kong Special Administrative Region

The contents of this document remain the property of and may not be
reproduced in whole or in part without the express permission of the
Government of the HKSAR

<table>
<colgroup>
<col style="width: 29%" />
<col style="width: 70%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2"><strong>Distribution</strong></th>
</tr>
<tr class="odd">
<th>Copy No.</th>
<th>Holder</th>
</tr>
<tr class="header">
<th>1</th>
<th></th>
</tr>
<tr class="odd">
<th>2</th>
<th><blockquote>
<p>Master Concept (Hong Kong) Limited</p>
</blockquote></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Prepared By:</p>
<p>Derek Chan</p>
<p>[Programme Manager, MCHK]</p></th>
<th><p>Endorsed By:</p>
<p>[ ]</p></th>
</tr>
<tr class="odd">
<th>Date: <u>26/Aug/2020</u></th>
<th>Date: <u>dd/mm/2020</u></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

| **Amendment History** |                      |                                      |                           |             |                    |
|-----------------------|----------------------|--------------------------------------|---------------------------|-------------|--------------------|
| Change Number         | Revision Description | Pages Affected on Respective Version | Revision / Version Number | Date        | Approval Reference |
| 1                     | Initial Version      | All                                  | 1.0                       | 26 Aug 2020 |                    |
|                       |                      |                                      |                           |             |                    |
|                       |                      |                                      |                           |             |                    |
|                       |                      |                                      |                           |             |                    |
|                       |                      |                                      |                           |             |                    |
|                       |                      |                                      |                           |             |                    |
|                       |                      |                                      |                           |             |                    |
|                       |                      |                                      |                           |             |                    |

Table of Contents

[***Introduction 3***](#introduction)

> [**Program Specifications 3**](#program-specifications)
>
> [Functional Requirements 3](#functional-requirements)
>
> [Non-functional Requirements 5](#non-functional-requirements)
>
> [Use Case or Scenarios 6](#use-case-or-scenarios)
>
> [User Interface (UI) Design 16](#user-interface-ui-design)
>
> [System Architecture 25](#system-architecture)
>
> [**Training manual and material 27**](#training-manual-and-material)

[***System & Programming Manual and Workflow
28***](#system-programming-manual-and-workflow)

> [**User Login 28**](#user-login)
>
> [**Database Structure 29**](#database-structure)
>
> [**System structure 30**](#system-structure)
>
> [**Website Layout 30**](#website-layout)
>
> [**API from innoportal CMS 31**](#api-from-innoportal-cms)
>
> [Solution import 31](#solution-import)
>
> [Wish import 32](#wish-import)
>
> [**INTPMIS Report 33**](#intpmis-report)
>
> [Trend of I&T Wishes, Solutions, and Matched Trial Projects Report
> 34](#trend-of-it-wishes-solutions-and-matched-trial-projects-report)
>
> [Summary of I&T Wishes Report 34](#summary-of-it-wishes-report)
>
> [Distribution of I&T Solutions by Technology Report
> 35](#distribution-of-it-solutions-by-technology-report)
>
> [Cash flow for Matched Trial Projects on E&M InnoPortal Report
> 35](#cash-flow-for-matched-trial-projects-on-em-innoportal-report)
>
> [Statistics on I&T Projects Report
> 36](#statistics-on-it-projects-report)
>
> [Statistics Technology on I&T Projects Report
> 37](#statistics-technology-on-it-projects-report)
>
> [Expenditure on I&T Projects Report
> 37](#expenditure-on-it-projects-report)

[***Users Procedures and Operation Manual
38***](#users-procedures-and-operation-manual)

> [**Login to INTPMIS 38**](#login-to-intpmis)
>
> [**Project 39**](#project)
>
> [Browsing Project List 39](#browsing-project-list)
>
> [Create a Project 41](#create-a-project)
>
> [Edit a Project 43](#edit-a-project)
>
> [**Wish List 45**](#wish-list)
>
> [Browsing Wish List 45](#browsing-wish-list)
>
> [Edit a Wish 47](#edit-a-wish)
>
> [**Solution List 48**](#solution-list)
>
> [Browsing Solution List 48](#browsing-solution-list)
>
> [Edit a Solution 49](#edit-a-solution)

[***Administrator Procedures and Operation Manual
51***](#administrator-procedures-and-operation-manual)

> [**Project 51**](#project-1)
>
> [Edit a Project 51](#edit-a-project-1)
>
> [**Log List 52**](#log-list)
>
> [Browsing Log List 52](#browsing-log-list)

# Introduction

This System & User Manual intended to provide the necessary information
to use the I&T Project Management Information System (INTPMIS).

The manual assumed that the working environment of the system is under
Window10 operation system with IE11 or Chrome browser.

## Program Specifications {#program-specifications .unnumbered}

### Functional Requirements {#functional-requirements .unnumbered}

1.  Login

- The system should support single sign on through the Windows Active
  > Directory

- Support Existing User Permission Matrix Mapping

- If the user is an Acting of another user according to the LDAP login
  > details, there should be an option for the user to choose whether to
  > access the INTPMIS as the role of Acting or the original role of the
  > user

2.  Project List

- A page allows users to search for the projects

- Support sorting and filtering

- Allow to export the project list result in file type \".csv\" in the
  > Project page

- Allow to configure the filtering and sorting criteria

- Allow to view / edit project

3.  Create a Project

- Allow users to create a project

4.  View or Edit a Project

- Support read-only and edit mode the permission of the user

5.  Wish List

- A page allows users to search for the wishes

- Support sorting and filtering

- Allow to export the wish list result in file type \".csv\" in the Wish
  > page

- Allow to configure the filtering and sorting criteria

- Allow to view / edit wish

6.  View or Edit a Wish

- Support read-only and edit mode the permission of the user

7.  Solution List

- A page allows users to search for the solutions

- Support sorting and filtering

- Allow to export the solution list result in file type \".csv\" in the
  > Solution page

- Allow to configure the filtering and sorting criteria

- Allow to view / edit solution

8.  View and Edit a Solution

- Support read-only and edit mode the permission of the user

9.  Report List

- Support sorting and filtering

- Allow to export the report list result in file type \".csv\" in the
  > Report page

- Allow to configure the filtering and sorting criteria

- Allow to view / edit report

10. View Report

- Support read-only mode the permission of the user

11. Log List

- Support sorting and filtering

- Allow to export the log list result in file type \".csv\" in the
  > Report page

- Allow to configure the filtering and sorting criteria

- Allow to view / edit log

12. View Log List

- Support read-only mode the permission of the user

13. Upload File

- Allow users to upload multiple formats of files, such as pdf, jpeg,
  > docx, xls

- Users can replace the files

- The files can be deleted

### Non-functional Requirements {#non-functional-requirements .unnumbered}

1.  Response Time

- The response time for predefined query should be 95% within 5 seconds,
  > subject to confirmation of the selected technical solution.

2.  Service Time

- The access to the new system would be 08:00 to 20:00 daily, and late
  > night provisionally. 7x24 availability is not required.

- Achieve availability of 99.0% (i.e. unscheduled downtime could not
  > exceed 7.2 minutes per day or 1.83 days per year on average).

3.  Export

- Allow data of tables to be exported in different external
  > easy-readable formats such as Excel.

4.  Scalability

- Provide scalability options of hardware, software, etc. for future
  > system expansion.

5.  System Performance

- Provide technically sound architecture to meet response time and
  > agreed performance level.

6.  User Interface Requirement

- The user-interfaces and graphical user interface (GUI) must be
  > user-friendly. Based on the user profile, personalised views can be
  > provided. The interface of the solution should be consistent with
  > web-based applications.

- Adopt responsive web design to adjust layout according to different
  > screen sizes in order to facilitate users' browsing experience in
  > devices including but not limited to desktops, tablets and mobile
  > phones.

- Function and display properly in multiple browsers including Internet
  > Explorer and Chrome with Apollo support version.

7.  Function Access Rights

- Able to define various user access rights of functions according to
  > operations or user levels (access right can be assigned to the user
  > group or individual user).

8.  Access to Data

- Able to define access rights for users to access particular data and
  > also on a conditional basis.

- Able to define access monitoring for the selected data.

9.  System Backup

- Able to meet general backup requirements including data and system;
  > and all audit logging information.

### Use Case or Scenarios {#use-case-or-scenarios .unnumbered}

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>SSO Login</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user logging into
the INTPMIS</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th>The user has an account with the application</th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>User gets an authentication ID from EMSD Active Directory</p>
</blockquote></li>
<li><blockquote>
<p>The system will call LDAP API to get users authentication code and
information by the staff ID</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>The landing page will be shown</th>
</tr>
<tr class="header">
<th>Alternative Scenario</th>
<th>The user name login page will be shown</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>User Name Login</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user logging into
the INTPMIS</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th>The user has an account with the application</th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>Open a browser (Internet Explorer/ Chrome)</p>
</blockquote></li>
<li><blockquote>
<p>Go to http://intpmis/#/login</p>
</blockquote></li>
<li><blockquote>
<p>Input email address and password</p>
</blockquote></li>
<li><blockquote>
<p>Click "Sign In" button</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>The page is navigated to the landing page</th>
</tr>
<tr class="header">
<th>Alternative Scenario</th>
<th>Login fail and an error prompt is shown.</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>Create Project</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user creating a new
project in the project management</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application.</p>
</blockquote></li>
<li><blockquote>
<p>The user has the necessary permissions to create a project.</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>Click “Create” under “Project Management”</p>
</blockquote></li>
<li><blockquote>
<p>Fill the required fields</p>
</blockquote></li>
<li><blockquote>
<p>Click “Submit” button</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>Project is created successfully and a successful message is shown
with the project number</th>
</tr>
<tr class="header">
<th>Alternative Scenario</th>
<th><ol type="1">
<li><blockquote>
<p>Input field is not filled</p>
</blockquote></li>
</ol>
<blockquote>
<p>The error message is shown under the field</p>
</blockquote>
<ol start="2" type="1">
<li><blockquote>
<p>Value is not valid</p>
</blockquote></li>
</ol>
<blockquote>
<p>The error message is shown</p>
</blockquote></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>Edit Project</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user editing an
existing project in the project management.</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application.</p>
</blockquote></li>
<li><blockquote>
<p>The user has the necessary permissions to create a project.</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>Click “Edit” under “Project Management”</p>
</blockquote></li>
<li><blockquote>
<p>Click edit icon to edit the project</p>
</blockquote></li>
<li><blockquote>
<p>To edit information of the project, users can:</p>
</blockquote>
<ul>
<li><blockquote>
<p>select completed</p>
</blockquote></li>
<li><blockquote>
<p>input values</p>
</blockquote></li>
<li><blockquote>
<p>empty input</p>
</blockquote></li>
</ul></li>
<li><blockquote>
<p>Then click “Save All” button</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>Save successfully and an successful message is shown</th>
</tr>
<tr class="header">
<th>Alternative Scenario</th>
<th>Invalid input and an alert message is shown</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>View Project</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user viewing the
details of an existing project in the project management.</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application.</p>
</blockquote></li>
<li><blockquote>
<p>The user has access to the project they want to view</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>Click “View” under “Project Management”</p>
</blockquote></li>
<li><blockquote>
<p>Scroll the bottom bar to the right to show the project detail</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>The user has viewed the details of the selected project.</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>Filter Project</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user filtering for
specific projects within the project management.</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application.</p>
</blockquote></li>
<li><blockquote>
<p>The user is on the project management list displaying a list of
projects.</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>Input filter value</p>
</blockquote></li>
<li><blockquote>
<p>Select display number of record per page</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>The results are shown</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>Search Project</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user searching for a
specific project within the project management.</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application.</p>
</blockquote></li>
<li><blockquote>
<p>The user is on the project management list displaying a list of
projects.</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>Click search section</p>
</blockquote></li>
<li><blockquote>
<p>Select search criteria</p>
</blockquote></li>
<li><blockquote>
<p>Select values of criteria</p>
</blockquote></li>
<li><blockquote>
<p>Click “Search” button</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>The results are shown</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>Export Project</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user exporting
project data from the project management.</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application.</p>
</blockquote></li>
<li><blockquote>
<p>The user is on the project management list displaying a list of
projects.</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><p>There are two options for exporting project</p>
<ul>
<li><blockquote>
<p>Export searched records</p>
</blockquote></li>
</ul>
<blockquote>
<p>Click “Export Records” button</p>
</blockquote>
<ul>
<li><blockquote>
<p>Export all records</p>
</blockquote></li>
</ul>
<blockquote>
<p>Click “Export All Records” button</p>
</blockquote></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>The exported results will be stored in a csv file</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>Edit Wish</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user editing the
details of an existing wish in the wish management.</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application</p>
</blockquote></li>
<li><blockquote>
<p>The user has access to the wish they want to edit</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>Input value to edit</p>
</blockquote></li>
<li><blockquote>
<p>Click “Save All” button</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>Wish is edited successfully and an alert message is shown</th>
</tr>
<tr class="header">
<th>Alternative Scenario</th>
<th>Invalid input and an alert message is shown</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>View Wish</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user viewing the
details of an existing wish in the wish management.</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application</p>
</blockquote></li>
<li><blockquote>
<p>The user has access to the wish they want to view</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>Click “View” under “Wish Management”</p>
</blockquote></li>
<li><blockquote>
<p>Scroll the bottom bar to right to view detail of the wish</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>The user has viewed the details of the selected wish.</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>Search Wish</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user searching for a
specific wish within the project management.</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application.</p>
</blockquote></li>
<li><blockquote>
<p>The user is on the wish management list displaying a list of
wishes.</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>Click search section</p>
</blockquote></li>
<li><blockquote>
<p>Select search criteria</p>
</blockquote></li>
<li><blockquote>
<p>Select values of criteria</p>
</blockquote></li>
<li><blockquote>
<p>Click “Search” button</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>The results are shown</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>Filter Wish</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user filtering for a
specific wish within the project management.</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application.</p>
</blockquote></li>
<li><blockquote>
<p>The user is on the wish management list displaying a list of
wishes.</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>Input filter value</p>
</blockquote></li>
<li><blockquote>
<p>Select display number of record per page</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>The results are shown</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>Export Wish</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user exporting wish
data from the wish management.</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application.</p>
</blockquote></li>
<li><blockquote>
<p>The user is on the wish management list displaying a list of
wishes.</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><p>There are two options for exporting wish</p>
<ul>
<li><blockquote>
<p>Export searched records</p>
</blockquote></li>
</ul>
<blockquote>
<p>Click “Export Records” button</p>
</blockquote>
<ul>
<li><blockquote>
<p>Export all records</p>
</blockquote></li>
</ul>
<blockquote>
<p>Click “Export All Records” button</p>
</blockquote></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>The exported results will be stored in a csv file</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>Edit Solution</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user editing the
details of an existing solution in solution management.</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application</p>
</blockquote></li>
<li><blockquote>
<p>The user has access to the solution they want to edit</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>Input value to edit</p>
</blockquote></li>
<li><blockquote>
<p>Click “Save All” button</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>Solution is edited successfully and an alert message is shown</th>
</tr>
<tr class="header">
<th>Alternative Scenario</th>
<th>Invalid input and an alert message is shown</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>View Solution</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user viewing the
details of an existing solution in solution management.</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application</p>
</blockquote></li>
<li><blockquote>
<p>The user has access to the solution they want to view</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>Click “View” under “Solution Management”</p>
</blockquote></li>
<li><blockquote>
<p>Scroll the bottom bar to right to view detail of the solution</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>The user has viewed the details of the selected solution.</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>Export Solution</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user exporting
solution data from the solution management.</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application.</p>
</blockquote></li>
<li><blockquote>
<p>The user is on the solution management list displaying a list of
wishes.</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><p>There are two options for exporting solution</p>
<ul>
<li><blockquote>
<p>Export searched records</p>
</blockquote></li>
</ul>
<blockquote>
<p>Click “Export Records” button</p>
</blockquote>
<ul>
<li><blockquote>
<p>Export all records</p>
</blockquote></li>
</ul>
<blockquote>
<p>Click “Export All Records” button</p>
</blockquote></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>The exported results will be stored in a csv file</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>View Report</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user viewing reports
in report management.</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>Click “View” under “Report Management”</p>
</blockquote></li>
<li><blockquote>
<p>Scroll down to view more reports</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>The user has viewed reports.</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>Print Report</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user printing a
report</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application</p>
</blockquote></li>
<li><blockquote>
<p>The user has access to the report they want to print</p>
</blockquote></li>
<li><blockquote>
<p>The report is displayed or accessible on the application's
interface</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>Select the period of the report</p>
</blockquote></li>
<li><blockquote>
<p>Select the other day for the report</p>
</blockquote></li>
<li><blockquote>
<p>Click “Confirm” button</p>
</blockquote></li>
<li><blockquote>
<p>The report is shown</p>
</blockquote></li>
<li><blockquote>
<p>Click “Print” to print all report</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th><ul>
<li><blockquote>
<p>The user has successfully printed the report with the chosen print
settings.</p>
</blockquote></li>
</ul></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>View and Export Log</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user viewing and
exporting log</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application</p>
</blockquote></li>
<li><blockquote>
<p>The user has access to the logs they want to export</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><ul>
<li><blockquote>
<p>Select tag type of log</p>
</blockquote></li>
<li><blockquote>
<p>Log records are shown in list</p>
</blockquote></li>
<li><blockquote>
<p>Click “+” button to view log detail</p>
</blockquote></li>
<li><blockquote>
<p>Click “Export Records” button to export records to a csv file</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>The logs are exported to a csv file</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 27%" />
<col style="width: 72%" />
</colgroup>
<thead>
<tr class="header">
<th>Use Case</th>
<th>Cancel Reminder</th>
</tr>
<tr class="odd">
<th>Actor</th>
<th>User</th>
</tr>
<tr class="header">
<th>Description</th>
<th>This use case describes the steps involved in a user cancelling a
reminder</th>
</tr>
<tr class="odd">
<th>Preconditions</th>
<th><ul>
<li><blockquote>
<p>The user is logged into the application</p>
</blockquote></li>
<li><blockquote>
<p>The user has created a reminder</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="header">
<th>Main Scenario</th>
<th><p>There are two options to cancel reminder(s):</p>
<ul>
<li><blockquote>
<p>Click checked button to cancel the reminder of a record</p>
</blockquote></li>
<li><blockquote>
<p>Select multiple records and click batch checked to cancel reminder of
selected records</p>
</blockquote></li>
</ul></th>
</tr>
<tr class="odd">
<th>Postconditions</th>
<th>The reminder is cancelled</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

### User Interface (UI) Design {#user-interface-ui-design .unnumbered}

1.  Login Page

![](media/image13.png){width="4.152083333333334in"
height="2.672222222222222in"}

2.  Project Management

![](media/image38.png){width="5.7659722222222225in"
height="2.734027777777778in"}

![](media/image8.png){width="6.499982502187226in"
height="9.379804243219597in"}

3.  Report Management

![](media/image56.jpg){width="5.777267060367454in"
height="2.7606036745406826in"}

![](media/image57.png){width="5.770138888888889in"
height="2.186111111111111in"}

![](media/image49.png){width="5.770138888888889in"
height="0.8479166666666667in"}

![](media/image50.png){width="5.770138888888889in"
height="2.1465277777777776in"}

![](media/image47.png){width="5.770138888888889in"
height="2.589583333333333in"}

![](media/image55.png){width="5.770138888888889in"
height="2.1638888888888888in"}

![](media/image4.png){width="5.770138888888889in" height="1.78125in"}

![](media/image53.png){width="5.770138888888889in"
height="3.2631944444444443in"}

![](media/image7.png){width="5.770138888888889in" height="2.6125in"}

![](media/image16.png){width="5.770138888888889in"
height="3.107638888888889in"}

![](media/image6.png){width="5.770138888888889in"
height="2.838888888888889in"}

4.  Wish Management

![](media/image34.jpg){width="5.872858705161855in"
height="2.8858431758530183in"}

![](media/image39.png){width="6.209057305336833in"
height="7.273497375328084in"}

5.  Solution Management

![](media/image32.jpg){width="6.318238188976378in"
height="2.9947965879265093in"}

![](media/image18.png){width="6.396002843394576in"
height="6.038707349081365in"}

6.  Log Management

![](media/image19.png){width="6.012259405074365in"
height="2.7914413823272093in"}

### System Architecture {#system-architecture .unnumbered}

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

## Training manual and material {#training-manual-and-material .unnumbered}

This System Manual intended to provide the necessary information to use
the revamped Innoportal, which was launched on [25-8-2020]{.mark}.

The manual assumed that the reader had a good knowledge of Vue, CSS,
JAVASCRIPT and Node.js language.

# System & Programming Manual and Workflow {#system-programming-manual-and-workflow}

## User Login {#user-login .unnumbered}

The system provide 2 ways to login.

1\. SSO login by LDAP API

> The SSO login was referred from other existing EMSD system. User will
> get authentication AD from EMSD Active Directory. And the system will
> call LDAP API to get users authentication code and information by the
> staff ID.

2\. By user name and password created by admin users.

> If user do not have authentication AD, system will redirect users to
> login page. Users can login to the system by input user name and
> password.

The following diagram showed the User Authentication workflow:

![https://lh6.googleusercontent.com/9TfPlLvGCpzEvWOVjZxf_al9ZOBFXuNn5yLJvNKAhIV9hGUtyvYIkOngBP2PddJPtOWtYu1j4TsLBfKwrIYOvdU7UY91NJdhV2q5KKuFhs_IENnXGta-spzD4UpfQT4GfrZMvVvQ](media/image41.png){width="5.770138888888889in"
height="4.076388888888889in"}

## Database Structure {#database-structure .unnumbered}

The system storing all data in eight table in a database. There are
include archive, hierarchy, log, project, role, role_user_user_reles,
solution, user and wish. All table attribute show as below:

![](media/image48.png){width="5.770138888888889in"
height="8.302281277340333in"}

## System structure {#system-structure .unnumbered}

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 74%" />
</colgroup>
<thead>
<tr class="header">
<th>Landing</th>
<th>Landing page calling SSO</th>
</tr>
<tr class="odd">
<th>Login</th>
<th>Manual Login page</th>
</tr>
<tr class="header">
<th>System user management</th>
<th><ol type="a">
<li><blockquote>
<p>Project Management</p>
</blockquote>
<ol type="i">
<li><blockquote>
<p>Project Create</p>
</blockquote></li>
<li><blockquote>
<p>Projects Edit</p>
</blockquote></li>
<li><blockquote>
<p>Project Detail Edit</p>
</blockquote></li>
<li><blockquote>
<p>Projects View</p>
</blockquote></li>
<li><blockquote>
<p>Project Locked Records</p>
</blockquote></li>
</ol></li>
<li><blockquote>
<p>Wish Management</p>
</blockquote>
<ol type="i">
<li><blockquote>
<p>Wish Edit</p>
</blockquote></li>
<li><blockquote>
<p>Wish Detail Edit</p>
</blockquote></li>
<li><blockquote>
<p>Wish View</p>
</blockquote></li>
<li><blockquote>
<p>Wish Locked Record</p>
</blockquote></li>
</ol></li>
<li><blockquote>
<p>Solution Management</p>
</blockquote>
<ol type="i">
<li><blockquote>
<p>Solution Edit</p>
</blockquote></li>
<li><blockquote>
<p>Solution Detail Edit</p>
</blockquote></li>
<li><blockquote>
<p>Solution View</p>
</blockquote></li>
<li><blockquote>
<p>Solution Locked Record</p>
</blockquote></li>
</ol></li>
<li><blockquote>
<p>Report Management</p>
</blockquote>
<ol type="i">
<li><blockquote>
<p>Report Edit</p>
</blockquote></li>
</ol></li>
</ol></th>
</tr>
<tr class="odd">
<th>Report View</th>
<th>Report browsing and printing</th>
</tr>
<tr class="header">
<th>Log Management</th>
<th>Log data</th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## Website Layout {#website-layout .unnumbered}

![](media/image38.png){width="5.7659722222222225in"
height="2.734027777777778in"}

After user login, the system would be divides in to three parts Header,
Side Menu and Content Component.

## API from innoportal CMS {#api-from-innoportal-cms .unnumbered}

The system needed to integrate to the InnoPortal CMS by API provided by
InnoPortal CMS side. They were list below:

### Solution import {#solution-import .unnumbered}

Post
[[http://intpmis/api/vi/data/import-solution]{.underline}](http://intpmis/api/vi/data/import-solution)

Description : This api allow InnoPortal CMS call to import solution

| Key                        | Type    | Required |
|----------------------------|---------|----------|
| **soln_id**                |  string |  true    |
| **cms_id**                 |  string |  false   |
| **cms_expiry_date**        |  string |  false   |
| **soln_title**             |  string |  false   |
| **soln_cat_tech**          |  string |  false   |
| **soln_cat_app**           |  string |  false   |
| **innoportal_upload_date** |  string |  false   |
| **int_soln_provider**      |  string |  false   |
| **int_soln_provider_type** |  string |  false   |
| **is_moc_partner**         |  string |  false   |
| **moc_partner**            |  string |  false   |
| **geog_location**          |  string |  false   |
| **soln_contact_name**      |  string |  false   |
| **soln_contact_title**     |  string |  false   |
| **soln_contact_tel**       |  string |  false   |
| **soln_contact_email**     |  string |  false   |
| **soln_contact_address**   |  string |  false   |
| **if_targetted_wish**      |  string |  false   |
| **target_wish**            |  string |  false   |
| **is_iirc**                |  string |  false   |
| **iirc_bulletin_no**       |  string |  false   |
| **iirc_review_date**       |  string |  false   |
| **iirc_endorse_date**      |  string |  false   |
| **is_intac**               |  string |  false   |
| **intac_review_date**      |  string |  false   |
| **intac_endorse_date**     |  string |  false   |
| **tech_feasible**          |  string |  false   |
| **remarks**                |  string |  false   |
| **last_modified_by**       |  string |  false   |
| **last_modified_at**       |  string |  false   |
| **matched**                |  string |  false   |
| **created_by**             |  string |  false   |
| **created_at**             |  string |  false   |

Response code :

| Response code | Description             |
|---------------|-------------------------|
| 200           | Import solution success |
| 400           | Import solution fail    |

### Wish import {#wish-import .unnumbered}

Post
[[http://intpmis/api/vi/data/import-wish]{.underline}](http://intpmis/api/vi/data/import-wish)

Description : This api allow InnoPortal CMS call to import wish

| Key                              | Type    | Required |
|----------------------------------|---------|----------|
| wish_id                          |  string |  true    |
| cms_id                           |  string |  false   |
| cms_expiry_date                  |  string |  false   |
| wish_title                       |  string |  false   |
| wish_cat_smart                   |  string |  false   |
| wish_cat_tech                    |  string |  false   |
| wish_cat_app                     |  string |  false   |
| innoportal_upload_date           |  string |  false   |
| type_of_organization             |  string |  false   |
| wish_client_dept                 |  string |  false   |
| proposing_emsd_arm               |  string |  false   |
| proposing_emsd_branch            |  string |  false   |
| proposing_emsd_div               |  string |  false   |
| proposing_emsd_sub_div           |  string |  false   |
| support_emsd_div                 |  string |  false   |
| wish_emsd_contact_name_eng       |  string |  false   |
| wish_emsd_contact_name_chi       |  string |  false   |
| wish_emsd_contact_post_short     |  string |  false   |
| wish_emsd_contact_post_eng       |  string |  false   |
| wish_emsd_contact_post_chi       |  string |  false   |
| wish_emsd_contact_email          |  string |  false   |
| wish_emsd_contact_tel            |  string |  false   |
| is_innoteam                      |  string |  false   |
| innoteam_round                   |  string |  false   |
| int_challenge_no                 |  string |  false   |
| int_challenge_title              |  string |  false   |
| is_iirc                          |  string |  false   |
| iirc_bulletin_no                 |  string |  false   |
| iirc_review_date                 |  string |  false   |
| iirc_endorse_date                |  string |  false   |
| is_intac                         |  string |  false   |
| iirc_deadline                    |  string |  false   |
| iirc_soln                        |  string |  false   |
| intac_review_date                |  string |  false   |
| intac_endorse_date               |  string |  false   |
| active_for_proposal              |  string |  false   |
| remarks                          |  string |  false   |
| last_modified_by                 |  string |  false   |
| last_modified_at                 |  string |  false   |
| matched                          |  string |  false   |
| created_by                       |  string |  false   |
| created_at                       |  string |  false   |
| wish_emsd_contact_tel_2          |  string |  false   |
| wish_emsd_contact_post_title_eng |  string |  false   |
| wish_emsd_contact_post_title_chi |  string |  false   |

Response code :

| Response code | Description         |
|---------------|---------------------|
| 200           | Import wish success |
| 400           | Import wish fail    |

## INTPMIS Report {#intpmis-report .unnumbered}

<table>
<colgroup>
<col style="width: 66%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2">View Report</th>
</tr>
<tr class="odd">
<th><img src="media/image56.jpg"
style="width:4.15208in;height:1.98403in" /></th>
<th><p>1. Click “View” under “Report Managment”</p>
<p>2. Scroll down to view more reports</p></th>
</tr>
<tr class="header">
<th colspan="2">Print Report</th>
</tr>
<tr class="odd">
<th><img src="media/image45.png"
style="width:4.15208in;height:2.86389in" /></th>
<th><p>1. Select the period of the report</p>
<p>2. Select the other day for the report</p>
<p>3. Click “Confirm” button</p>
<p>4. The report is shown</p>
<p>5. Click “Print” to print all report</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

The system containing seven report, the report has different aspect to
analysis and show result of pass of the project, wish and solution.

### Trend of I&T Wishes, Solutions, and Matched Trial Projects Report {#trend-of-it-wishes-solutions-and-matched-trial-projects-report .unnumbered}

This report showed all number of the wishes, solution and match report
in a month, user can swich the bar of top to control system month for
view.

![](media/image57.png){width="5.770138888888889in"
height="2.186111111111111in"}

### Summary of I&T Wishes Report {#summary-of-it-wishes-report .unnumbered}

This Report showed number of the wish belong to a division, other type
means the wishes are create form the other department out of EMSD.

![](media/image49.png){width="5.770138888888889in"
height="0.8479166666666667in"}

![](media/image50.png){width="5.770138888888889in"
height="2.1465277777777776in"}

### Distribution of I&T Solutions by Technology Report {#distribution-of-it-solutions-by-technology-report .unnumbered}

This report grouped and counted number of all technology would be used
in the solution

![](media/image47.png){width="5.770138888888889in"
height="2.589583333333333in"}

![](media/image55.png){width="5.770138888888889in"
height="2.1638888888888888in"}

### Cash flow for Matched Trial Projects on E&M InnoPortal Report {#cash-flow-for-matched-trial-projects-on-em-innoportal-report .unnumbered}

This report would be show all division which total cash flow of match
projects in a year.

![](media/image4.png){width="5.770138888888889in" height="1.78125in"}

### Statistics on I&T Projects Report {#statistics-on-it-projects-report .unnumbered}

This report grouped all division and counted the project of the
division. Also, the project would be divides status of compute or
in-progress. There have two buttons of the report, Show All and Filter 0
items button.

Clicked Filter 0 items button, the system only show the division which
contain a project.

![](media/image53.png){width="5.770138888888889in"
height="3.2631944444444443in"}

Clicked Show All button, the system would display all the division which
contain a project.

![](media/image7.png){width="5.770138888888889in" height="2.6125in"}

### Statistics Technology on I&T Projects Report {#statistics-technology-on-it-projects-report .unnumbered}

This report would be counted and calculated the percentage of
technologies used in the projects.

![](media/image16.png){width="5.770138888888889in"
height="3.107638888888889in"}

### Expenditure on I&T Projects Report {#expenditure-on-it-projects-report .unnumbered}

This report would be summed the actual expenditure and project
expenditure of the projects in the year. Also, it would display
expenditure of a division.

![](media/image6.png){width="5.770138888888889in"
height="2.838888888888889in"}

# Users Procedures and Operation Manual

## Login to INTPMIS {#login-to-intpmis .unnumbered}

<table>
<colgroup>
<col style="width: 78%" />
<col style="width: 21%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2">SSO login</th>
</tr>
<tr class="odd">
<th colspan="2"><p>User gets an authentication ID from EMSD Active
Directory. Then the system will call LDAP API to get users
authentication code and information by the staff ID. </p>
<p>If login is successful, the landing page will be shown.</p>
<p>Otherwise, the user name login page will be shown.</p></th>
</tr>
<tr class="header">
<th colspan="2">User name login</th>
</tr>
<tr class="odd">
<th><img src="media/image13.png"
style="width:4.15208in;height:2.67222in" /></th>
<th><p>1. Open a browser (Internet Explorer/ Chrome)</p>
<p>2. Go to http://intpmis/#/login</p>
<p>3. Input email address and password </p>
<p>4. click "Sign In" button</p></th>
</tr>
<tr class="header">
<th><img src="media/image30.png"
style="width:4.15208in;height:2.03194in" /></th>
<th><p>Case 1: Login successfully</p>
<p>The page is navigated to the landing page</p></th>
</tr>
<tr class="odd">
<th><img src="media/image9.png"
style="width:5.77014in;height:2.84861in" /></th>
<th><p>Case 2: Login fail</p>
<p>The error prompt is shown.</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## Project {#project .unnumbered}

### Browsing Project List {#browsing-project-list .unnumbered}

<table>
<colgroup>
<col style="width: 66%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2">View Project</th>
</tr>
<tr class="odd">
<th><img src="media/image2.jpg"
style="width:4.15208in;height:2.07222in" /></th>
<th><p>1. Click “View” under “Project Management”</p>
<p>2. Scoll the bottom bar to the right to show the project
detail</p></th>
</tr>
<tr class="header">
<th colspan="2">Filter Project</th>
</tr>
<tr class="odd">
<th><img src="media/image10.png"
style="width:4.15208in;height:1.92778in" /></th>
<th><p>1. Input filter value</p>
<p>2. Select display number of record per page</p>
<p>3. The results are shown</p></th>
</tr>
<tr class="header">
<th colspan="2">Search Project</th>
</tr>
<tr class="odd">
<th><img src="media/image25.png"
style="width:4.15208in;height:2.42431in" /></th>
<th><p>1. Click search section</p>
<p>2. Select search criteria</p>
<p>3. Select values of criteria</p>
<p>4. Click “Search” button</p>
<p>5. The results are shown</p></th>
</tr>
<tr class="header">
<th colspan="2">Export Project</th>
</tr>
<tr class="odd">
<th><p><img src="media/image20.png"
style="width:4.15208in;height:2.32014in" /></p>
<p><img src="media/image5.png"
style="width:4.15208in;height:0.99167in" /></p></th>
<th><p>There are two options for exporting project</p>
<p>1. Export searched records</p>
<ul>
<li><blockquote>
<p>Click “Export Records” button </p>
</blockquote></li>
</ul>
<p>2. Export all records</p>
<ul>
<li><blockquote>
<p>Click “Export All Records” button</p>
</blockquote></li>
</ul>
<p>The exported results will be stored in a csv file</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

### Create a Project {#create-a-project .unnumbered}

<table>
<colgroup>
<col style="width: 66%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2">Create Project</th>
</tr>
<tr class="odd">
<th><img src="media/image22.jpg"
style="width:4.15208in;height:1.87986in" /></th>
<th>Click “Create” under “Project Management"</th>
</tr>
<tr class="header">
<th><img src="media/image8.png"
style="width:4.15208in;height:5.99167in" /></th>
<th><p>1. Fill the required fields</p>
<p>2. Click “Submit” button</p></th>
</tr>
<tr class="odd">
<th><img src="media/image14.png"
style="width:4.15208in;height:1.24028in" /></th>
<th><p>Case 1: Input field is not filled</p>
<p>The error message is shown under the field</p></th>
</tr>
<tr class="header">
<th><p><img src="media/image3.png"
style="width:4.15208in;height:2.03194in" /></p>
<p><img src="media/image1.png"
style="width:4.15208in;height:1.99167in" /></p></th>
<th><p>Case 2: Value is not valid</p>
<p>The error message is shown</p></th>
</tr>
<tr class="odd">
<th><p><img src="media/image12.png"
style="width:4.15208in;height:1.74375in" /></p>
<p><img src="media/image2.jpg"
style="width:4.15208in;height:2.07222in" /></p></th>
<th><p>Case 3: Project is created successfully</p>
<p>A successful message is shown with the project number</p>
<p>1. Click “X” to redirect to project view page</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

### Edit a Project {#edit-a-project .unnumbered}

<table>
<colgroup>
<col style="width: 84%" />
<col style="width: 15%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2">Edit Project</th>
</tr>
<tr class="odd">
<th><img src="media/image29.jpg"
style="width:4.15208in;height:2.04792in" /></th>
<th><p>1. Click “Edit” under “Project Management”</p>
<p>2. Click edit icon to edit the project</p></th>
</tr>
<tr class="header">
<th><img src="media/image26.png"
style="width:3.18555in;height:5.63194in" /></th>
<th><p>To edit information of the project, users can:</p>
<p>1. select completed</p>
<p>2. input values</p>
<p>3. empty input</p>
<p>Then click “Save All” button</p></th>
</tr>
<tr class="odd">
<th><img src="media/image24.png"
style="width:5.77014in;height:0.82562in" /></th>
<th><p>Case 1: Invalid input</p>
<p>The alert message is shown</p></th>
</tr>
<tr class="header">
<th><img src="media/image23.png"
style="width:5.77014in;height:0.86028in" /></th>
<th><p>Case 2: Save successfully</p>
<p>The successful message is shown</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## Wish List {#wish-list .unnumbered}

### Browsing Wish List {#browsing-wish-list .unnumbered}

<table>
<colgroup>
<col style="width: 66%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2">View Wish</th>
</tr>
<tr class="odd">
<th><img src="media/image34.jpg"
style="width:4.15208in;height:2.04028in" /></th>
<th><p>1. Click “View” under “Wish Management”</p>
<p>2. Scroll the bottom bar to right to view detail of the wish</p></th>
</tr>
<tr class="header">
<th colspan="2">Search Wish</th>
</tr>
<tr class="odd">
<th><img src="media/image33.png"
style="width:4.15208in;height:2.32014in" /></th>
<th><p>1. Click search section</p>
<p>2. Select search criteria</p>
<p>3. Select values of criteria</p>
<p>4. Click “Search” button</p>
<p>5. The results are shown</p></th>
</tr>
<tr class="header">
<th colspan="2">Filter Wish</th>
</tr>
<tr class="odd">
<th><img src="media/image31.png"
style="width:4.15208in;height:1.82431in" /></th>
<th><p>1. Input filter value</p>
<p>2. Select display number of record per page</p>
<p>3. The results are shown</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 66%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2">Export Wish</th>
</tr>
<tr class="odd">
<th><p><img src="media/image28.png"
style="width:4.15208in;height:2.32014in" /></p>
<p><img src="media/image51.png"
style="width:4.15208in;height:1.72014in" /></p></th>
<th><p>There are two options for exporting wish</p>
<p>1. Export searched records</p>
<ul>
<li><blockquote>
<p>Click “Export Records” button </p>
</blockquote></li>
</ul>
<p>2. Export all records</p>
<ul>
<li><blockquote>
<p>Click “Export All Records” button</p>
</blockquote></li>
</ul>
<p>The exported results will be stored in a csv file</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

### Edit a Wish {#edit-a-wish .unnumbered}

<table>
<colgroup>
<col style="width: 86%" />
<col style="width: 13%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2">Edit Wish</th>
</tr>
<tr class="odd">
<th><img src="media/image39.png"
style="width:4.15208in;height:4.86389in" /></th>
<th><p>1. Input value to edit</p>
<p>2. Click “Save All” button</p></th>
</tr>
<tr class="header">
<th><img src="media/image24.png"
style="width:5.77014in;height:0.89545in" /></th>
<th><p>Case 1: Invalid input</p>
<p>An alert message is shown</p></th>
</tr>
<tr class="odd">
<th><img src="media/image11.png"
style="width:5.59167in;height:0.84886in" /></th>
<th><p>Case 2: Wish is edited successfully</p>
<p>An alert message is shown</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## Solution List {#solution-list .unnumbered}

### Browsing Solution List {#browsing-solution-list .unnumbered}

<table>
<colgroup>
<col style="width: 66%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2">View Solution</th>
</tr>
<tr class="odd">
<th><img src="media/image32.jpg"
style="width:4.15208in;height:1.96806in" /></th>
<th><p>1. Click “View” under “Solution  Management”</p>
<p>2. Scroll the bottom bar to right to view detail of the
solution</p></th>
</tr>
<tr class="header">
<th colspan="2">Search Solution</th>
</tr>
<tr class="odd">
<th><img src="media/image44.png"
style="width:4.15208in;height:2.41597in" /></th>
<th><p>1. Click search section</p>
<p>2. Select search criteria</p>
<p>3. Select values of criteria</p>
<p>4. Click “Search” button</p>
<p>5. The results are shown</p></th>
</tr>
<tr class="header">
<th colspan="2">Filter Solution</th>
</tr>
<tr class="odd">
<th><img src="media/image15.png"
style="width:4.15208in;height:1.82431in" /></th>
<th><p>1. Input filter value</p>
<p>2. Select display number of record per page</p>
<p>3. The results are shown</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

<table>
<colgroup>
<col style="width: 66%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2">Export Solution</th>
</tr>
<tr class="odd">
<th><img src="media/image36.png"
style="width:4.15208in;height:2.41597in" /></th>
<th><p>There are two options for exporting solution</p>
<p>1. Export searched records</p>
<ul>
<li><blockquote>
<p>Click “Export Records” button </p>
</blockquote></li>
</ul>
<p>2. Export all records</p>
<ul>
<li><blockquote>
<p>Click “Export All Records” button</p>
</blockquote></li>
</ul>
<p>The exported results will be stored in a csv file</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

### Edit a Solution {#edit-a-solution .unnumbered}

<table>
<colgroup>
<col style="width: 86%" />
<col style="width: 13%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2">Edit Solution</th>
</tr>
<tr class="odd">
<th><img src="media/image18.png"
style="width:4.15208in;height:3.92014in" /></th>
<th><p>1. Input value to edit</p>
<p>2. Click “Save All” button</p></th>
</tr>
<tr class="header">
<th><img src="media/image24.png"
style="width:5.77014in;height:0.70938in" /></th>
<th><p>Case 1: Invalid input</p>
<p>An alert message is shown</p></th>
</tr>
<tr class="odd">
<th><img src="media/image27.png"
style="width:5.75972in;height:0.84891in" /></th>
<th><p>Case 2: Solution is edited successfully</p>
<p>An alert message is shown</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

# Administrator Procedures and Operation Manual

## Project {#project-1 .unnumbered}

### Edit a Project {#edit-a-project-1 .unnumbered}

<table>
<colgroup>
<col style="width: 66%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2">Edit Project</th>
</tr>
<tr class="odd">
<th><img src="media/image21.png"
style="width:4.15208in;height:6.51181in" /></th>
<th><p>** Admin (Role 6) allowed edit more different fields, such as
Date of Uploading Interim Evaluation Report</p>
<p>To edit information of the project, users can:</p>
<p>1. select completed</p>
<p>2. input values</p>
<p>3. empty input</p>
<p>Then click “Save All” button</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

## Log List {#log-list .unnumbered}

### Browsing Log List {#browsing-log-list .unnumbered}

<table>
<colgroup>
<col style="width: 66%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th colspan="2">View and Export Log</th>
</tr>
<tr class="odd">
<th><img src="media/image19.png"
style="width:4.15208in;height:1.92778in" /></th>
<th><p>1. Select tag type of log</p>
<p>2. Log records are shown in list</p>
<p>3. Click “+” button to view log detail</p>
<p>4. Click “Export Records” button to export records to a csv
file</p></th>
</tr>
<tr class="header">
<th colspan="2">Cancel Reminder</th>
</tr>
<tr class="odd">
<th><img src="media/image17.png"
style="width:4.15208in;height:1.92778in" /></th>
<th><p>There are two options to cancel reminder(s):</p>
<p>1. Click checked button to cancel the reminder of a record</p>
<p>2. Select multiple records and click batch checked to cancel reminder
of selected records</p></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

Training courses and user experience session

Program Manual including workflow manual

System manual

User procedures manual

Search Function

![](media/image43.png){width="5.823846237970254in"
height="1.7508781714785653in"}

User can search project, wish or solution by used search function. The
function allow user to select one or more special search criteria which
are fields of the object. After user select criteria, that would be
display in below and have all value possible in that fields allow user
to search. When user complete the form of search. By click search
button, the system would display all object which are satisfy the
criteria in below table.

Search Function (report)

![](media/image37.png){width="5.756944444444445in"
height="1.2020833333333334in"}

The search function in the report, system allow user selecting a month,
then start date and end date would be auto assign in to filed. After
click Confirm button, system would be display report to below, that data
a during in the selected month.

Export Function

![](media/image40.png){width="5.75in" height="2.96875in"}

![](media/image46.png){width="5.768055555555556in"
height="0.8791666666666667in"}

User can export all records after search in the table by clicked Export
Records Button. The system would save all records to a csv file to user
local file.

Printing Report Function

![](media/image52.png){width="5.768055555555556in"
height="3.792361111111111in"}

System allow user to printing all report by click the Print button,
which in the right side of report search function. Then the system would
be pop up a preview page for user adjust the printing setting.

Create Project

<table>
<colgroup>
<col style="width: 24%" />
<col style="width: 16%" />
<col style="width: 11%" />
<col style="width: 46%" />
</colgroup>
<thead>
<tr class="header">
<th>Fields</th>
<th>Input Type</th>
<th>Require</th>
<th>Remark</th>
</tr>
<tr class="odd">
<th>Matched Through</th>
<th>select</th>
<th>yes</th>
<th>If user select Non-E&amp;M InnoPortal, Wish No, Solution No, Same
Person with Wish Proposer (Y/N) would be hidden</th>
</tr>
<tr class="header">
<th>Project Title</th>
<th>text</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Project Image</th>
<th>file</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>Wish No</th>
<th>number</th>
<th>no</th>
<th></th>
</tr>
<tr class="odd">
<th>Solution No</th>
<th>number</th>
<th>no</th>
<th></th>
</tr>
<tr class="header">
<th>Same Person with Wish Proposer (Y/N)</th>
<th>select</th>
<th>no</th>
<th>If click yes in Same Person with wish proposer (Y/N) field, all
field in Subject Officer and InnoTeam Related Information auto assign
that wish value, exclude InnoTeam (Y/N) field</th>
</tr>
<tr class="odd">
<th>Client Department</th>
<th>select</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>EMSTF/ RS</th>
<th>select</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Branch</th>
<th>select</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>Division</th>
<th>select</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Sub-Division</th>
<th>select</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>Subject Officer (Eng)</th>
<th>text</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Subject Officer (Chi)</th>
<th>text</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>Post</th>
<th>text</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Full Post (Eng)</th>
<th>text</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>Full Post (Chi)</th>
<th>text</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Email</th>
<th>email</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>Tel</th>
<th>number (max 20 digital)</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Tel 2</th>
<th>number (max 20 digital)</th>
<th>no</th>
<th></th>
</tr>
<tr class="header">
<th>InnoTeam (Y/N)</th>
<th>select</th>
<th>yes</th>
<th>If Click No in InnoTeam (Y/N) field, Round of InnoTeam, InnoTeam
Number , InnoTeam Proposal Title would hidden</th>
</tr>
<tr class="odd">
<th>Round of InnoTeam</th>
<th>text</th>
<th>no</th>
<th></th>
</tr>
<tr class="header">
<th>InnoTeam Number</th>
<th>text</th>
<th>no</th>
<th></th>
</tr>
<tr class="odd">
<th>InnoTeam Proposal Title</th>
<th>text</th>
<th>no</th>
<th></th>
</tr>
<tr class="header">
<th>Testing Grounds</th>
<th>text</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Trial Scale</th>
<th>text</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>Percentage of completion</th>
<th>number</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Monetary benefits</th>
<th>text</th>
<th>no</th>
<th></th>
</tr>
<tr class="header">
<th>Project Status</th>
<th>select</th>
<th>yes</th>
<th>If select Completed of Project Status field, Annual Return,
Investment per year, System Life Expectancy fields will be required for
create new project</th>
</tr>
<tr class="odd">
<th>Annual Return</th>
<th>number</th>
<th>no</th>
<th></th>
</tr>
<tr class="header">
<th>Investment per year</th>
<th>number</th>
<th>no</th>
<th></th>
</tr>
<tr class="odd">
<th>System Life Expectancy</th>
<th>number</th>
<th>no</th>
<th></th>
</tr>
<tr class="header">
<th>Remarks</th>
<th>text</th>
<th>no</th>
<th></th>
</tr>
<tr class="odd">
<th>PO issued (Y/NA)</th>
<th>select</th>
<th>yes</th>
<th>User Max can input three PO No. for a project</th>
</tr>
<tr class="header">
<th>PO No.</th>
<th>number</th>
<th>no</th>
<th></th>
</tr>
<tr class="odd">
<th>PO No. 2</th>
<th>number</th>
<th>no</th>
<th></th>
</tr>
<tr class="header">
<th>PO No. 3</th>
<th>number</th>
<th>no</th>
<th></th>
</tr>
<tr class="odd">
<th>Project Sum(HK$)</th>
<th>number</th>
<th>yes</th>
<th>The Project Sum would be same with sum all expenditure</th>
</tr>
<tr class="header">
<th>Anticipated/ Actual Contract Start Date</th>
<th>date</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Anticipated/ Actual Contract Completion Date (mm/yyyy)</th>
<th>date</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>Actual Expenditure in FY17/18</th>
<th>number</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Actual Expenditure in FY18/19</th>
<th>number</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>Actual Expenditure in FY19/20</th>
<th>number</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Actual Expenditure in FY20/21</th>
<th>number</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>Projected Expenditure in FY20/21</th>
<th>number</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Projected Expenditure in FY21/22</th>
<th>number</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>Projected Expenditure in FY22/23</th>
<th>number</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Expenditure in Remaining FY(s)</th>
<th>number</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>Funding Type</th>
<th>select</th>
<th>yes</th>
<th>If the Funding Type is Cost Center, user new to input cost center
number.<br />
If the Funding Type is Other, user need to special input the funding
type.<br />
If the Funding Type is ITF, ITF Scheme Applied, ITF Scheme Status, ITF
Project Ref, Year of Support need to input for new project.</th>
</tr>
<tr class="odd">
<th>ITF Scheme Applied</th>
<th>select</th>
<th>no</th>
<th></th>
</tr>
<tr class="header">
<th>ITF Scheme Status</th>
<th>select</th>
<th>no</th>
<th></th>
</tr>
<tr class="odd">
<th>ITF Project Ref</th>
<th>text</th>
<th>no</th>
<th></th>
</tr>
<tr class="header">
<th>Year of Support</th>
<th>select</th>
<th>no</th>
<th></th>
</tr>
<tr class="odd">
<th>Submission of Interim Report</th>
<th>select</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>Submission of MnV Report</th>
<th>select</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Interim Report</th>
<th>file</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>MnV Report</th>
<th>file</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Date of uploading Interim Report</th>
<th>date</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>Date of uploading MnV Report</th>
<th>date</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Upload of Interim Report</th>
<th>select</th>
<th>yes</th>
<th></th>
</tr>
<tr class="header">
<th>Upload of MnV Report</th>
<th>select</th>
<th>yes</th>
<th></th>
</tr>
<tr class="odd">
<th>Funding Type (Others)</th>
<th>text</th>
<th>no</th>
<th></th>
</tr>
<tr class="header">
<th>Cost Center Number</th>
<th>number</th>
<th>no</th>
<th></th>
</tr>
</thead>
<tbody>
</tbody>
</table>

Administrator Procedures Manual

Logging

![](media/image35.png){width="5.759722222222222in"
height="1.679861111111111in"}

In the logging page. User can check all log record of report, wish or
solution. They can select tag he/she wanted to check. After a user
create or edit an object, the system would be created log record. In the
table all log record would be have a reminder field to remind user that
record is new or need to be check. If the user is wants to cancel the
remind of a record, he/she can click Checked button in that record, then
the system would hidden the reminder of that record. User can also
select more than one log records and click Batch Checked button to
cancel a list reminder of the records.

![](media/image42.png){width="5.75625in"
height="1.8520833333333333in"}User can click + button to checking the
detail of the log record. That record would drow down a view to present
log detail. Different type of the log would be display different layout
of the detail.
