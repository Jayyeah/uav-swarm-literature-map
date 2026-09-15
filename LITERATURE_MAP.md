# LITERATURE MAP v0.5

> MASTER state after first SEARCH + SCREEN waves, completed R-PE-01 and R-LM-01 READ batches. Canonical decisions here supersede earlier scaffold wording. Evidence labels: `[原文]`, `[Web核验]`, `[AI判断]`.

## Map conventions
Coverage status: `UNSEARCHED / ACTIVE / PARTIAL / SATURATED`.
Screening decisions: `MUST READ / MAP / ARCHIVE`.
A `MUST READ` paper is not automatically in the immediate READ queue; `READING_LEDGER.md` controls timing.

---

# 1. Multi-Agent / UAV Swarm Foundations

## 1.1 Distributed control & consensus
**Coverage:** UNSEARCHED

## 1.2 Formation / flocking
**Coverage:** UNSEARCHED

## 1.3 Coverage control / Voronoi / Lloyd
**Coverage:** UNSEARCHED

## 1.4 Communication & interaction topology
**Coverage:** UNSEARCHED

## 1.5 Task allocation / coalition formation
**Coverage:** UNSEARCHED

## 1.6 Collision avoidance / CBF / MPC
**Coverage:** UNSEARCHED

---

# 2. Classical Encirclement / Enclosing / Circumnavigation

**Overall coverage:** PARTIAL; core READ pending R-CE-01.

## 2.1 Static-target encirclement
Representative screened nodes: P0003, P0004.

[AI判断] Classical literature already contains distributed/local relative-measurement enclosing and formal convergence. `target-capturing` in P0003 denotes geometric enclosing, not PE-style guaranteed capture.

## 2.2 Moving-target encirclement
Representative screened nodes: P0008, P0009, P0012.

## 2.3 Distributed / local-information encirclement
Representative screened nodes: P0004, P0008, P0009.

[AI判断] `distributed` and `partial observation` are separate axes. P0008 is decentralized but reconstructs globally relevant quantities through distributed estimation; P0004 has finite sensing-range structure but does not solve unknown-target exploration.

## 2.4 Obstacles / safety / boundaries
Representative screened node: P0013.

[AI判断] Current evidence is stronger for collision/safety than for obstacles/boundaries used as strategic capture geometry. Boundary-assisted capture remains undercovered.

## 2.5 Multi-target encirclement & allocation
Representative screened node: P0011.

Maintain distinction:
- aggregate / whole-group enclosure;
- target-wise allocation / subgroup recruitment.

P0011 does not settle target-wise dynamic subgroup recruitment.

## 2.6 Persistent / post-capture continuation
Representative screened node: P0010.

[AI判断] P0010 is evidence for concurrent monitoring/patrol + encirclement, not yet for `capture → release → return to coverage/search`. R-CE-01 must close this boundary before novelty wording is frozen.

## 2.7 Limited sensing / FOV / bearing / range
Representative screened nodes: P0004, P0009, P0012.

Standalone novelty for local sensing/FOV-constrained encirclement is untenable.

## 2.8 Realistic / nonholonomic / UAV dynamics
Representative screened nodes: P0004, P0008, P0009, P0012.

---

# 3. Pursuit–Evasion Foundations

**Overall coverage:** STRONG first CoCap-relevant theory skeleton after R-PE-01; not saturated.

## 3.1 Classical differential games
P0015 remains a MAP-level genealogy organizer. Useful PE guarantees are strategy-quantified statements, not static geometric labels.

## 3.2 HJI / reachability / reach-avoid / viability
Representative nodes: P0018, P0019; P0019 READ complete.

[原文 + AI判断] P0019 confirms:
- reachability asks whether target entry can be forced;
- reach-avoid asks whether target entry can be forced while satisfying state/avoid constraints;
- the guarantee is quantified through a non-anticipative strategy against every admissible competing input;
- the zero-sublevel set of the reach-avoid value is the guaranteed feasible set.

