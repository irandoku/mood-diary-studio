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

## Current host evidence

| Host | Evidence level | Verified scope |
|---|---|---|
| Codex Desktop on macOS | Host verified | Local Skill discovery; image-based ONBOARD; review-gated `local-filesystem` installation with relative reference resolution and post-write re-read; DIARY with an approved installed character card; model-neutral prompt delivery |
| Codex Desktop on macOS | Behavior tested | Public-safe AUDIT and existing-target acceptance cases, including absolute-path binding and byte-identical idempotent installation |
| ChatGPT Work on web | Host verified | Uploaded Skill package discovery; image-based ONBOARD; review-gated `manual-export` with an approved character card and byte-identical reference image; validated ZIP download; cross-chat character-package import; DIARY brief and model-neutral prompt delivery |
| Hermes | Specified only | Not yet behavior tested or host verified |

The Codex Desktop and ChatGPT Work verifications were completed on 2026-07-26.
Image rendering was requested separately through each host after DIARY delivered
its prompt; rendering is not a capability of this Skill. In both hosts, the
approved character anchors remained recognizable in the rendered result without
turning contextual work clothing into a permanent identity requirement.

On ChatGPT web, installed Skills were available in Work but not in ordinary
Chat during verification. Work exposed a writable cloud VM filesystem for
temporary assembly and validation, but a fresh Work chat used a different host
and could not read files created in the prior VM. It also could not read a file
from the user's macOS `/tmp` at the same path. These runtime paths are not
verified persistent character-pack bindings: the tested web workflow correctly
reported `manual-export` and `not installed`, then reloaded the downloaded
package as a chat attachment in a fresh Work chat.

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
