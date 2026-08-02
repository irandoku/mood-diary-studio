# Visual Budget

Use visual budget as a hard coherence limit, not as a target for maximum
sparseness or a suggestion to shrink more elements into the frame.

## Invariants

Every profile keeps:

```yaml
primary_subject: 1
primary_action_or_state: 1
unified_scene: 1
symbolic_elements: 0-1
text_elements: 0-2
```

Text elements normally mean one date and one short phrase. A symbolic element
is optional and always subordinate.

## Profiles

| Profile | Supporting objects | Environmental cues | Editorial use |
|---|---:|---:|---|
| `minimal` | 0-1 | 0-1 | The emotion is legible through the subject and one simple spatial relation. |
| `sparse` | 0-2 | 0-2 | A few cues support the subject without requiring a developed environment. |
| `moderate` | 0-2 | 2-4 | A coherent environment actively carries distance, expectation, season, routine, or another part of the emotional relationship. |
| `layered` | 0-4 | 4-6 | An opt-in, hierarchical environment carries environmental, commemorative, cultural, or seasonal narrative around one action and one complete scene. |

A supporting object is an independently meaningful object involved in the
character's state or action. An environmental cue establishes spatial,
atmospheric, seasonal, or everyday context. Count a cue independently when it
is separately described or visually salient.

For budget reporting, classify every theme carrier as `primary_subject`,
`primary_action_or_state`, `supporting_object`, or `environmental_cue`. If one
element carries two roles, report the role-sharing explicitly and count it
once in the applicable budget bucket; never leave a carrier uncounted.

Do not exceed `layered` within this framework. A dense poster, collage,
multi-event spread, or background showcase conflicts with the diary grammar.

## Profile selection

Choose the profile from the emotional relationship and scene function, then
verify that every count fits.

- Use `minimal` when additional setting would not strengthen the entry.
- Use `sparse` when a few light cues are sufficient.
- Use `moderate` when one complete, focused environment needs 2-4 cues that
  jointly serve the same emotional center. The user need not explicitly ask
  for a richer page.
- Use `layered` only when the environment itself carries environmental,
  commemorative, cultural, or seasonal narrative that cannot be expressed by
  a lighter profile. It is non-default and still contains one primary action,
  one complete scene, one detail-concentration zone, and a quieter breathing
  zone.
- Treat a user density preference as relevant input, not as the only authority
  for choosing `moderate`.
- Report the requested density preference, selected profile, and selection
  rationale. If the preference would erase a required theme carrier, preserve
  the carrier and explain why the selected profile is higher.
- Do not delete functional environment merely to fit `minimal` or `sparse`.

`sparse` and `moderate` may both contain two environmental cues. Use `moderate`
when those cues form an active environmental relationship; use `sparse` when
they only establish the scene lightly.

A profile label never overrides its limits. Do not count separately described
or independently salient cues as one, and do not evade the budget by shrinking,
renaming, or arbitrarily grouping them.

## Theme floor

Density is adjustable; thematic relevance is not optional. When the entry
names a concrete topic (an event, place, season, commemoration, cultural topic,
or another explicitly named subject beyond a generic mood), the
composition must contain at least one non-text theme carrier. A carrier can be
an environmental cue, contextual garment, activity relationship, or meaningful
supporting object already supported by the entry or an authorized source. One
visual element may carry more than one role without inflating the budget.

Editorial staging may count as a carrier only when it stays within the
`mood-to-scene.md` staging boundary and is explicitly labeled as editorially
constructed or inferred.

Use the caption-removal and character-substitution tests from DIARY mode. If
removing the caption or replacing the character erases the topic or emotional
orientation, or leaves only a generic mascot pose, the selected profile is
invalid even when its numeric counts fit. Add or
strengthen a relevant carrier before changing the profile. For commemorative or
cultural topics, normally use carriers from at least two different categories
when the evidence supports them; otherwise report the remaining ambiguity.

## Reduction order

When over budget:

1. remove decorative repetitions;
2. remove elements that do not express the emotional center;
3. genuinely merge cues with the same visual and narrative function;
4. convert a secondary event into one faint echo, if essential;
5. remove the symbolic element before weakening the unified scene;
6. preserve at least one evidence-backed theme carrier for an explicit topic;
7. preserve functional environment before forcing a lower-density label;
8. preserve character identity anchors without displaying them as inventory.

## Failure patterns

Reject:

- multiple equally prominent scenes;
- a prop for every sentence;
- symbols that duplicate facial expression;
- scenery added only to assert a specific unsourced place;
- small crowded objects used to claim the budget was respected;
- separately meaningful cues merged only to lower the reported count;
- uniform detail across the entire frame;
- labels, stickers, and decoration that consume the breathing zone.
- using `layered` as a default or as permission for a poster, catalog, or
  background showcase;
- using cultural specificity without a user-provided or reliable authorized
  source;
- using a date or phrase as the only evidence of an explicit topic;
- passing a numeric budget while failing caption removal or character
  substitution;
- replacing theme-bearing setting or clothing with generic scenery merely to
  keep a page sparse.
