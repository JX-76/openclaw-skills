# PM Skills - 产品经理实用技能集

基于实际工作场景设计，强调**可落地、有约束、高质量**。

---

## 设计原则

### 1. 精简聚焦（29个核心技能）
从 pm-skills 的 65 个精简到 29 个，覆盖产品全生命周期：需求→设计→验证→数据分析→AI产品→增长→商业化→战略。

### 2. 强制触发条件
每个技能都有明确的 When to Use，避免滥用。

### 3. 质量门控
输入检查 → 过程检查 → 输出检查，确保结果可用。

### 4. 真实场景驱动
不是理论框架，而是基于实际工作流的实用工具。

---

## 技能清单

### 需求阶段
| 技能 | 解决什么问题 | 触发条件 |
|------|-------------|---------|
| [requirement-clarify](./requirement-clarify/) | 一句话需求太模糊 | 需求 < 30 字或含"优化"等模糊词 |
| [user-research](./user-research/) | 不知道用户真正需要什么 | 明确说"调研"、"访谈"或从0到1 |
| [competitive-analysis](./competitive-analysis/) | 竞品分析变成功能罗列 | 明确说"竞品"、"对标" |

### 设计阶段
| 技能 | 解决什么问题 | 触发条件 |
|------|-------------|---------|
| [prd-writer](./prd-writer/) | PRD写不清楚，开发看不懂 | 明确说"写PRD"且提供背景/用户/功能 |
| [mvp-planner](./mvp-planner/) | 需求太大，迟迟上不了线 | 周期 > 1个月或明确说"MVP" |
| [prioritization](./prioritization/) | 需求太多，先做哪个 | 需求 > 5个或资源受限 |

### 验证阶段
| 技能 | 解决什么问题 | 触发条件 |
|------|-------------|---------|
| [metrics-design](./metrics-design/) | 无法衡量产品成功 | 提到"指标"、"度量"或模糊目标 |
| [a-b-test](./a-b-test/) | 凭感觉上线，不知道效果 | 有明确改动+指标+充足样本 |

### 数据分析
| 技能 | 解决什么问题 | 触发条件 |
|------|-------------|---------|
| [data-analysis](./data-analysis/) | 有数据但不知道怎么分析 | 明确说"分析一下"或数据决策 |
| [sql-query](./sql-query/) | 找数据团队要等一周 | 需要快速自助取数 |
| [cohort-analysis](./cohort-analysis/) | 留存数字波动大 | 需要看清真实留存趋势 |
| [funnel-analysis](./funnel-analysis/) | 转化率低不知道哪步出问题 | 有明确多步骤流程 |
| [retention-analysis](./retention-analysis/) | 留存低不知道怎么提升 | 次日留存<30%或持续下降 |
| [aarrr-metrics](./aarrr-metrics/) | 增长没头绪抓不住重点 | 需要全面诊断增长瓶颈 |

### AI 产品
| 技能 | 解决什么问题 | 触发条件 |
|------|-------------|---------|
| [prompt-design](./prompt-design/) | AI 输出不稳定 | 需要设计/优化 prompt |
| [ai-feature-planning](./ai-feature-planning/) | 什么都想用 AI | 评估 AI 适用性+规划方案 |
| [model-evaluation](./model-evaluation/) | 模型准确率多少算合格 | 模型上线前评估 |
| [ai-ux-design](./ai-ux-design/) | AI 出错用户不信任 | 设计 AI 交互体验 |
| [rag-product-design](./rag-product-design/) | AI 不知道企业知识 | 基于私有数据的 AI 问答 |

### 运营与优化
| 技能 | 解决什么问题 | 触发条件 |
|------|-------------|---------|
| [user-journey](./user-journey/) | 不知道哪里流失 | 明确说"用户路径"或转化率低 |
| [launch-checklist](./launch-checklist/) | 上线总出事故 | 功能准备上线（1-3天） |
| [retrospective](./retrospective/) | 踩过的坑重复踩 | 项目结束或重大事故 |

### 增长与获客
| 技能 | 解决什么问题 | 触发条件 |
|------|-------------|---------|
| [growth-loop](./growth-loop/) | 获客成本越来越高 | CAC高或主要靠付费投放 |
| [referral-design](./referral-design/) | 用户不主动推荐 | NPS>30且有分享场景 |
| [onboarding-optimization](./onboarding-optimization/) | 新用户来了就流失 | 次日留存<30%或激活率低 |

### 商业化
| 技能 | 解决什么问题 | 触发条件 |
|------|-------------|---------|
| [pricing-strategy](./pricing-strategy/) | 不知道怎么定价 | 产品准备商业化或定价转化<2% |
| [monetization-model](./monetization-model/) | 有用户但不赚钱 | 明确说"商业模式"或变现 |
| [unit-economics](./unit-economics/) | 不知道赚多少亏多少 | 融资需要或规模化前评估 |

### 战略与规划
| 技能 | 解决什么问题 | 触发条件 |
|------|-------------|---------|
| [roadmap](./roadmap/) | 规划只有PPT | 明确说"路线图"或战略汇报 |

---

## 核心改进点（vs pm-skills）

| 维度 | pm-skills | 本优化版 |
|------|-----------|---------|
| 数量 | 65个 | 29个 |
| 触发条件 | 模糊 | 强制检查（必须满足才触发） |
| 质量门控 | 无 | 输入/过程/输出三层检查 |
| 实际场景 | 理论框架 | 真实工作流 |
| 输出标准 | 灵活 | 必须可执行（开发能看懂/测试能测） |

---

## 完整工作流示例

```
【需求阶段】
用户："做个会员系统"
↓ 触发 requirement-clarify
输出：澄清后的需求（用户/场景/目标）
↓
用户："调研一下用户需求"
↓ 触发 user-research
输出：调研方案
↓
用户："看看竞品怎么做的"
↓ 触发 competitive-analysis
输出：竞品分析报告

【设计阶段】
用户："写个PRD"
↓ 触发 prd-writer
输出：完整PRD文档
↓
用户："需求太多了，先做哪些？"
↓ 触发 prioritization
输出：优先级排序
↓
用户："能不能快点上线？"
↓ 触发 mvp-planner
输出：MVP规划

【验证阶段】
用户："怎么衡量效果？"
↓ 触发 metrics-design
输出：指标体系
↓
用户："测试一下新方案"
↓ 触发 a-b-test
输出：测试报告

【运营优化】
用户："转化率太低了"
↓ 触发 user-journey
输出：用户路径地图+优化点
↓
用户："准备上线了"
↓ 触发 launch-checklist
输出：上线检查清单
↓
项目结束
↓ 触发 retrospective
输出：复盘报告

【增长获客】
用户："获客成本太高了"
↓ 触发 growth-loop
输出：增长飞轮方案
↓
用户："怎么让用户推荐朋友？"
↓ 触发 referral-design
输出：推荐体系方案
↓
用户："新用户来了就流失"
↓ 触发 onboarding-optimization
输出：激活优化方案

【商业化】
用户："怎么定价？"
↓ 触发 pricing-strategy
输出：定价策略
↓
用户："怎么赚钱？"
↓ 触发 monetization-model
输出：商业模式方案
↓
用户："融资需要算LTV"
↓ 触发 unit-economics
输出：单位经济模型

【战略规划】
用户："做个产品规划"
↓ 触发 roadmap
输出：产品路线图
```

---

## 快速开始

1. 明确当前阶段（需求/设计/验证/数据分析/AI产品/运营/增长/商业化/战略）
2. 对照触发条件选择技能
3. 提供必需信息
4. 按 Workflow 执行

---

*Version: v1.0.0 | 2026-04-07*
