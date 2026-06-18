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

Use this output structure for the analytics section. Do not replace it with a generic Event/Trigger/Properties table, the previous Data设计/字段枚举 block, or the old 名称/发起方/动作类型 table.

| 埋点ID | 事件名（event_name） | 事件名 | 端 | 模块/页面 | 触发时机 | 角色 | 属性清单 | 属性说明 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 唯一编号 | 英文 snake_case，全局唯一 | 业务可读名称 | Android/iOS/PC/H5/小程序/后台 | 页面或功能模块 | 何时上报（精确到动作） | 触发用户角色 | 键值对清单 | 每个属性的类型、含义、枚举 | 点位生命周期状态 |
| TRK-REQ-001-001 | order_submit_click | 提交订单按钮点击 | 造旺App、造旺PC | 订单确认页 | 用户点击「提交订单」且校验通过后 | 合伙人、区域经理 | order_id, amount, sku_count | amount: number，单位元 | 待评审/已评审/开发中/已上线/已废弃 |

Table rules:

- 埋点ID: use a globally unique tracking point id, such as `TRK-REQ-001-001`. Keep numbering stable after review.
- 事件名（event_name）: use English `snake_case`; keep it globally unique and stable for implementation.
- 事件名: write a business-readable Chinese event name.
- 端: list every applicable terminal, such as Android, iOS, PC, H5, 小程序, 后台, or specific app names.
- 模块/页面: write the page or functional module where the event happens.
- 触发时机: state exactly when the event is reported, precise to the user/system action and validation condition.
- 角色: list the triggering user role.
- 属性清单: list property keys as a comma-separated key list. Include PV/UV-related identity or counting properties when needed.
- 属性说明: explain each property's type, meaning, unit, enum, and UV deduplication rule when relevant.
- 状态: use lifecycle statuses such as 待评审, 已评审, 开发中, 已上线, or 已废弃.

The analytics plan must include menu exposure/click events and core behavior events. Each event should state PV/UV collection requirements through 属性清单 and 属性说明. UV commonly deduplicates by employeeId, userId, device_id, or another agreed identity within the selected time window.

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
- Menu and core behavior analytics use the required table columns, event_name naming, property list, property descriptions, lifecycle status, and fire at required points with PV and UV counting rules verified.
- Flowchart, prototype, and PRD text are consistent.
- The target Feishu document was the only modified reference.
