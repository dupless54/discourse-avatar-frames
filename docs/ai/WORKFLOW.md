# Multi-model quality workflow
Default: Claude Builder -> ChatGPT/Codex independent Reviewer -> Gemini mandatory Final Verifier. Reviewer independently uses locked task + rules + latest diff + available test/static evidence. Merge only after all approvals, exact-path validation, and latest exact PR-head CI green where CI exists; disagreement requires human arbitration.
