---
name: novel-chapter-distiller
description: Use when extracting, synthesizing, or running clean-room diagnostics for a single web-novel chapter. Triggers include 单章复刻, 小说章节提取, 单章证据, 章节正文身体, clean-room 写一章, chapter diagnostic packet, and updating a chapter-level novel distillation packet.
---

# Novel Chapter Distiller

Use this skill to turn source chapters into a diagnostic packet that can generate one complete clean-room chapter and be tested by blind review.

## Core Rule

The replication object is not a label, outline, route, or style note.

```text
单章复刻稿 = 一章完整小说正文。
```

The generated chapter must be long enough and continuous enough to sit anonymously beside two source chapters in a three-find-one blind review. It tests whether the packet captures chapter-level prose movement, not whether the agent can summarize a plot.

## Borrowed From Short-Video Distillation

Keep the same loop:

```text
source-open reading
-> evidence extraction
-> diagnostic packet synthesis
-> clean-room full-chapter drafting
-> three-find-one blind review
-> failure diagnosis
-> return to source evidence before updating packet
```

Do not update rules from reviewer opinion alone. Blind review diagnoses a missing or misweighted behavior; source chapters must confirm it.

## Required Inputs

- source book id, title, platform, and source path or reading notes
- target chapter number and neighboring chapters
- chapter text or safe structural reading notes outside Git
- known prohibited similarities
- target diagnostic goal: style-body / chapter-motion / reveal / obstacle / editor-readability / mixed

If only P2 summaries exist, mark the packet as `summary_based`. Do not claim full chapter fidelity.

## Source-Open Scope

For one target chapter, read:

```text
previous chapter
target chapter
next chapter
```

If testing opening-chapter replication, read:

```text
intro
chapter 1
chapter 2
chapter 3
```

Record what the target chapter inherits from the previous chapter and what pressure it sends into the next chapter.

## Extract These Fields

### Chapter Body

- `chapter_entry`: what state the chapter enters from
- `scene_count`: how many scenes or beats
- `scene_switch`: how scenes switch
- `paragraph_breath`: paragraph length, density, pause rhythm
- `narrative_distance`: close inner view, external camera, or narrator explanation
- `action_dialogue_psychology_ratio`: rough balance of action, dialogue, inner thought, exposition
- `exposition_method`: how setting/rules enter action instead of becoming encyclopedia text
- `chapter_exit`: what exact pressure, question, action, or image closes the chapter

### Movement

- `protagonist_micro_goal`: what the protagonist tries to do in this chapter
- `trigger_event`: what starts the chapter
- `conflict_unit`: the concrete conflict unit of the chapter
- `opposition_micro_action`: what the obstacle actively does
- `information_release`: what new information is released, withheld, or reframed
- `payoff_type`: survival, power, status, money, relationship, clue, reveal, face-slap, or dread
- `resource_power_delta`: what resource, power, permission, item, money, clue, or capability changes
- `visibility_legitimacy_delta`: who now knows, misreads, legitimizes, suspects, or publicly recognizes the protagonist
- `ending_hook`: why the reader clicks the next chapter

### Language Renderer MVP

- `sentence_texture`: sentence length, verb force, abstraction level
- `dialogue_texture`: how characters speak, interrupt, conceal, or explain
- `inner_voice`: how much self-talk, emotion, calculation, sarcasm, or fear
- `description_texture`: physical action, sensory detail, worldbuilding, fight detail, anomaly detail
- `rhythm_defects`: source-natural roughness that should not be over-polished
- `ai_slop_alarm`: phrases or moves that would make the draft feel generic, inflated, or AI-water-like

### Boundary

- `prohibited_shapes`: roles, abilities, organizations, monsters, rules, named scenes, scene order, high-identification lines
- `transferable_mechanisms`: abstract moves that can be used safely
- `risk_notes`: hard and soft similarity risks

## Synthesize A Diagnostic Packet

The packet must be executable by a clean-room writer. It should include:

```text
source_scope
target_chapter_role
chapter_entry_contract
beat_count_and_scene_shape
micro_goal_and_conflict
opposition_behavior
information_release_plan
payoff_and_delta_rules
chapter_exit_hook
minimum_language_renderer
prohibited_shapes
editor_gate_notes
validation_gate
```

Write rules as actions, not essays.

Bad:

```text
文风紧张，节奏好。
```

Better:

```text
Use short action paragraphs during danger, then one close inner-thought beat after the new rule is discovered. Do not explain the rule before the protagonist tests it.
```

## Clean-Room Writer Rules

The writer may read:

- the diagnostic packet
- the invented chapter brief
- house style constraints, if provided
- prohibited-shape list

The writer must not read:

- source chapter text
- source quotes
- source chapter order beyond the abstract packet
- evidence map
- answer key
- blind-review feedback from previous rounds unless it has been confirmed by source evidence

The writer must output one complete chapter, not an outline or excerpt.

## Self-Check Before Blind Review

Reject the draft before blind review if:

- it is only a summary or scene outline
- it copies source roles, powers, organization, monster, rule, or scene order
- the chapter has no protagonist micro-goal
- the obstacle does not act
- the ending hook is only a generic cliffhanger
- language feels like an explanation of the packet
- editor gate flags hard similarity or obvious AI-water risk

## Failure Diagnosis

When blind review catches the replica, classify failure by layer:

```text
chapter_object_failure: not a complete chapter
entry_exit_failure: wrong inherited pressure or ending hook
scene_body_failure: scene count, switch, or paragraph breath wrong
narrative_distance_failure: wrong POV distance or inner voice
causality_failure: events adjacent but not forced
opposition_failure: obstacle passive or fake
reveal_failure: information released too early, too late, or without consequence
payoff_delta_failure: no resource/status/visibility change
renderer_failure: prose texture wrong
editor_quality_failure: AI-water, low readability, or platform mismatch
similarity_failure: too close to source content shape
```

Update the diagnostic packet only after reopening source evidence for the failed layer.

