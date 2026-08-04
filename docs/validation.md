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

Include at least one writable local binding, one managed-project binding, one
account-library binding, one runtime-filesystem binding, and one missing-binding
case. Verify that only the approved persistent pack can reach
`pack-installed`. Also verify that an explicitly supplied accessible absolute
path remains `local-filesystem` even inside a workspace, while
`workspace-files` requires a host-supplied workspace-relative binding.

Exercise both existing-target branches. A complete byte-identical target must
remain untouched, be re-read, and report an idempotent `pack-installed` result. Any
different or unverifiable target must remain untouched and switch to AUDIT.

Run a v1 compatibility case, a v1-to-v2 AUDIT migration case, a quick-review
case, and a mixed-style guided-review case. Verify that style never becomes an
identity anchor by default and that output-style causation is not invented.

### Boundary-oriented evaluation

Evaluate hard invariants:

- source facts and `actual`, `desired`, `imagined`, or `uncertain` status;
- approved identity and unresolved canonical roles;
- stored style policy versus the effective entry style;
- date and text authorization;
- availability and persistence state; and
- approval before canonical revision or writes.

Do not fail a case merely because emotional wording, composition, object
classification, density profile, or prompt phrasing differs from another valid
run. Treat one compliant variation as expected model behavior. Revise the Skill
only when a failure crosses a hard boundary, changes downstream behavior, or is
reproducible enough to show a framework problem rather than sample variance.

Test the Skill as a user would:

```text
Use mood-diary-studio at <skill-path> in DIARY mode for this entry: ...
```

Do not tell the test agent the intended answer. Review whether the output follows the contract, distinguishes evidence from inference, and stops at approval gates.

### Bright fine-line treatment checks

The `tests/fixtures/bright-fine-line-gongbi-prompt.md` file is a semantic
snapshot, not an exact-string oracle. Review the final prompt against its
required visual-language and avoid markers while allowing equivalent natural
wording. Check the dedicated style case and the updated mascot, cultural,
text-policy, and anchor-fidelity cases for cross-rule behavior.

## Host claims

Record hosts as unverified until the packaged Skill has been installed and run there. Passing a static validator demonstrates structure, not host behavior.

## Next-version release-candidate milestone

The 2026-07-26 release-candidate validation covered:

- Codex Desktop fresh-context DIARY runs against an approved persistent local
  pack, including source-status preservation, date authorization, unknown-event
  protection, compact identity anchors, and stored-versus-effective style
  reporting;
- ChatGPT Work packaged-Skill loading, image-based quick ONBOARD, explicit
  schema-v2 identity and style approval, transient runtime assembly, validated
  `manual-export`, independent local ZIP and reference verification, and
  fresh-chat package import;
- DIARY brief and model-neutral prompt delivery after the fresh Work import;
  and
- separately requested downstream image rendering, observed by the user to
  preserve the approved identity and diary intent.

The private character, card, reference image, and identifying hashes used in
the Work acceptance run are not part of this repository. The verified public
artifact remains the portable Skill and its generic Paper Dot fixture.

This milestone does not verify persistent Work runtime storage, direct Skill
writes to Projects or Library, or deterministic image generation. The verified
web lifecycle remains transient assembly, user-controlled download, and
fresh-chat attachment import.

## Revision note

The next feature revision after `v0.4.0` is `v0.5.0`: it adds the optional,
portable bright fine-line gongbi diary treatment and its DIARY prompt assembly
and acceptance guidance. It does not change character schema, storage
semantics, or ONBOARD/AUDIT approval gates.
