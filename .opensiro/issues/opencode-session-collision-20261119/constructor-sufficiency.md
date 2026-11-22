# OpenCode — source-native S2 constructor and falsification contract

**AI/developer level: plan only.** **DRAFT — NOT PUBLISHED** Canonical status and complete six-function matrix are in [roadmap.md](roadmap.md), with the sole historical/current table in [issue.md](issue.md). This file does not create additional grades.

**Target transition:** S2=— -> S2=C
**Proposal-stage decision:** GO
**Research disposition:** NEEDS_EVIDENCE



## 1. Function-specific construction boundary and methodology checks

**Source and mode boundary:** OpenCode first-party v2 Core Session, FileAccess/FileMutation/FileWrite and CodeMode; old proposal source pinned in [roadmap.md](roadmap.md), refreshed relevant Core source at https://github.com/anomalyco/opencode/commit/ee5fe34e136488a1839ac73bcca8321c51a31b75 2026-11-22. Other processes, arbitrary plugins, CI and GitHub maintainers excluded.

**Six-function dependencies (S1/S2/S3/S3*/S4/S5):** S1 Sessions own actual tools, S2 is proposed peer coordination; S3 commitments, S3* complementary audit, S4 future adaptation and S5 ultimate user/maintainer policy are neither claimed nor constructed.

**Function witness:** A developer-composed S2 owner chooses admissible edit intent, original Core enforces at lawful commit, affected Session observes feedback for a subsequent decision.

**Counterfactual owner test:** With actor absent, per-file locks and permission remain, but no independent peer admit/defer/handoff decision belongs to a developer-composed S2 controller.

**Possible methodological negative control:** Native mutex/worktree or external plugin can satisfy narrower integrity needs. This is not a required product S2 implementation or an Index regrade.

**Contributor / maintainer priorities:** OpenCode CONTRIBUTING calls for design review before Core features; this particular proposal has no verified maintainer endorsement. Priority NOT_STATED.


