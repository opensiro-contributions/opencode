# Proposal: optional coordination of concurrent OpenCode sessions — Opensiro VSM architecture review

## Proposal in the project's own terms

### Feature hasn't been suggested before.
- [x] I reviewed the related requests below. They cover session messaging or file-write safety; this proposal is for an optional decision-and-feedback integration, not another chat tool or mutex bug report.

### Describe the enhancement you want to request

Could OpenCode optionally allow a developer-supplied coordinator to choose **which of two authorized coding sessions may edit a shared file next, which should wait, and when to hand work off**—then tell each session what happened?

**What exists today:** OpenCode has [file-mutation locking](https://github.com/anomalyco/opencode/blob/ee5fe34e136488a1839ac73bcca8321c51a31b75/packages/core/src/file-mutation.ts), [file access and permission checks](https://github.com/anomalyco/opencode/blob/ee5fe34e136488a1839ac73bcca8321c51a31b75/packages/core/src/file-access.ts), and [session inbox delivery](https://github.com/anomalyco/opencode/blob/ee5fe34e136488a1839ac73bcca8321c51a31b75/packages/core/src/session/inbox.ts).

**What may be missing:** An optional first-party link between a policy choosing among competing legitimate edits, the effect of that choice, and feedback to the affected sessions. This is a hypothesis, not a confirmed product gap.

**Closest existing project-native solution:** Locks, user permissions, separate Git worktrees, and manual scheduling. Those may be simpler and fully adequate.

**Existing discussion:** [#60509](https://github.com/anomalyco/opencode/issues/60509) reports a concurrent edit/write race; [#64869](https://github.com/anomalyco/opencode/issues/64869) and [PRs #65169](https://github.com/anomalyco/opencode/pull/65169) / [#65201](https://github.com/anomalyco/opencode/pull/65201) concern file locks and permissions. [#52297](https://github.com/anomalyco/opencode/issues/52297), [#58367](https://github.com/anomalyco/opencode/issues/58367) and [PR #60074](https://github.com/anomalyco/opencode/pull/60074) concern messaging. None is treated as evidence that maintainers want a separate coordination policy.

This is a request for architectural feedback, not a proposed implementation PR.

## How we reached this proposal — Opensiro VSM assessment

Opensiro applies Stafford Beer's Viable System Model (VSM) to examine **who owns organizational decisions** in AI-agent runtimes. Its six functions are a way to suggest and challenge possible architectures, not six components OpenCode should implement or a product-quality score.

**Historical assessment:** [accepted Index assessment](https://github.com/opensiro/vsm-harness-index/blob/1c2352b72bcb70cead9ffed869c0c31b0496b2ba/assessments/op/opencode.md); Index commit 1c2352b72bcb70cead9ffed869c0c31b0496b2ba; assessment blob 60cd4ec5d2dd5ba620c815e3579d198ab5274036; reviewed 2026-09-15; original review ref 95daf90670b7c039c436c85537da5fbfe2205b41; Profile 0.2.1; Skills Methodology 0.3.1.

**Boundary:** The first-party OpenCode agent/session runtime. The maintainers' human organization and external shell/plugin writers are not included in the assessment.

**Current original HEAD:** [dev@ee5fe34e136488a1839ac73bcca8321c51a31b75](https://github.com/anomalyco/opencode/commit/ee5fe34e136488a1839ac73bcca8321c51a31b75), checked 2026-11-22 separately from the historical Index.

| Key | Organizational function | Historical state | Evidence or limitation |
| --- | --- | --- | --- |
| **S1 · Operations** | Agents perform coding work | A | The assessed runtime executes coding tasks |
| **S2 · Coordination** | Prevent interference between working units | — | The historical assessment did not establish agent-owned peer coordination; current locks do not necessarily make discretionary choices |
| **S3 · Current management** | Manage current resources and commitments | — | No whole-runtime agent-owned closure established at this boundary |
| **S3* · Independent audit** | Independently check operational reality | — | Logs and tests alone are not an independent corrective owner |
| **S4 · Future adaptation** | Bring external and future change into decisions | — | No established first-party adaptation owner in the historical review |
| **S5 · Identity and policy** | Resolve ultimate authority and policy | — | User and maintainer governance is outside the assessed agent runtime |

States describe ownership, **not ranks**: `A` means autonomous agent ownership; `C` means a first-party path for a developer-composed autonomous owner; `P` means supported parent-governed S3–S5 ownership; `A(P)` / `C(P)` include an independently evidenced parent mode; `—` means no material first-party path was established at the historical boundary; `?` means insufficient evidence. Historical absence is not a claim of a present defect.

## Why this particular construction?

**Whole-repository prioritization:** After examining all six functions, we selected one bounded S2 hypothesis. Maintainer interest in this specific functionality is NOT_STATED.

**Construction hypothesis:** Historical S2=— -> S2=C, a possible developer-composable S2 owner rather than a new Index grade.

**Native building blocks:** Current file access, file mutation, permissions and session inbox, plus the existing discussions linked above.

**Minimal proposed addition:** An opt-in choice-and-feedback connection for competing authorized edits. No mandatory team scheduler or AI model.

**Scope exclusions:** No shell/plugin writer interception, cross-machine file guarantees, mandatory multi-agent mode, new S3–S5 authority, or bypass of user permission rules.

## Proposed approach and validation

1. Preserve current locking, permission and file-edit behavior by default.
2. When explicitly enabled, a developer-provided coordinator may select proceed / defer / handoff between authorized sessions, with an enforceable outcome and feedback.
3. Test a two-session conflict, stale/unauthorized decisions, and full compatibility when no coordinator is configured. These tests are NOT_RUN.

**Hypothesized benefit:** Developers could experiment with richer peer coordination without replacing OpenCode's normal editing safeguards. No user demand or improvement is demonstrated.

**How to falsify:** If core or plugins already support the complete decision/effect/feedback loop, or ordinary worktrees/locking suffice, no new integration is needed.

**Cost status:** NOT_MEASURED. No performance or cost improvement is claimed.

## Feedback requested

Would this optional coordination point make architectural sense in OpenCode, or is it better left to plugins and existing locks/worktrees? An existing equivalent mechanism or design thread would be especially useful. We will not open an implementation PR without maintainer design review.

## Three independent ways to participate

- **OpenCode:** Consider the narrow proposal only if it fits the project's priorities.
- **VSM methodology:** Challenge the mapping through [Opensiro Profile](https://github.com/opensiro/vsm-harness-profile) or [Skills](https://github.com/opensiro/vsm-harness-skills).
- **Separate experiments:** Explore the idea in a legally permitted fork/plugin without requiring any OpenCode adoption.

## Research attribution and AI disclosure

[Opensiro Upstream](https://github.com/opensiro/upstream) · [source-pinned technical research](https://github.com/opensiro-contributions/opencode/blob/33f04ec87dff229abde6014e4f2ea2ee3c3a986f/.opensiro/issues/opencode-session-collision-20261119/roadmap.md) · [fork discussion](https://github.com/opensiro-contributions/opencode/issues/1)

**AI involvement:** Research and drafting used AI assistance. We do not claim native implementation/tests, independent human assessment, maintainer endorsement, accepted new Index grade, demonstrated demand or measured benefit.
