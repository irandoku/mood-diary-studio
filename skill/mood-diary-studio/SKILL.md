---
name: mood-diary-studio
description: Turn daily experiences into focused, character-led mood diary illustration briefs and model-neutral prompts; draft review-gated character cards from visual references; and audit existing character cards against new references. Use when creating a character mood diary, onboarding a user-provided character, or reviewing character identity drift.
---

# Mood Diary Studio

Convert lived experience into a focused diary illustration decision, then express that decision as a model-neutral prompt. Treat character identity as user-governed data rather than built-in lore.

## Select a mode

- Use **DIARY** for daily narrative to illustration brief and prompt. Read `references/modes/diary.md`.
- Use **ONBOARD** to draft a candidate character card from references. Read `references/modes/character-onboarding.md`.
- Use **AUDIT** to compare an existing card with new references. Read `references/modes/character-audit.md`.

If the request mixes modes, complete ONBOARD or AUDIT review before DIARY uses changed character data.

## Apply common rules

1. Separate user-provided facts, direct observations, inferences, and unknowns.
2. Reduce the entry to one emotional center before composing.
3. Choose one focused scene and preserve elements that communicate that center.
4. Treat detail concentration and breathing space as narrative structure; breathing space need not be blank.
5. Use only approved character facts as identity requirements.
6. Keep character identity separate from rendering style.
7. Resolve the character source and storage profile before claiming availability or persistence.
8. Produce prompts in ordinary descriptive language without vendor syntax.
9. Run drift review before delivery.
10. Match the user's language unless the user requests another language.

## Protect character governance

- Never install or revise a character card without explicit user approval.
- Never use `assets/` as a destination for private or user-created characters.
- Treat a clearly visible feature and its canonical role as separate questions.
- Do not infer personality, backstory, ethnicity, gender identity, exact age, relationships, or protected traits from appearance.
- Do not promise exact cross-generation identity. Report reference quality and unresolved risks.
- Do not search arbitrary private locations. Use only references and character-pack locations the user provides.
- Before writing, resolve the exact target, check for collisions, show the candidate or diff, and obtain approval.
- If the host cannot write files, return the complete artifact for the user to save.

## Load references

For DIARY, always read:

- `references/schema/storage-profiles.md`
- `references/schema/style-guidance.md`
- `references/editorial/mood-to-scene.md`
- `references/editorial/visual-budget.md`
- `references/editorial/composition-and-negative-space.md`
- `references/editorial/text-and-date.md`
- `references/review/drift-review.md`
- `references/schema/output-contracts.md`

For ONBOARD, always read:

- `references/schema/storage-profiles.md`
- `references/schema/character-plugin.md`
- `references/schema/character-pack.md`
- `references/schema/style-guidance.md`
- `references/review/onboarding-review-levels.md`
- `references/review/drift-review.md`
- `references/schema/output-contracts.md`

Use `assets/templates/mascot-character.md` or `assets/templates/humanoid-character.md` as the candidate-card base. Use `assets/templates/onboarding-result.md` for review delivery.

For AUDIT, always read:

- `references/schema/storage-profiles.md`
- `references/schema/character-plugin.md`
- `references/schema/character-pack.md`
- `references/schema/style-guidance.md`
- `references/review/drift-review.md`
- `references/schema/output-contracts.md`

Use `assets/templates/audit-result.md` for review delivery.

## Boundaries

Keep the framework platform independent, agent independent, model independent, and free of private character IP. Do not execute character plugins: they contain data only. Do not generate an image unless the user separately requests image generation and the host provides that capability.