Therefore:
`reachable set ≠ reach-avoid set ≠ dominance region ≠ generic capture region`.

## 3.3 Capture / winning / dominance / barrier geometry
Representative nodes: P0020, P0021, P0025.

Keep distinct:
- joint-state winning/reach-avoid set;
- physical-space dominance region;
- barrier separating outcomes;
- Apollonius/Voronoi geometry.

Dominance geometry is a certificate primitive, not automatically a capture certificate.

## 3.4 Obstacles / constrained PE
Representative node: P0020.

[AI判断] Obstacles can alter strategic interception geometry itself. P0020 remains a deferred READ before strong obstacle/boundary-assisted claims.

## 3.5 Multi-pursuer / multi-evader allocation
Representative READ nodes: P0024, P0025; organizer P0016.

READ-confirmed complementary routes:
1. `pairwise HJI certificate → bipartite matching` (P0024): maximum matching size `m` guarantees at least `m` attackers stopped; conservative decomposition, not exact joint multiplayer optimum.
2. `coalition winning certificate → coalition-target assignment` (P0025): feasible coalition-target edges feed a resource/exclusivity-constrained 0–1 assignment; model-specific global-optimality scope confirmed.

Core abstraction:
`certificate → feasible edge/hyperedge → resource-constrained assignment`.

## 3.6 Encirclement → capture bridge
Strong READ node: P0028.

READ-confirmed bridge:
`speed-aware angular closure / no escape gap`
→ `maintain enclosure`
→ `radial/inward contraction`
→ `enter positive capture radius`
→ `capture`.

Thus:
`ring formation ≠ no-escape enclosure ≠ actual capture`.

CoCap evaluation should separate closure, closure maintenance, contraction, and terminal capture.

## 3.7 3D / heterogeneous / nonholonomic extensions
Canonical focused seeds:
- P0026 — 3D heterogeneous reach-avoid + matching;
- P0029 — nonholonomic/homicidal-chauffeur reach-avoid + pursuit enclosure functions.

---

# 4. Learning-Based Pursuit / Encirclement

**Overall coverage:** PARTIAL-to-strong around current CoCap nearest neighbors after R-LM-01.

## 4.1 Organizing principle
Do not organize primarily by backbone name. Organize by **which classical assumption is relaxed or which system layer is learned**.

## 4.2 Decentralized policy execution under vehicle constraints
Representative: P0032 — MUST READ, deferred.

Decentralized actors may still rely on centralized training, global teammate state, external localization or offboard execution.

## 4.3 Concurrent exploration + multi-target pursuit
Representative READ node: P0033.

[原文 + AI判断] P0033 is a strong predecessor for simultaneous exploration/scouting and multi-target pursuit, but its role classes/counts are predefined, target information is propagated through communication, multi-target subteams are not learned through explicit assignment, and success is tracking/proximity rather than coalition capture.

**Correction:** do not describe P0033 as evidence for dynamic role switching/recruitment merely because the paper uses “autonomous heterogeneous role assignments” wording.

## 4.4 Literal local FOV / range / occlusion / reacquisition
Representative READ node: P0034.

[原文] P0034 has finite range, finite viewing angle, building occlusion, target loss and reacquisition.

[AI判断] This kills standalone novelty for local/FOV-limited UAV pursuit and search→pursuit→reacquisition MARL. However, once any pursuer detects the target, the coordinate is shared team-wide; the critic has global target state during training; capture is any-one-agent proximity and terminates the episode.

Surviving distinction: strict/intermittent target knowledge under constrained propagation and uncertainty.

## 4.5 Variable-cardinality multi-target encirclement / target selection
Representative READ node: P0035 (TERL).

[原文] TERL provides entity-wise Transformer processing, multi-target encirclement, soft target prioritization, and 15P/4E training → 80P/20E evaluation without retraining.

[AI判断] It is the strongest network/scalability competitor. It does **not** provide explicit team assignment, capturability-aware recruitment, or strict local enemy sensing: active target positions are globally available.

