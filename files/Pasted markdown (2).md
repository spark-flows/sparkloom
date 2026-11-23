# HIGH-PRIORITY EXECUTION OVERRIDE: BUILD THE COMPLETE HRMS FIRST

This instruction changes the implementation priority of the existing **Kidswear Manufacturing SaaS ERP** project.

## 1. IMMEDIATE PRIORITY CHANGE

Immediately pause all unfinished non-HRMS development from the previous roadmap.

Do not continue with manufacturing, inventory, sales, accounting, AI, or any other pending phase until the complete HRMS module described below is implemented and verified.

Important:

* Do not delete, reset, revert, or discard any existing work.
* Do not create a separate project or repository.
* Do not recreate the monorepo.
* Do not replace the current architecture.
* Do not unnecessarily rewrite working code.
* Do not overwrite existing database data.
* Do not duplicate existing modules, components, APIs, tables, services, or utilities.
* Preserve all existing uncommitted and committed work.
* Continue inside the same project using the same codebase, folder structure, design system, authentication, permissions, APIs, database, events, workflows, audit system, notifications, and coding conventions.
* The actual repository is the source of truth. If the repository differs from the original master prompt, follow the current working repository.
* Extend existing foundations instead of introducing a second implementation.
* If an HRMS-related feature already exists, inspect and complete it rather than rebuilding it blindly.

This instruction overrides only the previous implementation order. All previous architectural, security, quality, multi-tenant, responsive UI, workflow, event-driven, audit, notification, and testing requirements remain active.

The new first priority is:

> Build a complete, production-ready, multi-tenant HRMS for web and mobile, with real backend APIs, database integration, permissions, workflows, reports, payroll, attendance, time tracking, recruitment, performance management, assets, and employee self-service.

Do not resume the previously paused roadmap until HRMS is complete and verified.

---

# 2. FIRST ACTION: AUDIT BEFORE IMPLEMENTATION

Before making major changes:

1. Inspect the complete repository.
2. Check the current Git status and preserve existing changes.
3. Inspect the current web, mobile, API, worker, shared packages, database schema, migrations, seeders, authentication, permissions, events, workflows, notifications, audit logs, and UI components.
4. Identify what is complete, partial, broken, duplicated, or missing.
5. Check whether any HR, employee, user, attendance, payroll, asset, project, or recruitment functionality already exists.
6. Reuse compatible existing code.
7. Update the main implementation plan and mark previous non-HRMS work as `PAUSED – HRMS PRIORITY`.
8. Create or update:

```text
docs/HRMS_IMPLEMENTATION_PLAN.md
docs/HRMS_REQUIREMENTS_MATRIX.md
docs/HRMS_ARCHITECTURE.md
docs/HRMS_DATABASE.md
docs/HRMS_PERMISSIONS.md
docs/HRMS_WORKFLOWS.md
docs/HRMS_EVENTS.md
docs/HRMS_API.md
docs/HRMS_MOBILE.md
docs/HRMS_REPORTS.md
```

The requirements matrix must track every requirement as:

```text
NOT_STARTED
IN_PROGRESS
IMPLEMENTED
TESTED
VERIFIED
BLOCKED
```

Do not stop after analysis or documentation. After the audit, immediately begin implementation.

---

# 3. REQUIRED HRMS PORTALS

Build the following connected experiences using one shared backend and permission system:

1. HR and Tenant Admin Portal
2. Employee Self-Service Portal
3. Manager Self-Service Portal
4. Payroll and Finance Workspace
5. Recruiter and Interviewer Workspace
6. Candidate/Careers Portal
7. Web Employee Portal
8. Mobile Employee Application
9. Mobile Manager and Approval Experience
10. Kiosk, QR, biometric, and device-integration-ready attendance architecture

All portals must use real APIs, tenant-isolated data, audit logs, workflow approvals, notifications, and permission checks.

---

# 4. MULTI-TENANT ORGANIZATION MANAGEMENT

Support:

* Tenant/company
* Legal entities
* Business units
* Branches
* Factories
* Offices
* Warehouses
* Work locations
* Departments
* Sub-departments
* Teams
* Cost centres
* Profit centres
* Designations
* Job titles
* Grades
* Bands
* Positions and sanctioned positions
* Reporting hierarchy
* Dotted-line managers
* Employee categories
* Employment types
* Worker types
* Contractors
* Interns
* Consultants
* Work locations
* Shift groups
* Holiday calendars
* Weekly-off policies
* Payroll groups
* Leave groups
* Attendance groups

