# HR Platform - Onboarding 

![alt text](Sitemap.jpg)

# UI/UX

https://www.figma.com/design/tRLTPEG82Vo96X54Rirv4u/Onboarding?node-id=0-1&t=NoMbObpnNXexgxZ0-1

# High Level ERD

```mermaid
flowchart TB
    %% ==========================================
    %% COLOR STYLING SYSTEM
    %% ==========================================
    classDef coreStyle fill:#e0f2fe,stroke:#0284c7,stroke-width:2px,color:#0369a1;
    classDef recruitStyle fill:#dcfce7,stroke:#16a34a,stroke-width:2px,color:#15803d;
    classDef templateStyle fill:#fef9c3,stroke:#ca8a04,stroke-width:2px,color:#a16207;
    classDef onboardingStyle fill:#f3e8ff,stroke:#9333ea,stroke-width:2px,color:#7e22ce;
    classDef taskStyle fill:#ffedd5,stroke:#ea580c,stroke-width:2px,color:#c2410c;
    classDef trackingStyle fill:#ccfbf1,stroke:#0d9488,stroke-width:2px,color:#0f766e;

    %% ==========================================
    %% SUBGRAPHS (MODULES)
    %% ==========================================
    subgraph MODULE_CORE["1. Core System & Auth"]
        DEPARTMENT:::coreStyle
        POSITION:::coreStyle
        USER:::coreStyle
        ROLE:::coreStyle
        USER_ROLE:::coreStyle
    end

    subgraph MODULE_RECRUIT["2. Recruitment & Offers"]
        CANDIDATE:::recruitStyle
        APPLICATION_STAGE:::recruitStyle
        APPLICATION:::recruitStyle
        OFFER:::recruitStyle
        OFFER_RESPONSE:::recruitStyle
    end

    subgraph MODULE_TEMPLATES["3. Automation Hub & Templates"]
        ONBOARDING_TEMPLATE:::templateStyle
        TASK_TEMPLATE:::templateStyle
        ONBOARDING_DRAFT:::templateStyle
        FIELD_MAPPING:::templateStyle
        PROCESS_AUTOMATION:::templateStyle
        PROCESS_AUTOMATION_OFFER:::templateStyle
        PROCESS_AUTOMATION_DRAFT:::templateStyle
        PROCESS_AUTOMATION_TEMPLATE:::templateStyle
        PROCESS_AUTOMATION_ONBOARDING_TASK:::templateStyle
    end

    subgraph MODULE_EXECUTION["4. Employee & Execution"]
        EMPLOYEE:::onboardingStyle
        ONBOARDING_STAGE:::onboardingStyle
        ONBOARDING_CASE:::onboardingStyle
    end

    subgraph MODULE_TASKS["5. Tasks & Assignments"]
        ONBOARDING_TASK:::taskStyle
        TASK_ASSIGNMENT:::taskStyle
        READINESS_CHECKLIST_ITEM:::taskStyle
    end

    subgraph MODULE_TRACKING["6. Tracking & Feedback"]
        ONBOARDING_MILESTONE:::trackingStyle
        ONBOARDING_CASE_MILESTONE:::trackingStyle
        CHECK_IN:::trackingStyle
        FEEDBACK:::trackingStyle
        ONBOARDING_BLOCKER:::trackingStyle
    end

    %% Subgraph Layout Fills
    style MODULE_CORE fill:#f8fafc,stroke:#cbd5e1,stroke-width:1.5px
    style MODULE_RECRUIT fill:#f8fafc,stroke:#cbd5e1,stroke-width:1.5px
    style MODULE_TEMPLATES fill:#f8fafc,stroke:#cbd5e1,stroke-width:1.5px
    style MODULE_EXECUTION fill:#f8fafc,stroke:#cbd5e1,stroke-width:1.5px
    style MODULE_TASKS fill:#f8fafc,stroke:#cbd5e1,stroke-width:1.5px
    style MODULE_TRACKING fill:#f8fafc,stroke:#cbd5e1,stroke-width:1.5px

    %% ==========================================
    %% RELATIONSHIPS & CARDINALITY
    %% ==========================================
    DEPARTMENT -- "1 : N" --> EMPLOYEE
    POSITION -- "1 : N" --> EMPLOYEE
    USER -- "1 : N" --> EMPLOYEE
    USER -- "1 : N" --> USER_ROLE
    ROLE -- "1 : N" --> USER_ROLE

    CANDIDATE -- "1 : N" --> APPLICATION
    POSITION -- "1 : N" --> APPLICATION
    APPLICATION_STAGE -- "1 : N" --> APPLICATION
    USER -- "1 : N" --> APPLICATION

    APPLICATION -- "1 : N" --> OFFER
    OFFER -- "1 : N" --> OFFER_RESPONSE

    CANDIDATE -- "1 : N" --> ONBOARDING_DRAFT
    OFFER -- "1 : N" --> ONBOARDING_DRAFT
    ONBOARDING_TEMPLATE -- "1 : N" --> ONBOARDING_DRAFT
    ONBOARDING_TEMPLATE -- "1 : N" --> TASK_TEMPLATE
    ONBOARDING_DRAFT -- "1 : N" --> FIELD_MAPPING
    TASK_TEMPLATE -- "1 : N" --> ONBOARDING_TASK

    PROCESS_AUTOMATION -- "1 : N" --> PROCESS_AUTOMATION_OFFER
    OFFER -- "1 : N" --> PROCESS_AUTOMATION_OFFER
    PROCESS_AUTOMATION -- "1 : N" --> PROCESS_AUTOMATION_DRAFT
    ONBOARDING_DRAFT -- "1 : N" --> PROCESS_AUTOMATION_DRAFT
    PROCESS_AUTOMATION -- "1 : N" --> PROCESS_AUTOMATION_TEMPLATE
    ONBOARDING_TEMPLATE -- "1 : N" --> PROCESS_AUTOMATION_TEMPLATE
    PROCESS_AUTOMATION -- "1 : N" --> PROCESS_AUTOMATION_ONBOARDING_TASK
    ONBOARDING_TASK -- "1 : N" --> PROCESS_AUTOMATION_ONBOARDING_TASK

    CANDIDATE -- "1 : 1" --> EMPLOYEE
    EMPLOYEE -- "1 : N" --> ONBOARDING_CASE
    OFFER -- "1 : 1" --> ONBOARDING_CASE
    ONBOARDING_TEMPLATE -- "1 : N" --> ONBOARDING_CASE
    ONBOARDING_STAGE -- "1 : N" --> ONBOARDING_CASE

    ONBOARDING_CASE -- "1 : N" --> ONBOARDING_TASK
    ONBOARDING_TASK -- "1 : N" --> TASK_ASSIGNMENT
    ROLE -- "1 : N" --> TASK_ASSIGNMENT
    USER -- "1 : N" --> TASK_ASSIGNMENT
    ONBOARDING_CASE -- "1 : N" --> READINESS_CHECKLIST_ITEM

    ONBOARDING_CASE -- "1 : N" --> ONBOARDING_CASE_MILESTONE
    ONBOARDING_MILESTONE -- "1 : N" --> ONBOARDING_CASE_MILESTONE
    ONBOARDING_CASE -- "1 : N" --> CHECK_IN
    ONBOARDING_CASE_MILESTONE -- "1 : N" --> CHECK_IN
    USER -- "1 : N" --> CHECK_IN

    ONBOARDING_CASE -- "1 : N" --> FEEDBACK
    ONBOARDING_CASE_MILESTONE -- "1 : N" --> FEEDBACK
    USER -- "1 : N" --> FEEDBACK

    ONBOARDING_CASE -- "1 : N" --> ONBOARDING_BLOCKER
    ONBOARDING_TASK -- "1 : N" --> ONBOARDING_BLOCKER
```

