# Fix Skill

This repo contains the `fix` agent skill, which runs project checks and fixes reported issues.

## Key Convention

- **Always use `make check`** — never run naked `make`. Projects encapsulate all validation targets (format, lint, test, coverage, typecheck) under `make check`. Running `make` without a target triggers a user permission prompt, which is disruptive. The `check` target avoids this.
- `make check` is also typically the default target in project Makefiles (so `make` at the command line runs checks), but agents should always explicitly specify the `check` target.
