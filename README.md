# Mood Diary Studio

[台灣繁體中文](README.zh-TW.md) | English

Mood Diary Studio is a portable Agent Skill for making character-led mood diary illustrations. It acts as an editorial decision framework: it extracts an emotional center from a daily account, preserves non-text cues for any concrete topic, removes competing events, plans a focused composition whose density follows the narrative need, applies an approved character card, and produces a model-neutral image prompt.

It also drafts and audits data-only character plugins without embedding private characters in the public framework.

## What makes it different

A generic prompt generator expands a description. Mood Diary Studio decides what to omit.

It coordinates:

- emotional-center selection;
- narrative reduction;
- visual-budget enforcement;
- meaningful negative space;
- character-card governance;
- quick, guided, and advanced onboarding review;
- separate identity and style governance;
- date and short-text handling; and
- identity and composition drift review.

DIARY may also select the optional `bright-fine-line-gongbi-diary` treatment:
cool-white paper, precise fine colored linework, transparent pale watercolor,
localized light shadows, and restrained hand-diary composition. It is a visual
treatment, not character identity or a stored character policy.

## Guardrails with creative room

Mood Diary Studio standardizes governance outcomes, not every sentence or
composition choice. Source status, approved identity, stored style policy,
date authority, storage state, and write approval are hard boundaries.
Emotional phrasing, scene treatment, supporting cues, and prompt wording may
vary when they remain inside those boundaries.

Acceptance therefore checks invariants rather than exact prose. A compliant
variation is expected model behavior; a repeatable violation that changes
facts, identity, authority, or persistence is a framework defect.

## Modes

- **DIARY** — daily account to emotional center, composition brief, and prompt.
- **ONBOARD** — visual references to a candidate `character.md`, with
  risk-based quick, guided, or advanced review.
- **AUDIT** — existing character card plus new evidence to a reviewable change proposal.

ONBOARD and AUDIT never install or revise character data without explicit user approval.

## Install the skill

Install or copy the complete folder:

```text
skill/mood-diary-studio/
```

Keep `SKILL.md`, `references/`, and `assets/` together. The repository root contains project documentation and tests; it is not the installable skill folder.

Then ask a compatible agent:

```text
Use mood-diary-studio in DIARY mode. Turn this daily account into a focused
character-led mood diary brief and a model-neutral image prompt.
```

## Character plugins

A character plugin is a data folder, not executable code:

```text
paper-dot/
├── character.md
└── references/
    └── front.png
```

The public repository includes one original, generic sample only. Keep personal character packs outside this repository. See [Private Character Packs](docs/private-character-packs.md).

`assets/sample-character/` is a read-only public fixture. Never use it as the destination for a private or newly onboarded character.

New candidates use `mood-diary-character/v2`, which separates immutable
identity from soft style guidance. Existing v1 cards remain readable and can be
migrated only through an approved AUDIT proposal. The bundled Paper Dot card
intentionally remains a v1 compatibility fixture; the v2 candidate templates
demonstrate the current schema.

## Where private characters live

The framework defines a character pack's structure but deliberately does not hardcode one universal directory. Each host supplies a storage binding:

| Storage profile | Typical use | Persistence |
|---|---|---|
| `bundled-assets` | Public samples shipped with the Skill | Skill-scoped and read-only |
| `local-filesystem` | Local agents with an approved pack path | Persistent local files |
| `workspace-files` | A controlled agent workspace | Workspace scoped |
| `managed-project` | A web project or managed knowledge area | Host managed |
| `account-library` | An account or workspace file library | Account scoped |
| `runtime-filesystem` | A task VM or temporary sandbox | Task scoped |
| `chat-attachments` | One conversation | Chat scoped |
| `manual-export` | No writable storage | User saves the returned artifact |

For a local agent, explicitly name the private pack:

```text
Use mood-diary-studio in ONBOARD mode. After review, install the approved
character into /exact/user-selected/mood-diary-characters.
```

For a web host without local-directory access, attach the reference image and
use ONBOARD normally. A new candidate is normally `in-context` and
`export-ready`. After the exact artifact is verified in a project or account
library it may be `host-saved`, but it is not `pack-installed`. A task VM stays
`transient` until persistence across a clean task is actually verified.

See [Private Character Packs](docs/private-character-packs.md) for complete local, workspace, and web-host workflows.

## Agent-neutral by design

The installable skill uses the open Agent Skills layout and requires no scripts, package manager, network service, MCP server, image model, or vendor-specific runtime metadata.

A compatible host needs to:

- discover or load `SKILL.md`;
- resolve relative reference and asset paths;
- read user-provided text;
- inspect images for ONBOARD or image-based AUDIT;
- return Markdown artifacts; and
- request approval before writing character data.

Hosts without image inspection can still use DIARY mode and must report ONBOARD or image-based AUDIT as unsupported rather than invent observations. See [Compatibility](COMPATIBILITY.md).

## Repository map

- `skill/mood-diary-studio/` — installable portable Skill.
- `docs/` — architecture, private-pack guidance, and validation policy.
- `tests/` — public-safe acceptance scenarios.
- `COMPATIBILITY.md` — capability contract and evidence levels.

## Scope boundaries

Mood Diary Studio does not:

- contain private character universes;
- guarantee exact identity across image generations;
- render images by itself;
- execute character plugins;
- silently write or update character cards; or
- require ChatGPT, Claude Code, Codex, Hermes, or a specific image service.

## License

MIT. The Paper Dot sample and its reference image are original demonstration assets distributed under the same repository license.
