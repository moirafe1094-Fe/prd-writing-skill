---
name: prd-write
description: Structured product requirement writing workflow for turning ideas, Feishu docs, PRD drafts, HTML prototypes, app/mini-program/PC demos, or screenshots into a complete PRD. Use when the user asks to write, update, rewrite, review-then-write, or directly publish a PRD/需求文档/产品方案, especially when the work should first inventory source materials, clarify requirements with brainstorming or Superpowers, create a requirement brief, design page/state inventory, build or inspect a prototype demo, then write a PRD with background, roles, permissions, business flowchart, requirement description, session/concurrency handling, PV/UV analytics events, acceptance checklist, and Feishu-ready screenshots.
---

# PRD Write

## Core Rule

Run the workflow in this order:

1. Inventory source materials and mark the single write target; treat all other Feishu links as read-only references.
2. Clarify requirements with Superpowers `using-superpowers` + `brainstorming`, or a local brainstorming pass if Superpowers is unavailable.
3. Produce a requirement brief and get alignment before design-heavy work.
4. Create a page/state inventory before image generation so visual work does not invent workflow coverage.
5. Generate a first-pass visual prototype with imagegen from the clarified product description.
6. Build, read, or refine an interactive HTML demo based on that visual prototype to validate real interactions.
7. Verify the demo flow, capture key screens, and optionally redraw them with imagegen for a cleaner PRD presentation.
8. Prepare business artifacts: flowchart, status machine, roles/permissions, fields/data dependencies, session/concurrency handling, analytics, and acceptance checks.
9. Write the PRD with the user's PRD template, self-check it, then update only the explicitly targeted document.

Do not jump straight into PRD writing when the product path is still blurry.

## Workflow

### 0. Source Inventory And Target Safety

Before brainstorming or editing, list the available inputs and classify each item.

- Target document: the one document/wiki/page that may be modified.
- Read-only references: Feishu docs, PRD examples, flowcharts, meeting notes, screenshots, HTML demos, data tables, API docs, or prior drafts.
- Prototype assets: current HTML files, screenshots, imagegen drafts, redrawn images, and generated artifacts.
- External systems: CRM, payment, inventory, approval, messaging, data warehouse, or manual operations.
- Constraints: deadline, platform, brand/design system, compliance, money/data risk, and permission boundaries.

If there is any ambiguity about which Feishu document may be edited, stop and ask before writeback.

### 1. Requirement Brainstorming

If Superpowers is installed, first use `using-superpowers`, then use `brainstorming` for requirement clarification and prototype design. If those skills are unavailable, run a compact brainstorming pass yourself.

Clarify these points before writing:

- Business background and why this change matters now.
- Primary users, secondary users, operators, reviewers, admins, and external systems.
- Platform type: mini-program, app, PC web, admin backend, or mixed.
- Existing inputs: Feishu docs, PRD drafts, HTML demos, screenshots, data tables, API docs, meeting notes.
- Final target: local document, Feishu doc/wiki, or a new artifact.
- Product scope: in scope, out of scope, and explicit non-goals.
- Main success path and important exception paths.
- Permissions, state changes, money/data/compliance risks, and audit needs.
- Whether Session mechanism handling is involved. Clarify login/session identity, session expiration, refresh/renewal, cross-device behavior, account switching, logout/invalid session handling, and whether the PRD should explicitly state "not involved".
- Whether concurrency scenarios are involved. Clarify repeated submit, simultaneous edits/actions, multi-user approval or task processing, inventory/quota/money/status updates, idempotency, locking, conflict resolution, retry, and whether the PRD should explicitly state "not involved".
- Menu and core behavior tracking. Identify menu exposure/click and core action events, define PV and UV counting requirements, and map each event to the required analytics table fields: 埋点ID, 事件名（event_name）, 事件名, 端, 模块/页面, 触发时机, 角色, 属性清单, 属性说明, and 状态.
- Open questions that block implementation versus details that can be assumed.

Output a short requirement brief before visual or HTML work:

- One-sentence product intent.
- Business goal and success signal.
- Users/roles and permission boundaries.
- In scope, out of scope, and explicit non-goals.
- Main success path and important exception paths.
- Session mechanism decision: involved or not involved, with key rules or open questions.
- Concurrency scenario decision: involved or not involved, with key rules or open questions.
- Tracking scope: menus and core behaviors that must record PV and UV, with preliminary event_name, platform, module/page, trigger timing, role, properties, property descriptions, and lifecycle status.
- Key assumptions and open questions.
- Proposed next artifact: image prototype, HTML demo, PRD outline, or Feishu writeback.

