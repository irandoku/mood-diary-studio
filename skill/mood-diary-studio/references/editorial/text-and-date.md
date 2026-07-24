# Text and Date

Treat every displayed word and date as factual content.

## Date sources

Use a date only when it is:

- explicitly provided by the user;
- present in an authorized source;
- requested as the current date and the host can verify it.

Do not infer a calendar date from `today`, weekday, season, holiday, weather, or conversation order when the host cannot verify the intended date.

If no reliable date exists, use `date: omitted` or ask only when the date materially matters.

## Short phrase

Prefer no phrase or one restrained phrase. It may be:

- exact user-provided wording;
- an agent-proposed caption clearly labeled as proposed;
- a non-quoted summary approved by the user.

Never present generated wording as a diary quotation or the user's exact words.

Keep the phrase subordinate to the image. Aim for one short line; adapt length to the user's language rather than imposing an English word count.

## Image-generation limitation

Request exact text verbatim in the prompt, but do not promise accurate rendering. If spelling or typography matters, recommend generating the art without text and adding the date or phrase as a separate layout layer.

## Output fields

Record:

```yaml
date:
  value: null
  source: omitted
phrase:
  value: null
  source: omitted
rendering_plan: none
```

Allowed source values are `user-provided`, `source-observed`, `verified-current`, `agent-proposed`, and `omitted`.
