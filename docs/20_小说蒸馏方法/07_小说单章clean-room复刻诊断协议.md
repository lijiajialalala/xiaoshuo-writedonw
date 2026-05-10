# 小说单章 clean-room 复刻诊断协议

## 0. 一句话定义

```text
文案复刻的对象是一条完整文案正文。
小说单章复刻的对象是一章完整小说正文。
```

不是复刻“route 运动”“章节功能”“阻力反咬”“文风”。这些只是分析维度。

真正要产出的复刻物是：

```text
一章可以匿名放进两章原文里做三找一盲审的完整小说章节。
```

它必须像小说正文，不像拆书表、剧情梗概、设定稿、AI 扩写段落或写作建议。

## 1. 为什么先做单章复刻

文案那边能跑通，是因为它的最小闭环很清楚：

```text
一条原文文案
-> 提取
-> 归纳
-> clean-room 写一条完整复刻文案
-> 两条原文 + 一条复刻稿三找一盲审
-> 失败回到原文证据修 skill
```

小说如果一上来复刻整本、第一卷或前 10 章，会同时混进结构、文风、大纲、角色、能力、长线一致性和平台策略，失败后不知道错在哪里。

所以小说先用单章作为最小可闭合正文单位：

```text
一章有进入状态、场景运动、主角微目标、阻力、信息释放、兑现、状态变化和章末钩子。
```

单章复刻不能证明一本书能写长，但可以先验证：

```text
我们能不能把样本机制转成真实小说正文。
```

## 2. 和文案复刻的对应关系

| 文案侧 | 小说单章侧 |
| --- | --- |
| 一条完整短视频文案 | 一章完整小说正文 |
| 作者生成模型 | 单章生成诊断包 |
| 语言渲染器 | 最小叙述渲染器 |
| source-open 整篇阅读 | source-open 目标章 + 前后章阅读 |
| clean-room 复刻稿 | clean-room 单章正文 |
| 三找一盲审 | 两章原文 + 一章复刻稿三找一 |
| route / renderer / body 失败复盘 | 章节进入、场景身体、叙述距离、阻力、翻牌、文风失败复盘 |
| 回原文证据修 skill | 回目标章和邻近章证据修 diagnostic packet / skill |

核心借鉴不变：

```text
复刻是诊断工具，不是生产目标。
盲审是显微镜，不是成功奖杯。
失败反馈不能直接变规则，必须回原文证据确认。
```

## 3. 本阶段使用哪些 skill

### 3.1 必用 skill

```text
.agents/skills/novel-chapter-distiller/SKILL.md
```

用途：

```text
单章 source-open 阅读
单章证据提取
单章 diagnostic packet 归纳
clean-room writer prompt 约束
失败后回证据修 packet
```

### 3.2 必用盲审 skill

```text
.agents/skills/novel-blind-forensic-review/SKILL.md
```

用途：

```text
匿名三找一
判断哪一章是异类
定位暴露指纹
区分正文身体、文风、阻力、翻牌、AI水文和相似风险失败
```

### 3.3 贯穿使用的 gate

```text
.agents/skills/critical-thinking-mode/SKILL.md
.agents/skills/novel-editor-gate/SKILL.md
```

`critical-thinking-mode` 用在：

```text
选章前：为什么选这一章，它能测试什么？
归纳后：这个规则是不是被单章过拟合？
盲审后：失败到底说明什么，不说明什么？
回修前：有没有把 reviewer 观点伪装成原文规律？
```

`novel-editor-gate` 用在：

```text
复刻前：目标章节是否具备平台和编辑意义？
复刻后：复刻稿是否像 AI 水文、是否低可读、是否有相似风险？
进入下一轮前：是否允许继续扩大到前3章或事件链复刻？
```

## 4. 单章复刻完整流程

```text
A. 选复刻对象章节
-> B. source-open 目标章 + 邻近章阅读
-> C. 提取单章证据
-> D. 归纳 single-chapter diagnostic packet
-> E. clean-room 写一章完整正文
-> F. 三找一盲审
-> G. 失败复盘
-> H. 回原文证据修 packet / skill
```

