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
| source_lineage_sample | S031 | 大一实习，你跑去749收容怪物 | 用户标记为 749/收容方向开山样本，番茄页面显示长篇连载体量；比低热 749 样本更适合校准源头机制 | 749/异常收容路线靠什么建立开局承诺、组织入口、怪物压力、收容成长和长线事件链 |
| current_hot_sample | S001 | 人在高武，系统非说在末世 | L0 中较接近当前番茄都市高武系统爽文读者基本盘，适合看免费阅读环境下的承诺兑现 | 高武系统爽文靠什么建立前 3 章承诺、前 10 章兑现和升级压力 |
| completed_system_sample | S032 | 高武：系统兜底，坚持就能无敌！ | 番茄页面显示已完结、138.2 万字、531 章；比低字数吞噬样本更适合验证长线高武系统结构 | 生存压力、系统兜底、资源循环和升级兑现能否支撑完本长线，而不只是前期比大小 |

## 2. 为什么替换 S002 / S014

S002 `749局：九处特案调查科` 的问题不是“不能拆”，而是热度、源头性和平台代表性不足。它可以作为 `observe_only` 结构样本，不能占用 P2-alpha 的 749/异常方向名额。

S014 `都市高武：我能无限吞噬灵气` 的问题是字数偏短、热度证据弱，更适合作为纯比大小爽文噪声样本。P2-alpha 需要先校准能支撑长线的高武系统样本，所以替换为 S032。

## 3. 为什么不是直接选 S010 / S016

但 P2-alpha 的任务不是挑最想学的书，而是测试提取器是否能顶住三种压力：

```text
源头/开山样本压力
当前平台热度样本压力
完本长线样本压力
```

如果第一轮就全选 S010、S016 这类喜欢的样本，最后归纳出来的可能是我们的阅读偏好，不是番茄平台机制。

S010 和 S016 暂列为 P2-beta 第一优先候选；P2-alpha 通过后再拆。

## 4. 每本必须输出

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

## 5. 证据边界

允许：

1. 人工阅读前 10 章后写结构摘要。
2. 记录章节标题、场景功能、状态变化和结构作用。
3. 用短摘要记录读者反馈，不复制大段评论。

禁止：

1. 复制完整章节。
2. 复制高识别段落。
3. 把样本桥段顺序迁移进我们的项目。
4. 把某本书的专属能力、组织、怪物、名场面写成通用机制。

## 6. P2-alpha 后判断

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

## 7. 停止条件

满足任一条件，停止扩大样本：

1. 3 本都拆不出前 10 章留人结构。
2. 只能拆出设定，拆不出主角行动发动机。
3. 只能拆出单书高识别桥段，压不成机制。
4. `transfer_boundary` 和 `risk_note` 普遍缺失。
5. E11 长期一致性需求记录不清。
6. P2 字段明显不适配真实样本。

停止后先回修 P2 协议或更换样本组合，不进入 P2-beta。

## 8. 当前下一步

按顺序执行：

```text
1. 创建 p2_alpha 目录。
2. 复制 3 份 chapter_evidence.yaml。
3. 先填 S001。
4. 再填 S031。
5. 最后填 S032。
6. 做 00_P2-alpha复盘.md。
```
