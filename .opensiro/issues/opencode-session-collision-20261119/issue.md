# OpenCode — repeated NO_GO, concurrent session interference (2026-11-20)

**Level 1 / Human decision.** Current-source recheck of existing Upstream #58 `NO_GO`; non-blind rerun, not a new independent first attempt.

**Target transition:** `NO_QUALIFIED_C_TARGET`
**Proposal-stage decision:** `NO_GO`
**Research disposition:** `NO_USEFUL_CHANGE`

[roadmap.md](roadmap.md) · [constructor-sufficiency.md](constructor-sufficiency.md)

## Decision

**NO_GO to building an additional autonomous VSM S2=C peer controller now.** This does **not** mean parallel OpenCode sessions are free of data-loss risks. The original [#56282](https://github.com/anomalyco/opencode/issues/56282) is OPEN for network-filesystem WAL corruption. [#33940](https://github.com/anomalyco/opencode/issues/33940) is CLOSED because of v1→v2 triage, not verified v2 regression resolution.

Current original source is [`dev@11883188a61b12a30bc4fb263cd217343981ca37`](https://github.com/anomalyco/opencode/commit/11883188a61b12a30bc4fb263cd217343981ca37). The [accepted Index](https://github.com/opensiro/vsm-harness-index/blob/c2e43bf4750841277b3e58d8ba80314121734764/assessments/op/opencode.md) is historical, not regraded: `review_ref=95daf90670b7c039c436c85537da5fbfe2205b41`, reviewed 2026-09-15, Profile 0.2.1 / Methodology 0.3.1, blob `60cd4ec5d2dd5ba620c815e3579d198ab5274036`.

## Six-function current-source screen

| Function | Historical state | Current observed owner/closure | New C justification |
| --- | --- | --- | --- |
| **S1 · Operations** | A | Agent runs code/tools in a session and receives tool/model feedback | Existing, no C target |
| **S2 · Coordination** | — | SessionRunCoordinator serializes by session key, but distinct sessions share paths; native snapshot/worktree repair is needed | No independent C need proven |
| **S3 · Current management** | — | Users/host control overall task priority; individual sessions lack autonomous whole-portfolio decision right | Not justified |
| **S3* · Audit** | — | Errors/traces/snapshot capture alone do not have separate corrective authority | Not justified |
| **S4 · Future adaptation** | — | No supported prospective external-environment choice-to-S3 loop in this case | Not justified |
| **S5 · Ultimate policy** | — | User/project configuration and maintainer authority remain outside autonomous runtime | Parent-reserved |

The six symbols describe historical function *ownership*, not maturity. No automatic promotion from `—` to `C`.

## Existing solution versus new controller

| Source-native Track A | Optional Track B | Verdict |
| --- | --- | --- |
| [SessionRevert](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/packages/core/src/session/revert.ts) selects files from session messages; [Snapshot.restore](https://github.com/anomalyco/opencode/blob/11883188a61b12a30bc4fb263cd217343981ca37/packages/core/src/snapshot.ts) restores paths | Add actor arbitrating conflicts between peer agents | No proof deterministic per-file CAS/worktree isolation would fail |
| [#64359](https://github.com/anomalyco/opencode/pull/64359) OPEN on child snapshot provenance; [#63475](https://github.com/anomalyco/opencode/pull/63475) OPEN legacy pruned-tree rollback | Independent autonomous reviewer | Does not fix missing tree or old file content |
| [#56282](https://github.com/anomalyco/opencode/issues/56282) OPEN; SQLite WAL on shared network FS; local-state/single-writer alternative | Agent DB coordinator | Cannot supply missing filesystem lock guarantees |

**P0** no qualified new C target. **P1** compare/validate native snapshot revert regression, file ownership, worktree separation and SQLite storage invariants under disposable tests. **P2** independent S2 actor only if two legitimate agent commitments cannot be resolved by least-cost native controls.

**Falsifier:** two lawful parallel session edits still collide even after native per-file version guard + isolated worktrees, and an independently composed, parent-authorized mediator makes a distinct admit/defer/replan decision with reproducibly better later task outcomes.

**Runtime tests:** NOT_RUN. **Cost:** NOT_MEASURED. **Publication:** no external Issue/PR/comment or fork Issue; do not call closed v1 #33940 a shipped fix.
