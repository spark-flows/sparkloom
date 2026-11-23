# MASTER AI AGENT PROMPT

## Build a Production-Ready, Multi-Tenant, Event-Driven Kidswear Manufacturing SaaS ERP

You are a **Principal Software Architect, SaaS Engineer, ERP Domain Expert, UI/UX Designer, Database Architect, DevOps Engineer, Mobile Engineer, Security Engineer, and AI Engineer**.

Your task is to design and build a complete, production-grade, interactive **Kidswear Garment Manufacturing ERP SaaS Platform**.

Use the attached document:

**Kidswear Manufacturing ERP + AI Blueprint**

as the primary business requirement and domain reference.

Do not create only a prototype, static dashboard, or mock screens.

I want a **real working ERP application** with:

* frontend
* backend
* database
* authentication
* authorization
* multi-tenancy
* event-driven architecture
* workflow engine
* notifications
* audit logs
* inventory
* manufacturing
* costing
* AI
* reporting
* responsive web application
* mobile application
* APIs
* background workers
* real-time updates
* SaaS administration
* subscription-ready architecture
* automated tests
* Docker-based local development
* production-ready project structure

---

# 1. PRODUCT

Build a SaaS ERP for companies manufacturing:

* Kids Shirts
* Kids T-Shirts
* Ages approximately 2 years to 17 years
* Custom garment products in the future

The platform must support the complete lifecycle:

Sample Development
→ Design
→ Sample BOM
→ Sample Costing
→ Sample Approval
→ Sales
→ Customer Order
→ PO
→ Merchandising
→ Material Planning
→ Store
→ Fabric
→ Accessories
→ Cutting
→ Checking
→ Numbering
→ Bundling
→ Embroidery / Printing
→ Stitching
→ Job Work
→ Wash
→ Dry
→ Press
→ Thread Cutting
→ Button / Buttonhole
→ Quality Checking
→ Finishing
→ Packing
→ Finished Goods Inventory
→ Dispatch
→ Delivery
→ Invoice
→ Accounting
→ Analytics

The system must be configurable so that new manufacturing steps can be added later without rewriting the application.

---

# 2. CORE ARCHITECTURAL REQUIREMENT

The ERP must be:

**Multi-Tenant + SaaS + Event-Driven + API-First + Mobile-Ready + AI-Enabled + Workflow-Driven**

Do not hardcode the business workflow.

Create a configurable **Workflow Engine**.

Each manufacturing stage must work like a state machine.

Example:

`PENDING → IN_PROGRESS → QC_PENDING → APPROVAL_PENDING → APPROVED → COMPLETED`

Possible additional states:

* REJECTED
* ON_HOLD
* REWORK
* CANCELLED
* BLOCKED

A stage cannot automatically move to the next stage unless its configured validations are satisfied.

---

# 3. RECOMMENDED TECHNOLOGY STACK

Use this stack unless there is a strong technical reason to replace something.

## Web Frontend

* Next.js
* React
* TypeScript
* Tailwind CSS
* shadcn/ui
* TanStack Query
* TanStack Table
* React Hook Form
* Zod
* Recharts
* Zustand where appropriate

## Mobile

Build a real mobile application using:

* React Native
* Expo
* TypeScript

Support:

* Android
* iOS
* Tablet layouts

Reuse API contracts, validation schemas, types, permissions, and business logic wherever possible.

## Backend

Use:

* NestJS
* TypeScript
* REST APIs
* WebSocket / Server Sent Events where appropriate
* OpenAPI / Swagger

## Database

Use:

* PostgreSQL

Use UUID primary keys.

Use migrations.

Use foreign keys, indexes, constraints and transactions properly.

## ORM

Use:

* Prisma

or another strongly typed PostgreSQL ORM if there is a strong reason.

## Cache

Use:

* Redis

## Event Bus

Use:

* NATS JetStream

Prefer NATS initially because it is simpler to operate for this SaaS while still supporting durable event-driven workflows.

The event bus abstraction should allow migration to Kafka later if necessary.

## Background Jobs

Use:

* BullMQ / Redis

or event-driven workers where appropriate.

## Storage

Use S3-compatible object storage.

Local development can use:

* MinIO

Production can support:

* AWS S3
* Cloudflare R2
* DigitalOcean Spaces
* other S3-compatible storage

---

# 4. PROJECT STRUCTURE

Use a professional monorepo.

Recommended:

```text
/apps
    /web
    /mobile
    /api
    /worker

/packages
    /ui
    /types
    /validation
    /database
    /auth
    /permissions
    /events
    /workflow
    /notifications
    /ai
    /config
    /utils
    /api-client

/infrastructure
    /docker
    /nginx
    /monitoring

/docs
```

Use Turborepo or equivalent monorepo tooling.

---

# 5. MULTI-TENANT SAAS ARCHITECTURE

The system must support many companies.

Hierarchy:

```text
Platform
   ↓
Tenant / Company
   ↓
Business Units
   ↓
Factories
   ↓
Warehouses / Stores
   ↓
Departments
   ↓
Users
```

Every tenant's data must be isolated.

Almost every tenant-owned table must contain:

```text
tenant_id
```

Implement tenant-aware repository/service layers.

Never trust tenant IDs supplied by the frontend.

Tenant identity must be derived from the authenticated user/session.

Prepare architecture for:

* Tenant plans
* Subscriptions
* Trial periods
* Feature limits
* User limits
* Storage limits
* API limits
* AI usage limits
* Module activation/deactivation
* Billing integration later

Create a SaaS Super Admin area.

---

# 6. SAAS SUPER ADMIN

Platform Super Admin must be able to:

* Create tenant
* Suspend tenant
* Activate tenant
* View tenants
* Manage plans
* Assign modules
* Define limits
* Check tenant usage
* Check AI usage
* Check storage usage
* Check active users
* View system health
* View failed jobs
* View failed events
* Retry events
* View tenant audit history

---

# 7. AUTHENTICATION

Implement secure authentication.

Support:

* email + password
* phone-ready architecture
* email verification
* forgot password
* reset password
* refresh tokens
* session management
* logout all devices
* optional two-factor authentication
* device/session history

Prepare architecture for future:

* Google login
* Microsoft login
* SSO

---

# 8. AUTHORIZATION

This is one of the most important parts of the ERP.

Build a powerful dynamic permission engine.

Support:

## Role-Based Access Control

Example roles:

* Tenant Owner
* Admin
* Merchandiser
* Junior Merchandiser
* Senior Merchandiser
* Designer
* Purchase Manager
* Store Manager
* Cutting Manager
* Stitching Manager
* QC Manager
* Washing Manager
* Production Manager
* Salesman
* Accountant
* Dispatcher
* Worker
* Viewer

Roles must NOT be hardcoded.

Tenant administrators can create unlimited custom roles.

---

# 9. MODULE-BASED PERMISSION

Permissions must support modules.

Example:

