# AUDIT Mode

Compare an existing approved character card with new user-authorized evidence. Produce a change proposal, not an automatic rewrite.

## Inputs

Require:

- the existing `character.md`;
- new reference images, user-provided facts, or a proposed revision;
- the exact target only if an approved update may follow.

Treat the existing card as current policy, not unquestionable visual truth. Treat new references as evidence, not automatic replacement authority.

## Comparison

Classify each relevant item:

- **unchanged** — evidence supports the current card;
- **new evidence** — previously unknown detail becomes observable;
- **contextual variant** — likely outfit, prop, pose, or scene-specific change;
- **candidate evolution** — user intent may be changing canonical design;
- **conflict** — new evidence contradicts an immutable anchor;
- **missing evidence** — the new reference cannot confirm an existing rule;
- **unresolved** — evidence or intent is insufficient.

Absence from one view is not proof of removal.

## Change policy

- Preserve current immutable anchors unless the user explicitly changes canon.
- Do not convert a contextual variant into a permanent rule based on repetition alone.
- Do not delete an anchor because it is occluded.
- Separate wording clarification from design change.
- Preserve history when a canonical decision changes.

## Delivery

Return:

1. audit scope and evidence quality;
2. unchanged anchors;
3. additions;
4. contextual variants;
5. conflicts and their impact;
6. proposed patch;
7. items deliberately left untouched;
8. questions requiring user authority;
9. `update_status: not-applied`.

Use `assets/templates/audit-result.md`.

Apply a revision only after the user approves the patch and exact target. Re-read the saved file and report what changed. Never overwrite a different character or substitute another destination.
