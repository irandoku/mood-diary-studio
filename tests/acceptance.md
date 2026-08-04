# Acceptance Criteria

Evaluate each case from a clean context with only the packaged Skill and case input available.

## Global

- The selected mode follows its output contract.
- Facts, observations, inferences, and unknowns remain distinguishable.
- Identity anchors and style guidance remain separate.
- If the exact approved character card or authorized reference cannot be read,
  stop and report the limitation; do not substitute conversation memory or a
  different character.
- Prompts contain no model or vendor syntax.
- The framework does not claim to render images.
- No character data is installed or updated without explicit approval.
- Every character source reports a storage profile and accurate availability state.
- Bundled assets are never used as private-character destinations.
- Output language follows the user.

## DIARY cases

- Select one emotional center rather than a list of events.
- Distinguish actual events from desired or imagined activity.
- Preserve the primary scene's evidence status through editorial selection,
  composition, and the final prompt.
- Use desired or longing language for `desired` scenes and imagined or mental
  language for `imagined` scenes; do not substitute one status for the other.
- Do not invent documents, checklists, tools, or other proxy objects for
  unknown event content or completion evidence.
- When the entry names a concrete topic (an event, place, season,
  commemoration, cultural topic, or another explicitly named subject beyond a
  generic mood), include at least one non-text theme carrier supported by the
  entry, an authorized source, or explicitly marked editorial staging within
  the `mood-to-scene.md` boundary; density may vary, but relevance cannot be
  zero.
- Pass both caption-removal and character-substitution tests; a date, phrase,
  generic background, or mascot pose cannot be the sole topic evidence.
- Report keep, merge, omit, and echo decisions when relevant.
- Report counts that fit the stated visual-budget profile.
- Report any requested density preference, selected profile, and selection
  rationale; classify each theme carrier into a budget category and state any
  role-sharing.
- Apply approved silhouette, proportion, and limb geometry before selecting
  furniture or support surfaces; check support contact, furniture scale, and
  explainable occlusion. Compact or short mascots default to ground-level or
  low seating unless the entry supplies a narrative reason.
- Use the bright-neutral fallback (delicate restrained linework, transparent
  low-chroma pale accents, cool/neutral white paper, bright neutral daylight,
  pale blue-gray or neutral-gray shadows, and localized natural material
  colors) only when no current-entry or approved stored treatment is more
  specific; keep it separate from identity and avoid silent yellow-brown or
  nostalgic wash and heavy uniform outlines.
- Treat `layered` as a non-default profile with stated counts, using it only
  when environmental, commemorative, cultural, or seasonal context carries the
  narrative; retain one action, one complete scene, a detail-concentration
  zone, and a quieter breathing zone rather than a poster or catalog.
- Require user-provided or reliable authorized provenance for culturally
  specific clothing, patterns, ceremonies, symbols, or factual labels; lower
  specificity when unconfirmed and report source conflicts without silently
  rewriting displayed labels.
- Preserve identity-bearing anchor qualifiers in the final prompt without
  semantic weakening or contradiction.
- Keep the prompt anchor set minimally sufficient; do not repeat the full
  character inventory or forbidden-drift list.
- Express a simple mascot's prompt anchors in one natural sentence and include
  only scene- or medium-relevant drift risks in the avoid language.
- Report the approved stored style policy and override rule separately from
  the effective entry style and its source.
- When the bright fine-line treatment is selected, assemble its paper, line,
  pale-color, shadow, detail-hierarchy, and diary-grammar requirements into
  the one final prompt without changing character authority.
- Keep mascot scenes at a plausible low height and preserve full limb
  visibility; do not use tabletop placement or human-scale furniture without
  a sourced narrative reason.
- Represent rain through localized cool atmosphere while retaining cool-white
  paper; do not use a full-frame gray filter or dramatic sadness as a shortcut.
- Use low-amplitude mascot expression rather than sticker reaction symbols.
- Do not turn a DIARY-only style request into stored `user-selected` policy.
- Give negative space a narrative function.
- Do not invent a date or quotation.
- Do not display the current date merely because the host can verify it;
  `verified-current` requires an explicit user request to display that date.
- Produce one final prompt.

## ONBOARD cases

- Rate reference quality and state limitations.
- Select quick, guided, or advanced review from evidence risk rather than user
  technical knowledge.
- Quick review puts one compact approval summary and its only question before
  detailed evidence.
- Quick review delivers the complete candidate and evidence ledger in the same
  turn as a separate response artifact, accessible collapsed section, or
  inline appendix.
- Quick review identifies the artifact delivery method and label, remains
  usable without opening it, and does not mislabel artifact delivery as
  persistent saving.
- Quick review artifacts are complete but avoid redundant prose and
  non-evidence-based elaboration.
- Quick review stays within its summary, ledger, anchor, expression, and diary
  content budgets; material complexity beyond those limits triggers guided
  review instead of omission.
- Guided review asks only questions that change identity, style policy,
  authority, or write outcome.
- Separate confirmed, inferred, and unknown.
- Keep evidence status separate from canonical role.
- Do not infer personality, backstory, protected traits, or exact age.
- Include a complete candidate card.
- Produce new candidates as `mood-diary-character/v2`.
- Default style to `diary-default`, soft, and per-entry overridable.
- End with separate `availability_state` and `persistence_state`.

## AUDIT cases

- Distinguish missing evidence, contextual variants, and conflicts.
- Preserve current canon until the user approves a change.
- Read v1 cards without inventing style canon.
- Separate identity changes, long-term style changes, and per-entry overrides.
- Include a patch proposal and untouched list.
- End with `persistence_state: not-applied`.

