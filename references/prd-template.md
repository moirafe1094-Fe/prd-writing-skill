# 标准 PRD 模板（七章结构）

Use this structure when writing the final PRD body. Fields marked `*` are required.

Heading numbering follows the Feishu template: chapters use `一、`, sections use `1、`. Chapter 一 alone uses `1.1` / `1.2`. Example: `二、产品模块概述`, `1、需求背景`.

Heading levels: every chapter, including 一、重点信息概述, is a level-1 heading; every section, including 1.1 / 1.2, is a level-2 heading. The Feishu template shows Chapter 一 as level 2; do not copy that, or the doc outline puts Chapter 一 at the same level as its own sections.

## 标题

`xx域-xx模块-需求名称-版本号`

Example: `商品管理域-SKU管理模块-SKU标签优化-20260401`

---

## 一、重点信息概述

Write this chapter last, from the confirmed fields in chapters 二 to 七. Do not ask for content that is already confirmed elsewhere.

Whenever chapters 三, 四, or 六 change after the first draft, regenerate this chapter from the updated content and confirm it with the user before writeback.

### *1.1 一句话结论

为 ______ 解决 ______ 的问题，本期通过 ______ 实现 ______，上线后 ______ 从 ______ 提升至 ______。

Fill every blank. If the goal has no baseline number, state the measurable target instead of inventing one.

### *1.2 关键结论速览

| 维度 | 结论（一句话） |
| --- | --- |
| 业务痛点 | 现状是什么、痛点在哪、量化损失 |
| 本次目标 | 本期要达成的可衡量结果 |
| 本期范围（做） | 明确交付的功能边界 |
| 本期不做 | 明确排除项/边界及原因 |
| 价值 | 做完能带来什么，解决什么问题 |
| 影响面 | 涉及系统、角色、存量数据、其他模块 |
| 关键风险 | 主要风险及应对结论 |
| 待拍板事项 | 本次评审必须给结论的问题 |
| 需求单链接 | |

One sentence per row. Keep the row and write **无** when 待拍板事项 has no open item.

待拍板事项 is the review agenda. After the review, replace each item with its outcome, e.g. `已定：……` or `待定：……（负责人、截止时间）`, and update the affected chapters to match.

---

## 二、产品模块概述

### 1、产品模块迭代简述（新模块非必填）

- 上次模块迭代内容、版本（版本记录）
- 上次模块迭代 PRD 链接

**版本记录表**

| 版本号 | 核心修改内容 | 修订人 | 修订时间 | PRD链接 |
| --- | --- | --- | --- | --- |
| 1.0 | | | | |

New module: write **本需求不涉及** under the heading.

### 2、产品模块规划

最新产品模块规划链接或大图

---

## 三、需求与背景分析

### *1、需求背景

实际业务场景、用户痛点或需求

### *2、需求目标（包含关键指标）

基于背景，在本次产品迭代中，业务希望达到的目的。需要与业务共识清楚，尽可能量化、细化

### *3、目标用户

角色、场景、行为说明、权限说明（含组织、功能权限、数据权限）

### *4、核心价值（量化）

业绩、效率、成本、风险控制、体验、基础能力

### *5、需求成本（预估）

预估投入工时，换算为小时：

| 角色 | 预估工时（小时） |
| --- | --- |
| 产品 | |
| 前端 | |
| 后端 | |
| 设计 | |
| 客户端 | |
| 测试 | |

涉及 AI 项目或外部采购 API 时，另写现金预估。

### 6、竞品分析

大模块、核心模块、0-1 构建，需要有竞品分析。不涉及则写：**本需求不涉及**

---

## 四、产品实现方案

### *1、业务流程图

以业务视角，角色在什么系统做什么操作，业务节点如何流转

- 基于业务流程图标记「新增」「修改」
- 针对调整的部分明确标记并说明
- 最终呈现：飞书画板泳道图（SVG）

### *2、产品流程图

基于不同产品类型，输出不同的图示：

| 产品类型 | 图示 |
| --- | --- |
| 通用（非 App、非中台） | 整体抽象模型 |
| App 产品 | 流程图、页面流转图 |
| 中台产品 | 系统层级图、角色时序图 |

最终呈现：飞书画板（SVG）

### *3、界面设计及功能说明

（1）原型HTML

**硬性要求：** 这一节必须放入原型，只有文字不合格，不得发布。

- 有 HTML 原型：用 HTML 组件块（`html5-block`）嵌入，不用附件卡片，也不再放这份 HTML 的截图。
- 没有 HTML：放现网截图或设计稿。
- 顺序：每组先放加粗标题和组件块，组件块下方再写对应页面的说明（页面标题、页面目标、模块表 / 列表）。

（2）需求功能点逻辑描述

（3）异常场景

（4）案例说明

（5）场景是否涉及 Session 处理机制

（6）场景是否高并发

需要体现页面层级和页面关联性

### *4、数据指标

| 指标名称 | 类型 | 指标定义与口径 | 变更说明 | 所在页面 | 数据来源 |
| --- | --- | --- | --- | --- | --- |
| | 新增 | | - | 如商品库存查询页 | 数仓/xx域xx模块 |
| | 改动 | | 本次如何调整 | | |

---

## 五、数据埋点

**门控**：本需求是否涉及埋点？否 → 本章正文写 **本需求不涉及**，保留章节标题。

### 1、复盘/监测指标

### 2、数据分析的拆解

### *3、数据埋点需求（采集规则）

模板示例（商品手册）：

1. 复盘：手册使用数据情况
2. 拆解：角色点击、角色下载、角色转发
3. 安卓、iOS 分角色记录，页面点击事件

采集规则用下表逐条列出：

| 埋点ID | 事件名（event_name） | 事件名 | 端 | 模块/页面 | 触发时机 | 角色 | 属性清单 | 属性说明 | 状态 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- | --- |
| TRK-REQ-001-001 | order_submit_click | 提交订单按钮点击 | App、PC | 订单确认页 | 用户点击「提交订单」且校验通过后 | 区域经理 | order_id, amount | amount: number，单位元 | 待评审 |

Table rules:

- 埋点ID: globally unique, e.g. `TRK-REQ-001-001`
- 事件名（event_name）: English `snake_case`, globally unique
- 属性清单 / 属性说明: include PV/UV counting and UV deduplication key when needed

---

## 六、运营落地计划

### *1、运营方案

运营角色、执行动作、观测指标；核心运营策略、异常处理方案

### *2、执行节奏

整体产品上线运营计划

### *3、反馈机制

如何收集用户反馈，反馈体量

### 4、数据调整

历史数据是否需要调整，如果调整规则是什么，技术如何操作。不涉及则写：**本需求不涉及**

---

## 七、验收清单

### *1、验收清单表

| 序号 | 验收项 | 预期结果 | 验收结果 | 验收人 |
| --- | --- | --- | --- | --- |
| 1 | | | | |

- 验收项：一条一个可验收的功能点，用「支持…」「点击后…」「展示…」这类短句。
- 预期结果：可观察、可判断通过与否的结果，不复述前面章节的背景、口径和异常。
- 验收结果：写 PRD 时留空，验收时填写。
- 验收人：填角色或姓名；未确定时留空。
- 不写排期。

---

## PRD 质量要求

- 产品经理 PRD 需要图文并茂
- PRD 在飞书管理（创建/更新飞书文档）
