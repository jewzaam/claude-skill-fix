---
name: fix
description: Run make check and fix issues, optionally in a submodule
allowed-tools: Bash, Read, Edit, Glob, Grep
---

# Fix Skill

## Purpose

Run `make check` to validate code and automatically fix any issues found. Supports working in submodules.

## Process

1. **Determine working directory:**
   - If no arguments: work in current directory
   - If argument provided: check if it's a submodule directory and cd into it

2. **Run `make check`:**
   - Always use `make check` — never run naked `make`
   - The `check` target encapsulates all validation (format, lint, coverage, test, typecheck, etc.)
   - If a Makefile exists but has no `check` target, look for and run individual check targets: `format`, `lint`, `coverage`, `test`, `test-unit`, `typecheck`

3. **Fix issues:**
   - Parse error output from make check
   - Identify files and issues
   - Use Read tool to examine code
   - Use Edit tool to fix issues
   - Re-run `make check` to verify

4. **Iterate until clean:**
   - Keep running `make check` and fixing issues
   - Stop when `make check` completes successfully

## Critical Rules

- **NEVER run naked `make`** - always use `make check` to avoid unnecessary permission prompts
- **NEVER run git commands** - no add, commit, push, pull, etc.
- **Fix code only** - make changes to source files and tests
- **Verify fixes** - always re-run `make check` after changes
- **Read before editing** - always read files before making changes
