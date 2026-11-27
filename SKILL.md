---
name: prd-write
description: >-
  Structured PRD writing with field-by-field user confirmation against the
  seven-chapter PRD template, brainstorming for requirement and solution design
  clarification, Feishu doc output with whiteboard flow diagrams, a required
  prototype in the interface section (HTML component block by default;
  screenshot only when no HTML exists), and a key-information summary chapter
  generated last. Use when the user asks to write, update, or publish a
  PRD/需求文档/产品方案, especially when requirements must be confirmed
  step-by-step before Feishu writeback.
---

# PRD Write

## Core Rule

Run the workflow in this order:

1. Inventory source materials; mark the single write target.
2. **First brainstorming** — requirement clarification → requirement brief.
3. **Field-by-field confirmation** — walk chapters 二 to 七 one field at a time.
4. **Second brainstorming** — before Chapter 四 (产品实现方案), solution design clarification.
5. **Confirm flows in text, then draw** — business swimlane + product flow diagram chosen by product type.
6. **Prototype** — required in 4.3（1）原型HTML; build an imagegen / HTML demo only when the user asks.
7. **Key-information summary** — generate Chapter 一 (重点信息概述) from the confirmed fields, then confirm it.
8. **Feishu writeback** — create or update the PRD in Feishu.

Do not skip to PRD writing or Feishu output before field confirmation is complete.

**REQUIRED SUB-SKILL:** `brainstorming` (if unavailable: `using-superpowers` or a compact local brainstorm pass).

**Supporting skills:** `lark-doc`, `lark-drive`, `lark-whiteboard`.

---

## Writing Style

Keep the seven-chapter structure; write only information that changes product understanding, implementation, testing, or decisions.

- Start sections with business facts, not document meta.
- Omit narration such as "本 PRD 以原型为依据" when the prototype already shows it.
- Use direct product language: "支持…", "点击后…", "校验失败时…".
- When a module is not applicable, write **本需求不涉及** under that section (keep the heading).
- Heading numbering follows the Feishu template: `一、` for chapters, `1、` for sections, `1.1` only in Chapter 一.
- Chapter 一 is a summary for reviewers: one filled-in conclusion sentence plus the 关键结论速览 table, one sentence per row. It must not contradict or add scope beyond the later chapters.
- Chapter 七 heading is **七、验收清单**, written as the 序号 / 验收项 / 预期结果 / 验收结果 / 验收人 table. 验收项 is a short phrase such as 「支持…」「点击后…」「展示…」. Leave 验收结果 blank. Do not write schedules, or repeat background, formulas, and exceptions already covered earlier.

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

Chapter order: 标题 → 二 → 三 → **(brainstorm gate)** → 四 → 五 → 六 → 七 → 一.

---

### 3. Second Brainstorming — Solution Design (Chapter 四 Gate)

**Before** entering Chapter 四 field confirmation, run `brainstorming` again for solution design:

- Product type (App / 中台 / general), which decides the 4.2 diagram
- Role × scenario matrix
- Process branches and approval nodes
- Page/state inventory, page hierarchy and page relations
- Exception and edge cases
- Data metric definitions

Output a **solution brief**, then continue field-by-field confirmation for Chapter 四.

---

### 4. Flow Diagrams — Text First, Then Whiteboard

For **4.1 业务流程图** and **4.2 产品流程图**:

1. Present the flow in text (roles, systems, steps, branches, exceptions, start/end, 新增/修改 marks).
2. Wait for explicit user confirmation.
3. Only then create the diagram with `lark-whiteboard`:
   - 4.1 → **swimlane SVG** whiteboard
   - 4.2 → by product type: general → overall abstract model; App → flowchart + page-flow map; 中台 → system layer diagram + role sequence diagram
4. Insert as a Feishu whiteboard block; preview and verify legibility.

Read `references/feishu-whiteboard-flowcharts.md` before drawing.

**Never draw before text confirmation.**

---

### 5. Analytics Gate (Chapter 五)

Before Chapter 五 fields, ask: **本需求是否涉及埋点？**

- **否** → write **本需求不涉及** under Chapter 五; skip埋点 fields.
- **是** → confirm 5.1–5.3 and fill the analytics table per `references/prd-template.md`.

---

### 6. Prototype Asset (Required)

Chapter 4.3（1）原型HTML must contain a visible prototype inside the Feishu doc. A text description alone is not a prototype. Do not publish, and do not treat the PRD as complete, when this section has none.

Insert the prototype directly in that section. Leaving it only on disk, or only at the end of the document, does not count.