```text
samples
designs
bom
sales
customers
purchase
po
inventory
fabric
accessories
cutting
stitching
washing
quality
packing
dispatch
accounting
reports
ai
users
roles
settings
```

Each role/user can receive permissions per module.

---

# 10. ACTION-LEVEL PERMISSIONS

Support:

```text
view
create
edit
delete
approve
reject
cancel
export
import
print
assign
reassign
upload
download
dispatch
receive
issue
adjust
override
```

Example:

```text
inventory.fabric.view
inventory.fabric.create
inventory.fabric.edit
inventory.fabric.delete

production.cutting.view
production.cutting.create
production.cutting.edit
production.cutting.approve
```

---

# 11. USER-SPECIFIC PERMISSIONS

Permissions must work at:

1. Role level
2. User override level

User-specific permission may:

* grant additional permission
* deny inherited permission

Use explicit conflict rules.

Recommended:

```text
Explicit DENY
    >
User ALLOW
    >
Role ALLOW
    >
Default DENY
```

---

# 12. FIELD-LEVEL PERMISSIONS

Implement field-level security.

For example:

A salesman may view:

* Product
* Quantity
* Delivery date

but may not view:

* Manufacturing cost
* Profit
* Vendor purchase rates

A merchandiser may edit BOM but not final accounting values.

Admin must be able to configure:

```text
Field → View
Field → Edit
Field → Hidden
Field → Read Only
```

---

# 13. FORM-LEVEL PERMISSIONS

Forms must also be dynamic.

For every form support:

* Can open form
* Can create record
* Can edit record
* Can delete record
* Can view field
* Can edit field
* Required field by role
* Hidden field by role
* Read-only field by role

Permissions must be applied both:

* Frontend
* Backend

Never rely only on hiding UI buttons.

---

# 14. MOBILE PERMISSIONS

The same central permission engine must work for:

* Web
* Mobile
* API

Do not build separate mobile authorization logic.

One permission service must be the source of truth.

---

# 15. DYNAMIC MODULE SYSTEM

Modules must be configurable by tenant.

Example:

Tenant A may use:

* Sample
* Purchase
* Manufacturing
* Inventory

Tenant B may additionally use:

* Accounting
* CRM
* AI
* Job Work

Disabled modules must disappear from:

* Navigation
* Permissions
* APIs where appropriate
* Dashboards
* Mobile menu

---

# 16. DYNAMIC FORM BUILDER

Create architecture for dynamic custom fields.

Admin should eventually be able to add fields without coding.

Support custom fields:

* Text
* Number
* Decimal
* Currency
* Date
* DateTime
* Dropdown
* Multi-select
* Checkbox
* Radio
* File
* Image
* User
* Vendor
* Customer
* Product
* Boolean

Store field definitions separately from values.

Support validation.

---

# 17. WORKFLOW ENGINE

Create entities like:

```text
Workflow
WorkflowVersion
WorkflowStage
WorkflowTransition
WorkflowRule
WorkflowCondition
WorkflowChecklist
WorkflowApproval
WorkflowInstance
WorkflowStageInstance
WorkflowHistory
```

Each tenant should eventually be able to modify workflows.

Example transition:

```text
CUTTING
   ↓
CUTTING_QC
   ↓
NUMBERING
   ↓
STITCHING
```

Transition should be allowed only when configured conditions are true.

---

# 18. APPROVAL ENGINE

Create reusable approval system.

Examples:

* Sample approval
* Design approval
* BOM approval
* PO approval
* Material issue approval
* Cutting approval
* QC approval
* Dispatch approval
* Price override approval

Support:

* Single approver
* Multiple approvers
* Sequential approval
* Parallel approval
* Role-based approval
* Specific-user approval
* Amount-based approval
* Conditional approval

Example:

```text
Junior Merchandiser
       ↓
Senior Merchandiser
       ↓
Production Manager
```

---

# 19. GATE VALIDATION

Every major stage must have a configurable gate.

Example Cutting → Stitching gate:

Validate:

* Cutting quantity entered
* Cut QC completed
* Numbering completed
* Bundle created
* Required print/embroidery completed
* Required approvals completed
* Material consumption posted

Then allow next stage.

Otherwise show:

```text
Cannot move to Stitching.

Missing requirements:
- Cutting QC pending
- Bundle numbering incomplete
```

Never silently fail.

---

# 20. AUDIT LOG

Every important action must generate an immutable audit log.

Capture:

* tenant
* user
* action
* module
* resource
* resource ID
* previous value
* new value
* timestamp
* IP
* device
* session
* reason if required

Examples:

```text
PO APPROVED
BOM EDITED
PRICE CHANGED
STOCK ADJUSTED
QC FAILED
PERMISSION UPDATED
ORDER CANCELLED
```

---

# 21. SAMPLE DEVELOPMENT

Implement complete Sample Development.

Sample flow:

```text
Sample Request
→ Sample Fabric Purchase
→ Accessories
→ Designer
→ Design
→ Sample BOM
→ Cutting
→ Print / Embroidery
→ Stitching
→ Wash
→ Finishing
→ Sample QC
→ Costing
→ Approval
→ Sales Sample
```

---

# 22. STYLE MANAGEMENT

Create Style Master.

A style may contain:

* Style number
* Product type
* Shirt/T-Shirt
* Gender/category if required
* Age group
* Season
* Collection
* Designer
* Images
* Fabric
* Color
* Print
* Embroidery
* Collar
* Cuff
* Sleeve
* Buttons
* Thread
* Labels
* Packaging
* BOM
* Measurement chart
* Production instructions

Support versioning.

Example:

```text
STYLE-001
Version 1
Version 2
Version 3
```

Once used by production PO, relevant versions should be locked.

---

# 23. AI DESIGN COPILOT

Add AI inside Designer module.

Designer should be able to enter:

```text
Create a premium kids shirt for age 8-10.
Use blue check fabric.
Mandarin collar.
Wooden-style buttons.
Small embroidery on chest.
```

AI should suggest:

* Design ideas
* Collar
* Sleeve
* Cuff
* Button type
* Thread color
* Trim
* Print ideas
* Embroidery placement
* Fabric combinations
* Size suitability
* Collection names
* Product descriptions

If image-generation providers are configured, architecture should allow generated design concepts.

AI output must never automatically approve production design.

Human approval remains required.

---

# 24. BOM

Create Bill of Materials.

Example BOM items:

```text
Fabric
Button
Thread
Label
Collar material
Cuff
Interlining
Embroidery
Printing
Packing bag
Hang tag
Carton
```

Store:

* required quantity
* unit
* wastage
* price
* vendor
* consumption
* estimated cost
* actual cost

Version the BOM.

---

# 25. AI BOM ASSISTANT

Based on previous products, style details and design, AI may recommend:

* likely materials
* quantity
* accessories
* wastage percentage
* missing BOM items

Always clearly mark AI suggestions.

User must approve them.

---

# 26. COSTING ENGINE

Calculate:

