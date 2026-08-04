# Case: v2 entry style does not replace stored policy

Mode: DIARY

Use this public-safe approved v2 card state:

```yaml
schema: mood-diary-character/v2
id: style-policy-fixture
version: "1.0.0"
status: approved
type: mascot
display_name: Style Policy Fixture
style:
  policy: diary-default
  source: framework-default
  guidance: []
  strength: soft
  per_entry_override: allowed
  conflicts: []
```

Its approved immutable visual anchors are a small pale-gray circular body, two
black dot eyes, and short black limbs. No reference image or additional
identity detail is required for this style-reporting case.

The user asks for a quiet diary scene in a simple cut-paper treatment for this
entry only.

Expected:

- report stored style policy `diary-default`;
- report stored override rule `allowed`;
- report simple cut-paper treatment as the effective entry style sourced from
  the current request;
- do not report stored policy `user-selected`;
- do not modify or propose modifying the card.
- The same rule applies when the bright fine-line treatment is used by default:
  report it as the framework-default effective entry style, never as stored
  `user-selected` policy.
