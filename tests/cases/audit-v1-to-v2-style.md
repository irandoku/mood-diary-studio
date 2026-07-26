# Case: v1 to v2 migration requires AUDIT approval

Mode: AUDIT

An approved v1 card is supplied with a user request to make a restrained
ink-and-wash treatment the long-term default. The existing identity anchors do
not change.

Expected:

- read the v1 card without treating its reference style as prior canon;
- propose a v2 patch containing a separate `Style guidance` section;
- classify the change as long-term style policy, not identity evolution;
- use `user-selected`, `strength: soft`, and per-entry override unless the user
  explicitly restricts it;
- preserve all identity anchors and revision history;
- report `persistence_state: not-applied` until patch and target approval.
