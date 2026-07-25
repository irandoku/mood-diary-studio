# ONBOARD Mode

Draft a reviewable candidate character plugin from user-authorized references. Never install it automatically.

## Preconditions

Obtain:

- the proposed display name;
- at least one user-authorized reference image or a user-provided visual inventory;
- the intended type: mascot, humanoid, or unresolved;
- a storage binding, or enough context to select `chat-attachments` or `manual-export`;
- the exact candidate-pack target only if installation may follow.

Do not require personality or worldbuilding to begin visual onboarding.

## Reference-quality assessment

Rate the visual evidence:

- **A** — unobstructed full body plus useful secondary view or explicit user facts;
- **B** — clear full-body front or three-quarter view with minor unknowns;
- **C** — partial, obstructed, stylized, or scene-heavy evidence;
- **Insufficient** — identity-relevant features cannot be inspected.

List what is visible and what the references cannot establish. Stop visual analysis when the host cannot inspect the image.

## Evidence extraction

For each observation, record:

- `statement`;
- `evidence_status`: `confirmed`, `inferred`, or `unknown`;
- `source`: a reference filename or `user-provided`;
- `confidence`: `high`, `medium`, or `low`;
- `canonical_role`: `immutable`, `flexible`, `contextual`, or `undecided`.

Use `confirmed` only for a direct, clear observation or explicit user fact. A confirmed appearance in one image may still have `canonical_role: undecided`.

## Observation boundaries

Observe visible presentation without inventing identity. Do not infer:

- personality or moral traits;
- occupation, relationships, or backstory;
- ethnicity, nationality, religion, health, or disability;
- gender identity or sexual orientation;
- exact age;
- whether a visible item is permanent.

Record occluded, absent, or contradictory features as unknown or conflicts.

## Candidate-card construction

Use:

- `assets/templates/mascot-character.md` for mascot proportions, silhouette, markings, limbs, appendages, and props;
- `assets/templates/humanoid-character.md` for visible presentation, hair, facial structure, proportions, clothing layers, and accessories.

Populate:

- approved identity metadata;
- reference inventory;
- evidence ledger;
- proposed immutable anchors;
- flexible and contextual attributes;
- forbidden drift;
- expression grammar;
- diary behavior;
- unresolved questions.

Do not promote inferred evidence into an immutable anchor.

## Review gate

Return:

1. reference-quality rating;
2. confirmed observations;
3. inferred candidates;
4. unknown or obstructed areas;
5. canonical-role decisions still required;
6. the complete candidate `character.md`;
7. the storage profile, locator, persistence, and write capability;
8. a proposed destination, if supplied;
9. an accurate install status.

Ask only questions whose answers would change canonical identity. Ask for a locator, collision check, or write approval only when the user requests installation in the current task. Otherwise report the binding as missing, unverified, or read-only without turning future storage into a review question.

Use `not-installed` or `export-ready` before a persistent write. Use
`export-ready` when a newly produced candidate still needs host-managed or
manual saving. Use `available-in-context` only when the character card itself,
not merely its reference image, is already readable from project or chat
context.

Install only after the user explicitly approves the complete candidate and
exact writable destination. Never install into bundled Skill assets. If the
target exists, follow the exact comparison and idempotent no-op rules in
`references/schema/character-pack.md`; any non-identical or unverifiable target
switches to AUDIT without a write.