When the user already gives enough context, summarize assumptions and proceed, but still keep the brief as the source of truth.

### 2. Page And State Inventory

Create a screen/module inventory before image generation or HTML work.

For each page or module, capture:

- Platform and layout type: mini-program/app two-column PRD layout, PC vertical PRD layout, backend/admin, or mixed.
- Entry condition and actor.
- Session dependency, session change, or invalid-session behavior.
- Primary user decision or action.
- Required displayed fields and data source.
- Actions, validation, concurrent/repeated-operation handling, and next state.
- Empty, loading, disabled, expired, failed, repeated-submit, and permission-denied states.
- Related tracking events, explicitly distinguishing menu tracking and core behavior tracking, with PV/UV requirements and the required analytics table fields.

For workflows driven by task/order/payment/approval status, create a status table before writing page details:

| Status | Definition | Entry condition | User/system action | Next status |
| --- | --- | --- | --- | --- |

### 3. First-Pass Visual Prototype

After the requirement brief and page/state inventory, use imagegen to create a first-pass static prototype from the clarified product description. If imagegen is unavailable, stop and tell the user instead of silently substituting another generator.

Use this node to:

- Turn rough user language into concrete page composition, hierarchy, and visual direction.
- Explore key screens before spending time on interactive HTML.
- Align with the user on product feel, information density, and workflow coverage.

Rules:

- Generate only screens that are needed to understand the main workflow and major exceptions.
- Keep output close to the clarified requirement; do not invent unapproved business logic.
- Label unresolved areas as assumptions in discussion, not as final PRD facts.
- Treat this visual prototype as a design draft, not as source-of-truth interaction logic.

### 4. Interactive HTML Demo

Build, read, or refine an interactive HTML demo before writing the PRD.

- Base the HTML demo on the approved first-pass visual prototype.
- For an existing HTML prototype, inspect the DOM, screens, state variables, event handlers, and navigation paths.
- For screenshots, map every screenshot to a page state and interaction step.
- For a new prototype request, create a concise demo that exposes the real workflow, not a marketing page.
- Add enough interaction to validate navigation, branching, state transitions, and major exception paths.
- Capture key screens for the PRD. Prefer actual prototype screenshots when available.
- List screen inventory, user actions, state transitions, empty/error states, and backend dependencies.

Validate the demo with a compact interaction matrix:

| Screen | Actor | Action | Expected result | State change | Edge case |
| --- | --- | --- | --- | --- | --- |

### 5. PRD Screenshot Redraw

Before final Feishu writeback, decide whether the prototype screenshots should be redrawn.

Use imagegen when:

- The prototype screenshot is visually rough but the interaction is already clear.
- The PRD needs cleaner, more consistent app/mini-program/PC visuals.
- The user explicitly asks to redraw, beautify, or normalize prototype screenshots.

Rules:

- Preserve the original interaction, fields, wording, page state, and information hierarchy.
- Do not invent new features, controls, metrics, states, or business rules during redraw.
- Keep a mapping from original screenshot to redrawn image so the PRD remains traceable.
- If both are useful, keep original screenshots for validation and use redrawn images in the PRD.
- Label redrawn assets clearly in filenames or captions when they are not direct screenshots.

Read `references/page-description-layout.md` for how first-pass visuals, HTML screenshots, and redrawn PRD images should be placed or tracked.

### 6. Business Artifacts

Create the business artifacts before or during PRD writing.

