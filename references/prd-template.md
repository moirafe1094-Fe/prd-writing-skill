# PRD Template

Use this structure when no stronger user-provided PRD template overrides it.

## 1. Requirement Background

Cover:

- Current business context.
- User pain point or operational gap.
- Why now.
- Expected business outcome.
- Success metrics when available.

## 2. Goals, Scope, And Non-Goals

Use a table:

| Type | Content |
| --- | --- |
| Goals | What the product must achieve |
| In scope | What this PRD covers |
| Out of scope | What this PRD will not solve |
| Dependencies | External systems, upstream data, policy, finance, legal, or ops dependencies |

## 3. Roles And Permissions

Include:

- Role definition.
- Entry points.
- Viewable data.
- Allowed actions.
- Forbidden actions.
- Audit log requirements when actions affect money, inventory, task status, contracts, approvals, or customer data.

## 4. Business Process Flowchart

Use a flowchart to show:

- Main success path.
- Role/status branching.
- Exception handling.
- End states.

For Feishu PRDs, prefer a whiteboard over plain Mermaid text in the final doc.

## 5. Requirement Description

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

## 6. Status And Rules

Add when behavior depends on status.

Recommended table:

| Status | Definition | Entry condition | User/system action | Next status |
| --- | --- | --- | --- | --- |

## 7. Interfaces, Fields, And Data

Include only when useful for execution:

- API or service name.
- Purpose.
- Request fields.
- Response fields.
- Error codes.
- Idempotency and retry rules.
- Data ownership and source of truth.

## 8. Analytics Events

Recommended table:

| Event | Trigger | Properties | Purpose |
| --- | --- | --- | --- |

Properties commonly include user_id, role, page_id, task_id, store_id, status, amount, result, failure_reason, and source.

## 9. Risk And Exception Handling

Cover:

- Permission risk.
- Fraud/collusion risk.
- Data consistency risk.
- Financial/compliance risk.
- Privacy and sensitive data handling.
- Manual review or fallback path.

## 10. Acceptance Checklist

Write as testable statements:

- User can complete the main flow.
- Each role sees only permitted data/actions.
- Each exception state has a visible and recoverable behavior.
- Status and data updates are idempotent.
- Analytics fire at required points.
- Flowchart, prototype, and PRD text are consistent.
