---
name: novel-blind-forensic-review
description: Use when running blind three-find-one review for clean-room web-novel chapters or openings. Triggers include 小说盲审, 三找一, 单章复刻盲测, clean-room chapter review, source-confusion check, AI水文诊断, and chapter forensic review.
---

# Novel Blind Forensic Review

Use this skill to test whether a clean-room novel chapter behaves like a real chapter from the source family without exposing the reviewer to the answer key.

## Core Rule

Blind review is a diagnostic microscope, not a production license.

Passing means:

```text
The current packet did not get exposed in this blind set.
```

It does not mean:

```text
The draft is publishable.
The source can be copied.
The route is validated.
```

## Input Format

Prepare an anonymous packet:

```text
A.md
B.md
C.md
review_prompt.md
answer_key.md
```

The reviewer receives only A/B/C and `review_prompt.md`.

The reviewer must not see:

- answer key
- source title or author
- file paths that reveal source or replica
- diagnostic packet
- evidence notes
- prior reviews
- user expectations

## Review Task

The reviewer answers:

```text
Which one is the odd chapter out?
Why?
Confidence?
If unsure, what are the top two candidates and why?
```

Then diagnose the oddness by layers:

- complete-chapter feel
- opening inherited pressure
- scene movement and scene switch
- paragraph breath
- narrative distance and POV
- action/dialogue/psychology/exposition ratio
- protagonist micro-goal
- obstacle activity
- causality
- information release and flip
- payoff and changed state
- chapter-ending hook
- prose texture
- AI-water smell
- source-similarity or content-shape risk

## Required Output

Use this format:

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
- ...

相似风险：
- hard_risk / soft_risk / low / unknown

AI水文风险：
- high / medium / low

下一步建议：
- return_to_source_evidence / revise_packet / rerun_writer / stop
```

Do not suggest copying source phrases or content shapes.

## Failure Interpretation

If the replica is caught:

- Treat the review as calibration evidence.
- Identify the most likely failed layer.
- Reopen source chapters before changing the diagnostic packet.

If an original is caught instead:

- Check whether source chapters were unfairly matched.
- Check whether the selected source chapters came from different route, volume phase, or renderer.
- Do not automatically declare the replica successful.

If the reviewer is uncertain:

- Record which layers were indistinguishable.
- Record which layers still showed risk.
- Run a second packet with different source chapters if the result matters.

## Similarity Risk Gate

Flag `hard_risk` if the replica appears to reuse:

- role identity combinations
- specific ability mechanics
- organization names or structures
- monster/anomaly rules
- scene sequence
- signature reveal or famous moment
- high-identification prose

Flag `soft_risk` if the replica does not copy directly but would make readers say it feels like the same book, author, or trend-chasing shell.

Hard risk stops the loop. Soft risk requires packet repair before any production use.

