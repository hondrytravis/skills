# Facet

**The last pressure-test before you write a spec.** Facet grills your draft design — one sharp question at a time — then hands you a tight Facet Brief that maps directly into your SDD tool.

```bash
npx skills@latest add hondrytravis/skills
```

## Why Facet

Most design-review skills stop at "shared understanding." Facet goes further — it produces a **structured artifact** (Facet Brief) that feeds directly into openspec or speckit. No re-reading chat history. No "let me summarize what we talked about."

What sets Facet apart:

| Capability | grill-me | grill-with-docs | brainstorming | **Facet** |
|---|---|---|---|---|
| Grill a draft design | ✅ | ✅ | ❌ (generates from scratch) | ✅ |
| Structured output for SDD | ❌ | ❌ | ❌ (produces a spec) | ✅ **Facet Brief** |
| Silent failure probing | ❌ | ❌ | ❌ | ✅ |
| Verify every claim against code | partial | partial | ❌ | ✅ **instant** |
| Resumable early exit | ❌ | ❌ | ❌ | ✅ **Facet Quick Note** |
| Update project docs | ❌ | ✅ | ❌ | ❌ (read-only) |
| Generate design from nothing | ❌ | ❌ | ✅ | ❌ |

> **Facet is not a design generator.** You bring a draft (even 3 sentences). Facet pressure-tests it. brainstorming helps you go 0→1; Facet takes you from 0.7→0.95 before the spec crystallizes.

## Workflow with openspec

```
rough draft → facet → Facet Brief → openspec → code
```

### Example

Start with a draft:

> "We need a notification system. Users get notified when someone mentions them in a comment. Email + in-app. That's it."

Run `facet` (trigger: "facet this plan"). Facet grills:

> *"If the email provider is down for 30 seconds, does the in-app notification still go through? Or does one failure block the other?"*

> *"You said 'mention in a comment' — but the codebase has three comment types: inline review comments, issue comments, and PR thread comments. Which ones trigger notifications?"*

> *"Write succeeds, but the notification queue write silently fails — does the comment still appear? Who discovers the missing notification?"*

After 8-12 rounds, Facet outputs a Brief. Here's how it maps to openspec:

```
openspec/
├── changes/
│   └── notification-system/
│       ├── proposal.md    ← Facet "Conclusion" + "Evidence"
│       ├── design.md      ← Facet "Weak points" + "Rejected approaches" + "Risks"
│       └── tasks.md       ← Facet "Next steps"
```

The Brief becomes your openspec change in one step — no translation layer, no lost context.

## Skill

- **[facet](./skills/facet/SKILL.md)** — Full skill definition. Triggers: "facet", "pressure-test this plan", "stress-test the design".

## Reference

Each skill lives in `skills/<name>/SKILL.md` and must have a reference in this README and an entry in `.claude-plugin/plugin.json`.


