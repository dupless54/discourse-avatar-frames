# Durable decisions

Load only when eligibility, config compatibility, or Discourse extension behavior is relevant.

- Frame eligibility is server-authoritative and derives from configured trust-level/group conditions; client claims never grant access.
- Invalid/nonexistent/unauthorized frame IDs fail closed.
- Public custom-field output contains selected presentation state only, not internal permission data.
- Settings/config format changes preserve existing installations or require an explicit compatibility/migration plan.
- When touching legacy extension patterns such as `User.class_eval`, verify the current supported Discourse API and refactor only when the task requires it.
- Large frame media trees are exact-asset only for AI inspection.

Do not record temporary PR/CI state here; use `CURRENT_STATE.md` for volatile facts.
