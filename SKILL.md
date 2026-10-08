---
name: prd-write
description: >-
  Structured PRD writing with field-by-field user confirmation against the
  six-chapter PRD template, brainstorming for requirement and solution design
  clarification, Feishu doc output with whiteboard swimlane/sequence diagrams,
  and a required prototype image or HTML file in the interface section. Use when the user asks to write, update, or
  publish a PRD/需求文档/产品方案, especially when requirements must be confirmed
  step-by-step before Feishu writeback.
---

# PRD Write

## Core Rule

Run the workflow in this order:

1. Inventory source materials; mark the single write target.
2. **First brainstorming** — requirement clarification → requirement brief.
3. **Field-by-field confirmation** — walk the six-chapter template one field at a time.
4. **Second brainstorming** — before Chapter 3 (产品实现方案), solution design clarification.
5. **Confirm flows in text, then draw** — business swimlane + product sequence diagrams.
6. **Optional prototype** — imagegen / HTML demo only when the user asks.
7. **Feishu writeback** — create or update the PRD in Feishu.

Do not skip to PRD writing or Feishu output before field confirmation is complete.

**REQUIRED SUB-SKILL:** `brainstorming` (if unavailable: `using-superpowers` or a compact local brainstorm pass).

**Supporting skills:** `lark-doc`, `lark-drive`, `lark-whiteboard`.

---

## Writing Style

Keep the six-chapter structure; write only information that changes product understanding, implementation, testing, or decisions.

- Start sections with business facts, not document meta.
- Omit narration such as "本 PRD 以原型为依据" when the attachment already shows it.
- Use direct product language: "支持…", "点击后…", "校验失败时…".
- When a module is not applicable, write **本需求不涉及** under that section (keep the heading).
- Chapter 6 heading is **六. 验收功能清单**. Section 1 lists one acceptance point per line, in a short phrase such as 「支持…」「点击后…」「展示…」. Do not write schedules, owners, or repeat background, formulas, and exceptions already covered earlier. Section 2 keeps **风险说明** as a risk / impact / response table.

---

## Workflow

### 0. Source Inventory And Target Safety

Before any clarification, list inputs:

| Type | Rule |
| --- | --- |
| Write target | The one Feishu doc/folder the agent may create or modify |
| Read-only references | Feishu docs, drafts, screenshots, demos — do not edit |
| Constraints | Platform, deadline, compliance, permission boundaries |

If the write target is unclear, ask before proceeding.

**Feishu location default:** user specifies a folder/wiki/doc path → create there; otherwise create in the user's **Feishu personal cloud drive** via `lark-drive` + `lark-doc`.

---

### 1. First Brainstorming — Requirement Clarification

Use `brainstorming` to clarify unknowns with MECE domains:

- Business goal and success metrics
- Users, roles, permissions
- Scope and non-goals
- Main path and exception paths
- Platform (App / PC / mini-program / backend / mixed)
- Data, compliance, and operational risks

Output a **requirement brief** (≤1 page):

- One-sentence product intent
- Goals, users, scope, non-goals
- Main and exception paths
- Assumptions and open questions

Fields already settled in the brief are **pre-filled** during field confirmation — confirm or edit, do not re-ask.

---

### 2. Field-By-Field Confirmation (Default Main Flow)

Read `references/field-confirmation-checklist.md` and `references/prd-template.md`.

Rules:

- **One field per turn.** Wait for the user's answer before the next field.
- `*` fields are **required**; others may be skipped with 「跳过」 or 「不涉及」.
- Skipped / not-applicable → final PRD writes **本需求不涉及** (keep section heading).
- Track progress; show a compact checklist of confirmed / open / skipped fields.

Chapter order: 标题 → 一 → 二 → **(brainstorm gate)** → 三 → 四 → 五 → 六.

---

### 3. Second Brainstorming — Solution Design (Chapter 3 Gate)

**Before** entering Chapter 3 field confirmation, run `brainstorming` again for solution design:

- Role × scenario matrix
- Process branches and approval nodes
- Page/state inventory
- Exception and edge cases
- Data metric definitions

Output a **solution brief**, then continue field-by-field confirmation for Chapter 3.

---

### 4. Flow Diagrams — Text First, Then Whiteboard

For **3.2 业务流程图** and **3.3 产品流程图**:

1. Present the flow in text (roles, steps, branches, exceptions, start/end, 新增/修改 marks).
2. Wait for explicit user confirmation.
3. Only then create the diagram with `lark-whiteboard`:
   - 3.2 → **swimlane SVG** whiteboard
   - 3.3 → **role sequence / page-flow SVG** whiteboard
4. Insert as a Feishu whiteboard block; preview and verify legibility.

Read `references/feishu-whiteboard-flowcharts.md` before drawing.

**Never draw before text confirmation.**

---

### 5. Analytics Gate (Chapter 4)

Before Chapter 4 fields, ask: **本需求是否涉及埋点？**

- **否** → write **本需求不涉及** under Chapter 4; skip埋点 fields.
- **是** → confirm 4.1–4.3 and fill the analytics table per `references/prd-template.md`.

---

### 6. Prototype Asset (Required)

Chapter 3.4（1）原型图与功能布局 must contain a visible image or an HTML file inside the Feishu doc. A text description alone is not a prototype. Do not publish, and do not treat the PRD as complete, when this section has neither.

Insert the asset directly under that heading. Leaving it only on disk, or only at the end of the document, does not count.

Use one of these:

- **Image**: screenshot of the current page, or a design image of the changed screen. Do not invent unapproved logic.
- **HTML**: one self-contained file attached in that section. Mixed PC + App: two separate files. Read `references/page-description-layout.md` for layout.

Either an image or an HTML file satisfies the rule. Text can sit beside the asset; it cannot replace it.

---

### 7. PRD Composition

After all fields are confirmed, assemble the PRD using `references/prd-template.md`.

Self-check before publish:

- All `*` fields filled; skipped modules say 本需求不涉及
- Text flows match whiteboard diagrams
- Requirement brief, solution brief, and PRD body are consistent
- No accidental edits to read-only references

---

### 8. Feishu Writeback

When the target is Feishu:

- Use `lark-doc` to create or update the document.
- Use `lark-drive` to resolve folder path or personal cloud drive location.
- Insert whiteboard blocks for 3.2 and 3.3 diagrams.
- Insert the prototype image or HTML file under 3.4（1）原型图与功能布局. A doc with only prototype text is incomplete.
- Confirm before high-impact overwrite of existing PRD content.

If CLI credentials are unavailable, prepare a self-contained script and tell the user exactly what it will modify.

---

## Output Quality Checklist

Before finalizing:

- [ ] Requirement brief and field confirmation complete
- [ ] Second brainstorming done before Chapter 3
- [ ] Business and product flows confirmed in text before whiteboard insertion
- [ ] Analytics gate handled (涉及埋点 → table; 否 → 本需求不涉及)
- [ ] Six-chapter template structure preserved
- [ ] Chapter 6 is 验收功能清单: short function points, plus 风险说明
- [ ] Chapter 3.4（1）原型图与功能布局 contains an image or an HTML file in the Feishu doc. Text-only prototype sections fail this check.
- [ ] PRD created in specified Feishu location or personal cloud drive
- [ ] Only the write target was modified
- [ ] No unnecessary meta prose

## Reference Files

| File | When to read |
| --- | --- |
| `references/prd-template.md` | Assembling final PRD body |
| `references/field-confirmation-checklist.md` | During field-by-field loop |
| `references/feishu-whiteboard-flowcharts.md` | Before creating flow diagrams |
| `references/page-description-layout.md` | Optional prototype screenshot layout |
