# Private Character Packs

Keep private characters outside the public framework repository.

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

## Safe workflow

1. Supply the exact pack path or storage destination.
2. Confirm the target character ID.
3. Check whether the target already exists.
4. Review the complete candidate card or proposed diff.
5. Approve installation or revision explicitly.
6. Write only to the approved target.
7. Re-read the saved card and report the result.

If the host cannot write files, return the complete candidate or patch for manual saving. Do not substitute another location.

## Sharing

Share a character plugin only when every included setting and reference image is authorized for that audience. The framework license does not grant rights to private character packs.
