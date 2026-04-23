# 天工（TianGong）框架使用手册

> **天工（TianGong）** —— 让 AI 在已有系统上做定制化开发，从"小心翼翼"升级为"游刃有余"

---

## 一、快速开始

### 1.1 这套框架是什么

TianGong 是一套面向**已有系统定制化开发（客开/二开）**的 AI 驱动方法论。它告诉你和 AI 应该按什么步骤、什么规则来完成一个客开项目。

**适用场景**：
- 在现有系统上添加新功能
- 修改现有系统的业务逻辑
- 对现有系统进行架构调整或技术升级
- 修复现有系统的复杂 Bug
- 对外购系统进行定制化改造

**不适用场景**：
- 从零开始搭建新系统（请使用 Paoding 原版）
- 纯文档编写或知识问答
- 与代码变更无关的任务

### 1.2 五分钟上手

#### Step 1: 准备工作区

在你的项目旁边创建工作区，按 `workspace-convention.md` 规范组织目录：

```bash
mkdir -p project-workspace/{00-framework,01-docs,02-src,03-bak,04-delivery,05-knowledge,06-logs}
```

#### Step 2: 放置框架文件

将 `00-framework/` 目录下的所有 Markdown 文件放入工作区。

#### Step 3: 加载核心约束

将 `core/SKILL.md` 的内容提供给 AI（复制粘贴或通过工具加载），让 AI 理解并遵循铁律和优先级体系。

**关键提示**：只需加载 `core/SKILL.md`，AI 会根据 1% 触发原则自动加载其他需要的文件。

#### Step 4: 开始 Phase 0

告诉 AI："请执行 Phase 0 系统画像"，AI 会按照 `phase-0-system-profiling/SKILL.md` 的流程开始工作。

### 1.3 框架文件清单

```
00-framework/
├── core/                                    # 【必加载】核心约束
│   ├── SKILL.md                             #   核心技能入口（最先加载）
│   ├── iron-laws.md                         #   6 条铁律
│   ├── anti-patterns.md                     #   17 条反模式
│   ├── workflow-overview.md                 #   全流程总览
│   └── workspace-convention.md              #   工作目录规范
│
├── phase-0-system-profiling/                # Phase 0 模板
│   ├── SKILL.md                             #   阶段流程定义
│   ├── system-profile-template.md           #   系统画像模板
│   ├── ai-capability-profile-template.md    #   AI 能力画像模板
│   └── feasibility-assessment-template.md   #   可行性评估模板
│
├── phase-1-change-analysis/                 # Phase 1 模板
│   ├── SKILL.md
│   ├── change-request-template.md
│   ├── impact-analysis-template.md
│   └── change-alignment-checklist.md
│
├── phase-2-architecture-understanding/       # Phase 2 模板
│   ├── SKILL.md
│   ├── architecture-understanding-template.md
│   ├── change-plan-template.md
│   └── design-review-checklist.md
│
├── phase-3-change-implementation/            # Phase 3 模板
│   ├── SKILL.md
│   ├── regression-testing-guide.md
│   ├── code-review-guide.md
│   └── systematic-debugging-guide.md
│
├── phase-4-knowledge-consolidation/          # Phase 4 模板
│   ├── SKILL.md
│   ├── ai-error-notebook-template.md
│   ├── retrospective-template.md
│   └── system-knowledge-template.md
│
├── phase-5-change-delivery/                  # Phase 5 模板
│   ├── SKILL.md
│   ├── delivery-checklist.md
│   └── change-deliverables-template.md
│
├── module-7-knowledge-distillation/          # Module 7 模板
│   ├── SKILL.md
│   ├── project-brain-template.md
│   ├── distillation-process-guide.md
│   └── memory-capture-guide.md
│
└── module-8-constraint-analytics/            # Module 8 模板
    ├── SKILL.md
    ├── constraint-trace-template.md
    ├── iteration-snapshot-template.md
    ├── aggregate-analysis-template.md
    └── optimization-loop-guide.md
```

---

## 二、完整使用流程

### 2.1 流程总览

```
Phase 0 → Phase 1 → Phase 2 → Phase 3 → Phase 4 → Phase 5
系统画像   变更分析   架构理解   变更实施   知识沉淀   变更交付
  │          │          │          │          │          │
  ▼          ▼          ▼          ▼          ▼          ▼
 Gate 0    Gate 1    Gate 2    Gate 3    Gate 4    Gate 5
 硬性      硬性      硬性      硬性      软性      硬性
```

