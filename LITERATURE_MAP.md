# LITERATURE MAP v0.6

> MASTER state after first SEARCH + SCREEN waves and completed R-PE-01, R-LM-01, R-CE-01 READ batches. Canonical decisions here supersede earlier scaffold wording. Evidence labels: `[原文]`, `[Web核验]`, `[AI判断]`.

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

**Overall coverage:** PARTIAL-to-strong on the CoCap-relevant local-information / persistence / interception boundary after R-CE-01; not saturated.

## 2.1 Static / geometric target enclosing

READ nodes: P0003, P0004.

[原文 + AI判断]
- P0003 achieves 3-D target-centered regular enclosing from only target-relative and one-successor-relative vectors, with no inter-agent communication and collision-avoidance/convergence guarantees.
- Its title word `target-capturing` is a **lexical false friend**: the terminal object is a target-centered enclosing/tracking formation, not PE winning/no-escape/physical capture.
- P0004 extends the line to bounded unicycle motion, finite sensing and reachability/invariance reasoning around a fixed target.

Canonical terminology:
`geometric target-capturing/enclosing ≠ PE/physical capture`.

## 2.2 Moving-target / 3-D encirclement

READ nodes: P0008, P0009, P0012.

- P0008: moving 3-D target, decentralized estimation/control and collision-safe encirclement.
- P0009: moving-target FOV-constrained reference/tracking under nonholonomic uncertainty.
- P0012: moving hostile target with noisy-range estimation and encirclement→interception.

## 2.3 Distributed / local-information encirclement

READ nodes: P0003, P0004, P0008, P0010, P0012.

R-CE-01 fixes the following boundary:

`distributed ≠ partial observation`.

Evidence:
- P0008 can have one informed robot and use distributed estimators so all robots reconstruct target/frame and team quantities needed by the controller.
- P0010 uses neighbor-only distributed optimization while auxiliary dynamics reconstruct aggregate/macroscopic quantities; the target itself is a known static datum.
- P0012 begins from partial noisy ranges but fuses them into a full hostile-state estimate before control.

Therefore three separate axes are mandatory:
1. computation/decision decentralization;
2. raw measurement locality;
3. residual uncertainty in the controller's target belief after communication/estimation.

## 2.4 Obstacles / safety / boundaries

Representative nodes: P0013; P0003/P0008 provide inter-agent collision guarantees.

**Coverage:** PARTIAL.

Current evidence is stronger for inter-agent safety / CBF-type safety than for obstacles or boundaries used as strategic capture geometry. Boundary-assisted capture remains undercovered.

## 2.5 Multi-target encirclement & allocation

Representative MAP node: P0011.

Maintain distinction:
- aggregate / whole-group enclosure;
- target-wise assignment;
- dynamic subgroup/support recruitment;
- capturability-aware recruitment.

P0011 does not settle target-wise dynamic subgroup recruitment.

## 2.6 Persistent monitoring / post-capture continuation

READ node: P0010.

[原文] P0010 concurrently optimizes:
- encirclement of a known static target;
- monitoring/placement near fixed sensitive points;
- danger avoidance.

[AI判断] This **kills** novelty claims based only on “encirclement while another monitoring objective remains active.”

But P0010 does **not** implement:
- area coverage/search as the nominal mission;
- target-triggered recruitment;
- a terminal capture event;
- coalition dissolution/release;
- return to coverage/patrol.

Thus:
`concurrent monitoring + encirclement ≠ post-capture recovery`.

The lifecycle gap now concerns **task-completion-triggered resource cycling**, not persistence in general.

## 2.7 Limited sensing / FOV / bearing / range

READ nodes: P0004, P0008, P0009, P0012.

Canonical sensing ladder after R-CE-01:
1. raw local relative measurement;
2. finite sensing/FOV constraint;
3. actual intermittent target loss/occlusion;
4. distributed/filtered reconstruction of global target state;
5. unresolved local belief/uncertainty retained at decision time.

Examples:
- P0004: finite sensing + visibility invariance; not unknown-target search.
- P0009: FOV is primarily a keep-in-view geometric feasibility constraint; no loss/reacquisition/belief process, simulation only.
- P0008: blind-zone/local sensing can be overcome through distributed mutual localization/global-quantity estimation.
- P0012: noisy range-only hostile sensing is filtered into target position/velocity estimates.

Therefore standalone novelty for local sensing, finite range, FOV, range-only sensing or decentralized estimation is untenable.

## 2.8 Classical encirclement → interception

READ node: P0012.

[原文] P0012 couples:
`protected-target encirclement`
→ `hostile detection / noisy-range estimation`
→ `hostile encirclement`
→ `radius contraction`
→ `capture/takedown`,
with real-UAV direct-impact neutralization.

[AI判断] Therefore:
“classical encirclement cannot transition to actual interception” is false.

However, its formal results are estimation/encirclement bounded-convergence results, not a strategy-quantified `∀ admissible evader control` capture theorem.

