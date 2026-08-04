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

# Mindmap for Core HR 
```mermaid
flowchart LR

    %% CENTER
    CORE["Core HR"]

    %% LEFT SIDE — 2 SUB-MODULES
    ORGANIZATION["Organization & Access"] --- CORE
    EMPLOYEE_INFO["Employee Information"] --- CORE

    OA1["Organization Structure"] --- ORGANIZATION
    OA2["User Account Management"] --- ORGANIZATION
    OA3["Role & Permission Management"] --- ORGANIZATION

    EI1["Employee Records & Directory"] --- EMPLOYEE_INFO
    EI2["Employee Documents"] --- EMPLOYEE_INFO
    EI3["Data Change History"] --- EMPLOYEE_INFO

    %% RIGHT SIDE — 2 SUB-MODULES
    CORE --- EXPERIENCE["Employee Experience"]
    CORE --- PERFORMANCE["Performance & Goals"]

    EXPERIENCE --- EE1["Engagement & Wellbeing Surveys"]
    EXPERIENCE --- EE2["Recognition & Rewards"]
    EXPERIENCE --- EE3["Internal Announcements"]

    PERFORMANCE --- PG1["Goal Tracking & 1-on-1s"]
    PERFORMANCE --- PG2["Self & Manager Assessments"]
    PERFORMANCE --- PG3["360 Feedback & Performance Reviews"]

    %% STYLES
    classDef center fill:#0f172a,stroke:#3b82f6,stroke-width:4px,color:#ffffff,font-weight:bold;
    classDef layer1 fill:#dbeafe,stroke:#2563eb,stroke-width:2px,color:#1e293b,font-weight:bold;
    classDef layer2 fill:#ffffff,stroke:#94a3b8,stroke-width:1px,color:#334155;

    class CORE center;
    class ORGANIZATION,EMPLOYEE_INFO,EXPERIENCE,PERFORMANCE layer1;
    class OA1,OA2,OA3,EI1,EI2,EI3,EE1,EE2,EE3,PG1,PG2,PG3 layer2;
```

# Mindmap for Time & Attendance 
```mermaid
flowchart LR

    %% CENTER
    TIME["Time & Attendance"]

    %% LEFT SIDE — 2 SUB-MODULES
    ATTENDANCE["Attendance Management"] --- TIME
    TIME_TRACKING["Time Tracking"] --- TIME

    AM1["Clock In & Clock Out"] --- ATTENDANCE
    AM2["Late & Absence Detection"] --- ATTENDANCE
    AM3["Paid & Unpaid Breaks"] --- ATTENDANCE
    AM4["Overtime Calculation & Approval"] --- ATTENDANCE

    TT1["Start & Stop Timers"] --- TIME_TRACKING
    TT2["Project & Task Tracking"] --- TIME_TRACKING
    TT3["Manual & Offline Time"] --- TIME_TRACKING
    TT4["Billable & Non-Billable Rules"] --- TIME_TRACKING

    %% RIGHT SIDE — 2 SUB-MODULES
    TIME --- SCHEDULING["Scheduling"]
    TIME --- LEAVE["Leave Management"]

    SCHEDULING --- SC1["Work Shifts & Team Assignment"]
    SCHEDULING --- SC2["Recurring Schedules"]
    SCHEDULING --- SC3["Schedule Conflict Detection"]

    LEAVE --- LM1["Time-Off Policies & Balances"]
    LEAVE --- LM2["Leave Requests & Approvals"]
    LEAVE --- LM3["Holiday Calendar"]

    %% STYLES
    classDef center fill:#0f172a,stroke:#10b981,stroke-width:4px,color:#ffffff,font-weight:bold;
    classDef layer1 fill:#d1fae5,stroke:#059669,stroke-width:2px,color:#064e3b,font-weight:bold;
    classDef layer2 fill:#ffffff,stroke:#94a3b8,stroke-width:1px,color:#334155;

    class TIME center;
    class ATTENDANCE,TIME_TRACKING,SCHEDULING,LEAVE layer1;
    class AM1,AM2,AM3,AM4,TT1,TT2,TT3,TT4,SC1,SC2,SC3,LM1,LM2,LM3 layer2;
```

