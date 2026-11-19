# anomalyco/opencode — Upstream #58 independent v0.18 receipt

- Receipt contract: proposal-gate
- Original repository: anomalyco/opencode
- Original HEAD: b4d81f04ad350b9a9de7ec97af3ce93ecb5c5e2c
- Observed at: 2026-11-19
- Accepted Index assessment: https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/assessments/op/opencode.md
- Accepted assessment blob SHA: 60cd4ec5d2dd5ba620c815e3579d198ab5274036
- Accepted review ref: 95daf90670b7c039c436c85537da5fbfe2205b41
- Accepted reviewed at: 2026-09-15
- Accepted Index commit: c2e43bf4750841277b3e58d8ba80314121734764
- Accepted Profile version: 0.2.1
- Accepted Skills methodology version: 0.3.1
- Accepted VSM vector: S1=A · S2=— · S3=— · S3*=— · S4=— · S5=—
- System in focus: OpenCode native core Session/Revert/Snapshot mechanisms and concurrent coding sessions sharing a workspace; excludes out-of-tree plugin coordination and project governance
- Matching working fork: opensiro-contributions/opencode
- Fork owner control: ACTIVE/ALLOW per .opensiro/state.json
- Repository-wide source map: packages/core/src/session/revert.ts; packages/core/src/session/session.ts; specs/v2/session.md; original README, docs, tests, license, contributing and focused original Issues/PRs
- Evaluation object: Avoid one concurrent session's undo reverting another session's edits and prevent shared-store corruption
- Existing-work overlap: Open session undo conflict and shared SQLite filesystem failures are tracked in original Issues. Open PR #64359 handles parent/subagent rollback tracking, #63475 handles pruned snapshot safety; none is merged proof of completed conflict fix.
- Our on-top contribution: No added autonomous S2=C controller at this stage; prefer source-native rollback ownership, optimistic conflict checks/transaction boundaries and filesystem-safe storage investigation in tracked Issues/PRs.
- Incremental benefit: no distinct measured improvement over native repair and parent controls; no deployed C claimed
- Decision scope: one current-head C feasibility test, not repository-wide Index reclassification
- Priority rationale: Current S2 candidate overlaps source-native rollback and shared-store corrections; parent rights and other functions do not give automatic new C need
- Target transition: NO_QUALIFIED_C_TARGET
- P1 dependencies: Compare active #64359/#63475 actual patches and original #33940/#56282 reproduction; determine independent peer conflict ownership only after base bugs fixed
- P2 optional: NONE
- Proposed C construction: No added autonomous S2=C controller at this stage; prefer source-native rollback ownership, optimistic conflict checks/transaction boundaries and filesystem-safe storage investigation in tracked Issues/PRs.
- C sufficiency falsifier: After scoped native snapshot and rollback fixes, a reproducible peer coordination problem still needs a developer-composed autonomous negotiator choosing among conflicting session commitments and feeding a lawful new work plan back to both sessions
- Scenario basis: OBSERVED
- Proposal-stage decision: NO_GO
- Research disposition: NO_USEFUL_CHANGE
- Proposed validation: Two simultaneous sessions editing overlapping and nonoverlapping files; undo/revert preserving other session's data; concurrent SQLite WAL store under supported filesystem; native regression tests NOT_RUN
- Validation state: NOT_RUN
- Proposal falsifier: After scoped native snapshot and rollback fixes, a reproducible peer coordination problem still needs a developer-composed autonomous negotiator choosing among conflicting session commitments and feeding a lawful new work plan back to both sessions
- Result: NO_USEFUL_CHANGE
- External issue: DRAFT — NOT PUBLISHED
- Public fork Issue: DRAFT — NOT PUBLISHED
- Cost status: NOT_MEASURED
- S1 disposition: standard agent performs autonomous tool operations and responds to results
- S2 disposition: nested task delegation lacks independent peer interference regulator
- S3 disposition: parent-child control alone is not full-workspace S3
- S3* disposition: no protected independent corrective review evidenced
- S4 disposition: current coding exploration is not future environmental analysis
- S5 disposition: human/deployer governance and configured permissions retain ultimate policy right

## Identity and pins