```text
Fabric Cost
+
Accessories Cost
+
Cutting Cost
+
Print Cost
+
Embroidery Cost
+
Stitching Cost
+
Wash Cost
+
Finishing Cost
+
Packing Cost
+
Job Work Cost
+
Overhead
+
Transport
+
Tax if configured
+
Profit Margin
=
Selling Price
```

Support:

* estimated cost
* actual cost
* variance
* selling price
* margin
* markup

---

# 27. AI COST ANALYSIS

AI should detect:

* unusual material cost
* abnormal wastage
* unusually low margin
* cost increase
* vendor cost anomalies
* product profitability problems

Example:

```text
Warning:
Fabric cost for this style is approximately 14% higher than similar styles.
```

---

# 28. SALES

Create CRM-lite Sales module.

Support:

* Salesman
* Customers
* Shops
* Leads
* Sample presentations
* Customer feedback
* Quotations
* Orders
* Follow-ups

Salesman mobile app must allow:

* viewing samples
* showing product catalog
* creating order
* adding customer
* recording feedback
* adding notes
* uploading customer/shop photo if permitted

---

# 29. CUSTOMER ORDER

Support orders by:

* Style
* Color
* Size
* Quantity

Example:

```text
Style A

Red:
2Y: 100
4Y: 150
6Y: 200

Blue:
2Y: 80
4Y: 120
6Y: 180
```

Generate a size-color matrix.

---

# 30. PURCHASE ORDER / PRODUCTION ORDER

When order is confirmed generate appropriate production/PO records.

Junior Merchandiser:

* calculates fabric
* calculates accessories
* calculates order requirements
* checks size ratios
* creates material requirement

Senior Merchandiser:

* reviews
* edits if allowed
* approves
* verifies stock
* verifies shrinkage
* verifies fabric width
* verifies testing information
* confirms production feasibility

---

# 31. MATERIAL REQUIREMENT PLANNING

MRP must calculate:

```text
Required Quantity
-
Available Stock
-
Reserved Stock
+
Safety Stock
=
Purchase Requirement
```

Support:

* Fabric requirement
* Accessories
* Labels
* Packaging

---

# 32. INVENTORY

Create strong inventory architecture.

Do not maintain stock only as an editable quantity.

Use an immutable stock ledger.

Every movement should create a transaction.

Examples:

```text
PURCHASE_RECEIPT
MATERIAL_ISSUE
MATERIAL_RETURN
JOBWORK_ISSUE
JOBWORK_RECEIPT
PRODUCTION_RECEIPT
TRANSFER
ADJUSTMENT
REJECTION
SCRAP
DISPATCH
CUSTOMER_RETURN
```

Maintain:

* On hand
* Reserved
* Available
* In transit
* WIP
* Rejected
* Scrap

---

# 33. FABRIC INVENTORY

Fabric tracking must support:

* Fabric code
* Fabric name
* Supplier
* Roll number
* Lot
* Shade
* Width
* GSM
* Meter
* Weight
* Purchase rate
* Shrinkage
* Lab report
* Received quantity
* Used quantity
* Remaining quantity

Support roll-level tracking.

---

# 34. ACCESSORIES INVENTORY

Track:

* Button
* Thread
* Label
* Zipper if needed later
* Packing bag
* Tag
* Carton
* Interlining
* Other trims

---

# 35. CUTTING

Cutting module must support:

* Production order
* Style
* Color
* Size
* Fabric lot
* Fabric roll
* Marker
* Layers
* Planned quantity
* Actual quantity
* Waste
* Reject
* Operator
* Date/time

---

# 36. NUMBERING AND BUNDLING

After cutting:

Generate piece/bundle numbers.

Example:

```text
PO-1001
STYLE-20
COLOR-BLUE
SIZE-8
BUNDLE-001
PIECES 1-20
```

Support QR/Barcode labels.

Components like:

* front
* back
* sleeve
* collar
* cuff

must remain traceable.

---

# 37. QR / BARCODE TRACKING

Implement architecture for QR or barcode scanning.

Each production bundle should be scannable.

Scanning can update:

```text
Received at Cutting
Cutting Completed
QC Completed
Issued to Stitching
Stitching Started
Stitching Completed
Wash Started
Wash Completed
Packing Completed
```

The mobile app must support scanning.

---

# 38. STITCHING

Support:

* In-house stitching
* External stitching

Track:

* bundles
* workers
* lines
* operations
* quantities
* defects
* rework
* start time
* completion time

---

# 39. STITCHING QC

Support at least three quality stages:

### QC 1

Verify numbering and correct joining of components.

### QC 2

Half-garment QC.

### QC 3

Final stitched garment QC.

Support:

* Pass
* Fail
* Rework
* Reject

---

# 40. JOB WORK

Support external outsourcing models.

## Only Stitch

Company sends cut components.

Vendor performs stitching.

## Stitch to Pack

Vendor performs:

* stitching
* washing
* drying
* pressing
* finishing
* packing

## Cut to Pack

Vendor may receive:

* design
* BOM
* material
* measurement
* instructions

and returns final packed product.

Allow custom job-work templates.

---

# 41. JOB WORK VENDOR PORTAL

Create architecture for vendor portal.

Vendor can see only assigned work.

Vendor may:

* accept job
* update progress
* enter production quantity
* report rejection
* upload documents
* upload invoice
* mark dispatch
* confirm completion

---

# 42. WASH / FINISHING

Support:

* Wash
* Dry
* Press
* Thread Cutting
* Buttonhole
* Button
* Finishing
* Packing

Each should be configurable as workflow stages.

Track per-piece or batch rate.

---

# 43. QUALITY MANAGEMENT

Create generic reusable Quality module.

QC record must support:

* Item
* Stage
* Inspector
* Quantity inspected
* Passed
* Failed
* Rework
* Defect category
* Defect reason
* Images
* Notes
* Date/time

---

# 44. QC CHECKLISTS

Checklists must be configurable.

Example:

```text
Measurement correct
Color correct
Stitch correct
Buttons correct
Collar aligned
Print correct
Embroidery correct
No stains
No damage
Packing correct
```

Different product/style/stage can use different checklist.

---

# 45. AI QC ASSISTANT

Design architecture for future computer vision.

Allow image upload.

AI may detect/suggest:

* stain
* misalignment
* print problems
* visible stitching defects
* missing button
* color inconsistency

AI result is advisory.

Human QC makes final decision.

---

# 46. FINISHED GOODS

Once production passes final QC and packing:

Create Finished Goods inventory.

Track SKU by:

```text
Style
Color
Size
```

Example SKU:

```text
STYLE100-BLUE-08Y
```

---

# 47. DISPATCH

Dispatch must validate:

* PO completed
* QC passed
* packed quantity
* inventory available
* customer details
* invoice requirements
* transport details

Create:

* Dispatch Note
* Packing List
* Shipment record
* Invoice connection
* Transport information

---

# 48. ORDER TRACKING