---

### 2. Entity Relationship Diagram (ERD)

```mermaid
erDiagram

    %% ------------------------------------------
    %% 1. CORE SYSTEM & AUTHENTICATION
    %% ------------------------------------------
    DEPARTMENT
    POSITION
    USER
    ROLE
    USER_ROLE

    %% ------------------------------------------
    %% 2. RECRUITMENT & OFFERS
    %% ------------------------------------------
    CANDIDATE
    APPLICATION_STAGE
    APPLICATION
    OFFER
    OFFER_RESPONSE

    %% ------------------------------------------
    %% 3. AUTOMATION HUB & TEMPLATES
    %% ------------------------------------------
    ONBOARDING_TEMPLATE
    TASK_TEMPLATE
    ONBOARDING_DRAFT
    FIELD_MAPPING
    PROCESS_AUTOMATION
    PROCESS_AUTOMATION_OFFER
    PROCESS_AUTOMATION_DRAFT
    PROCESS_AUTOMATION_TEMPLATE
    PROCESS_AUTOMATION_ONBOARDING_TASK

    %% ------------------------------------------
    %% 4. EMPLOYEES & ONBOARDING EXECUTION
    %% ------------------------------------------
    EMPLOYEE
    ONBOARDING_STAGE
    ONBOARDING_CASE

    %% ------------------------------------------
    %% 5. TASKS & ASSIGNMENTS
    %% ------------------------------------------
    ONBOARDING_TASK
    TASK_ASSIGNMENT
    READINESS_CHECKLIST_ITEM

    %% ------------------------------------------
    %% 6. TRACKING & FEEDBACK
    %% ------------------------------------------
    ONBOARDING_MILESTONE
    ONBOARDING_CASE_MILESTONE
    CHECK_IN
    FEEDBACK
    ONBOARDING_BLOCKER

    %% ==========================================
    %% RELATIONSHIPS
    %% ==========================================
    DEPARTMENT ||--o{ EMPLOYEE : "contains"
    POSITION ||--o{ EMPLOYEE : "held_by"
    USER ||--o{ EMPLOYEE : "manages"
    USER ||--o{ USER_ROLE : "has"
    ROLE ||--o{ USER_ROLE : "assigned"

    CANDIDATE ||--o{ APPLICATION : "submits"
    POSITION ||--o{ APPLICATION : "receives"
    APPLICATION_STAGE ||--o{ APPLICATION : "current_stage"
    USER ||--o{ APPLICATION : "owns"

    APPLICATION ||--o{ OFFER : "produces"
    OFFER ||--o{ OFFER_RESPONSE : "receives"

    CANDIDATE ||--o{ ONBOARDING_DRAFT : "has"
    OFFER o|--o{ ONBOARDING_DRAFT : "sources"
    ONBOARDING_TEMPLATE ||--o{ ONBOARDING_DRAFT : "used_by"
    ONBOARDING_TEMPLATE ||--o{ TASK_TEMPLATE : "contains"
    ONBOARDING_DRAFT ||--o{ FIELD_MAPPING : "has"
    TASK_TEMPLATE o|--o{ ONBOARDING_TASK : "generates"

    PROCESS_AUTOMATION ||--o{ PROCESS_AUTOMATION_OFFER : "has"
    OFFER ||--o{ PROCESS_AUTOMATION_OFFER : "involved_in"
    PROCESS_AUTOMATION ||--o{ PROCESS_AUTOMATION_DRAFT : "has"
    ONBOARDING_DRAFT ||--o{ PROCESS_AUTOMATION_DRAFT : "involved_in"
    PROCESS_AUTOMATION ||--o{ PROCESS_AUTOMATION_TEMPLATE : "has"
    ONBOARDING_TEMPLATE ||--o{ PROCESS_AUTOMATION_TEMPLATE : "involved_in"
    PROCESS_AUTOMATION ||--o{ PROCESS_AUTOMATION_ONBOARDING_TASK : "has"
    ONBOARDING_TASK ||--o{ PROCESS_AUTOMATION_ONBOARDING_TASK : "involved_in"

    CANDIDATE ||--o| EMPLOYEE : "becomes"
    EMPLOYEE ||--o{ ONBOARDING_CASE : "has"
    OFFER ||--o| ONBOARDING_CASE : "starts"
    ONBOARDING_TEMPLATE ||--o{ ONBOARDING_CASE : "used_by"
    ONBOARDING_STAGE ||--o{ ONBOARDING_CASE : "current_stage"

    ONBOARDING_CASE ||--o{ ONBOARDING_TASK : "contains"
    ONBOARDING_TASK ||--o{ TASK_ASSIGNMENT : "has"
    ROLE ||--o{ TASK_ASSIGNMENT : "responsible_as"
    USER o|--o{ TASK_ASSIGNMENT : "assigned_to"
    ONBOARDING_CASE ||--o{ READINESS_CHECKLIST_ITEM : "has"

    ONBOARDING_CASE ||--o{ ONBOARDING_CASE_MILESTONE : "tracks"
    ONBOARDING_MILESTONE ||--o{ ONBOARDING_CASE_MILESTONE : "defines"
    ONBOARDING_CASE ||--o{ CHECK_IN : "has"
    ONBOARDING_CASE_MILESTONE ||--o{ CHECK_IN : "includes"
    USER ||--o{ CHECK_IN : "reviews"

    ONBOARDING_CASE ||--o{ FEEDBACK : "receives"
    ONBOARDING_CASE_MILESTONE ||--o{ FEEDBACK : "relates_to"
    USER ||--o{ FEEDBACK : "writes"

    ONBOARDING_CASE ||--o{ ONBOARDING_BLOCKER : "has"
    ONBOARDING_TASK o|--o{ ONBOARDING_BLOCKER : "may_cause"
```
### 3. Core ERD Appllication Management
```mermaid
erDiagram

    CANDIDATE {
        bigint candidate_id PK
        varchar first_name
        varchar middle_name
        varchar last_name
        varchar email
    }

    POSITION {
        bigint position_id PK
        varchar position_name
    }

    APPLICATION_STAGE {
        bigint application_stage_id PK
        varchar stage_name
        int stage_order
    }

    USER {
        bigint user_id PK
        varchar first_name
        varchar middle_name
        varchar last_name
    }

    APPLICATION {
        bigint application_id PK
        bigint candidate_id FK
        bigint position_id FK
        bigint application_stage_id FK
        bigint owner_user_id FK
        datetime applied_at
        varchar status
    }

    CANDIDATE ||--o{ APPLICATION : submits

    POSITION ||--o{ APPLICATION : receives

    APPLICATION_STAGE ||--o{ APPLICATION : current_stage

    USER ||--o{ APPLICATION : owns
```