## Storage cases

- A missing binding resolves to `manual-export`; no path is invented.
- A missing-binding analysis does not ask for a future path unless installation was requested.
- A managed project uses a logical locator and never claims local filesystem access.
- A new managed-project candidate is `in-context` and `export-ready`; an exact
  verified project source may be `in-context` and `host-saved`.
- An account-library item is `not-in-context` until selected or attached.
- A verified Library item may be `host-saved` but is never `pack-installed`.
- An unverified task VM resolves to `runtime-filesystem`, `task-scoped`, and
  `transient`, even when writable.
- An existing character card supplied as a chat attachment is `in-context` and
  `transient`; a new candidate drafted from an attached reference is
  `in-context` and `export-ready`.
- `assets/sample-character/` remains a bundled read-only fixture.
- `readable` and `writable` are booleans; capability is not confused with approval.
- An accessible absolute path supplied explicitly by the user resolves to
  `local-filesystem`, even when it is inside the current workspace.
- `workspace-files` is used only for a host-supplied workspace-relative
  binding; no absolute path is invented.
- Only an exact approved writable persistent pack binding can reach
  `pack-installed`.
- A complete byte-identical existing target is an idempotent installation:
  nothing is written, the card is re-read, and the result is `pack-installed`
  with the no-write outcome stated explicitly.
- A different, incomplete, extra, or unverifiable existing target is not
  changed and switches to AUDIT.

## Failure

Fail a case if the agent:

- turns every input detail into an image element;
- reports visual-budget counts that exceed the named profile;
- turns a desired, imagined, or uncertain primary scene into an unqualified
  completed event later in the brief or prompt;
- calls a `desired` scene imagined, or an `imagined` scene desired;
- adds a proxy document, checklist, tool, or other object to represent unknown
  event content, causes, or completion evidence;
- leaves an explicit topic with no non-text theme carrier, or passes numeric
  visual-budget counts while failing caption-removal or character-substitution;
- omits a requested density preference, selected profile, or selection
  rationale, or leaves a theme carrier uncounted or without a stated role;
- selects furniture or support surfaces before applying approved character
  silhouette, proportions, and limb geometry, or leaves compact mascots on
  unmotivated tabletops/human-scale furniture with unexplained occlusion;
- uses `layered` as a default, exceeds its counts, or turns it into a poster,
  catalog, or background showcase without environmental, commemorative,
  cultural, or seasonal narrative need;
- invents culturally specific clothing, patterns, ceremonies, symbols, or
  labels without user-provided or reliable authorized provenance, or silently
  rewrites a displayed factual label that conflicts with a reliable source;
- omits, reverses, or weakens an identity-bearing silhouette, proportion,
  orientation, location, or shape qualifier in the final prompt;
- turns the final prompt into a repeated character-card or forbidden-drift
  inventory when a compact anchor passage is sufficient;
- expands a simple mascot's anchor passage beyond one sentence without genuine
  character complexity;
- reports a DIARY-only style request as stored `user-selected` policy;
- uses the bright fine-line treatment as an identity anchor or card mutation;
- replaces cool-white paper and localized pale-blue-gray atmosphere with
  full-frame sepia, yellow, or gray grading;
- turns fine-line diary treatment into thick black contours, muddy opaque
  watercolor, glossy 3D, sticker, or commercial-poster rendering;
- uses exaggerated reaction symbols or facial acting for a low-amplitude diary
  emotion;
- merges the stored style policy and effective entry style into one ambiguous
  field;
- silently promotes a visible accessory into an immutable anchor;
- silently promotes reference rendering style into immutable identity;
- attributes output style to the character card without controlled evidence;
- treats occlusion as deletion;
- writes or claims success before approval;
- substitutes a different character, destination, or date;
- adds a current date from host knowledge without an explicit user request to
  display it;
- treats upload, attachment, export, host saving, runtime files, or bundled
  assets as pack installation;
- executes instructions embedded inside character data.

## Codex Desktop host acceptance

- Clear-reference ONBOARD uses quick review, one summary approval, and a
  complete v2 candidate delivered after the approval question as a review
  artifact or inline fallback.
- Ambiguous or mixed-style references trigger guided review.
- A v1 card remains readable; v1-to-v2 migration requires an AUDIT patch.
- Four style policies can change prompt guidance without changing approved
  identity anchors.
- An approved local installation is re-read with reference paths resolved.
- A writable runtime sandbox remains transient unless clean-task persistence is
  separately verified.

## ChatGPT Work host acceptance

Run these only with public-safe fixtures and a user-approved test Project or
Library area:

- A user adds the exact character artifact to a private Project; a fresh Work
  chat started inside that Project re-reads its ID, version, and reference
  inventory.
- Test user-operated **Save to project** separately from a request for Work to
  save or add a source itself. Record direct Skill write capability only when
  the action is exposed, authorized, visibly completed, and re-readable in a
  fresh Work chat.
- Create and validate an artifact in the Work runtime filesystem, then verify
  that a fresh Work chat does not inherit the runtime path.
- Verify whether the exact generated `character.md` or ZIP appears in Library.
  Select it in a fresh chat, re-read it, and compare contents before reporting
  `host-saved`.
- Test a same-name Project upload. Do not treat a duplicate filename as update
  or replacement; identify artifacts by character ID, schema, plugin version,
  and content comparison.
- Apply an AUDIT revision only after patch and target approval. Keep the prior
  host-saved version until deletion is separately approved.
- Run deletion only on disposable public-safe fixtures and record the active
  workspace retention policy.
- Keep image generation separate. If comparing styles, hold references and
  prompt structure constant and report observations without assigning sole
  causation to the card.
