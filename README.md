# 天工（TianGong）

> **面向已有系统定制化开发的 AI 驱动方法论**

TianGong 是基于 [Paoding（庖丁）](https://github.com/klmk/Paoding) 框架改造的 AI 驱动开发框架。Paoding 擅长从无到有（Greenfield）的软件开发，而本框架专注于在已有系统上进行定制化开发（Brownfield Customization）。

---

## 与 Paoding 的关系

Paoding 和 TianGong 共享相同的设计哲学 -- **用约束保障质量，用流程降低风险**，但面向不同的开发场景：

| 维度 | Paoding | TianGong |
|------|---------|----------------------|
| 场景 | 从无到有（Greenfield） | 在已有系统上定制化（Brownfield） |
| AI 角色 | 创造者 | 理解者 + 改造者 |
| 首要任务 | 设计与构建 | 分析与改造 |
| 最大风险 | 需求理解偏差 | 破坏已有功能 |
| 测试策略 | 新功能测试为主 | 回归测试优先 |
| 知识积累 | 项目知识 | 系统理解 + 项目知识 |

**继承的部分**：约束体系（铁律、反模式、审查机制、调试方法）、四级优先级体系、"精神与字面"原则。

**改造的部分**：流程体系（Phase 0-5 全部重新设计）、知识体系（增加系统结构认知、地雷区、变更认知等维度）。

---

## 核心特色

### 1. 系统画像：先理解现有系统再动手

在动手做任何变更之前，先建立对目标系统的全面理解。系统画像覆盖技术栈、架构风格、模块关系、数据流、关键依赖等维度，为后续变更提供知识基础。

### 2. 变更分析：评估影响范围和回归风险

每一个变更需求都必须经过结构化的影响分析，明确变更会影响哪些模块、接口和数据，评估可能破坏的已有功能，制定回归测试策略。

### 3. 先保护再修改：回归测试优先

在已有系统上做变更，必须先建立回归测试保护，然后才能修改代码。回归测试是客开场景的安全网。

### 4. 系统知识沉淀：持续积累对现有系统的理解

每一次变更都是加深系统理解的机会。通过知识蒸馏机制，将持续积累的系统认知结构化地沉淀到项目大脑中，让 AI 越来越了解目标系统。

---

## 框架结构总览

```
TianGong/
│
├── README.md                              # 项目总览（本文件）
│
├── core/                                  # 核心约束体系
│   ├── SKILL.md                           # 核心技能入口
│   ├── iron-laws.md                       # 6 条铁律清单
│   ├── anti-patterns.md                   # 反模式清单（17 条）
│   └── workflow-overview.md               # 6 阶段全流程总览
│
├── phase-0-system-profiling/              # Phase 0: 系统画像
│   ├── SKILL.md                           # 阶段技能入口
│   ├── system-profile-template.md         # 系统画像模板
│   ├── ai-capability-profile-template.md  # AI 能力画像模板
│   └── feasibility-assessment-template.md # 客开可行性评估模板
│
├── phase-1-change-analysis/               # Phase 1: 变更分析
│   ├── SKILL.md                           # 阶段技能入口
│   ├── change-request-template.md         # 变更需求模板
│   ├── impact-analysis-template.md        # 影响分析模板
│   └── change-alignment-checklist.md      # 变更对齐检查清单
│
├── phase-2-architecture-understanding/    # Phase 2: 架构理解
│   ├── SKILL.md                           # 阶段技能入口
│   ├── architecture-understanding-template.md # 架构理解模板
│   ├── change-plan-template.md            # 变更方案模板
│   └── design-review-checklist.md         # 设计审查清单
│
├── phase-3-change-implementation/         # Phase 3: 变更实施
│   ├── SKILL.md                           # 阶段技能入口
│   ├── regression-testing-guide.md        # 回归测试指南
│   ├── code-review-guide.md               # 代码审查指南
│   └── systematic-debugging-guide.md      # 系统化调试指南
│
├── module-7-knowledge-distillation/       # Module 7: 知识蒸馏
│   ├── SKILL.md                           # 模块技能入口
│   ├── project-brain-template.md          # 项目大脑模板（客开版）
│   ├── distillation-process-guide.md      # 蒸馏流程指南
│   └── memory-capture-guide.md            # 记忆捕获指南
│
└── module-8-constraint-analytics/         # Module 8: 约束有效性分析
    ├── SKILL.md                           # 模块技能入口
    ├── constraint-trace-template.md       # 约束追溯记录模板
    ├── iteration-snapshot-template.md     # 迭代快照模板
    ├── aggregate-analysis-template.md     # 聚合分析报告模板
    └── optimization-loop-guide.md         # 框架优化闭环指南
```

---

## 阶段流程图

```
Phase 0 ──→ Phase 1 ──→ Phase 2 ──→ Phase 3 ──→ Phase 4 ──→ Phase 5
系统画像    变更分析    架构理解    变更实施    知识沉淀    变更交付
  │            │            │            │            │            │
  ▼            ▼            ▼            ▼            ▼            ▼
[硬性门控]  [硬性门控]   [硬性门控]   [硬性门控]   [软性门控]  [硬性门控]
  G-0         G-1          G-2          G-3          G-4          G-5

持续运行模块：
Module 7: 知识蒸馏 ──────────────────────────────────────────→ 贯穿全流程
Module 8: 约束有效性分析 ───────────────────────────────────→ 贯穿全流程
```

### 各阶段概要

| 阶段 | 名称 | 核心目标 | 关键活动 |
|------|------|----------|----------|
| Phase 0 | 系统画像 | 理解目标系统 | 技术栈识别、模块关系梳理、AI 能力评估、可行性评估 |
| Phase 1 | 变更分析 | 明确变更需求 | 需求澄清、影响范围分析、回归风险评估、验收标准定义 |
| Phase 2 | 架构理解 | 深入理解相关模块 | 模块深度分析、数据流追踪、隐含约束识别、变更方案设计 |
| Phase 3 | 变更实施 | 安全地实施变更 | 回归测试编写、代码变更、变更自审、测试执行 |
| Phase 4 | 知识沉淀 | 积累系统认知 | 系统画像更新、经验教训总结、技术债务记录 |
| Phase 5 | 变更交付 | 完整交付变更成果 | 变更总结、部署说明、回退方案、最终验证 |

---

## 快速开始

### 1. 理解核心约束

从 `core/SKILL.md` 开始，了解框架的触发规则、四级优先级体系和客开三大原则。

### 2. 学习铁律和反模式

阅读 `core/iron-laws.md`（6 条铁律）和 `core/anti-patterns.md`（17 条反模式），理解框架的底线和常见错误。

### 3. 了解全流程

阅读 `core/workflow-overview.md`，了解 6 阶段的完整流程、门控体系和回退机制。

### 4. 按阶段执行

从 Phase 0（系统画像）开始，按照各阶段的 SKILL.md 和模板文件逐步执行。

### 5. 持续蒸馏和分析

在客开过程中，持续使用 Module 7（知识蒸馏）沉淀系统认知，使用 Module 8（约束有效性分析）优化框架执行。

---

## 与 Paoding 的对比

| 对比维度 | Paoding（Greenfield） | TianGong（Brownfield） |
|----------|----------------------|-------------------------------------|
| **开发场景** | 从零构建新系统 | 在已有系统上做定制化开发 |
| **AI 角色** | 创造者 -- 从零设计和构建 | 理解者 + 改造者 -- 先理解后改造 |
| **阶段设计** | 5 个阶段（需求分析 → 系统设计 → 编码实现 → 测试验证 → 交付部署） | 6 个阶段（系统画像 → 变更分析 → 架构理解 → 变更实施 → 知识沉淀 → 变更交付） |
| **起始点** | 需求分析 | 系统画像（先理解系统） |
| **核心风险** | 需求理解偏差 | 破坏已有功能 |
| **测试策略** | 新功能测试为主 | 回归测试优先，先建立测试基线再改代码 |
| **门控重点** | 设计完整性和代码质量 | 影响分析和回归安全 |
| **文档重点** | 设计文档和 API 文档 | 变更文档、影响分析、系统认知 |
| **知识体系** | 项目知识（业务、编码、避坑） | 系统理解 + 项目知识（增加系统结构认知、地雷区、变更认知） |
| **约束特色** | 通用开发约束 | 增加系统保护约束、回归安全约束、影响分析约束、兼容性约束、知识沉淀约束 |
| **成长方式** | 项目经验积累 | 系统理解深化 + 影响预测能力提升 |

---

## 致谢

- **[Paoding（庖丁）](https://github.com/klmk/Paoding)** -- 本框架的基础，提供了约束体系（铁律、反模式）和设计哲学。
- **[Superpowers](https://github.com/obra/Superpowers)** -- AI 驱动开发的灵感来源。
- **[BMad Method](https://github.com/bmad-code-org/BMAD-METHOD)** -- 结构化方法论的设计参考。

---

## 许可证

MIT License

Copyright (c) 2024 TianGong Contributors

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
