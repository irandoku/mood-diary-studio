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

### Chat attachments

Use `chat-attachments` for one-off analysis. The character is `available-in-context`, not installed. Return a candidate card for download, project saving, or later local installation.

### Manual export

Use `manual-export` when no persistent binding exists. The complete candidate is `export-ready`; the user decides where to save it.

## Safe local installation workflow

1. Supply the exact pack path or storage destination.
2. Confirm the storage profile is readable, writable, and persistent.
3. Confirm the target character ID.
4. Check whether the target already exists.
5. Review the complete candidate card or proposed diff.
6. Approve installation or revision explicitly.
7. Write only to the approved target.
8. Re-read the saved card and report the result as `installed`.

If the host cannot write files, return the complete candidate or patch for manual saving. Do not substitute another location.

## Sharing

Share a character plugin only when every included setting and reference image is authorized for that audience. The framework license does not grant rights to private character packs.