## 5. A：选复刻对象章节

不要先选“最爽的一章”。先选能测试系统的章节。

### 5.1 可选章节类型

| 类型 | 测什么 |
| --- | --- |
| 第 1 章 | 书名/简介承诺如何落成正文、开局代入、第一钩子 |
| 第 2-3 章 | 承诺是否继续兑现、主角是否开始行动 |
| 第一个小高潮章 | 爽点/反杀/翻牌能不能写成正文 |
| 第一个任务启动章 | 组织、规则、资源入口如何进入 |
| 第一个阻力反咬章 | 敌人或规则是否主动改变主角处境 |
| 第一个章末强钩子章 | 信息释放和下一章压力 |

### 5.2 第一轮建议

第一轮不要选第 1 章。

原因：

```text
第 1 章同时承载书名、简介、世界观、主角初始状态和平台第一眼，变量太多。
```

更适合第一轮的是：

```text
第 3-8 章中一个“有明确进入状态、有冲突、有兑现、有章末钩子”的中段章节。
```

### 5.3 选章记录必须回答

```yaml
book_id:
chapter_no:
chapter_role:
why_this_chapter:
what_it_tests:
neighbor_scope:
prohibited_shapes:
editor_gate_reason:
```

## 6. B：source-open 目标章 + 邻近章阅读

单章不能孤立读。至少读：

```text
前一章
目标章
后一章
```

如果是第 1 章，读：

```text
简介
第1章
第2章
第3章
```

必须记录：

```text
目标章从哪里接压力
本章内部怎么移动
本章把什么压力交给下一章
```

不能只读章节摘要，否则会漏掉小说最关键的正文身体：

```text
叙述距离
段落呼吸
对白/动作/心理比例
设定如何进入行动
章末气口
```

## 7. C：提取单章证据

### 7.1 章节身体证据

```yaml
chapter_entry: ""
scene_count: ""
scene_switch: ""
paragraph_breath: ""
narrative_distance: ""
action_dialogue_psychology_ratio: ""
exposition_method: ""
chapter_exit: ""
```

判断目标：

```text
这一章到底怎么像一章小说正文，而不是一段剧情概括。
```

### 7.2 章节运动证据

```yaml
protagonist_micro_goal: ""
trigger_event: ""
conflict_unit: ""
opposition_micro_action: ""
protagonist_response: ""
information_release: ""
payoff_type: ""
resource_power_delta: ""
visibility_legitimacy_delta: ""
ending_hook: ""
```

判断目标：

```text
这一章是否有“必须发生”的运动，而不是作者随手安排。
```

### 7.3 最小文风 / 叙述渲染器证据

```yaml
sentence_texture: ""
dialogue_texture: ""
inner_voice: ""
description_texture: ""
rhythm_defects: ""
ai_slop_alarm: ""
```

注意：

```text
这里不做完整 Style Bible。
这里只抽足以让 clean-room 单章不像 AI 水文的最低叙述约束。
```

### 7.4 信息释放 / 翻牌证据

```yaml
open_question: ""
withheld_info: ""
visible_clue: ""
false_assumption: ""
reveal_or_flip: ""
flip_effect_on_future: ""
```

强翻牌标准：

```text
翻牌后必须改变主角目标、解法、敌我关系、风险等级、世界规则或下一章压力。
```

只解释过去、不改变未来，是弱翻牌。

### 7.5 相似风险边界

```yaml
prohibited_shapes:
  - ""
transferable_mechanisms:
  - ""
risk_notes:
  hard_risk: ""
  soft_risk: ""
```

禁止迁移：

```text
角色身份组合
能力设定
组织名和组织结构
怪物/异常规则
开局桥段顺序
名场面
高识别台词和句法
```

允许迁移：

```text
章节进入方式
压力交接方式
阻力主动动作方式
信息释放位置
兑现后状态变化类型
章末钩子功能
叙述距离和段落呼吸的抽象规则
```

