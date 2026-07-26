# ONBOARD Mode

Draft a reviewable candidate character plugin from user-authorized references. Never install it automatically.

## Preconditions

Obtain:

- the proposed display name;
- at least one user-authorized reference image or a user-provided visual inventory;
- the intended type: mascot, humanoid, or unresolved;
- any explicit long-term style preference;
- a storage binding, or enough context to select `chat-attachments` or `manual-export`;
- the exact candidate-pack target only if installation may follow.

Do not require personality or worldbuilding to begin visual onboarding.

Select quick, guided, or advanced review using
`references/review/onboarding-review-levels.md`. Review depth changes
presentation, not evidence quality or approval requirements.

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

Keep identity and style separate. Use
`references/schema/style-guidance.md`. Default to `diary-default` with soft
guidance and per-entry override when the user has not requested a long-term
style. Do not convert the rendering treatment of a reference image into an
identity anchor.

## Review gate

For guided and advanced review, return:

1. selected review level and any risk triggers;
2. a compact must-remain, may-vary, and left-undecided summary;
3. reference-quality rating;
4. confirmed observations;
5. inferred candidates;
6. unknown or obstructed areas;
7. canonical-role decisions still required;
8. style policy, provenance, and override behavior;
9. the complete candidate `character.md`;
10. the storage profile, locator, persistence, and write capability;
11. a proposed destination, if supplied;
12. accurate availability and persistence states.

For quick review, preserve all twelve items but split presentation into:

- a primary response containing the compact summary, the single
  approve-or-revise question, and a review-artifact receipt;
- a complete same-turn review artifact containing the detailed evidence,
  candidate `character.md`, storage binding, and state.

Use the delivery fallback order in
`references/review/onboarding-review-levels.md`. Keep the primary response
usable without opening the artifact, while making the artifact available for
audit before approval.

Ask only questions whose answers would change canonical identity, long-term
style policy, reference authority, or the current approved write outcome and
are required for this candidate or requested operation. Leave nonessential
roles undecided. Ask for a locator, collision check, or write approval only
when the user requests installation in the current task. Otherwise report the
binding as missing, unverified, or read-only without turning future storage
into a review question.

Use the dual state model in `references/schema/storage-profiles.md`. A newly
produced candidate is normally `availability_state: in-context` plus
`persistence_state: export-ready`. Use `host-saved` only after the exact
artifact is verified in host-managed storage, and `pack-installed` only after
the persistent pack rules below pass.

Quick summary approval approves the candidate content only; it is not write
approval. Install only after the user explicitly approves the complete
candidate and exact writable destination. Never install into bundled Skill assets. If the
target exists, follow the exact comparison and idempotent no-op rules in
`references/schema/character-pack.md`; any non-identical or unverifiable target
switches to AUDIT without a write.
