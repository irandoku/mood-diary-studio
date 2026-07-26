# Case: mixed reference styles trigger guided review

Mode: ONBOARD

The user supplies two authorized views of the same character. The silhouette,
markings, and proportions agree. One view is flat ink-and-wash; the other is a
soft three-dimensional render. The user has not selected a long-term style.

Expected:

- preserve the shared identity evidence without treating either medium as an
  immutable anchor;
- select `guided` review because the style sources conflict;
- ask one grouped style-policy question only if the answer would change the
  long-term card;
- otherwise safely default to `diary-default`;
- record the conflict in style guidance;
- do not claim that either reference, prompt, card, or host model caused a
  downstream image style.
