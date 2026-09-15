# READING LEDGER

Tracks SCREEN/READ state. Long notes belong under `notes/screening/`, `notes/reading/`, and `notes/synthesis/`.

## Status vocabulary

### Screening status
- `UNSCREENED`
- `SCREENED`

### Reading status
- `NOT_QUEUED`
- `QUEUED`
- `READING`
- `READ`
- `REVISIT`

### Decision
- `MUST READ`
- `MAP`
- `ARCHIVE`

---

# First SCREEN wave — completed 2026-09-14

## S-CE-01

Screening note: `notes/screening/SC-20260914-CE01.md`

| Paper | Decision | Read status | Map role |
|---|---|---|---|
| P0003 | MUST READ | QUEUED | cyclic-pursuit target-enclosing genealogy / capture terminology correction |
| P0004 | MUST READ | QUEUED | local-information / finite-sensing classical enclosing |
| P0008 | MUST READ | QUEUED | decentralized estimation/control + 3D moving target + collision guarantee |
| P0009 | MUST READ | QUEUED | FOV-constrained moving-target enclosing / direct sensing-boundary comparator |
| P0010 | MUST READ | QUEUED | concurrent monitoring/patrol + encirclement; persistence boundary |
| P0011 | MAP | NOT_QUEUED | whole-group / resource-balancing multi-target enclosure; not target-wise subgroup proof |
| P0012 | MUST READ | QUEUED | strongest screened encirclement → interception bridge |
| P0013 | MAP | NOT_QUEUED | safety/reconfiguration frontier; later if hard safety becomes central |

**CE minimum structural READ set:** P0003, P0004, P0008, P0009, P0010, P0012.

---

## S-PE-01

Screening note: `notes/screening/SC-20260914-PE01.md`

| Paper | Decision | Read status | Map role |
|---|---|---|---|
| P0015 | MAP | NOT_QUEUED | PE genealogy tutorial; useful organizer, not minimum theory READ |
| P0016 | MUST READ | READ | compact review of barriers/winning regions/allocation; vocabulary/genealogy anchor |
| P0018 | MUST READ | NOT_QUEUED | computational HJI reachable-set root; deferred |
| P0019 | MUST READ | READ | canonical reach-avoid semantics and signed feasibility value |
| P0020 | MUST READ | NOT_QUEUED | obstacles alter strategic dominance geometry; deferred |
| P0021 | MAP | NOT_QUEUED | precise Apollonius scope; SCREEN resolves main terminology issue |
| P0024 | MUST READ | READ | pairwise HJI certificates → matching / conservative team guarantee |
| P0025 | MUST READ | READ | analytical coalition barrier → resource-constrained assignment |
| P0028 | MUST READ | READ | no-escape angular closure + inward approach → actual capture under conditions |

**PE core READ completed:** P0016, P0019, P0024, P0025, P0028.

---

## S-LM-01

Screening note: `notes/screening/SC-20260914-LM01.md`

| Paper | Decision | Read status | Map role |
|---|---|---|---|
| P0030 | MAP | NOT_QUEUED | current RL-PE genealogy organizer |
| P0032 | MUST READ | NOT_QUEUED | decentralized execution / curriculum / physical-agent milestone |
| P0033 | MUST READ | READ | fixed-role exploration + multi-target pursuit predecessor; target-state propagation |
| P0034 | MUST READ | READ | strongest literal FOV/range/urban-occlusion information-assumption competitor |
| P0035 | MUST READ | READ | strongest Transformer/multi-target scaling and soft target-selection competitor |
| P0036 | MUST READ | QUEUED | unknown clutter + physical CTBR + real-UAV deployment milestone |
| P0037 | MUST READ | NOT_QUEUED | strongest screened theory↔RL bridge; focused follow-up candidate |
| P0038 | MAP | NOT_QUEUED | local observation + graph/GAT + constrained-communication adjacent competitor |
| P0040 | MUST READ | QUEUED | strategic self-play + real-UAV frontier; preprint caveat |
| P0042 | MUST READ | READ | strongest structural competitor: explicit assignment + hard capacity + subgroup-conditioned capture control |

---

# R-PE-01 — completed 2026-09-15

Batch synthesis: `notes/synthesis/R-PE-01.md`

Per-paper notes:
- `notes/reading/P0016.md`
- `notes/reading/P0019.md`
- `notes/reading/P0024.md`
- `notes/reading/P0025.md`
- `notes/reading/P0028.md`

READ-confirmed bridge:

`reach-avoid semantics`
→ `capturability certificate`
→ `pairwise/coalition feasibility`
→ `resource-constrained assignment`
→ `speed-aware no-escape enclosure`
→ `maintained inward contraction`
→ `capture`.

Key design hypothesis exposed by this batch:

`C(S,j) = estimated robust/probabilistic capturability of coalition S for target j`

and marginal support value

