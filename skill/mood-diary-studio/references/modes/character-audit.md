# AUDIT Mode

Compare an existing approved character card with new user-authorized evidence. Produce a change proposal, not an automatic rewrite.

## Inputs

Require:

- the existing `character.md`;
- new reference images, user-provided facts, or a proposed revision;
- the storage binding that supplies the current card;
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
2. storage profile, locator, and write capability;
3. unchanged anchors;
4. additions;
5. contextual variants;
6. conflicts and their impact;
7. proposed patch;
8. items deliberately left untouched;
9. questions requiring user authority;
10. `update_status: not-applied`.

Use `assets/templates/audit-result.md`.

Apply a revision only after the user approves the patch and exact writable target. Never update bundled samples as a substitute for a private card. Re-read the saved file and report what changed. Never overwrite a different character or substitute another destination.
