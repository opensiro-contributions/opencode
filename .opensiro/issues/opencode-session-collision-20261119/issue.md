# OpenCode — cross-session conflict safety: native-first S2 roadmap (OpenSiro plan-only)

**OpenSiro research · PLAN_ONLY / NO_USEFUL_CHANGE · DRAFT — NOT PUBLISHED**  
**Final operator decision: NO_GO** for introducing a new S2=C orchestration constructor now. This is a first-party engineering research decision, not a denial that the cited bugs exist.

**Human case:** this file. **AI/developer contract:** [constructor-sufficiency.md](https://github.com/opensiro-contributions/opencode/blob/opensiro/meta/.opensiro/issues/opencode-session-collision-20261119/constructor-sufficiency.md). **Receipt:** [roadmap.md](https://github.com/opensiro-contributions/opencode/blob/opensiro/meta/.opensiro/issues/opencode-session-collision-20261119/roadmap.md).

## 1. Why OpenSiro and the accepted assessment

OpenSiro studies whether reusable, VSM-informed organizational specifications and evidenced native engineering can reduce the total effort of integrating and maintaining agent harnesses. Cost savings are a hypothesis, not a measured benefit; OpenCode is not asked to adopt VSM.

**STARTING POINT — ACCEPTED INDEX, NOT THE CURRENT TARGET:**  
**S1=A · S2=— · S3=— · S3*=— · S4=— · S5=—**.  
[Accepted Index assessment](https://github.com/opensiro/vsm-harness-index/blob/34e11ec4dd52e1ba3ee0111d8bca73f13918f54f/assessments/op/opencode.md), assessment blob `60cd4ec5d2dd5ba620c815e3579d198ab5274036`, reviewed 2026-09-15 at `95daf90670b7c039c436c85537da5fbfe2205b41`, checked 2026-09-17; Profile 0.2.1 / Methodology 0.3.1. These grades describe only the old reviewed revision, not [current OpenCode `dev`](https://github.com/anomalyco/opencode/commit/88c90d08add7dd899a0caefc15609fdbb1d4b2ed). Reassessment is recommended because the successful check is 63 days old; it does not block this provisional plan.

| Function | Historical accepted state | Current research treatment |
| --- | --- | --- |
| S1 Operations | A | Autonomous coding-agent operations established historically; not a C target |
| **S2 Coordination** | — | **Investigate** actual interference among parallel first-party sessions; not sufficient alone to claim missing present-day S2 |
| S3 Current control | — | Session management and rollback are not necessarily organizational S3 decisions |
| S3* Complementary audit | — | No audit-constructor target shown by these bugs |
| S4 Future adaptation | — | No separate prospective environmental intelligence target evidenced |
| S5 Ultimate policy | — | Preserve existing user, maintainer and permissions authority; no invented agent S5 |

**Boundary:** original `anomalyco/opencode` first-party developer runtime, multiple concurrent sessions/subagents acting in one project/worktree; exclude independently packaged third-party plugin decisions, maintainer governance and external deployment policies. **Sources:** original default `dev` at 88c90d08add7dd899a0caefc15609fdbb1d4b2ed, observed 2026-11-19. Working fork `opensiro-contributions/opencode` is a verified GitHub fork of the original, default `dev` at d4d8567da804fc9e913363f2b0f59b1002533e07; new metadata is initialized separately on `opensiro/meta`. Original MIT license. `CONTRIBUTING.md` requires design review for core features, discourages generic AI-generated walls of text, and does not itself establish a CLA/DCO grant. No original-repository write or external maintainer interaction is authorized by this research.

## 2. User need and simplest native path

A developer has independent sessions in the same worktree. A revert in session B should not silently undo unrelated uncommitted edits made in session A. [Original issue #54026](https://github.com/anomalyco/opencode/issues/54026) reproduces destructive rollback; [#56282](https://github.com/anomalyco/opencode/issues/56282) reports SQLite locking and corruption with shared network-backed home directories. These are distinct problems: a cross-session revert integrity bug and a storage coordination/deployment issue. They do not prove a generic agent-run S2 constructor is required.

**Smallest native alternative:** scope revert to attributable changes; detect conflicts before applying any restoring patch; preserve unrelated writes; document worktree isolation and unsupported SQLite-on-shared-filesystem conditions. Use the already open [PR #64359](https://github.com/anomalyco/opencode/pull/64359) for related parent/background-subagent rollback scope, [PR #63475](https://github.com/anomalyco/opencode/pull/63475) for missing-snapshot safety, and [PR #60074](https://github.com/anomalyco/opencode/pull/60074) for cooperative cross-session messaging. These are **OPEN_PR**, not shipped code, and their cited bodies/diffs do not by themselves prove #54026 is resolved.

## 3. Original overlap and proposed priorities

| Topic | Native evidence | Remaining question |
| --- | --- | --- |
| Cross-session revert | [#54026](https://github.com/anomalyco/opencode/issues/54026) OPEN; [#64359](https://github.com/anomalyco/opencode/pull/64359) OPEN_PR; [#63475](https://github.com/anomalyco/opencode/pull/63475) OPEN_PR | Native regression needed: B's rollback must preserve A's uncommitted edits |
| Multi-session coordination | [#12711](https://github.com/anomalyco/opencode/issues/12711) CLOSED design; [#19215](https://github.com/anomalyco/opencode/issues/19215) CLOSED design; [#20849](https://github.com/anomalyco/opencode/issues/20849) CLOSED, expressly fork/plugin-scoped; [#60074](https://github.com/anomalyco/opencode/pull/60074) OPEN_PR | Demonstrate a new outcome beyond plugin-first and existing session mechanisms |
| Shared SQLite storage | [#56282](https://github.com/anomalyco/opencode/issues/56282) OPEN | Replicate on affected filesystem and resolve single-writer/storage constraints natively before inventing S2 |

**P0 (rejected for now):** a new first-party S2=C developer-composable autonomous conflict coordinator. The added operator outcome and advantage over native fixes are unproven; **not authorized work**.  
**P1 (not automatically queued):** investigate existing issues/PRs and narrow destructive-revert regression tests inside the original engineering process, if separately selected.  
**P2:** none; no second S-function constructor supported by these sources.

## 4. Sufficiency and falsifiable stop gate

To qualify a later S2=C proposal, show a supported first-party composition path in which distinct S1 session actors genuinely interfere; a developer can install a separately agentic S2 decision owner; it receives scoped conflicts and at least `serialize`, `isolate` or `hold` choices; authorized decisions actually change which sessions may write/restore; and an observed later run returns conflict-resolution feedback. A notification-only hook, ordinary snapshot patch, fixed lock or independent plugin prototype is not by itself C.

**Acceptance to compare, NOT EXECUTED:** (a) two overlapping sessions, B reverts a read-only turn, A's uncommitted data remains byte-identical; (b) rejected untrusted/unauthorized cross-session override; (c) no extra serialization of disjoint tasks; (d) conflicting restore returns attributable status; (e) same case against the smallest native patch. A constructor is warranted only if these observable user outcomes cannot be achieved more simply. No tests were executed in this plan-only pass.

## 5. Cost and final decision

Compare the exact revert/concurrent-write task using the native scoped-restore fix versus a proposed configurable S2 controller: implementation hours, native test coverage, integration/review load, ownership and long-term maintenance. **NOT_MEASURED**; no savings claimed.

**Final operator decision: NO_GO.** Do **not** add a broad agent-team manager, new S2 runtime, scheduler, policy tier or VSM-labelled framework merely to fill the old Index `S2=—`. Prefer existing native issue/PR paths first; if a concrete independently measured coordination need survives, a new research/Upgrade command may re-enter with fresh original refs and owner authority. No product code, Index grade, parent policy or original maintainer issue is changed. The independent [AI companion](https://github.com/opensiro-contributions/opencode/blob/opensiro/meta/.opensiro/issues/opencode-session-collision-20261119/constructor-sufficiency.md) reaches the same verdict.

**Public GitHub Issue:** NOT PUBLISHED; publication in this fork requires an exact new current-conversation approval of destination, title and complete body. **AI disclosure:** Prepared with AI assistance; not human-reviewed, independently tested or maintainer-endorsed.