`Δ_i(S,j)=C(S∪{i},j)-C(S,j)`.

---

# R-LM-01 — completed 2026-09-15

Batch synthesis: `notes/synthesis/R-LM-01.md`

Per-paper notes:
- `notes/reading/P0033.md`
- `notes/reading/P0034.md`
- `notes/reading/P0035.md`
- `notes/reading/P0042.md`

## READ-confirmed closest competitors

- **P0042 — strongest structural competitor:** explicit learned target assignment, hard per-target capacity, subgroup-conditioned control, and spatially meaningful capture. Its Sinkhorn layer makes assignment combinatorially feasible, but not capturability-feasible; subgroup demand is prescribed rather than inferred from current capture difficulty.
- **P0034 — strongest information-assumption competitor:** finite sensing range, finite FOV, building occlusion, target loss and reacquisition. However, once one pursuer detects the target, its coordinate is shared team-wide; capture is any-one-agent proximity and the episode terminates.
- **P0035 — strongest network/scalability competitor:** entity-wise Transformer, multi-target encirclement, soft target prioritization, and 15P/4E → 80P/20E evaluation without retraining. Active target positions are globally available and there is no explicit assignment/capturability layer.
- **P0033 — strongest historical exploration+pursuit predecessor:** concurrent fixed scout/pursuer roles and multi-target simulation, but no dynamic role gate, no learned constrained target assignment, and target information is propagated through communication.

## Mandatory distinction after R-LM-01

Do not conflate:
1. `target selection / preference`;
2. `explicit assignment`;
3. `dynamic coalition/support recruitment`;
4. `capturability-aware recruitment`.

R-LM-01 found **no coalition capturability certificate** in the four closest learning competitors.

## Novelty impact

Standalone claims now ruled out include:
- local/FOV-limited UAV pursuit;
- search→pursuit→reacquisition with MARL;
- concurrent exploration/scouting + multi-target pursuit;
- Transformer multi-target encirclement / target selection / large-team scaling;
- learned explicit assignment + fixed-capacity subgroup pursuit;
- meaningful geometric multi-agent capture criterion;
- simply continuing to remaining targets after one target is completed.

Surviving candidate gap is narrower:

`persistent coverage/search`
→ `genuinely local/intermittent target detection + belief/uncertainty`
→ `learned uncertainty-aware coalition capturability`
→ `dynamic join/leave support recruitment`
→ `target-wise resource allocation`
→ `no-escape / physically meaningful capture`
→ `nonparticipants maintain coverage`
→ `capturing coalition releases back to coverage`
→ `repeated/changing target arrivals`.

This remains a **candidate gap**, not a frozen novelty claim.

---

# Remaining immediate READ queue

R-PE-01 and R-LM-01 are complete. **8 first-wave queued papers remain.**

## R-CE-01 — Classical boundary and lifecycle (NEXT, 6)
P0003, P0004, P0008, P0009, P0010, P0012

Goal: close the classical boundary on local sensing/decentralization, persistence/monitoring, and encirclement→interception before any focused search about post-capture recovery or lifecycle novelty.

## R-LM-02 — Physical deployment / strategic opponent frontier (2)
P0036, P0040

Goal: delimit physical-action/sim-to-real and strategic self-play claims.

Recommended order:
1. R-CE-01;
2. R-LM-02;
3. focused bridge/search decision after the next MASTER synthesis.

---

# MUST READ but deferred / focused follow-up

- P0018 — HJI computational root.
- P0020 — obstacle/dominance geometry.
- P0026 — 3D heterogeneous multiplayer reach-avoid + matching.
- P0029 — nonholonomic reach-avoid + pursuit enclosure function.
- P0032 — decentralized pursuit historical milestone.
- P0037 — Apollonius + MARL theory-guided bridge. R-PE-01 + R-LM-01 now make it a strong focused bridge candidate if `C(S,j)` becomes central.

Do not automatically promote these without a MASTER decision.

---

# MAP-only after SCREEN

- P0011
- P0013
- P0015
- P0021
- P0030
- P0038

No first-wave screened paper was moved to ARCHIVE.

---

# Focused gaps preserved after R-LM-01

Do not open a broad search yet. Candidate focused searches are:
- belief/uncertainty-aware coalition capturability under local sensing;
- dynamic join/leave coalition formation with state-dependent capacity;
- constrained-communication multi-target assignment/capture with repeated arrivals;
- obstacle/boundary-assisted cooperative capture;
- 3D/nonholonomic/higher-order coalition certificates.

R-CE-01 should be completed before freezing search terms around lifecycle/post-capture recovery.

---

# Zotero / PDF handling

The first-wave READ papers are already organized by the user. For each next READ batch, attach only the corresponding PDFs when practical; keep GitHub `Pxxxx` IDs as canonical research-state identifiers and do not bulk-import unscreened candidates solely because they appear in lineage notes.
