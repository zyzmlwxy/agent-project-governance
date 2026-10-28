# Local Private File Contract

- Project-relative path: `.agent-local/private.env`
- Purpose: private runtime and agent configuration
- Required keys (names only): TBD
- Initialization owner: project maintainer
- Missing-file behavior: stop dependent operations and request configuration; do not fabricate values
- Confidentiality: never commit or print contents; redact logs and reports
- `.agent-local/` must be ignored by Git

Local paths are hints, not credentials. Use secure secret transfer or manual setup on a new machine.

## Safe local path references
Git may record a verified local path **reference** to a credential file (for example `.agent-local/ssh/nas_key`) or an environment variable naming that path, if the path itself is safe to disclose in the repository. Never commit the key, passphrase, token, contents of secret-bearing SSH configuration, or raw sensitive logs. In public repositories, prefer relative paths and aliases; keep identity-bearing absolute paths in ignored local private files and record only their safe reference in Git. A path reference is not permission to read or use the credential.