- **HTML exists → HTML component block (default).** Insert each self-contained HTML as `<html5-block path="@./x.html"/>`, not as a file attachment card. Do not add screenshots of that HTML anywhere in the PRD.
- **No HTML → image.** Screenshot of the current page, or a design image of the changed screen. Do not invent unapproved logic.

Order inside the section: for each prototype group, a bold title line → the component block → the page descriptions for that prototype (page heading, 页面目标, module table / list). Descriptions always come after the block, never before it or beside it.

Mixed PC + App: separate HTML files, each its own component block group; PC groups first, then App.

Read `references/page-description-layout.md` for the XML structure and the embedding rules (required meta tags, fit-to-width scaling, size limit, verification). For scaling, never zoom or transform `html` / `body`: Feishu measures the unscaled height, which leaves blank space under the block. Scale an inner wrapper, and set the outer wrapper's height to the scaled height.

---

### 7. Key-Information Summary (Chapter 一)

After chapters 二 to 七 are confirmed, draft Chapter 一 from them:

- **1.1 一句话结论**: fill every blank of 「为 ______ 解决 ______ 的问题，本期通过 ______ 实现 ______，上线后 ______ 从 ______ 提升至 ______。」 from 3.1 背景, 3.2 目标, 3.3 用户, and the solution. Without a baseline number, state the measurable target; do not invent one.
- **1.2 关键结论速览**: 业务痛点 ← 3.1; 本次目标 ← 3.2; 本期范围（做）/ 本期不做 ← confirmed Chapter 四 (brief non-goals only where Chapter 四 is silent); 价值 ← 3.4; 影响面 ← 3.3 + Chapter 四 + 6.4; 关键风险 ← brief + exceptions.
- Show the whole draft once for confirmation. Ask separately only for fields that cannot be derived: 待拍板事项 (write **无** when none), 需求单链接, and 影响面 / 关键风险 when earlier chapters do not cover them.

---

### 8. PRD Composition

After all fields are confirmed, assemble the PRD using `references/prd-template.md`.

Self-check before publish:

- All `*` fields filled; skipped modules say 本需求不涉及
- Text flows match whiteboard diagrams
- Requirement brief, solution brief, Chapter 一, and PRD body are consistent
- No accidental edits to read-only references

---

### 9. Feishu Writeback

When the target is Feishu:

- Use `lark-doc` to create or update the document.
- Use `lark-drive` to resolve folder path or personal cloud drive location.
- Insert whiteboard blocks for 4.1 and 4.2 diagrams.
- Insert the prototype under 4.3（1）原型HTML: HTML component blocks when HTML exists, images only when it does not. A doc with only prototype text is incomplete.
- After writing, fetch the doc and confirm the `html5-block` count matches the number of HTML files, and that no screenshot of an embedded HTML remains.
- Confirm before high-impact overwrite of existing PRD content.

If CLI credentials are unavailable, prepare a self-contained script and tell the user exactly what it will modify.

---

## Output Quality Checklist

Before finalizing:

- [ ] Requirement brief and field confirmation complete
- [ ] Second brainstorming done before Chapter 四
- [ ] Business and product flows confirmed in text before whiteboard insertion; 4.2 diagram matches the product type
- [ ] Analytics gate handled (涉及埋点 → table; 否 → 本需求不涉及)
- [ ] Seven-chapter template structure and `一、` / `1、` numbering preserved
- [ ] Chapter 一 has a fully filled conclusion sentence and all ten 关键结论速览 rows, consistent with later chapters
- [ ] 3.5 需求成本 is in hours per role, plus cash only for AI / external API
- [ ] Chapter 七 is the 验收清单 table: short 验收项, observable 预期结果, blank 验收结果
- [ ] Chapter 4.3（1）原型HTML contains the prototype in the Feishu doc: HTML component blocks when HTML exists (no attachment cards, no screenshots of that HTML), images only when no HTML exists. Text-only prototype sections fail this check.
- [ ] Each prototype group is ordered title → component block → page descriptions.
- [ ] Embedded HTML scales an inner wrapper, not `html` / `body`. The simulated auto-height check shows no blank strip under any block.
- [ ] PRD created in specified Feishu location or personal cloud drive
- [ ] Only the write target was modified
- [ ] No unnecessary meta prose

## Reference Files

| File | When to read |
| --- | --- |
| `references/prd-template.md` | Assembling final PRD body |
| `references/field-confirmation-checklist.md` | During field-by-field loop |
| `references/feishu-whiteboard-flowcharts.md` | Before creating flow diagrams |
| `references/page-description-layout.md` | Before inserting prototypes: HTML component block layout and embedding, screenshot fallback |
