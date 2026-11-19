# OpenCode — Upstream #58 repeated NO_GO roadmap re-evaluation (2026-11-20)

- Receipt contract: proposal-gate
- Original repository: anomalyco/opencode
- Original HEAD: 11883188a61b12a30bc4fb263cd217343981ca37
- Observed at: 2026-11-20
- Accepted Index assessment: https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/assessments/op/opencode.md
- Accepted assessment blob SHA: 60cd4ec5d2dd5ba620c815e3579d198ab5274036
- Accepted review ref: 95daf90670b7c039c436c85537da5fbfe2205b41
- Accepted reviewed at: 2026-09-15
- Accepted Index commit: c2e43bf4750841277b3e58d8ba80314121734764
- Accepted catalog blob SHA: 8609180ea6b25cc0d3e51e3c8111f2a4ae4f73f7
- Accepted Profile version: 0.2.1
- Accepted Methodology version: 0.3.1
- Accepted VSM vector: S1=A · S2=— · S3=— · S3*=— · S4=— · S5=—
- System in focus: First-party OpenCode v2 dev runtime session executor, child/subagent and plugin route, SessionRevert, Snapshot, SQL store, same worktree concurrency and supported host process modes; plugins authored by third parties, git itself, network filesystem semantics, and maintainer governance outside boundary
- Repository-wide source map: README.md, CONTRIBUTING.md, AGENTS.md, SECURITY.md, packages/core/src/session/session.ts, run-coordinator.ts, revert.ts, packages/core/src/snapshot.ts, database/database.ts, packages/core/src/agent.ts, packages/plugin, packages/server, original issue #33940/#56282/#20849 and original PR #64359/#63475/#54396 plus exact bodies/diffs/status
- Evaluation object: Correct cross-session /undo interference and storage collision under concurrent coding; test if a distinct composable first-party S2 coordinator offers value beyond native snapshot, operation guards, worktree and SQLite fixes
- Existing-work overlap: Shipped SessionRunCoordinator serializes per session key only, while separate sessions may still share a worktree; revert plan selects files from session messages but snapshot restoration is file-scoped rather than writer/commitment ownership; original #64359 OPEN proposes parent/nested-subagent rollback inclusion, original #63475 OPEN targets legacy packages/opencode missing-tree handling (not current dev shipped), original #54396 CLOSED_UNMERGED SQLite retry; native issue #56282 OPEN identifies network-FS WAL and service registration failures
- Our on-top contribution: No justified extra S2=C actor now; first implement native optimistic compare-and-swap on shared file changes, explicit per-session/worktree isolation or inter-session safe rollback scopes, and DB local storage / single-writer filesystem compatibility. Plugin-based scheduling exists as a native alternative, not proof a new C is required
- Incremental benefit: A separate autonomous peer negotiator has not shown a lawful distinct decision and later operations outcome that safer native file ownership/storage alone cannot provide; cost and benefit NOT_MEASURED
- Decision scope: NO_GO for a new VSM S2 organizational controller for the declared concurrency/rollback/storage incidents; NOT a claim that #56282 is fixed, that #33940 is fixed for v2, nor a rejection of original native code fixes; does not regrade Index
- Target transition: NO_QUALIFIED_C_TARGET
- Priority rationale: S2 peer conflict is plausible as a hypothesis but present incidents are incorrect file restoration and unsupported shared SQLite assumptions, already addressed by source-native Issues and PRs; no distinct independently authorized peer choice/commitment correction beyond native safeguards evidenced, while other Sx have no supported on-top target
- P1 dependencies: Original-native regression on parallel same-file/different-file sessions, v2 undo and child snapshots including #64359, stale and missing snapshot negative, single-host vs NFS multi-node WAL and node-local XDG_DATA_HOME, and explicit application owner worktree/DB isolation
- P2 optional: Reconsider S2=C only with reproduced conflicting yet individually legitimate peer commitments after native guards, a designated independent admission/defer/replan actor, enforceable owner-approved choice and later two-session feedback; no permission grant inferred
- Proposed C construction: REJECTED pending real need — hypothetical developer-composed task/ownership mediator would observe two active sessions' file intentions and revisions, decide admit/defer/replan under user authority, protect active changes and feed results back to both. Existing source lacks evidenced additional value over native file conflict checks and separate worktrees
- C sufficiency falsifier: Run two legitimate concurrent overlapping edits and one undo after native #64359 and bounded workspace ownership repairs. If the same user-safe outcome is reached by version-guarded file revert, single-writer storage and worktree separation, then an independent S2=C controller is redundant; if they fail on a genuinely distinct coordination choice, retry with independent actor and measured outcome
- Scenario basis: OBSERVED
- Proposal-stage decision: NO_GO
- Research disposition: NO_USEFUL_CHANGE
- Proposed validation: Build pinned v2 tests for same-file conflict, distinct-file rollback, nested child snapshot and missing tree; shared DB local and NFS; compare native path and optional actor; not run in this review, native PR author-declared test results are not our test results
- Validation state: NOT_RUN
- Proposal falsifier: A repeatable first-party current runtime case with independent lawful peer commitment choices, authorized enforced decisions and returned two-session outcomes that native ownership/host isolation cannot supply
- S1 disposition: Standard agent handles coding prompts with tool feedback and explicit per-session run execution; accepted historical S1=A; no new C target
- S2 disposition: The SessionRunCoordinator serializes only each session key; peer sessions share files/DB without distinct owner, but wrong undo and SQLite WAL overlap is not proof an autonomous peer S2 is useful; NO_QUALIFIED_C_TARGET
- S3 disposition: User/application controls session start, worktree scope and permissions; per-session queue does not establish first-party whole-portfolio commitments or additional lawful S3 C actor
- S3* disposition: Snapshot logs, tests, plugins and error events do not constitute independently protected corrective audit of organizational commitments
- S4 disposition: Current code examination and model changes are not a source-grounded external future scenario with autonomous adaptation and return; no qualified target
- S5 disposition: Repository governance and tool permissions remain user/parent-configured, not transferable autonomous ultimate purpose/identity choice
- Result: NO_USEFUL_CHANGE
- External issue: DRAFT — NOT PUBLISHED
- Public fork Issue: DRAFT — NOT PUBLISHED
- Cost status: NOT_MEASURED

