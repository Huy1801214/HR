```mermaid
flowchart LR

    %% =====================================================
    %% CENTER
    %% =====================================================

    HR["HR Platform"]

    %% =====================================================
    %% LEFT SIDE — MAIN MODULES (4 MODULES)
    %% =====================================================

    CORE["Core HR"] --- HR
    RECRUITMENT["Recruitment & Onboarding"] --- HR
    GOVERNANCE["Platform & Governance"] --- HR
    ANALYTICS["Analytics & AI"] --- HR

    %% =====================================================
    %% CORE HR
    %% =====================================================

    ORGANIZATION["Organization & Access"] --- CORE
    EMPLOYEE_INFO["Employee Information"] --- CORE
    EXPERIENCE["Employee Experience"] --- CORE
    PERFORMANCE["Performance & Goals"] --- CORE

    OA1["Organization Structure"] --- ORGANIZATION
    OA2["User Account Management"] --- ORGANIZATION
    OA3["Role & Permission Management"] --- ORGANIZATION

    EI1["Employee Records & Directory"] --- EMPLOYEE_INFO
    EI2["Employee Documents"] --- EMPLOYEE_INFO
    EI3["Data Change History"] --- EMPLOYEE_INFO

    EE1["Engagement & Wellbeing Surveys"] --- EXPERIENCE
    EE2["Recognition & Rewards"] --- EXPERIENCE
    EE3["Internal Announcements"] --- EXPERIENCE

    PG1["Goal Tracking & 1-on-1s"] --- PERFORMANCE
    PG2["Self & Manager Assessments"] --- PERFORMANCE
    PG3["360 Feedback & Performance Reviews"] --- PERFORMANCE

    %% =====================================================
    %% RECRUITMENT & ONBOARDING
    %% =====================================================

    HIRING["Hiring & ATS"] --- RECRUITMENT
    ONBOARDING["Onboarding & Offboarding"] --- RECRUITMENT

    HA1["Job Opening Management"] --- HIRING
    HA2["Candidate Pipeline & Interviews"] --- HIRING
    HA3["Candidate Evaluation"] --- HIRING
    HA4["Offer Management"] --- HIRING

    OO1["New-Hire Information Collection"] --- ONBOARDING
    OO2["Onboarding Checklists"] --- ONBOARDING
    OO3["Electronic Signatures"] --- ONBOARDING
    OO4["Access & Equipment Recovery"] --- ONBOARDING

    %% =====================================================
    %% PLATFORM & GOVERNANCE
    %% =====================================================

    COMPLIANCE["Compliance & Security"] --- GOVERNANCE
    INTEGRATIONS["Integrations & Workflows"] --- GOVERNANCE

    CS1["Secure Authentication, 2FA & SSO"] --- COMPLIANCE
    CS2["Role-Based Access Control"] --- COMPLIANCE
    CS3["Privacy & Audit Logs"] --- COMPLIANCE

    IW1["Public API & Webhooks"] --- INTEGRATIONS
    IW2["Payroll & Accounting Integrations"] --- INTEGRATIONS
    IW3["Multi-Level Approval Engine"] --- INTEGRATIONS
    IW4["Dashboards & Notifications"] --- INTEGRATIONS

    %% =====================================================
    %% ANALYTICS & AI
    %% =====================================================

    REPORTING["Reporting & Analytics"] --- ANALYTICS
    INTELLIGENCE["HR Intelligence & AI"] --- ANALYTICS

    RA1["HR & Recruitment Reports"] --- REPORTING
    RA2["Time, Attendance & Cost Reports"] --- REPORTING
    RA3["Custom Dashboards & Export"] --- REPORTING

    AI1["Natural Language Questions"] --- INTELLIGENCE
    AI2["Policy & Document Search"] --- INTELLIGENCE
    AI3["Workforce Trend & Anomaly Detection"] --- INTELLIGENCE
    AI4["Data-Driven Recommendations"] --- INTELLIGENCE

    %% =====================================================
    %% RIGHT SIDE — MAIN MODULES (3 MODULES)
    %% =====================================================

    HR --- TIME["Time & Attendance"]
    HR --- TRACKING["Workforce Tracking"]
    HR --- PAYROLL["Payroll & Benefits"]

    %% =====================================================
    %% TIME & ATTENDANCE
    %% =====================================================

    TIME --- ATTENDANCE["Attendance Management"]
    TIME --- TIME_TRACKING["Time Tracking"]
    TIME --- SCHEDULING["Scheduling"]
    TIME --- LEAVE["Leave Management"]

    ATTENDANCE --- AM1["Clock In & Clock Out"]
    ATTENDANCE --- AM2["Late & Absence Detection"]
    ATTENDANCE --- AM3["Paid & Unpaid Breaks"]
    ATTENDANCE --- AM4["Overtime Calculation & Approval"]

    TIME_TRACKING --- TT1["Start & Stop Timers"]
    TIME_TRACKING --- TT2["Project & Task Tracking"]
    TIME_TRACKING --- TT3["Manual & Offline Time"]
    TIME_TRACKING --- TT4["Billable & Non-Billable Rules"]

    SCHEDULING --- SC1["Work Shifts & Team Assignment"]
    SCHEDULING --- SC2["Recurring Schedules"]
    SCHEDULING --- SC3["Schedule Conflict Detection"]

    LEAVE --- LM1["Time-Off Policies & Balances"]
    LEAVE --- LM2["Leave Requests & Approvals"]
    LEAVE --- LM3["Holiday Calendar"]

    %% =====================================================
    %% WORKFORCE TRACKING
    %% =====================================================

    TRACKING --- ACTIVITY["Activity & Productivity"]
    TRACKING --- LOCATION["Location & Field Operations"]

    ACTIVITY --- AP1["Keyboard & Mouse Activity"]
    ACTIVITY --- AP2["Screenshot Capture"]
    ACTIVITY --- AP3["Application & Website Tracking"]
    ACTIVITY --- AP4["Idle Time & Focus Analysis"]

    LOCATION --- LF1["Real-Time GPS Tracking"]
    LOCATION --- LF2["Location & Route History"]
    LOCATION --- LF3["Geofence Clock-In"]
    LOCATION --- LF4["Field Attendance Tracking"]

    %% =====================================================
    %% PAYROLL & BENEFITS
    %% =====================================================

    PAYROLL --- PAYROLL_PROCESS["Payroll Processing"]
    PAYROLL --- COMPENSATION["Compensation & Benefits"]
    PAYROLL --- BILLING["Client Billing & Expenses"]

    PAYROLL_PROCESS --- PP1["Pay Rates & Hourly/Salary Pay"]
    PAYROLL_PROCESS --- PP2["Payroll from Approved Timesheets"]
    PAYROLL_PROCESS --- PP3["Payroll Tax & Direct Deposit"]
    PAYROLL_PROCESS --- PP4["Payroll History"]

    COMPENSATION --- CB1["Salary Bands & Reviews"]
    COMPENSATION --- CB2["Benefit Plan Eligibility"]
    COMPENSATION --- CB3["Open & New-Hire Enrollment"]

    BILLING --- BE1["Billable Hours & Rates"]
    BILLING --- BE2["Invoice Generation & Delivery"]
    BILLING --- BE3["Expense Reimbursement & Invoicing"]

    %% =====================================================
    %% STYLES BY LAYER & HIGHLIGHTS
    %% =====================================================

    classDef center fill:#0f172a,stroke:#38bdf8,stroke-width:4px,color:#ffffff,font-weight:bold;
    classDef layer1 fill:#2563eb,stroke:#1d4ed8,stroke-width:3px,color:#ffffff,font-weight:bold;
    classDef highlightLayer1 fill:#f59e0b,stroke:#b45309,stroke-width:4px,color:#ffffff,font-weight:bold;
    classDef layer2 fill:#dbeafe,stroke:#3b82f6,stroke-width:2px,color:#1e293b,font-weight:bold;
    classDef layer3 fill:#ffffff,stroke:#94a3b8,stroke-width:1px,color:#334155;

    class HR center;

    class CORE,TIME highlightLayer1;
    class RECRUITMENT,GOVERNANCE,ANALYTICS,TRACKING,PAYROLL layer1;

    class ORGANIZATION,EMPLOYEE_INFO,EXPERIENCE,PERFORMANCE,HIRING,ONBOARDING,COMPLIANCE,INTEGRATIONS,REPORTING,INTELLIGENCE,ATTENDANCE,TIME_TRACKING,SCHEDULING,LEAVE,ACTIVITY,LOCATION,PAYROLL_PROCESS,COMPENSATION,BILLING layer2;

    class OA1,OA2,OA3,EI1,EI2,EI3,EE1,EE2,EE3,PG1,PG2,PG3,HA1,HA2,HA3,HA4,OO1,OO2,OO3,OO4,CS1,CS2,CS3,IW1,IW2,IW3,IW4,RA1,RA2,RA3,AI1,AI2,AI3,AI4,AM1,AM2,AM3,AM4,TT1,TT2,TT3,TT4,SC1,SC2,SC3,LM1,LM2,LM3,AP1,AP2,AP3,AP4,LF1,LF2,LF3,LF4,PP1,PP2,PP3,PP4,CB1,CB2,CB3,BE1,BE2,BE3 layer3;
```