# Actors, Funtionals Mindmap for Core HR
```mermaid
flowchart LR

    %% =====================================================
    %% CENTER
    %% =====================================================

    CORE["Core HR"]

    %% =====================================================
    %% LEFT SIDE — HUMAN ACTORS
    %% =====================================================

    HUMAN["Human Actors"] --- CORE

    EMP["Employee"] --- HUMAN
    MGR["Manager"] --- HUMAN
    HRA["HR Administrator"] --- HUMAN
    HRM["HR Manager"] --- HUMAN
    SYS["System Administrator"] --- HUMAN
    REVIEWER["Review Participant"] --- HUMAN
    EXEC["Executive"] --- HUMAN

    %% Employee responsibilities
    EMP1["Manage Own Profile"] --- EMP
    EMP2["Manage Personal Documents"] --- EMP
    EMP3["Participate in Employee Experience"] --- EMP
    EMP4["Manage Goals and Assessments"] --- EMP

    %% Manager responsibilities
    MGR1["View and Manage Team Information"] --- MGR
    MGR2["Review Employee Data Changes"] --- MGR
    MGR3["Manage Team Goals and 1-on-1s"] --- MGR
    MGR4["Conduct Performance Reviews"] --- MGR

    %% HR Administrator responsibilities
    HRA1["Manage Organization Structure"] --- HRA
    HRA2["Manage Employee Records"] --- HRA
    HRA3["Manage Documents and Data Changes"] --- HRA
    HRA4["Administer Surveys and Review Cycles"] --- HRA

    %% HR Manager responsibilities
    HRM1["Approve Important HR Changes"] --- HRM
    HRM2["Monitor Employee Data Quality"] --- HRM
    HRM3["Approve HR Policies and Programs"] --- HRM
    HRM4["Review Organization-Wide HR Results"] --- HRM

    %% System Administrator responsibilities
    SYS1["Manage User Accounts"] --- SYS
    SYS2["Manage Roles and Permissions"] --- SYS
    SYS3["Configure Authentication and Security"] --- SYS
    SYS4["Manage Technical Integrations"] --- SYS

    %% Review Participant responsibilities
    REV1["View Feedback Requests"] --- REVIEWER
    REV2["Provide 360-Degree Feedback"] --- REVIEWER
    REV3["Evaluate Assigned Employees"] --- REVIEWER
    REV4["Submit Review Feedback"] --- REVIEWER

    %% Executive responsibilities
    EX1["View HR Summary Reports"] --- EXEC
    EX2["Review Engagement Trends"] --- EXEC
    EX3["Review Performance Trends"] --- EXEC
    EX4["Support Strategic HR Decisions"] --- EXEC

    %% =====================================================
    %% RIGHT SIDE — EXTERNAL SYSTEM ACTORS
    %% =====================================================

    CORE --- EXTERNAL["External System Actors"]

    EXTERNAL --- IDP["Identity Provider"]
    EXTERNAL --- NOTIFY["Notification Service"]
    EXTERNAL --- ESIGN["Electronic Signature Service"]

    %% Identity Provider responsibilities
    IDP --- IDP1["Authenticate Users"]
    IDP --- IDP2["Verify User Identity"]
    IDP --- IDP3["Issue and Validate Tokens"]
    IDP --- IDP4["Support Account Recovery"]

    %% Notification Service responsibilities
    NOTIFY --- N1["Send Account Notifications"]
    NOTIFY --- N2["Send Data Change Notifications"]
    NOTIFY --- N3["Send Survey and Review Reminders"]
    NOTIFY --- N4["Send Recognition and Document Alerts"]

    %% Electronic Signature Service responsibilities
    ESIGN --- E1["Receive Documents for Signing"]
    ESIGN --- E2["Verify Signer Identity"]
    ESIGN --- E3["Record Electronic Signatures"]
    ESIGN --- E4["Return Signed Documents and Status"]

    %% =====================================================
    %% STYLES
    %% =====================================================

    classDef center fill:#dbeafe,stroke:#2563eb,stroke-width:4px,color:#111,font-weight:bold;

    classDef category fill:#e0e7ff,stroke:#4f46e5,stroke-width:2px,color:#111,font-weight:bold;

    classDef employee fill:#fef08a,stroke:#ca8a04,stroke-width:2px,color:#111,font-weight:bold;
    classDef manager fill:#fdba74,stroke:#ea580c,stroke-width:2px,color:#111,font-weight:bold;
    classDef hr fill:#86efac,stroke:#16a34a,stroke-width:2px,color:#111,font-weight:bold;
    classDef system fill:#c4b5fd,stroke:#7c3aed,stroke-width:2px,color:#111,font-weight:bold;
    classDef specialized fill:#f9a8d4,stroke:#db2777,stroke-width:2px,color:#111,font-weight:bold;
    classDef executive fill:#fca5a5,stroke:#dc2626,stroke-width:2px,color:#111,font-weight:bold;
    classDef external fill:#67e8f9,stroke:#0891b2,stroke-width:2px,color:#111,font-weight:bold;

    classDef functional fill:#ffffff,stroke:#94a3b8,stroke-width:1px,color:#111;

    class CORE center;
    class HUMAN,EXTERNAL category;

    class EMP employee;
    class MGR manager;
    class HRA,HRM hr;
    class SYS system;
    class REVIEWER specialized;
    class EXEC executive;

    class IDP,NOTIFY,ESIGN external;

    class EMP1,EMP2,EMP3,EMP4 functional;
    class MGR1,MGR2,MGR3,MGR4 functional;
    class HRA1,HRA2,HRA3,HRA4 functional;
    class HRM1,HRM2,HRM3,HRM4 functional;
    class SYS1,SYS2,SYS3,SYS4 functional;
    class REV1,REV2,REV3,REV4 functional;
    class EX1,EX2,EX3,EX4 functional;
    class IDP1,IDP2,IDP3,IDP4 functional;
    class N1,N2,N3,N4 functional;
    class E1,E2,E3,E4 functional;
```