- Business flowchart: split complex workflows into small scenario-level diagrams instead of one combined mega-flow. Separate by business scenario, product type, actor path, lifecycle stage, or state transition when branches would otherwise mix together. Use the user's actual business terms; do not reuse example labels unless they appear in the source materials.
- Feishu PRD product/business flowcharts must be inserted as Feishu whiteboard blocks, not left as raw Mermaid, PlantUML, SVG source, screenshots, or code blocks. Simple flows may use `<whiteboard type="svg">`, `<whiteboard type="mermaid">`, or `<whiteboard type="plantuml">`; complex flows use a blank whiteboard plus `lark-whiteboard`. Never leave `<pre lang="mermaid">` or similar source code as the final flowchart presentation in Feishu.
- Feishu process diagrams: prefer Feishu-compatible PlantUML swimlane activity diagrams for final PRD presentation when the flow is approval-heavy. Keep each diagram to one scenario with one start, one end, clear swimlanes, and only the exception paths needed for that scenario. Avoid nested multi-scenario diagrams that combine unrelated create/close, submit/review, approve/reject, timeout, vacancy, resignation, or fallback rules in one chart.
- Roles and permissions matrix: role, entry point, viewable data, allowed action, forbidden action, audit requirement.
- Status machine: status definition, entry condition, trigger action, next status, exception/fallback.
- Session handling: state whether Session is involved. If involved, define session identity, validity/expiration, renewal, logout/invalid-session behavior, account switching, cross-device behavior, and affected pages/actions. If not involved, record that decision explicitly when it was part of clarification.
- Concurrency handling: state whether concurrency is involved. If involved, define duplicate submission prevention, idempotency, locking or optimistic conflict rules, retry behavior, status/data consistency, and user-visible conflict/error handling. If not involved, record that decision explicitly when it was part of clarification.
- Field/data dictionary: field name, meaning, source of truth, required/optional, validation, display rule.
- Analytics plan: output the analytics event table with exactly these columns: 埋点ID, 事件名（event_name）, 事件名, 端, 模块/页面, 触发时机, 角色, 属性清单, 属性说明, 状态. Do not use the previous Data设计/字段枚举 block or the old 名称/发起方/动作类型 table. Put PV/UV counting rules, UV deduplication key, and special collection rules in 属性清单 and 属性说明.

Use product language in labels, not implementation jargon.

### 7. PRD Composition

Read `references/prd-template.md` when writing the PRD body.

Required sections:

- Requirement background and goals.
- Scope and non-goals.
- Roles and permissions.
- Business process flowchart.
- Requirement description.
- State machine or status rules when status affects behavior.
- Data, interface, or field requirements when needed.
- Session mechanism handling and concurrency scenario handling. Include an explicit "not involved" conclusion when these were checked and ruled out.
- Analytics and event tracking, including menu and core behavior events that record PV and UV. Use the required table format from `references/prd-template.md`, not a generic Event/Trigger/Properties table.
- Risk, exception, and compliance handling.
- Acceptance checklist.

If the user provides an existing PRD template/reference, follow that structure and style unless it conflicts with the requested workflow.

Before publishing, run a PRD self-check. If a `check-prd` skill is available, use it; otherwise check manually for source coverage, flow/prototype/text consistency, permissions, status rules, session/concurrency handling, exception handling, required analytics table format, PV/UV analytics, and testable acceptance criteria.

### 8. Requirement Description Layout

Read `references/page-description-layout.md` when writing screen-level requirements.

- When an HTML prototype exists, the Feishu PRD functional requirements section must include the HTML prototype file itself near the section start. Prefer a standalone single-file HTML attachment when the original prototype depends on separate CSS/JS/assets; otherwise attach the original HTML file. Use `docs +media-insert --type file` and move the attachment block into the functional requirements section if the insert command appends it elsewhere.
- Requirement description sections must use a one-to-one screenshot-to-requirement layout when an HTML prototype exists: each requirement item starts with the matching HTML screenshot, followed immediately by its own requirement description. Do not batch all screenshots first and place descriptions elsewhere.
- For app or mini-program screens: use a two-column layout. Left side is the prototype screenshot, right side is requirement details.
- For PC pages: use a vertical layout. Screenshot on top, requirement details below.
- Each page description should cover page goal, entry condition, displayed fields, user actions, validation, backend dependency, session dependency, concurrency/repeated-operation handling, empty/error states, and menu/core tracking events with PV/UV requirements in the required analytics table format.

### 9. Feishu Writeback

When the target is a Feishu doc/wiki:

- Use `lark-doc`, `lark-wiki`, and `lark-whiteboard` skills as needed.
- Only modify the document explicitly named as the target. Treat other Feishu links as read-only references unless the user explicitly says they may be changed.
- Run screenshot redraw before this step if the PRD should use polished prototype images.
- Upload local images with paths relative to the current working directory when using `lark-cli`; avoid absolute `--file` paths.
- Prefer an outline/block-id read before editing an existing Feishu document; choose append, overwrite, or block-level replacement deliberately.
- Confirm before high-impact writeback, especially when replacing existing PRD content, inserting multiple images, or updating whiteboards.
- If the CLI cannot access credentials in the current environment, prepare a self-contained script and tell the user exactly what it will modify.