## Use Case Catalogue

| No. | Use Case ID | Module | Feature Group | High-Level Use Case | Actors | Functional Description |
|---:|---|---|---|---|---|---|
| 1 | UC-CORE-01 | Core HR | Organization & Access | Manage Organization Structure | Employee; Manager; HR Staff | Create and manage departments, teams, positions, job titles, reporting lines, and the organizational chart. |
| 2 | UC-CORE-02 | Core HR | Organization & Access | Manage User Accounts | Employee; HR Staff; System Administrator | Create, activate, deactivate, unlock, and recover user accounts. |
| 3 | UC-CORE-03 | Core HR | Organization & Access | Manage Roles and Permissions | HR Staff; System Administrator | Create roles, assign permissions, and configure data-access scopes. |
| 4 | UC-CORE-04 | Core HR | Employee Information | Manage Employee Records and Directory | Employee; Manager; HR Staff | Create, view, update, search, archive, and manage employee records. |
| 5 | UC-CORE-05 | Core HR | Employee Information | Manage Employee Documents | Employee; HR Staff; External System | Upload, classify, electronically sign, track, and store employee documents. |
| 6 | UC-CORE-06 | Core HR | Employee Information | View Employee Data Change History | Manager; HR Staff | Track data changes, the user who made each change, and the time of modification. |
| 7 | UC-CORE-07 | Core HR | Employee Experience | Manage Engagement and Wellbeing Surveys | Employee; Manager; HR Staff | Create surveys, distribute them, collect responses, and analyze engagement and wellbeing. |
| 8 | UC-CORE-08 | Core HR | Employee Experience | Manage Recognition and Rewards | Employee; Manager; HR Staff | Recognize contributions, nominate employees, approve rewards, and manage recognition records. |
| 9 | UC-CORE-09 | Core HR | Employee Experience | Manage Internal Announcements | Employee; HR Staff; External System | Create, approve, publish, and distribute internal announcements. |
| 10 | UC-CORE-10 | Core HR | Performance & Goals | Manage Goals and One-on-One Meetings | Employee; Manager; HR Staff | Create goals, update progress, schedule one-on-one meetings, and manage follow-up actions. |
| 11 | UC-CORE-11 | Core HR | Performance & Goals | Manage Self and Manager Assessments | Employee; Manager; HR Staff | Configure and complete self-assessments and manager assessments. |
| 12 | UC-CORE-12 | Core HR | Performance & Goals | Manage 360-Degree Feedback and Performance Reviews | Employee; Manager; HR Staff | Collect multi-source feedback, conduct review cycles, and publish performance results. |
| 13 | UC-REC-01 | Recruitment & Onboarding | Hiring & ATS | Manage Job Openings | Recruiter; Manager; HR Staff | Create, update, approve, publish, close, and archive job openings. |
| 14 | UC-REC-02 | Recruitment & Onboarding | Hiring & ATS | Manage Candidate Pipeline and Interviews | Candidate / New Hire; Recruiter; Manager | Receive applications, move candidates through the pipeline, and schedule interviews. |
| 15 | UC-REC-03 | Recruitment & Onboarding | Hiring & ATS | Evaluate Candidates | Recruiter; Manager | Score candidates, record feedback, compare candidates, and support hiring decisions. |
| 16 | UC-REC-04 | Recruitment & Onboarding | Hiring & ATS | Manage Job Offers | Candidate / New Hire; Recruiter; Manager; HR Staff; External System | Create, approve, send, sign, accept, reject, and track job offers. |
| 17 | UC-REC-05 | Recruitment & Onboarding | Onboarding & Offboarding | Collect New-Hire Information | Candidate / New Hire; HR Staff | Collect personal, banking, tax, emergency-contact, and required employment information. |
| 18 | UC-REC-06 | Recruitment & Onboarding | Onboarding & Offboarding | Manage Onboarding Checklists | Candidate / New Hire; Manager; HR Staff; System Administrator | Create onboarding checklists, assign tasks, and track onboarding progress. |
| 19 | UC-REC-07 | Recruitment & Onboarding | Onboarding & Offboarding | Manage Electronic Signatures | Candidate / New Hire; HR Staff; External System | Send documents for signing, verify the signer, record signatures, and track signature status. |
| 20 | UC-REC-08 | Recruitment & Onboarding | Onboarding & Offboarding | Recover Employee Access and Equipment | Employee; Manager; HR Staff; System Administrator | Revoke accounts, recover equipment, remove access, and track offboarding completion. |
| 21 | UC-GOV-01 | Platform & Governance | Compliance & Security | Authenticate Users with 2FA and SSO | Employee; Manager; HR Staff; Recruiter; Payroll / Finance Staff; System Administrator; External System | Authenticate users with passwords, two-factor authentication, or single sign-on. |
| 22 | UC-GOV-02 | Platform & Governance | Compliance & Security | Manage Role-Based Access Control | HR Staff; System Administrator | Manage roles, permissions, access scopes, and RBAC assignments. |
| 23 | UC-GOV-03 | Platform & Governance | Compliance & Security | Manage Privacy and Audit Logs | HR Staff; System Administrator | Record audit logs, monitor access, support privacy controls, and enable compliance reviews. |
| 24 | UC-GOV-04 | Platform & Governance | Integrations & Workflows | Manage Public APIs and Webhooks | System Administrator; External System | Configure API keys, endpoints, webhooks, events, and integration monitoring. |
| 25 | UC-GOV-05 | Platform & Governance | Integrations & Workflows | Integrate Payroll and Accounting Systems | Payroll / Finance Staff; System Administrator; External System | Synchronize timesheets, payroll records, invoices, expenses, and accounting data. |
| 26 | UC-GOV-06 | Platform & Governance | Integrations & Workflows | Manage Multi-Level Approval Workflows | Manager; HR Staff; System Administrator | Configure multi-level approval workflows for leave, overtime, offers, and data changes. |
| 27 | UC-GOV-07 | Platform & Governance | Integrations & Workflows | Manage Dashboards and Notifications | Employee; Manager; HR Staff; Recruiter; Payroll / Finance Staff; External System | Display role-based dashboards and deliver email, push, and in-app notifications. |
| 28 | UC-AI-01 | Analytics & AI | Reporting & Analytics | Generate HR and Recruitment Reports | Recruiter; HR Staff; Manager | Generate headcount, turnover, recruitment, and candidate-pipeline reports. |
| 29 | UC-AI-02 | Analytics & AI | Reporting & Analytics | Generate Time, Attendance and Cost Reports | Manager; HR Staff; Payroll / Finance Staff | Analyze working hours, attendance, overtime, leave, and labor costs. |
| 30 | UC-AI-03 | Analytics & AI | Reporting & Analytics | Create Custom Dashboards and Export Data | Manager; HR Staff; Payroll / Finance Staff | Create custom dashboards and export data to CSV, Excel, or PDF. |
| 31 | UC-AI-04 | Analytics & AI | HR Intelligence & AI | Ask Natural-Language HR Questions | Employee; Manager; HR Staff | Ask natural-language questions and receive answers based on authorized HR data. |
| 32 | UC-AI-05 | Analytics & AI | HR Intelligence & AI | Search HR Policies and Documents | Employee; Manager; HR Staff | Search policies, handbooks, and HR documents using semantic search. |
| 33 | UC-AI-06 | Analytics & AI | HR Intelligence & AI | Detect Workforce Trends and Anomalies | Manager; HR Staff; Payroll / Finance Staff | Detect trends and anomalies in attendance, turnover, cost, or productivity data. |
| 34 | UC-AI-07 | Analytics & AI | HR Intelligence & AI | Generate Data-Driven Recommendations | Manager; HR Staff | Recommend actions based on workforce data and HR metrics. |
| 35 | UC-TA-01 | Time & Attendance | Attendance Management | Clock In and Clock Out | Employee; External System | Record the start and end time of a work shift. |
| 36 | UC-TA-02 | Time & Attendance | Attendance Management | Detect Late Arrivals and Absences | Manager; HR Staff; External System | Compare schedules with attendance records to detect lateness, absences, and missed shifts. |
| 37 | UC-TA-03 | Time & Attendance | Attendance Management | Manage Paid and Unpaid Breaks | Employee; Manager; HR Staff | Record breaks and classify them as paid or unpaid according to policy. |
| 38 | UC-TA-04 | Time & Attendance | Attendance Management | Calculate and Approve Overtime | Employee; Manager; HR Staff; Payroll / Finance Staff | Calculate overtime, submit requests, approve hours, and send approved data to payroll. |
| 39 | UC-TA-05 | Time & Attendance | Time Tracking | Start and Stop Work Timers | Employee; External System | Start, stop, pause, and monitor work timers. |
| 40 | UC-TA-06 | Time & Attendance | Time Tracking | Track Time by Project and Task | Employee; Manager; External System | Record working time against projects, tasks, clients, or work items. |
| 41 | UC-TA-07 | Time & Attendance | Time Tracking | Manage Manual and Offline Time | Employee; Manager; HR Staff | Add manual entries, record time offline, synchronize records, and approve corrections. |
| 42 | UC-TA-08 | Time & Attendance | Time Tracking | Manage Billable and Non-Billable Time | Employee; Manager; Payroll / Finance Staff | Classify time as billable or non-billable and apply billing rules. |
| 43 | UC-TA-09 | Time & Attendance | Scheduling | Manage Work Shifts and Team Assignments | Employee; Manager; HR Staff | Create shifts, assign employees or teams, update schedules, and notify participants. |
| 44 | UC-TA-10 | Time & Attendance | Scheduling | Manage Recurring Schedules | Manager; HR Staff | Create and maintain repeating daily, weekly, or rotating schedules. |
| 45 | UC-TA-11 | Time & Attendance | Scheduling | Detect Schedule Conflicts | Manager; HR Staff | Detect overlapping shifts, leave conflicts, staffing gaps, and excessive scheduled hours. |
| 46 | UC-TA-12 | Time & Attendance | Leave Management | Manage Time-Off Policies and Leave Balances | Employee; HR Staff | Create leave types, accrual and carry-over rules, and calculate employee leave balances. |
| 47 | UC-TA-13 | Time & Attendance | Leave Management | Manage Leave Requests and Approvals | Employee; Manager; HR Staff | Submit, edit, cancel, review, approve, or reject leave requests. |
| 48 | UC-TA-14 | Time & Attendance | Leave Management | Manage Holiday Calendars | Employee; Manager; HR Staff | Create and display company, national, and regional holiday calendars. |
| 49 | UC-WT-01 | Workforce Tracking | Activity & Productivity | Track Keyboard and Mouse Activity | Employee; Manager; External System | Record keyboard and mouse activity levels during authorized work sessions. |
| 50 | UC-WT-02 | Workforce Tracking | Activity & Productivity | Capture Employee Screenshots | Employee; Manager; External System | Capture screenshots at configured intervals according to company policy. |
| 51 | UC-WT-03 | Workforce Tracking | Activity & Productivity | Track Application and Website Usage | Employee; Manager; External System | Record applications and websites used during work sessions. |
| 52 | UC-WT-04 | Workforce Tracking | Activity & Productivity | Analyze Idle Time and Focus | Employee; Manager; HR Staff | Analyze idle periods, activity levels, and focus time. |
| 53 | UC-WT-05 | Workforce Tracking | Location & Field Operations | Track Real-Time GPS Location | Employee; Manager; External System | Record authorized real-time GPS location during work hours. |
| 54 | UC-WT-06 | Workforce Tracking | Location & Field Operations | View Location and Route History | Employee; Manager; HR Staff | View authorized location and route history for field work sessions. |
| 55 | UC-WT-07 | Workforce Tracking | Location & Field Operations | Manage Geofence Clock-In | Employee; Manager; HR Staff; External System | Allow or restrict clock-in based on configured geofences. |
| 56 | UC-WT-08 | Workforce Tracking | Location & Field Operations | Track Field Employee Attendance | Employee; Manager; HR Staff | Track attendance for employees working outside company locations. |
| 57 | UC-PB-01 | Payroll & Benefits | Payroll Processing | Manage Pay Rates and Salary Types | HR Staff; Payroll / Finance Staff | Configure hourly rates, salaries, overtime rates, and effective dates. |
| 58 | UC-PB-02 | Payroll & Benefits | Payroll Processing | Calculate Payroll from Approved Timesheets | Manager; Payroll / Finance Staff; External System | Calculate payroll from approved hours, overtime, leave, and timesheets. |
| 59 | UC-PB-03 | Payroll & Benefits | Payroll Processing | Process Payroll Tax and Direct Deposit | Employee; Payroll / Finance Staff; External System | Calculate taxes and deductions and process direct deposits. |
| 60 | UC-PB-04 | Payroll & Benefits | Payroll Processing | View Payroll History | Employee; HR Staff; Payroll / Finance Staff | View payroll runs, payslips, deductions, and payment history. |
| 61 | UC-PB-05 | Payroll & Benefits | Compensation & Benefits | Manage Salary Bands and Salary Reviews | Manager; HR Staff | Create salary bands, conduct salary reviews, and manage salary adjustments. |
| 62 | UC-PB-06 | Payroll & Benefits | Compensation & Benefits | Manage Benefit Plan Eligibility | Employee; HR Staff; Payroll / Finance Staff | Determine eligibility for benefit plans based on employee attributes and policy. |
| 63 | UC-PB-07 | Payroll & Benefits | Compensation & Benefits | Manage Open and New-Hire Enrollment | Employee; Candidate / New Hire; HR Staff; Payroll / Finance Staff | Allow employees and new hires to enroll in, change, or confirm benefit plans. |
| 64 | UC-PB-08 | Payroll & Benefits | Client Billing & Expenses | Manage Billable Hours and Rates | Employee; Manager; Payroll / Finance Staff | Define billable hours, client rates, and billing rules. |
| 65 | UC-PB-09 | Payroll & Benefits | Client Billing & Expenses | Generate and Deliver Invoices | Payroll / Finance Staff; External System | Generate invoices from billable time and deliver them to clients. |
| 66 | UC-PB-10 | Payroll & Benefits | Client Billing & Expenses | Manage Expense Reimbursement and Invoicing | Employee; Manager; Payroll / Finance Staff | Submit expenses, approve reimbursements, and include eligible expenses in client invoices. |