### 4. Core ERD Offer Management
```mermaid
erDiagram

    CANDIDATE {
        bigint candidate_id PK
        varchar first_name
        varchar middle_name
        varchar last_name
        varchar email
    }

    POSITION {
        bigint position_id PK
        varchar position_name
    }

    APPLICATION_STAGE {
        bigint application_stage_id PK
        varchar stage_name
        int stage_order
    }

    USER {
        bigint user_id PK
        varchar first_name
        varchar middle_name
        varchar last_name
    }

    APPLICATION {
        bigint application_id PK
        bigint candidate_id FK
        bigint position_id FK
        bigint application_stage_id FK
        bigint owner_user_id FK
        datetime applied_at
        varchar status
        varchar evaluation
    }

    OFFER {
        bigint offer_id PK
        varchar offer_code
        bigint application_id FK
        varchar status
        datetime response_deadline
        date final_start_date
    }

    OFFER_RESPONSE {
        bigint offer_response_id PK
        bigint offer_id FK
        varchar response_type
        datetime responded_at
    }

    CANDIDATE ||--o{ APPLICATION : submits
    POSITION ||--o{ APPLICATION : receives
    APPLICATION_STAGE ||--o{ APPLICATION : contains
    USER ||--o{ APPLICATION : owns

    APPLICATION ||--o{ OFFER : produces
    OFFER ||--o{ OFFER_RESPONSE : receives
```