Build an interactive real-time order tracker.

For each order show:

```text
Order Received
↓
Merchandising
↓
Material Planning
↓
Material Ready
↓
Cutting
↓
Numbering
↓
Stitching
↓
Wash
↓
Finishing
↓
Final QC
↓
Packing
↓
Ready to Dispatch
↓
Dispatched
↓
Delivered
```

Show:

* planned date
* actual date
* delay
* responsible department
* responsible user
* completed quantity
* pending quantity
* rejected quantity
* rework quantity
* blockers
* approval status

Use timeline, progress bar and visual workflow.

---

# 49. REAL-TIME UI

Use WebSockets/SSE where beneficial.

Examples:

When manager approves PO:

Merchandiser screen should update immediately.

When bundle scan is completed:

Production dashboard should update immediately.

When material shortage occurs:

Relevant users should receive notification immediately.

---

# 50. NOTIFICATION ENGINE

Create centralized notification service.

Channels:

* In-app
* Push
* Email
* SMS-ready
* WhatsApp-ready

Events:

```text
ORDER_CREATED
PO_PENDING_APPROVAL
PO_APPROVED
PO_REJECTED
MATERIAL_SHORTAGE
CUTTING_COMPLETED
QC_FAILED
REWORK_CREATED
JOBWORK_OVERDUE
PRODUCTION_DELAYED
PACKING_COMPLETED
DISPATCH_DUE
ORDER_DISPATCHED
PAYMENT_DUE
```

---

# 51. USER NOTIFICATION SETTINGS

Users should configure:

* Which notifications they receive
* Push
* Email
* In-app
* Priority
* Quiet hours where appropriate

Critical operational alerts may be tenant-controlled.

---

# 52. EVENT-DRIVEN ARCHITECTURE

Business modules should communicate using domain events where appropriate.

Example:

```text
OrderConfirmed
      ↓
MaterialRequirementCalculated
      ↓
InventoryReservationRequested
      ↓
ProductionOrderCreated
      ↓
NotificationCreated
```

Another:

```text
CuttingCompleted
      ↓
CuttingQCRequested
```

Another:

```text
QCApproved
      ↓
WorkflowStageCompleted
      ↓
NextStageUnlocked
```

---

# 53. EVENT DESIGN

Every event should include:

```json
{
  "eventId": "",
  "eventType": "",
  "eventVersion": 1,
  "tenantId": "",
  "aggregateType": "",
  "aggregateId": "",
  "userId": "",
  "correlationId": "",
  "causationId": "",
  "timestamp": "",
  "payload": {}
}
```

---

# 54. EVENT RELIABILITY

Implement:

* Transactional Outbox Pattern
* Idempotent consumers
* Retry
* Exponential backoff
* Dead Letter handling
* Event versioning
* Correlation IDs
* Event logs
* Replay-safe consumers

Avoid dual-write problems.

---

# 55. DO NOT OVER-MICROSERVICE

The application must be event-driven, but do not create dozens of tiny microservices unnecessarily.

Start using a **well-designed modular architecture** with clearly separated bounded contexts.

Potential modules:

```text
Identity
Tenant
Permissions
Samples
Design
Sales
Customers
Orders
Merchandising
BOM
Purchasing
Inventory
Production
Cutting
Stitching
JobWork
Quality
Finishing
Packing
Dispatch
Accounting
Notifications
Workflow
AI
Reporting
Audit
```

Each module should own its business logic.

The architecture must allow modules to become separate services later.

---

# 56. DATABASE DESIGN

Create a detailed relational schema.

Important entities should include but are not limited to:

```text
tenants
tenant_settings
subscription_plans
tenant_subscriptions

users
roles
permissions
role_permissions
user_permissions
user_roles

departments
factories
warehouses

customers
vendors

styles
style_versions
style_images
style_measurements

samples
sample_status_history

bom
bom_versions
bom_items

materials
fabrics
fabric_rolls
accessories

inventory_locations
inventory_transactions
inventory_balances
inventory_reservations

sales_orders
sales_order_items
sales_order_size_breakdowns

production_orders
production_order_items

cutting_orders
cutting_batches

bundles
bundle_items
bundle_scans

job_work_orders
job_work_items

stitching_batches

qc_inspections
qc_checklists
qc_checklist_items
qc_defects

workflow_definitions
workflow_versions
workflow_stages
workflow_transitions
workflow_instances
workflow_stage_instances
workflow_history

approvals
approval_steps
approval_actions

packing_records
dispatches
dispatch_items

notifications
notification_preferences

audit_logs

documents
attachments

ai_requests
ai_usage
ai_suggestions

outbox_events
processed_events
```

Add appropriate indexes and constraints.

---

# 57. SOFT DELETE

For master/configuration entities where appropriate, use:

```text
deleted_at
deleted_by
```

Do not soft-delete financial or inventory ledger history in a way that destroys traceability.

---

# 58. ACCOUNTING

Prepare basic accounting architecture.

Modules:

* Customers
* Vendors
* Sales invoices
* Purchase bills
* Receipts
* Payments
* Expenses
* Job Work Payments
* Ledgers
* Taxes
* Credit notes
* Debit notes

Keep financial transaction history auditable.

---

# 59. AI ARCHITECTURE

AI is a core feature.

Create an internal:

**AI Gateway**

Application modules must never directly call a specific AI vendor.

Use an interface such as:

```typescript
interface AIProvider {
  chat(input): Promise<AIResponse>;
  vision?(input): Promise<AIResponse>;
  embeddings?(input): Promise<AIResponse>;
}
```

Implement adapters.

Possible providers:

* Google Gemini
* Groq
* OpenRouter-compatible providers
* Ollama
* Local models
* other providers later

I will supply API keys.

---

# 60. FREE / LOW-COST AI

During initial development prioritize providers that provide free or low-cost development options when available.

The provider must remain configurable.

Example environment variables:

```text
AI_PROVIDER=
GEMINI_API_KEY=
GROQ_API_KEY=
OPENROUTER_API_KEY=
OLLAMA_BASE_URL=
```

Never expose secret keys to frontend or mobile app.

All AI calls must pass through backend.

---

# 61. AI USAGE TRACKING

Track:

* tenant
* user
* module
* provider
* model
* request count
* token usage if available
* estimated cost
* latency
* success/failure

Tenant admin should see AI consumption.

---

# 62. AI ERP ASSISTANT

Build an AI assistant inside ERP.

Users can ask:

```text
Which orders are delayed?

Which styles have highest margin?

Which vendor has highest rejection?

How much blue fabric is available?

Show material shortage for PO-1005.

Why is Order 5008 blocked?

Which orders are due this week?
```

The AI must respect tenant and user permissions.

AI must never expose information the logged-in user does not have permission to view.

---

# 63. AI ANALYTICS

AI should generate insights such as:

