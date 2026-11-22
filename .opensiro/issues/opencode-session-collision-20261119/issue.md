# OpenCode — optional native S2 coordination for concurrent file edits (Wave 4)

**PLAN_ONLY · proposal-stage GO · research NEEDS_EVIDENCE · DRAFT — NOT PUBLISHED**

**One-sentence proposal:** Offer one opt-in first-party Core construction seam for a developer-composed autonomous coordinator to make and enforce different permitted edit decisions when two live OpenCode Sessions target the same FileAccess resource, with feedback delivered to later work.

**Canonical decision receipt:** [roadmap.md](roadmap.md). **Technical companion:** [constructor-sufficiency.md](constructor-sufficiency.md).
**Working fork:** opensiro-contributions/opencode at opensiro/meta.
**Case:** .opensiro/issues/opencode-session-collision-20261119/

**Target transition:** S2=— -> S2=C
**Proposal-stage decision:** GO
**Research disposition:** NEEDS_EVIDENCE



## 1. Why Opensiro and central accepted VSM assessment

**Why Opensiro:** Test whether a source-native S2 peer coordinator can be made developer-composable; not a requirement that maintainers adopt VSM, and no measured cost savings.

**ACCEPTED HISTORICAL INDEX:** S1=A · S2=— · S3=— · S3*=— · S4=— · S5=—. Historical ownership categories, not quality ranks.

**Repository-wide audit:** Existing case surveyed OpenCode v2 Core Session/agent, file, CodeMode, documentation, tests, and current Issue/PR alternatives at recorded original SHA. Fresh relevant first-party Core source read on 2026-11-22 at https://github.com/anomalyco/opencode/commit/ee5fe34e136488a1839ac73bcca8321c51a31b75 is a source relevance check, not a new Index assessment.

**Priority rationale:** S2 is the case-local hypothesis: process-local locking is not a discretionary autonomous choice between competing lawful Sessions. Other functions have no supported higher priority in this case.

**Deliberate exclusions / methodology challenge:** External shell/plugin writers, network filesystem sharing and maintainers are outside this supported S2 runtime boundary. No intentional S3/S3*/S4/S5 omission is inferred. Methodology concerns belong to Skills and Index.


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



## 2. Selected construction hypothesis and operator outcome

**Function-specific disturbance:** HYPOTHETICAL need for an autonomous peer choice when two Sessions intend to edit one FileAccess target; actual file collision incidents exist but do not establish demand for this feature.

**Proposed C capability (P0):** Optional scoped S2 owner with lawful admit/defer/handoff choices, effective revision-guarded Core commit, and actual returned feedback for later Session work.

**Best native operator alternative:** Use current per-file locking, operator scheduling, separate Git worktrees, stale-edit rejection, or existing plugin-based coordination.

**Expected user benefit:** HYPOTHETICAL bounded peer-decision composability; actual demand, task-quality gains and total cost NOT_MEASURED.

**Architectural sufficiency argument:** Reuse first-party FileAccess identity, FileWrite permission, FileMutation protected edits, SessionInbox and SessionExecution. Add opt-in decision, fence and receipt; never hold a file lock during human/model choice.


Two independently executing Sessions may edit the same local target. OpenCode already has process-local file locks and ordinary permission; those serialize or authorize narrow operations without selecting **which legitimate peer task should proceed next and why**. Under the hypothesis, the app developer installs a separately operating S2 coordinator that sees both live edit intents and file revisions; it may choose **admit / defer / handoff**, enforce that choice through the first-party file mutation boundary and send the result to the affected Session.

Native minimal connection: [FileAccess.Invocation.sessionID and FileAccess.key](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/file-access.ts) identify the Sessions and canonical file; [FileWrite](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/file-write.ts) retains user approval; [FileMutation.withLock](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/file-mutation.ts) supplies the guarded commit boundary; [SessionInbox](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/session/inbox.ts) and [SessionExecution](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/session/execution.ts) return durable feedback/wake. The proposed **missing** piece is an opt-in, legitimate autonomous peer decision + lease/fence and feedback bridge in these specific code paths. It must never hold a file lock during a model or user decision.

**Native alternative:** separate worktrees, existing edit/patch per-path locking, stale version rejection and operator resolution. If all the operator wants is no lost file contents, these may be simpler; no requirement that maintainers ship a new actor.