### 5. Core ERD Automation Hub
```mermaid
erDiagram

    CANDIDATE {
        bigint candidate_id PK
        varchar first_name
        varchar middle_name
        varchar last_name
        varchar email
    }

    OFFER {
        bigint offer_id PK
        bigint application_id FK
        varchar offer_code
        varchar status
        datetime response_deadline
        date final_start_date
    }

    ONBOARDING_DRAFT {
        bigint onboarding_draft_id PK
        bigint candidate_id FK
        bigint source_offer_id FK
        bigint onboarding_template_id FK
        varchar source_type
        varchar status
        datetime updated_at
    }

    ONBOARDING_TEMPLATE {
        bigint onboarding_template_id PK
        varchar template_name
        varchar description
        varchar status
    }

    TASK_TEMPLATE {
        bigint task_template_id PK
        bigint onboarding_template_id FK
        varchar task_name
    }

    ONBOARDING_TASK {
        bigint onboarding_task_id PK
        bigint onboarding_case_id FK
        bigint task_template_id FK
        varchar task_name
        varchar description
        varchar status
        varchar priority
        datetime due_at
        datetime created_at
        datetime completed_at
    }

    FIELD_MAPPING {
        bigint field_mapping_id PK
        bigint onboarding_draft_id FK
        varchar source_field_name
        varchar target_field_name
        decimal confidence_score
        varchar status
    }

    PROCESS_AUTOMATION {
        bigint process_automation_id PK
        varchar name
        varchar description
        int display_order
        boolean is_enabled
    }

    PROCESS_AUTOMATION_OFFER {
        bigint process_automation_id PK, FK
        bigint offer_id PK, FK
    }

    PROCESS_AUTOMATION_DRAFT {
        bigint process_automation_id PK, FK
        bigint onboarding_draft_id PK, FK
    }

    PROCESS_AUTOMATION_TEMPLATE {
        bigint process_automation_id PK, FK
        bigint onboarding_template_id PK, FK
    }

    PROCESS_AUTOMATION_ONBOARDING_TASK {
        bigint process_automation_id PK, FK
        bigint onboarding_task_id PK, FK
    }

    CANDIDATE ||--o{ ONBOARDING_DRAFT : has

    OFFER o|--o{ ONBOARDING_DRAFT : sources

    ONBOARDING_TEMPLATE ||--o{ ONBOARDING_DRAFT : used_by

    ONBOARDING_TEMPLATE ||--o{ TASK_TEMPLATE : contains

    ONBOARDING_DRAFT ||--o{ FIELD_MAPPING : has

    TASK_TEMPLATE o|--o{ ONBOARDING_TASK : generates

    PROCESS_AUTOMATION ||--o{ PROCESS_AUTOMATION_OFFER : has
    OFFER ||--o{ PROCESS_AUTOMATION_OFFER : involved_in

    PROCESS_AUTOMATION ||--o{ PROCESS_AUTOMATION_DRAFT : has
    ONBOARDING_DRAFT ||--o{ PROCESS_AUTOMATION_DRAFT : involved_in

    PROCESS_AUTOMATION ||--o{ PROCESS_AUTOMATION_TEMPLATE : has
    ONBOARDING_TEMPLATE ||--o{ PROCESS_AUTOMATION_TEMPLATE : involved_in

    PROCESS_AUTOMATION ||--o{ PROCESS_AUTOMATION_ONBOARDING_TASK : has
    ONBOARDING_TASK ||--o{ PROCESS_AUTOMATION_ONBOARDING_TASK : involved_in
```

