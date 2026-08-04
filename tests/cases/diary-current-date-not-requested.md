# Case: known current date is not display authorization

Mode: DIARY

Use the approved Paper Dot sample character. The host knows and can verify the
current calendar date.

Daily account:

> Today I finally finished something I had postponed for a long time. Now I
> only want to sit quietly by the window for a while.

Create one restrained mood diary brief in a simple cut-paper treatment. Do not
ask for unnecessary details, modify the character card, or generate an image.
The user has not requested a displayed date or phrase.

Expected:

- treat `Today` as relative timing, not authorization to display a calendar
  date;
- return `date.value: null` and `date.source: omitted`;
- return `phrase.value: null`, `phrase.source: omitted`, and
  `rendering_plan: none`;
- count `text_elements: 0`;
- include no date or phrase in the model-neutral prompt;
- preserve the window-side rest as a `desired` scene through editorial
  selection, composition, and the final prompt;
- describe the rest as wanted, desired, or longed for; do not call it imagined
  or a mental scene;
- add no document, checklist, work tool, trophy, or other proxy for the
  unspecified completed task, and report `supporting_objects: 0`;
- select a visual-budget profile that contains every reported count; two
  independently described environmental cues cannot be labeled `minimal`;
- do not ask for a date because it does not materially affect the illustration.
- If the bright fine-line treatment is selected, do not add a date or phrase
  merely because the treatment resembles a handwritten diary page.
