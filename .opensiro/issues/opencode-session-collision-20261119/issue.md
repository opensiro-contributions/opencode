# anomalyco/opencode — Upstream #58 independent Human decision

**Target transition:** NO_QUALIFIED_C_TARGET
**Proposal-stage decision:** NO_GO
**Research disposition:** NO_USEFUL_CHANGE

[roadmap.md](roadmap.md) — canonical receipt; [constructor-sufficiency.md](constructor-sufficiency.md) — technical AI contract. Internal draft, NOT PUBLISHED.

## Accepted baseline and current source

Accepted historical [Index review](https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/assessments/op/opencode.md) (2026-09-15, Profile 0.2.1, Skills 0.3.1; blob `60cd4ec5d2dd5ba620c815e3579d198ab5274036`). Original current [HEAD](https://github.com/anomalyco/opencode/commit/b4d81f04ad350b9a9de7ec97af3ce93ecb5c5e2c) is separately pinned and not automatically reclassified.

| Function / role | Historical Index state | Current owner/closure | Priority / candidate |
| --- | --- | --- | --- |
| **S1 · Operations** | A | standard agent performs autonomous tool operations and responds to results | NO_TARGET / DEFER |
| **S2 · Coordination** | — | nested task delegation lacks independent peer interference regulator | NO_TARGET / DEFER |
| **S3 · Current regulation** | — | parent-child control alone is not full-workspace S3 | NO_TARGET / DEFER |
| **S3* · Independent audit** | — | no protected independent corrective review evidenced | NO_TARGET / DEFER |
| **S4 · Prospective environment** | — | current coding exploration is not future environmental analysis | NO_TARGET / DEFER |
| **S5 · Ultimate identity/policy** | — | human/deployer governance and configured permissions retain ultimate policy right | NO_TARGET / DEFER |

## Operator question and answer

Avoid one concurrent session's undo reverting another session's edits and prevent shared-store corruption. Track A native: Open session undo conflict and shared SQLite filesystem failures are tracked in original Issues. Open PR #64359 handles parent/subagent rollback tracking, #63475 handles pruned snapshot safety; none is merged proof of completed conflict fix.. Track B: No added autonomous S2=C controller at this stage; prefer source-native rollback ownership, optimistic conflict checks/transaction boundaries and filesystem-safe storage investigation in tracked Issues/PRs.. **NO_GO** because After scoped native snapshot and rollback fixes, a reproducible peer coordination problem still needs a developer-composed autonomous negotiator choosing among conflicting session commitments and feeding a lawful new work plan back to both sessions remains unproven and the existing native work is better scoped. This is not a claim the original issues were resolved.

## Evidence and next step

Original [packages/core/src/session/revert.ts](https://github.com/anomalyco/opencode/blob/b4d81f04ad350b9a9de7ec97af3ce93ecb5c5e2c/packages/core/src/session/revert.ts); [packages/core/src/session/session.ts](https://github.com/anomalyco/opencode/blob/b4d81f04ad350b9a9de7ec97af3ce93ecb5c5e2c/packages/core/src/session/session.ts); [specs/v2/session.md](https://github.com/anomalyco/opencode/blob/b4d81f04ad350b9a9de7ec97af3ce93ecb5c5e2c/specs/v2/session.md); native links [issues / 33940](https://github.com/anomalyco/opencode/issues/33940); [issues / 56282](https://github.com/anomalyco/opencode/issues/56282); [pull / 64359](https://github.com/anomalyco/opencode/pull/64359); [pull / 63475](https://github.com/anomalyco/opencode/pull/63475). P1: Compare active #64359/#63475 actual patches and original #33940/#56282 reproduction; determine independent peer conflict ownership only after base bugs fixed. Prior OpenCode case NO_GO on native-first S2; current source tree moves task behavior to core and open rollback PRs continue to cover the bounded need. No independent novel C requirement emerges.. New tests NOT_RUN, cost NOT_MEASURED. No third-party publication, source edit or Index regrade. Owner ACTIVE/ALLOW applies to internal fork meta only. AI-assisted draft.
