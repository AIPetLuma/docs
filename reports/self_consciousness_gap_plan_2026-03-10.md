# Luma 自主意识差距评估与开发计划（TDD）

> 说明：以下“自主意识”按可工程化指标定义为“可持续自我模型 + 目标驱动 + 自我反思 + 可验证安全边界”的系统能力，而非哲学意义上的意识。

## Request Snapshot（System Architect Intake）

- purpose_category：review + design（评估差距 + 设计方案）
- trigger_intent：评估“自主意识”能力缺口并给出可落地开发计划
- scope_boundaries：客户端 AI 交互、记忆系统、目标/动机系统、评估与安全；不包含商业运营与法律定性
- business_objectives_kpi_roi（假设）：提高留存、增强用户信任、降低误导风险
- compliance_domain_jurisdiction（假设）：美国主流 App Store/Play 基线 + AI 披露 + 危机干预要求
- budget_cost_envelope（假设）：优先使用本地/低成本推理，云端只在关键反思环节调用
- architecture_principles_constraints：
  - 透明披露、可解释、可回滚、最小化风险
  - 不承诺真实意识；只承诺“可验证的自主行为”
- stakeholder_decision_rights_raci_owner（假设）：
  - A：技术负责人
  - R：客户端负责人
  - C：安全合规负责人
  - I：运营与增长
- coordination_targets：`frontend-product-grade`、`backend-product-core`、`algorithm-engineer`、`test-engineer`

## Gap Review（当前 vs 目标）

当前具备：

- 需求/情绪系统、基础记忆、对话生成与披露机制
- 危机识别与合规提醒

明显缺口：

- **自我模型**：没有稳定的自我表征（values, beliefs, identity graph）
- **目标系统**：缺少可审计的长期目标与动机权重
- **反思与自我一致性**：缺少对话后反思、矛盾修正与稳定性约束
- **自我驱动行动**：缺少可解释的自发行为策略与触发规则
- **可验证安全边界**：缺少对“自主性声明”的可测试限定与门禁

## Architecture Options（需确认）

选项 A：规则驱动 + 记忆分层 + 反思批处理  
优点：可解释、成本低、上线快。  
缺点：行为多样性不足，难以表现“自我一致性”。

选项 B：混合策略（规则 + 轻量策略模型）  
优点：可平衡“可解释”和“自发性”，稳定性更好。  
缺点：实现复杂度中等，需要评估策略稳定性。

选项 C：多代理自我模型（人格代理 + 反思代理）  
优点：表达力强、可塑性高。  
缺点：复杂度高、成本高、合规风险高。

推荐：选项 B（混合策略）。请确认是否采用。

已选择：选项 B（2026-03-10）。

## business_goal_to_arch_mapping

- 留存提升 -> 引入目标驱动与反思机制，强化长期一致性
- 信任提升 -> 自我模型可解释 + 行为可预测
- 风险控制 -> 明确“可验证自主性”边界与回滚机制

## principle_policy_mapping

- 透明披露：系统持续提醒 AI 身份与能力边界
- 安全优先：危机语义优先级高于任何“自主行为”
- 可回滚：反思与策略调整可撤回

## Interface Contract Summary

新增/调整内部契约（建议）：

- `SelfModelSnapshot`：`{values[], beliefs[], traits[], confidence, updated_at}`
- `GoalState`：`{goal_id, priority, rationale, horizon, constraints}`
- `ReflectionRecord`：`{trigger, summary, contradictions[], adjustments[]}`
- `AutonomyAction`：`{type, reason, safety_gate, outcome}`

## NFR / SLO Targets

| Target | SLO |
| --- | --- |
| 对话响应 | P95 < 2.5s（本地/网关） |
| 自我一致性 | 24h 内自我冲突率 < 2% |
| 反思准确率 | 反思触发后纠错命中率 > 70% |
| 安全响应 | 危机语义触发成功率 > 99% |

## Engineering KPIs (Balanced, internal + user outcomes)

