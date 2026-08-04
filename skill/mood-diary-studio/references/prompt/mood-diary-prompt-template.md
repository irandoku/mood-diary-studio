# Mood Diary Prompt Assembly

Assemble one model-neutral prompt from the following blocks. Keep the labels
out of the final prompt if a natural paragraph reads better, but preserve the
information and ordering. Do not add model names, API parameters, seeds,
quality flags, or vendor syntax.

## Character authority

Include:

- exact character ID and approved status, when available;
- only the minimum sufficient approved identity anchors;
- authorized reference-image requirements and unresolved limitations;
- character-specific avoid rules that are plausible for this scene.

Never let this template invent, remove, or overwrite canonical identity,
marking meaning, species, proportions, props, or forbidden drift. If the
character card and the requested treatment conflict, stop and report the
conflict.

## Diary intent

Include:

- authorized date, or no date;
- actual, desired, imagined, or uncertain scene status;
- one emotional core;
- one primary action or state;
- what has and has not happened.

Keep desired and imagined language distinct. Do not add a proxy object for
unknown event content or completion evidence.

## Visual language

When this treatment is the framework default or is selected explicitly, express
the semantic requirements rather than copying a long style inventory:

- cool-white or near-white paper with generous narrative breathing space;
- very fine warm gray-brown or lightly colored precise linework;
- local gongbi-like detail at identity, face, prop, and topic anchors;
- transparent, pale, low-muddiness watercolor washes;
- extremely light neutral-gray or pale blue-gray shadows;
- secondary areas lightly described and atmospheric areas allowed to remain
  unpainted;
- handwritten mood-diary page feeling, not commercial key art.

## Scene construction

Include character scale, support contact, furniture scale, unified setting,
supporting props and cues, detail-concentration zone, breathing zone, and any
provenance or editorial-staging labels. For a short mascot, prefer floor-level
or low seating and keep the body and limbs naturally visible.

## Emotion direction

Name one low-amplitude emotion and express it through eyes, gaze, mouth, head
angle, body tension, and interaction with props. Do not use reaction symbols
unless they are explicitly requested.

## Text policy

State whether the prompt contains no text, an exact authorized date, an exact
authorized phrase, or an authorized title. Keep text in the breathing area and
subordinate to the scene. Do not rewrite user-approved wording.

## Avoid

Combine only relevant character-specific and treatment-specific risks:

```text
Avoid thick black outlines, muddy opaque watercolor, full-frame sepia or
yellow grading, heavy uniform shadows, dense decorative backgrounds, sticker
or commercial-poster aesthetics, glossy 3D rendering, genericized markings,
and unapproved anthropomorphism.
```

Remove an avoid item when it is irrelevant to the current scene. Do not repeat
the complete character card or forbidden-drift inventory.