Provide an interactive organization chart and position/headcount view.

Every tenant-owned record must be isolated using the existing tenant architecture. Never trust a tenant ID sent by the frontend.

---

# 5. COMPLETE EMPLOYEE LIFECYCLE

Implement the complete employee lifecycle.

## Employee Profile

Support:

* Employee number with configurable number series
* Profile photo
* Personal information
* Contact information
* Current and permanent address
* Date of birth
* Gender
* Marital status
* Blood group
* Nationality
* Emergency contacts
* Dependants
* Nominees
* Education
* Previous employment
* Skills
* Certifications
* Languages
* Bank accounts
* Tax details
* Government and statutory identifiers
* Passport, visa and work permit
* Medical information with restricted permissions
* Uploaded documents
* Digital acknowledgements
* Job and employment details
* Department, designation, grade and manager
* Location, shift, cost centre and payroll group
* Joining date
* Confirmation date
* Probation details
* Contract details
* Notice period
* Compensation history
* Transfer history
* Promotion history
* Manager history
* Employment status
* Custom fields through the existing dynamic form system

Sensitive information such as salary, bank, tax, medical, identification, and disciplinary data must use strict field-level permissions.

## Lifecycle Actions

Support:

* Preboarding
* Joining
* Onboarding
* Probation
* Confirmation
* Extension of probation
* Transfer
* Deputation
* Promotion
* Demotion
* Salary revision
* Role change
* Department change
* Manager change
* Location change
* Employment-type change
* Contract renewal
* Suspension
* Resignation
* Termination
* Retirement
* Absconding
* Exit process
* Clearance
* Full and final settlement
* Exit interview
* Alumni records
* Rehire

All employment changes must be effective-dated and retain complete history.

---

# 6. ONBOARDING AND OFFBOARDING

Build configurable onboarding and offboarding workflows.

Support:

* Checklist templates by role, department, location, and employment type
* Document collection
* Identity verification
* Offer acceptance
* Policy acknowledgement
* E-signature-ready documents
* Asset allocation
* Account and access requests
* Department tasks
* Manager tasks
* HR tasks
* IT tasks
* Training assignments
* Buddy assignment
* Probation goals
* Due dates and reminders
* Progress tracking
* Escalations
* Exit checklist
* Asset return
* Access revocation
* Knowledge transfer
* Payroll clearance
* Department clearance
* Final settlement
* Experience and relieving letters

---

# 7. EMPLOYEE AND MANAGER SELF-SERVICE

Employees must be able to:

* View and update permitted profile fields
* Upload documents
* View organization directory
* View reporting hierarchy
* View shifts and rosters
* Start, pause, resume, and stop work timers
* View time entries and timesheets
* Request time corrections
* Punch attendance
* Request attendance regularization
* Apply for leave
* View leave balances
* View holidays
* Submit expense and travel requests
* View salary structure
* View and download payslips
* Submit tax declarations and proofs
* View assigned assets
* Request asset support or return
* View goals and reviews
* Provide feedback
* Access assigned learning
* View letters and HR documents
* Raise HR requests and grievances
* View announcements and notifications
* Resign through a controlled workflow

Managers must be able to:

* View their reporting team
* View team availability
* View attendance exceptions
* Approve or reject requests
* Review timesheets
* Manage rosters
* Assign projects and tasks
* Review goals and performance
* Initiate employee lifecycle actions
* View only authorized compensation data
* Monitor team overtime and capacity
* Delegate approvals during absence

---

# 8. ATTENDANCE MANAGEMENT

Build a production-grade attendance system.

Support:

* Web punch-in and punch-out
* Mobile punch-in and punch-out
* Kiosk-ready attendance
* QR attendance
* Biometric device/import integration
* API-based attendance ingestion
* Manual attendance entry with approval
* Work from office
* Work from home
* Field duty
* On-duty attendance
* Business travel
* Client-site work
* Multiple punches per day
* Break punches
* Overnight and cross-midnight shifts
* Flexible shifts
* Fixed shifts
* Rotational shifts
* Split shifts
* Shift roster planning
* Shift swaps
* Grace periods
* Late arrival
* Early departure
* Half day
* Full day
* Absence
* Weekly off
* Paid and unpaid breaks
* Overtime
* Compensatory off
* Missed punch
* Attendance regularization
* Manager correction
* Attendance lock and unlock
* Monthly attendance closure
* Geofencing
* Location accuracy
* Approved work locations
* Device and IP policies
* Employee timezone and tenant timezone
* Facial-verification-ready architecture where legally allowed
* Offline punch queue with safe synchronization
* Duplicate prevention and idempotency
* Complete audit history

