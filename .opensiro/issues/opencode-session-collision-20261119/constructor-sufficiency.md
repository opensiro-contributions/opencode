# OpenCode — AI/developer C-sufficiency, repeated NO_GO (2026-11-20)

**Level 2 / AI.** Proposal-only source recheck; previous OpenSiro case existence known, strict fresh-chat independence NOT claimed.

**Target transition:** `NO_QUALIFIED_C_TARGET`
**Proposal-stage decision:** `NO_GO`
**Research disposition:** `NO_USEFUL_CHANGE`

[roadmap.md](roadmap.md) · [issue.md](issue.md)

## Evidence/pins

- Original `anomalyco/opencode dev@11883188a61b12a30bc4fb263cd217343981ca37`, accepted `included` [Index](https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/assessments/op/opencode.md), blob `60cd4ec5d2dd5ba620c815e3579d198ab5274036`, historical `review_ref=95daf90670b7c039c436c85537da5fbfe2205b41`, date 2026-09-15, Profile 0.2.1 / Methodology 0.3.1.
- Boundary: installed first-party v2 Agent + per-session execution and revert/snapshot, SQL persistence, optional child tasks and plugins; filesystem semantics and human S5 remain outside.
- Current [run coordinator](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/packages/core/src/session/run-coordinator.ts) serializes per key; [revert planner](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/packages/core/src/session/revert.ts) uses session IDs, but [snapshot restoration](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/packages/core/src/snapshot.ts) selects paths without a demonstrated cross-session revision-owner check. This admits source-backed tests, not a claim current undo always loses work.
- Native source PR [#64359](https://github.com/anomalyco/opencode/pull/64359) OPEN, head `e5ebc83a7d2078d6884af339b053768af3dd612b`, current v2 code plus regression test proposal; [#63475](https://github.com/anomalyco/opencode/pull/63475) OPEN, head `61fe7576834a3444c5b37100d5f388a4a8ab7605`, former packages/opencode tree-failure handler; [#54396](https://github.com/anomalyco/opencode/pull/54396) CLOSED_UNMERGED, never presume shipped.
- Original #33940 CLOSED by migration triage, not demonstrated V2 fix. #56282 OPEN; [database](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/packages/core/src/database/database.ts) still sets WAL/5s busy_timeout in supported SQLite environments, shared network filesystem issues need native storage and service coordination.

## Counterfactual requirements

A qualified S2=C should have two separate operational peer S1 agents, independently observed legitimate conflicting commitments, an **actual developer-composed first-party decisive** coordinator that can grant bounded `admit/defer/replan`, apply it under external operator S5 rights, and return result/feedback to both agents after later file operations. A deterministic file lock, rollback guard, Git merge, host scheduler, or plugin scheduling a single queue is not proof of such separate C decision right.

| Target | Cheapest native baseline | On-top delta | Disqualifier |
| --- | --- | --- | --- |
| Concurrent independent writes | Per-file writer provenance/CAS, sibling worktrees and Git merge-back | Independent actor chooses among conflicting legitimate tasks | Native protections already preserve both intended edits |
| Session /undo after peer changes | Session-scoped snapshot planning, restore against known file revision | Intervene in session priority/intent | No lawful need beyond stale-write rejection and user resolution |
| Parent/child rollback | Pending PR #64359 provenance | Separate reviewer/controller | Parent/child is hierarchical, not independent peer decision |
| Corrupt NFS WAL / shared service | Node-local `XDG_DATA_HOME` or one DB writer; native storage compatibility fix | Agent-chosen DB writer | Filesystem locking is not a choice autonomous S2 solves |
| New independent organization | Opt-in first-party port, parent scoped tools/permissions, task feedback | Proposed C actor | No observed demand/benefit at current source |

## Test plan and guardrails

If authorized for implementation later: two independent sessions A/B edit different files and same file; stage an undo from A after B's edit; ensure no B loss, no stale snapshot deletion, no unconsented overwrite; nested child and parent commit handling; session cancellation. For database test distinct local files and supported sharing patterns; isolate NFS tests to disposable data. Baseline A should satisfy these before testing autonomy. Optional B must demonstrate a distinct lawful decision *and* later-operation feedback under the same input, performance and maintenance accounting. Negative missing actor/parent denial/stale version must leave user work intact.

Do not add product code, claim tests pass, open original issue/PR/comment, change Index, or claim a closed V1 issue means V2 is fixed. `ACTIVE/ALLOW` is internal metadata only. **Validation state: NOT_RUN**, cost **NOT_MEASURED**. Scoped verdict **NO_GO / NO_USEFUL_CHANGE** is legitimate until falsified; historical metadata remains in Git history, with source-specific limits.
