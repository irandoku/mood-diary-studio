# Mood Diary Studio

[台灣繁體中文](README.zh-TW.md) | English

Mood Diary Studio is a portable Agent Skill for making character-led mood diary illustrations. It acts as an editorial decision framework: it extracts an emotional center from a daily account, removes competing events, plans a low-density composition, applies an approved character card, and produces a model-neutral image prompt.

It also drafts and audits data-only character plugins without embedding private characters in the public framework.

## What makes it different

A generic prompt generator expands a description. Mood Diary Studio decides what to omit.

It coordinates:

- emotional-center selection;
- narrative reduction;
- visual-budget enforcement;
- meaningful negative space;
- character-card governance;
- date and short-text handling; and
- identity and composition drift review.

## Modes

- **DIARY** — daily account to emotional center, composition brief, and prompt.
- **ONBOARD** — visual references to a candidate `character.md`, with confirmed, inferred, and unknown evidence kept separate.
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
Use mood-diary-studio in DIARY mode. Turn this daily account into a restrained
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
