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

Stop for unresolved permission model, config migration, security, or product decisions. Preserve unrelated work and `.claude/settings.local.json`; no force-push/reset/clean/branch deletion/deploy/destructive production actions. Prefer targeted reads/diffs.

## CI-only merge gate
Claude/Gemini/Codex reviewer or verifier approval is not required and must never block merge. Do not request or wait for AI approvals as a merge condition.

For a normal scoped PR, the merge gate is CI only:
- validate exact changed paths still match the task;
- use only the latest exact PR head SHA;
- require the repository's official required Discourse CI workflow/checks on that exact head to conclude GREEN;
- a new commit invalidates all older CI evidence;
- `NO_CI`, missing, skipped, pending, cancelled, neutral, stale-head, or failed checks are not GREEN.

When the latest exact head is GREEN and no unresolved security/schema/product/architecture blocker remains, the agent is pre-authorized to merge without another user confirmation. Prefer squash merge with `expected_head_sha` when supported. Never weaken tests or broaden scope just to obtain GREEN.

Task procedures live under `.agents/skills/` and load on demand; use `task-packet` for non-trivial work.

## Adaptive model / effort routing
Classify execution risk with `docs/ai/EFFORT_ROUTER.md` before broad reads. Start at the lowest sufficient tier: T0 mechanical, T1 routine, T2 high-risk, T3 exceptional. Escalate for risk/ambiguity rather than task size, and de-escalate when the risky phase ends. Use platform-native workers under `.claude/agents/` or `.codex/agents/` when supported; never trade away correctness, permission safety, or validation to save tokens.

## Live Discourse developer source gate

Canonical live upstream index: https://meta.discourse.org/t/developer-guides-index/308036?tl=en

For any Discourse-version-sensitive implementation, refactor, review, or compatibility decision:
- start at the live Developer Guides Index and open only the task-relevant official topic(s);
- for plugin work prioritize **Code & Internals + Plugins**; for theme work prioritize **Code & Internals + Themes & Components / Theme Developer Tutorial**; use environment/general guides only when relevant;
- verify version-sensitive APIs and deprecations against current `discourse/discourse` core or the current official plugin/theme skeleton before coding when needed;
- current official docs/core beat remembered examples, old snippets, and copied local guidance unless the repo deliberately targets an older validated release via `.discourse-compatibility` / d-compat;
- do not preload the full index: read the nearest local rules and target source/tests first, then fetch only the upstream guide(s) needed for the current choice.