# Actor Relationships 
![alt text](docs/usecase/HR.png)
# UC-CORE-01 — Manage Organization Structure
![alt text](docs/usecase/UC-CORE-01_Manage-Organization-Structure.png)

# UC-CORE-02 — Manage User Accounts
![alt text](docs/usecase/UC-CORE-02_Manage-User-Accounts.png)

# UC-CORE-03 — Manage Roles and Permissions
![alt text](docs/usecase/UC-CORE-03_Manage-Roles-and-Permissions.png)

# UC-CORE-04 — Manage Employee Records and Directory
![alt text](docs/usecase/UC-CORE-04_Manage-Employee-Records-and-Directory.png)

# UC-CORE-05 — Manage Employee Documents
![alt text](docs/usecase/UC-CORE-05_Manage-Employee-Documents.png)

# UC-CORE-06 — View Employee Data Change History
![alt text](docs/usecase/UC-CORE-06_View-Employee-Data-Change-History.png)

# UC-CORE-07 — Manage Engagement and Wellbeing Surveys
![alt text](docs/usecase/UC-CORE-07_Manage-Engagement-and-Wellbeing-Surveys.png)

# UC-CORE-08 — Manage Recognition and Rewards
![alt text](docs/usecase/UC-CORE-08_Manage-Recognition-and-Rewards.png)

