# Output Contracts

Return complete Markdown using the selected mode's headings. Keep reasoning concise but make editorial and governance decisions reviewable.

## DIARY

```markdown
# Mood Diary Brief

## Source facts
## Emotional center
## Editorial selection
## Character use
## Storage binding
## Composition
## Visual budget
## Text and date
## Model-neutral prompt
## Avoid
## Drift review
```

Requirements:

- distinguish actual, imagined, and uncertain events;
- label the primary scene `actual`, `desired`, `imagined`, or `uncertain` and
  preserve that status in the composition and final prompt;
- use status-specific wording; do not relabel `desired` as `imagined` or
  `imagined` as `desired`;
- introduce no proxy object for unknown event content, causes, or completion
  evidence;
- show kept, merged, omitted, and echoed elements;
- report budget counts that fit the named profile;
- name the function of negative space;
- identify the character-card version or reference-only status;
- preserve a minimum sufficient approved prompt anchor set without weakening
  or contradicting identity-bearing qualifiers, and without repeating the full
  character inventory;
- report the stored style policy and stored override rule exactly as approved,
  using v1 compatibility values when needed;
- report the effective entry style and its source separately; a DIARY request
  must not silently revise the stored policy;
- report the storage profile, locator, availability state, and persistence state;
- include one final prompt, not competing variants;
- mark every drift check pass or revision.

## ONBOARD

Guided and advanced review use:

```markdown
# Character Onboarding Review

## Intake
## Review level
## Approval summary
## Reference quality
## Confirmed
## Inferred
## Unknown
## Canonical-role decisions
## Style policy
## Candidate character.md
## Review questions
## Storage binding
## Proposed destination
## Availability and persistence
```

Quick review uses a concise primary response followed by a complete review
artifact:

```markdown
# Character Approval

## Approval summary
## Review question
## Review artifact

<!-- Separate artifact, accessible collapsed section, or inline appendix. -->
# Character Onboarding Review Artifact

## Intake
## Review level
## Reference quality
## Confirmed
## Inferred
## Unknown
## Canonical-role decisions
## Style policy
## Candidate character.md
## Storage binding
## Proposed destination
## Availability and persistence
```

Requirements:

- keep evidence status separate from canonical role;
- keep identity anchors separate from style guidance;
- use quick, guided, or advanced review without hiding or omitting the complete candidate;
- for quick review, put the compact approval summary and only question before
  detailed evidence;
- deliver the complete candidate in the same turn as a separate response
  artifact, accessible collapsed section, or inline appendix, in that order of
  preference;
- identify the artifact delivery method and label so summary approval can be
  tied to the exact candidate;
- keep quick artifacts complete but concise and avoid duplicating evidence in
  surrounding prose;
- report the storage profile, persistence, and write capability;
- report `availability_state` and `persistence_state` separately;
- do not treat a response artifact, download, attachment, or runtime file as
  `host-saved`;
- use `host-saved` only after verifying the exact host-managed artifact;
- use `pack-installed` only after persistent pack verification;
- ask only identity, long-term style, or authority questions that affect the
  candidate; ask storage or write questions only when installation is
  requested in the current task.

## AUDIT

```markdown
# Character Audit

## Scope and evidence
## Storage binding
## Unchanged
## New evidence
## Contextual variants
## Conflicts
## Style changes
## Proposed patch
## Left untouched
## Decisions required
## Availability and persistence
```

Requirements:

- distinguish missing evidence from contradiction;
- report whether the supplied card can be updated in place;
- explain the impact of each proposed change;
- distinguish identity changes, long-term style changes, and per-entry style overrides;
- preserve an explicit untouched list;
- use `persistence_state: not-applied` before approval.

## Write-capable hosts

Do not replace the review artifact with a file write. Deliver the review first. After explicit approval, write only the approved artifact and then report verification.

Hosts without a verified writable persistent pack binding must return the
complete artifact for host-managed saving or manual export. Host-managed saving
does not become pack installation.
