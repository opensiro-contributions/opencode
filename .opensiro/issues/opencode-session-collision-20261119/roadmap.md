# OpenCode — Wave 4 v0.18.1 native-specific S2 construction rerun

- Receipt contract: proposal-gate
- Original repository: anomalyco/opencode
- Original HEAD: 1607d4e624bfb2e25cf2fe6a5c44be443faa9153
- Observed at: 2026-11-20
- Accepted Index assessment: https://github.com/opensiro/vsm-harness-index/blob/1c2352b72bcb70cead9ffed869c0c31b0496b2ba/assessments/op/opencode.md
- Accepted assessment blob SHA: 60cd4ec5d2dd5ba620c815e3579d198ab5274036
- Accepted review ref: 95daf90670b7c039c436c85537da5fbfe2205b41
- Accepted reviewed at: 2026-09-15
- Accepted Index commit: 1c2352b72bcb70cead9ffed869c0c31b0496b2ba
- Accepted catalog blob SHA: e910ba68979e1f5bd2958450a23b46dc80d8f7f7
- Accepted Profile version: 0.2.1
- Accepted Methodology version: 0.3.1
- Accepted VSM vector: S1=A · S2=— · S3=— · S3*=— · S4=— · S5=—
- System in focus: First-party OpenCode v2 developer-hosted runtime of concurrently operating coding Sessions in one supported FileAccess Environment, with Core tool-mediated file operations and returned Session input; user, external shell processes, arbitrary plugins, other servers, shared NFS filesystem promises and product maintainers are outside the claimed S2 constructor
- Repository-wide source map: Default dev source entry and packages/core session execution/inbox/agent, file-access/file-write/file-mutation/tool plugins and CodeMode Bun, snapshot/revert, workspace/worktree, schema/protocol/server/app and TUI distribution, relevant core tests and docs, README/AGENTS/CONTRIBUTING/SECURITY, original issues 64869/40255/6470/33940/56282 and original PRs 65169/65201/60998/64359/63475
- Evaluation object: Developer-composable S2 choice for two independent live OpenCode sessions contending for a same-Environment file mutation, with lawful admit/defer/handoff, first-party enforcement and later feedback, distinct from deterministic native mutex, permission or filesystem repair
- Existing-work overlap: SessionRunCoordinator serializes by sessionID not shared file owner; FileMutation has process-local keyed transaction lock; FileAccess.Invocation carries sessionID and FileAccess.key identifies environment plus resolved target; FileWrite.authorize handles user permission but is not a peer coordination decision; edit/patch/write/CodeMode mutation paths and Snapshot.restore require explicit closure coverage; original PRs 65169 and 65201 repair permission-under-lock stalls (OPEN, unmerged), PR 60998 scopes inbox DB lock (OPEN), PR 64359 changes subagent revert provenance (OPEN); shared-temp issue 40255 CLOSED without proving a shipped autonomous inter-session owner
- Our on-top contribution: Optional source-native S2 decision service attached to one Core execution/Location scope, accepting real FileAccess.Invocation.sessionID plus FileAccess.key and revision from two independently running Sessions; after ordinary permission and before any per-path mutation lock it chooses admit/defer/handoff within user-provided rights; FileMutation transaction checks fence/revision at commit; deferred intent is durably recorded and completion/decline is returned through existing SessionInbox/SessionExecution wake to the affected later Session; unsupported paths fail safe or remain explicitly excluded
- Incremental benefit: A developer can install a first-party mediated decision owner choosing among two legitimate competing session commitments rather than relying solely on deterministic lock ordering; distinctness is architectural and falsifiable, actual benefit, usability, costs and runtime closure are unmeasured
- Decision scope: GO for proposed S2 constructibility only under the named local host and supported Core file-operation mode; not shipped, not a product feature recommendation, not current Index classification, not a correctness fix for arbitrary shell, undo, NFS storage or multi-host use
- Target transition: S2=— -> S2=C
- Priority rationale: S2 first because concrete two-Session competing edits, FileAccess session identity, process-local locks and durable Session execution provide original-native enforcement/feedback seams; S3 whole-project commitments and S3*/S4/S5 have weaker function-specific native construction arguments in this evaluation
- P1 dependencies: Keep exact original permission boundary and user/application authority; confirm accessible Core extension seam and per-Environment resource key; cover edit/patch/write/CodeMode mutations and either guarded Snapshot.restore or explicit fail-closed exclusion; avoid waiting on agent/model authorization under any FileMutation transaction lock; test stale claim, peer cancellation, missing owner and later feedback
- P2 optional: NONE, do not expand into S3 project-wide task scheduling, S4 model lifecycle, S5 policy, new orchestrator or speculative multi-server NFS guarantees
- Proposed C construction: PROPOSED_C_SUFFICIENT as architecture after future implementation and validation of one optional first-party Core inter-session decision owner; reuse FileAccess.Invocation.sessionID, FileAccess.key, FileMutation.withLock, FileWrite permission and SessionInbox with SessionExecution.wake; add explicit decision/commit-fence/receipt integration only where these paths currently lack it
- C sufficiency falsifier: If the native runtime already exposes an equally developer-composable autonomous S2 peer decision right with enforceable alternative choices and returned outcomes, or if the proposed service cannot enforce and return a lawful choice for two supported Sessions without bypassing standard permission, this C hypothesis fails
- Scenario basis: HYPOTHETICAL
- Proposal-stage decision: GO
- Research disposition: NEEDS_EVIDENCE
- Proposed validation: A/B with two real Core Sessions and one shared FileAccess target; independent installed S2 owner chooses defer then handoff and a different lawful choice on matched inputs, Core guards mutation at commit and returns durable feedback; compare native edit/patch mutex and dedicated worktrees, plus stale claim/missing owner/cancellation/permission and non-cooperating shell negatives; no tests executed
- Validation state: NOT_RUN
- Proposal falsifier: Native source demonstrates full S2 ownership/closure or implemented opt-in S2 cannot produce independent lawful choices, first-party effects and later feedback; simple file locks and plugin naming alone do not qualify
- S1 disposition: Agent and tool/session execution own bounded coding operations with returned environment feedback; historical A retained; no redundant C target
- S2 disposition: Sessions are independent S1s; shipped per-session scheduler and per-file process locks guard narrower mechanics, but no source-supported developer-composable cross-session owner with discretionary alternate commitments and returned S2 feedback was identified; proposed native C target
- S3 disposition: Current Session execution and background job tracking do not establish whole-project persistent adaptive resource and commitment ownership; separate S3 path not selected or inferred as required
- S3* disposition: Logging, tests, PR review and snapshot capture are not an independent corrective auditing actor in a running application; no qualified P0 in this case
- S4 disposition: Models/configuration and retrieved environment observations do not prove prospective externally informed adaptation closed into later organizational operations at chosen boundary; omission intent UNKNOWN
- S5 disposition: User/application permission and policy define lawful authority; repository governance is not an in-boundary autonomous ultimate policy owner; no S5 constructor proposed
- Result: NEEDS_EVIDENCE
- External issue: DRAFT — NOT PUBLISHED
- Public fork Issue: DRAFT — NOT PUBLISHED
- Cost status: NOT_MEASURED