# UC-CORE-09 — Manage Internal Announcements
![alt text](docs/usecase/UC-CORE-09_Manage-Internal-Announcements.png)

# UC-CORE-10 — Manage Goals and One-on-One Meetings
![alt text](docs/usecase/UC-CORE-10_Manage-Goals-and-One-on-One-Meetings.png)

# UC-CORE-11 — Manage Self and Manager Assessments
![alt text](docs/usecase/UC-CORE-11_Manage-Self-and-Manager-Assessments.png)

# UC-CORE-12 — Manage 360-Degree Feedback and Performance Reviews
![alt text](docs/usecase/UC-CORE-12_Manage-360-Degree-Feedback-and-Performance-Reviews.png)

# UC-REC-01 — Manage Job Openings
![alt text](docs/usecase/UC-REC-01_Manage-Job-Openings.png)

# UC-REC-02 — Manage Candidate Pipeline and Interviews
![alt text](docs/usecase/UC-REC-02_Manage-Candidate-Pipeline-and-Interviews.png)

# UC-REC-03 — Evaluate Candidates
![alt text](docs/usecase/UC-REC-03_Evaluate-Candidates.png)

# UC-REC-04 — Manage Job Offers
![alt text](docs/usecase/UC-REC-04_Manage-Job-Offers.png)

