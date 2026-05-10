# 策略漏洞循环登记模板

## 0. 基本信息

```yaml
risk_loop_id:
created_at:
owner:
stage:
related_doc:
status: open # open / mitigated / verified / accepted / closed
```

## 1. 风险描述

```text
risk_name:
problem:
why_it_matters:
failure_mode:
```

## 2. 影响范围

```text
affected_stage:
affected_outputs:
hard_risk:
soft_risk:
```

## 3. 根部假设

```text
assumption:
why_this_assumption_may_fail:
counterexample_needed:
```

## 4. 修复措施

```text
mitigation:
owner_action:
doc_or_schema_change:
```

## 5. 验证门

```text
validation_gate:
pass_condition:
fail_condition:
fallback_action:
```

## 6. 当前置信

```text
confidence_before:
confidence_after:
remaining_risk:
next_review_at:
```

## 7. 决策

```text
decision: # continue / revise / stop / accept_risk
decision_reason:
```