Transformer, attention, target selection and scale transfer are implementation/benchmark dimensions, not CoCap headline novelty.

## 4.6 Unknown clutter + physical action + sim-to-real
Representative: P0036 — MUST READ in R-LM-02.

## 4.7 Theory-/geometry-guided MARL
Representative: P0037 — MUST READ; P0038 — MAP.

R-PE-01 + R-LM-01 now make P0037 a strong focused bridge candidate if a learned capturability/escape-margin head becomes central. It remains deferred until R-CE-01 closes the lifecycle boundary.

## 4.8 Strategic opponent learning / self-play
Representative: P0040 — MUST READ, R-LM-02; preprint caveat.

## 4.9 Explicit assignment + subgroup pursuit/control
Representative READ node: P0042.

[原文 + AI判断] P0042 is the strongest structural CoCap competitor found so far. It combines learned target preference, hard capacity-constrained binary assignment, assignment-aware subgroup control and spatially meaningful multi-agent capture.

Critical distinction:
- P0042's Sinkhorn/rounding makes assignment **combinatorially/resource feasible**;
- it does not establish that the assigned subgroup is **capture feasible** from the current state;
- subgroup demand/capacity is prescribed rather than inferred from target difficulty and uncertainty;
- target positions are available through external support, so “local observation” is not local target sensing;
- captured subgroups do not demonstrate return-to-coverage recovery.

Therefore P0042 is not a learned equivalent of P0025's `capturability certificate → feasible coalition-target pair → assignment` chain.

## 4.10 Learning review
Representative: P0030 — MAP.

---

# 5. Cross-Branch Bridges

## 5.1 Encirclement ↔ PE
Strong nodes: P0012, P0028.

Current synthesis:
- geometric enclosure alone is insufficient;
- no-escape closure must be speed-aware and maintained;
- actual capture also needs contraction into the capture set;
- recent classical work already performs encirclement→interception, so that transition alone cannot carry novelty.

## 5.2 Classical PE ↔ RL
PE teacher structures are READ-confirmed from P0019/P0024/P0025/P0028.

[AI判断] The useful bridge is not simply hard-coding a classical controller. Theory can provide stronger supervision/features/priors:
- escape feasibility;
- coalition capturability;
- marginal support-agent value;
- no-escape gap;
- near-barrier curriculum states.

RL then relaxes exact-model, full-state, simple-motion and static-assignment assumptions.

## 5.3 PE certificate ↔ learned allocation
READ-confirmed classical chain:
`P0019 reach-avoid semantics`
→ `P0024 pairwise certificate + matching`
→ `P0025 coalition certificate + constrained assignment`.

Closest learned analog:
`P0042 learned preference`
→ `fixed-capacity assignment`
→ `assignment-conditioned control`
→ `terminal spatial capture test`.

The semantic gap is **capture-feasibility estimation**.

Current strongest design hypothesis:

`C(S,j) = P(capture target j | coalition S, belief/state, dynamics, obstacles)`

with marginal support value

`Δ_i(S,j)=C(S∪{i},j)-C(S,j)`.

A practical objective should trade this against coverage loss, alternative-target demand, collision/safety and communication cost.

This remains a **design hypothesis**, not an established CoCap contribution.

---

# 6. Current CoCap Position after R-LM-01

## 6.1 Standalone novelty claims now ruled out

Do not claim novelty from any one of:
- local sensing / limited FOV;
- search→pursuit→reacquisition MARL;
- concurrent scouting/exploration + multi-target pursuit;
- decentralized execution;
- multi-target pursuit;
- Transformer/attention/GNN for pursuit;
- target selection;
- learned explicit assignment with fixed capacity;
- subgroup pursuit/control;
- meaningful geometric multi-agent capture criterion;
- continuing to remaining targets after one target is completed;
- generic capability-aware assignment;
- generic coalition capture;
- generic encirclement→capture;
- obstacles;
- continuous/physical UAV actions;
- real-UAV pursuit;
- Apollonius/game geometry + RL.