# UC-REC-05 — Collect New-Hire Information
![alt text](docs/usecase/UC-REC-05_Collect-New-Hire-Information.png)

# UC-REC-06 — Manage Onboarding Checklists
![alt text](docs/usecase/UC-REC-06_Manage-Onboarding-Checklists.png)

# UC-REC-07 — Manage Electronic Signatures
![alt text](docs/usecase/UC-REC-07_Manage-Electronic-Signatures.png)

# UC-REC-08 — Recover Employee Access and Equipment
![alt text](docs/usecase/UC-REC-08_Recover-Employee-Access-and-Equipment.png)

# UC-GOV-01 — Authenticate Users with 2FA and SSO
![alt text](docs/usecase/UC-GOV-01_Authenticate-Users-with-2FA-and-SSO.png)

# UC-GOV-02 — Manage Role-Based Access Control
![alt text](docs/usecase/UC-GOV-02_Manage-Role-Based-Access-Control.png)

# UC-GOV-03 — Manage Privacy and Audit Logs
![alt text](docs/usecase/UC-GOV-03_Manage-Privacy-and-Audit-Logs.png)

# UC-GOV-04 — Manage Public APIs and Webhooks
![alt text](docs/usecase/UC-GOV-04_Manage-Public-APIs-and-Webhooks.png)

# UC-GOV-05 — Integrate Payroll and Accounting Systems
![alt text](docs/usecase/UC-GOV-05_Integrate-Payroll-and-Accounting-Systems.png)

# UC-GOV-06 — Manage Multi-Level Approval Workflows
![alt text](docs/usecase/UC-GOV-06_Manage-Multi-Level-Approval-Workflows.png)

# UC-GOV-07 — Manage Dashboards and Notifications
![alt text](docs/usecase/UC-GOV-07_Manage-Dashboards-and-Notifications.png)

# UC-AI-01 — Generate HR and Recruitment Reports
![alt text](docs/usecase/UC-AI-01_Generate-HR-and-Recruitment-Reports.png)

# UC-AI-02 — Generate Time, Attendance and Cost Reports
![alt text](docs/usecase/UC-AI-02_Generate-Time-Attendance-and-Cost-Reports.png)

# UC-AI-03 — Create Custom Dashboards and Export Data
![alt text](docs/usecase/UC-AI-03_Create-Custom-Dashboards-and-Export-Data.png)

# UC-AI-04 — Ask Natural-Language HR Questions
![alt text](docs/usecase/UC-AI-04_Ask-Natural-Language-HR-Questions.png)

# UC-AI-05 — Search HR Policies and Documents
![alt text](docs/usecase/UC-AI-05_Search-HR-Policies-and-Documents.png)

# UC-AI-06 — Detect Workforce Trends and Anomalies
![alt text](docs/usecase/UC-AI-06_Detect-Workforce-Trends-and-Anomalies.png)

# UC-AI-07 — Generate Data-Driven Recommendations
![alt text](docs/usecase/UC-AI-07_Generate-Data-Driven-Recommendations.png)

# UC-TA-01 — Clock In and Clock Out
![alt text](docs/usecase/UC-TA-01_Clock-In-and-Clock-Out.png)

# UC-TA-02 — Detect Late Arrivals and Absences
![alt text](docs/usecase/UC-TA-02_Detect-Late-Arrivals-and-Absences.png)

# UC-TA-03 — Manage Paid and Unpaid Breaks
![alt text](docs/usecase/UC-TA-03_Manage-Paid-and-Unpaid-Breaks.png)

# UC-TA-04 — Calculate and Approve Overtime
![alt text](docs/usecase/UC-TA-04_Calculate-and-Approve-Overtime.png)

