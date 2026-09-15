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
| P0018 | MUST READ | NOT_QUEUED | computational HJI reachable-set root; retain but defer after core bridge set |
| P0019 | MUST READ | READ | canonical reach-avoid semantics and signed feasibility value |
| P0020 | MUST READ | NOT_QUEUED | obstacles alter strategic dominance geometry; important but second wave |
| P0021 | MAP | NOT_QUEUED | precise Apollonius scope; SCREEN already resolves main terminology issue |
| P0024 | MUST READ | READ | pairwise HJI certificates → matching / conservative team guarantee |
| P0025 | MUST READ | READ | analytical coalition barrier → capacity/resource-constrained assignment |
| P0028 | MUST READ | READ | no-escape angular closure + inward approach → actual capture under conditions |

**PE core READ completed:** P0016, P0019, P0024, P0025, P0028.

---

## S-LM-01

Screening note: `notes/screening/SC-20260914-LM01.md`

| Paper | Decision | Read status | Map role |
|---|---|---|---|
| P0030 | MAP | NOT_QUEUED | current RL-PE genealogy organizer |
| P0032 | MUST READ | NOT_QUEUED | decentralized execution / curriculum / physical-agent historical milestone |
| P0033 | MUST READ | QUEUED | closest older multi-target UAV scout/tracker predecessor |
| P0034 | MUST READ | QUEUED | literal local-FOV/range/urban-occlusion novelty competitor |
| P0035 | MUST READ | QUEUED | Transformer + multi-target encirclement + selection/scaling competitor |
| P0036 | MUST READ | QUEUED | unknown clutter + physical CTBR + real-UAV deployment milestone |
| P0037 | MUST READ | NOT_QUEUED | strongest screened theory↔RL bridge; now eligible for focused READ after PE core |
| P0038 | MAP | NOT_QUEUED | local observation + graph/GAT + constrained communication adjacent competitor |
| P0040 | MUST READ | QUEUED | strategic self-play + real-UAV frontier; preprint caveat |
| P0042 | MUST READ | QUEUED | strongest screened allocation + subgroup pursuit/control structural competitor |

**LM minimum next READ set:** P0033, P0034, P0035, P0036, P0040, P0042.

---

# R-PE-01 — completed 2026-09-15

Batch synthesis: `notes/synthesis/R-PE-01.md`

Per-paper notes:
- `notes/reading/P0016.md`
- `notes/reading/P0019.md`
- `notes/reading/P0024.md`
- `notes/reading/P0025.md`
- `notes/reading/P0028.md`

## READ-confirmed theory bridge

`reach-avoid semantics`
→ `signed/binary capturability certificate`
→ `pairwise or coalition feasibility`
→ `resource-constrained assignment / recruitment`
→ `speed-aware no-escape enclosure`
→ `maintained inward contraction`
→ `capture`.

Key confirmed points:
- P0019: reach-avoid is a strategy-quantified `reach + avoid` guarantee, not ordinary reachability; the zero-sublevel set of the value function is the guaranteed reach-avoid set.
- P0024: pairwise guaranteed outcomes can form a bipartite graph; a maximum matching of cardinality `m` guarantees at least `m` attackers can be stopped, rather than proving a globally optimal multiplayer joint strategy.
- P0025: coalition feasibility can be converted into constrained 0–1 assignment; in its specific simple-motion/convex-domain model, the reduced assignment is globally optimal for maximizing guaranteed intercepted evaders.
- P0028: geometric surrounding alone is insufficient. Strategy-independent capture of a faster evader requires speed-aware angular closure/no escape gap, maintained geometry, positive capture radius, sufficient geometry/cardinality conditions, and an inward/radial hunting component.

## CoCap implication

Current strongest theory-guided design hypothesis:

`C(S,j) = estimated robust/probabilistic capturability of coalition S for target j`

with marginal recruitment value

`Δ_i(S,j)=C(S∪{i},j)-C(S,j)`,

then subtract coverage opportunity cost / competing-target cost / safety or communication cost.

This is a research-design hypothesis, not yet a committed CoCap architecture.

---

# Remaining immediate READ queue

R-PE-01 is complete. **12 queued papers remain** from the first READ wave.

## R-LM-01 — Closest multi-target / sensing / allocation competitors (NEXT, 4)
P0033, P0034, P0035, P0042

Goal: delimit the strongest current CoCap novelty boundary on multi-target pursuit, local sensing, Transformer target selection, explicit allocation/subgroup control, and capture semantics.

## R-CE-01 — Classical boundary and lifecycle (6)
P0003, P0004, P0008, P0009, P0010, P0012

Goal: establish exactly what classical encirclement already solves, where local sensing/decentralization is easier than CoCap, and what exists for persistence/interception.

## R-LM-02 — Physical deployment / strategic opponent frontier (2)
P0036, P0040

Goal: delimit physical-action/sim-to-real and strategic self-play claims.

Recommended order after R-PE-01:
1. R-LM-01;
2. R-CE-01;
3. R-LM-02;
4. focused bridge/follow-up READ only if the first synthesis requires it.

---

# MUST READ but deferred / focused follow-up

- P0018 — HJI computational root; read if computational reachability lineage needs deeper reconstruction.
- P0020 — obstacle/dominance geometry; read before strategic obstacle/boundary claims.
- P0026 — 3D heterogeneous multiplayer reach-avoid + matching; R-PE-01 identified it as the most natural extension for 3D/positive-radius coalition certificates.
- P0029 — nonholonomic homicide-chauffeur reach-avoid + pursuit enclosure function; natural extension for action/dynamics realism.
- P0032 — decentralized pursuit historical milestone; read if execution architecture becomes central.
- P0037 — Apollonius + MARL theory-guided bridge; PE core prerequisite is now satisfied, but defer until R-LM-01 shows whether geometry-guided learning is central to the final CoCap story.

Do not automatically promote these into the immediate queue without a MASTER decision.

---

# MAP-only after SCREEN

- P0011
- P0013
- P0015
- P0021
- P0030
- P0038

No paper in the first SCREEN wave was moved to ARCHIVE.

---

# Focused gaps exposed by R-PE-01

Do not open a broad search yet. Preserve these as later focused-search candidates:

- partial-observation / belief-space reach-avoid + coalition assignment;
- dynamic coalition formation under target appearance/disappearance and repeated arrivals;
- robust/probabilistic capturability under local sensing and model mismatch;
- obstacle/boundary-assisted cooperative capture;
- 3D/nonholonomic/higher-order coalition certificates.

P0026 and P0029 already cover part of the last item and should be inspected before launching a new search.

---

# Zotero / PDF handling

The 17 first-wave queued papers are already organized by the user. For subsequent READ batches:
1. attach the corresponding PDFs to the child READ conversation when practical;
2. prefer the formal publication PDF, with arXiv/author manuscript as fallback;
3. keep GitHub `Pxxxx` IDs as canonical research-state identifiers;
4. do not bulk-import unscreened SEARCH candidates solely because they appear in lineage notes.