## 6.2 Strongest current competitors by axis

- **Overall structural competitor:** P0042 — explicit assignment + hard capacity + subgroup-conditioned pursuit + spatial capture.
- **Information-assumption competitor:** P0034 — literal finite FOV/range/building occlusion + loss/reacquisition.
- **Network/scalability competitor:** P0035 — Transformer multi-target encirclement + soft selection + 80/20 scale transfer.
- **Exploration+pursuit predecessor:** P0033 — fixed scouts + pursuers, multi-target simulation, learning evaders, real Crazyflie demonstration under UWB/offboard infrastructure.
- **Classical allocation/capturability:** P0024/P0025.
- **Formal encirclement→capture:** P0028.
- **Persistent classical boundary:** P0010, pending READ.
- **Physical/self-play frontier:** P0036/P0040, pending R-LM-02.

## 6.3 Mandatory semantic distinctions

The map must keep separate:
1. target selection/preference;
2. explicit assignment;
3. dynamic coalition/support recruitment;
4. capturability-aware recruitment.

Also distinguish:
- capacity-feasible assignment vs capturability-feasible assignment;
- instantaneous spatial capture condition vs strategy-/future-aware capturability;
- continue to remaining targets vs release/return to coverage.

R-LM-01 found **no coalition capturability certificate** in the four closest learning competitors.

## 6.4 Candidate CoCap gap that survives

[AI判断] The defensible gap has narrowed to an integrated coupling:

`persistent coverage/search`
→ `genuinely local/intermittent target detection + belief/uncertainty`
→ `learned uncertainty-aware coalition capturability`
→ `dynamic support recruitment / join / leave`
→ `target-wise resource allocation`
→ `no-escape / physically meaningful capture`
→ `nonparticipants maintain coverage`
→ `capturing coalition is released to coverage`
→ `repeated/changing target arrivals`.

No R-LM-01 paper covers this full lifecycle. Individual links are already well occupied; any defensible novelty must be about the **information + coalition-feasibility + persistent lifecycle coupling**, not isolated components.

This remains a candidate gap until R-CE-01 and focused follow-up close the main uncertainties.

## 6.5 Method hypothesis after R-PE-01 + R-LM-01

Leading theory-guided extension:
- estimate `C(S,j)` from local/belief features instead of using a hard exact-model certificate;
- recruit agent `i` based on marginal gain `Δ_i(S,j)` rather than distance or fixed count;
- combine with a resource-feasible assignment operator (P0042 is the strongest learned structural baseline);
- make target capacity/admission **adaptive to estimated capturability**, not a fixed `q_j`;
- use P0035/P0042 geometric metrics (angular balance, convex-hull enclosure, closing margin) as diagnostics/labels, not as novelty by themselves.

Directly reusable engineering:
- P0034 target-loss memory / reacquisition semantics;
- P0035 variable-cardinality entity-token processing;
- P0042 allocation/control decomposition and hard feasibility projection.

## 6.6 Focused gaps preserved

Do not launch broad search yet. Candidate focused searches:
- belief/uncertainty-aware coalition capturability under local sensing;
- dynamic join/leave coalition formation with state-dependent capacity;
- constrained-communication multi-target assignment/capture with repeated arrivals;
- obstacle/boundary-assisted cooperative capture;
- 3D/nonholonomic/higher-order coalition certificates.

R-CE-01 should be completed before freezing lifecycle/post-capture search terms. Existing P0026/P0029 should be inspected before broadening the last theory item.

## 6.7 Immediate next validation

**R-CE-01 is next.** It must determine whether classical encirclement/monitoring work already covers more of:
- persistent search/coverage while a subgroup encircles;
- release/reassignment after task completion;
- strict sensing/decentralization boundaries;
- encirclement→interception under noisy/local sensing.

After R-CE-01, run a MASTER synthesis before deciding whether to launch focused Search or proceed directly to R-LM-02.