* Delay risk
* Bottlenecks
* High rejection
* High wastage
* Low margin
* Slow vendors
* Abnormal consumption
* Inventory shortage
* Overstock
* Production efficiency
* Sales trends

---

# 64. AI DELIVERY RISK

Create an AI-ready feature that can calculate delivery risk.

Inputs may include:

* current production stage
* remaining quantity
* factory capacity
* historical stage duration
* vendor performance
* material availability
* QC failure
* rework rate
* promised delivery date

Output:

```text
LOW
MEDIUM
HIGH
CRITICAL
```

with explanation.

---

# 65. DASHBOARD

Create a beautiful executive dashboard.

Show:

* Today's Orders
* Active POs
* Pending Approvals
* Material Shortages
* Cutting Pending
* Stitching WIP
* QC Pending
* Rework
* Finished Goods
* Dispatch Due
* Revenue
* Margin
* Vendor Performance
* Production Efficiency
* Delivery Risk

---

# 66. ROLE-BASED DASHBOARDS

Dashboard must adapt by role.

Examples:

Merchandiser sees:

* New orders
* BOM
* material requirement
* PO approvals

Cutting Manager sees:

* Cutting queue
* fabric availability
* cutting QC

QC sees:

* pending inspections
* failed QC
* rework

Salesman sees:

* customers
* samples
* orders
* follow-ups

Owner sees company-wide KPIs.

---

# 67. UI / UX

This is extremely important.

I want a:

**Beautiful, Premium, Professional, Modern Enterprise ERP UI**

Avoid:

* outdated ERP design
* cluttered UI
* excessive gradients
* random bright colors
* giant cards everywhere
* poor spacing
* inconsistent icons

Use:

* clean typography
* clear hierarchy
* professional tables
* sticky headers
* filters
* saved views
* smart search
* breadcrumbs
* drawers
* modals where appropriate
* tabs
* command palette
* keyboard shortcuts
* loading skeletons
* empty states
* contextual actions
* responsive data views
* status badges
* timelines
* Kanban where useful

Use a consistent design system.

---

# 68. RESPONSIVE DESIGN

Every screen must work properly on:

* Mobile
* Small phone
* Large phone
* Tablet
* iPad
* Laptop
* Desktop
* Large desktop
* PC

Do not simply shrink desktop tables on mobile.

For mobile:

Convert tables into:

* cards
* accordions
* swipe actions
* responsive lists
* compact filters

---

# 69. MOBILE APP

Build a dedicated mobile app.

Priority mobile workflows:

* Login
* Dashboard
* Notifications
* Approvals
* Sales
* Customer orders
* Production status
* QR/barcode scanning
* Bundle tracking
* QC
* Photo upload
* Job work status
* Inventory lookup
* Dispatch confirmation

---

# 70. MOBILE OFFLINE MODE

For factory workflows, prepare offline-first support.

Allow temporary offline:

* QR scans
* QC
* production entry

Queue local actions.

Sync when network returns.

Handle duplicate events safely.

---

# 71. GLOBAL SEARCH

Create universal search.

Search:

* Order
* PO
* Style
* Sample
* Customer
* Vendor
* Fabric
* SKU
* Bundle
* Invoice

Provide command-palette style search.

---

# 72. FILTERING

Every important table should support:

* search
* sorting
* filtering
* pagination
* column visibility
* saved filters
* export

---

# 73. DOCUMENT MANAGEMENT

Allow attachments for:

* PO
* Style
* Sample
* Fabric
* QC
* Vendor
* Dispatch

Examples:

* images
* PDFs
* lab reports
* invoices
* measurement sheets

Store metadata in database and files in S3-compatible storage.

---

# 74. LAB TEST / FABRIC QC

Support:

* Shrinkage
* Color fastness
* GSM
* Width
* Shade
* Fabric test report
* Image/document attachment

Associate test reports with fabric lot/roll.

---

# 75. REPORTING

Build reporting architecture.

Reports:

* Order status
* Production status
* Material consumption
* Fabric balance
* Cutting wastage
* Stitching efficiency
* QC rejection
* Rework
* Job work
* Vendor performance
* Product costing
* Margin
* Inventory ageing
* Finished goods
* Dispatch
* Sales
* Profitability

---

# 76. EXPORT

Allow export where user has permission:

* Excel
* CSV
* PDF where appropriate

Exports must respect permissions.

---

# 77. SECURITY

Implement:

* Secure password hashing
* JWT/session security
* Refresh token rotation
* Rate limiting
* Input validation
* Zod validation
* Helmet/security headers
* CORS configuration
* SQL injection prevention
* XSS prevention
* CSRF protection where relevant
* Secure cookies
* encrypted sensitive secrets
* tenant isolation
* audit logs
* upload validation
* malware-scan-ready file pipeline

Never trust client input.

---

# 78. API SECURITY

Every API endpoint must check:

1. Authentication
2. Tenant
3. Module entitlement
4. Permission
5. Resource access
6. Field-level rules where necessary

---

# 79. OBSERVABILITY

Add:

* Structured logging
* Correlation IDs
* Error tracking
* API metrics
* Event metrics
* Worker metrics
* Queue metrics

Prepare integration with:

* OpenTelemetry
* Grafana
* Prometheus
* Sentry

---

# 80. ERROR HANDLING

Use standardized errors.

Example:

```json
{
  "code": "WORKFLOW_GATE_FAILED",
  "message": "Cutting cannot move to stitching.",
  "details": [
    "Cutting QC is incomplete",
    "Numbering is pending"
  ],
  "correlationId": "..."
}
```

---

# 81. TESTING

Create:

* Unit tests
* Integration tests
* API tests
* Permission tests
* Tenant isolation tests
* Workflow tests
* Inventory tests
* Event idempotency tests
* End-to-end tests

Use Playwright for important web workflows.

---

# 82. CRITICAL TEST

Create tests proving:

**Tenant A can never access Tenant B data.**

Test this at:

* API
* database service
* exports
* file access
* AI assistant
* reports

---

# 83. DEVOPS

Create Docker-based local environment.

Provide:

```text
PostgreSQL
Redis
NATS
MinIO
API
Web
Worker
```

with Docker Compose.

---

# 84. ENVIRONMENT MANAGEMENT

Create:

```text
.env.example
```

Never commit secrets.

Support:

* local
* development
* staging
* production

---

# 85. CI/CD

Prepare GitHub Actions or equivalent.

Run:

* lint
* typecheck
* tests
* build
* migration validation

---

# 86. SEED DATA

Create realistic seed data.

Example tenant:

**Demo Kidswear Pvt Ltd**

Users:

* Owner
* Admin
* Merchandiser
* Designer
* Cutting Manager
* Stitching Manager
* QC Manager
* Salesman

Create sample:

* vendors
* customers
* fabrics
* accessories
* styles
* BOM
* sample
* order
* PO
* inventory
* production stages

This must allow me to open the ERP and test the complete flow immediately.

---

# 87. DEMO CREDENTIALS

For local development only, document demo logins.

