# Gemini + Antigravity Parity Execution Plan

## Current-State Gaps
- Rust skills were missing from `skills/`.
- `python-developer` and `python-tester` diverged from Cursor canonical content.
- `skills-manifest.lock.json` was missing.
- `antigravity/mcp_config.json` was empty.
- Transient browser runtime state (`antigravity-browser-profile/`) was not ignored.
- No CI workflow existed for docs/config/manifest validation.

## Ordered Implementation Steps
1. Sync all shared `skills/*/SKILL.md` files from Cursor canonical source.
2. Add Rust skills (`rust-developer`, `rust-tester`) to match shared catalog.
3. Keep Gemini-specific safety gate in `GEMINI.md` unchanged.
4. Maintain medium guardrail parity with Cursor/Codex for shared safety behavior.
5. Generate `skills-manifest.lock.json` for drift detection.
6. Populate `antigravity/mcp_config.json` from a declared baseline (non-empty, valid JSON).
7. Add `antigravity-browser-profile/` to `.gitignore`.
8. Add workflow validation for markdown/links/manifest plus Gemini-specific config checks.
9. Establish sync cadence from Cursor canonical skills.

## Validation Checklist
- [ ] `skills/` includes all 14 shared skills.
- [ ] `python-*` skills match Cursor canonical bodies.
- [ ] `skills-manifest.lock.json` hashes match local skill files.
- [ ] `antigravity/mcp_config.json` is non-empty and valid JSON.
- [ ] `.gitignore` excludes transient browser profile state.
- [ ] Workflow checks pass.

## Rollback Notes
- Revert synced skill files from git if parity strategy changes.
- Restore previous `mcp_config.json` if MCP baseline needs redesign.
- Revert `.gitignore` line for `antigravity-browser-profile/` only if intentionally tracking local browser state.
- Restore prior workflow definition if CI scope is reduced.

## Ongoing Maintenance Cadence
- **Per canonical update:** pull skill updates from Cursor and regenerate manifest.
- **Weekly:** compare Gemini manifest with Cursor manifest for drift.
- **Monthly:** review GEMINI guardrails and MCP baseline validity.