Attendance calculations must use configurable policies. Do not hardcode one attendance rule for every tenant.

---

# 9. EMPLOYEE WORK TIMER AND TIME TRACKING

This is a critical priority and must work on both web and mobile.

## Timer Functions

Employees must be able to:

* Start work
* Pause work
* Resume work
* Start and end breaks
* Stop work
* Select a project
* Select a task
* Select a cost centre
* Mark time as billable or non-billable
* Add work notes
* Add attachments where permitted
* Switch between tasks without losing time
* View the currently running timer
* View today’s accumulated time
* View weekly accumulated time
* Submit timesheets
* Request correction of completed entries

## Timer Reliability Rules

* The backend server time is authoritative.
* Never calculate final worked time only from a mobile counter.
* Store server-side start, pause, resume, break, and stop timestamps.
* The timer must continue correctly when the app is minimized, closed, restarted, or the employee logs in again.
* An employee must see the same active timer after logging in on another authorized device.
* Prevent multiple active timers unless the tenant policy explicitly allows them.
* Stop, pause, and resume operations must be idempotent.
* Handle weak internet and offline events safely.
* Queue offline actions with device timestamps and sync metadata.
* Detect and resolve conflicts without double-counting time.
* Track timezone, device, IP, optional GPS, and source.
* GPS tracking must be policy-controlled and consent-aware.
* Store original records and correction history.
* Manual changes must require a reason and configured approval.
* Managers must not silently alter time records without an audit entry.
* Locked payroll periods must prevent unauthorized time changes.
* Break, overtime, rounding, minimum-hours, and maximum-hours rules must be configurable.

## Required Time Reports

Provide real reports for:

* Daily
* Weekly
* Monthly
* Yearly
* Custom date range
* Employee
* Team
* Manager
* Department
* Branch
* Location
* Shift
* Project
* Task
* Cost centre
* Billable versus non-billable
* Regular hours
* Break hours
* Overtime
* Late time
* Early-departure time
* Missing time
* Idle/unallocated time where policy permits
* Approved, pending, rejected, corrected, and locked entries

Reports must support filters, grouping, totals, drill-down, saved views, charts, pagination, and CSV/XLSX/PDF export.

---

# 10. PROJECTS, TASKS, AND TIMESHEETS

Because time tracking may be project-based, implement an HRMS-integrated project and task layer.

Support:

* Project creation
* Project manager
* Members
* Client or internal project
* Start and end dates
* Budgeted hours
* Billable settings
* Cost centres
* Milestones
* Tasks and subtasks
* Task assignments
* Estimated hours
* Actual hours
* Priority and status
* Timesheet submission
* Weekly timesheet
* Approval and rejection
* Timesheet locking
* Missing-timesheet reminders
* Project utilization
* Employee utilization
* Capacity planning
* Project labour cost
* Payroll and accounting integration

Do not attempt to replace the ERP’s broader production workflow. This module is for employee work allocation, HR capacity, and timesheet reporting.

---

# 11. LEAVE MANAGEMENT

Support:

* Unlimited configurable leave types
* Leave policies by employee group
* Paid and unpaid leave
* Full-day, half-day, and hourly leave
* Accrual
* Proration
* Carry-forward
* Expiry
* Encashment
* Negative balance
* Advance leave
* Compensatory off
* Maternity, paternity, adoption, bereavement, sick and casual leave
* Probation restrictions
* Notice-period restrictions
* Sandwich rules
* Prefix and suffix holiday rules
* Blackout dates
* Minimum and maximum leave
* Supporting documents
* Cancellation
* Recall
* Extension
* Multi-level approval
* Delegated approval
* Team leave calendar
* Leave balance ledger
* Leave forecast
* Payroll loss-of-pay integration
* Attendance synchronization
* Calendar synchronization
* Notifications and reminders

Every balance adjustment must create a ledger entry and audit record.

---

# 12. HOLIDAY AND WORK CALENDAR

Support:

* Multiple holiday calendars
* Country, state, location, factory and branch calendars
* Public holidays
* Company holidays
* Optional/restricted holidays
* Floating holidays
* Weekly offs
* Alternate Saturdays
* Shift-specific holidays
* Employee holiday eligibility
* Holiday import
* Calendar view
* Mobile calendar
* Leave and attendance integration

---

# 13. PAYROLL, COMPENSATION, AND BENEFITS