Never use insecure credentials in production.

---

# 88. DATA MODELING RULE

Do not create one giant generic table for everything.

Use proper domain modeling.

But use configurable metadata only where genuine dynamic behavior is needed.

---

# 89. NO FAKE FUNCTIONALITY

Do not create UI buttons that do nothing.

Do not show static dashboard metrics pretending to be real.

Every important UI function should connect to a real API and database.

---

# 90. DEVELOPMENT APPROACH

Do not attempt to generate the entire ERP as disconnected files in one step.

Build it systematically.

Start with foundations.

Recommended sequence:

## Phase 1

* Monorepo
* Docker
* Database
* Authentication
* Tenant system
* User management
* Role/permission engine
* SaaS Super Admin
* UI design system

## Phase 2

* Master data
* Customer
* Vendor
* Material
* Fabric
* Accessories
* Style

## Phase 3

* Sample
* Design
* BOM
* Costing
* AI design assistant

## Phase 4

* Sales
* Customer Orders
* PO
* Merchandising
* Material planning

## Phase 5

* Inventory
* Stock ledger
* Reservation
* Store

## Phase 6

* Workflow engine
* Approvals
* Notifications
* Event architecture

## Phase 7

* Cutting
* Numbering
* Bundling
* Stitching
* Job Work
* Wash
* Finishing
* QC

## Phase 8

* Finished Goods
* Packing
* Dispatch
* Delivery

## Phase 9

* Accounting
* Reports
* Dashboards
* AI analytics

## Phase 10

* Mobile app
* QR scanning
* Offline sync
* Push notifications

---

# 91. FIRST VERTICAL SLICE

Before expanding everywhere, create one fully working vertical workflow:

```text
Login
→ Tenant
→ Customer
→ Style
→ BOM
→ Sales Order
→ Production Order
→ Material Reservation
→ Cutting
→ Cutting QC
→ Stitching
→ Final QC
→ Packing
→ Finished Goods
→ Dispatch
```

All of this must use the real:

* database
* permissions
* events
* workflow
* audit
* notifications

---

# 92. USER EXPERIENCE FOR APPROVAL

When an item is waiting for approval show:

```text
Pending Approval

Requested By:
Requested At:
Current Stage:
Required Approver:
Checklist:
Comments:
Attachments:
```

Buttons:

```text
Approve
Reject
Send Back
Request Changes
```

Require reason when appropriate.

---

# 93. ACTIVITY TIMELINE

Every order should show activity history.

Example:

```text
10:15 — Order created by Salesman
10:17 — PO generated
10:35 — Material requirement calculated
11:05 — Junior Merchandiser submitted
11:15 — Senior Merchandiser approved
12:00 — Fabric reserved
14:20 — Cutting started
```

---

# 94. PRODUCTION BOARD

Create visual production monitoring.

Show stages horizontally or vertically.

Example:

```text
Material
   100%

Cutting
   100%

Stitching
   72%

Wash
   35%

QC
   15%

Packing
   0%
```

---

# 95. DELAY ALERTING

If actual progress is behind planned progress:

Generate event:

```text
ProductionDelayDetected
```

Notify relevant users.

Show reason if known.

---

# 96. CAPACITY PLANNING

Prepare feature for:

* workers
* sewing lines
* machines
* daily capacity
* vendor capacity

Calculate whether order can meet promised delivery.

---

# 97. VENDOR PERFORMANCE

Calculate:

* On-time %
* Rejection %
* Rework %
* Average completion time
* Price
* Quality score

---

# 98. CHANGE MANAGEMENT

After BOM/Design/PO approval:

Changes must not silently overwrite history.

Use:

* Versioning
* Change request
* Reapproval
* Audit log

Example:

```text
BOM Change Request #003
Reason:
Button supplier unavailable.

Old:
BUTTON-A

New:
BUTTON-B
```

---

# 99. CANCELLATION

Cancellation must be controlled.

When order is cancelled:

Check:

* reserved material
* WIP
* job work
* finished goods
* purchased material
* accounting impact

Do not simply set `status = cancelled`.

Generate compensating workflows where required.

---

# 100. DATA CONSISTENCY

Use database transactions for critical operations.

Especially:

* inventory
* approval
* order confirmation
* reservation
* dispatch
* accounting

---

# 101. IDEMPOTENCY

APIs such as:

* Create Order
* Approve PO
* Scan Bundle
* Receive Material
* Dispatch Order

must support idempotency where duplicate requests are dangerous.

---

# 102. DESIGN SYSTEM

Build reusable components:

```text
AppShell
Sidebar
Topbar
MobileNavigation
PageHeader
StatCard
DataTable
FilterBar
StatusBadge
ApprovalBadge
WorkflowTimeline
ActivityTimeline
FormSection
ConfirmDialog
PermissionGuard
ModuleGuard
EmptyState
Skeleton
Upload
ImageViewer
NotificationDrawer
AIChatPanel
```

---

# 103. THEMING

Support:

* Light Mode
* Dark Mode
* System Mode

Tenant branding should eventually support:

* logo
* company name
* accent color

Do not make tenant theming destroy accessibility.

---

# 104. ACCESSIBILITY

Use proper:

* contrast
* labels
* keyboard navigation
* semantic HTML
* focus states
* screen-reader-friendly controls

---

# 105. PERFORMANCE

Use:

* Server-side pagination
* Proper indexes
* Caching
* Lazy loading
* Code splitting
* Optimized images
* Background processing
* Debounced search

Do not load thousands of production rows into browser at once.

---

# 106. MOBILE PERFORMANCE

Optimize APIs for mobile.

Support paginated and compact responses.

Do not send unnecessary large nested objects.

---

# 107. API VERSIONING

Use API versioning.

Example:

```text
/api/v1/...
```

---

# 108. API DOCUMENTATION

Generate Swagger/OpenAPI.

Document:

* requests
* responses
* permission requirements
* errors
* pagination

---

# 109. BUSINESS DATE/TIME

Store timestamps in UTC.

Display according to tenant/user timezone.

---

# 110. MONEY

Never use floating point for money.

Use decimal/numeric.

Support configurable currency.

---

# 111. QUANTITIES

Garment manufacturing uses different units:

* meter
* kilogram
* piece
* cone
* roll
* box
* dozen
* carton

Create Unit of Measure master.

Support conversions where configured.

---

# 112. SIZE MASTER

Create configurable kids size master.

Example:

```text
2Y
3Y
4Y
5Y
6Y
7Y
8Y
9Y
10Y
11Y
12Y
13Y
14Y
15Y
16Y
17Y
```

Do not hardcode it permanently.

Tenant can add/customize sizes.

---

# 113. MEASUREMENT CHART

Support measurement specifications:

* Chest
* Length
* Shoulder
* Sleeve
* Collar
* Waist
* other measurements

Support tolerance:

```text
+0.5 cm
-0.5 cm
```

---

# 114. PRODUCTION TRACEABILITY

