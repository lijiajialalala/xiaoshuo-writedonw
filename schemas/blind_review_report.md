# 盲审 / 追读诊断报告模板

## 0. 基本信息

```yaml
review_id:
draft_id:
route_candidate:
content_kernel:
reviewed_at:
reviewer:
blind_level: # full_blind / partial_blind / self_review
```

## 1. 输入材料

```text
draft_scope: # 单章 / 前3章 / 前10章计划 / 事件链 / 第一卷
reviewer_can_see:
reviewer_cannot_see:
```

## 2. 追读判断

```text
would_read_next:
why:
drop_point:
drop_reason:
strongest_hook:
weakest_link:
```

## 3. 机制诊断

| 项 | 结论 | 证据位置 | 问题等级 |
| --- | --- | --- | --- |
| reader_promise |  |  |  |
| protagonist_engine |  |  |  |
| obstacle_system |  |  |  |
| causal_chain |  |  |  |
| reveal_or_flip |  |  |  |
| payoff |  |  |  |
| chapter_hook |  |  |  |
| style_voice |  |  |  |

## 4. 风险诊断

```text
ai_water_text_risk:
similarity_risk:
platform_mismatch_risk:
logic_break_risk:
style_drift_risk:
```

## 5. 失败归因

```text
failure_layer: # route / kernel / causality / obstacle / reveal / style / similarity / platform
root_cause:
required_fix:
```

## 6. 决策

```text
decision: # approve_next_stage / revise / stop
decision_reason:
evidence_to_recheck:
next_action:
```
