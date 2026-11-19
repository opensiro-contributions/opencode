# OpenCode — Upstream Capability Roadmap Receipt

- Original repository: anomalyco/opencode
- Original HEAD: 88c90d08add7dd899a0caefc15609fdbb1d4b2ed
- Observed at: 2026-11-19
- Accepted Index assessment: https://github.com/opensiro/vsm-harness-index/blob/34e11ec4dd52e1ba3ee0111d8bca73f13918f54f/assessments/op/opencode.md
- Accepted assessment blob SHA: 60cd4ec5d2dd5ba620c815e3579d198ab5274036
- Accepted review ref: 95daf90670b7c039c436c85537da5fbfe2205b41
- Accepted reviewed at: 2026-09-15
- System in focus: Native OpenCode concurrent coding sessions and subagent sessions sharing the same project worktree, excluding external plugins and maintainer governance
- Result: NO_USEFUL_CHANGE
- External issue: DRAFT — NOT PUBLISHED
- Cost status: NOT_MEASURED

## Identity and pins

Current original branch `dev@88c90d08add7dd899a0caefc15609fdbb1d4b2ed` ([commit](https://github.com/anomalyco/opencode/commit/88c90d08add7dd899a0caefc15609fdbb1d4b2ed)), current verified working fork `opensiro-contributions/opencode` parented to `anomalyco/opencode`, fork default `dev@d4d8567da804fc9e913363f2b0f59b1002533e07`. Index repository commit `34e11ec4dd52e1ba3ee0111d8bca73f13918f54f`; assessment profile 0.2.1, method 0.3.1, last successful check 2026-09-17 (63 days). Historical six-state vector **S1=A · S2=— · S3=— · S3*=— · S4=— · S5=—**; recommend new Index-owned reassessment before relying on old classification. The current code is not newly graded here.

## Rights and authority

Original MIT license; `CONTRIBUTING.md` prioritizes narrow fixes and requires design review for core features. No independent CLA/DCO verification or maintainer consent is asserted. Internal fork research write only. Fork metadata branch absent at preflight; initial source-pinned branch bootstrap initializes **owner_control=PAUSE, attention=DORMANT**. No later effectful mutation is permitted absent attributable RESUME. No product change, original Issue, public fork Issue, public fork PR, external PR or human review was authorized.

## Existing work / overlap

- [Open issue #54026](https://github.com/anomalyco/opencode/issues/54026): one session's revert can overwrite another session's work.
- [Open issue #56282](https://github.com/anomalyco/opencode/issues/56282): concurrent storage failures on shared/parallel filesystem.
- [Open PR #64359](https://github.com/anomalyco/opencode/pull/64359): parent/subagent rollback tracking (proposed, not merged).
- [Open PR #63475](https://github.com/anomalyco/opencode/pull/63475): missing snapshot safety (proposed, not merged).
- [Open PR #60074](https://github.com/anomalyco/opencode/pull/60074): cross-session question/answer (proposed, not merged).
- [Closed design #12711](https://github.com/anomalyco/opencode/issues/12711), [closed #19215](https://github.com/anomalyco/opencode/issues/19215), [closed fork-local plugin proposal #20849](https://github.com/anomalyco/opencode/issues/20849): alternatives, not first-party shipped proof.

Targeted PR search and exact three PR bodies/diffs were inspected; no exhaustive clean PR-overlap result is claimed. Source/current status can change.

## Function ownership

S1=A was established at the Index review. Present interference among multiple real sessions is source-backed, but historical S2=— is not evidence that a currently missing autonomous S2 owner should be added. A fixed conflict-safe snapshot/restore patch is task safety, not by itself S2=C. No developer-composed organizational S2 decision actor with `hold/isolate/serialize` alternatives, authority-controlled action and feedback is shown necessary. S3/S3*/S4/S5 remain out of this proposal; no current grade inference.

## Capability priority

**P0 (rejected):** introduce a first-party S2=C multi-session coordination constructor. Added benefit beyond a narrow original-native scoped-revert fix is not demonstrated; do not implement. **P1 (not automatically a backlog):** original issue/PR alignment and the smallest regression test, conditional on separate engineering intent. **P2:** none. This is **NO_GO**, not an unresolved intermediate label.

## Implementation options

**Option A — preferred:** use source-native issue #54026, conflict-safe revert staging and regression test; incorporate compatible existing PR work if maintained. **Option B — speculative:** an installable agent-composed S2 coordinator with conflict signals, selectable authorized decisions, enforcement, later return and negative tests. The latter has more engineering/maintenance surface without a distinct proven outcome. Do not convert an old Index absence into mandatory construction.

## Specification and domain alternatives

Only if repeated native counterfactual tests establish an unresolved inter-S1 decision need should a future separate case specify S2=C ports and consider Profile/Skills feedback. A domain experimental fork is optional under license and owner rights; no public maintainer adoption or profile revision is claimed. [Human issue](https://github.com/opensiro-contributions/opencode/blob/opensiro/meta/.opensiro/issues/opencode-session-collision-20261119/issue.md) and [AI companion](https://github.com/opensiro-contributions/opencode/blob/opensiro/meta/.opensiro/issues/opencode-session-collision-20261119/constructor-sufficiency.md) agree on the baseline, priorities and NO_GO.

## Cost experiment

Same user task: session A modifies a file while session B reverts an unrelated turn. Compare a minimal native patch against an agent-composable conflict controller for preservation, regressions, developer time, review load and subsequent maintenance. No implementation/tests or matched measurements were performed. **NOT_MEASURED**.

## Delivery and publication

**PLAN_ONLY / NO_USEFUL_CHANGE; FINAL OPERATOR DECISION: NO_GO.** No speculative S2 constructor, automatic Upgrade or product branch write. Research stored only under the fork's `opensiro/meta:.opensiro/issues/opencode-session-collision-20261119/`. The full draft public fork Issue body is `issue.md`, suggested title in `README.md`; **NOT PUBLISHED**, pending separate exact current-conversation approval. No external maintainer issue is proposed. AI-assisted research; not independent human verification.