## Output Quality Checklist

Before finalizing:

- The PRD reflects one clear product方案 unless the user explicitly asks for alternatives.
- Source inventory identifies the write target and read-only references.
- Requirement brief, page/state inventory, prototype, flowchart, and PRD text agree with each other.
- Flowcharts are split into small scenario-level diagrams when a combined chart would mix unrelated branches or become hard to read.
- Each flowchart matches the described screens and state transitions for its scenario.
- Requirement descriptions match the screenshots/prototype.
- Status machine and permission matrix are explicit when behavior varies by status or role.
- Session involvement and concurrency involvement are explicitly answered, with rules documented when involved.
- Redrawn prototype images preserve the original interaction and do not introduce unapproved requirements.
- Roles and permissions are explicit.
- Analytics events map to menu exposure/click, core user actions, and business states, with PV and UV counting rules, required event_name naming, platform/module/trigger/role coverage, property list, property descriptions, lifecycle status, and the required table columns.
- Acceptance criteria are testable.
- Reference documents were not modified accidentally.

## UI Screenshot Evidence Standard

When the PRD is based on an existing UI design, screenshot, prototype, or visual reference, treat screenshots as structured product evidence rather than decoration.

Required capture pattern:

1. Start with one complete UI overview screenshot.
   - Capture the whole relevant screen, canvas, or full design frame first.
   - Place this overview before the detailed module analysis so readers can build spatial context.
   - Label it clearly, for example: "Overall UI reference" or "Full-page UI overview".

2. Follow with focused screenshots for each important area.
   - Crop or capture each specific module, interaction area, state, table, form, card, navigation region, or empty/loading/error state that the PRD discusses.
   - Each focused screenshot must be placed immediately next to the requirement text it supports.
   - Do not rely on a single full-screen capture when the requirement depends on visual details that are hard to inspect at full scale.

3. Describe each focused screenshot in product terms.
   - Explain what the user sees, what the component is for, what data or state it represents, and what behavior is implied.
   - Call out visible controls, labels, hierarchy, status indicators, default values, validation hints, and action affordances.
   - Connect the visual evidence to requirements, acceptance criteria, and edge cases.

4. Preserve visual traceability.
   - Use stable screenshot labels such as "Figure 1: Full UI overview", "Figure 2: Filter panel", and "Figure 3: Result card details".
   - Reference those labels from the corresponding requirement sections.
   - If multiple states exist, capture them separately instead of describing invisible state changes from memory.

Quality bar:

- A reader who has never seen the source UI should understand the full layout from the overview screenshot and the behavior of each key area from the focused screenshots.
- Screenshots should be sharp enough that important text and controls are legible.
- Avoid vague captions such as "screenshot above"; name the UI area and explain why it matters.
- For long pages or complex canvases, use one complete stitched/full-page view when possible, then separate crops for each key section.

Recommended Feishu PRD layout for UI-driven requirements:

1. At the start of the functional requirements section, attach the HTML/prototype file when one exists, then explain that screenshots are taken from that prototype or UI draft.
2. Add a dedicated overview subsection before module details, for example "6.0 整体 UI 稿".
   - Insert the complete UI screenshot in this subsection.
   - Explain which areas are changed in this requirement and which existing areas remain unchanged.
3. For each subsequent module subsection, use this order:
   - Focused screenshot for the module or state.
   - A short "页面目标" paragraph that explains the user's review/operation goal and why this module matters.
   - A requirement table with three columns: "模块/指标卡/字段", "需求说明", and "规则/异常".
4. In the table, separate display requirements from calculation rules, data-source rules, empty-state rules, and read-only/editability rules.
5. When an interaction is visible in the screenshot, such as click-to-preview, hover tooltip, sticky alert, disabled action, status dot, or empty placeholder, write it as an explicit requirement and add the exception behavior in the "规则/异常" column.
6. For metric modules, include formula, numerator/denominator, zero-value behavior, threshold behavior, and whether the field is only for display or can be manually edited.
