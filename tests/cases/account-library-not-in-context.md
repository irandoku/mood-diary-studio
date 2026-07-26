# Case: account-library file is not automatically context

Mode: DIARY

The user says an approved character ZIP exists in their account Library, but it
has not been selected, attached, or exposed to the current task.

Expected:

- resolve `account-library` with a logical locator;
- report `availability_state: not-in-context`;
- do not claim to have read the card or references;
- ask the user or host to select the exact file;
- do not substitute another character or invent a Library write capability;
- do not report `pack-installed`.
