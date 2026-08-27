# Discourse Avatar Frames Agent Router

Canonical instructions for ChatGPT/Codex, Claude, and Gemini.

## Context routing
Current source/tests > `docs/ai/CURRENT_STATE.md` > nearest local `AGENTS.md` > stable docs > plans/history. Read only the task surface:
- Discourse/Glimmer frame preferences/connectors -> `assets/javascripts/discourse/AGENTS.md`
- shipped frame images -> `public/AGENTS.md`
Use the minimal three-file work packet only for genuine multi-session work.

## Fast task path
For non-trivial work, use `.agents/skills/task-packet/SKILL.md` before broad reads. Use `docs/ai/REPO_MAP.md` to locate code/assets, `COMMANDS.md` only for validation, and `DECISIONS.md` only for eligibility/config/extension choices. Skip the formal packet for trivial one-file edits.

## Product/security invariants
This plugin lets users select public avatar-frame custom-field values, with server-side eligibility based on configured trust-level/group conditions.

- Server-side permission validation is authoritative; client UI only presents available choices.
- Invalid/nonexistent frame IDs and unauthorized frames fail closed.
- Do not trust client-supplied trust level, group membership, or permission state.
- The public custom field should expose only the selected frame identifier/presentation state, not internal authorization data.
- Changes to the settings parser/config format must preserve existing installations or include an explicit migration/compatibility plan.
- Avoid raw HTML/CSS/URL injection from frame IDs/config values.
- Current code uses older patterns such as `User.class_eval`; when touching that area verify current supported Discourse extension APIs and migrate only if the task actually requires it.
- User-visible validation messages should follow current Discourse localization conventions when changed.
- Large media tree: inspect only exact assets needed by the task; do not bulk process for context.

## Implementation/tests/safety
Use current Discourse APIs verified from source, smallest scoped changes, and server-authoritative validation. Test allowed/denied/unknown frame paths and relevant trust/group boundaries when behavior changes. Never claim unrun tests passed; use static/source validation when no suite exists.

Stop for unresolved permission model, config migration, security, or product decisions. Preserve unrelated work and `.claude/settings.local.json`; no force-push/reset/clean/branch deletion/deploy/destructive production actions. Remote writes only when explicitly authorized. Prefer targeted reads/diffs.

Task procedures live under `.agents/skills/` and load on demand; use `task-packet` for non-trivial work.

## Adaptive model / effort routing
Classify execution risk with `docs/ai/EFFORT_ROUTER.md` before broad reads. Start at the lowest sufficient tier: T0 mechanical, T1 routine, T2 high-risk, T3 exceptional. Escalate for risk/ambiguity rather than task size, and de-escalate when the risky phase ends. Use platform-native workers under `.claude/agents/` or `.codex/agents/` when supported; never trade away correctness, permission safety, or validation to save tokens.