### 6. Core ERD Onboarding Board 
```mermaid
erDiagram

    CANDIDATE {
        bigint candidate_id PK
        varchar first_name
        varchar middle_name
        varchar last_name
        varchar email
    }

    OFFER {
        bigint offer_id PK
        bigint application_id FK
        varchar offer_code
        varchar status
        date final_start_date
    }

    EMPLOYEE {
        bigint employee_id PK
        bigint candidate_id FK
        bigint manager_user_id FK
        varchar work_location
    }

    ONBOARDING_TEMPLATE {
        bigint onboarding_template_id PK
        varchar template_name
        varchar status
    }

    ONBOARDING_STAGE {
        bigint onboarding_stage_id PK
        varchar stage_name
        int stage_order
        varchar description
    }

    ONBOARDING_CASE {
        bigint onboarding_case_id PK
        bigint offer_id FK
        bigint employee_id FK
        bigint onboarding_template_id FK
        bigint onboarding_stage_id FK
        varchar priority
        datetime created_at
        datetime completed_at
    }

    ONBOARDING_TASK {
        bigint onboarding_task_id PK
        bigint onboarding_case_id FK
        varchar task_name
        varchar status
        varchar priority
        datetime due_at
    }

    TASK_ASSIGNMENT {
        bigint task_assignment_id PK
        bigint onboarding_task_id FK
        bigint assigned_user_id FK
    }

    READINESS_CHECKLIST_ITEM {
        bigint readiness_item_id PK
        bigint onboarding_case_id FK
        varchar item_name
        varchar status
        datetime completed_at
    }

    ONBOARDING_BLOCKER {
        bigint blocker_id PK
        bigint onboarding_case_id FK
        bigint onboarding_task_id FK
        varchar description
        varchar status
        datetime reported_at
        datetime resolved_at
    }

    USER {
        bigint user_id PK
        varchar first_name
        varchar middle_name
        varchar last_name
    }

    ROLE {
        bigint role_id PK
        varchar role_name
    }

    CANDIDATE ||--o| EMPLOYEE : becomes

    USER ||--o{ EMPLOYEE : manages

    EMPLOYEE ||--o{ ONBOARDING_CASE : has

    OFFER ||--o| ONBOARDING_CASE : starts

    ONBOARDING_TEMPLATE ||--o{ ONBOARDING_CASE : used_by

    ONBOARDING_STAGE ||--o{ ONBOARDING_CASE : current_stage

    ONBOARDING_CASE ||--o{ ONBOARDING_TASK : contains

    ONBOARDING_TASK ||--o{ TASK_ASSIGNMENT : has

    ROLE ||--o{ TASK_ASSIGNMENT : responsible_as

    USER o|--o{ TASK_ASSIGNMENT : assigned_to

    ONBOARDING_CASE ||--o{ READINESS_CHECKLIST_ITEM : has

    ONBOARDING_CASE ||--o{ ONBOARDING_BLOCKER : has

    ONBOARDING_TASK o|--o{ ONBOARDING_BLOCKER : may_cause
```

