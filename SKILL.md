---
name: prd-write
description: Structured product requirement writing workflow for turning ideas, Feishu docs, PRD drafts, HTML prototypes, app/mini-program/PC demos, or screenshots into a complete PRD. Use when the user asks to write, update, rewrite, review-then-write, or directly publish a PRD/需求文档/产品方案, especially when the work should first clarify requirements with brainstorming or superpower, then build or inspect a prototype demo, then write a PRD with background, roles, permissions, business flowchart, requirement description, analytics events, and acceptance checklist.
---

# PRD Write

## Core Rule

Run the workflow in this order:

1. Clarify requirements with Superpowers `using-superpowers` + `brainstorming`, or a local brainstorming pass if Superpowers is unavailable.
2. Generate a first-pass visual prototype with image2/imagegen from the clarified product description.
3. Build, read, or refine an interactive HTML demo based on that visual prototype to validate real interactions.
4. Capture interactive demo screens and optionally redraw them with image2/imagegen for a cleaner PRD presentation.
5. Write the PRD with the user's PRD template and update only the explicitly targeted document.

Do not jump straight into PRD writing when the product path is still blurry.

## Workflow

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
- Open questions that block implementation versus details that can be assumed.

When the user already gives enough context, summarize assumptions and proceed.

### 2. First-Pass Visual Prototype

After requirement brainstorming and before building HTML, use image2/imagegen or an equivalent image generation capability to create a first-pass static prototype from the clarified product description.

Use this node to:

- Turn rough user language into concrete page composition, hierarchy, and visual direction.
- Explore key screens before spending time on interactive HTML.
- Align with the user on product feel, information density, and workflow coverage.

Rules:

- Generate only screens that are needed to understand the main workflow and major exceptions.
- Keep output close to the clarified requirement; do not invent unapproved business logic.
- Label unresolved areas as assumptions in discussion, not as final PRD facts.
- Treat this visual prototype as a design draft, not as source-of-truth interaction logic.

### 3. Interactive HTML Demo

Build, read, or refine an interactive HTML demo before writing the PRD.

- Base the HTML demo on the approved first-pass visual prototype.
- For an existing HTML prototype, inspect the DOM, screens, state variables, event handlers, and navigation paths.
- For screenshots, map every screenshot to a page state and interaction step.
- For a new prototype request, create a concise demo that exposes the real workflow, not a marketing page.
- Add enough interaction to validate navigation, branching, state transitions, and major exception paths.
- Capture key screens for the PRD. Prefer actual prototype screenshots when available.
- List screen inventory, user actions, state transitions, empty/error states, and backend dependencies.

### 4. PRD Screenshot Redraw

Before final Feishu writeback, decide whether the prototype screenshots should be redrawn.

Use image2/imagegen or an equivalent image generation/editing capability when:

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

### 5. Business Flowchart

Create a flowchart before or during PRD writing.

- Use Mermaid for draft logic.
- When writing to Feishu and the PRD needs a process diagram, insert a Feishu whiteboard and write the flowchart there.
- Include the main path, branching by role/status, exception paths, and terminal states.
- Use product language in node labels, not implementation jargon.

### 6. PRD Composition

Read `references/prd-template.md` when writing the PRD body.

Required sections:

- Requirement background and goals.
- Scope and non-goals.
- Roles and permissions.
- Business process flowchart.
- Requirement description.
- State machine or status rules when status affects behavior.
- Data, interface, or field requirements when needed.
- Analytics and event tracking.
- Risk, exception, and compliance handling.
- Acceptance checklist.

If the user provides an existing PRD template/reference, follow that structure and style unless it conflicts with the requested workflow.

### 7. Requirement Description Layout

Read `references/page-description-layout.md` when writing screen-level requirements.

- For app or mini-program screens: use a two-column layout. Left side is the prototype screenshot, right side is requirement details.
- For PC pages: use a vertical layout. Screenshot on top, requirement details below.
- Each page description should cover page goal, entry condition, displayed fields, user actions, validation, backend dependency, empty/error states, and tracking events.

### 8. Feishu Writeback

When the target is a Feishu doc/wiki:

- Use `lark-doc`, `lark-wiki`, and `lark-whiteboard` skills as needed.
- Only modify the document explicitly named as the target. Treat other Feishu links as read-only references unless the user explicitly says they may be changed.
- Run screenshot redraw before this step if the PRD should use polished prototype images.
- Upload local images with paths relative to the current working directory when using `lark-cli`; avoid absolute `--file` paths.
- If the CLI cannot access credentials in the current environment, prepare a self-contained script and tell the user exactly what it will modify.

## Output Quality Checklist

Before finalizing:

- The PRD reflects one clear product方案 unless the user explicitly asks for alternatives.
- The flowchart matches the described screens and state transitions.
- Requirement descriptions match the screenshots/prototype.
- Redrawn prototype images preserve the original interaction and do not introduce unapproved requirements.
- Roles and permissions are explicit.
- Analytics events map to key user actions and business states.
- Acceptance criteria are testable.
- Reference documents were not modified accidentally.