**Track A overlap:** [#64869](https://github.com/anomalyco/opencode/issues/64869) OPEN edit lock deadlock; [#65169](https://github.com/anomalyco/opencode/pull/65169) and [#65201](https://github.com/anomalyco/opencode/pull/65201) OPEN unmerged permission/lock patches; [#60998](https://github.com/anomalyco/opencode/pull/60998) OPEN database inbox lock scope; [#64359](https://github.com/anomalyco/opencode/pull/64359) OPEN subagent revert provenance. None currently establishes an autonomous S2 peer decision owner. Reports [#40255](https://github.com/anomalyco/opencode/issues/40255) and [#33940](https://github.com/anomalyco/opencode/issues/33940) are historical CLOSED, not proof of a current bug or a product need.

**P0:** optional Core S2 construction for in-scope edits. **P1:** permission/decision/commit-revision/feedback wiring covering declared Core mutation paths and safety around undo; verify original code and tests. **P2:** NONE. Host authority remains intact; external shell and NFS operations are not guaranteed.



## 3. Existing native work versus missing construction

**Track A — native coverage:** Original file mutex and Session run loop, open permission-lock fixes #65169 and #65201, open inter-session messaging proposal #52297 / PR #60074, and plugin alternatives. Source coverage is limited to the declared runtime, not a complete maintainer decision.

**Track B — independent on-top C construction:** Optional peer actor, admission permit at supported Core commit, replay-safe revision fence and return via session feedback. These are unimplemented constructor steps, not native test results.

**Distinctness and falsifier:** A static mutex does not choose peer priorities. An existing decisive and feedback-closed S2 native API would make this redundant; an actor unable to enforce authorized effects would make the proposed C path incomplete.

**Age-triggered recheck (2026-11-22):** #40255 created 2026-08-03 (111 days; CLOSED, linked #15739); #52297 created 2026-09-30 (53 days; OPEN, comments mention PR #60074 and third-party Concord MCP); #64869 created 2026-11-19 (3 days; OPEN, two competing open fixes). Re-read body and available discussion, current states, related PRs, and Core source at https://github.com/anomalyco/opencode/commit/ee5fe34e136488a1839ac73bcca8321c51a31b75. Date is a recheck trigger, not evidence of remaining need.

## 4. Priorities and minimum sufficient result

- **P0:** Optional Core S2 peer decision owner + lawful commit effect + returned Session feedback.

- **P1:** User permission, revision fencing, supported edit/patch/write/CodeMode coverage, cancellation/rollback scope and real native tests.

- **P2:** NONE.

**Proposed C-sufficiency verdict:** PROPOSED_C_SUFFICIENT as an unimplemented design proposal (GO / NEEDS_EVIDENCE), not a new Index grade.

## 5. Proposed acceptance and stop gates

**Future positive test:** Two real Sessions share a target; actor chooses admit A/defer B, A commits and returns evidence, actor handoffs to B and B changes later work under a checked permit.

**Future negative test:** No owner, revoked right, stale revision, denied user permission, cancelled Session and unsupported writer must not silently commit a protected action. Without an opt-in actor, old native behavior remains.

**Proposed falsifier:** Equivalent first-party actor already shipped, or the prospective source-native path cannot enforce and return lawful peer decisions.

**Validation state:** NOT_RUN for native functional tests; template validation is structural only.


Under a disposable two-Session same-resource test, a developer-composed actor must select **defer** for one Session, then legally **handoff** after feedback; a different lawful decision must produce a different subsequent tool/session outcome. A missing owner preserves existing native behavior. A revoked/stale decision must never apply a write; cancelled session and skipped tool/undo paths must fail safely. Compare the same scenario with native mutex/worktree control. If the actor cannot enforce/return alternative choices, the proposed C is **incomplete**. Passing native tests and measured advantages are **not claimed**.

**Status:** GO / NEEDS_EVIDENCE is architectural proposal-stage only; **native tests NOT_RUN**, benefit/cost **NOT_MEASURED**, no code implementation, no original maintainer acceptance, and no Index regrade. Older same-case NO_GO remains available in Git history because it concerned unproven additional product value; acceptance of a design and a product decision are separate.



## 6. Independent paths

**Original-native contribution:** Prefer current project issues and fixes first; possible original feature design needs maintainer review and separate publication approval.

**Profile / Skills:** Route concrete assessment-method corrections separately; do not regrade the current historical Index vector here.

**Domain fork:** Permissioned experimental plugin/worktree/fork is a valid comparator; do not imply OpenCode Core adoption.

## 7. Cost hypothesis

**Cost status: NOT_MEASURED.** Compare same native task with locks/worktrees/plugin versus a prospective S2 composer, including implementation, integration, review, test and maintenance costs.

## 8. Decision / handoff

**Proposal-stage decision:** GO (architecturally coherent proposed constructor only).

**Research disposition:** NEEDS_EVIDENCE (native tests, user need, value and adoption unproven).

**Decision reason / next permitted step:** Refresh original default HEAD and old Issue/PR states; require the exact destination/body and owner approval before any public fork or third-party interaction. Do not create a duplicate.

**Agent/developer handoff:** [constructor-sufficiency.md](constructor-sufficiency.md) and canonical [roadmap.md](roadmap.md).

**Rights and publication:** ACTIVE/ALLOW permits OpenSiro case maintenance, not external Issue/PR publication. Original Core feature design needs maintainer review. DRAFT — NOT PUBLISHED.

**AI disclosure:** AI-assisted roadmap with no independently run native tests, product adoption evidence, independent human endorsement or changed Index grade.


**Public fork Issue title (draft only):** OpenCode — optional first-party S2 peer coordination for concurrent Core edits.

**Public fork Issue body (draft only):** This document is the proposed Issue body: historical Index context, native source links, the single bounded S2 target, alternative native approaches, owner rights, falsifiable acceptance and limitations above. **DRAFT — NOT PUBLISHED**; a public fork Issue and any external original Issue/PR/comment need separate exact current-conversation consent. OpenCode [CONTRIBUTING](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/CONTRIBUTING.md) also requires feature-request design approval before implementation PR. There is no automatic proposal to external maintainers.