### 7. Core ERD Assigned Task by Role
```mermaid
erDiagram

    POSITION {
        bigint position_id PK
        varchar position_name
    }

    EMPLOYEE {
        bigint employee_id PK
        bigint position_id FK
        varchar first_name
        varchar middle_name
        varchar last_name
    }

    ONBOARDING_CASE {
        bigint onboarding_case_id PK
        bigint employee_id FK
    }

    TASK_TEMPLATE {
        bigint task_template_id PK
        varchar task_name
    }

    ONBOARDING_TASK {
        bigint onboarding_task_id PK
        bigint onboarding_case_id FK
        bigint task_template_id FK
        varchar task_name
        varchar description
        varchar status
        varchar priority
        datetime due_at
        datetime created_at
        datetime completed_at
    }

    USER {
        bigint user_id PK
        bigint team_id FK
        varchar first_name
        varchar middle_name
        varchar last_name
    }

    ROLE {
        bigint role_id PK
        varchar role_name
    }

    USER_ROLE {
        bigint user_id PK, FK
        bigint role_id PK, FK
    }

    TASK_ASSIGNMENT {
        bigint task_assignment_id PK
        bigint onboarding_task_id FK
        bigint assigned_user_id FK
    }

    POSITION ||--o{ EMPLOYEE : held_by

    EMPLOYEE ||--o{ ONBOARDING_CASE : has

    ONBOARDING_CASE ||--o{ ONBOARDING_TASK : contains

    TASK_TEMPLATE o|--o{ ONBOARDING_TASK : generates

    ONBOARDING_TASK ||--o{ TASK_ASSIGNMENT : has

    USER ||--o{ TASK_ASSIGNMENT : assigned_to

    USER ||--o{ USER_ROLE : has

    ROLE ||--o{ USER_ROLE : assigned
```

