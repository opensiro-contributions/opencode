# OpenCode — optional coordination between concurrent coding sessions

**PLAN_ONLY · proposal-stage GO · research NEEDS_EVIDENCE · DRAFT — NOT PUBLISHED**

**One-sentence proposal:** Explore an optional way for OpenCode developers to coordinate competing edits from different coding sessions, including deciding which session proceeds and how the outcome is returned to the other.

**Canonical decision receipt:** [roadmap.md](roadmap.md).
**Technical companion:** [constructor-sufficiency.md](constructor-sufficiency.md).
**Working fork:** opensiro-contributions/opencode at opensiro/meta.
**Case:** .opensiro/issues/opencode-session-collision-20261119/

## 1. Why Opensiro and central accepted VSM assessment

**Why Opensiro:** Opensiro explores how Stafford Beer's Viable System Model (VSM) can inform practical AI-agent architecture. The purpose is to offer optional design ideas for discussion, not to require OpenCode to adopt VSM or claim that its current design is defective.

**ACCEPTED HISTORICAL INDEX:** S1=A · S2=— · S3=— · S3*=— · S4=— · S5=—. These are historical agent-function ownership categories, not quality ranks or current product scores.

**Repository-wide audit:** The research reviewed the OpenCode agent/session runtime, file operations, developer configuration, tests, and relevant discussions. The current original source was rechecked on 2026-11-22 at [dev@ee5fe34e136488a1839ac73bcca8321c51a31b75](https://github.com/anomalyco/opencode/commit/ee5fe34e136488a1839ac73bcca8321c51a31b75). This freshness check is not a new Index assessment.

The [accepted historical assessment](https://github.com/opensiro/vsm-harness-index/blob/1c2352b72bcb70cead9ffed869c0c31b0496b2ba/assessments/op/opencode.md) (Index commit `1c2352b72bcb70cead9ffed869c0c31b0496b2ba`; assessment blob `60cd4ec5d2dd5ba620c815e3579d198ab5274036`; review source `95daf90670b7c039c436c85537da5fbfe2205b41`, 2026-09-15; Profile 0.2.1 / Skills methodology 0.3.1) describes a previous revision of the **agent runtime**, not OpenCode's human organization.

| Function / plain-language role | Historical Index | Current source-backed observation | Candidate / priority |
| --- | --- | --- | --- |
| **S1 · Operations** — agents perform coding tasks | A | Sessions and tools carry out coding operations | Existing capability |
| **S2 · Coordination** — reduce interference between operating units | — | File locks and permissions protect individual operations; a configurable peer-decision owner was not identified | **P0:** optional S2 construction |
| **S3 · Current management** — balance current commitments and resources | — | No comparable agent-owned whole-project management closure established in this review | Not selected |
| **S3* · Independent audit** — check operational reality independently | — | Logs and tests alone do not establish an independent corrective actor | Not selected |
| **S4 · Future adaptation** — respond to external or future changes | — | No supported prospective adaptation owner established at this boundary | Not selected |
| **S5 · Identity/policy** — resolve ultimate policy and authority | — | User permissions remain binding; human governance is outside the assessed agent runtime | Parent/user authority |

**Priority rationale:** S2 provides one concrete, source-grounded construction hypothesis: choosing among competing permitted session activities is different from merely locking a file. This does not imply that OpenCode needs to add it.

**Deliberate exclusions / methodology challenge:** Human organizational decisions, external tools, plugins and multi-host/shared-filesystem guarantees are outside this proposal. We do not infer that OpenCode intentionally omitted S3–S5, or that any missing historical function must be implemented.

States `A` (agent-owned), `C` (developer-composable function owner) and `—` (no established first-party path in the historical assessment) describe ownership and construction options, not maturity. Other states, including parent-governed `P`, are explained in the linked assessment methodology.

## 2. Selected construction hypothesis and operator outcome

**Target transition:** S2=— -> S2=C

**Function-specific disturbance:** HYPOTHETICAL — two independent coding sessions may intend to edit the same file, and both may have legitimate reasons to proceed.

**Proposed C capability (P0):** Give developers an optional way to provide a coordinator that can permit, defer or hand off a competing edit, and communicate the result to affected sessions.

**Best native operator alternative:** Existing file locks, permission prompts, separate Git worktrees, and manual task scheduling may already be sufficient for many users.

**Expected user benefit:** HYPOTHETICAL — more explicit control over how concurrent sessions negotiate shared work. Actual demand, speed, quality and engineering cost are NOT_MEASURED.

**Architectural sufficiency argument:** Reuse OpenCode's existing session and file-operation safeguards; add only a developer-composable decision and feedback connection if ordinary locking does not already achieve the intended outcome. The detailed possible interfaces and safety constraints are in the technical companion.

## 3. Existing native work versus missing construction

**Track A — native coverage:** OpenCode already coordinates file mutations and authorizes writes. Related work includes [#64869](https://github.com/anomalyco/opencode/issues/64869) and open fixes [#65169](https://github.com/anomalyco/opencode/pull/65169) / [#65201](https://github.com/anomalyco/opencode/pull/65201), plus [inter-session communication #52297](https://github.com/anomalyco/opencode/issues/52297). Those discussions concern related behavior but do not establish demand for this proposal.

**Track B — independent on-top C construction:** Explore an optional first-party integration for a developer-supplied session coordinator, with lawful decisions that affect subsequent work and return feedback. No such implementation or native test result is claimed.

**Distinctness and falsifier:** Locking prevents simultaneous operations; the proposed coordinator would make explicit choices between legitimate sessions. If existing OpenCode interfaces already support that full choice-and-feedback loop, no additional mechanism is justified.

## 4. Priorities and minimum sufficient result

- **P0:** Optional developer-composable S2 coordination for permitted competing session edits, with an observable decision and returned feedback.
- **P1:** Preserve user permissions, file consistency, cancellation safety, and existing behavior when no coordinator is configured. Validate in real OpenCode sessions before claiming an implemented capability.
- **P2:** NONE.

**Proposed C-sufficiency verdict:** PROPOSED_C_SUFFICIENT as a design hypothesis only, not implemented functionality or a changed Index grade.

## 5. Proposed acceptance and stop gates

**Future positive test:** Two real sessions encounter competing edits; an optional coordinator chooses which proceeds, defers the other, and communicates the eventual handoff.

**Future negative test:** Missing or revoked authority, stale decisions or cancelled work must not bypass user permissions or leave unsafe file changes.

**Proposed falsifier:** Native OpenCode already supports an equivalent configurable choice-and-feedback loop, or the proposed connection cannot safely affect real session behavior.

**Validation state:** NOT_RUN — these are future tests, not claimed results.

## 6. Independent paths

**Original-native contribution:** Discuss with maintainers only if useful to them; prefer existing native solutions and discussions before proposing new product changes.

**Profile / Skills:** Corrections to the VSM interpretation can be proposed separately in Opensiro's public methodology.

**Domain fork:** An independently maintained research experiment is another option; OpenCode adoption is not required.

## 7. Cost hypothesis

**Cost status: NOT_MEASURED.** Whether coordination provides value over existing locks or worktrees remains an open engineering and product question, not a prerequisite for discussing the architecture.

## 8. Decision / handoff

**Proposal-stage decision:** GO

The optional S2 construction is a coherent, falsifiable architectural hypothesis, not a product recommendation.

**Research disposition:** NEEDS_EVIDENCE

No native implementation, tests, demonstrated user demand or measured benefit.

**Decision reason / next permitted step:** Invite architectural feedback about the proposed capability and existing alternatives. Any public GitHub Issue requires approval of its exact final text; nothing has been shipped or endorsed by OpenCode maintainers.

**Agent/developer handoff:** The implementation-level evidence and acceptance plan live in [constructor-sufficiency.md](constructor-sufficiency.md); canonical source pins and decisions are in [roadmap.md](roadmap.md).

**Rights and publication:** The fork's ACTIVE/ALLOW state authorizes case maintenance, not third-party contributions or automatic public publication. DRAFT — NOT PUBLISHED.

**AI disclosure:** This research and draft were prepared with AI assistance. No independent native tests, product adoption evidence, independent human validation, accepted new Index grade or cost reduction are claimed.

**Public fork Issue title (draft only):** OpenCode — optional coordination between concurrent coding sessions

**Public fork Issue body (draft only):** The eight-section Human document above is the proposed GitHub Issue body. Publication requires exact owner approval and a final payload check; this line and other draft-only instructions must not appear in a published Issue.