Build a real payroll engine, not a payslip mockup.

## Payroll Core

Support:

* Multiple payroll groups
* Monthly, weekly, biweekly and custom pay cycles
* Salary structures
* CTC
* Gross pay
* Net pay
* Fixed and variable components
* Earnings
* Deductions
* Employer contributions
* Benefits
* Allowances
* Reimbursements
* Bonuses
* Incentives
* Commissions
* Overtime
* Arrears
* Retroactive changes
* Salary revisions
* Loss of pay
* Proration
* Joining and separation calculations
* Loans and advances
* Recovery schedules
* Garnishment-ready architecture
* One-time payments and deductions
* Payroll adjustments
* Off-cycle payroll
* Full and final settlement
* Gratuity calculation
* Leave encashment
* Notice-pay recovery
* Payroll validation
* Maker-checker approval
* Payroll locking
* Reopening with authorization
* Payslip generation
* Bulk payslip publishing
* Bank transfer files
* Payment advice
* Payroll journal entries
* Cost-centre allocation
* Payroll comparison and variance reports

Payroll must integrate with approved attendance, leave, overtime, timesheets, expenses, benefits, loans, and employee lifecycle changes.

## India-First Statutory Support

Prepare configurable, effective-dated support for:

* Provident Fund
* ESI
* Professional Tax
* TDS
* Labour Welfare Fund
* Gratuity
* Statutory bonus
* Tax regimes
* Investment declarations
* Proof submission
* Form 16-ready data
* Quarterly return-ready data
* State-specific rules

Do not hardcode statutory rates permanently. Store versioned rules with effective dates and allow future multi-country payroll adapters.

## Compensation and Benefits

Support:

* Salary bands
* Grade-based structures
* Compensation planning
* Increment cycles
* Promotion increases
* Budget allocation
* Merit increases
* Variable-pay plans
* Benefit plans
* Benefit eligibility
* Employee benefit enrollment
* Compensation letters
* Restricted compensation analytics

---

# 14. RECRUITMENT AND APPLICANT TRACKING

Build a complete recruitment system.

Support:

* Manpower and headcount planning
* Position control
* Job requisitions
* Budget approval
* Hiring approval
* Job opening creation
* Job descriptions
* Job templates
* Internal jobs
* External jobs
* Public careers page
* Candidate application portal
* Employee referrals
* Recruitment agencies
* Candidate sources
* Resume upload and parsing-ready architecture
* Duplicate candidate detection
* Candidate talent pool
* Tags and skills
* Screening questions
* Candidate pipeline
* Configurable hiring stages
* Shortlisting
* Assessments
* Interview scheduling
* Calendar integration
* Interview panels
* Interview scorecards
* Feedback and rating
* Background verification workflow
* Reference checks
* Salary negotiation
* Offer approval
* Offer-letter templates
* Offer acceptance and rejection
* Joining-date tracking
* Preboarding
* Candidate-to-employee conversion
* Rejection and hold reasons
* Recruitment communication history
* Recruitment analytics
* Time-to-hire
* Time-to-fill
* Cost-per-hire
* Source effectiveness
* Diversity metrics where legally appropriate

Recruiters and interviewers must also have mobile-ready views for schedules, candidate profiles, scorecards, feedback, and approvals.

---

# 15. PERFORMANCE MANAGEMENT

Implement complete Performance Management.

Support:

* Performance cycles
* Probation reviews
* Goal setting
* SMART goals
* OKRs
* KPIs
* Goal libraries
* Individual goals
* Team goals
* Organization goals
* Goal cascading
* Weightages
* Progress updates
* Evidence and attachments
* Competency frameworks
* Role-based competencies
* Self-review
* Manager review
* Peer review
* Upward review
* 360-degree feedback
* Continuous feedback
* Check-ins
* One-to-one meetings
* Review reminders
* Rating scales
* Normalization
* Calibration
* Calibration committees
* Final ratings
* Employee acknowledgement
* Appeal workflow
* Performance Improvement Plans
* Development plans
* Promotions and increment recommendations
* Potential assessment
* Nine-box talent grid
* Succession planning
* High-potential employee tracking
* Recognition and awards
* Performance analytics
* Complete review history

Performance data must have strict confidentiality and field-level permission rules.

---

# 16. ASSET MANAGEMENT

Build HR-integrated asset management.

Support:

* Asset categories
* Asset types
* Asset inventory
* Serial numbers
* QR/barcodes
* Vendors
* Purchase information
* Warranty
* Insurance
* Asset condition
* Stock and availability
* Employee allocation
* Department allocation
* Temporary allocation
* Transfer
* Return
* Replacement
* Repair
* Maintenance
* Service history
* Loss
* Theft
* Damage
* Recovery from payroll where approved
* Depreciation-ready data
* Asset audit
* Physical verification
* Asset requests
* Approval workflow
* Employee asset acknowledgement
* Offboarding clearance
* Asset reports
* Mobile QR scanning

---

# 17. EXPENSES AND TRAVEL

Support:

* Expense categories
* Expense policies
* Limits
* Mileage
* Per diem
* Receipts
* OCR-ready architecture
* Expense claims
* Advance requests
* Multi-level approvals
* Rejection and resubmission
* Finance verification
* Reimbursement through payroll or payment
* Corporate-card-ready reconciliation
* Travel requests
* Travel approvals
* Itinerary
* Hotel and transport details
* Travel advance
* Travel settlement
* Policy violations
* Project and cost-centre allocation
* Mobile receipt capture
* Expense analytics

---

# 18. LEARNING, SKILLS, AND CERTIFICATIONS

Support:

* Course catalogue
* Internal and external training
* Training batches
* Trainers
* Enrollment
* Approval
* Attendance
* Assessments
* Completion
* Certificates
* Certificate expiry
* Renewal reminders
* Mandatory training
* Learning paths
* Skills matrix
* Skill gaps
* Training effectiveness
* Development plans
* Employee learning history

---

# 19. ENGAGEMENT, HR HELPDESK, AND EMPLOYEE RELATIONS

Support:

* Announcements
* Policies
* Employee acknowledgements
* Surveys
* Pulse surveys
* Anonymous feedback where enabled
* Recognition
* Birthdays and work anniversaries
* HR helpdesk tickets
* Request categories
* SLA
* Escalation
* Grievances
* Complaints
* Disciplinary cases
* Warnings
* Show-cause notices
* Investigation workflow
* Restricted case access
* Whistleblower-ready confidential workflow
* Employee suggestions
* Exit surveys
* Engagement analytics

---

# 20. DOCUMENTS, LETTERS, AND TEMPLATES

Support:

* Employee document vault
* Document categories
* Expiry tracking
* Version history
* Restricted access
* Offer letters
* Appointment letters
* Confirmation letters
* Transfer letters
* Promotion letters
* Increment letters
* Warning letters
* Experience letters
* Relieving letters
* Salary certificates
* Employment certificates
* Custom templates
* Variable placeholders
* PDF generation
* Bulk generation
* Approval
* E-signature-ready architecture
* Employee acknowledgement

Use the existing object-storage and document infrastructure.

---

# 21. WORKFLOWS, APPROVALS, EVENTS, AND NOTIFICATIONS

All configurable HR processes must use the existing workflow and approval engines.

Examples:

* Leave request
* Attendance correction
* Timesheet submission
* Overtime approval
* Shift change
* Employee transfer
* Promotion
* Salary revision
* Payroll run
* Job requisition
* Offer
* Expense
* Travel
* Asset allocation
* Asset loss
* Performance review
* Resignation
* Offboarding
* Full and final settlement

Support:

* Sequential approvals
* Parallel approvals
* Conditional approvals
* Role-based approvers
* Manager hierarchy
* Amount-based approval
* Delegation
* Escalation
* Reminder
* Reassignment
* Approval history
* Comments and attachments

Publish domain events through the existing event infrastructure, such as:

```text
hr.employee.created
hr.employee.updated
hr.employee.transferred
hr.employee.separated
attendance.punched_in
attendance.punched_out
attendance.regularization_requested
time.timer_started
time.timer_paused
time.timer_resumed
time.timer_stopped
time.timesheet_submitted
leave.requested
leave.approved
payroll.run_started
payroll.run_approved
payroll.payslip_published
recruitment.job_published
recruitment.candidate_moved
recruitment.offer_accepted
performance.review_completed
asset.allocated
asset.returned
```

Use the transactional outbox, idempotent consumers, retries, dead-letter handling, audit logs, real-time UI updates, email, in-app, push, and configurable notification preferences.

---

# 22. DYNAMIC PERMISSIONS

Reuse and extend the existing permission engine.

Permissions must cover:

* Module
* Navigation
* Action
* Record
* Field
* Form
* Report
* Export
* Approval
* Mobile action
* Salary visibility
* Bank and tax visibility
* Medical information
* Performance information
* Recruitment information
* Employee relations cases

Example roles, which must remain configurable rather than hardcoded:

* Tenant Owner
* HR Admin
* HR Manager
* HR Executive
* Payroll Admin
* Recruiter
* Interviewer
* Department Manager
* Reporting Manager
* Finance Approver
* Asset Manager
* Employee
* Contractor
* Auditor

Managers may access only their authorized reporting hierarchy. Employees may access only their own restricted records unless explicitly permitted.

Backend APIs must enforce permissions. Hiding a frontend button is not sufficient.

---

# 23. HRMS NAVIGATION

Generate navigation dynamically based on tenant modules and user permissions.

Recommended navigation:

```text
HRMS
├── Overview
├── My Work
├── People
│   ├── Employees
│   ├── Organization Chart
│   ├── Positions
│   ├── Onboarding
│   ├── Employee Changes
│   └── Offboarding
├── Time & Attendance
│   ├── Live Attendance
│   ├── Attendance Register
│   ├── Shifts
│   ├── Rosters
│   ├── Regularization
│   ├── Overtime
│   ├── Work Timer
│   └── Timesheets
├── Leave & Holidays
├── Payroll
│   ├── Compensation
│   ├── Payroll Runs
│   ├── Payslips
│   ├── Tax
│   ├── Loans
│   ├── Benefits
│   └── Full & Final
├── Recruitment
│   ├── Requisitions
│   ├── Job Openings
│   ├── Candidates
│   ├── Interviews
│   ├── Offers
│   └── Careers
├── Performance
├── Projects & Tasks
├── Assets
├── Expenses & Travel
├── Learning
├── Engagement
├── HR Helpdesk
├── Documents
├── Reports
└── HRMS Settings
```

Reuse the project’s existing premium design system. Do not create a second visual theme.

---

# 24. MOBILE APPLICATION REQUIREMENTS

Use the existing mobile application and framework. If mobile has not yet been created, use the framework selected by the original project architecture. Do not create a second mobile codebase.

Support Android, iOS, phones, and tablets.

## Employee Mobile Features

* Secure login
* Optional biometric app unlock
* Dashboard
* Start, pause, resume, and stop timer
* Persistent running timer
* Break timer
* Project and task selection
* Punch in and out
* Geofenced attendance
* Shift and roster
* Attendance history
* Time reports
* Timesheet submission
* Attendance correction
* Leave application and balance
* Holiday calendar
* Payslips
* Salary and tax documents
* Expense submission with camera capture
* Travel requests
* Assigned assets
* Asset QR scanning
* Goals and reviews
* Feedback and check-ins
* Learning and certificates
* Employee directory
* Profile and documents
* HR helpdesk
* Announcements
* Notifications
* Approvals
* Deep links

## Manager Mobile Features

* Team dashboard
* Live team attendance
* Approval inbox
* Leave approvals
* Time-correction approvals
* Timesheet approvals
* Overtime approvals
* Expense and travel approvals
* Team roster
* Team availability
* Candidate interview schedule
* Interview scorecards
* Performance reviews
* Goal updates
* Asset approvals
* Employee lifecycle approvals

## Mobile Offline Requirements

Allow safe offline operation where appropriate:

* Timer actions
* Attendance punches
* Time notes
* Expense drafts
* Receipt capture
* Selected approvals
* Cached shifts, holidays, and profile data

Use:

* Encrypted local storage
* Offline action queue
* Client-generated idempotency keys
* Retry handling
* Conflict resolution
* Sync status
* Duplicate prevention
* Server reconciliation
* Clear failed-sync feedback

Do not silently lose mobile actions.

---

# 25. REPORTS AND ANALYTICS

All reports must use real database data.

Support:

* Dashboard widgets
* Custom date ranges
* Saved filters
* Saved views
* Drill-down
* Grouping
* Column selection
* Sorting
* Pagination
* Totals
* Charts
* Scheduled report-ready architecture
* CSV export
* XLSX export
* PDF export
* Permission-aware export
* Export audit logging

Required report groups include:

## Workforce

* Headcount
* Active and inactive employees
* New joiners
* Separations
* Turnover and retention
* Department and location distribution
* Diversity where legally appropriate
* Probation
* Contracts and document expiry
* Employee movement
* Span of control

## Attendance and Time

* Daily attendance
* Weekly attendance
* Monthly muster
* Yearly attendance
* Custom-period attendance
* Late and early departures
* Absence
* Overtime
* Breaks
* Missing punches
* Regularizations
* Shift utilization
* Employee time
* Project time
* Task time
* Billable and non-billable hours
* Utilization
* Timesheet compliance