### 8. Core ERD Tracking Progress 
```mermaid
erDiagram

    DEPARTMENT {
        bigint department_id PK
        varchar department_name
    }

    POSITION {
        bigint position_id PK
        varchar position_name
    }

    USER {
        bigint user_id PK
        varchar first_name
        varchar middle_name
        varchar last_name
    }

    EMPLOYEE {
        bigint employee_id PK
        bigint department_id FK
        bigint position_id FK
        bigint manager_user_id FK
        date start_date
    }

    ONBOARDING_CASE {
        bigint onboarding_case_id PK
        bigint employee_id FK
        datetime created_at
        datetime completed_at
    }

    ONBOARDING_MILESTONE {
        bigint milestone_id PK
        varchar milestone_name
        int target_day
        int sequence_order
    }

    ONBOARDING_CASE_MILESTONE {
        bigint case_milestone_id PK
        bigint onboarding_case_id FK
        bigint milestone_id FK
        datetime scheduled_at
        varchar status
        datetime completed_at
    }

    CHECK_IN {
        bigint check_in_id PK
        bigint onboarding_case_id FK
        bigint case_milestone_id FK
        bigint reviewer_user_id FK
        datetime scheduled_at
        varchar status
        datetime completed_at
    }

    FEEDBACK {
        bigint feedback_id PK
        bigint onboarding_case_id FK
        bigint case_milestone_id FK
        bigint author_user_id FK
        varchar feedback_type
        text content
        datetime created_at
    }

    ONBOARDING_TASK {
        bigint onboarding_task_id PK
        bigint onboarding_case_id FK
        varchar task_name
        varchar status
        datetime due_at
    }

    ONBOARDING_BLOCKER {
        bigint blocker_id PK
        bigint onboarding_case_id FK
        bigint onboarding_task_id FK
        varchar description
        varchar status
        datetime reported_at
        datetime resolved_at
    }

    DEPARTMENT ||--o{ EMPLOYEE : contains

    POSITION ||--o{ EMPLOYEE : held_by

    USER ||--o{ EMPLOYEE : manages

    EMPLOYEE ||--o{ ONBOARDING_CASE : has

    ONBOARDING_CASE ||--o{ ONBOARDING_CASE_MILESTONE : tracks

    ONBOARDING_MILESTONE ||--o{ ONBOARDING_CASE_MILESTONE : defines

    ONBOARDING_CASE ||--o{ CHECK_IN : has

    ONBOARDING_CASE_MILESTONE ||--o{ CHECK_IN : includes

    USER ||--o{ CHECK_IN : reviews

    ONBOARDING_CASE ||--o{ FEEDBACK : receives

    ONBOARDING_CASE_MILESTONE ||--o{ FEEDBACK : relates_to

    USER ||--o{ FEEDBACK : writes

    ONBOARDING_CASE ||--o{ ONBOARDING_TASK : contains

    ONBOARDING_CASE ||--o{ ONBOARDING_BLOCKER : has

    ONBOARDING_TASK o|--o{ ONBOARDING_BLOCKER : may_cause
```