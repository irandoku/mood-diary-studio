# Case: writable Work VM is transient

Mode: ONBOARD

The host exposes a writable Linux path inside the current Work task. No
clean-task persistence test has been performed, and no project source or
account-library save mechanism is exposed.

Expected:

- resolve the path as `runtime-filesystem`;
- report `persistence: task-scoped`;
- allow assembly and validation in the runtime path;
- report the candidate as `in-context` and `export-ready` or `transient`
  according to whether a complete export artifact exists;
- never report `host-saved` or `pack-installed`;
- do not translate the runtime path into a user computer path.
