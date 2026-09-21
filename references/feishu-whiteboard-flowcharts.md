# Feishu Whiteboard Flowchart Rules

Use this reference when a PRD needs business process flowcharts or product flow diagrams.

## Two-Step Rule: Confirm Flow In Text First, Then Draw

**Never draw before the user confirms the text flow.**

1. **Text confirmation**: List roles, steps, branches, exceptions, start/end nodes in plain language. Get explicit user approval.
2. **Whiteboard output**: Only after approval, create the Feishu whiteboard diagram with `lark-whiteboard`.

Applies to:

- **3.2 业务流程图** → swimlane SVG whiteboard
- **3.3 产品流程图** → role sequence / page-flow SVG whiteboard

If the user changes the flow after seeing the diagram, update the text confirmation first, then redraw.

## Diagram Type Mapping

| PRD section | Diagram type | Whiteboard format |
| --- | --- | --- |
| 3.2 业务流程图 | Business process swimlane | SVG swimlane with actor/phase lanes |
| 3.3 产品流程图 | Product flow / role sequence | SVG sequence or page-flow map |

## Final Output Rule

The final Feishu PRD must present diagrams as Feishu whiteboard blocks. Do not leave raw Mermaid, PlantUML, SVG source text, code blocks, or screenshot-only diagrams as the final output.

| Diagram complexity | Final Feishu format |
| --- | --- |
| Simple flow, under 12 nodes | `<whiteboard type="svg">` |
| Medium flow, 12-30 nodes | `<whiteboard type="svg">` with grouped lanes |
| Complex flow, many branches | Blank whiteboard + `lark-whiteboard` editable nodes |

## Visual Style

- Title and subtitle at the top
- Phase rows or swimlanes for actors, lifecycle stages, or pages
- Rounded cards for steps, pages, states, decisions
- Arrows for primary flow; dashed for fallback; colored for exceptions
- Compact legend when status colors are meaningful
- Readable at 50%-70% zoom

## Color Semantics

| Meaning | Color |
| --- | --- |
| Primary flow | Blue |
| Approved / completed | Green |
| Review / pending | Purple |
| Rejected / failed | Red |
| Timeout / manual intervention | Orange or yellow |
| Neutral lane background | Light blue, gray |

## Text Confirmation Template (before drawing)

Use this format when confirming with the user:

```markdown
### 业务流程（待确认）

**场景**：[scenario name]
**参与角色**：[role A, role B, system]
**主路径**：
1. [role] → [action] → [result]
2. ...
**分支/异常**：
- 若 [condition] → [branch]
**新增/修改标记**：[node X 新增, node Y 修改]
**起止**：[start] → [end]
```

For product flow (3.3), add page/system names and interaction order between roles.

## Writeback Rules

- Insert the whiteboard block near the related PRD section (3.2 or 3.3).
- Export or preview after insertion; verify legibility and connector direction.
- One diagram per scenario unless the user asks for a combined overview.
- Caption example: `订单审核业务全流程` or `App 端页面与状态流转图`

## Skills

- Create/update whiteboards: `lark-whiteboard`
- Insert into Feishu doc: `lark-doc` (see `lark-doc-whiteboard.md`)
