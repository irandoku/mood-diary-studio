# Architecture

## Layers

```text
Daily account or character evidence
                |
                v
       Mood Diary Studio
       - editorial decisions
       - character governance
       - style governance
       - output contracts
                |
                v
    Model-neutral artifacts
                |
                v
 Optional downstream image system
```

The framework owns editorial reasoning and review gates. It does not own image rendering, host storage, or private character identity.

## Guardrails and degrees of freedom

The framework uses low freedom only where a mistake changes authority or data:

- evidence and scene status;
- approved identity and canonical-role changes;
- stored style policy versus per-entry style;
- date and text authorization;
- storage capability, availability, and persistence; and
- review, write, update, and delete approval.

It keeps high freedom where several results can be equally valid:

- emotional wording;
- presence of a non-text theme carrier for a concrete topic (hard invariant);
- choice and arrangement of those carriers (high freedom);
- composition and negative-space treatment;
- supporting cues at narrative-appropriate density;
- visual-budget profile selection when the reported counts fit; and
- model-neutral prompt phrasing.

This boundary prevents validation from overfitting one stochastic model sample.
Acceptance tests evaluate semantic and governance invariants, not exact output
strings. Model variation becomes actionable only when it reproducibly crosses a
boundary or changes a downstream operation.

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

## Identity and style

Character schema v2 keeps identity and rendering style separate:

```text
Identity policy                 Style policy
- immutable anchors            - reference-guided
- flexible attributes          - diary-default
- contextual variants          - user-selected
- forbidden drift              - per-entry
```

Style guidance is soft, portable, and overridable per entry. It must not become
an immutable identity anchor merely because a reference image has a distinctive
medium, line treatment, palette, or texture. V1 cards remain readable and have
no inferred long-term style policy.

## Availability and persistence

Storage state has two dimensions:

```yaml
availability_state: in-context
persistence_state: host-saved
```

This prevents a project source, Library file, chat attachment, runtime path, and
persistent character-pack installation from being treated as equivalent.
`runtime-filesystem` is task-scoped. `account-library` and `managed-project`
may be host-saved, but only an approved persistent pack that was re-read can be
`pack-installed`.

## Public and private separation

The public repository contains the framework, schema, templates, tests, and one original sample. Private character packs remain in user-controlled locations outside the public repository and its Git history.

No default path is prescribed. The host or user supplies the pack location at use time.
