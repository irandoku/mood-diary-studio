# Validation

Validation separates structural conformance, behavioral quality, and host evidence.

## Structural checks

1. Validate `skill/mood-diary-studio/` with an Agent Skills validator.
2. Confirm the folder and frontmatter names match.
3. Confirm every path named by `SKILL.md` exists.
4. Confirm the installable Skill contains no executable files or vendor configuration.
5. Confirm no environment-specific hardcoded paths or private character identifiers appear in the portable core.
6. Confirm bundled assets are never offered as private-character destinations.

## Behavioral checks

Run every case in `tests/cases/` in a clean context. Evaluate against `tests/acceptance.md`.

Include at least one writable local binding, one managed-project binding, and
one missing-binding case. Verify that only the first can reach `installed`.
Also verify that an explicitly supplied accessible absolute path remains
`local-filesystem` even inside a workspace, while `workspace-files` requires a
host-supplied workspace-relative binding.

Exercise both existing-target branches. A complete byte-identical target must
remain untouched, be re-read, and report an idempotent `installed` result. Any
different or unverifiable target must remain untouched and switch to AUDIT.

Test the Skill as a user would:

```text
Use mood-diary-studio at <skill-path> in DIARY mode for this entry: ...
```

Do not tell the test agent the intended answer. Review whether the output follows the contract, distinguishes evidence from inference, and stops at approval gates.

## Host claims

Record hosts as unverified until the packaged Skill has been installed and run there. Passing a static validator demonstrates structure, not host behavior.