From a finished piece/bundle, user should eventually be able to trace:

```text
Customer Order
→ PO
→ Style
→ Fabric Lot
→ Fabric Roll
→ Cutting Batch
→ Bundle
→ Stitching
→ Job Worker
→ QC
→ Packing
→ Dispatch
```

---

# 115. DASHBOARD DESIGN DIRECTION

Use premium SaaS inspiration from modern enterprise products.

Design characteristics:

* spacious
* calm
* information dense but uncluttered
* minimal
* premium typography
* strong grid
* subtle borders
* clear hierarchy
* intelligent use of badges
* excellent tables

Do not copy any product exactly.

---

# 116. NAVIGATION

Desktop:

```text
Sidebar
+
Top Navigation
```

Mobile:

```text
Bottom Navigation
+
Drawer / More menu
```

Navigation must be generated dynamically based on:

* tenant modules
* user permissions

---

# 117. AI USER EXPERIENCE

AI must not be a separate gimmick page only.

Integrate it contextually.

Examples:

### Style Page

`Ask AI for design variations`

### BOM Page

`AI: Check missing materials`

### Order Page

`AI: Analyze delivery risk`

### Inventory

`AI: Predict shortages`

### Dashboard

`Ask your ERP`

### QC

`AI: Analyze defect photo`

---

# 118. AI APPROVAL RULE

AI may:

* suggest
* predict
* summarize
* classify
* analyze

AI may NOT silently:

* approve PO
* dispatch goods
* modify financial ledger
* alter stock
* cancel order
* delete records

Human approval is required for high-impact actions.

---

# 119. AI SAFETY

Before AI receives ERP data:

* enforce tenant isolation
* enforce permission
* minimize data
* redact secrets
* log AI access

---

# 120. ADMIN SETTINGS

Tenant Admin settings should include:

* Company
* Factories
* Warehouses
* Departments
* Users
* Roles
* Permissions
* Modules
* Workflow
* Approval Rules
* Notifications
* Units
* Sizes
* Tax
* Currency
* Number Series
* AI Provider
* Branding

---

# 121. NUMBER SERIES

Create configurable numbering:

```text
SO-2026-000001
PO-2026-000001
STYLE-0001
SAMPLE-0001
CUT-0001
BUNDLE-000001
QC-000001
DSP-000001
INV-000001
```

Tenant can configure prefixes.

---

# 122. FEATURE FLAGS

Implement feature flags.

Useful for:

* beta modules
* tenant rollout
* AI features
* experimental features

---

# 123. DATABASE BACKUPS

Prepare production architecture for:

* automated backups
* point-in-time recovery
* restore process

Document it.

---

# 124. DOCUMENTATION

Maintain:

```text
README.md
ARCHITECTURE.md
DATABASE.md
EVENTS.md
PERMISSIONS.md
WORKFLOWS.md
AI.md
DEPLOYMENT.md
MOBILE.md
API.md
```

Update documentation while implementing.

---

# 125. ADR

For important architectural decisions create Architecture Decision Records.

Example:

```text
ADR-001: NATS JetStream
ADR-002: PostgreSQL Multi-Tenancy
ADR-003: Transactional Outbox
ADR-004: Permission Model
ADR-005: Modular Architecture
```

---

# 126. CODE QUALITY

Use:

* TypeScript strict mode
* ESLint
* Prettier
* clear naming
* small modules
* dependency inversion where useful
* DTO validation
* reusable domain services

Avoid excessive abstraction.

---

# 127. IMPORTANT ENGINEERING RULES

Do not:

* put all business logic in controllers
* put all logic in frontend
* use one giant service
* hardcode tenant-specific rules
* hardcode roles
* hardcode workflow
* hardcode statuses unnecessarily
* bypass permission checks
* edit inventory balances manually
* expose AI keys
* trust frontend permission checks
* skip audit history
* use fake dashboard data after real backend exists

---

# 128. AGENT WORKING METHOD

Work autonomously.

Do not repeatedly ask me basic engineering questions.

When a requirement is ambiguous:

1. choose a sensible enterprise-grade default
2. implement it cleanly
3. document your assumption

Only ask me when a decision could fundamentally change the business model.

---

# 129. BEFORE WRITING MAJOR CODE

First inspect:

* attached ERP blueprint
* existing repository
* package configuration
* database
* current architecture

Then create/update:

```text
docs/IMPLEMENTATION_PLAN.md
```

Maintain a checklist.

---

# 130. BUILD IN SMALL WORKING INCREMENTS

For every increment:

1. Design
2. Database migration
3. Backend
4. Permissions
5. Events
6. Audit
7. UI
8. Mobile impact
9. Tests
10. Documentation

Do not leave half-integrated modules.

---

# 131. EACH SCREEN MUST HAVE

Where applicable:

* Loading
* Empty state
* Error state
* Permission denied state
* Create
* View
* Edit
* Delete
* Validation
* Search
* Filters
* Pagination
* Responsive layout

---

# 132. FIRST DELIVERY

Your first implementation delivery should include:

### Platform

* Monorepo
* Docker Compose
* PostgreSQL
* Redis
* NATS
* MinIO

### Core SaaS

* Tenant
* Auth
* Users
* Roles
* Permissions
* Modules
* SaaS Super Admin

### UI

* Premium responsive shell
* Login
* Dashboard
* User management
* Roles
* Permission matrix
* Module management

### Backend

* APIs
* Swagger
* Tenant middleware
* Permission guards
* Audit system
* Event publishing
* Outbox

### Testing

* Auth test
* Permission test
* Tenant isolation test

Then continue into ERP domain modules.

---

# 133. PERMISSION MATRIX UI

Build an advanced permission matrix.

Example:

| Module    | View | Create | Edit | Delete | Approve | Export |
| --------- | ---- | ------ | ---- | ------ | ------- | ------ |
| Sales     | ✓    | ✓      | ✓    | ✗      | ✗       | ✓      |
| PO        | ✓    | ✓      | ✓    | ✗      | ✓       | ✓      |
| Inventory | ✓    | ✗      | ✗    | ✗      | ✗       | ✓      |

Support:

* Select entire module
* Select all
* Clear
* Inherit
* User override

---

# 134. FORM PERMISSION UI

Admin should eventually see:

```text
Sales Order Form

Customer
View ✓
Edit ✓

Cost Price
View ✗
Edit ✗

Selling Price
View ✓
Edit ✓

Profit Margin
View ✗
Edit ✗
```

---

# 135. DYNAMIC STATUS CONFIGURATION

Support status metadata:

* Label
* Color semantic
* Icon
* Ordering
* Terminal state
* Active/inactive

Do not allow tenant configuration to break domain integrity.

---

# 136. MASTER DATA IMPORT

Prepare Excel/CSV imports for:

* Customers
* Vendors
* Fabric
* Accessories
* Styles
* Opening Inventory

Validate imports before committing.

---

# 137. BULK OPERATIONS

