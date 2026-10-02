# Portfolio Consolidation Audit — 2026-10-02

Status: DRAFT / NO REPOSITORIES ARCHIVED BY THIS AUDIT

## Live inventory

- GitHub currently reports 78 repositories owned by `thebrazenbeard`.
- 2 are already archived: `conditioning` and `self`.
- 76 are currently unarchived.
- The supplied portfolio table contains 66 repository rows, so it is not a complete current inventory.
- `pro-run` resolves to the same repository now named `pre-active`; this is a rename, not a second repository.

## Dispositions

### Already archived

- `conditioning`
- `self`

### Consolidate / reconcile before archive

#### `build-team-2.0` -> `bt2`

Evidence:
- Current `build-team-2.0` README calls itself a non-canonical predecessor/compatibility source and identifies `bt2` as active canonical BT2 source.
- `bt2/main` contains preserved material under `archive/training-sources/build-team-2.0/`.
- `build-team-2.0` has no open issues or pull requests.
- However, current `vera/main` still contains a lineage registry entry stating `build_team_2_vs_bt2 = NO_SUPERSESSION_RELATION_ESTABLISHED`.

Disposition:
`LINEAGE_RECONCILIATION_REQUIRED_BEFORE_ARCHIVE`.

Archive should not erase or rewrite historical migration records that correctly name `build-team-2.0`; archived GitHub repositories remain useful provenance sources.

#### `bugops` -> `RepairTracker`

Evidence:
- `RepairTracker` states that it supersedes BugOps as the incident and repair authority.
- BugOps still has open issue #14 (SEV-1), so operational state remains live.

Disposition:
`MIGRATE_OPEN_INCIDENTS_AND_DURABLE_REPORTS_THEN_ARCHIVE`.

Do not archive until the live issue/report lifecycle has a verified destination in RepairTracker.

### Hold active

#### `vera-R9A0`

Repository description identifies it as a historical Vera R9 snapshot, but it still has open issue #7 and open PRs #21 and #24.

Disposition:
`HOLD_ACTIVE_UNTIL_OPEN_REPAIR_LINE_CLOSES_OR_MIGRATES`.

#### `transcendence`

Tree comparison against `hc-brain/main`:
- Transcendence blobs: 268
- Every Transcendence path exists in HC-Brain.
- 260/268 same-path blobs are byte-identical.
- HC-Brain has 39 additional blobs.

This initially looks redundant, but Transcendence has active PRs #1, #6, #7, and #8, including Transcendence-specific continuity/backup architecture.

Disposition:
`HOLD_ACTIVE_DISTINCT_SUBJECT_DESPITE_HIGH_SOURCE_OVERLAP`.

#### WorkBridge family vs `executor`

- `workbridge`, `WorkBridgeMCP`, and `workbridgecommander` are still recently pushed and correspond to the currently exposed WorkBridge stack.
- `executor` is an active newer delegated-execution project and is not yet evidence that the WorkBridge stack can be archived safely.

Disposition:
`CUTOVER_REQUIRED_BEFORE_ANY_WORKBRIDGE_ARCHIVE`.

### Keep separate by current design

- `ccb-core` vs private `chat-communication-bus`: reusable public core vs private operational overlay.
- `hc-brain` vs `bt2`: reusable generic cognitive-organ template vs BT2 working/qualification workspace.
- `fuckup` vs `RepairTracker`: corrective-learning protocol/runtime vs portfolio repair operating system.
- `roots`, `semanticatlas`, and `semiotics`: provenance reconstruction, semantic mapping, and deterministic sign/interpretation registry are related but non-equivalent roles.

## First executable cleanup wave

1. Reconcile the `build-team-2.0` -> `bt2` lineage conflict in current authoritative portfolio records.
2. After exact archive authorization, archive `build-team-2.0` as read-only provenance.
3. Migrate BugOps issue/report state into RepairTracker with explicit cross-links and readback.
4. After migration verification and exact archive authorization, archive `bugops`.
5. Revisit `vera-R9A0` only after its live PR/issue line is resolved or moved.
6. Treat WorkBridge -> Executor as a later cutover project, not a cosmetic archive operation.

## Effect boundary

This audit intentionally performs no repository archive, delete, visibility change, merge, direct main mutation, deployment, credential change, or provider cutover.


## Executed cleanup wave — 2026-10-02

Verified archived repositories:

- `build-team-2.0` — archived as legacy predecessor/compatibility provenance; active BT2 workspace remains `bt2`.
- `bugops` — four open SEV-1 incidents transferred to RepairTracker issues #6–#9; exact reports and registry preserved in RepairTracker Draft PR #5; BugOps then archived.
- `brigit-unbound` — archive validator passed at exact head `f1350ef794acd0e8a657bb38d21e66f4775501a0`; repository then archived as historical provenance.

Current hold set includes `vera-R9A0`, `deepmemorystorage`, `transcendence`, and the WorkBridge family because each still has live work or an unresolved cutover dependency.

A dated Vera-side archive receipt is prepared in Draft PR #218. No merge was performed.
