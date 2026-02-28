# gemini-home

Safe-to-share baseline for a Gemini home directory.

## What this repo tracks

- `GEMINI.md` (global AI safety guardrails and instructions)

## What this repo does not track

The `.gitignore` blocks local state, logs, and machine-specific data:

- `antigravity/annotations/`, `antigravity/brain/`, `antigravity/code_tracker/`
- `antigravity/context_state/`, `antigravity/conversations/`
- `antigravity/html_artifacts/`, `antigravity/implicit/`
- `antigravity/knowledge/`, `antigravity/playground/`
- `antigravity/installation_id`, `antigravity/user_settings.pb`

## Bootstrap on a new machine

1. Back up existing `~/.gemini` if present.
2. Clone this repo into `~/.gemini`.
3. Start Gemini CLI or Antigravity and authenticate locally.

## Safety checks before sharing publicly

- Run `git status` and `git diff --cached` before each commit.
- Never force-add ignored files.
- If a secret is ever committed, rotate it immediately.
