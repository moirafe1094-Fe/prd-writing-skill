# Regression Scenario: Field-By-Field Confirmation

## Input

User asks to write a PRD for a medium inventory-management feature. Some context is provided (business background, two roles, one main flow).

## Failure Patterns

- Agent writes the full PRD without walking fields one at a time.
- Agent skips the first brainstorming and asks template questions cold.
- Agent enters Chapter 3 without a second brainstorming pass.
- Agent draws business/product flowcharts before presenting and confirming text flows.
- Agent fills Chapter 4 analytics without asking whether tracking is involved.
- Agent deletes skipped sections instead of writing **本需求不涉及**.

## Required Result

- First brainstorming produces a requirement brief; brief-covered fields are pre-filled for confirmation only.
- Agent asks one field at a time following `field-confirmation-checklist.md`.
- Second brainstorming runs before Chapter 3 field confirmation.
- Text flow is presented and confirmed before any whiteboard diagram.
- Analytics gate question is asked; if user says no, Chapter 4 contains **本需求不涉及**.
- Final output uses the six-chapter template and is written to Feishu (specified location or personal cloud drive).
