# PRD Writing Skill

`prd-write` is a Codex/OpenSkills/Cursor skill for writing structured PRDs with **field-by-field user confirmation** against a six-chapter template, then publishing to Feishu.

## Workflow

1. **Inventory sources** — mark the single Feishu write target; everything else is read-only.
2. **First brainstorming** — clarify requirements (MECE), output a requirement brief.
3. **Field-by-field confirmation** — walk the six-chapter template one field at a time; required fields must be answered; skipped modules write **本需求不涉及**.
4. **Second brainstorming** — before Chapter 3 (产品实现方案), clarify solution design (roles, flows, pages, exceptions, metrics).
5. **Confirm flows in text, then draw** — business swimlane diagram (3.2) and product sequence diagram (3.3) via Feishu whiteboard SVG; never draw before user confirms the text flow.
6. **Analytics gate** — ask whether the requirement involves tracking; if not, Chapter 4 writes **本需求不涉及**.
7. **Optional prototype** — imagegen / HTML demo only when explicitly requested.
8. **Feishu writeback** — create PRD in the user-specified location, or personal cloud drive by default.

## Six-Chapter Template

| Chapter | Key sections |
| --- | --- |
| 一、产品模块概述 | 迭代简述, 模块规划, MRD |
| 二、需求与背景分析 | 背景*, 目标*, 用户*, 价值*, 成本*, 竞品 |
| 三、产品实现方案 | 基础信息*, 业务流程图*, 产品流程图*, 界面功能*, 数据指标* |
| 四、数据埋点 | 门控：是否涉及埋点；指标, 拆解, 埋点表 |
| 五、运营落地计划 | 运营方案*, 节奏*, 反馈*, 数据调整 |
| 六、项目计划 | 排期, 风险 |

See `references/prd-template.md` for the full template and `references/field-confirmation-checklist.md` for the confirmation script.

## Installation

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/moirafe1094-Fe/prd-writing-skill.git ~/.agents/skills/prd-write
```

For Cursor:

```bash
mkdir -p ~/.cursor/skills
git clone https://github.com/moirafe1094-Fe/prd-writing-skill.git ~/.cursor/skills/prd-write
```

Verify:

```bash
npx openskills read prd-write
```

## Companion Skills

- **brainstorming** — required for requirement and solution design clarification
- **lark-doc** / **lark-drive** / **lark-whiteboard** — Feishu document and diagram output

## Repository Contents

```text
SKILL.md
references/prd-template.md
references/field-confirmation-checklist.md
references/feishu-whiteboard-flowcharts.md
references/page-description-layout.md
evals/
agents/openai.yaml
```

## License

MIT
