# Chapter Four – Figures (Text Version)

Text descriptions and layouts for Figures 4.1 – 4.5 of the
Centralized Web-Based Student Clearance System.

---

## Figure 4.1: System Architecture of the Proposed Centralized Web-Based Student Clearance System

```
+=====================================================================+
|                        PRESENTATION LAYER (Client)                  |
|                                                                     |
|   +-------------+   +------------------+   +---------------------+  |
|   |   Student   |   | Departmental     |   | Registry            |  |
|   |   Portal    |   | Officer Portal   |   | Administrator Portal|  |
|   | (Web Browser)|  | (Web Browser)    |   | (Web Browser)       |  |
|   +------+------+   +--------+---------+   +----------+----------+  |
+==========|===================|========================|=============+
           |        HTTPS Requests / Responses          |
           v                   v                        v
+=====================================================================+
|                   APPLICATION LAYER (Web Server)                    |
|                                                                     |
|  +----------------+  +-----------------+  +----------------------+  |
|  | Authentication |  | Clearance       |  | Approval / Rejection |  |
|  | & Role Access  |  | Request Module  |  | Module (Officers)    |  |
|  +----------------+  +-----------------+  +----------------------+  |
|  +----------------+  +-----------------+  +----------------------+  |
|  | Notification   |  | Report &        |  | User & Department    |  |
|  | Module         |  | Certificate Gen.|  | Management (Admin)   |  |
|  +----------------+  +-----------------+  +----------------------+  |
+===================================|=================================+
                                    |  SQL Queries
                                    v
+=====================================================================+
|                        DATA LAYER (Database Server)                 |
|                                                                     |
|   +-----------+ +-------------+ +-------------+ +----------------+  |
|   | Students  | | Officers /  | | Clearance   | | Departments /  |  |
|   | Table     | | Users Table | | Records     | | Units Table    |  |
|   +-----------+ +-------------+ +-------------+ +----------------+  |
+=====================================================================+
```

**Description:** The system follows a three-tier architecture. The
Presentation Layer consists of three web portals (Student, Departmental
Officer and Registry Administrator) accessed through a web browser. All
requests pass over HTTPS to the Application Layer, which handles
authentication and role-based access, submission of clearance requests,
approval/rejection by officers, notifications, report/certificate
generation and user management. The Application Layer reads from and
writes to a central relational database in the Data Layer, which stores
student records, officer accounts, clearance records and departmental
units.

---

## Figure 4.2: Screenshot Showing Student Login Page

```
+---------------------------------------------------------------+
|  [University Logo]   STUDENT CLEARANCE SYSTEM                 |
+---------------------------------------------------------------+
|                                                               |
|                 +-------------------------------+             |
|                 |         STUDENT LOGIN         |             |
|                 |                               |             |
|                 |  Matriculation Number         |             |
|                 |  [ e.g. CSC/2020/001        ] |             |
|                 |                               |             |
|                 |  Password                     |             |
|                 |  [ ********                 ] |             |
|                 |                               |             |
|                 |  [ ] Remember me              |             |
|                 |                               |             |
|                 |        [   LOGIN   ]          |             |
|                 |                               |             |
|                 |  Forgot password?             |             |
|                 |  Staff / Officer Login  >>    |             |
|                 +-------------------------------+             |
|                                                               |
+---------------------------------------------------------------+
|        (c) 2025 Student Clearance System. All rights reserved.|
+---------------------------------------------------------------+
```

