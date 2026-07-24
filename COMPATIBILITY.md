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
