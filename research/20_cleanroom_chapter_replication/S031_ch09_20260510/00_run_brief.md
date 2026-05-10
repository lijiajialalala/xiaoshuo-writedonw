# P2.1 单章 clean-room 复刻校准：S031 第9章

## 0. 运行定位

本轮不是正式正文生产，也不是复刻某本书用于发布。

本轮只测试一件事：

```text
小说单章能不能像文案一样跑通：
提取 -> 归纳 -> clean-room 写一章完整正文 -> 三找一盲审 -> 失败回证据修 packet。
```

## 1. 选章

```yaml
run_id: S031_ch09_20260510
book_id: S031
title: 大一实习，你跑去749收容怪物
platform: 番茄小说
target_chapter: 第9章
target_chapter_role: 考核结束后的资源兑现章 + 第一个正式任务入口章
neighbor_scope: 第8章 / 第9章 / 第10章
source_text_location: D:\小说创作\书本源数据\大一实习，你跑去749收容怪物\all.txt
repo_policy: 不提交原文章节全文，只提交结构摘要、机制、packet、风险边界和诊断产物。
```

## 2. 为什么选第9章

不选第1章：

```text
第1章绑定书名、简介、工地开局、金手指和怪物首次出现，内容形状识别度太高，第一轮容易误把开局壳当机制。
```

选第9章：

```text
第9章处在第8章考核完美和第10章正式任务出发之间。
它不是单纯打斗，也不是纯设定说明，而是把组织资源、功法选择、境界突破、任务 APP、案件承诺和辅调规则接在一起。
```

它适合测试：

```text
资源兑现如何不变成福利说明书。
主角升级后如何马上进入新压力。
组织规则如何制造任务约束。
第一个案件如何在章末形成下一章钩子。
一章里如何处理设定、修炼、任务信息和论坛反应。
```

## 3. 本轮不复刻什么

禁止迁移：

```text
749 组织名和制度外壳
飞熊观想图
开窍丹 / 照璇 / 飞熊扑杀法
黑老太太
灭门案
贡献点具体数值
任务 APP 的具体外观和论坛喊话内容
主角陆鼎、邓国福、燕非凡等角色形状
```

本轮只学习：

```text
考核结果如何兑现成资源。
资源如何立刻转成新能力。
新能力如何接第一个正式任务。
组织任务规则如何制造“必须找搭档/辅调”的约束。
章末如何用公开招募/社群反应把下一章推出去。
```

## 4. 使用 skill

```text
.agents/skills/novel-chapter-distiller/SKILL.md
.agents/skills/novel-blind-forensic-review/SKILL.md
.agents/skills/critical-thinking-mode/SKILL.md
.agents/skills/novel-editor-gate/SKILL.md
```

## 5. 本轮产物

```text
00_run_brief.md
01_source_open_memo.md
02_single_chapter_evidence.yaml
03_diagnostic_packet.md
04_cleanroom_writer_prompt.md
05_replica_chapter.md              # 待隔离写手生成
blind_packet/A.md                   # 原文全文不入 Git；如需盲审，放外部安全包
blind_packet/B.md
blind_packet/C.md
blind_packet/review_prompt.md
blind_packet/answer_key.md
06_blind_review_report.md           # 待盲审
07_failure_repair.md                # 待盲审后回修
```

## 6. critical-thinking-mode 自问自答

### Q1：我是不是把例子当成结论了？

没有。第9章只作为“资源兑现 -> 任务入口”的单章校准样本，不升级成所有小说单章规则。

### Q2：这个章节还有哪些替代解释？

至少有三种：

```text
它可能是组织福利章。
它可能是战力升级章。
它可能是第一个案件入口章。
```

本轮选择把它视为“资源兑现和任务入口复合章”，不是定论。

### Q3：什么证据会推翻本轮选择？

如果 clean-room 写手只能写出福利说明、修炼说明或任务列表，而写不出完整章节正文，说明第9章不适合作为第一轮单章复刻样本，或者我们的提取字段漏掉了正文身体。

### Q4：这轮成功说明什么？

只说明单章 diagnostic packet 可能驱动一章完整正文。不能说明 S031 route 可生产，也不能说明可以复刻 749 或黑老太太。

### Q5：这轮失败优先查哪里？

优先查：

```text
正文身体是否抽得太少。
资源兑现是否被写成设定说明。
任务入口是否没有真实下一章压力。
文风是否变成 AI 大纲扩写。
相似风险是否被低估。
```

