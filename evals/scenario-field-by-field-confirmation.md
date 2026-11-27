# Regression Scenario: Field-By-Field Confirmation

## Input

User asks to write a PRD for a medium inventory-management feature. Some context is provided (business background, two roles, one main flow).

## Failure Patterns

- Agent writes the full PRD without walking fields one at a time.
- Agent skips the first brainstorming and asks template questions cold.
- Agent enters Chapter 四 without a second brainstorming pass.
- Agent draws business/product flowcharts before presenting and confirming text flows.
- Agent uses a role sequence diagram for an App product instead of a flowchart + page-flow map.
- Agent fills Chapter 五 analytics without asking whether tracking is involved.
- Agent deletes skipped sections instead of writing **本需求不涉及**.
- Agent asks the user for Chapter 一 content that is already confirmed in later chapters, or writes Chapter 一 first.
- Agent leaves blanks in the 1.1 conclusion sentence, or invents a baseline number.
- Agent writes 需求成本 in RMB instead of hours per role.
- Agent writes 验收清单 as a bullet list, fills 验收结果, or adds a separate 风险说明 table.
- Agent adds sections that are not in the template: 1.3 MRD, 基础信息, 功能清单, 交互设计描述.

## Required Result

- First brainstorming produces a requirement brief; brief-covered fields are pre-filled for confirmation only.
- Agent asks one field at a time following `field-confirmation-checklist.md`, in the order 标题 → 二 → 三 → 四 → 五 → 六 → 七 → 一.
- Second brainstorming runs before Chapter 四 field confirmation and decides the product type.
- Text flow is presented and confirmed before any whiteboard diagram.
- Analytics gate question is asked; if user says no, Chapter 五 contains **本需求不涉及**.
- Chapter 一 is drafted from confirmed fields, shown once for confirmation; only 待拍板事项, 需求单链接, and uncovered 影响面 / 关键风险 are asked.
- Chapter 七 is the 序号 / 验收项 / 预期结果 / 验收结果 / 验收人 table with 验收结果 blank.
- Final output uses the seven-chapter template with `一、` / `1、` numbering and is written to Feishu (specified location or personal cloud drive).
