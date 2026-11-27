# PRD Writing Skill

`prd-write` is a Codex/OpenSkills/Cursor skill for writing structured PRDs with **field-by-field user confirmation** against a seven-chapter template, then publishing to Feishu.

## Workflow

1. **Inventory sources** — mark the single Feishu write target; everything else is read-only.
2. **First brainstorming** — clarify requirements (MECE), output a requirement brief.
3. **Field-by-field confirmation** — walk chapters 二 to 七 one field at a time; required fields must be answered; skipped modules write **本需求不涉及**.
4. **Second brainstorming** — before Chapter 四 (产品实现方案), clarify solution design (product type, roles, flows, pages, exceptions, metrics).
5. **Confirm flows in text, then draw** — business swimlane diagram (4.1) and a product flow diagram chosen by product type (4.2) via Feishu whiteboard SVG; never draw before user confirms the text flow.
6. **Analytics gate** — ask whether the requirement involves tracking; if not, Chapter 五 writes **本需求不涉及**.
7. **Required prototype** — under 4.3（1）原型HTML, embed HTML prototypes as HTML component blocks (no attachment cards, no screenshots of that HTML); use images only when no HTML exists. Page descriptions follow each block. Text alone is not enough. Do not publish without it.
8. **Key-information summary** — generate Chapter 一 (一句话结论 + 关键结论速览) from the confirmed chapters, then confirm it.
9. **Feishu writeback** — create PRD in the user-specified location, or personal cloud drive by default.

## Seven-Chapter Template

| Chapter | Key sections |
| --- | --- |
| 一、重点信息概述 | 一句话结论*, 关键结论速览*（最后生成） |
| 二、产品模块概述 | 迭代简述（新模块非必填）, 模块规划 |
| 三、需求与背景分析 | 背景*, 目标*, 用户*, 价值*, 成本*（按角色工时）, 竞品 |
| 四、产品实现方案 | 业务流程图*, 产品流程图*（按产品类型选图示）, 界面设计及功能说明*（原型：有 HTML 用组件块，没有才用图片）, 数据指标* |
| 五、数据埋点 | 门控：是否涉及埋点；复盘/监测指标, 分析拆解, 埋点需求（采集规则） |
| 六、运营落地计划 | 运营方案*, 节奏*, 反馈*, 数据调整 |
| 七、验收清单 | 验收清单表*（序号、验收项、预期结果、验收结果、验收人） |

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