P0012 and P0028 are complementary bridges:
- P0012: **perception/control → real interception**;
- P0028: **game geometry → strategy-robust no-escape/capture guarantee**.

## 2.9 Dynamic team cardinality

P0008 hardware tolerates robot addition/removal/kidnapping and restores the encircling formation.

Canonical correction:
`dynamic cardinality robustness ≠ event-driven target-specific coalition join/leave/release`.

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

CoCap evaluation should separate closure, closure maintenance, contraction and terminal capture.

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

[原文 + AI判断] P0033 is a strong predecessor for simultaneous exploration/scouting and multi-target pursuit, but role classes/counts are predefined, target information is propagated, target subteams are not produced through explicit constrained assignment, and success is tracking/proximity rather than coalition capture.

Do not interpret the paper's “autonomous heterogeneous role assignments” wording as evidence of state-dependent role switching/recruitment.

## 4.4 Literal local FOV / range / occlusion / reacquisition

Representative READ node: P0034.

[原文] P0034 has finite range, finite viewing angle, building occlusion, target loss and reacquisition.

[AI判断] This kills standalone novelty for local/FOV-limited UAV pursuit and search→pursuit→reacquisition MARL. Once any pursuer detects the target, however, its coordinate is shared team-wide; capture is any-one-agent proximity and terminates the episode.

Surviving information distinction:
**intermittent/non-globally reconstructed target belief whose uncertainty directly affects coalition/resource decisions.**

## 4.5 Variable-cardinality multi-target encirclement / target selection

Representative READ node: P0035 (TERL).

[原文] TERL provides entity-wise Transformer processing, multi-target encirclement, soft target prioritization and 15P/4E training → 80P/20E evaluation without retraining.

[AI判断] It is the strongest network/scalability competitor. It does not provide explicit team assignment, capturability-aware recruitment or strict local enemy sensing: active target positions are globally available.

Transformer, attention, target selection and scale transfer are implementation/benchmark dimensions, not CoCap headline novelty.

## 4.6 Unknown clutter + physical action + sim-to-real

Representative: P0036 — MUST READ in R-LM-02.

## 4.7 Theory-/geometry-guided MARL

Representative: P0037 — MUST READ; P0038 — MAP.

R-PE-01 + R-LM-01 make P0037 a strong focused bridge candidate if a learned capturability/escape-margin head becomes central.

## 4.8 Strategic opponent learning / self-play

Representative: P0040 — MUST READ, R-LM-02; preprint caveat.

## 4.9 Explicit assignment + subgroup pursuit/control

Representative READ node: P0042.

[原文 + AI判断] P0042 is the strongest structural CoCap competitor found so far. It combines learned target preference, hard capacity-constrained binary assignment, assignment-aware subgroup control and spatially meaningful multi-agent capture.

Critical distinction:
- assignment is **combinatorially/resource feasible**;
- subgroup size/capacity is prescribed;
- assignment is not established as **capture feasible** from current state/belief;
- target positions are available through external support;
- captured subgroups do not demonstrate return-to-coverage recovery.

Therefore P0042 is not a learned equivalent of P0025's:
`capturability certificate → feasible coalition-target pair → assignment`.

## 4.10 Learning review

Representative: P0030 — MAP.

---

# 5. Cross-Branch Bridges

## 5.1 Encirclement ↔ PE

Strong READ nodes: P0012, P0028.

Canonical synthesis:
- `geometric ring ≠ no-escape`;
- no-escape closure must be speed/strategy aware and maintained;
- actual capture requires contraction into a capture set;
- classical control can already execute perception-aware encirclement→physical interception (P0012);
- classical game theory can already give sufficient no-escape/capture conditions under strong assumptions (P0028).

Novelty cannot rest on “we move from encirclement to capture.”

## 5.2 Classical PE ↔ RL

PE teacher structures are READ-confirmed from P0019/P0024/P0025/P0028.

Potential theoretical supervision/features:
- escape feasibility;
- coalition capturability;
- marginal support-agent value;
- no-escape gap;
- near-barrier curriculum states.

RL's relevant role is to relax exact-model, full-state, simple-motion and static-assignment assumptions.

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

Leading design hypothesis:

`C(S,j) = P(capture target j | coalition S, belief/state, dynamics, obstacles)`

and

`Δ_i(S,j)=C(S∪{i},j)-C(S,j)`.

This remains a design hypothesis, not an established contribution.

## 5.4 Persistence / lifecycle bridge

R-CE-01 + R-LM-01 jointly show:
- P0033: nonparticipants/scouts can continue exploration under fixed role classes;
- P0010: monitoring objectives can coexist with encirclement in classical distributed optimization;
- P0035: agents can continue to remaining targets after one target is completed;
- P0012: classical encirclement can terminate in actual interception.

But none of the READ core shows:
`capture completion`
→ `coalition release/dissolution`
→ `return to area coverage/patrol`
→ `ready for repeated/changing arrivals`.

This is now the highest-priority literature uncertainty.

---

# 6. Current CoCap Position after R-CE-01

## 6.1 Standalone novelty claims ruled out

