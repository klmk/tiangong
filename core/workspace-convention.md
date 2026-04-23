# 项目工作目录规范（Workspace Convention）

> **定位**：定义客开项目的标准工作目录结构，确保方案文档、源代码、备份、交付物等文件的有序管理。
> **适用阶段**：贯穿整个客开流程（Phase 0 - Phase 5）

---

## 1. 为什么需要工作目录规范

客开项目涉及大量不同类型的文件：方案文档、源代码、测试代码、备份、交付物、知识沉淀等。如果没有统一的目录规范，会导致：

- 文件散落各处，找不到需要的文档
- 备份和正式代码混在一起，容易误操作
- 新 AI 实例接手时无法快速理解项目结构
- 交付时遗漏文件

**本规范的目标：让任何人（包括新的 AI 实例）打开项目目录就能快速理解项目全貌。**

---

## 2. 标准目录结构

```
project-workspace/                    # 项目工作区根目录
│
├── 00-framework/                     # 框架文件（本框架的 Markdown 文件）
│   ├── core/                         # 核心约束
│   ├── phase-0-system-profiling/     # Phase 0 模板
│   ├── phase-1-change-analysis/      # Phase 1 模板
│   ├── phase-2-architecture-understanding/  # Phase 2 模板
│   ├── phase-3-change-implementation/       # Phase 3 模板
│   ├── phase-4-knowledge-consolidation/     # Phase 4 模板
│   ├── phase-5-change-delivery/             # Phase 5 模板
│   ├── module-7-knowledge-distillation/     # Module 7 模板
│   └── module-8-constraint-analytics/       # Module 8 模板
│
├── 01-docs/                          # 📋 方案与文档（所有阶段产出的文档）
│   ├── phase-0/                      # Phase 0 产出
│   │   ├── system-profile.md         #   系统画像文档
│   │   ├── ai-capability-profile.md  #   AI 能力画像
│   │   └── feasibility-report.md     #   客开可行性报告
│   ├── phase-1/                      # Phase 1 产出
│   │   ├── change-specification.md   #   变更规格文档（CRD）
│   │   ├── impact-analysis.md        #   影响分析报告
│   │   └── alignment-record.md       #   变更对齐确认记录
│   ├── phase-2/                      # Phase 2 产出
│   │   ├── architecture-understanding.md  #   架构理解文档
│   │   ├── change-plan.md            #   变更方案与实施计划
│   │   ├── review-record.md          #   方案评审记录
│   │   └── reports/                  #   角色化方案报告
│   │       ├── technical-full.md     #     完整技术版（给技术人员）
│   │       ├── business-summary.md   #     业务摘要版（给产品经理）
│   │       └── user-brief.md         #     简要说明版（给使用者）
│   ├── phase-3/                      # Phase 3 产出
│   │   ├── code-review-records/      #   代码审查记录
│   │   ├── test-reports/             #   测试报告
│   │   └── change-log.md             #   变更日志
│   ├── phase-4/                      # Phase 4 产出
│   │   ├── retrospective.md          #   变更回顾报告
│   │   ├── ai-error-notebook.md      #   AI 错题本
│   │   └── system-knowledge.md       #   系统知识库
│   └── phase-5/                      # Phase 5 产出
│       ├── delivery-checklist.md     #   交付校验清单
│       └── delivery-record.md        #   交付确认记录
│
├── 02-src/                           # 💻 源代码（客开的代码工作区）
│   ├── original/                     #   原始源代码（从目标系统获取的原始版本）
│   │   └── ...                       #     保持与目标系统一致的目录结构
│   ├── working/                      #   工作副本（实际修改的代码）
│   │   └── ...                       #     与 original 结构一致
│   └── tests/                        #   测试代码
│       ├── regression/               #     回归测试（保护已有功能）
│       └── change/                   #     变更测试（验证新功能）
│
├── 03-bak/                           # 🗄️ 备份区（重要节点的代码快照）
│   ├── pre-change/                   #   变更前备份（每个变更开始前的完整快照）
│   │   ├── snapshot-v1.0/            #     快照版本号
│   │   │   └── ...                   #       完整的代码备份
│   │   └── snapshot-v1.1/
│   ├── pre-phase3/                   #   Phase 3 开始前的完整备份
│   └── pre-delivery/                 #   交付前的完整备份
│
├── 04-delivery/                      # 📦 交付区（最终交付物）
│   ├── v1.0/                         #   交付版本号
│   │   ├── src/                      #     变更后的源代码
│   │   ├── tests/                    #     测试代码
│   │   ├── docs/                     #     文档（从 01-docs 复制最终版）
│   │   ├── deploy/                   #     部署文件
│   │   │   ├── deploy-guide.md       #       部署指南
│   │   │   ├── rollback-guide.md     #       回滚指南
│   │   │   └── config-changes/       #       配置变更文件
│   │   └── README.md                 #     交付包说明
│   └── archive/                      #   历史交付版本归档
│       └── v0.x/                     #     旧版本交付包
│
├── 05-knowledge/                     # 🧠 知识资产（持续积累）
│   ├── project-brain.md              #   项目大脑（AI 写给 AI 看）
│   ├── project-context.md            #   项目上下文（快速恢复用）
│   ├── ai-memory/                    #   AI 记忆存储
│   │   ├── decisions/                #     决策记录
│   │   ├── patterns/                 #     模式发现
│   │   ├── errors/                   #     错误记录
│   │   ├── pitfalls/                 #     地雷区标记
│   │   └── index.md                  #     记忆索引
│   └── constraint-analytics/         #   约束有效性分析数据
│       ├── traces/                   #     约束追溯记录
│       └── snapshots/                #     迭代快照
│
└── 06-logs/                          # 📝 过程日志（可追溯）
    ├── session-logs/                 #   会话日志（每次 AI 会话的关键记录）
    │   ├── 2026-04-23-session-01.md  #     按日期编号
    │   └── ...
    └── gate-records/                 #   门控检查记录
        ├── gate-0-pass.md            #     Gate 0 通过记录
        ├── gate-1-pass.md
        └── ...
```

