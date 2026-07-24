# Compatibility

Mood Diary Studio targets the open Agent Skills directory and `SKILL.md` conventions. Portability is a capability claim, not a promise that every host has been behavior-tested.

## Required host capabilities

| Capability | DIARY | ONBOARD | AUDIT |
|---|---:|---:|---:|
| Load `SKILL.md` and relative files | Required | Required | Required |
| Read user-provided text | Required | Required | Required |
| Inspect local or attached images | Optional | Required for image onboarding | Required when auditing images |
| Return complete Markdown artifacts | Required | Required | Required |
| Request approval before file writes | Required for writes | Required for install | Required for updates |

If image inspection is unavailable, the host must not convert guesses into observations. It may ask the user for a textual visual inventory, but must label that inventory as user-provided evidence.

## Storage capability mapping

| Host capability | Storage profile | Expected result |
|---|---|---|
| Exact persistent path with read/write permission | `local-filesystem` | Can install after review and approval |
| Controlled workspace files | `workspace-files` | Can install only when the workspace exposes an approved write target |
| Managed project or knowledge sources | `managed-project` | Read in context; return an artifact for host-managed saving |
| Conversation attachments only | `chat-attachments` | Read in the current chat; do not claim installation |
| No persistent readable or writable storage | `manual-export` | Return the complete artifact |

`bundled-assets` is reserved for the Skill's public samples and templates. It is always read-only and never a private-character destination.

## Evidence levels

- **Specified** — the framework defines behavior for the host capability.
- **Statically validated** — the Skill structure and references pass validation.
- **Behavior tested** — the mode completed a public-safe acceptance case in a clean context.
- **Host verified** — the packaged Skill completed the workflow in the named host.

Do not promote one evidence level into another.

## Runtime neutrality

The portable core contains no:

- executable scripts;
- network calls;
- package dependencies;
- MCP requirements;
- model-specific parameters;
- absolute filesystem paths; or
- vendor-specific activation metadata.

ChatGPT, Claude Code, Codex, Hermes, and other clients may use different installation and file-access mechanisms. Those mechanisms are outside the core contract. Record a host as verified only after testing the packaged Skill there.

Product features and permission models can change. Resolve the actual capabilities of the current host rather than inferring them from its brand name.
