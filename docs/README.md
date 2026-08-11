# HR Platform - Onboarding 

![alt text](Sitemap.png)
# UI/UX

https://www.figma.com/design/zdmEvaHXfHBNyfO5F5zDxh/HR-Platform?node-id=0-1&p=f&t=0EqTrWfMMwvZHJOq-0

# BPMN
![alt text](Onboarding.png)

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
        varchar full_name
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
        varchar full_name
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
        varchar full_name
    }

    POSITION {
        bigint position_id PK
        varchar position_name
    }

    APPLICATION_STAGE {
        bigint application_stage_id PK
        varchar stage_name
    }

    USER {
        bigint user_id PK
        varchar full_name
    }

    APPLICATION {
        bigint application_id PK
        bigint candidate_id FK
        bigint position_id FK
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

### 5. Core ERD Intake Review
```mermaid
erDiagram

    CANDIDATE {
        bigint candidate_id PK
    }

    OFFER {
        bigint offer_id PK
    }

    ONBOARDING_DRAFT {
        bigint onboarding_draft_id PK
        bigint candidate_id FK
        bigint source_offer_id FK
        varchar status
    }

    ONBOARDING_TEMPLATE {
        bigint onboarding_template_id PK
        varchar template_name
    }

    TASK_TEMPLATE {
        bigint task_template_id PK
        varchar task_name
    }

    ONBOARDING_TASK {
        bigint onboarding_task_id PK
        varchar task_name
    }

    FIELD_MAPPING {
        bigint field_mapping_id PK
        bigint onboarding_draft_id FK
        varchar source_field_name
        varchar target_field_name
        decimal confidence_score
    }

    PROCESS_AUTOMATION {
        bigint process_automation_id PK
        varchar name
        boolean is_enabled
    }

    PROCESS_AUTOMATION_OFFER {
        bigint process_automation_id FK
        bigint offer_id FK
    }

    PROCESS_AUTOMATION_DRAFT {
        bigint process_automation_id FK
        bigint onboarding_draft_id FK
    }

    PROCESS_AUTOMATION_TEMPLATE {
        bigint process_automation_id FK
        bigint onboarding_template_id FK
    }

    PROCESS_AUTOMATION_ONBOARDING_TASK {
        bigint process_automation_id FK
        bigint onboarding_task_id FK
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
    }

    OFFER {
        bigint offer_id PK
        date final_start_date
    }

    EMPLOYEE {
        bigint employee_id PK
        bigint candidate_id FK
    }

    ONBOARDING_TEMPLATE {
        bigint onboarding_template_id PK
        varchar template_name
    }

    ONBOARDING_STAGE {
        bigint onboarding_stage_id PK
        varchar stage_name
    }

    ONBOARDING_CASE {
        bigint onboarding_case_id PK
        bigint offer_id FK
        bigint employee_id FK
        bigint onboarding_stage_id FK
        varchar priority
    }

    ONBOARDING_TASK {
        bigint onboarding_task_id PK
        bigint onboarding_case_id FK
        varchar task_name
        varchar status
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
    }

    ONBOARDING_BLOCKER {
        bigint blocker_id PK
        bigint onboarding_case_id FK
        varchar status
    }

    USER {
        bigint user_id PK
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
    }

    EMPLOYEE {
        bigint employee_id PK
        bigint position_id FK
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
        varchar status
    }

    USER {
        bigint user_id PK
        bigint team_id FK
    }

    ROLE {
        bigint role_id PK
        varchar role_name
    }

    USER_ROLE {
        bigint user_id FK
        bigint role_id FK
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
    }

    POSITION {
        bigint position_id PK
    }

    USER {
        bigint user_id PK
    }

    EMPLOYEE {
        bigint employee_id PK
        bigint department_id FK
        bigint position_id FK
    }

    ONBOARDING_CASE {
        bigint onboarding_case_id PK
        bigint employee_id FK
        varchar status
    }

    ONBOARDING_MILESTONE {
        bigint milestone_id PK
        varchar milestone_name
        int target_day
    }

    ONBOARDING_CASE_MILESTONE {
        bigint case_milestone_id PK
        bigint onboarding_case_id FK
        bigint milestone_id FK
        varchar status
    }

    CHECK_IN {
        bigint check_in_id PK
        bigint onboarding_case_id FK
        bigint case_milestone_id FK
        bigint reviewer_user_id FK
        varchar status
    }

    FEEDBACK {
        bigint feedback_id PK
        bigint onboarding_case_id FK
        bigint case_milestone_id FK
        bigint author_user_id FK
        varchar feedback_type
    }

    ONBOARDING_TASK {
        bigint onboarding_task_id PK
        bigint onboarding_case_id FK
        varchar status
    }

    ONBOARDING_BLOCKER {
        bigint blocker_id PK
        bigint onboarding_case_id FK
        bigint onboarding_task_id FK
        varchar status
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