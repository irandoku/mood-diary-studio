# Architecture

## Layers

```text
Daily account or character evidence
                |
                v
       Mood Diary Studio
       - editorial decisions
       - character governance
       - output contracts
                |
                v
    Model-neutral artifacts
                |
                v
 Optional downstream image system
```

The framework owns editorial reasoning and review gates. It does not own image rendering, host storage, or private character identity.

## Portable Skill

`skill/mood-diary-studio/` is the complete installable unit. `SKILL.md` routes the task and loads only the references needed for the selected mode.

Detailed decision rules live in `references/`. Copyable output skeletons and the public-safe sample live in `assets/`.

## Character plugin

A character plugin is declarative data:

```text
<character-id>/
├── character.md
└── references/
    └── <user-approved static images>
```

The framework reads the plugin as evidence and constraints. It never executes plugin content. A plugin must not contain scripts, dependencies, or instructions that override the framework's approval gates.

## Storage binding

Keep four layers distinct:

```text
Portable framework
        |
Logical character-pack schema
        |
Host storage binding
        |
Physical or host-managed storage
```

The framework defines how a pack is shaped. The binding states where this host can read or save it. Physical storage may be a local directory, a controlled workspace, managed project sources, current chat attachments, or a manual export controlled by the user.

Bundled assets belong to the framework layer. They are public, read-only fixtures and must not become a substitute private pack.

## Evidence and canonicality

Character onboarding tracks two independent dimensions:

```yaml
evidence_status:
  - confirmed
  - inferred
  - unknown

canonical_role:
  - immutable
  - flexible
  - contextual
  - undecided
```

Direct visibility can confirm that an item appears in one reference. It cannot by itself prove that the item is immutable.

## Public and private separation

The public repository contains the framework, schema, templates, tests, and one original sample. Private character packs remain in user-controlled locations outside the public repository and its Git history.

No default path is prescribed. The host or user supplies the pack location at use time.