## 8. D：归纳 single-chapter diagnostic packet

归纳不是写“这章很好”。归纳要产出 clean-room 写手能执行的 packet。

最低结构：

```markdown
# Single Chapter Diagnostic Packet

## Source Scope

## Target Chapter Role

## Chapter Entry Contract

## Beat Count And Scene Shape

## Micro Goal And Conflict

## Opposition Behavior

## Information Release Plan

## Payoff And Delta Rules

## Chapter Exit Hook

## Minimum Language Renderer

## Prohibited Shapes

## Editor Gate Notes

## Validation Gate
```

写法要求：

```text
规则必须是生成动作。
不要写读后感。
不要写原文情节。
不要把专属能力、专属组织、专属怪物改名后塞进去。
```

坏规则：

```text
本章节奏紧张，主角很爽，文风轻松。
```

好规则：

```text
开章必须接一个未解决的外部压力。
前 1/3 让主角用旧解法试探，但让阻力主动反咬。
中段释放一个小信息，让读者以为解法成立。
后 1/3 翻牌，让旧解法只解决表层问题，同时给主角一个资源或认知增量。
章末落在新的外部行动，而不是旁白总结。
```

## 9. E：clean-room 写一章完整正文

clean-room 写手只能读：

```text
single-chapter diagnostic packet
虚构的新题 brief
禁止迁移清单
house style 约束，如果有
```

clean-room 写手不能读：

```text
原文章节
原文摘录
证据文件
source-open memo
盲审答案
上一轮失败结论，除非已回原文确认并写入 packet
```

输出必须是：

```text
一章完整小说正文
```

不是：

```text
章节大纲
剧情梗概
设定说明
片段试写
三幕结构表
```

## 10. F：三找一盲审

盲审包结构：

```text
blind_packet/
  A.md
  B.md
  C.md
  review_prompt.md
  answer_key.md
```

评审只能看到：

```text
A.md
B.md
C.md
review_prompt.md
```

评审不能看到：

```text
answer_key.md
书名
作者名
路径
diagnostic packet
source evidence
上一轮 review
```

评审问题：

```text
哪一章是异类？
为什么？
另外两章为什么更像同一来源？
异类暴露在哪些层？
它像不像 AI 水文？
它有没有相似风险？
```

## 11. G：失败复盘

如果复刻稿被抓，不要马上加 prompt。先归因。

失败层级：

```text
chapter_object_failure：不像完整章节
entry_exit_failure：进入压力或章末钩子错
scene_body_failure：场景数量、切换、段落呼吸错
narrative_distance_failure：POV 距离或内心戏错
causality_failure：事件相邻但不是被逼出来
opposition_failure：阻力被动或假
reveal_failure：信息释放太早、太晚或无后果
payoff_delta_failure：没有资源/状态/认知变化
renderer_failure：文风和句段身体错
editor_quality_failure：AI水文、低可读或平台不适配
similarity_failure：太贴近源书内容形状
```

如果原文被抓，也不能直接宣布成功。要检查：

```text
两章原文是否本来就不是同 route
是否来自不同卷或不同阶段
是否一个章节天然异常
盲审包是否泄漏格式、标题、路径或长度
```

## 12. H：回原文证据修 packet / skill

回修规则：

```text
盲审反馈 = 校准证据。
原文章节 = 主证据。
```

只有当盲审失败点能在原文章节中确认，才能写入 packet。

不能做：

```text
评审说哪里不像，就把哪里直接加成硬规则。
为了骗过盲审，加入高识别口癖、桥段顺序、角色壳或专属能力。
把一次失败升级成永久规律。
```

可以做：

```text
记录失败层级。
回看目标章和邻近章。
确认原文是否有稳定行为。
修正 diagnostic packet。
再跑下一轮 clean-room。
```

## 13. 第一轮单章复刻建议产物

建议路径：

```text
research/20_cleanroom_chapter_replication/<run_id>/
```

产物：

