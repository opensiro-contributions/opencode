# anomalyco/opencode — AI constructor feasibility and falsifier

**Target transition:** NO_QUALIFIED_C_TARGET
**Proposal-stage decision:** NO_GO
**Research disposition:** NO_USEFUL_CHANGE

Human [issue.md](issue.md), canonical [roadmap.md](roadmap.md). Internal PLAN_ONLY draft; historical grades only in canonical receipt/Human.

## Boundary and functional counterfactual

OpenCode native core Session/Revert/Snapshot mechanisms and concurrent coding sessions sharing a workspace; excludes out-of-tree plugin coordination and project governance. Question: Avoid one concurrent session's undo reverting another session's edits and prevent shared-store corruption. First-party sources [packages/core/src/session/revert.ts](https://github.com/anomalyco/opencode/blob/b4d81f04ad350b9a9de7ec97af3ce93ecb5c5e2c/packages/core/src/session/revert.ts); [packages/core/src/session/session.ts](https://github.com/anomalyco/opencode/blob/b4d81f04ad350b9a9de7ec97af3ce93ecb5c5e2c/packages/core/src/session/session.ts); [specs/v2/session.md](https://github.com/anomalyco/opencode/blob/b4d81f04ad350b9a9de7ec97af3ce93ecb5c5e2c/specs/v2/session.md). If a new model or reviewer is removed, could the native producer/host and existing issue fixes still solve the same concrete task? At present yes for the bounded research stage; there is no independently demonstrated new decision right.

## Track A and Track B

| Function-specific obligation | Existing original path | Smallest future proposal versus no-construction | Falsifier |
| --- | --- | --- | --- |
| Separate lawful decision and evidence | Open session undo conflict and shared SQLite filesystem failures are tracked in original Issues. Open PR #64359 handles parent/subagent rollback tracking, #63475 handles pruned snapshot safety; none is merged proof of completed conflict fix. | No added autonomous S2=C controller at this stage; prefer source-native rollback ownership, optimistic conflict checks/transaction boundaries and filesystem-safe storage investigation in tracked Issues/PRs. | After scoped native snapshot and rollback fixes, a reproducible peer coordination problem still needs a developer-composed autonomous negotiator choosing among conflicting session commitments and feeding a lawful new work plan back to both sessions |
| Applied correction and later operational feedback | Existing first-party state, host permissions and current tool/task loops | Do not add speculative port; fix native defect, then retest separate owner and parent authority | New path adds no unique outcome or cannot enforce lawful correction |

## Engineering and native validation boundary

P1 Compare active #64359/#63475 actual patches and original #33940/#56282 reproduction; determine independent peer conflict ownership only after base bugs fixed; P2 NONE. Consider candidate only if source and maintainer permit actual decision/enforcement feedback on this supported runtime. Do not re-label logging, a named reviewer, task delegation or model catalog change as an autonomous function. Native acceptance scenarios **NOT_RUN**: Two simultaneous sessions editing overlapping and nonoverlapping files; undo/revert preserving other session's data; concurrent SQLite WAL store under supported filesystem; native regression tests NOT_RUN. Negative controls: stale/missing owner, permission denial, baseline compatibility and duplicate/native fix competitor where applicable. Falsifier: After scoped native snapshot and rollback fixes, a reproducible peer coordination problem still needs a developer-composed autonomous negotiator choosing among conflicting session commitments and feeding a lawful new work plan back to both sessions.

## Decision, rights and handoff

**NO_GO / NO_USEFUL_CHANGE**. Prior OpenCode case NO_GO on native-first S2; current source tree moves task behavior to core and open rollback PRs continue to cover the bounded need. No independent novel C requirement emerges.. No implemented constructor, current Index grade, cost result, original-facing Issue/PR or public fork Issue; all external publication DRAFT — NOT PUBLISHED. AI assistance acknowledged.