---

## 3. 目录使用规则

### 3.1 文件存放原则

| 原则 | 说明 |
|------|------|
| **原始不动** | `02-src/original/` 中的代码永远不修改，只作为参考和对比基准 |
| **工作分离** | 所有代码修改在 `02-src/working/` 中进行 |
| **先备份后修改** | 每个重要变更前，在 `03-bak/` 中创建快照 |
| **文档集中** | 所有方案文档统一放在 `01-docs/`，按阶段分目录 |
| **知识独立** | 知识资产放在 `05-knowledge/`，与具体交付物分离 |
| **交付打包** | 交付时从各目录提取最终版，打包到 `04-delivery/` |

### 3.2 备份规则

| 备份时机 | 备份位置 | 备份内容 | 命名规则 |
|----------|----------|----------|----------|
| 每个变更开始前 | `03-bak/pre-change/` | `02-src/working/` 的完整快照 | `snapshot-v{版本号}/` |
| Phase 3 开始前 | `03-bak/pre-phase3/` | `02-src/working/` 的完整快照 | `snapshot-phase3-start/` |
| 交付前 | `03-bak/pre-delivery/` | `02-src/working/` 的完整快照 | `snapshot-pre-delivery/` |
| 重大方案变更时 | `03-bak/pre-change/` | `02-src/working/` 的完整快照 | `snapshot-v{版本号}-before-{变更描述}/` |

### 3.3 版本命名规则

| 类型 | 命名规则 | 示例 |
|------|----------|------|
| 备份快照 | `snapshot-v{主版本}.{次版本}/` | `snapshot-v1.0/`、`snapshot-v1.1/` |
| 交付版本 | `v{主版本}.{次版本}/` | `v1.0/`、`v1.1/` |
| 文档版本 | 文件名不变，通过 Git 追踪 | `impact-analysis.md` |
| 会话日志 | `{日期}-session-{序号}.md` | `2026-04-23-session-01.md` |

---

## 4. 关键场景的文件操作流程

### 4.1 变更开始前

```
1. 在 03-bak/pre-change/ 创建当前代码快照
2. 确认 01-docs/phase-1/ 中的变更规格文档已定稿
3. 确认 01-docs/phase-2/ 中的变更方案已确认
4. 在 02-src/working/ 中开始修改代码
```

### 4.2 变更实施中

```
1. 在 02-src/working/ 中修改代码
2. 在 02-src/tests/ 中编写回归测试和变更测试
3. 在 01-docs/phase-3/ 中记录代码审查和测试报告
4. 在 06-logs/session-logs/ 中记录会话日志
```

### 4.3 变更完成后

```
1. 在 01-docs/phase-4/ 中完成知识沉淀
2. 更新 05-knowledge/project-brain.md
3. 在 01-docs/phase-5/ 中完成交付校验
4. 从各目录提取最终版，打包到 04-delivery/v{版本号}/
```

### 4.4 AI 实例切换时

```
新 AI 实例需要加载：
1. 05-knowledge/project-brain.md     ← 快速恢复项目认知
2. 05-knowledge/project-context.md   ← 快速恢复项目上下文
3. 01-docs/ 中当前阶段的文档         ← 了解当前进度
4. 06-logs/session-logs/ 中最近的日志 ← 了解上次做了什么
```

---

## 5. 与框架各阶段的关系

| 阶段 | 主要操作的目录 | 产出物存放位置 |
|------|---------------|---------------|
| Phase 0 | `01-docs/phase-0/` | 系统画像、AI 能力画像、可行性报告 |
| Phase 1 | `01-docs/phase-1/` | 变更规格文档、影响分析报告 |
| Phase 2 | `01-docs/phase-2/` | 架构理解文档、变更方案、角色化报告 |
| Phase 3 | `02-src/`、`01-docs/phase-3/` | 源代码、测试代码、审查记录 |
| Phase 4 | `01-docs/phase-4/`、`05-knowledge/` | 回顾报告、AI 错题本、系统知识库 |
| Phase 5 | `04-delivery/`、`01-docs/phase-5/` | 交付包、交付确认记录 |
| Module 7 | `05-knowledge/` | project-brain.md、AI 记忆 |
| Module 8 | `05-knowledge/constraint-analytics/` | 约束追溯、迭代快照 |

---

## 6. 检查清单

项目启动时，确认以下目录已创建：

- [ ] `00-framework/` — 框架文件已就位
- [ ] `01-docs/` — 各阶段子目录已创建
- [ ] `02-src/original/` — 原始源代码已拷入
- [ ] `02-src/working/` — 工作副本已从 original 拷贝
- [ ] `02-src/tests/` — 测试目录已创建
- [ ] `03-bak/` — 备份目录已创建
- [ ] `04-delivery/` — 交付目录已创建
- [ ] `05-knowledge/` — 知识资产目录已创建
- [ ] `06-logs/` — 日志目录已创建