# Actors, Funtionals Mindmap for Time & Attedence
```mermaid
flowchart LR

    %% =====================================================
    %% CENTER
    %% =====================================================

    TA["Time & Attendance"]

    %% =====================================================
    %% LEFT SIDE — HUMAN ACTORS
    %% =====================================================

    HUMAN["Human Actors"] --- TA

    EMP["Employee"] --- HUMAN
    MGR["Manager"] --- HUMAN
    HRA["HR Administrator"] --- HUMAN
    HRM["HR Manager"] --- HUMAN
    PAY["Payroll Administrator"] --- HUMAN
    SYS["System Administrator"] --- HUMAN

    %% Employee responsibilities
    EMP1["Record Attendance"] --- EMP
    EMP2["Track Working Time"] --- EMP
    EMP3["View Work Schedule"] --- EMP
    EMP4["Submit Leave Requests"] --- EMP

    %% Manager responsibilities
    MGR1["Review Team Attendance"] --- MGR
    MGR2["Approve Timesheets"] --- MGR
    MGR3["Manage Team Schedules"] --- MGR
    MGR4["Approve Leave Requests"] --- MGR

    %% HR Administrator responsibilities
    HRA1["Configure Attendance Policies"] --- HRA
    HRA2["Configure Time Tracking Rules"] --- HRA
    HRA3["Manage Organization Schedules"] --- HRA
    HRA4["Configure Leave Policies"] --- HRA

    %% HR Manager responsibilities
    HRM1["Approve HR Policies"] --- HRM
    HRM2["Review Attendance Trends"] --- HRM
    HRM3["Approve Exceptional Requests"] --- HRM
    HRM4["Monitor Workforce Capacity"] --- HRM

    %% Payroll Administrator responsibilities
    PAY1["View Approved Time Data"] --- PAY
    PAY2["Validate Payroll Hours"] --- PAY
    PAY3["Export Data to Payroll"] --- PAY
    PAY4["Mark Data as Processed"] --- PAY

    %% System Administrator responsibilities
    SYS1["Manage Access Permissions"] --- SYS
    SYS2["Configure Time Clock Devices"] --- SYS
    SYS3["Manage Integrations"] --- SYS
    SYS4["Monitor Technical Logs"] --- SYS

    %% =====================================================
    %% RIGHT SIDE — EXTERNAL SYSTEM ACTORS
    %% =====================================================

    TA --- EXTERNAL["External System Actors"]

    EXTERNAL --- KIOSK["Time Clock / Kiosk"]
    EXTERNAL --- NOTIFY["Notification Service"]
    EXTERNAL --- PROJECT["Project / Task Management System"]

    %% Time Clock responsibilities
    KIOSK --- K1["Capture Clock-In"]
    KIOSK --- K2["Capture Clock-Out"]
    KIOSK --- K3["Capture Break Events"]
    KIOSK --- K4["Synchronize Attendance Data"]

    %% Notification responsibilities
    NOTIFY --- N1["Send Attendance Reminders"]
    NOTIFY --- N2["Send Shift Notifications"]
    NOTIFY --- N3["Send Approval Notifications"]
    NOTIFY --- N4["Send Leave Notifications"]

    %% Project system responsibilities
    PROJECT --- P1["Provide Project Information"]
    PROJECT --- P2["Provide Task Information"]
    PROJECT --- P3["Validate Active Work Items"]
    PROJECT --- P4["Receive Tracked Time"]

    %% =====================================================
    %% STYLES
    %% =====================================================

    classDef center fill:#dbeafe,stroke:#2563eb,stroke-width:4px,color:#111,font-weight:bold;

    classDef category fill:#e0e7ff,stroke:#4f46e5,stroke-width:2px,color:#111,font-weight:bold;

    classDef employee fill:#fef08a,stroke:#ca8a04,stroke-width:2px,color:#111,font-weight:bold;
    classDef manager fill:#fdba74,stroke:#ea580c,stroke-width:2px,color:#111,font-weight:bold;
    classDef hr fill:#86efac,stroke:#16a34a,stroke-width:2px,color:#111,font-weight:bold;
    classDef payroll fill:#fca5a5,stroke:#dc2626,stroke-width:2px,color:#111,font-weight:bold;
    classDef system fill:#c4b5fd,stroke:#7c3aed,stroke-width:2px,color:#111,font-weight:bold;
    classDef external fill:#67e8f9,stroke:#0891b2,stroke-width:2px,color:#111,font-weight:bold;

    classDef functional fill:#ffffff,stroke:#94a3b8,stroke-width:1px,color:#111;

    class TA center;
    class HUMAN,EXTERNAL category;

    class EMP employee;
    class MGR manager;
    class HRA,HRM hr;
    class PAY payroll;
    class SYS system;

    class KIOSK,NOTIFY,PROJECT external;

    class EMP1,EMP2,EMP3,EMP4 functional;
    class MGR1,MGR2,MGR3,MGR4 functional;
    class HRA1,HRA2,HRA3,HRA4 functional;
    class HRM1,HRM2,HRM3,HRM4 functional;
    class PAY1,PAY2,PAY3,PAY4 functional;
    class SYS1,SYS2,SYS3,SYS4 functional;
    class K1,K2,K3,K4,N1,N2,N3,N4,P1,P2,P3,P4 functional;
```
# Usecase Diagram for CoreHR
## Organization & Access
![alt text](<docs/images/Organization & Access.png>)
## Employee Infomation
![alt text](<docs/images/Employee Infomation.png>)
## Employee Experience 
![alt text](<docs/images/Employee Experience.png>)
## Performance & Goal Management
![alt text](<docs/images/Performance & Goal Management.png>)

# Usecase Diagram for Time & Attendance
## Attendance Management
![alt text](<docs/images/Attendance Management.png>)
## Time Tracking
![alt text](<docs/images/Time Tracking.png>)
## Scheduling
![alt text](docs/images/Scheduling.png)
## Leave Management 
![alt text](<docs/images/Leave Management.png>)