```text
00_run_brief.md
01_source_open_memo.md
02_single_chapter_evidence.yaml
03_diagnostic_packet.md
04_cleanroom_writer_prompt.md
05_replica_chapter.md
blind_packet/A.md
blind_packet/B.md
blind_packet/C.md
blind_packet/review_prompt.md
blind_packet/answer_key.md
06_blind_review_report.md
07_failure_repair.md
```

注意：

```text
不要把受版权保护的整章原文提交进 Git。
blind_packet 里的原文章节如果是完整版权文本，只能放仓库外部。
Git 里只放结构摘要、packet、复刻稿、盲审问题和不含长原文的报告。
```

## 14. 第一轮停止条件

停止并回修，不继续扩大样本：

```text
复刻稿不像完整小说章节。
复刻稿只能复述 packet，不能自然成文。
盲审明确识别 AI 水文。
盲审指出高相似风险。
失败层级无法归因。
归因无法回到原文证据确认。
```

允许进入下一轮：

```text
复刻稿至少像完整章节。
盲审失败点可定位到具体层级。
没有硬相似风险。
packet 回修能明确说明改了什么和为什么。
```

允许扩大到前 3 章复刻：

```text
至少 2 轮单章复刻能稳定生成完整章节。
失败不再集中在正文身体和 AI 水文。
相似风险边界稳定。
editor gate 不再判定为 stop。
```

## 15. critical-thinking-mode 自问自答

### Q1：为什么复刻对象必须是一章完整正文？

因为文案复刻不是复刻“观点结构表”，而是复刻一条可盲审的完整文案。小说如果只复刻 route、阻力、翻牌或文风标签，就没有可盲审对象，也无法知道系统能不能真的写出小说正文。

### Q2：为什么不是先复刻前 3 章？

前 3 章同时测试开局承诺、人物建立、世界观、主线引爆、平台第一眼和追读，变量太多。单章先把“能不能写出真实章节身体”测出来，再扩大到前 3 章更稳。

### Q3：为什么第一轮不建议第 1 章？

第 1 章有太多书名和简介绑定内容，最容易碰到高识别开局桥段和平台套路。中段章节更适合先测试章节进入、冲突、兑现、章末钩子这些可迁移机制。

### Q4：单章复刻会不会太小，无法代表小说？

会。所以单章复刻只能证明章节级 packet 是否可执行，不能证明长篇 route 成立。它是最小诊断，不是最终验证。后面仍要做前 3 章、事件链、第一卷和 Story Bible。

### Q5：盲审通过能不能说明我们可以生产？

不能。盲审通过只说明这一组没有暴露。生产还需要 house style、原创设定、平台门、相似风险门、长期一致性和编辑门。

### Q6：如果盲审说复刻稿不像，能不能直接按建议改？

不能。盲审是校准证据，不是主证据。必须回到目标章和邻近章确认失败点是否真的来自源章节行为，再修 packet。

### Q7：单章复刻最容易走偏在哪里？

最容易把“结构像”误认为“正文像”。小说正文还有叙述距离、段落呼吸、对白动作心理比例、设定进入方式和章末气口。这些不抽，复刻稿会像 AI 剧情大纲扩写。

### Q8：最重要的安全边界是什么？

复刻章节运动和叙述机制，不复刻内容形状。角色、能力、组织、怪物、规则、桥段顺序、名场面和高识别文风都不能迁移。

## 16. 当前执行建议

下一步先跑一轮最小闭环：

```text
1. 从 P2-alpha 三本里选 1 本。
2. 选第 3-8 章里一个完整中段章。
3. 读前一章、目标章、后一章。
4. 用 novel-chapter-distiller 做单章证据和 diagnostic packet。
5. 隔离写一章全新内容。
6. 用 novel-blind-forensic-review 做三找一盲审。
7. 用 critical-thinking-mode 做失败归因。
8. 用 novel-editor-gate 做相似、AI水文和平台可读性门。
9. 回源章节修 packet。
```

第一轮目标不是骗过盲审，而是确认：

```text
小说单章复刻这个诊断闭环能不能跑起来。
```