### 2.2 Phase 0: 系统画像（预计 2-4 小时）

**目标**：理解现有系统，评估客开可行性

**你（使用者）需要做的**：
1. 提供目标系统的代码访问权限
2. 提供现有的系统文档（如果有）
3. 回答 AI 关于系统的问题
4. 确认系统画像的准确性

**AI 会自动做的**：
1. 分析技术栈和架构
2. 梳理模块关系和依赖
3. 评估代码质量
4. 生成系统画像文档
5. 评估 AI 自身的能力匹配度
6. 识别利益相关者角色

**产出物**：
- `01-docs/phase-0/system-profile.md` — 系统画像
- `01-docs/phase-0/ai-capability-profile.md` — AI 能力画像
- `01-docs/phase-0/feasibility-report.md` — 可行性报告

**Gate 0 通过条件**：系统画像完整 + 可行性等级非"不建议" + 使用者已确认

### 2.3 Phase 1: 变更需求分析（预计 2-6 小时）

**目标**：明确要改什么、影响什么、风险在哪

**你（使用者）需要做的**：
1. 告诉 AI 你要改什么、加什么、去什么
2. 确认 AI 的影响分析是否准确
3. 对争议点做出决策
4. 确认变更范围和优先级

**AI 会自动做的**：
1. 收集和分类变更需求
2. 分析每个变更的影响范围（模块/接口/数据/用户）
3. 评估现有资源的复用情况（可复用/需适配/不可复用/需新增）
4. 识别争议点（新需求与现有架构的冲突）
5. 追踪级联影响链（改了A会影响B，B会影响C...）
6. 生成角色化报告（技术版/业务版/简要版）

**产出物**：
- `01-docs/phase-1/change-specification.md` — 变更规格文档
- `01-docs/phase-1/impact-analysis.md` — 影响分析报告（含复用评估、争议点、级联链）
- `01-docs/phase-1/alignment-record.md` — 对齐确认记录

**Gate 1 通过条件**：所有变更都有影响分析 + 争议点已决策 + 使用者已确认

### 2.4 Phase 2: 架构理解与变更方案（预计 4-8 小时）

**目标**：深入理解现有架构，设计变更方案

**你（使用者）需要做的**：
1. 提供架构相关的补充信息
2. 对争议点的备选方案做出选择
3. 确认变更方案

**AI 会自动做的**：
1. 深入分析现有架构（代码阅读、设计模式识别、隐式依赖发现）
2. 为每个变更设计技术方案
3. 评估兼容性（架构/接口/数据/行为）
4. 为争议点提供备选方案
5. 量化级联影响（具体到模块/接口/工作量）
6. 生成角色化方案报告
7. 组织多轮专家验证（架构/数据/安全/业务专家 + QA 门控）
8. 生成可执行任务清单

**产出物**：
- `01-docs/phase-2/architecture-understanding.md` — 架构理解文档
- `01-docs/phase-2/change-plan.md` — 变更方案与实施计划
- `01-docs/phase-2/reviews/` — 多轮评审记录
- `01-docs/phase-2/reports/` — 角色化方案报告（三个版本）

**Gate 2 通过条件**：方案通过多轮专家验证 + QA 门控 APPROVED + 使用者已确认

### 2.5 Phase 3: 变更实施（预计 varies）

**目标**：先保护再修改，安全地实施变更

**你（使用者）需要做的**：
1. 在关键节点进行人工验收
2. 对审查发现的问题确认修复方案

**AI 会自动做的**：
1. 编写回归测试（保护已有功能）
2. 编写变更测试（定义新功能行为）
3. 实施变更（最小化代码改动）
4. 运行回归验证（确保无破坏）
5. 执行两阶段代码审查
6. 修复审查问题
7. 生成完成报告

**产出物**：
- `02-src/working/` — 变更后的代码
- `02-src/tests/` — 测试代码
- `01-docs/phase-3/` — 审查记录和测试报告

**Gate 3 通过条件**：全量测试通过 + 审查问题已解决 + 有新鲜验证证据

### 2.6 Phase 4: 知识沉淀（预计 1-2 小时）

**目标**：沉淀经验和系统理解

**AI 会自动做的**：
1. 变更回顾（做了什么、遇到了什么问题）
2. 更新系统理解（新发现的隐式依赖、地雷区）
3. 更新 AI 错题本
4. 更新 project-brain.md

**产出物**：
- `01-docs/phase-4/retrospective.md` — 变更回顾
- `01-docs/phase-4/ai-error-notebook.md` — AI 错题本
- `05-knowledge/project-brain.md` — 项目大脑