Permission-controlled bulk actions:

* assign
* approve
* export
* print
* status update where safe

High-impact bulk actions require confirmation.

---

# 138. COMMENTS AND MENTIONS

Allow contextual comments on:

* orders
* PO
* style
* QC
* workflow tasks

Support:

```text
@user
```

Generate notification.

---

# 139. TASK / INBOX

Create a "My Work" inbox.

Show:

* Pending approvals
* QC tasks
* Assigned production tasks
* Material shortage actions
* Rework
* Overdue work

This should become a major homepage feature for operational users.

---

# 140. COMMAND CENTER

Owner/Admin should have Operations Command Center.

Show:

```text
Orders at Risk
Blocked Orders
Overdue Approvals
Material Shortages
QC Failures
Job Work Delays
Dispatch Due
```

---

# 141. MOBILE HOME

Mobile should prioritize actions.

Example:

```text
Scan Bundle
My Tasks
Approvals
QC
Orders
Notifications
```

Not a miniature desktop dashboard.

---

# 142. PUSH NOTIFICATIONS

Prepare mobile push notifications using Expo Notifications or suitable service.

Opening a notification must deep-link to the correct record.

---

# 143. DEEP LINKS

Example:

```text
erp://orders/123
erp://approvals/456
erp://qc/789
```

---

# 144. QR SECURITY

QR code should contain opaque identifiers or signed tokens.

Do not expose sensitive business information directly in QR.

---

# 145. PRINTING

Prepare print templates:

* Bundle label
* QR label
* Packing list
* Dispatch note
* PO
* Invoice
* Job work challan

---

# 146. PRODUCTION KPIs

Calculate:

* Planned vs actual
* Stage efficiency
* WIP
* Rejection %
* Rework %
* Wastage %
* On-time delivery %
* Vendor performance
* Order cycle time

---

# 147. ANALYTICS ARCHITECTURE

Operational transactions must remain normalized.

Create reporting views/materialized views where useful instead of damaging transactional schema for dashboards.

---

# 148. DATABASE PERFORMANCE

Index common tenant-scoped queries.

Typical indexes:

```text
tenant_id
tenant_id + status
tenant_id + created_at
tenant_id + order_number
tenant_id + style_id
tenant_id + production_order_id
```

Use explain plans when needed.

---

# 149. EVENT NAMES

Use past-tense domain events.

Good:

```text
OrderConfirmed
POApproved
MaterialReserved
CuttingCompleted
QCRejected
BundleScanned
PackingCompleted
OrderDispatched
```

Avoid vague events like:

```text
UpdateDone
DataChanged
ProcessEvent
```

---

# 150. EVENT SCHEMA REGISTRY

Document event contracts.

Version them.

Do not silently make breaking event changes.

---

# 151. UI FEEDBACK

After user action:

Show meaningful feedback.

Example:

```text
PO approved successfully.
Material planning has been notified.
```

Not:

```text
Success.
```

---

# 152. OPTIMISTIC UI

Use optimistic updates only when safe.

Do not optimistically show approval, inventory or financial operations as final before backend confirmation.

---

# 153. CONCURRENCY

Handle concurrency.

Examples:

Two users cannot consume the same fabric stock beyond available balance.

Two approvers should not produce invalid duplicate transitions.

Use:

* transactions
* locks where required
* optimistic concurrency/version columns where appropriate

---

# 154. DATA VERSIONING

For records like:

* BOM
* Style
* Workflow
* Approval Rule

store version numbers.

---

# 155. AI CONFIGURATION UI

Tenant Admin can configure:

```text
AI Enabled
Provider
Model
Usage limit
Modules allowed
```

Do not display full secret API key after saving.

Use masked values.

---

# 156. AI FALLBACK

AI Gateway may support fallback provider.

Example:

```text
Primary: Gemini
Fallback: Groq
```

But do not retry endlessly.

---

# 157. AI CACHE

Cache non-sensitive repeated AI tasks where safe.

Do not cache user-sensitive conversational output globally across tenants.

---

# 158. AI PROMPT MANAGEMENT

Create central prompt templates.

Store:

* name
* module
* version
* template
* active version

Do not scatter giant AI prompts throughout controllers.

---

# 159. AI FEEDBACK

Allow users to mark AI responses:

```text
Helpful
Not Helpful
```

Use feedback for future evaluation.

---

# 160. FINAL PRODUCT EXPECTATION

I want the final product to feel like a real modern SaaS ERP, not a student project.

It should be:

* Fast
* Beautiful
* Professional
* Responsive
* Secure
* Scalable
* Dynamic
* Configurable
* Auditable
* Multi-tenant
* Event-driven
* AI-powered
* Mobile-ready
* Maintainable

---

# 161. IMPORTANT BUSINESS RULE

For every stage:

**Verify → QC → Approval → Event → Notification → Next Stage**

when configured.

A user must never move an order to the next manufacturing stage merely by changing a dropdown value.

Transitions must go through the Workflow Engine.

---

# 162. END-TO-END TRACEABILITY

A manager should be able to open a customer order and see:

```text
ORDER
│
├── Customer
├── Styles
├── Quantities
├── PO
├── BOM
├── Materials
├── Inventory Reservation
├── Cutting
├── Bundles
├── Stitching
├── Job Work
├── Wash
├── QC
├── Rework
├── Packing
├── Finished Goods
├── Dispatch
├── Invoice
├── Payments
├── Timeline
├── Documents
├── Approvals
├── Audit Log
└── AI Insights
```

---

# 163. FINAL AGENT INSTRUCTION

Start by doing the following:

1. Read the attached Kidswear Manufacturing ERP + AI Blueprint completely.
2. Inspect the current repository if one exists.
3. Create the recommended monorepo architecture.
4. Create `docs/IMPLEMENTATION_PLAN.md`.
5. Create `docs/ARCHITECTURE.md`.
6. Create `docs/DATABASE.md`.
7. Create `docs/PERMISSIONS.md`.
8. Create `docs/EVENTS.md`.
9. Create `docs/WORKFLOWS.md`.
10. Set up Docker infrastructure.
11. Implement authentication.
12. Implement multi-tenancy.
13. Implement dynamic module system.
14. Implement role/user/module/action/field/form permissions.
15. Build the responsive application shell.
16. Build the SaaS Super Admin.
17. Add event bus + transactional outbox.
18. Add audit logging.
19. Add notifications.
20. Start the first ERP vertical slice.

Do not stop after planning.

After planning, begin implementing the working application.

At every milestone:

* run lint
* run typecheck
* run tests
* run database migrations
* verify the application boots
* verify responsive UI
* verify tenant isolation
* update documentation

When you discover a missing requirement, choose the safest scalable enterprise default and document the decision.

The objective is to deliver a **complete interactive Kidswear Manufacturing SaaS ERP with a premium responsive UI, event-driven backend, dynamic workflow engine, granular permission system, mobile application, and integrated AI capabilities.**