## Leave and Holidays

* Leave balance
* Leave ledger
* Leave utilization
* Loss of pay
* Comp-off
* Leave liability
* Team availability

## Payroll

* Payroll register
* Earnings and deductions
* Salary variance
* Cost-centre payroll cost
* Overtime cost
* Statutory contributions
* Tax
* Bank advice
* Loan balances
* Full and final settlements

## Recruitment

* Open positions
* Hiring pipeline
* Time-to-fill
* Time-to-hire
* Source effectiveness
* Offer acceptance
* Recruiter performance
* Interview status
* Headcount against plan

## Performance

* Goal completion
* Rating distribution
* Review completion
* Calibration
* High performers
* Performance improvement plans
* Skills and succession

## Assets, Expenses, and Learning

* Asset allocation and availability
* Missing or damaged assets
* Warranty and maintenance
* Expense trends
* Policy violations
* Training completion
* Certification expiry
* Skill gaps

---

# 26. DATABASE AND API RULES

Use the existing database and ORM conventions.

* Use proper normalized domain models.
* Use UUIDs if that is the existing project standard.
* Add `tenant_id` to tenant-owned data.
* Add created, updated, deleted, and version metadata where appropriate.
* Use soft deletion according to existing project rules.
* Use effective-dated records for policies, reporting lines, salaries, shifts, and statutory rules.
* Use decimal types for money.
* Store timestamps consistently and render them using tenant/user timezone.
* Add proper indexes, foreign keys, constraints, and transactions.
* Never create one giant generic HR table.
* Use metadata only for genuinely dynamic fields.
* Use migrations; do not manually alter production schemas.
* Do not delete or recreate existing migrations.
* Do not reseed destructively.

Follow existing API conventions and versioning. Provide complete OpenAPI/Swagger documentation.

Critical APIs must include equivalent operations for:

```text
employees
employee-lifecycle
organization
positions
attendance
punches
shifts
rosters
time-entries
active-timer
timesheets
leave
holidays
payroll
payslips
tax
recruitment
jobs
candidates
interviews
offers
performance
goals
reviews
projects
tasks
assets
expenses
travel
learning
documents
hr-helpdesk
reports
```

Use request validation, permission checks, tenant isolation, transactions, audit records, idempotency, pagination, filtering, and consistent error responses.

---

# 27. SECURITY AND PRIVACY

Implement:

* Encryption for sensitive data
* Secure object-storage access
* Signed file URLs
* Field-level permissions
* Salary confidentiality
* Bank and tax confidentiality
* Medical-data restrictions
* Audit logs for sensitive views and exports
* Session and device management
* Rate limiting
* Secure refresh tokens
* Optional 2FA
* Data-retention policies
* Employee consent for GPS or biometric functionality
* Configurable privacy policies
* India DPDP-ready data architecture
* Data export and correction workflows
* Legal-hold-ready architecture
* No secrets in frontend or mobile code
* No sensitive values in logs or notifications

---

# 28. IMPLEMENTATION ORDER

Implement HRMS in complete vertical increments.

## HRMS Phase 0

* Repository audit
* Requirements matrix
* Architecture and database plan
* Reuse map
* Previous work marked paused

## HRMS Phase 1

* Organization structure
* Employee master
* Employee lifecycle
* HRMS permissions
* Employee and manager self-service foundations

## HRMS Phase 2 – Highest Functional Priority

* Attendance
* Shifts and rosters
* Mobile punch
* Work timer
* Breaks
* Projects and tasks
* Timesheets
* Daily, weekly, monthly, yearly, and custom reports
* Mobile offline synchronization

## HRMS Phase 3

* Leave
* Holidays
* Overtime
* Attendance closure
* Policy engine

## HRMS Phase 4

* Compensation
* Payroll
* Statutory configuration
* Payslips
* Loans
* Benefits
* Full and final settlement

## HRMS Phase 5

* Recruitment
* Job openings
* Careers portal
* Interviews
* Offers
* Preboarding and onboarding

## HRMS Phase 6

* Performance management
* Goals
* Reviews
* Feedback
* Calibration
* Succession and development

## HRMS Phase 7

* Assets
* Expenses
* Travel
* Learning
* Documents
* HR helpdesk
* Engagement
* Offboarding

## HRMS Phase 8

* Complete reports
* Integrations
* Security hardening
* Performance optimization
* Mobile completion
* End-to-end tests
* Documentation
* Production readiness

Each phase must include:

1. Database
2. Backend
3. Permissions
4. Workflows
5. Events
6. Notifications
7. Audit logs
8. Web UI
9. Mobile UI and API integration
10. Tests
11. Documentation
12. Verified builds

Do not create all web screens first and postpone the backend or mobile app.

---

# 29. CRITICAL ACCEPTANCE TESTS

The HRMS cannot be marked complete until these scenarios pass.

## Timer

1. Employee logs in on mobile and starts work.
2. The app is minimized or closed.
3. The backend continues to preserve the active session.
4. The employee reopens the app and sees the correct running time.
5. The employee pauses, resumes, takes a break, and stops.
6. Final duration is calculated from server timestamps.
7. The same entry appears on web and mobile.
8. The manager reviews it.
9. Daily, weekly, monthly, yearly, and custom reports show correct totals.
10. Offline actions sync once without duplicate time.

## Attendance

* Fixed, flexible, rotating, split, and overnight shifts calculate correctly.
* Late, early, half-day, overtime, holidays, leave, and weekly offs work correctly.
* Missed punches and corrections follow approval workflows.
* Locked attendance cannot be changed without authorization.

## Payroll

* Payroll uses approved attendance, leave, overtime, compensation, and adjustments.
* Joining, separation, arrears, loss of pay, loans, and full-and-final scenarios calculate correctly.
* Approval, locking, payslip generation, bank advice, and payroll reports work.
* Unauthorized employees cannot access another employee’s salary.

## Recruitment

* Requisition proceeds through approval, job opening, candidate application, interviews, offer, acceptance, and employee conversion.
* Candidate records are not duplicated during conversion.

## Performance

* Goals, self-review, manager review, calibration, final rating, acknowledgement, and history work end to end.

## Assets

* Asset is received, allocated, transferred, returned, repaired, audited, and cleared during offboarding.

## Multi-Tenancy and Permissions

* Tenant A can never access Tenant B’s HR data.
* Employees see only authorized records.
* Managers see only permitted reporting lines.
* Frontend restrictions and backend restrictions match.
* Field-level salary and personal-data permissions are enforced.

---

# 30. QUALITY RULES

* No static dashboard numbers.
* No fake APIs.
* No buttons without working actions.
* No hardcoded roles.
* No hardcoded tenant-specific policies.
* No client-only permission checks.
* No client-only timer calculation.
* No disconnected mobile screens.
* No duplicate HRMS implementations.
* No destructive database operations.
* No unfinished screens represented as complete.
* No TODO-only functionality for a required feature.
* No silent offline failures.

Every relevant screen must provide:

* Loading state
* Empty state
* Error state
* Permission-denied state
* Validation
* Search
* Filters
* Pagination
* Responsive layout
* Audit history
* Correct mobile representation

Run at every milestone:

* Lint
* Formatting checks
* Type checking
* Unit tests
* Integration tests
* API tests
* Permission tests
* Tenant-isolation tests
* Database migrations
* Web production build
* Mobile build checks
* End-to-end tests
* Responsive UI verification

---

# 31. AGENT WORKING METHOD

Work autonomously.

Do not repeatedly ask basic implementation questions.

When a detail is ambiguous:

1. Inspect the existing code and documentation.
2. Reuse the established project pattern.
3. Select a safe enterprise-grade default.
4. Document the assumption.
5. Continue implementation.

Ask only when a decision would fundamentally change the business model or requires credentials that are unavailable.

After each milestone, report:

```text
Completed
In Progress
Remaining
Problems Found
Existing Problems Fixed
Tests Run
Test Results
Documentation Updated
Next Implementation Step
```

Do not provide only plans, mockups, or status reports. Continue writing and testing the real implementation.

---

# 32. FINAL EXECUTION INSTRUCTION

Begin now.

First inspect the existing project and preserve all current work. Mark unfinished non-HRMS tasks as paused, create the HRMS requirements matrix and implementation plan, and then immediately implement the first complete HRMS vertical slice:

```text
Employee Login
→ Employee Profile
→ Shift Assignment
→ Mobile/Web Start Timer
→ Pause/Resume/Break
→ Stop Timer
→ Attendance Calculation
→ Timesheet
→ Manager Approval
→ Daily/Weekly/Monthly/Yearly/Custom Reports
→ Audit Log
→ Events
→ Notifications
```

After this vertical slice is fully working and tested, continue through every HRMS phase until the complete HRMS is production-ready on both web and mobile.

Do not resume the earlier non-HRMS roadmap before completing and verifying this HRMS priority.
