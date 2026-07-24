# Character Storage Profiles

Separate the logical character-pack schema from the host-specific place that supplies or stores it. Never assume a universal directory.

## Contents

- Binding fields
- Storage profiles
- Resolution order
- Status language

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
- `persistence`: `skill-scoped`, `persistent`, `workspace-scoped`, `host-managed`, `chat-scoped`, or `user-controlled-after-export`;
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

Use when the host can read and write an exact user-approved directory.

- Persistence: `persistent`.
- Read: according to host permission.
- Write: only after candidate or patch approval.
- Locator: an exact path supplied by the user or authorized workspace context.

### workspace-files

Use for a host-controlled workspace with file capabilities but no general filesystem assumption.

- Persistence: `workspace-scoped`.
- Read and write: according to workspace permission.
- Locator: the host's authorized workspace-relative location.
- Rule: do not translate it into an invented local absolute path.

### managed-project

Use for a host-managed project or knowledge area that exposes selected files as context.

- Persistence: `host-managed`.
- Read: yes when the files are attached to the project context.
- Direct Skill write: no unless the host explicitly exposes and authorizes it.
- Locator: a logical label such as `project-sources`.
- Rule: return artifacts for the user or host to add; do not claim a filesystem installation.

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

1. Use a binding explicitly supplied in the current request.
2. Otherwise use a binding already established in the current authorized workspace or project context.
3. Otherwise derive `chat-attachments` only when the current character files are attached.
4. Otherwise use `manual-export`.

Do not search arbitrary directories, infer a path from platform conventions, or reuse an uncertain binding from another project.

## Status language

Use these states precisely. A state describes the character card being read or
produced, not merely a reference image used to draft it:

- `bundled-sample` — public read-only fixture shipped with the Skill;
- `available-in-context` — an existing character card is readable in a project, workspace, or chat but is not installed into a character pack;
- `not-installed` — candidate exists but no persistent install occurred;
- `export-ready` — a complete new candidate or revision artifact is ready for host-managed or manual saving;
- `installed` — the approved plugin was written to a persistent pack and re-read successfully;
- `not-applied` — an audit patch was proposed but not written.

For example, a managed-project reference image can be available in context while
a newly drafted candidate card remains `export-ready`. Use
`available-in-context` only when the character card itself is already readable
from that context.

Never report `installed` based only on generating, uploading, attaching, or displaying a candidate card.
