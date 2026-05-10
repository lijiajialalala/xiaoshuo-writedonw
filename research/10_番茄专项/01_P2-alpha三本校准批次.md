# P2-alpha 三本校准批次

## 0. 目的

P2-alpha 不是正式拆书，也不是选最终对标。

它只做一件事：

```text
用 3 本差异明显的样本，测试 P2 前 10 章提取器能不能产出 route_candidate。
```

如果这 3 本跑不动，不扩大到 10-15 本。

## 1. 本批次样本

| sample_role | 编号 | 书名 | 为什么选 | 本批次验证重点 |
| --- | --- | --- | --- | --- |
| head_sample | S001 | 人在高武，系统非说在末世 | L0 中最接近有体量的番茄都市高武系统爽文，适合看免费阅读基本盘 | 高武系统爽文靠什么建立前 3 章承诺、前 10 章兑现和升级压力 |
| mid_sample | S002 | 749局：九处特案调查科 | 完结 75.9 万字，异常事件小队路线，贴合“城市异常事件处理”目标 | 异常事件/749 小队能否形成案件压力、组织阻力和第一卷方向 |
| counter_preference_sample | S014 | 都市高武：我能无限吞噬灵气 | 偏纯吞噬升级和比大小，不是我们当前最想写的方向，但能代表平台上常见高武爽文噪声 | 验证纯战力爽文是否只有设定和升级，能不能拆出可迁移机制，防止我们只按偏好选样本 |

## 2. 为什么不是直接选 S010 / S016

S010 无限读档、S016 破绽推演都更贴近我们主观偏好的“智斗/信息差/破绽反杀”。

但 P2-alpha 的任务不是挑最想学的书，而是测试提取器是否能顶住三种压力：

```text
主流爽文压力
异常事件路线压力
反偏好/噪声样本压力
```

如果第一轮就全选 S010、S016 这类喜欢的样本，最后归纳出来的可能是我们的阅读偏好，不是番茄平台机制。

S010 和 S016 暂列为 P2-beta 第一优先候选；P2-alpha 通过后再拆。

## 3. 每本必须输出

每本复制一份：

```text
schemas/chapter_evidence.yaml
```

并保存到：

```text
research/10_番茄专项/p2_alpha/<book_id>_<short_title>.yaml
```

每本必须填：

```text
sample_role
book_level_observation
chapter_records 前 10 章
chapter_motion_summary
editor_gate_summary
route_candidate_decision
```

P2-alpha 必须重点填这些字段：

```text
reader_promise
protagonist_goal
trigger_event
obstacle
protagonist_action
information_reveal
payoff
state_change
ending_hook
next_chapter_pressure
outline_signal
continuity_memory_signal
ai_quality_signal
transfer_boundary
risk_note
```

## 4. 证据边界

允许：

1. 人工阅读前 10 章后写结构摘要。
2. 记录章节标题、场景功能、状态变化和结构作用。
3. 用短摘要记录读者反馈，不复制大段评论。

禁止：

1. 复制完整章节。
2. 复制高识别段落。
3. 把样本桥段顺序迁移进我们的项目。
4. 把某本书的专属能力、组织、怪物、名场面写成通用机制。

## 5. P2-alpha 后判断

三本完成后，必须先做一次 P2-alpha 复盘，不允许直接进入 P2-beta。

输出文件：

```text
research/10_番茄专项/p2_alpha/00_P2-alpha复盘.md
```

复盘必须回答：

1. 三本是否都能填完核心字段？
2. 哪些字段最难填，是样本问题还是模板问题？
3. 是否能从三本里产出 route_candidate？
4. 哪些证据是可迁移机制，哪些只是单书内容形状？
5. 反偏好样本有没有暴露我们的偏见？
6. P2 协议是否需要回修？
7. 是否允许扩到 P2-beta？

## 6. 停止条件

满足任一条件，停止扩大样本：

1. 3 本都拆不出前 10 章留人结构。
2. 只能拆出设定，拆不出主角行动发动机。
3. 只能拆出单书高识别桥段，压不成机制。
4. `transfer_boundary` 和 `risk_note` 普遍缺失。
5. E11 长期一致性需求记录不清。
6. P2 字段明显不适配真实样本。

停止后先回修 P2 协议或更换样本组合，不进入 P2-beta。

## 7. 当前下一步

按顺序执行：

```text
1. 创建 p2_alpha 目录。
2. 复制 3 份 chapter_evidence.yaml。
3. 先填 S001。
4. 再填 S002。
5. 最后填 S014。
6. 做 00_P2-alpha复盘.md。
```
