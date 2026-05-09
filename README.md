# xiaoshuo-writedonw

Fiction distillation and commercial web-novel planning workspace.

Current scope is intentionally narrow. Phase 1 only builds the foundation for
novel-side research and repeatable creation workflows:

1. novel distillation thinking and schema drafts
2. corpus / evidence organization rules
3. route-aware author and book modeling
4. clean-room replication discipline
5. validation standards for readability, likeness, and continuation drive

This repository does not need to solve the whole writing system on day one.
The goal is to make later novel research, planning, drafting, and review
version-controlled and reproducible, the same way `douyin-wenan` did for short
video script work.

## Initial Layout

```text
.agents/    skills and runtime author/source packages
docs/       architecture notes, migration docs, and schemas in prose
data/       repo-safe fixtures and small examples only
research/   route tables, sample matrices, and working notes
schemas/    structured templates for novel distillation
scripts/    CLI utilities and batch helpers
src/        library code if/when the pipeline becomes executable
tests/      validation and regression tests
```

## Phase 1 Goals

1. define the novel distillation object clearly
2. separate author-layer and book-layer modeling
3. define multi-granularity analysis:
   - book
   - arc / volume
   - chapter
   - scene
4. define validation beyond likeness:
   - continuation drive
   - false-reveal detection
   - pacing drop points

## First Documents

- `docs/01_小说蒸馏迁移思考.md`
- `docs/02_前期规划目录优化建议.md`
- `docs/前期规划/`

## Repository Rules

- Do not commit large raw manuscript corpora by default.
- Keep repo content to docs, schemas, scripts, fixtures, and small examples.
- Treat external corpora as source inputs, not as Git payloads.
- Prefer clean-room drafting and evidence-backed updates over ad hoc prompting.
