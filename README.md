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

## Operations (day-2)

### New machine setup verification checklist

After bootstrap, verify the machine is actually usable end-to-end:

- **Auth present**
  - Confirm auth tokens are present (e.g., `antigravity/installation_id`).
  - Run a simple command and confirm there is no auth prompt loop.
- **Rules loaded**
  - Confirm `GEMINI.md` is present and reflects expected safety rules.
- **Skills visible**
  - Ensure your user skills are present under `skills/`.
  - Start Antigravity and verify expected skills/tools are listed.
- **Sample prompt works**
  - Run a small "smoke" prompt (for example: ask for a summary of `README.md`) and confirm response + file access are working.

### Upgrade path (safe pulls)

Use this sequence whenever updating from upstream:

1. Inspect local changes:
   - `git status`
2. If you have local edits, either commit them on a branch or stash safely:
   - `git stash push -u -m "pre-upgrade $(date +%F)"`
3. Fetch and fast-forward:
   - `git fetch origin`
   - `git pull --ff-only`
4. Re-apply local changes (if stashed):
   - `git stash pop`

### Disaster recovery (restore + re-authenticate)

If the working copy becomes corrupted or misconfigured:

1. Preserve anything you may need:
   - `cp -a ~/.gemini ~/.gemini.backup.$(date +%F-%H%M%S)`
2. Re-clone a clean copy of this repo into `~/.gemini`.
3. Restore any machine-specific edits from backup.
4. Re-authenticate (generates fresh auth state).
5. Validate with the checklist above (auth/rules/skills/sample prompt).

### Troubleshooting matrix (IDE integrations)

| Symptom | Likely cause | What to check/fix | Local logs/state location |
| --- | --- | --- | --- |
| Extension cannot connect | Wrong workspace path | Verify extension points to `~/.gemini` | `~/.gemini/` |
| Repeated auth prompts | Missing/expired auth | Re-authenticate and confirm state recreated | `~/.gemini/antigravity/` |
| Skills missing in UI | Skills not installed/synced | Check `skills/` contents and restart extension | `~/.gemini/skills/` |

## Safety checks before sharing publicly

- Run `git status` and `git diff --cached` before each commit.
- Never force-add ignored files.
- If a secret is ever committed, rotate it immediately.