[Accepted included Index assessment](https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/assessments/op/opencode.md) at frozen `c2e43bf4750841277b3e58d8ba80314121734764`, reviewed 2026-09-15 at [original review commit](https://github.com/anomalyco/opencode/commit/95daf90670b7c039c436c85537da5fbfe2205b41); historical blob `60cd4ec5d2dd5ba620c815e3579d198ab5274036`; Profile 0.2.1, Skills 0.3.1. Distinct [current original HEAD](https://github.com/anomalyco/opencode/commit/b4d81f04ad350b9a9de7ec97af3ce93ecb5c5e2c). Source-first decision precedes comparison to original fork case. No present Index regrade.

## Rights and authority

Fork parent and owner-controlled ACTIVE/ALLOW on `opensiro/meta` independently checked. Original repo public with read rights, licensed OSS; contributor policy checked. OpenCode requires prior feature design approval and linked Issues for many changes. Third-party messages/public fork Issues not authorized. Original product, deployment and Index unchanged.

## Existing work / overlap

Source [packages/core/src/session/revert.ts](https://github.com/anomalyco/opencode/blob/b4d81f04ad350b9a9de7ec97af3ce93ecb5c5e2c/packages/core/src/session/revert.ts); [packages/core/src/session/session.ts](https://github.com/anomalyco/opencode/blob/b4d81f04ad350b9a9de7ec97af3ce93ecb5c5e2c/packages/core/src/session/session.ts); [specs/v2/session.md](https://github.com/anomalyco/opencode/blob/b4d81f04ad350b9a9de7ec97af3ce93ecb5c5e2c/specs/v2/session.md). Original Issues/PRs: [issues / 33940](https://github.com/anomalyco/opencode/issues/33940); [issues / 56282](https://github.com/anomalyco/opencode/issues/56282); [pull / 64359](https://github.com/anomalyco/opencode/pull/64359); [pull / 63475](https://github.com/anomalyco/opencode/pull/63475). Open session undo conflict and shared SQLite filesystem failures are tracked in original Issues. Open PR #64359 handles parent/subagent rollback tracking, #63475 handles pruned snapshot safety; none is merged proof of completed conflict fix.. OPEN_PR is not SHIPPED, and search absence cannot certify global absence.

## Function ownership

- **S1** historical **A**: standard agent performs autonomous tool operations and responds to results. No new credited ownership or compulsory A-to-C conversion.
- **S2** historical **—**: nested task delegation lacks independent peer interference regulator. No new credited ownership or compulsory A-to-C conversion.
- **S3** historical **—**: parent-child control alone is not full-workspace S3. No new credited ownership or compulsory A-to-C conversion.
- **S3*** historical **—**: no protected independent corrective review evidenced. No new credited ownership or compulsory A-to-C conversion.
- **S4** historical **—**: current coding exploration is not future environmental analysis. No new credited ownership or compulsory A-to-C conversion.
- **S5** historical **—**: human/deployer governance and configured permissions retain ultimate policy right. No new credited ownership or compulsory A-to-C conversion.

## Parallel contribution-on-top review

| Candidate function/outcome | Track A: original and competing work | Track B: smallest on-top complete C or NONE | What would disprove this decision? |
| --- | --- | --- | --- |
| Avoid one concurrent session's undo reverting another session's edits and prevent shared-store corruption | Open session undo conflict and shared SQLite filesystem failures are tracked in original Issues. Open PR #64359 handles parent/subagent rollback tracking, #63475 handles pruned snapshot safety; none is merged proof of completed conflict fix. | No added autonomous S2=C controller at this stage; prefer source-native rollback ownership, optimistic conflict checks/transaction boundaries and filesystem-safe storage investigation in tracked Issues/PRs. | After scoped native snapshot and rollback fixes, a reproducible peer coordination problem still needs a developer-composed autonomous negotiator choosing among conflicting session commitments and feeding a lawful new work plan back to both sessions |
| Source-native later-operation feedback | First-party sessions, host policy and existing task controls | No independent new actor or gate; preserve parent authority and implement base defects via native issues | Evidence of a missing authorized independent decision that changes subsequent operations |

## Capability priority

P0: **NO_QUALIFIED_C_TARGET**. P1: Compare active #64359/#63475 actual patches and original #33940/#56282 reproduction; determine independent peer conflict ownership only after base bugs fixed. P2: NONE. **NO_GO / NO_USEFUL_CHANGE**; no mandatory C target just because S2/S3*/S4/S5 is absent.

## Implementation options

No added autonomous S2=C controller at this stage; prefer source-native rollback ownership, optimistic conflict checks/transaction boundaries and filesystem-safe storage investigation in tracked Issues/PRs.. A complete novel constructor would have to identify separate owner and decision, first-party interface, enforcement and feedback with a parent-bounded correction; After scoped native snapshot and rollback fixes, a reproducible peer coordination problem still needs a developer-composed autonomous negotiator choosing among conflicting session commitments and feeding a lawful new work plan back to both sessions. Source-native alternative is more limited and sufficient for the present evidence.

## Specification and domain alternatives

Prior OpenCode case NO_GO on native-first S2; current source tree moves task behavior to core and open rollback PRs continue to cover the bounded need. No independent novel C requirement emerges.. Intent behind any absent functions UNKNOWN, not a default intentional absence. No Profile or Skills specification patch proposed.

## Cost experiment

Two simultaneous sessions editing overlapping and nonoverlapping files; undo/revert preserving other session's data; concurrent SQLite WAL store under supported filesystem; native regression tests NOT_RUN. Matched implementation/integration/test hours, false decisions, token/latency and cost unmeasured; NOT_RUN / NOT_MEASURED.

## Delivery and publication

Canonical [Human](issue.md) and [AI](constructor-sufficiency.md) agree: **NO_GO / NO_USEFUL_CHANGE**. Only internal .opensiro receipt modified, original-facing Issue/PR/comment and public fork Issue NOT PUBLISHED, source code untouched and historical Index assessment unchanged.