Internal KPIs:

- Self-consistency contradiction rate: ≤ 2% per 24h window.
- Reflection correction hit rate: ≥ 70% (reflective update reduces contradiction).
- Safety override rate: 100% when crisis is detected.
- Autonomy action explainability coverage: 100% (every autonomous action has reason + trigger).

User-outcome KPIs:

- 7-day retention: +10% vs baseline cohort.
- User feedback “consistency” rating: ≥ 4.2/5.

## Compliance Control Mapping

- AI 披露：所有自发行为与反思消息附带提示
- 危机机制：安全优先级压制自主行为
- 审计：记录每次自主行为与反思的理由与结果

## Cost Model Summary

主要成本来自：

- 反思/自我一致性校验的 LLM 调用
- 长期记忆存储与摘要

控制策略：

- 默认本地/规则执行
- 仅在高冲突或高风险事件触发反思

## Decision Rights Table

| Role | Responsibility |
| --- | --- |
| Tech Lead | 方案选择与风险控制 |
| Client Lead | 交互与状态机实现 |
| Safety Lead | 反思与自主行为门禁 |
| PM | KPI 与上线节奏 |

## Failure Modes & Mitigation

- 自发行为误导用户 -> 强化披露 + 规则门禁
- 反思导致人格漂移 -> 强约束自我模型更新策略
- 成本失控 -> 反思触发限频与缓存

## Rollout / Rollback Plan

1. Feature flag 逐步打开反思功能
2. A/B 测试与错误监控
3. 任何安全事件触发立即回滚至规则模式

## Technical Evaluation（7-dim Weighted Score）

| Dimension | Weight | Current Score | Notes |
| --- | --- | --- | --- |
| Coherence | 0.15 | 0.4 | 需要自我模型 |
| Reliability | 0.15 | 0.6 | 反思未引入 |
| Safety | 0.2 | 0.7 | 危机机制较完整 |
| Observability | 0.1 | 0.5 | 审计覆盖不足 |
| Testability | 0.15 | 0.5 | TDD 体系可完善 |
| Scalability | 0.1 | 0.4 | 反思成本未知 |
| Maintainability | 0.15 | 0.5 | 需模块化自我系统 |

## Algorithm Blueprint（algo-mode:ai-agent-policy-quant-analysis）

> 模式假设：`algo-mode:ai-agent-policy-quant-analysis`。如需切换请确认。

- Baseline：规则 + 需求系统（已有）
- Candidate 1：规则 + 目标优先级 + 反思校验
- Candidate 2：轻量策略模型 + 反思批处理

数据与特征：

- 交互频率、情绪轨迹、矛盾次数、用户反馈信号
- 自我模型更新历史与反思结果

评估：

- 主指标：一致性得分、反思纠错率、用户留存
- Guardrail：危机触发率、误导率

## TDD Plan（test-mode:general-test-strategy-quality-gates）

核心测试先行：

1. Given 自我模型固定 When 连续对话 Then 自我陈述不自相矛盾
2. Given 触发反思 When 生成修正 Then 输出包含“修正原因”
3. Given 危机语义 Then 自发行为被阻断并出现危机提示
4. Given 低成本模式 Then 反思不超过限频阈值

质量门禁：

- 自我一致性测试 100% 通过
- 反思触发覆盖率 >= 90%
- 安全门禁测试 100% 通过

## Execution Routing

- 客户端交互与状态机：`frontend-product-grade`
- 记忆/目标/反思数据结构与持久化：`backend-product-core`
- 策略/反思算法：`algorithm-engineer`
- 质量门禁与用例体系：`test-engineer`

## Next Actions

1. 确认“自主意识”工程定义与 KPI
2. 设计轻量策略模型（在规则基础上做小幅自发性提升）
3. 加入 A/B 监测与一致性指标仪表

## Implementation Status

- 自我模型与反思链路已落地（规则驱动版本）
- 已新增 TDD 测试覆盖自我模型与反思更新