### 2.7 Phase 5: 变更交付（预计 1-2 小时）

**目标**：确保交付质量，打包交付物

**你（使用者）需要做的**：
1. 验收功能
2. 确认交付

**AI 会自动做的**：
1. 变更完整性检查
2. 全量回归测试
3. 追溯验证
4. 交付打包

**产出物**：
- `04-delivery/v{版本号}/` — 完整交付包

---

## 三、核心概念速查

### 3.1 六条铁律（必须遵守）

| 编号 | 铁律 | 一句话 |
|------|------|--------|
| IL-1 | 变更需求不清晰不得进入开发 | 需求必须可理解、可验证、可追溯 |
| IL-2 | 没有回归测试保护就没有变更代码 | 先写测试保护已有功能，再改代码 |
| IL-3 | 每个变更必须经过审查 | 自审 + 交叉审查 + 铁律合规检查 |
| IL-4 | 完成声明必须有新鲜验证证据 | 必须是本次会话生成的测试结果 |
| IL-5 | 每个阶段必须有文档输出 | 文档是思考过程的沉淀 |
| IL-6 | 每段变更代码必须可追溯到变更需求 | 代码 → 变更ID → 影响分析 |

### 3.2 四种复用判定

| 符号 | 含义 | 说明 |
|------|------|------|
| ✅ | 可直接复用 | 现有模块完全满足需求 |
| ⚠️ | 需适配后复用 | 基本可用，但需要调整 |
| ❌ | 不可复用 | 需要重写或替换 |
| 🆕 | 需新增 | 系统中不存在 |

### 3.3 三种角色化报告

| 报告版本 | 适用角色 | 内容 |
|----------|----------|------|
| 完整技术版 | 技术人员 | 全部技术细节 |
| 业务摘要版 | 产品经理、决策者 | 功能影响 + 风险点 + 工期 |
| 简要说明版 | 使用者 | 变更内容 + 操作变化 |

### 3.4 门控类型

| 类型 | 含义 | 处理方式 |
|------|------|----------|
| 硬性门控 | 不可绕过 | 不通过必须回退修复 |
| 软性门控 | 建议完成 | 允许在后续阶段补充 |

---

## 四、常见问题

### Q1: 框架太重了，能不能跳过一些阶段？

**A:** Phase 0 和 Phase 1 是基础，不建议跳过。但如果是对同一个系统做多次小变更，Phase 0 只需在首次执行，后续变更可以从 Phase 1 开始。

### Q2: 我不懂技术，能用这套框架吗？

**A:** 可以。框架会生成"业务摘要版"报告，只包含功能影响和风险点，不包含技术细节。你只需要关注业务层面的确认和决策。

### Q3: AI 能力不够怎么办？

**A:** Phase 0 的 AI 能力画像会评估 AI 的能力匹配度。如果某些任务超出 AI 能力，会标注需要人工介入的点。

### Q4: 框架支持哪些 AI 平台？

**A:** 框架是纯 Markdown 文件，理论上支持所有能读取 Markdown 的 AI 平台（Claude、GPT、DeepSeek、豆包等）。但不同 AI 的能力差异会影响执行效果。

### Q5: 多次客开怎么用？

**A:** 第一次完整执行 Phase 0-5。后续变更从 Phase 1 开始，但每次都要更新 Module 7 的知识蒸馏和 Phase 0 的系统画像。

---

## 五、文件打包与发布

### 5.1 框架发布包结构

将整个 `TianGong/` 目录打包发布：

```
TianGong-v1.0/
├── README.md                    # 项目总览
├── framework-guide.md           # 本使用手册
├── self-assessment.md           # 自我评估报告
├── core/                        # 核心约束
├── phase-0-system-profiling/    # Phase 0
├── phase-1-change-analysis/     # Phase 1
├── phase-2-architecture-understanding/  # Phase 2
├── phase-3-change-implementation/       # Phase 3
├── phase-4-knowledge-consolidation/     # Phase 4
├── phase-5-change-delivery/             # Phase 5
├── module-7-knowledge-distillation/     # Module 7
└── module-8-constraint-analytics/       # Module 8
```

### 5.2 版本管理

- **MAJOR**（主版本）：阶段流程重大变更
- **MINOR**（次版本）：新增模板或机制
- **PATCH**（补丁版本）：模板内容修正和优化

### 5.3 许可证

MIT License — 可自由使用、修改、分发。
