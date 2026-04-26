# PRD Template

Use this structure when no stronger user-provided PRD template overrides it.

## 1. Requirement Background

Cover:

- Current business context.
- User pain point or operational gap.
- Why now.
- Expected business outcome.
- Success metrics when available.

## 2. Source Materials And Decisions

Use this when the PRD is assembled from Feishu references, demos, screenshots, or prior drafts.

| Type | Content | Rule |
| --- | --- | --- |
| Write target | The document/wiki/page to update | Only this document may be modified |
| Read-only references | Background docs, PRD examples, flowcharts, data tables | Do not modify unless user explicitly says so |
| Prototype assets | HTML demos, screenshots, image2 drafts, redrawn images | Keep mapping to requirement sections |
| Decisions | Confirmed product decisions | Treat as PRD facts |
| Assumptions/open questions | Unresolved items | Label clearly and do not present as final facts |

## 3. Goals, Scope, And Non-Goals

Use a table:

| Type | Content |
| --- | --- |
| Goals | What the product must achieve |
| In scope | What this PRD covers |
| Out of scope | What this PRD will not solve |
| Dependencies | External systems, upstream data, policy, finance, legal, or ops dependencies |

## 4. Roles And Permissions

Include:

- Role definition.
- Entry points.
- Viewable data.
- Allowed actions.
- Forbidden actions.
- Audit log requirements when actions affect money, inventory, task status, contracts, approvals, or customer data.

Recommended table:

| Role | Entry point | Viewable data | Allowed actions | Forbidden actions | Audit requirement |
| --- | --- | --- | --- | --- | --- |

## 5. Business Process Flowchart

Use a flowchart to show:

- Main success path.
- Role/status branching.
- Exception handling.
- End states.

For Feishu PRDs, prefer a whiteboard over plain Mermaid text in the final doc.

## 6. Page And State Inventory

Write this before detailed page requirements.

| Page/module | Actor | Entry condition | Core action | Key state | Exception state |
| --- | --- | --- | --- | --- | --- |

## 7. Requirement Description

For each page/module:

- Page/module name.
- Prototype screenshot placement according to platform layout rules.
- Page goal.
- Entry condition.
- Displayed fields.
- User actions.
- Validation rules.
- Backend/data dependency.
- Empty, loading, disabled, failed, expired, and repeated-submit states.
- Tracking events.

## 8. Status And Rules

Add when behavior depends on status.

Recommended table:

| Status | Definition | Entry condition | User/system action | Next status |
| --- | --- | --- | --- | --- |

## 9. Interfaces, Fields, And Data

Include only when useful for execution:

- API or service name.
- Purpose.
- Request fields.
- Response fields.
- Error codes.
- Idempotency and retry rules.
- Data ownership and source of truth.

Recommended field table:

| Field | Meaning | Source of truth | Required | Validation/display rule |
| --- | --- | --- | --- | --- |

## 10. Analytics Events

Recommended table:

| Event | Trigger | Properties | Purpose | QA check |
| --- | --- | --- | --- | --- |

Properties commonly include user_id, role, page_id, task_id, store_id, status, amount, result, failure_reason, and source.

## 11. Risk And Exception Handling

Cover:

- Permission risk.
- Fraud/collusion risk.
- Data consistency risk.
- Financial/compliance risk.
- Privacy and sensitive data handling.
- Manual review or fallback path.

## 12. Acceptance Checklist

Write as testable statements:

- User can complete the main flow.
- Each role sees only permitted data/actions.
- Each exception state has a visible and recoverable behavior.
- Status and data updates are idempotent.
- Analytics fire at required points.
- Flowchart, prototype, and PRD text are consistent.
- The target Feishu document was the only modified reference.
