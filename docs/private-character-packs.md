# Private Character Packs

Keep private characters outside the public framework repository.

`skill/mood-diary-studio/assets/sample-character/` contains a public read-only fixture. Do not place private characters beside it.

## Recommended layout

```text
my-character-pack/
├── character-a/
│   ├── character.md
│   └── references/
└── character-b/
    ├── character.md
    └── references/
```

Do not commit private cards and later rely on `.gitignore`. Content already committed can remain in Git history after deletion.

## Select a storage profile

### Local filesystem

Use when an agent can access an exact approved path:

```yaml
storage:
  profile: local-filesystem
  locator: /exact/user-selected/mood-diary-characters
  persistence: persistent
  readable: true
  writable: true
  authority: user-provided
```

The path is an example shape, not a framework default. Each user chooses and authorizes the real location.

### Controlled workspace

Use `workspace-files` when a host exposes a limited project workspace. Supply a workspace-relative locator and respect its permissions. Do not invent a local absolute path.

### Web project or managed knowledge area

Use `managed-project` when a web host makes selected files available as project sources:

```yaml
storage:
  profile: managed-project
  locator: project-sources
  persistence: host-managed
  readable: true
  writable: false
  authority: host-context
```

Upload or select `character.md` and its reference images as project sources. Use explicit unique filenames because folder-relative paths may not be preserved. Return revised cards as artifacts for the user or host to save.

Treat project creation, adding sources, replacing files, and deletion as user
or host operations unless the current host exposes and verifies those exact
actions. A UI feature does not by itself prove that a Skill can invoke it.

### Account or workspace library

Use `account-library` when the host saves files for later reuse across
conversations:

```yaml
storage:
  profile: account-library
  locator: character-a-pack-v1.0.0.zip
  persistence: account-scoped
  readable: false
  writable: false
  authority: host-context
```

Set `readable: true` only after the exact file is selected for the current task.
After verifying the saved bytes, report `host-saved`; do not report
`pack-installed`. Use unique filenames containing character ID and version.

### Runtime filesystem

Use `runtime-filesystem` for a cloud task VM, sandbox, or temporary container.
It may be writable and useful for assembling or validating a ZIP, but it remains
`task-scoped` and `transient` until a clean-task test proves otherwise. Never
substitute it for the user's persistent pack.

### Chat attachments

Use `chat-attachments` for one-off analysis. The exact card may be
`in-context`, but its persistence is `transient`. Return a candidate card for
download, project saving, or later local installation.

### Manual export

Use `manual-export` when no persistent binding exists. The complete candidate
has `persistence_state: export-ready`; the user decides where to save it.

## Reference fidelity across hosts

A web host may normalize an uploaded image before exposing it to a Skill. Keep
three claims separate:

- **attachment-byte identity** — the exported reference matches the bytes the
  active host exposed to the task;
- **source-byte identity** — the exported reference matches the user's original
  file outside the host;
- **pixel identity** — decoded dimensions and color pixels match even if PNG
  channel layout, metadata, or compression differs.

Verify ZIP CRC, reference paths, and attachment-byte identity during export.
When the original file is available after download, compare it separately.
For example, adding a fully opaque alpha channel can preserve every RGB pixel
while changing the file hash. Report that result as pixel-identical, not
byte-identical. Do not silently replace the exported reference merely to make
hashes match.

## Host-managed lifecycle governance

Use stable, collision-resistant names:

```text
<character-id>-character-v<plugin-version>.md
<character-id>-pack-v<plugin-version>.zip
<character-id>-ref-<view>-<number>.<extension>
```

Do not treat a matching filename as an update. Compare character ID, schema,
plugin version, complete file set, and file contents. If comparison is
unavailable, keep both artifacts and report the ambiguity.

Treat each lifecycle action separately:

- **Save** — requires candidate approval and verification of the exact
  host-managed artifact before `host-saved`.
- **AUDIT update** — returns a versioned artifact or patch; it does not replace
  the prior version automatically.
- **Delete** — requires the exact locator, impact explanation, and separate
  approval. Never infer deletion from deprecation or a newer version.
- **Export** — preserve `character.md`, authorized references, schema version,
  plugin version, and relative relationships in a portable ZIP when possible.

Project, Library, sharing, training, residency, and retention behavior belongs
to the active host and workspace policy. Report only capabilities verified for
the current context. Prefer a private, character-scoped project or knowledge
area when the host supports isolation, but do not claim that the Skill can
create or configure it.

## Safe local installation workflow

1. Supply the exact pack path or storage destination.
2. Confirm the storage profile is readable, writable, and persistent.
3. Confirm the target character ID.
4. Check whether the target already exists.
5. Review the complete candidate card or proposed diff.
6. Approve installation or revision explicitly.
7. Write only to the approved target.
8. Re-read the saved card and report `persistence_state: pack-installed`.

If the host cannot write files, return the complete candidate or patch for manual saving. Do not substitute another location.

## Sharing

Share a character plugin only when every included setting and reference image is authorized for that audience. The framework license does not grant rights to private character packs.
