---
name: task-packet
description: Compress a non-trivial task into the minimum execution context before broader reads.
---
# Task packet

Goal:
Allowed paths:
Relevant context:
Acceptance:
Validation:
Risk:
Effort tier:
Escalation trigger:

Rules:
- Target 12 lines or fewer, but exceed that target whenever correctness, eligibility/security, config compatibility, or acceptance detail would otherwise be lost.
- Resolve locations from `docs/ai/REPO_MAP.md` first; it is a navigation hint, never authority. If stale or inconsistent with current source/tests, use targeted search and trust current source/tests.
- Do not scan media trees first. Inspect exact assets only when named or required by the task.
- Read `DECISIONS.md` only for eligibility/config/extension behavior; read `COMMANDS.md` only for validation.
- Prefer symbol/search -> targeted range -> exact asset.
- Minimum context is adaptive, not fixed: if a change crosses trust/group eligibility, config parsing/migration, public custom fields, extension APIs, CSS/URL safety, or another subsystem boundary, load the relevant local `AGENTS.md`, source, and tests/static evidence.
- Select T0/T1/T2/T3 from `docs/ai/EFFORT_ROUTER.md` before broad reads. Use a platform-native worker when supported and useful; do not spawn parallel workers unless tasks are genuinely independent.
- Do not carry history or long reasoning into the packet.
- Reuse equivalent user-supplied scope/acceptance; skip the packet for trivial one-file, low-risk edits.
- Absence of CI is never GREEN. When no required workflow/check exists, use targeted validation plus exact diff/scope validation and report `NO_CI`/`NOT_RUN` honestly.
- Correctness and safety outrank token savings; expand context when evidence is insufficient.
