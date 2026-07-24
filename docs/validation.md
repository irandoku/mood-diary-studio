# Validation

Validation separates structural conformance, behavioral quality, and host evidence.

## Structural checks

1. Validate `skill/mood-diary-studio/` with an Agent Skills validator.
2. Confirm the folder and frontmatter names match.
3. Confirm every path named by `SKILL.md` exists.
4. Confirm the installable Skill contains no executable files or vendor configuration.
5. Confirm no absolute paths or private character identifiers appear in the portable core.

## Behavioral checks

Run every case in `tests/cases/` in a clean context. Evaluate against `tests/acceptance.md`.

Test the Skill as a user would:

```text
Use mood-diary-studio at <skill-path> in DIARY mode for this entry: ...
```

Do not tell the test agent the intended answer. Review whether the output follows the contract, distinguishes evidence from inference, and stops at approval gates.

## Host claims

Record hosts as unverified until the packaged Skill has been installed and run there. Passing a static validator demonstrates structure, not host behavior.