## Identity and pins

The [accepted included Index assessment](https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/assessments/op/opencode.md) is pinned to `c2e43bf4750841277b3e58d8ba80314121734764`, blob `60cd4ec5d2dd5ba620c815e3579d198ab5274036`, historical review `95daf90670b7c039c436c85537da5fbfe2205b41`, date 2026-09-15 and Profile/Methodology 0.2.1/0.3.1. Exact `harness_id=opencode`, original URL and review_ref match data/catalog.psv at that commit; the original review ref resolves. The current product default is **dev**, pinned `dev@11883188a61b12a30bc4fb263cd217343981ca37`; new original source does not silently update historical grade. Root [LICENSE](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/LICENSE) is MIT, [CONTRIBUTING](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/CONTRIBUTING.md) requires design review for UI/core features, and [AGENTS](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/AGENTS.md) names dev as default. [SECURITY](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/SECURITY.md) explicitly says local agent is not sandboxed and AI-generated security reports are not accepted; avoid representing this as a vulnerability submission or security claim. Fork `opensiro-contributions/opencode` with matching parent, `opensiro/meta` and `ACTIVE/ALLOW` verified before this recheck.

## Rights and authority

First-party software owns runtime execution and per-session state; the user/app decides whether sessions may share a repository/worktree or must be isolated. Filesystem locking and external DB server semantics belong outside the agent authority boundary. Core feature PRs require maintainer design review, and third-party public issue/PR/comment requires exact separate consent not granted by this review. Internal research metadata is authorized by existing `ACTIVE/ALLOW`; no original product branch changes, new public fork Issue or original maintainer communication, license exemptions or Index regrade.

