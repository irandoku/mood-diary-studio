# INSTALL Case: Identical Existing Target

Use `mood-diary-studio` with the approved Paper Dot sample character.

The exact writable persistent pack root is
`/example/private-character-pack`. The user approves installing the complete
bundled sample plugin at `paper-dot/`.

That target already exists. Its complete file set and every file are
byte-for-byte identical to the approved bundled sample plugin.

Handle the request according to the existing-target rules. Do not rewrite,
touch, or otherwise change any target file. Re-read the target card and report
`availability_state: in-context`,
`persistence_state: pack-installed`, and the no-write outcome accurately.
