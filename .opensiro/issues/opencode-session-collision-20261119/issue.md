# OpenCode — optional native S2 coordination for concurrent file edits (Wave 4)

**PLAN_ONLY · proposal-stage GO · research NEEDS_EVIDENCE · DRAFT — NOT PUBLISHED**

**One-sentence proposal:** Offer one opt-in first-party Core construction seam for a developer-composed autonomous coordinator to make and enforce different permitted edit decisions when two live OpenCode Sessions target the same FileAccess resource, with feedback delivered to later work.

**Canonical receipt:** [roadmap.md](roadmap.md). **Implementation/validation companion:** [constructor-sufficiency.md](constructor-sufficiency.md).
**Working fork:** opensiro-contributions/opencode, stable case .opensiro/issues/opencode-session-collision-20261119 on opensiro/meta.

**Target transition:** S2=— -> S2=C
**Proposal-stage decision:** GO
**Research disposition:** NEEDS_EVIDENCE

## Historical general VSM assessment and source-first screen

Accepted Index: [included assessment](https://github.com/opensiro/vsm-harness-index/blob/1c2352b72bcb70cead9ffed869c0c31b0496b2ba/assessments/op/opencode.md), blob 60cd4ec5d2dd5ba620c815e3579d198ab5274036, review source 95daf90670b7c039c436c85537da5fbfe2205b41 (2026-09-15), Profile 0.2.1 / methodology 0.3.1. **Accepted historical** states describe ownership at the old revision, not grades for [current dev@1607d4e624bfb2e25cf2fe6a5c44be443faa9153](https://github.com/anomalyco/opencode/commit/1607d4e624bfb2e25cf2fe6a5c44be443faa9153). System in focus is the OpenCode v2 first-party agent/session runtime, including supported Core tools, optional CodeMode, per-session execution and file operations; external shell writers, arbitrary plugins, other server processes and OpenCode maintainers are outside this S2 candidate.

| Function / ordinary role | Historical Index | Current first-party ownership at the scoped boundary | Candidate / priority |
| --- | --- | --- | --- |
| **S1 · Operations** | A | [Agent](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/agent.ts) and Session execute coding/tool tasks with returned observations | Existing, no new C |
| **S2 · Coordination** | — | [RunCoordinator](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/session/run-coordinator.ts) serializes each Session; [FileMutation](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/file-mutation.ts) serializes cooperating file writes, but not independent inter-Session autonomous choices | **P0** S2 constructor hypothesis |
| **S3 · Current management** | — | Per-Session execution and job views are not a demonstrable whole-project commitment owner | DEFER, not a proven deficit |
| **S3* · Independent audit** | — | Logs, tests and snapshots are observers, not a separately owned corrective audit actor | NO_TARGET here |
| **S4 · Future adaptation** | — | Current config/model behavior does not establish prospective external-change adaptation | NO_TARGET here; intent UNKNOWN |
| **S5 · Identity/policy** | — | Application/user permits operations; maintainer governs product adoption | Parent-reserved, no local S5 |

States A (agent-owned), C (developer-composable autonomous owner) and — (no proven path in the historical assessment) are ownership categories, not quality or maturity scores. No mandatory six-feature requirement follows.

## The specific proposed capability

Two independently executing Sessions may edit the same local target. OpenCode already has process-local file locks and ordinary permission; those serialize or authorize narrow operations without selecting **which legitimate peer task should proceed next and why**. Under the hypothesis, the app developer installs a separately operating S2 coordinator that sees both live edit intents and file revisions; it may choose **admit / defer / handoff**, enforce that choice through the first-party file mutation boundary and send the result to the affected Session.

Native minimal connection: [FileAccess.Invocation.sessionID and FileAccess.key](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/file-access.ts) identify the Sessions and canonical file; [FileWrite](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/file-write.ts) retains user approval; [FileMutation.withLock](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/file-mutation.ts) supplies the guarded commit boundary; [SessionInbox](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/session/inbox.ts) and [SessionExecution](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/session/execution.ts) return durable feedback/wake. The proposed **missing** piece is an opt-in, legitimate autonomous peer decision + lease/fence and feedback bridge in these specific code paths. It must never hold a file lock during a model or user decision.

**Native alternative:** separate worktrees, existing edit/patch per-path locking, stale version rejection and operator resolution. If all the operator wants is no lost file contents, these may be simpler; no requirement that maintainers ship a new actor.

**Track A overlap:** [#64869](https://github.com/anomalyco/opencode/issues/64869) OPEN edit lock deadlock; [#65169](https://github.com/anomalyco/opencode/pull/65169) and [#65201](https://github.com/anomalyco/opencode/pull/65201) OPEN unmerged permission/lock patches; [#60998](https://github.com/anomalyco/opencode/pull/60998) OPEN database inbox lock scope; [#64359](https://github.com/anomalyco/opencode/pull/64359) OPEN subagent revert provenance. None currently establishes an autonomous S2 peer decision owner. Reports [#40255](https://github.com/anomalyco/opencode/issues/40255) and [#33940](https://github.com/anomalyco/opencode/issues/33940) are historical CLOSED, not proof of a current bug or a product need.

**P0:** optional Core S2 construction for in-scope edits. **P1:** permission/decision/commit-revision/feedback wiring covering declared Core mutation paths and safety around undo; verify original code and tests. **P2:** NONE. Host authority remains intact; external shell and NFS operations are not guaranteed.

## Planned acceptance and falsifier

Under a disposable two-Session same-resource test, a developer-composed actor must select **defer** for one Session, then legally **handoff** after feedback; a different lawful decision must produce a different subsequent tool/session outcome. A missing owner preserves existing native behavior. A revoked/stale decision must never apply a write; cancelled session and skipped tool/undo paths must fail safely. Compare the same scenario with native mutex/worktree control. If the actor cannot enforce/return alternative choices, the proposed C is **incomplete**. Passing native tests and measured advantages are **not claimed**.

**Status:** GO / NEEDS_EVIDENCE is architectural proposal-stage only; **native tests NOT_RUN**, benefit/cost **NOT_MEASURED**, no code implementation, no original maintainer acceptance, and no Index regrade. Older same-case NO_GO remains available in Git history because it concerned unproven additional product value; acceptance of a design and a product decision are separate.

## Publication and owner handoff

**Public fork Issue title (draft only):** OpenCode — optional first-party S2 peer coordination for concurrent Core edits.

**Public fork Issue body (draft only):** This document is the proposed Issue body: historical Index context, native source links, the single bounded S2 target, alternative native approaches, owner rights, falsifiable acceptance and limitations above. **DRAFT — NOT PUBLISHED**; a public fork Issue and any external original Issue/PR/comment need separate exact current-conversation consent. OpenCode [CONTRIBUTING](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/CONTRIBUTING.md) also requires feature-request design approval before implementation PR. There is no automatic proposal to external maintainers.
