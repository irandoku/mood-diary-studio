# Style Guidance

Keep rendering style separate from character identity. A character may remain
recognizable across different media, line treatments, palettes, and levels of
detail.

## Policy

Record style guidance in `character.md`:

```yaml
style:
  policy: diary-default
  source: framework-default
  guidance: []
  strength: soft
  per_entry_override: allowed
  conflicts: []
```

Allowed policies:

- `reference-guided` — softly follow user-approved, non-identity rendering
  qualities observed across coherent references;
- `diary-default` — use the current diary brief's focused editorial grammar
  without imposing a fixed rendering aesthetic;
- `user-selected` — use generic style guidance explicitly supplied or approved
  by the user;
- `per-entry` — store no long-term default and decide in each DIARY task.

`strength` is always `soft`. Do not promise that a host image system will obey
style guidance or preserve exact identity.

`per_entry_override` is `allowed` by default. It may be
`requires-approval` only after the user explicitly chooses that governance
rule. Do not use `forbidden`; a soft style policy is not a rendering lock.

## Evidence and provenance

Style observations use the same evidence discipline as identity observations,
but they do not become identity anchors. Record:

- the authorized source;
- whether the observation is direct, inferred, conflicting, or unknown;
- whether several references share the treatment;
- limitations caused by scene lighting, medium, compression, or host rendering.

Do not name or imitate a living artist. Prefer portable descriptions of medium,
line, shape language, palette behavior, texture, and visual density.

## Selection

- Default to `diary-default` when the user does not request a long-term style.
- Require explicit approval for `reference-guided` or `user-selected`.
- Require explicit approval for `per_entry_override: requires-approval`.
- Use `per-entry` when references conflict or the character must travel across
  substantially different scenes and media.
- Let the current DIARY request override stored guidance unless the card
  explicitly records `per_entry_override: requires-approval`.
- Resolve the effective entry style in this order: an allowed explicit
  current-entry request, approved stored guidance, then the fallback baseline
  below when neither supplies a more specific treatment.

`diary-default` is not a rigid house style or identity anchor. When neither the
current entry nor the approved card supplies a more specific rendering
treatment, use this flexible, portable bright-neutral diary baseline:

- delicate, restrained linework;
- transparent, low-chroma pale color accents;
- clean cool-white or neutral-white paper;
- bright neutral daylight;
- pale blue-gray or neutral-gray shadows; and
- localized natural material colors where the scene calls for them.

Adapt the baseline to the scene hierarchy and medium, and keep it soft rather
than treating it as a rendering lock. Do not silently apply a full-frame
yellow-brown or nostalgic wash, thick uniform outlines, or any named visual
style. The baseline changes only the effective entry style; it never revises
the approved stored policy or weakens identity anchors. Report its source as the
framework's style-guidance fallback, not as a user-selected stored policy.

Control focus through value, color, detail, and spatial hierarchy rather than
by removing the setting or applying a global muted filter.

## DIARY reporting

Report long-term card state separately from the style used for the current
entry:

- **Stored style policy** — copy the approved card's `style.policy` exactly.
  For a v1 card with no style block, report the compatibility policy
  `per-entry`.
- **Stored override rule** — copy the approved card's
  `style.per_entry_override`; for v1 compatibility, use `allowed`.
- **Effective entry style** — describe the medium, rendering treatment, and
  guidance actually selected for this DIARY result, with its source.

A style request made inside a DIARY task changes only the effective entry
style. It never changes or renames the stored policy. In particular, do not
report `user-selected` as the stored policy merely because the user requested
cut-paper, watercolor, ink, or another treatment for the current entry.
`user-selected` becomes a stored policy only after explicit long-term policy
approval in ONBOARD or AUDIT.

## Causal boundary

Do not attribute an output style to the character card without controlled
evidence. Separate the possible influence of:

- reference-image conditioning;
- the final prompt;
- the host image model and its defaults;
- character-card text;
- current scene and composition requirements.

Report observable differences without claiming which source caused them.

## Drift boundary

Identity drift and style drift are separate:

- identity drift changes who the character is;
- style drift changes how the approved character is rendered for the current task.

Never sacrifice immutable identity anchors merely to satisfy style guidance.
