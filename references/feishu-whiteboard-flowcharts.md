# Feishu Whiteboard Flowchart Rules

Use this reference when a PRD needs business process flowcharts, page/status maps, approval flows, lifecycle diagrams, or role collaboration diagrams.

## Final Output Rule

The final Feishu PRD must present flowcharts as Feishu whiteboard blocks. Do not leave raw Mermaid, PlantUML, SVG source text, code blocks, or screenshot-only diagrams as the final output.

Preferred output by complexity:

| Diagram complexity | Final Feishu format |
| --- | --- |
| Simple flow, under 12 nodes | `<whiteboard type="svg">` |
| Medium flow, 12-30 nodes, clear phases | `<whiteboard type="svg">` with grouped lanes/sections |
| Complex flow, many branches, cross-role status map | Blank Feishu whiteboard plus `lark-whiteboard` editable SVG/native nodes |
| Approval-heavy process | SVG whiteboard swimlane or phase-row diagram |
| Page/status relationship map | SVG whiteboard page/status map |

## Visual Style

Create diagrams similar to polished product whiteboards:

- Use a title and subtitle at the top.
- Use phase rows, swimlanes, or grouped bands to separate actors, lifecycle stages, pages, or status domains.
- Use rounded cards for steps, pages, states, decisions, and outcomes.
- Use arrows for primary flow, dashed arrows for fallback/return/async paths, and colored arrows for exception branches.
- Use small numbered chips for ordered steps.
- Use a compact legend for role, page, status, pass/fail, timeout, freeze, or rollback semantics.
- Keep labels concise and product-facing.
- Leave enough spacing so Feishu reviewers can read the diagram at 50%-70% zoom.

## Color Semantics

Use consistent colors:

| Meaning | Color direction |
| --- | --- |
| Primary flow / default action | Blue |
| Approved / effective / completed | Green |
| Review / freeze / pending review | Purple |
| Rejected / failed / voided | Red |
| Timeout / pending / manual intervention | Orange or yellow |
| Neutral background lane | Light blue, light purple, light green, or light gray |
| Notes / constraints | Pale yellow or light gray |

## Diagram Types

### Business Process Flow

Use when describing an end-to-end business process.

Required content:

- Actor or phase lanes.
- Main success path.
- Key review/approval nodes.
- Exception branches.
- End states.
- Legend if statuses or colors are meaningful.

### Page And Status Map

Use when describing how pages, roles, and statuses relate.

Required content:

- Role/page cards grouped by app/PC/backend or actor.
- Status transition strip or phase row.
- Page entry and exit conditions.
- Shared data/state notes.
- Cross-terminal sync notes when applicable.

### Approval Or Freeze/Unfreeze Flow

Use when approval, freezing, settlement, audit, or risk control is central.

Required content:

- Submitter lane.
- Reviewer lane.
- System/risk-control lane when applicable.
- Approve/reject/timeout branches.
- Data or money/status effect after each branch.
- Final state card.

## SVG Whiteboard Construction Guidance

When generating `<whiteboard type="svg">`:

- Use an SVG viewport large enough for readability, usually 1200-1800px wide.
- Use `rect` with rounded corners for cards and lanes.
- Use `text` for labels; avoid tiny text.
- Use `path` or `line` with arrow markers for connectors.
- Use consistent spacing and alignment.
- Include a subtle background and lane bands when the diagram has multiple roles or phases.
- Keep the SVG self-contained; do not reference external assets.
- Do not paste SVG as a code block in the final PRD. Insert it as a Feishu whiteboard block.

## Writeback Rules

When the target is a Feishu doc/wiki:

- Insert the flowchart as a whiteboard block near the related PRD section.
- For simple/medium SVG diagrams, use `<whiteboard type="svg">`.
- For complex diagrams, create or update a Feishu whiteboard with `lark-whiteboard`.
- Confirm the visible Feishu block renders as a diagram, not raw source text.
- Use the diagram caption to name the scenario, such as `抄单审核与旺金币冻结业务全流程` or `拜访计划与日复盘角色页面与状态地图`.
- Keep one diagram per scenario unless the user explicitly asks for a combined overview.
