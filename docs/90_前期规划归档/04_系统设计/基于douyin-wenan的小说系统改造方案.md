# 基于 douyin-wenan 的小说系统改造方案

更新时间：2026-05-04

参考仓库：https://github.com/lijiajialalala/douyin-wenan

## 当前仓库可复用资产

`douyin-wenan` 当前已经具备以下基础：

- manifest 作为单一事实源。
- 批处理状态机。
- ASR转写和清洗。
- 去重入口。
- transcript 标准化输出。
- Phase 2 行标注、作者baseline、高低表现对比。
- evidence record 证据记录。
- Phase 3 skill / anti-skill 卡片。
- composition plan 组合计划。

这些能力适合迁移成小说生产系统的底座。

## 不能直接迁移的部分

短视频文案和长篇小说的差异很大：

- 短视频文案通常几百字，主要看钩子、节奏、观点和表达。
- 长篇小说几十万字，核心是人物一致性、伏笔回收、节奏曲线、情绪递进和读者追读。
- 文案去AI味可以靠局部改写；小说去AI味必须靠长篇结构和持续一致性。

因此，小说系统不是简单增加“生成章节”脚本，而是要增加长篇状态管理和原创性风控。

## 建议新增模块

1. 爆款样本库

收集平台公开样本、榜单、推文、书评、短视频讲书内容。目标是提炼通用结构规律，不复制具体桥段、人设、设定、台词和文风。

2. 题材路线分析器

分析题材、目标读者、开篇钩子、爽点类型、章节密度、推荐平台。

3. Story Bible 管理器

维护人物、人设、关系、世界观、战力、伏笔、禁用桥段、阶段目标。

4. Style Bible 管理器

维护整体语气、叙述距离、句子节奏、对话规则、禁用AI腔、偏好写法和人类修改样本。它决定正文是否像同一个人写，而不是默认AI腔。

5. 长篇记忆管理器

维护 `project_state.json`、章节摘要、人物状态、伏笔列表、未解决冲突和 `context_pack`。每章写前加载最小必要记忆包，每章写后更新状态，避免长篇后期遗忘前文。

6. 本地知识库检索器

维护章节全文、摘要、人物事件、伏笔事件、审稿结果、平台规则和 skill 的本地索引。第一阶段建议使用 SQLite + FTS5，后续再加入向量检索做语义相似和桥段相似检查。

7. 结构 Skill 蒸馏器

从公开样本中提炼题材、开篇、章节、冲突、爽点、追读、反转等通用机制。输出必须经过原创性剥离，不能保留具体桥段和标志性表达。

8. 文笔 Skill 蒸馏器

沉淀动作替代情绪、对话压迫感、描写密度、句子节奏等文笔规则。来源应以人类修改记录和通用写作技巧为主，不模仿具体作者。

9. 章节策划器

每章先生成章节策划卡，让AI说明本章目的、节奏、情绪、风险和需要人类确认的问题。

10. 人类决策记录器

记录人类对AI方案的选择、否决、修改意见和最终采纳理由。

11. 正文生成器

根据确认后的章节策划卡生成正文草稿。

12. 风控审稿器

检查AI味、低质模板、重复桥段、人物崩坏、伏笔遗漏、洗稿/相似风险、平台敏感风险。

13. 发布复盘器

记录章节数据、读者反馈、推荐变化，用于下一章节奏调整。

## 完整闭环

```text
平台风控层
↓
公开样本观察层
↓
结构 skill 蒸馏层
↓
Story Bible 故事圣经
↓
Style Bible 文风圣经
↓
本地知识库检索
↓
Context Pack 长篇记忆包
↓
章节策划卡
↓
人类讨论确认
↓
AI生成草稿
↓
结构审稿 + 文笔审稿 + 风险审稿
↓
人类验收
↓
发布复盘
↓
反哺 skill / anti-skill / style bible
```

## 建议目录结构

```text
novel_runtime/
  projects/
    project_id/
      story_bible.yaml
      style_bible.yaml
      project_state.json
      platform_strategy.yaml
      outline/
      structure_skills/
      prose_skills/
      chapter_cards/
      context_packs/
      chapter_summaries/
      memory/
      knowledge_base/
        source_docs/
        sqlite/
        rag_index/
      drafts/
      revisions/
      final/
      human_decisions/
      risk_reports/
      publish_logs/
```

## 建议新增数据结构

章节策划卡：

- chapter_id
- project_id
- platform
- chapter_goal
- reader_emotion_curve
- conflict_unit
- plot_beats
- cliffhanger
- do_not_do
- human_questions
- approved_by_human

人类决策记录：

- decision_id
- chapter_id
- proposed_options
- selected_option
- rejected_options
- human_reason
- ai_revision_instruction
- final_acceptance_note

长篇记忆包：

- project_core
- recent_context
- character_state
- continuity_constraints
- style_constraints
- chapter_task
- avoid_this_chapter

风控报告：

- chapter_id
- ai_tone_score
- repetition_signals
- similarity_signals
- character_consistency_issues
- plot_logic_issues
- platform_policy_risks
- required_fixes

## 难度判断

技术难度：中高。

最难的不是生成正文，而是：

- 长篇记忆不乱。
- 不同章节节奏不重复。
- 人物动机持续可信。
- 不像模板化AI文。
- 不落入洗稿或桥段相似。
- 能保存完整创作证据链。

如果只做“AI生成章节”，难度不高，但商业风险大。如果做“数据策划 + 人类决策 + AI执行 + 风控证据链”，难度更高，但更适合长期做。
