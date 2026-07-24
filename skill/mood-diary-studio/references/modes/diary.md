# DIARY Mode

Turn a daily account into one restrained, character-led diary illustration brief and one model-neutral prompt.

## Inputs

Accept:

- a daily account or emotional note;
- an approved character card;
- optional approved reference images;
- an optional date or short phrase;
- optional output-language, aspect-ratio, or visual-density preferences.

Resolve the character source through `references/schema/storage-profiles.md`. A bundled sample is read-only. A project source or chat attachment is available in context, not installed.

If no approved card exists, allow a user-authorized reference-only character for this result, but label identity as ephemeral and do not claim cross-entry consistency. Do not silently create or install a card.

## Workflow

### 1. Establish source facts

List only facts that affect the illustration. Separate:

- events;
- felt or stated emotions;
- desired or imagined events;
- contextual details;
- exact user-provided text and date.

Do not treat imagined activity as completed activity.

### 2. Select one emotional center

State the underlying tension, shift, or emotional orientation in one sentence. Prefer a precise relationship such as:

- anticipation before action;
- relief after sustained effort;
- quiet disappointment under an ordinary routine;
- distance between outward calm and inward fatigue.

Do not use a list of mood adjectives as the emotional center.

### 3. Make editorial cuts

For each event or object, mark:

- **keep** — directly communicates the emotional center;
- **merge** — overlaps with another cue;
- **omit** — factual but visually distracting;
- **echo** — appears only as a faint symbolic or imagined trace.

Keep one primary action or state.

### 4. Translate emotion into space

Use `references/editorial/mood-to-scene.md`. Decide:

- posture and gaze;
- character scale;
- occupied and empty areas;
- object distance;
- environmental motion;
- one optional symbolic element.

### 5. Enforce visual budget

Use `references/editorial/visual-budget.md`. If the composition exceeds the selected profile, remove or merge elements before writing the prompt.

### 6. Plan text and date

Use `references/editorial/text-and-date.md`. Do not invent missing dates, quotations, or diary phrases.

### 7. Apply character identity

Use immutable anchors as requirements. Use flexible or contextual features only when they support the entry. Ignore inferred or undecided items unless the user explicitly approves them for this result.

Do not display every anchor like a product catalog. Preserve identity while keeping the diary action natural.

Record the storage profile, locator, card version or candidate status, and availability state.

### 8. Write the prompt

Use ordinary descriptive language. Include:

1. diary medium or visual grammar requested by the user;
2. one scene and one primary emotional action;
3. approved character anchors;
4. composition, scale, and meaningful negative space;
5. limited supporting cues;
6. exact text only when approved;
7. a concise avoid list.

Do not include model names, API parameters, quality flags, seeds, or vendor syntax.

### 9. Review

Run `references/review/drift-review.md`. Revise once if any required check fails.

## Delivery

Use the DIARY contract in `references/schema/output-contracts.md` and the skeleton in `assets/templates/diary-result.md`.

Deliver the editorial decision and prompt. Do not generate an image unless separately requested.
