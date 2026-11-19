# OpenCode — S2 conflict-constructor sufficiency and negative decision

**PLAN_ONLY / NO_USEFUL_CHANGE · DRAFT — NOT PUBLISHED**. This is the AI/developer companion to the [Human issue](https://github.com/opensiro-contributions/opencode/blob/opensiro/meta/.opensiro/issues/opencode-session-collision-20261119/issue.md), not a second GitHub Issue.

**Accepted historical Index:** S1=A · S2=— · S3=— · S3*=— · S4=— · S5=—. [Assessment](https://github.com/opensiro/vsm-harness-index/blob/34e11ec4dd52e1ba3ee0111d8bca73f13918f54f/assessments/op/opencode.md) (blob `60cd4ec5d2dd5ba620c815e3579d198ab5274036`), reviewed 2026-09-15 at `95daf90670b7c039c436c85537da5fbfe2205b41`, Profile 0.2.1 / Methodology 0.3.1. Last successful check 2026-09-17; 63 days ago. Current source `anomalyco/opencode@88c90d08add7dd899a0caefc15609fdbb1d4b2ed` on `dev` is **not automatically regraded**. Recommend separate Index-owned reassessment.

## 1. System boundary and counterfactual

The system is the native OpenCode service with concurrent first-party S1 coding sessions/subagent sessions and shared worktree state. A user expects session B's revert to preserve unrelated session A changes. Real [#54026](https://github.com/anomalyco/opencode/issues/54026) reports cross-session destructive restore; real [#56282](https://github.com/anomalyco/opencode/issues/56282) reports database damage with concurrent processes on network/parallel storage. These must not be conflated into one hypothetical S2 system. Code, plugin configuration and static checks do not alone prove an agent-owned organizational decision. The counterfactual is a minimal project-native snapshot/revert repair plus existing separate worktrees and explicit operator guidance.

## 2. Source-native overlap by status

| Evidence item | Live status 2026-11-19 | Consequence |
| --- | --- | --- |
| [#54026](https://github.com/anomalyco/opencode/issues/54026) | OPEN ISSUE | User-facing destructive-revert need; not a constructor requirement |
| [PR #64359](https://github.com/anomalyco/opencode/pull/64359) | OPEN_PR (reviewed proposal body and diff) | Captures background-subagent changes in parent revert; cites #54026 but does not prove full cross-session isolation |
| [PR #63475](https://github.com/anomalyco/opencode/pull/63475) | OPEN_PR (reviewed body and diff) | Keeps files if snapshot is missing; distinct failure mode |
| [PR #60074](https://github.com/anomalyco/opencode/pull/60074) | OPEN_PR (reviewed body and diff) | Adds cooperative ask/answer across sessions; not independent coordination control |
| [#12711](https://github.com/anomalyco/opencode/issues/12711) | CLOSED ISSUE, original design | Flat agent teams were proposed; closure is not deployment |
| [#19215](https://github.com/anomalyco/opencode/issues/19215) | CLOSED ISSUE, original design | DB-backed agent teams proposed, not accepted shipped state |
| [#20849](https://github.com/anomalyco/opencode/issues/20849) | CLOSED ISSUE, original author redirected to its own fork | `promptAsync`, events and plugin tools can enable plugin-first orchestration without original core change; proposal, not runtime proof |
| [#56282](https://github.com/anomalyco/opencode/issues/56282) | OPEN ISSUE | Network-backed SQLite coordination failure; first isolate storage deployment/ownership |

The original project [contribution contract](https://github.com/anomalyco/opencode/blob/88c90d08add7dd899a0caefc15609fdbb1d4b2ed/CONTRIBUTING.md) prioritizes bug fixes and requires design review for core features. MIT license permits independent fork experiments; external public interaction has its own consent gate. First-page and targeted PR search plus the three listed PR bodies/diffs were examined; this is **not** an exhaustive proof that all open PRs are unrelated. Reconcile exact heads before any future implementation.

## 3. Proposed S2=C ports — NOT QUALIFIED

| Logical construction port | Required witness if reopened | Current sufficiency |
| --- | --- | --- |
| A. Conflict signal | Attributed overlap of independent S1 write/restore claims, with revision, worktree and provenance | #54026 gives a real disturbance, but no first-party S2 sensor contract proved |
| B. Option/state record | Decision context and choices `hold`, `isolate`, `serialize`; bounded agent scope | Existing session state and plugin proposal do not establish this S2 option right |
| C. Composed S2 agent | Developer-wired autonomous agent legally chooses among alternatives for interfering sessions | No source-backed materially necessary owner beyond the native fix |
| D. Enforcement | Version-checked restore/write gate honors that agent decision, denies unauthorized scope | A native scoped-restore check likely achieves the current user outcome more simply |
| E. Return/feedback | Later operation reflects the choice; conflict/preservation result returns to the coordinating actor | No operational S2=C first-party end-to-end proof |

This is a **disproven priority**, not a feature specification ready to implement. No missing port is marked shipped, and these abstract logical ports are not mandatory code architecture. Parent owner retains ultimate policy; S3 resource management and S3* review are not silently reclassified as S2.

## 4. Required matched native tests for any future claim (NOT RUN)

- Positive user outcome: two sessions on one worktree; session A changes an unrelated file, B reverts; A's bytes and file existence survive; return says which files were changed.
- Distinct lawful choice: truly overlapping B-owned change is restored; disjoint A-owned change is preserved.
- Negative authority: an agent/plugin without rights cannot roll back another session's changes, use a foreign project or override user policy.
- Staleness: change arrives between snapshot and restore; operation fails safely or retries with bounded feedback; no silent clobber.
- Compatibility: ordinary single-session revert remains functional, parent/background-subagent cases match PR #64359, and missing-snapshot behavior matches PR #63475.
- Counterfactual: test the same cases against a minimal native scoped-restore fix and an optional constructor. Added constructor must demonstrate material operator benefit, not merely pass a second test suite.

## 5. Priority, cost, rights and hard stop

**P0 — rejected:** a broad S2=C autonomous construction system. **P1 — not automatically queued:** narrowly repair/check original revert issues and native tests through separately authorized original engineering. **P2 — none.** No S3, S3*, S4, S5 proposal passes native sufficiency from this research. **Cost status: NOT_MEASURED**; compare development, integration, review, rollback, operational support and maintenance on equal inputs only if reopened.

Fork is correctly parented `opensiro-contributions/opencode`, product default `dev@d4d8567da804fc9e913363f2b0f59b1002533e07`. The `opensiro/meta` branch was absent before bootstrap; initial research record sets **PAUSE/DORMANT** without asserting owner ALLOW. No product branch changes, public fork Issue, external Issue/PR, CLA agreement, source-native tests, Index change or proven savings. New work requires actual owner RESUME where applicable and a separately requested Upgrade/communication authorization.

**Final operator decision: NO_GO.** Do not implement the S2 constructor. Native reversible conflicts and storage protection should be handled by the narrow original work unless a separately grounded operator outcome makes that insufficient. [Human decision](https://github.com/opensiro-contributions/opencode/blob/opensiro/meta/.opensiro/issues/opencode-session-collision-20261119/issue.md) · [receipt](https://github.com/opensiro-contributions/opencode/blob/opensiro/meta/.opensiro/issues/opencode-session-collision-20261119/roadmap.md).