Do not claim novelty from any one of:
- local sensing / finite sensing / limited FOV;
- range-only/noisy target sensing;
- FOV-constrained classical encirclement;
- target loss/reacquisition MARL;
- decentralized/distributed execution;
- concurrent monitoring or scouting while pursuit/encirclement occurs;
- dynamic number of encircling agents by itself;
- multi-target pursuit;
- Transformer/attention/GNN for pursuit;
- target selection;
- explicit fixed-capacity assignment;
- subgroup pursuit/control;
- meaningful geometric multi-agent capture;
- encirclement→physical interception;
- continuing to remaining targets;
- generic capability-aware assignment;
- generic coalition capture;
- obstacles;
- continuous/physical UAV actions;
- real-UAV pursuit;
- Apollonius/game geometry + RL.

## 6.2 Strongest competitors / boundary anchors by axis

- **Structural learning competitor:** P0042 — explicit assignment + fixed hard capacity + subgroup-conditioned pursuit + spatial capture.
- **Information-assumption learning competitor:** P0034 — FOV/range/occlusion + loss/reacquisition, followed by team-wide target sharing.
- **Network/scalability competitor:** P0035 — Transformer multi-target encirclement + soft selection + 80/20 scale transfer.
- **Exploration+pursuit predecessor:** P0033 — fixed scouts + pursuers.
- **Classical distributed/local-information anchors:** P0003/P0004/P0008.
- **Classical FOV anchor:** P0009.
- **Classical concurrent persistence anchor:** P0010.
- **Classical perception→real-interception anchor:** P0012.
- **Classical capturability/allocation:** P0024/P0025.
- **Formal no-escape/capture:** P0028.
- **Physical/self-play frontier:** P0036/P0040, pending R-LM-02.

## 6.3 Mandatory semantic distinctions

The map must keep separate:

### Information
1. direct local measurement;
2. finite sensing/FOV constraint;
3. intermittent loss/occlusion;
4. reconstructed global target state;
5. unresolved local belief/uncertainty.

### Coordination
1. target preference/selection;
2. explicit assignment;
3. dynamic coalition/support recruitment;
4. capturability-aware recruitment.

### Lifecycle
1. concurrent monitoring/scouting;
2. task switching;
3. target completion;
4. coalition release;
5. return to coverage/patrol;
6. repeated-arrival readiness.

### Capture
1. geometric enclosing;
2. instantaneous spatial capture criterion;
3. no-escape closure;
4. strategy-/future-aware capturability;
5. physical interception.

## 6.4 Surviving candidate gap

[AI判断] After R-PE-01 + R-LM-01 + R-CE-01, the defensible candidate gap is:

`persistent area coverage/search`
→ `genuinely local/intermittent target belief that is not immediately globally reconstructed`
→ `uncertainty-aware coalition capturability C(S,j)`
→ `dynamic support join/leave + adaptive coalition size`
→ `target-wise resource-feasible assignment`
→ `no-escape / physically meaningful capture`
→ `nonparticipants maintain coverage`
→ **`capture completion → coalition release → return to coverage`**
→ **`repeated/changing target arrivals`**.

The gap has narrowed again:
- **concurrent persistence** is already occupied by P0010/P0033;
- **encirclement→interception** is occupied by P0012;
- **meaningful capture geometry** is occupied by P0035/P0042/P0028.

The strongest surviving story is now:
**belief-aware capture feasibility + event-driven resource cycling in a persistent coverage↔capture mission.**

This remains a **candidate novelty**, not a frozen claim.

## 6.5 Leading method hypothesis

Potential CoCap abstraction:
- learn/estimate `C(S,j)` from local/belief features;
- define support marginal gain `Δ_i(S,j)`;
- subtract coverage opportunity cost / competing-target demand / safety / communication cost;
- make target coalition capacity adaptive instead of fixed;
- release agents once capture completion makes their marginal capture value collapse;
- return released agents to coverage.

This literature map does **not** yet say this architecture should be implemented immediately; it identifies the most theory-supported design direction.

## 6.6 Focused search decision

**YES: open a narrow lifecycle-focused SEARCH before R-LM-02.**

Do not reopen broad classical or MARL searches.

Primary question:

> Has prior work already implemented `target-triggered coalition formation → capture completion → coalition release/dissolution → resume coverage/patrol → repeated threats`?

Priority query families:
- post-capture return to patrol / return to coverage;
- coalition/role dissolution and reassignment after capture;
- persistent surveillance/defense with repeated target arrivals.

Secondary, only if lifecycle search points there:
- local/uncertain target belief directly determining coalition size/membership.

## 6.7 Immediate next validation

**FS-LIFE-01 focused SEARCH is next.**

After FS-LIFE-01:
1. SCREEN only structurally relevant lifecycle candidates;
2. MASTER decides whether the lifecycle gap survives;
3. then complete R-LM-02 (P0036/P0040) unless new evidence changes priority;
4. only afterward consider P0037 / belief-aware capturability focused bridge work.