# UC-TA-05 — Start and Stop Work Timers
![alt text](docs/usecase/UC-TA-05_Start-and-Stop-Work-Timers.png)

# UC-TA-06 — Track Time by Project and Task
![alt text](docs/usecase/UC-TA-06_Track-Time-by-Project-and-Task.png)

# UC-TA-07 — Manage Manual and Offline Time
![alt text](docs/usecase/UC-TA-07_Manage-Manual-and-Offline-Time.png)

# UC-TA-08 — Manage Billable and Non-Billable Time
![alt text](docs/usecase/UC-TA-08_Manage-Billable-and-Non-Billable-Time.png)

# UC-TA-09 — Manage Work Shifts and Team Assignments
![alt text](docs/usecase/UC-TA-09_Manage-Work-Shifts-and-Team-Assignments.png)

# UC-TA-10 — Manage Recurring Schedules
![alt text](docs/usecase/UC-TA-10_Manage-Recurring-Schedules.png)

# UC-TA-11 — Detect Schedule Conflicts
![alt text](docs/usecase/UC-TA-11_Detect-Schedule-Conflicts.png)

# UC-TA-12 — Manage Time-Off Policies and Leave Balances
![alt text](docs/usecase/UC-TA-12_Manage-Time-Off-Policies-and-Leave-Balances.png)

# UC-TA-13 — Manage Leave Requests and Approvals
![alt text](docs/usecase/UC-TA-13_Manage-Leave-Requests-and-Approvals.png)

# UC-TA-14 — Manage Holiday Calendars
![alt text](docs/usecase/UC-TA-14_Manage-Holiday-Calendars.png)

# UC-WT-01 — Track Keyboard and Mouse Activity
![alt text](docs/usecase/UC-WT-01_Track-Keyboard-and-Mouse-Activity.png)

# UC-WT-02 — Capture Employee Screenshots
![alt text](docs/usecase/UC-WT-02_Capture-Employee-Screenshots.png)

# UC-WT-03 — Track Application and Website Usage
![alt text](docs/usecase/UC-WT-03_Track-Application-and-Website-Usage.png)

# UC-WT-04 — Analyze Idle Time and Focus
![alt text](docs/usecase/UC-WT-04_Analyze-Idle-Time-and-Focus.png)

# UC-WT-05 — Track Real-Time GPS Location
![alt text](docs/usecase/UC-WT-05_Track-Real-Time-GPS-Location.png)

# UC-WT-06 — View Location and Route History
![alt text](docs/usecase/UC-WT-06_View-Location-and-Route-History.png)

# UC-WT-07 — Manage Geofence Clock-In
![alt text](docs/usecase/UC-WT-07_Manage-Geofence-Clock-In.png)

# UC-WT-08 — Track Field Employee Attendance
![alt text](docs/usecase/UC-WT-08_Track-Field-Employee-Attendance.png)

# UC-PB-01 — Manage Pay Rates and Salary Types
![alt text](docs/usecase/UC-PB-01_Manage-Pay-Rates-and-Salary-Types.png)

# UC-PB-02 — Calculate Payroll from Approved Timesheets
![alt text](docs/usecase/UC-PB-02_Calculate-Payroll-from-Approved-Timesheets.png)

# UC-PB-03 — Process Payroll Tax and Direct Deposit
![alt text](docs/usecase/UC-PB-03_Process-Payroll-Tax-and-Direct-Deposit.png)

# UC-PB-04 — View Payroll History
![alt text](docs/usecase/UC-PB-04_View-Payroll-History.png)

# UC-PB-05 — Manage Salary Bands and Salary Reviews
![alt text](docs/usecase/UC-PB-05_Manage-Salary-Bands-and-Salary-Reviews.png)

# UC-PB-06 — Manage Benefit Plan Eligibility
![alt text](docs/usecase/UC-PB-06_Manage-Benefit-Plan-Eligibility.png)

# UC-PB-07 — Manage Open and New-Hire Enrollment
![alt text](docs/usecase/UC-PB-07_Manage-Open-and-New-Hire-Enrollment.png)

# UC-PB-08 — Manage Billable Hours and Rates
![alt text](docs/usecase/UC-PB-08_Manage-Billable-Hours-and-Rates.png)

# UC-PB-09 — Generate and Deliver Invoices
![alt text](docs/usecase/UC-PB-09_Generate-and-Deliver-Invoices.png)

# UC-PB-10 — Manage Expense Reimbursement and Invoicing
![alt text](docs/usecase/UC-PB-10_Manage-Expense-Reimbursement-and-Invoicing.png)

# Swimlane Process Catalogue