Original default dev [1607d4e624bfb2e25cf2fe6a5c44be443faa9153](https://github.com/anomalyco/opencode/commit/1607d4e624bfb2e25cf2fe6a5c44be443faa9153); accepted included historical [Index@1c2352b72bcb70cead9ffed869c0c31b0496b2ba](https://github.com/opensiro/vsm-harness-index/blob/1c2352b72bcb70cead9ffed869c0c31b0496b2ba/assessments/op/opencode.md) gives S1=A and S2/S3/S3*/S4/S5=— at 2026-09-15, reviewed source 95daf90670b7c039c436c85537da5fbfe2205b41. P0 is **S2**, not generic scheduling or S3 project-wide resource optimization.

In-scope S1 units: two independent first-party running OpenCode Sessions with different SessionSchema IDs, both allowed by the operator to use one FileAccess Environment and target path. Disturbance: overlapping legitimate write intents requiring cross-Session order/coordination; native locks serialize mutations but do not own discretionary peer selection. The proposed **decisive owner** is a developer-composed, autonomously choosing opt-in coordinator; FileWrite/FileMutation enforce only the choice within existing permissions. No model/actor installed means no autonomous S2 choice. No rights over arbitrary shell or third-party writes are assumed.



## 2. Source-pinned baseline and parallel native Track A / on-top Track B

**Original native workflow:** Two running Sessions send authorized Core edit/patch/write/CodeMode file operations through FileAccess/permission/FileMutation; the result returns to their own execution.

**Closest existing solution:** Core keyed locks, user approval, separate worktrees, manual sequencing; previously open #65169/#65201 concern moving permission outside critical sections.

**Relevant original Issues/PRs:** #64869 OPEN created 2026-11-19, #65169/#65201 OPEN; #40255 CLOSED created 2026-08-03 and linked #15739; #52297 OPEN created 2026-09-30, linked to current open #60074 and a third-party MCP alternative. Confirmed ages and discussions on 2026-11-22.

**On-top distinctness:** Current mutex locking is deterministic and scoped, whereas the S2 candidate needs a separately chosen lawful peer decision with first-party commit effect and returned feedback.

**Source ambiguity / rights blockers:** No end-to-end implemented S2 constructor or native tests. A distinct product need and project design fit remain unproven. Current source checking does not amend historical Index grades.


| Decision or effect | Existing original first-party path | Minimum proposed source-native delta | Negative / stop |
| --- | --- | --- | --- |
| Identify independent S1s | [FileAccess.Invocation](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/file-access.ts) carries context.sessionID; FileAccess.key includes environment.id and canonical resolved path | Collect two live same-key intent claims and revision in optional host/Location S2 service; do not infer cross-machine global locks | Same textual path in different Environment is not same resource |
| Preserve original permission | [FileWrite.target/authorize](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/file-write.ts) and [Permission](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/permission.ts) already enforce allowed operations | Autonomous S2 actor only chooses among already permitted scoped admit/defer/handoff alternatives; user denial remains denial | Owner absent/revoked or user declines prevents effect |
| Decide between Sessions | [SessionRunCoordinator](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/session/run-coordinator.ts) owns per-ID run/wake, [FileMutation](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/file-mutation.ts) process-local transactionLocks serialize same file | Expose opt-in first-party coordination hook consuming competing Session claims and granted alternatives, generating a versioned bounded decision. Invoke outside critical section, after ordinary approval | Static first-come lock or model suggestion without binding effect is NOT S2=C |
| Enforce protected file write | [edit](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/tool/plugin/edit.ts) and [patch](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/tool/plugin/patch.ts) wrap operations in withLock; [write](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/tool/plugin/write.ts) uses FileWrite; [CodeMode Bun](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/codemode/bun.ts) writes via FileMutation | At guarded mutation commit, verify current FileAccess.key, owner permit, file revision/fence and selected allow/defer/handoff; refused/deferred action makes no mutation | Stale authorization, cancellation, bypassing CodeMode or multi-path patch silently applying is a falsifier |
| Return into future work | [SessionSynthetic](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/session/synthetic.ts) admits durable synthetic messages; [SessionInbox](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/session/inbox.ts) orders them and [SessionExecution.wake](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/session/execution.ts) resumes processing | Emit durable applied/deferred/conflict/release receipt to affected session; wake only when allowed and valid, so the autonomous S2 owner can use observed effect for next peer choice | No actual later S1 feedback or only dashboard telemetry fails C |

The current Edit implementation takes a path transaction lock across FileWrite.authorize. Original OPEN [#65169](https://github.com/anomalyco/opencode/pull/65169) and [#65201](https://github.com/anomalyco/opencode/pull/65201) seek to remove permission prompts from held locks; these are **unmerged**, not shipped. A proposed S2 model decision must **never be awaited inside withLock**. Guard must recheck any revision after approval and before commit, not lock all peer work during an LLM decision. This is a specific architectural constraint of OpenCode, not a generic port pattern.

The shared-temp collision [#40255](https://github.com/anomalyco/opencode/issues/40255) (CLOSED), native per-session queue suggestion [#6470](https://github.com/anomalyco/opencode/issues/6470) (CLOSED) and edit hang [#64869](https://github.com/anomalyco/opencode/issues/64869) (OPEN) are incident/interest context, **not** proof that an S2 policy actor is needed. [#60998](https://github.com/anomalyco/opencode/pull/60998) (OPEN, current head 016f9fac26b3d0c0a53b734d47391ac4da3e9c84) fixes inbox lock identity, not decisions across competing coding tasks. [#64359](https://github.com/anomalyco/opencode/pull/64359) (OPEN, head e5ebc83a7d2078d6884af339b053768af3dd612b) addresses subagent rollback provenance; not peer coordination.



## 3. Minimal complete S2 first-party C construction

**Required property:** First-party, optional constructor for a lawful autonomous S2 owner with nontrivial peer choices and returned operational feedback, not merely a callback/queue.

**Architectural C-sufficiency argument:** Reuse FileAccess Invocation.sessionID and key, FileWrite authorization, FileMutation lock, and Session inbox/execution. Add bounded decision, revision/permit check, and receipt; enforce outside human/model waits within locks.

**Explicit non-goals:** No new S3/S4/S5 controller, no blanket authority over shell or external writes, no guaranteed cross-process protection, no unverified snapshot support.

**Implementation dependency graph:** Inspect current Core paths and rights -> install optional peer decision service -> check permit at supported mutation commit -> deliver Session receipt -> real native comparative tests.


A future implementation could place one optional S2 interface alongside current Core Session/Location services, not create a separate global manager. The interface receives a bounded immutable request carrying Session ID, FileAccess.key, operation kind (edit/patch/write/CodeMode) and expected revision. It can consult already admitted live claims of a second independent Session for that key, then make an autonomous **admit, defer or handoff** decision bounded by operator-configured permission, scoped location and deadlines. The first-party Core edit path enforces its response at file commit using existing FileMutation transaction identity and a new revision/fence check. An emitted SessionSynthetic receipt is later observed by the waiting Session; newly observed success/failure can inform the next decision. File owner controls remain with the original runtime/app, not an OpenSiro service.

The smallest concrete edited surfaces **if approved later** are an opt-in registration in Core service composition, FileWrite/FileAccess session-aware preflight and guarded commit, common use by edit/patch/write/CodeMode mutation leaves, plus an inbox/Session execution feedback adapter. For multi-file patch, acquisition and stale validation must be atomic as needed, or return no mutation. Revert/Snapshot.restore must either use the same guard or be explicitly disabled/unsupported in the claimed coordinated mode; do not label unsafe undo protected. Arbitrary plugin/shell writes, external editors and multiple independent server processes are unsupported absent a separate native bridge. This is one bounded hypothesis, not six new function controllers. Changing Core's Service APIs, CodeMode and Snapshot integration requires normal project design review.

**Counterfactual:** remove the configured S2 actor while keeping RunCoordinator, FileMutation mutex and permission; deterministic edit serialization still works, but there is no independently composed owner to select peer **handoff versus defer** based on live conflicting intentions and return corrective feedback. If a current first-party API already lets a developer install such a decisive closed owner, the proposed bridge is redundant and GO must be revisited.



## 4. Priorities, optional alternative and stopping rules

**P0 and P1:** P0 source-native S2 composition, real effect and feedback. P1 permission and revision/commit safety, supported paths and negative tests; canonical values remain in [roadmap.md](roadmap.md).

**P2:** NONE.

**Alternative path:** Native mutex/worktree/manual user ordering or a compatible external plugin when full runtime peer choice is not justified.

**Stop:** Equivalent first-party C, lack of lawful choice/effect/feedback, current source incompatibility or explicit original maintainer prohibition; no coercion of product adoption.

## 5. Future source-native acceptance — derive tests, do not copy a matrix

**Native test commands and entry points:** Source-pinned Bun tests for Core file mutation/tool/session paths as in package.json; new proposal tests NOT_RUN.

**Positive functional closure:** Native two-Session test shows actor admit A/defer B and subsequent handoff after received commit feedback.

**Independent alternative (where applicable):** Matched initial conditions with B admitted before A must yield a distinguishable lawful later state.

**Negative authority and compatibility (where applicable):** No actor, revoked permission, stale revision, interrupted session, unguarded tool or undo path must preserve native safety; no-actor baseline remains unchanged.

**Matched native alternative:** Per-path mutex, distinct worktree, and operator scheduling under identical local task. Outcome and cost NOT_MEASURED.


**Real runner:** [packages/core/package.json](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/package.json) defines bun run test and bun typecheck. **Execution: NOT_RUN.** Prepare disposable Environment and two genuine Core Sessions under same app, with the same source commit and input workload for baseline and experiment.

1. **Positive bounded choice:** A and B both intend to change a same-key file; composed owner chooses admit(A), defer(B) under explicit rights. Verify A commits with a revision receipt; subsequent feedback releases B and the owner chooses handoff so B runs after a fresh revision check. Both Sessions see the correct tool result/message.
2. **Alternative autonomous choice:** with matched initial facts, configured owner chooses defer(A)/admit(B), producing a different legitimate later file and session state. This discriminates S2 decision ownership from a hardcoded lock.
3. **Negative authority/revision:** denied permission, absent actor, stale fence, interrupted A, no longer-live B or a changed file must not lead to unauthorized write; missing actor stays on native baseline without invented peer governance.
4. **Tool coverage:** repeat for edit/patch/write and supported CodeMode Bun routes; never claim protected undo unless Snapshot.restore is guarded; mixed and uninstrumented shell/plugin operations are documented as unsupported, not silently protected.
5. **Matched baseline:** compare normal native process locks, explicit separate worktrees and revision-guard alternatives, measuring end-to-end task result/correctness if available, plus eventual developer effort. No claimed ROI until observed.

**Stop/qualify:** If actor's decisions cannot be legally enforced in Core with actual later return, this is an incomplete chain and would lose GO; if native first-party equivalents already close S2 with independently selectable choices, no additional constructor; if no authority or supported boundary exists, BLOCKED on that exact source fact, not on unmeasured product value. Original maintainer, not OpenSiro, decides eventual adoption.



## 6. Proposal verdict, falsification, evidence ownership and handoff

**Primary falsifier:** Equivalent owner already first-party or chosen peer decision cannot be legally enforced with return to later work.

**Validation state:** NOT_RUN native implementation tests; validator PASS is formatting-only.

**Ownership of truth:** Profile semantics, Skills assessment, Index historical grades, original maintainer implementation decisions, and the case-local [roadmap.md](roadmap.md) receipt remain separate.

**Cost status:** NOT_MEASURED.

**Next permitted action:** Finish source/Issue dedupe and exact human approval of any public Issue action. No external posting by default.

**Human backlink:** [issue.md](issue.md).

**case receipt:** [roadmap.md](roadmap.md).

**AI disclosure:** Prepared with AI assistance, not validated by independent native test evidence.


Historical fork case was NO_GO because no *incremental product value* beyond deterministic file/snapshot/SQLite repair had been demonstrated. Published v0.18.0 neutrality separates product desirability from architecturally complete C construction. v0.18.1 further recommends actual FileAccess/FileMutation/SessionInbox details rather than a generic peer supervisor. The independent source-first checkpoint preceding old-case review is [#58 comment 7043555021](https://github.com/opensiro/upstream/issues/58#issuecomment-7043555021); this is **not** a claim of strict clean-room fresh context. Proposal GO + NEEDS_EVIDENCE remains a hypothesis; **native tests NOT_RUN, benefit NOT_MEASURED, product code NOT_WRITTEN, third-party and fork Issue NOT_PUBLISHED**.