## Identity and pins

[Accepted Index assessment](https://github.com/opensiro/vsm-harness-index/blob/1c2352b72bcb70cead9ffed869c0c31b0496b2ba/assessments/op/opencode.md) is included, exact repository/harness_id/review_ref matches pinned data/catalog.psv, historical source review ref [resolves](https://github.com/anomalyco/opencode/commit/95daf90670b7c039c436c85537da5fbfe2205b41), and blob 60cd4ec5d2dd5ba620c815e3579d198ab5274036 is unchanged; these are historical A/— ownership states, not current grading. Source-first verdict [#58 checkpoint](https://github.com/opensiro/upstream/issues/58#issuecomment-7043555021) was sealed against [dev@55c6827566ed4b45dd22e2fdb5660374e87faf11](https://github.com/anomalyco/opencode/commit/55c6827566ed4b45dd22e2fdb5660374e87faf11) BEFORE reading prior fork-local NO_GO. Later source freshness checked through [dev@1607d4e624bfb2e25cf2fe6a5c44be443faa9153](https://github.com/anomalyco/opencode/commit/1607d4e624bfb2e25cf2fe6a5c44be443faa9153); the three newer commits touch CodeMode and App, do not modify run-coordinator/FileMutation/SessionInbox, and do not independently establish S2 actor. Updated pin governs this receipt. A later observed original dev HEAD c1a6e6f0ead147cacc3106ea749c427b76363989 adds one UI focus-rescue change only (packages/app/component-tests/focus-rescue.spec.ts and packages/ui/src/context/focus-rescue.tsx), with no changes in the pinned S2-critical Core source paths; keep reproducible evidence pinned at 1607d4e624bfb2e25cf2fe6a5c44be443faa9153. The same-conversation rerun is source-first temporally, NOT an independently blind fresh-chat attestation.

## Rights and authority

Original LICENSE is MIT. [Original contributing instructions](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/CONTRIBUTING.md) require feature-request design approval before an original feature PR. Developer/host owns permitted sharing and file-modification scope; normal user-facing permission via FileWrite/Permission remains mandatory. An optional autonomous S2 decision cannot grant access the user refused, waive file safety or usurp S5. Fork .opensiro/state.json was ACTIVE/ALLOW for OpenSiro-internal metadata. No third-party Issue, PR, comment, product branch write or Index regrade is authorized by this record.

## Existing work / overlap

**2026-11-22 pre-publication age/source check:** Original dev now at https://github.com/anomalyco/opencode/commit/ee5fe34e136488a1839ac73bcca8321c51a31b75 (+90 commits after the recorded case revision). Relevant Core FileAccess, FileMutation, FileWrite, Session/Inbox and edit/patch/CodeMode seams were read, with no shipped optional discretionary S2 actor demonstrated in those selected paths. Original #64869 OPEN (created 2026-11-19) has competing OPEN #65169/#65201; #40255 CLOSED (created 2026-08-03) was compared with duplicate pointer #15739; #52297 OPEN (created 2026-09-30) has cross-session design discussion and open PR #60074 plus an external plugin alternative. This is a scoped freshness check, not an independent regrade, proof of need, complete current-source assessment, native test run or third-party publication. Current original maintainer authority and duplicate checks remain binding.


- [SessionRunCoordinator](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/session/run-coordinator.ts) executes at most one drain per session key and allows different session keys concurrently; it does not arbitrate overlapping intentions across Sessions.
- [FileAccess](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/file-access.ts) provides Invocation.sessionID plus canonical FileAccess.key(environment.id, absolute path). This is the exact native identity bridge for conflict claims rather than an invented global resource registry.
- [FileMutation](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/file-mutation.ts) exposes withLock on paths, process-global transactionLocks, Location-scoped write locks. It serializes cooperating mutations but does not make independent S2 choices, and does not ensure cross-process or external-writer exclusivity.
- [Edit tool](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/tool/plugin/edit.ts) performs FileWrite.target, FileWrite.authorize, commit within fileMutation.withLock; [patch tool](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/tool/plugin/patch.ts) takes multi-path mutation lock; [write tool](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/tool/plugin/write.ts) uses FileWrite.write; [CodeMode Bun](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/codemode/bun.ts) also executes authorized file writes. Proposal must place optional coordination outside long-held locks and include all in-scope first-party write leaves or expressly fail closed.
- [SessionInbox](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/session/inbox.ts), [SessionSynthetic](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/session/synthetic.ts) and [SessionExecution](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/session/execution.ts) supply durable session-directed input and wake behavior. They do not themselves arbitrate peer commitments.
- [SessionRevert](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/session/revert.ts) and [Snapshot.restore](https://github.com/anomalyco/opencode/blob/1607d4e624bfb2e25cf2fe6a5c44be443faa9153/packages/core/src/snapshot.ts) can mutate a shared tree; proposed S2 scope must not silently claim protected undo unless same revision/ownership guard exists.
- Original issue [#64869](https://github.com/anomalyco/opencode/issues/64869) OPEN describes per-path edit hang. Original [PR #65169](https://github.com/anomalyco/opencode/pull/65169) OPEN head c41f6b5f7808fd6ef0643272ea98baa20690a2cb and [PR #65201](https://github.com/anomalyco/opencode/pull/65201) OPEN head 0ab4fda9bb6fc4f7a3a06a5ce3c732ad71e6b75e both relocate permission relative to locks; these are not merged and do not supply discretionary S2 closure. [PR #60998](https://github.com/anomalyco/opencode/pull/60998) OPEN head 016f9fac26b3d0c0a53b734d47391ac4da3e9c84 scopes a database inbox mutex, not peer tasks. [PR #64359](https://github.com/anomalyco/opencode/pull/64359) OPEN head e5ebc83a7d2078d6884af339b053768af3dd612b concerns child revert snapshots, not a coordination actor.
- Original [#40255](https://github.com/anomalyco/opencode/issues/40255) CLOSED reports same-named helper-script collision across sessions, [#6470](https://github.com/anomalyco/opencode/issues/6470) CLOSED suggests sequential/parallel scheduling, [#33940](https://github.com/anomalyco/opencode/issues/33940) CLOSED historical undo risk and [#56282](https://github.com/anomalyco/opencode/issues/56282) OPEN network WAL problem. None alone establishes actual need for S2 or proves V2 current native repair; NFS/different processes, shell scripts and snapshot undo are distinct engineering problems.

## Function ownership

| Function | Historical | Current source-specific boundary | Present priority |
| --- | --- | --- | --- |
| S1 | A | Agent executes model-mediated tools with feedback inside Session | No target |
| S2 | — | FileAccess key and process FileMutation mutex; no composable cross-session choice closure shown | P0 native C hypothesis |
| S3 | — | Per-session runner and background activity, not whole team commitments | Defer |
| S3* | — | Tests/snapshots/telemetry are not independent corrective ownership | No target |
| S4 | — | Provider/config and episodic model use not shown to close prospective adaptation | No target |
| S5 | — | Operator/app permissions and original maintainer decisions are parent/environment | No target |

No observed source statement proves deliberate omission of any named VSM function; intent is UNKNOWN when not explicit.

## Capability priority

P0 is the minimum optional first-party S2 peer decision/feedback seam for supported same-Environment Core edits. P1 is source-native exact authority/fence/commit/return wiring and matched tests; P2 NONE. Rank reflects documented source affordances and falsifiability, not a feature quota, product preference, demand measurement or a missing-grade shortcut. A fully native deterministic per-file CAS or separate-worktree workflow is the cheapest baseline; its success does not veto construction unless it also owns equivalent S2 discretionary decisions and closed feedback.

## Parallel contribution-on-top review

- Evaluation object: Two live Session IDs authorized to change one resolved Environment file; distinguish independent S2 coordination choice from file lock ordering or manual isolation
- Existing-work overlap: Shipped RunCoordinator/FileMutation/FileWrite plus OPEN PR #65169/#65201/#60998/#64359 and existing Issue #64869; no sourced complete first-party autonomous S2 actor for this scoped peer case
- Our on-top contribution: One optional first-party Location-hosted peer coordination interface consuming FileAccess.Invocation.sessionID and FileAccess.key with versioned mutable intent, returning lawful decision through guarded FileMutation commit and SessionInbox feedback; no generic S2 platform
- Incremental benefit: Architecturally possible differently authorized peer outcome with later feedback; real user value unmeasured and not mandated by OpenCode maintainers
- Decision scope: Proposed S2=C constructibility GO only, not native file-write correctness, implementation acceptance, deployed C, Index regrade or third-party publication

| Required S2 link | Track A actual native coverage | Proposed missing native link | Primary falsifier |
| --- | --- | --- | --- |
| Recognize distinct S1s and collision | Invocation.sessionID and FileAccess.key; RunCoordinator per Session | Persist/reconcile competing in-scope session edit intentions with current resource revision | Claims remain stale or refer to different Environment |
| Autonomous lawful decision | Native Permission.assert and mutex lock ordering; no peer S2 actor evidenced | Developer-composable autonomous coordinator chooses admit/defer/handoff within user rights after approval | All choices remain hardcoded or override refused permissions |
| Enforce different outcome | FileMutation.withLock and FileWrite.commit | Verify decision fence/revision under commit lock; rejected/deferred mutation never applied | A previously deferred tool still writes or other session overwrites |
| Later feedback | SessionSynthetic/Inbox, SessionExecution.wake | Deliver durable release/conflict/commit receipt and wake eligible Session | Peer never observes outcome and cannot choose next action |

## Implementation options

Prefer the narrowest first-party edit-mode seam. (1) Observe Session ID from FileAccess.Invocation at FileWrite.target/tool leaves; compute same-Environment FileAccess.key. (2) After existing approval and before entering FileMutation.withLock, call an optional developer-composed autonomous S2 actor over both live commitments; no lock held across an LLM or human decision. (3) For the winning action revalidate a revision/claim fence at the locked mutation transaction; defer means exit without mutation and record an intent. (4) On completion, cancellation or stale revision, publish a typed synthetic receipt through SessionInbox and wake the waiting Session; the actor may then choose a different lawful handoff. Edit, patch, write and CodeMode Bun must share guards at the declared mode; if the implementation can only protect a subset, explicitly narrow the declared boundary and reject unsupported cross-path assertions. Snapshot.restore, shell writes, external writers and multi-server shared state do not inherit a guarantee. Prefer worktree isolation/native revision checks if the requested outcome is solely preventing lost writes. No code written now.

## Specification and domain alternatives

Accepted Index S2=— does not establish an error. A static lock, permission prompt, parent scheduler or plugin event alone is not an autonomous S2 constructor. The independently composed actor must change a legitimate peer coordination choice and obtain real later feedback, while OpenCode retains first-party supported effect rights. An arbitrary policy/approval/S5 actor is neither introduced nor claimed. Any semantic dispute belongs in Profile/Skills, not an Upstream grade rewrite. Original maintainer decides if the architecture is desirable or if simpler native repair is preferred.

## Cost experiment

Run future native tests under packages/core (package.json defines bun run test and bun typecheck) for a disposable two-Session same-file task; compare same observations and user-permitted scopes for baseline locks/worktrees and optional S2 intervention. Measure edits preserved, task completion and human interruption/engineering maintenance only if implemented; costs and actual benefits NOT_MEASURED. No native tests were run in this plan-only research.

## Delivery and publication

- New Wave 4 source-first conclusion was posted to [Upstream #58](https://github.com/opensiro/upstream/issues/58#issuecomment-7043555021) before reading fork history. Prior fork historical NO_GO evaluated lack of demonstrated incremental product utility and native file/rollback/storage alternatives; current v0.18.1 GO evaluates possible independent S2 ownership/feedback construction, not product usefulness. Both are preserved in Git history, neither is an external maintainer verdict.
- In the previous fork case, [historical NO_GO commit](https://github.com/opensiro-contributions/opencode/commit/10ce52828e926a41c8731367f66264fec84de5c6) was NON_BLIND repeated assessment; this run is temporally source-first but not claimed as a totally fresh independent-context evaluation.
- Full authority stays in this fork .opensiro case and attributed append-only event. Original native tests NOT_RUN, cost NOT_MEASURED, public fork Issue DRAFT — NOT PUBLISHED, original maintainer Issue/PR NOT_PUBLISHED, Upstream status-only PR NOT_CREATED under post-v0.18.1 reporting hygiene.
