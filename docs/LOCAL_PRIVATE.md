# Local Private File Contract

- Project-relative path: `.agent-local/private.env`
- Purpose: private runtime and agent configuration
- Required keys (names only): TBD
- Initialization owner: project maintainer
- Missing-file behavior: stop dependent operations and request configuration; do not fabricate values
- Confidentiality: never commit or print contents; redact logs and reports
- `.agent-local/` must be ignored by Git

Local paths are hints, not credentials. Use secure secret transfer or manual setup on a new machine.
