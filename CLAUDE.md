# Facet Skills

SDD-focused agent skills. Each skill stress-tests one phase of the spec-to-code pipeline.

## Structure

```
skills/<name>/SKILL.md          ← English skill definition (shipped)
reference/<name>/SKILL.zh.md    ← Chinese original (reference only, not distributed)
```

## Adding a skill

1. Create `skills/<name>/SKILL.md`
2. Add an entry in `README.md` linking to it
3. Add an entry in `.claude-plugin/plugin.json`
4. Run `scripts/list-skills.sh` to verify

## Conventions

- Skills are read-only — they don't create or update project docs
- Every skill outputs a structured artifact, not just a conversation
- Reference translations are kept for authorship provenance, not shipped

