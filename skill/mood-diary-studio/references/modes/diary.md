# DIARY Mode

Turn a daily account into one focused, character-led diary illustration brief and one model-neutral prompt.

## Inputs

Accept:

- a daily account or emotional note;
- an approved character card;
- optional approved reference images;
- an optional date or short phrase;
- optional output-language, aspect-ratio, or visual-density preferences.

Resolve the character source through `references/schema/storage-profiles.md`.
A bundled sample is read-only. A project source, account-library selection, or
chat attachment may be in context without being installed in a character pack.
An unverified task VM is `runtime-filesystem`, not persistent storage.

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

Assign the primary scene an evidence status: `actual`, `desired`, `imagined`,
or `uncertain`. Preserve that status in editorial selection, composition, and
the final prompt. Use status-specific language:

- `desired` — describe a wish, wanted scene, or longing; do not call it
  imagined or a mental scene;
- `imagined` — describe an imagined, remembered-as-imagined, or mental scene;
- `uncertain` — describe a possibility whose occurrence is unresolved.

Any of these scenes may be visualized, but never describe it as a completed
event unless its status is `actual`.

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

Do not invent a proxy object to stand for unknown event content or causes. If
the user says an unspecified task was completed, do not add documents,
checklists, tools, trophies, or generic work artifacts to prove completion.
Express the change through sourced action, posture, spacing, and environment.

Editorial staging may add a non-factual illustrative environment only within
the boundary in `references/editorial/mood-to-scene.md`. Label each unsourced
choice in Editorial selection as `editorially constructed` or `inferred`,
never as a source fact. It may carry a known emotion, time quality, distance,
or expectation, but must not add a new event, person, location, cause, or
completion state, and must not act as a proxy for unknown content. Remove it
when its removal would not weaken the emotional relationship.

### 3.5 Preserve theme legibility

If the entry names a concrete topic (an event, place, season, commemoration,
cultural topic, or another explicitly named subject beyond a generic mood),
identify at least one non-text theme carrier before choosing a density profile.
A carrier may be a source-supported setting, contextual garment,
activity relationship, meaningful object, or environmental condition. An
editorially constructed or inferred carrier is allowed only within the
`mood-to-scene.md` staging boundary and must be labeled as such. Use more than
one when the topic would otherwise be ambiguous, but do not add props just to
raise a count.

Run two quick tests:

- **Caption removal** — hide the date and phrase; the scene must still convey
  the topic at a recognizable level.
- **Character substitution** — replace the approved character with a neutral
  figure; the setting and relationships must still communicate the topic and
  emotional orientation.

If either test fails, revise the scene carriers before lowering or raising the
visual density. A low-density page may use fewer carriers; it may not use zero
when the entry has an explicit topic. Do not use text, a generic background, or
the mascot's pose as the sole evidence of the topic.

### 4. Translate emotion into space

Use `references/editorial/mood-to-scene.md`. Decide:

- approved silhouette, proportion, and limb geometry before selecting any
  furniture or support surface;
- character-environment fit, including support contact, furniture scale, and
  explainable occlusion;
- posture and gaze;
- character scale;
- one unified scene and its primary spatial relationship;
- a detail-concentration zone and a breathing zone;
- object distance;
- environmental motion;
- environmental cues grouped by their shared narrative function;
- one optional symbolic element.

### 5. Enforce visual budget

Use `references/editorial/visual-budget.md`. Count the final elements before
naming the profile. If the composition exceeds the selected profile, remove or
genuinely merge elements, or select a profile that contains the counts before
writing the prompt.

Select density from the emotional and narrative need, not from a default
`sparse` assumption or only from an explicit request for richness. Do not
remove functional environment merely to claim a lower-density profile.

### 6. Plan text and date

Use `references/editorial/text-and-date.md`. Do not invent missing dates, quotations, or diary phrases.

### 7. Apply character identity

Use immutable anchors as requirements. Use flexible or contextual features only when they support the entry. Ignore inferred or undecided items unless the user explicitly approves them for this result.

Do not display every anchor like a product catalog. Preserve identity while keeping the diary action natural.

Build the minimum sufficient prompt anchor set from the approved immutable
visual anchors. Keep recognition-critical anchors and any qualifier whose
removal would change silhouette, proportions, orientation, feature location,
or required shape. Paraphrasing and grouping are allowed, but do not omit,
invert, or weaken those semantics.

For a simple mascot, express this set in one natural sentence. Prioritize:

1. silhouette and proportion;
2. a small number of recognition-critical features;
3. an immutable prop only when it remains visible in the chosen action.

Expand only when genuine character complexity requires it. Do not copy the full
card or repeat the Character use inventory. Add a forbidden-drift item to the
prompt's avoid language only when the current action, view, or medium makes that
specific drift plausible; never duplicate the full forbidden-drift list.

Record the storage profile, locator, card version or candidate status,
availability state, and persistence state.

### 8. Apply style guidance

Use `references/schema/style-guidance.md`.

1. Report the approved card's stored style policy and override rule without
   changing their names or values.
2. For a v1 card with no style block, report `per-entry` and `allowed` as
   compatibility values; do not infer long-term style from its references.
3. Resolve the effective entry style: apply an explicit current-entry request
   first, otherwise use the stored guidance or diary default.
4. Report the effective entry style separately. A current-entry request never
   changes the stored policy to `user-selected`.

Keep style guidance soft and portable. Never weaken identity anchors to satisfy
medium, texture, line, or palette guidance.

When no current-entry request or approved stored treatment is more specific,
use `bright-fine-line-gongbi-diary` as the effective entry style, sourced from
the framework default. Also read
`references/visual-style/bright-fine-line-gongbi-diary.md` whenever it is the
default or selected treatment. Apply its paper, line, color, density,
scene-scale, emotion, weather, and failure rules as visual guidance only. Do
not copy any character identity from its examples or allow it to replace the
approved card.

### 9. Write the prompt

Use `references/prompt/mood-diary-prompt-template.md` to assemble the prompt
in this order: character authority, diary intent, visual language, scene
construction, emotion direction, text policy, and avoid. The final result may
be one natural paragraph, but all required decisions must remain represented.

Use ordinary descriptive language. Include:

1. diary medium or visual grammar requested by the user;
2. one scene, one primary emotional action, and the scene's evidence status;
3. the compact approved prompt anchor set;
4. composition, scale, detail concentration, and meaningful breathing space;
5. source-supported cues and any clearly labeled editorial staging;
6. exact text only when approved;
7. a concise avoid list.

Do not include model names, API parameters, quality flags, seeds, or vendor syntax.

### 10. Review

Run `references/review/drift-review.md`. Revise once if any required check fails.

## Delivery

Use the DIARY contract in `references/schema/output-contracts.md` and the skeleton in `assets/templates/diary-result.md`.

Deliver the editorial decision and prompt. Do not generate an image unless separately requested.
