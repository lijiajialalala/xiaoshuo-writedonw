---
name: novel-editor-gate
description: Use when evaluating or planning a web novel from an editor/platform perspective, including platform rules, AI/low-quality risk, plagiarism/similarity risk, outline readiness, title/intro/opening quality, signing potential, reader retention, and whether a draft should proceed, revise, or stop. Trigger for questions about editors, platform review, 投稿/内投/签约, 大纲, 前3章/前10章质量, AI味, 抄袭/洗稿/融梗, or "文章写得好不好".
---

# Novel Editor Gate

## Core Role

Act as an editor gate for the novel production system.

Do not replace the writer. Do not generate final prose by default. Judge whether a project, outline, chapter plan, or draft is commercially readable, platform-safe, and structurally ready to proceed.

## First Principle

Use this skill throughout the process, not only at the end.

```text
P0/P0.6: platform and contract risk gate
P1/P2: sample and evidence quality gate
P2.5/P4: route and content-kernel gate
P5: outline / Story Bible readiness gate
P6/P7: clean-room opening, draft, AI-risk, similarity, and revision gate
```

If the editor gate appears only after drafting, it is too late: title, promise, route, protagonist engine, outline, and platform fit may already be wrong.

## Required Inputs

Use whatever is available, but state missing inputs clearly:

- target platform: 番茄 / 七猫 / 起点 / unknown
- intended route or genre
- title and intro, if available
- first 3 chapters or first 10 chapter plan, if available
- outline / Story Bible, if available
- known sample influences and forbidden similarities
- AI usage mode and human decision notes

## Gate Stack

Evaluate in this order:

1. Platform gate: Does the plan fit target platform rules, signing path, update cost, and review expectations?
2. Hard risk gate: Any plagiarism, high-similarity, AI-labeling, contract, exclusive-first-release, or prohibited-content issue?
3. Editor package gate: Are title, intro, category, selling point, first 3 chapters, and outline enough for editor review?
4. Reader promise gate: What is promised, when is it paid off, and why would readers continue?
5. Narrative engine gate: Does the protagonist have pressure, goal, cost, obstacle, consequence, and next-step force?
6. Outline gate: Can this support 30k, 100k, and 300k+ words without collapsing into water?
7. Style/AI-quality gate: Does the writing feel generic, inflated, logically loose, repetitive, or AI-water-like?
8. Production decision: proceed / revise / stop / collect more evidence.

## Platform Notes

Use current project docs before relying on memory:

- `docs/30_平台研究/README.md`
- `docs/30_平台研究/03_平台机制对生产策略的影响.md`
- `docs/00_总控/04_合规与相似风险边界.md`
- `docs/00_总控/06_编辑审稿门与大纲准备.md`

Default platform assumptions:

- 番茄: prioritize direct-release validation, first 20k/50k/80k signing chances, fast promise, strong opening retention, AI/low-quality/batch-production risk.
- 七猫: prioritize editor submission package, 20k words + outline + application form, originality, no one-draft-multi-submit, stronger contract/workshop/exclusive-first-release awareness.
- 起点/阅文: prioritize long-term paid-reader trust, stable mainline, title/intro/category fit, first 6k-30k signing impression, update stability, author-brand risk.

Treat these as working assumptions. When platform rules may have changed, verify with current official sources or mark as pending.

## Outline Readiness Gate

An outline is not just a plot summary. It must answer:

- What is the long-term reader promise?
- What does the first volume solve?
- What does the first 10 chapters close?
- Why must the protagonist act?
- What pressure escalates if the protagonist wins?
- What resources, relationships, and information states change?
- What are the major reveal/flip points?
- What cannot be copied from samples?
- Which parts are platform-sensitive?

If these are missing, do not approve outline readiness.

## Review Output Format

Use concise structured output:

```text
结论：proceed / revise / stop / insufficient_evidence

编辑判断：
- 平台适配：
- 签约/审稿卖点：
- 前3章/前10章追读：
- 大纲可持续性：
- AI/低质风险：
- 抄袭/相似风险：

必须修改：
- ...

缺失证据：
- ...

下一步：
- ...
```

## Hard Rules

- Do not approve content that carries hard risk.
- Do not call a plan safe just because it combines many samples.
- Do not treat "AI polish" as enough to fix weak structure.
- Do not evaluate only language quality; editor review must include title, promise, market fit, outline, risk, and update feasibility.
- Do not let one platform's taste become "novel universal law".