| No. | Swimlane ID | Module | Process Name | Related Use Cases | Lanes / Participants | Process Summary | Priority |
|---:|---|---|---|---|---|---|---|
| 1 | SW-CORE-01 | Core HR | Employee Data Change Approval | UC-CORE-04; UC-CORE-06 | Employee; Manager; HR Staff; HR Platform; External System | Employee submits a data-change request; Manager or HR Staff reviews it; the system updates the employee record, records the audit trail, and sends the result. | Must-have |
| 2 | SW-CORE-02 | Core HR | Employee Account Provisioning | UC-CORE-02; UC-CORE-03 | HR Staff; System Administrator; HR Platform; External System | HR Staff requests an account; System Administrator creates it, assigns roles and permissions, activates access, and triggers account notification. | Should-have |
| 3 | SW-CORE-03 | Core HR | Employee Document E-Signature | UC-CORE-05 | HR Staff; Employee; HR Platform; External System | HR Staff uploads a document and requests a signature; Employee signs; the external signature service verifies it; the platform updates document status. | Must-have |
| 4 | SW-CORE-04 | Core HR | Recognition and Reward Approval | UC-CORE-08 | Employee; Manager; HR Staff; HR Platform; External System | Employee or Manager submits recognition or a reward nomination; HR Staff reviews and approves or rejects it; the platform records and notifies the result. | Should-have |
| 5 | SW-CORE-05 | Core HR | Performance Review Cycle | UC-CORE-10; UC-CORE-11; UC-CORE-12 | Employee; Manager; HR Staff; Review Participant / External System; HR Platform | HR Staff configures the review cycle; employees and managers complete assessments; reviewers provide feedback; HR Staff closes the cycle and publishes results. | Must-have |
| 6 | SW-REC-01 | Recruitment & Onboarding | Job Opening Approval and Publication | UC-REC-01 | Manager; Recruiter; HR Staff; HR Platform; External System | Manager submits a hiring request; Recruiter prepares the job opening; HR Staff approves it; the platform publishes it internally and externally. | Must-have |
| 7 | SW-REC-02 | Recruitment & Onboarding | Candidate Application and Screening | UC-REC-02 | Candidate / New Hire; Recruiter; Manager; HR Platform; External System | Candidate applies; Recruiter screens the application; Manager reviews the candidate; the platform advances or rejects the candidate. | Must-have |
| 8 | SW-REC-03 | Recruitment & Onboarding | Interview Scheduling and Completion | UC-REC-02 | Candidate / New Hire; Recruiter; Manager; HR Platform; External System | Recruiter proposes an interview; Candidate confirms or requests rescheduling; Manager attends; the platform records completion and updates the candidate stage. | Should-have |
| 9 | SW-REC-04 | Recruitment & Onboarding | Candidate Evaluation and Hiring Decision | UC-REC-03 | Recruiter; Manager; HR Staff; HR Platform | Interview feedback is submitted; Recruiter compares candidates; Manager recommends a decision; HR Staff or the platform finalizes the hiring decision. | Should-have |
| 10 | SW-REC-05 | Recruitment & Onboarding | Job Offer Approval and Acceptance | UC-REC-04; UC-REC-07 | Recruiter; Manager; HR Staff; Candidate / New Hire; HR Platform; External System | Recruiter creates the offer; Manager reviews terms; HR Staff approves; Candidate accepts or rejects and signs; the platform updates offer status. | Must-have |
| 11 | SW-REC-06 | Recruitment & Onboarding | New-Hire Onboarding | UC-REC-05; UC-REC-06 | Candidate / New Hire; Manager; HR Staff; System Administrator; HR Platform; External System | New Hire submits required information; HR Staff validates it and assigns a checklist; System Administrator provisions access; Manager assigns team tasks; onboarding is completed. | Must-have |
| 12 | SW-REC-07 | Recruitment & Onboarding | Employee Offboarding | UC-REC-08 | Manager; Employee; HR Staff; System Administrator; HR Platform | Manager initiates offboarding; HR Staff creates the checklist; Employee returns equipment; System Administrator revokes access; the employee record is closed. | Must-have |
| 13 | SW-GOV-01 | Platform & Governance | User Authentication with SSO and 2FA | UC-GOV-01 | User; HR Platform; External System; System Administrator | User signs in; the platform redirects to the identity provider; identity and second factor are verified; a token is issued and access is granted. | Should-have |
| 14 | SW-GOV-02 | Platform & Governance | Multi-Level Approval Workflow | UC-GOV-06 | Requester; Manager; HR Staff; HR Platform; External System | Requester submits a request; one or more approval levels review it; the final decision updates status and triggers notification. | Must-have |
| 15 | SW-GOV-03 | Platform & Governance | External System Data Synchronization | UC-GOV-04; UC-GOV-05 | Payroll / Finance Staff; System Administrator; HR Platform; External System | A user initiates synchronization; the platform validates and maps data; the external system processes it and returns status; failures are retried or corrected. | Should-have |
| 16 | SW-AI-01 | Analytics & AI | Natural-Language HR Question | UC-AI-04; UC-AI-05 | Employee / Manager / HR Staff; HR Platform; External System | User asks a question; the platform checks authorization, retrieves relevant data or documents, generates an answer, and returns supporting sources. | Should-have |
| 17 | SW-AI-02 | Analytics & AI | Workforce Anomaly Review | UC-AI-06; UC-AI-07 | External System; HR Platform; HR Staff; Manager | The system detects a workforce anomaly, generates a recommendation, and routes it to HR Staff and Manager for review and action. | Should-have |
| 18 | SW-TA-01 | Time & Attendance | Attendance Correction | UC-TA-01; UC-TA-02 | Employee; Manager; HR Staff; HR Platform; External System | A clock event is recorded; the platform detects an abnormality; Employee requests correction; Manager and HR Staff review; the record is updated. | Should-have |
| 19 | SW-TA-02 | Time & Attendance | Overtime Approval | UC-TA-04 | Employee; Manager; HR Staff; Payroll / Finance Staff; HR Platform | Employee submits overtime; Manager reviews; HR Staff handles exceptions; approved hours are sent to payroll. | Must-have |
| 20 | SW-TA-03 | Time & Attendance | Manual and Offline Time Approval | UC-TA-07 | Employee; Manager; HR Staff; HR Platform | Employee records manual or offline time; the platform synchronizes it; Manager approves or rejects; HR Staff handles corrections. | Should-have |
| 21 | SW-TA-04 | Time & Attendance | Shift Assignment and Change | UC-TA-09; UC-TA-10 | Manager; Employee; HR Staff; HR Platform; External System | Manager creates and assigns a shift; the platform checks rules; Employee confirms or requests a change; the schedule is updated and notification is sent. | Should-have |
| 22 | SW-TA-05 | Time & Attendance | Schedule Conflict Resolution | UC-TA-11 | Manager; HR Staff; HR Platform | The platform detects overlap, leave conflict, staffing gap, or excessive workload; Manager and HR Staff review and correct the schedule. | Should-have |
| 23 | SW-TA-06 | Time & Attendance | Leave Request Approval | UC-TA-12; UC-TA-13 | Employee; Manager; HR Staff; HR Platform; External System | Employee submits leave; the platform validates dates and balance; Manager reviews staffing; HR Staff handles exceptions; the decision updates balance and triggers notification. | Must-have |
| 24 | SW-WT-01 | Workforce Tracking | Authorized Activity Tracking Session | UC-WT-01; UC-WT-02; UC-WT-03; UC-WT-04 | Employee; External System; HR Platform; Manager; HR Staff | Employee starts an authorized session; the tracking agent collects activity, screenshots, and app usage; the platform calculates metrics; Manager and HR Staff review permitted results. | Should-have |
| 25 | SW-WT-02 | Workforce Tracking | Field Attendance and Geofence Validation | UC-WT-05; UC-WT-06; UC-WT-07; UC-WT-08 | Employee; External System; HR Platform; Manager; HR Staff | Employee attempts field clock-in; device captures location; the platform validates the geofence; attendance is accepted or rejected; exceptions are reviewed. | Must-have |
| 26 | SW-PB-01 | Payroll & Benefits | Payroll Calculation | UC-PB-01; UC-PB-02 | Manager; Payroll / Finance Staff; HR Staff; HR Platform; External System | Manager confirms timesheets; Payroll Staff imports approved hours; the platform applies rates, overtime, and leave; payroll is reviewed and finalized. | Must-have |
| 27 | SW-PB-02 | Payroll & Benefits | Tax and Direct Deposit Processing | UC-PB-03 | Payroll / Finance Staff; HR Platform; External System; Employee | Payroll Staff initiates payment; the platform calculates taxes and deductions; tax and banking services validate and process payment; Employee receives the result. | Must-have |
| 28 | SW-PB-03 | Payroll & Benefits | Salary Review and Adjustment | UC-PB-05 | Manager; HR Staff; Payroll / Finance Staff; HR Platform | Manager submits a salary recommendation; HR Staff reviews the salary band and approves or rejects the adjustment; payroll applies the new salary. | Should-have |
| 29 | SW-PB-04 | Payroll & Benefits | Benefit Enrollment | UC-PB-06; UC-PB-07 | Employee / Candidate / New Hire; HR Staff; Payroll / Finance Staff; HR Platform; External System | The platform determines eligible plans; Employee or New Hire enrolls; HR Staff reviews; Payroll applies deductions; the provider receives enrollment data. | Must-have |
| 30 | SW-PB-05 | Payroll & Benefits | Invoice Generation and Delivery | UC-PB-08; UC-PB-09 | Employee; Manager; Payroll / Finance Staff; HR Platform; External System | Employee records billable time; Manager approves hours; Finance calculates and approves the invoice; the external system delivers it and returns payment status. | Should-have |
| 31 | SW-PB-06 | Payroll & Benefits | Expense Reimbursement | UC-PB-10 | Employee; Manager; Payroll / Finance Staff; HR Platform; External System | Employee submits an expense and receipt; Manager reviews; Finance approves or rejects and processes reimbursement; client-billable expenses may be invoiced. | Must-have |