**Description:** The login page is the entry point for students. The
student enters their Matriculation Number and Password and clicks
**LOGIN**. The system validates the credentials against the database and,
if they are correct, redirects the student to the Clearance Status
Dashboard. If they are wrong, an error message ("Invalid matriculation
number or password") is shown. Links are provided for password recovery
and for staff/officer login.

---

## Figure 4.3: Screenshot Showing Student Clearance Status Dashboard

```
+-----------------------------------------------------------------------+
| [Logo] STUDENT CLEARANCE SYSTEM        Welcome, John Doe | [Logout]   |
+----------------+------------------------------------------------------+
| > Dashboard    |  CLEARANCE STATUS DASHBOARD                          |
|   My Profile   |                                                      |
|   Apply for    |  Name: John Doe         Matric No: CSC/2020/001      |
|   Clearance    |  Department: Computer Science   Session: 2024/2025   |
|   Upload Docs  |                                                      |
|   Notifications|  Overall Progress:  [#########.........]  4 of 7     |
|   Print        |                                                      |
|   Certificate  |  +-----+----------------------+-----------+--------+ |
|   Logout       |  | S/N | Unit / Office        | Status    | Remark | |
|                |  +-----+----------------------+-----------+--------+ |
|                |  |  1  | Department (HOD)     | APPROVED  |   -    | |
|                |  |  2  | Faculty Office       | APPROVED  |   -    | |
|                |  |  3  | Library              | APPROVED  |   -    | |
|                |  |  4  | Bursary              | APPROVED  |   -    | |
|                |  |  5  | Hostel / Student     | PENDING   |   -    | |
|                |  |     | Affairs              |           |        | |
|                |  |  6  | Sports Unit          | REJECTED  | Return | |
|                |  |     |                      |           | jersey | |
|                |  |  7  | Registry (Final)     | PENDING   |   -    | |
|                |  +-----+----------------------+-----------+--------+ |
|                |                                                      |
|                |  [ Print Clearance Certificate ] (enabled when all   |
|                |                                   units approve)     |
+----------------+------------------------------------------------------+
```

**Description:** After logging in, the student sees the dashboard. The
left sidebar has the menu (Dashboard, My Profile, Apply for Clearance,
Upload Documents, Notifications, Print Certificate, Logout). The main
area shows the student's details, a progress bar, and a table listing
each clearance unit with its status: **Approved** (green), **Pending**
(yellow) or **Rejected** (red), along with any remark from the officer.
The student can see which office is holding up their clearance and why.
The **Print Clearance Certificate** button is enabled only after every
unit, including the Registry, has approved.

---

## Figure 4.4: Screenshot Showing Departmental Officer Approval Interface

```
+-----------------------------------------------------------------------+
| [Logo] CLEARANCE SYSTEM - OFFICER    Library Officer: Mrs. A. Bello   |
|                                                          [Logout]     |
+----------------+------------------------------------------------------+
| > Pending      |  PENDING CLEARANCE REQUESTS - LIBRARY UNIT           |
|   Requests     |                                                      |
|   Approved     |  Search: [ Matric No / Name      ] [Search]          |
|   Rejected     |  Filter: [ All Departments  v ]                      |
|   Reports      |                                                      |
|   Profile      |  +----+-------------+-----------+--------+---------+ |
|   Logout       |  |S/N | Matric No   | Name      | Dept   | Action  | |
|                |  +----+-------------+-----------+--------+---------+ |
|                |  | 1  | CSC/2020/001| John Doe  | CSC    | [View]  | |
|                |  |    |             |           |        |[Approve]| |
|                |  |    |             |           |        |[Reject] | |
|                |  +----+-------------+-----------+--------+---------+ |
|                |  | 2  | MTH/2020/014| Ada Obi   | MTH    | [View]  | |
|                |  |    |             |           |        |[Approve]| |
|                |  |    |             |           |        |[Reject] | |
|                |  +----+-------------+-----------+--------+---------+ |
|                |                                                      |
|                |  Remark (required if rejecting):                     |
|                |  [ e.g. Outstanding library book not returned     ]  |
|                |                                                      |
|                |  Summary:  Pending: 12 | Approved: 85 | Rejected: 3  |
+----------------+------------------------------------------------------+
```

**Description:** Each departmental officer (e.g. Library, Bursary,
Hostel, Sports, HOD) logs into their own portal and sees only the
requests meant for their unit. The table lists students awaiting
clearance with their matric number, name and department. For each
student the officer can **View** submitted details/documents, **Approve**
the request, or **Reject** it with a remark stating the reason. The
decision is saved to the database immediately and the student's
dashboard is updated. A summary bar shows the number of pending, approved
and rejected requests.

---

## Figure 4.5: Screenshot Showing Registry Administrator Dashboard

```
+-----------------------------------------------------------------------+
| [Logo] CLEARANCE SYSTEM - REGISTRY ADMIN       Admin: Registrar      |
|                                                          [Logout]     |
+----------------+------------------------------------------------------+
| > Dashboard    |  REGISTRY ADMINISTRATOR DASHBOARD                    |
|   Manage       |                                                      |
|   Students     |  +-----------+ +-----------+ +---------+ +---------+ |
|   Manage       |  | Total     | | Fully     | | Pending | |Rejected | |
|   Officers     |  | Students  | | Cleared   | |         | |         | |
|   Manage Units |  |   1,250   | |    830    | |   395   | |   25    | |
|   Final        |  +-----------+ +-----------+ +---------+ +---------+ |
|   Approval     |                                                      |
|   Reports      |  STUDENTS AWAITING FINAL REGISTRY APPROVAL           |
|   Settings     |  +----+-------------+-----------+-------+----------+ |
|   Logout       |  |S/N | Matric No   | Name      | Units | Action   | |
|                |  +----+-------------+-----------+-------+----------+ |
|                |  | 1  | CSC/2020/005| Musa Ali  | 6/6   | [Final   | |
|                |  |    |             |           |       | Approve] | |
|                |  | 2  | BIO/2020/021| Grace Eze | 6/6   | [Final   | |
|                |  |    |             |           |       | Approve] | |
|                |  +----+-------------+-----------+-------+----------+ |
|                |                                                      |
|                |  Clearance by Department (bar chart)                 |
|                |  CSC  |##########          |                         |
|                |  MTH  |#######             |                         |
|                |  BIO  |#########           |                         |
|                |  PHY  |#####               |                         |
|                |                                                      |
|                |  [ Generate Report (PDF) ]  [ Export to Excel ]      |
+----------------+------------------------------------------------------+
```

**Description:** The Registry Administrator has the highest level of
access. The dashboard shows summary cards (total students, fully cleared,
pending, rejected), a list of students who have been approved by all
units and are waiting for final Registry approval, and a chart of
clearance progress by department. From the sidebar the administrator can
manage student and officer accounts, add or edit clearance units, give
final approval (which unlocks the student's clearance certificate), and
generate or export reports.
