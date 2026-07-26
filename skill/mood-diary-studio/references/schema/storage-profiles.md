# Character Storage Profiles

Separate the logical character-pack schema from the host-specific place that supplies or stores it. Never assume a universal directory.

## Contents

- Binding fields
- Storage profiles
- Resolution order
- State language

## Binding

Describe the active storage context:

```yaml
storage:
  profile: local-filesystem
  locator: /exact/user-approved/character-pack
  persistence: persistent
  readable: true
  writable: true
  authority: user-provided
```

Use these field types and values:

- `profile`: one of the profile names defined below;
- `locator`: a host-valid string, or `none` for `manual-export`;
- `persistence`: `skill-scoped`, `persistent`, `workspace-scoped`,
  `host-managed`, `account-scoped`, `task-scoped`, `chat-scoped`, or
  `user-controlled-after-export`;
- `readable`: a boolean describing current host capability;
- `writable`: a boolean describing current host capability, not approval to write;
- `authority`: `user-provided`, `authorized-context`, or `host-context`.

## Profiles

### bundled-assets

Use for public samples and templates shipped inside the Skill.

- Persistence: `skill-scoped`.
- Read: yes.
- Write: never.
- Locator: a relative path under `assets/`.
- Rule: never install private or user-created characters here.

### local-filesystem

Use when the host exposes an exact absolute path that it can read or write.

- Persistence: `persistent`.
- Read: according to host permission.
- Write: only after candidate or patch approval.
- Locator: the exact absolute path supplied by the user or authorized context.
- Rule: an explicitly supplied absolute path remains `local-filesystem` even
  when it happens to be inside the current workspace.

### workspace-files

Use for a host-controlled workspace with file capabilities but no general filesystem assumption.

- Persistence: `workspace-scoped`.
- Read and write: according to workspace permission.
- Locator: the host's authorized workspace-relative location.
- Rule: use this profile only when the host supplies a workspace-relative
  binding; do not translate it into an invented local absolute path.

### managed-project

Use for a host-managed project or knowledge area that exposes selected files as context.

- Persistence: `host-managed`.
- Read: yes when the files are attached to the project context.
- Direct Skill write: no unless the host explicitly exposes and authorizes it.
- Locator: a logical label such as `project-sources`.
- Rule: return artifacts for the user or host to add; do not claim a filesystem installation.

### account-library

Use for an account- or workspace-managed file library that can supply saved
files to later conversations.

- Persistence: `account-scoped` for a personal library or `host-managed` for a
  workspace library.
- Read: only after the exact file is selected or attached to the current task.
- Direct Skill write: no unless the host exposes and authorizes a verifiable
  save mechanism.
- Locator: a host-valid file identifier or unique filename, never an invented
  local path.
- Rule: a file visible in a library may be `host-saved` without being
  `in-context` or installed in a character pack.

### runtime-filesystem

Use for a task VM, sandbox, container, or temporary filesystem that has not
been verified across a fresh task.

- Persistence: `task-scoped`.
- Read and write: according to current task capability.
- Locator: the exact runtime path.
- Rule: use only for assembly, validation, and packaging. Never call a runtime
  path persistent or `pack-installed` without a clean-task persistence test.

### chat-attachments

Use for files attached to the current conversation.

- Persistence: `chat-scoped`.
- Read: yes while available to the conversation.
- Write: no.
- Locator: attachment filenames or host file identifiers.
- Rule: a character is available in context, not installed.

### manual-export

Use when no readable persistent pack binding exists or the host cannot write.

- Persistence: `user-controlled-after-export`.
- Read: only current inputs.
- Write: no.
- Locator: `none`.
- Rule: return the complete candidate plugin or patch for manual saving.

## Resolution order

1. Use a binding explicitly supplied in the current request. An accessible
   absolute path resolves to `local-filesystem`; a host-supplied
   workspace-relative binding resolves to `workspace-files`.
2. Otherwise use a binding already established in the current authorized workspace or project context.
3. Otherwise use an exact account-library file selected for the current task.
4. Otherwise derive `chat-attachments` only when the current character files are attached.
5. Treat an unverified task VM or sandbox as `runtime-filesystem`.
6. Otherwise use `manual-export`.

Do not search arbitrary directories, infer a path from platform conventions, or reuse an uncertain binding from another project.

## State language

Report availability and persistence separately. States describe the character
card or complete plugin, not merely a reference image.

`availability_state`:

- `in-context` — the exact card is readable in the current task;
- `not-in-context` — the card may exist elsewhere but is not readable now;
- `unknown` — current readability has not been verified.

`persistence_state`:

- `bundled-sample` — public read-only fixture shipped with the Skill;
- `transient` — exists only in current task, chat, or unverified runtime storage;
- `export-ready` — complete artifact is ready for user-controlled or
  host-managed saving, but saving has not been verified;
- `host-saved` — the exact artifact was verified in host-managed persistent
  storage, but not installed into a character pack;
- `pack-installed` — the approved plugin is present in an approved persistent
  pack and was re-read successfully, either after an approved write or after
  verifying that an existing target is byte-identical;
- `not-applied` — an audit patch was proposed but not written or saved.

Examples:

- a new candidate returned in a managed project:
  `availability_state: in-context`, `persistence_state: export-ready`;
- a Library file not selected in the current chat:
  `availability_state: not-in-context`, `persistence_state: host-saved`;
- a card attached to the current chat:
  `availability_state: in-context`, `persistence_state: transient`;
- an approved local pack re-read after installation:
  `availability_state: in-context`, `persistence_state: pack-installed`.

Legacy v1 output labels may be read as follows:

- `available-in-context` maps to `availability_state: in-context` with
  persistence determined from the binding;
- `export-ready` maps to `persistence_state: export-ready`;
- `installed` maps to `persistence_state: pack-installed` only when the
  persistent re-read evidence is present;
- `not-applied` maps to `persistence_state: not-applied`;
- `not-installed` is ambiguous and must not be emitted by new outputs.

Never report `host-saved` from a generated download link alone. Never report
`pack-installed` based on generating, uploading, attaching, exporting,
displaying, or saving a file in Library or project sources. When installation
is an idempotent no-op, state explicitly that no write was performed.
