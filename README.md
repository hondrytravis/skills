# Facet

**The last gate before the spec gets written.** Facet stress-tests your draft design — one sharp question at a time — then hands you a structured brief that feeds directly into openspec or speckit. No chat-scrolling. No "let me summarize."

## Install

```bash
# All skills from this repo
npx skills@latest add hondrytravis/skills

# Just Facet
npx skills add https://github.com/hondrytravis/skills --skill facet
```

## What makes it different

Most design-review skills stop at "shared understanding." Facet goes further with a **structured artifact** — the Facet Brief — that maps onto spec tooling without a translation step.

| Capability | grill-me | grill-with-docs | brainstorming | **Facet** |
|---|---|---|---|---|
| Grill an existing draft | ✅ | ✅ | ❌ | ✅ |
| Structured SDD output | ❌ | ❌ | ❌ | ✅ |
| Silent-failure probing | ❌ | ❌ | ❌ | ✅ |
| Verify claims against code | partial | partial | ❌ | ✅ |
| Early exit, resume later | ❌ | ❌ | ❌ | ✅ |
| Update project docs | ❌ | ✅ | ❌ | ❌ |
| Generate design from nothing | ❌ | ❌ | ✅ | ❌ |

> Facet is not a design generator. You bring the draft — even three sentences. Facet takes it from 0.7 to 0.95 before the spec crystallizes.

## How it works with openspec

```
rough draft  →  facet  →  Facet Brief  →  openspec  →  code
```

### Walkthrough

You walk in with a draft:

> *"Notification system. Users get notified on @mentions. Email + in-app. Done."*

Facet grills it, one question at a time:

> *"If the email provider is down for 30 seconds, does the in-app notification still fire — or does one failure block the other?"*

> *"Three comment types exist in the codebase: inline reviews, issue comments, PR threads. Which ones trigger a notification?"*

> *"Write succeeds but the notification queue write fails silently — does the comment still appear? Who discovers the gap? How soon?"*

After 8–12 rounds, Facet hands you a Brief. Drop it into openspec:

```
openspec/
├── changes/
│   └── notification-system/
│       ├── proposal.md    ← Facet "Conclusion" + "Evidence"
│       ├── design.md      ← Facet "Weak points" + "Rejected approaches" + "Risks"
│       └── tasks.md       ← Facet "Next steps"
```

No synthesis. No re-typing. Brief → spec artifacts in one pass.

## The skill

- **[facet](./skills/facet/SKILL.md)** — triggers: `facet`, `pressure-test this plan`, `stress-test the design`

## Structure

```
skills/<name>/SKILL.md          ← English skill (shipped)
reference/<name>/SKILL.zh.md    ← Chinese original (reference only)
```

Every skill needs a reference in this README and an entry in `.claude-plugin/plugin.json`.