## Existing work / overlap

- Current [SessionRunCoordinator](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/packages/core/src/session/run-coordinator.ts) promises one active execution per **key**, not a global worktree-level writer lock. This is useful native per-session serialization but does not protect two sessions writing the same file.
- Current [SessionRevert.plan](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/packages/core/src/session/revert.ts) selects assistant messages with `session_id` and earliest per-file snapshot, while [Snapshot.restore](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/packages/core/src/snapshot.ts) applies selected path snapshots. There is no demonstrated cross-session optimistic file revision compare before restoring a path; this is native integrity design, not inherently autonomous S2 coordination.
- [Original #33940](https://github.com/anomalyco/opencode/issues/33940) reported `/undo` reversing other chat edits. **CLOSED** with maintainer note that v1 issues were closed during migration to v2; therefore do NOT treat closure as a v2 fix or as an active v2 reproduction. Related discussion points to shared snapshot interactions.
- [Original #56282](https://github.com/anomalyco/opencode/issues/56282) is **OPEN** with WAL corruption and SQLITE_BUSY in shared network home; follow-ups include service registration handoff and single-node NFS corruption. Current [DB code](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/packages/core/src/database/database.ts) sets WAL / `busy_timeout=5000` for supported non-Durable-Object stores. Node/job-local `XDG_DATA_HOME` or supported single-writer storage is the least invasive alternative to an agent controller; this is a workaround recommendation, not verified fix for all storage.
- [Original PR #64359](https://github.com/anomalyco/opencode/pull/64359) **OPEN**, head `e5ebc83a7d2078d6884af339b053768af3dd612b`, current packages/core session and subagent diffs add background child snapshot provenance and bounded revert. Claimed 163 passed/1 skipped in PR body; NOT independently executed here.
- [Original PR #63475](https://github.com/anomalyco/opencode/pull/63475) **OPEN**, head `61fe7576834a3444c5b37100d5f388a4a8ab7605`, affects legacy packages/opencode snapshot tree failure and cannot be credited as shipped for current v2 packages/core.
- [Original PR #54396](https://github.com/anomalyco/opencode/pull/54396) **CLOSED_UNMERGED**, head `a121b9de671c12994b1b6abae00680b1c0fcf6d4`; proposes SQLite busy retries, no current shipped result from this PR.
- [Original #20849](https://github.com/anomalyco/opencode/issues/20849) describes SDK/plugin-based background team execution and optional per-agent git worktrees; CLOSED issue is research/alternative, not proof a first-party C controller ships.
- Native [Agent](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/packages/core/src/agent.ts), [Session](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/packages/core/src/session/session.ts) and runtime/plugin paths make current operations and orchestration configurable; tests and [contributors](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/CONTRIBUTING.md) bound legal contributions.

## Function ownership

| Function | Historical accepted | Current observed actor / boundary | C decision |
| --- | --- | --- | --- |
| S1 | A | Agent tasks, session tools and feedback | Existing A |
| S2 | — | Same-key run coordinator; shared file and DB operations across distinct sessions require native integrity; no independent peer arbiter established | Not qualified |
| S3 | — | Parent/user controls current session/task and worktree scope; no first-party whole-organization resource owner established | Not qualified |
| S3* | — | Error events, snapshot/audit metadata and tests are observers, not a protected independent corrective organizational reviewer | Not qualified |
| S4 | — | Coding prompts and provider configuration do not show a prospective external environment choice-to-future-work return | Not qualified |
| S5 | — | Operator retains purpose and safety envelope; user permissions are not framework identity/policy owner | Parent |

These are **source-based dispositions of the declared case** and historical accepted states, NOT a new Index classification. Whether omissions were intentional is UNVERIFIED except that operator governance remains parent-controlled by the runtime boundary.

## Capability priority

P0 **NO_QUALIFIED_C_TARGET / NO_GO**, research **NO_USEFUL_CHANGE**. P1 original-native pinned remediation of v2 restore isolation and shared SQLite compatibility, with a counterfactual after upstream PRs #64359/#63475 change status. P2 only contingent, source-backed test of an independent peer coordinator once basic integrity, worktree scoping and parent rights are demonstrated. Confidence HIGH that no on-top C is presently evidenced; native bug closure/impact are NOT validated, and S2 future usefulness remains falsifiable.

## Parallel contribution-on-top review

| Operator outcome | Track A shipped / source-native work | Track B minimal added C and test | Incremental benefit / falsifier |
| --- | --- | --- | --- |
| Undo A without deleting B's unrelated edits | Per-session message selection + path-scoped snapshot restoration; add compare-and-swap/file-writer provenance at restore | Independent S2 choice for active conflicting writes, only after native guard fails | A native revision guard is simpler; if same user outcome, new C redundant |
| Parent undo includes its already-authored child edits | OPEN #64359 accounts for child provenance and earliest snapshots; do not duplicate | A supervisor planning tool alone adds no peer decision; no qualified S2 C | PR #64359 changes behavior natively if merged; current tests not run |
| Pruned snapshot must not delete current files | OPEN #63475 legacy tree validation; current v2 requires native missing-tree negative too | External reviewer cannot reconstruct pruned data or lawfully overwrite concurrent writer | Native fail-closed restore can solve without autonomous actor |
| SQLite WAL concurrency on NFS/multi-node | OPEN #56282, current WAL/timeout, local state path or one writer per DB | Agent task arbitrator cannot repair SQLite lock guarantees | Native storage path or deployment contract needed; negative multi-node test |
| Reconcile legitimate conflicting edits from two independent coding sessions | Standard separate worktrees + git conflict resolution, application plugin coordination (#20849); no guaranteed first-party C | Hypothetical opt-in admit/defer/replan actor with independent inputs, parent bounded effect and eventual result to both sessions | Only qualified if native/host controls fail in a reproducible equal-baseline test |

## Implementation options

Prefer (a) source-native per-path version guards and stale-tree safe failure, (b) explicit worktree isolation for parallel sessions, (c) per-node or single-owner local SQLite storage or filesystem-compatible database, (d) compare exact original PR heads and current default before new code. No new controller implementation authorized.

## Specification and domain alternatives

A reviewer plugin, deterministic file guard, git worktree merge tool, database mutex or host queue may be valuable without satisfying VSM `C`. To qualify S2=C, a first-party opt-in development port must insert an independently authorized peer-coordination actor between at least two otherwise legitimate autonomous S1 sessions, choose differing allowed commitments, enforce them, and receive later execution outcomes. No current evidence that this beats deterministic conflict management; do not infer from historical `S2=—` alone.

## Cost experiment

Proposed A/B: two or more v2 sessions with identical conflicting/nonconflicting file writes, one staged undo and measured changes preserved, retries, human interrupts and task latency. Repeat with supported local storage and explicit NFS multi-process only in safe disposable environments. Compare native guard/worktrees vs independent actor including error/negative cases and maintenance complexity. **Native tests NOT_RUN; incremental cost NOT_MEASURED**.

## Delivery and publication

- `REVIEWED=true` (source/pins/PR diffs); `VALIDATION=STRUCTURAL_ONLY`; `PERSISTED` only upon exact metadata branch SHA readback; `PUBLISHED_EXTERNAL=false`.
- Historical source-pinned [old NO_GO receipt](https://github.com/opensiro-contributions/opencode/blob/0014547bb4dcc5c46fef60b2a2538b68be5ffb7f/.opensiro/issues/opencode-session-collision-20261119/roadmap.md) at different original `dev@b4d81f04...` remains available in fork Git history. New scoped verdict matches it, but the earlier case's existence and previous conversations were known before this review; **NON_BLIND_REPEAT**, not a new independently isolated first attempt.
- Do not count as new independent #58 cohort coverage. Do not claim repair of issue #56282, original product test pass, validated ROI, new Index grade, public fork issue or original maintainer communication.
