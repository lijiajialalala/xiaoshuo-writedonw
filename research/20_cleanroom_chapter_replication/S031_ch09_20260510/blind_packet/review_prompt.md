# Blind Review Prompt：小说单章三找一

你会看到 A、B、C 三章。

其中两章是同一来源家族的原文相邻章节或近似章节，一章是 clean-room 复刻稿。

你的任务：

```text
找出哪一章是异类。
```

不要判断哪章“更好看”。判断哪章更不像另外两章的来源家族。

## 输出格式

```text
结论：A / B / C / uncertain
置信度：high / medium / low

异类判断：
- ...

另外两篇更像的原因：
- ...

暴露指纹：
- ...

失败层级：
- complete_chapter_feel:
- opening_inherited_pressure:
- scene_movement:
- paragraph_breath:
- narrative_distance:
- action_dialogue_psychology_exposition_ratio:
- protagonist_micro_goal:
- obstacle_activity:
- causality:
- information_release_or_flip:
- payoff_and_changed_state:
- chapter_ending_hook:
- prose_texture:
- ai_water_smell:
- source_similarity_risk:

相似风险：
- hard_risk / soft_risk / low / unknown

AI水文风险：
- high / medium / low

下一步建议：
- return_to_source_evidence / revise_packet / rerun_writer / stop
```

注意：

```text
如果你怀疑某章是 AI 写的，说明具体暴露点。
如果你觉得两章原文也不像同一来源，说明盲审包可能不公平。
不要建议复制原文口癖、桥段或设定。
```

