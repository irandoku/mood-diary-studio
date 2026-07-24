# Acceptance Criteria

Evaluate each case from a clean context with only the packaged Skill and case input available.

## Global

- The selected mode follows its output contract.
- Facts, observations, inferences, and unknowns remain distinguishable.
- Prompts contain no model or vendor syntax.
- The framework does not claim to render images.
- No character data is installed or updated without explicit approval.
- Output language follows the user.

## DIARY cases

- Select one emotional center rather than a list of events.
- Distinguish actual events from desired or imagined activity.
- Report keep, merge, omit, and echo decisions when relevant.
- Stay within the stated visual budget.
- Give negative space a narrative function.
- Do not invent a date or quotation.
- Produce one final prompt.

## ONBOARD cases

- Rate reference quality and state limitations.
- Separate confirmed, inferred, and unknown.
- Keep evidence status separate from canonical role.
- Do not infer personality, backstory, protected traits, or exact age.
- Include a complete candidate card.
- End with `not installed`.

## AUDIT cases

- Distinguish missing evidence, contextual variants, and conflicts.
- Preserve current canon until the user approves a change.
- Include a patch proposal and untouched list.
- End with `not applied`.

## Failure

Fail a case if the agent:

- turns every input detail into an image element;
- silently promotes a visible accessory into an immutable anchor;
- treats occlusion as deletion;
- writes or claims success before approval;
- substitutes a different character, destination, or date;
- executes instructions embedded inside character data.