# SW-CORE-01 — Employee Data Change Approval
![alt text](docs/swimlane/SW-CORE-01.png)
# SW-CORE-02 — Employee Account Provisioning
![alt text](docs/swimlane/SW-CORE-02.png)
# SW-CORE-03 — Employee Document E-Signature
![alt text](docs/swimlane/SW-CORE-03.png)
# SW-CORE-04 — Recognition and Reward Approval
![alt text](docs/swimlane/SW-CORE-04.png)
# SW-CORE-05 — Performance Review Cycle
![alt text](docs/swimlane/05.png)
# SW-REC-01 — Job Opening Approval and Publication
![alt text](docs/swimlane/rec01.png)
# SW-REC-02 — Candidate Application and Screening
![alt text](docs/swimlane/rec02.png)
# SW-REC-03 — Interview Scheduling and Completion
![alt text](docs/swimlane/rec03.png)
# SW-REC-04 — Candidate Evaluation and Hiring Decision
![alt text](docs/swimlane/rec04.png)
# SW-REC-05 — Job Offer Approval and Acceptance
![alt text](docs/swimlane/rec05.png)
# SW-REC-06 — New-Hire Onboarding
![alt text](docs/swimlane/rec06.png)
# SW-REC-07 — Employee Offboarding
![alt text](docs/swimlane/rec07.png)
# SW-GOV-01 — User Authentication with SSO and 2FA
![alt text](docs/swimlane/gov01.png)
# SW-GOV-02 — Multi-Level Approval Workflow
![alt text](docs/swimlane/gov02.png)
# SW-GOV-03 — External System Data Synchronization
![alt text](docs/swimlane/gov03.png)
# SW-AI-01 — Natural-Language HR Question
![alt text](docs/swimlane/al01.png)
# SW-AI-02 — Workforce Anomaly Review
![alt text](docs/swimlane/al02.png)
# SW-TA-01 — Attendance Correction
![alt text](docs/swimlane/ta01.png)
# SW-TA-02 — Overtime Approval
![alt text](docs/swimlane/ta02.png)
# SW-TA-03 — Manual and Offline Time Approval
![alt text](docs/swimlane/ta03.png)
# SW-TA-04 — Shift Assignment and Change
![alt text](docs/swimlane/ta04.png)
# SW-TA-05 — Schedule Conflict Resolution
![alt text](docs/swimlane/ta05.png)
# SW-TA-06 — Leave Request Approval
![alt text](docs/swimlane/ta06.png)
# SW-WT-01 — Authorized Activity Tracking Session
![alt text](docs/swimlane/wt01.png)
# SW-WT-02 — Field Attendance and Geofence Validation
![alt text](docs/swimlane/wt02.png)
# SW-PB-01 — Payroll Calculation
![alt text](docs/swimlane/pb01.png)
# SW-PB-02 — Tax and Direct Deposit Processing
![alt text](docs/swimlane/pb02.png)
# SW-PB-03 — Salary Review and Adjustment
![alt text](docs/swimlane/pb03.png)
# SW-PB-04 — Benefit Enrollment
![alt text](docs/swimlane/pb04.png)
# SW-PB-05 — Invoice Generation and Delivery
![alt text](docs/swimlane/pb05.png)
# SW-PB-06 — Expense Reimbursement
![alt text](docs/swimlane/pb06.png)


