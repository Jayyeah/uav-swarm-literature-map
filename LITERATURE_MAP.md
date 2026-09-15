# LITERATURE MAP v0.7

> MASTER state after first SEARCH + SCREEN waves, completed R-PE-01 / R-LM-01 / R-CE-01 READ batches, and completed FS-LIFE-01 focused lifecycle SEARCH. Detailed evidence remains in `notes/reading/`, `notes/synthesis/`, and search handoffs. Evidence labels: `[原文]`, `[Web核验]`, `[AI判断]`.

## Map conventions

Coverage status: `UNSEARCHED / ACTIVE / PARTIAL / SATURATED`.
Screening decisions: `MUST READ / MAP / ARCHIVE`.
A `MUST READ` paper is not automatically in the immediate READ queue; `READING_LEDGER.md` controls timing.

---

# 1. Multi-Agent / UAV Swarm Foundations

These background branches remain intentionally underdeveloped because current work is problem-boundary driven rather than a full general swarm-control survey.

- distributed control & consensus — `UNSEARCHED`
- formation / flocking — `UNSEARCHED`
- coverage / Voronoi / Lloyd — `UNSEARCHED`
- communication topology — `UNSEARCHED`
- generic MRTA / coalition formation — only CoCap-relevant slices searched
- collision avoidance / CBF / MPC — only encirclement/pursuit-relevant slices searched

---

# 2. Classical Encirclement / Enclosing

**Coverage:** PARTIAL-to-strong on CoCap-relevant sensing, decentralization, persistence and interception boundaries after R-CE-01.

## 2.1 Geometric enclosing is mature and is not PE capture

READ anchors: P0003, P0004, P0008, P0009.

Classical work already covers:
- communication-free/local relative geometry;
- finite sensing and visibility invariance;
- nonholonomic motion;
- moving 3-D targets;
- decentralized estimation;
- collision-safe encirclement;
- FOV-constrained tracking.

Canonical terminology:

`geometric target-capturing/enclosing ≠ no-escape enclosure ≠ PE/physical capture`.

P0003's `target-capturing` is a lexical false friend: the result is target-centered enclosing/tracking formation, not forced capture.

## 2.2 Distributed is not the same as partial observation

READ anchors: P0008, P0010, P0012.

The map must distinguish:
1. computation/decision decentralization;
2. raw measurement locality;
3. communication topology;
4. reconstructed target/global state;
5. residual uncertainty in each agent's decision-time belief.

P0008 is the canonical counterexample to equating distributed execution with local target knowledge: decentralized estimators reconstruct global target/frame quantities. P0012 begins with noisy local ranges but filters them into a target-state estimate before control.

## 2.3 Sensing ladder

Canonical sensing levels:
1. direct local relative measurement;
2. finite range/FOV constraint;
3. actual intermittent loss/occlusion;
4. distributed/filtered global-state reconstruction;
5. unresolved local belief/uncertainty retained at decision time.

P0004/P0009 occupy levels 2; P0034 occupies true loss/occlusion/reacquisition; P0008/P0012 show reconstruction. CoCap can no longer claim novelty from local sensing/FOV/range-only sensing alone.

## 2.4 Persistence already exists, but task-completion recovery is different

READ anchor: P0010.

P0010 proves that distributed classical optimization can concurrently maintain known-target encirclement, fixed-spot monitoring and safety objectives.

Therefore:

`monitoring/patrol + encirclement ≠ post-capture recovery`.

Concurrent persistence is old. The open lifecycle question is completion-triggered resource cycling.

## 2.5 Classical encirclement can transition to real interception

READ anchor: P0012.

P0012 couples noisy range sensing → KF target estimation → mode switching → hostile encirclement → radius contraction → real-UAV direct-impact interception.

Thus the claim “classical encirclement cannot perform actual interception” is false.

P0012 and P0028 are complementary:
- P0012: perception/control → physical interception;
- P0028: game geometry → no-escape / strategy-robust capture conditions.

---

# 3. Pursuit–Evasion Foundations

**Coverage:** STRONG first CoCap-relevant theory skeleton after R-PE-01; not globally saturated.

## 3.1 Reach-avoid semantics

READ anchor: P0019.

`reachable set ≠ reach-avoid set ≠ dominance region ≠ generic capture region`.

Reach-avoid is a strategy-quantified guarantee of reaching a target while respecting avoid/state constraints. Its value function is useful for CoCap primarily as an oracle/teacher for feasibility or escape margin, not as a direct many-UAV online solver.

## 3.2 Pairwise / coalition certificates → assignment

READ anchors: P0024, P0025.

Two complementary routes are confirmed:

1. `pairwise HJI outcome → bipartite feasible edge → maximum matching` (P0024). A matching of size `m` gives a conservative guarantee that at least `m` attackers can be stopped; it is not an exact joint multiplayer solution.
2. `coalition winning certificate → coalition-target feasible hyperedge → constrained assignment` (P0025). In its model-specific simple-motion/convex-domain setting, resource/exclusivity-constrained assignment maximizes guaranteed intercepted evaders.

Canonical abstraction:

`capturability certificate → feasible edge/hyperedge → resource-constrained assignment`.

## 3.3 Encirclement → capture requires more than a ring

READ anchor: P0028.

Confirmed bridge:

`speed-aware escape-gap closure`
→ `maintain closure`
→ `radial/inward contraction`
→ `enter positive capture radius`
→ `capture`.

Therefore:

`ring formation ≠ no-escape enclosure ≠ actual capture`.

## 3.4 Deferred theory extensions

- P0020 — obstacles alter strategic dominance geometry.
- P0026 — 3-D heterogeneous multiplayer reach-avoid + matching.
- P0029 — nonholonomic/homicidal-chauffeur reach-avoid + pursuit enclosure functions.

Inspect these before opening another broad theory search.

---

# 4. Learning-Based Pursuit / Encirclement

**Coverage:** PARTIAL-to-strong around current CoCap nearest neighbors after R-LM-01.

Organize learning work by **which classical assumption/system layer is relaxed**, not by backbone name alone.

## 4.1 Strongest current competitors by axis

- **P0042 — structural:** learned target preference + hard capacity-constrained assignment + subgroup-conditioned pursuit + spatial multi-agent capture.
- **P0034 — information assumption:** finite range/FOV/building occlusion + target loss/reacquisition, followed by team-wide sharing after detection.
- **P0035 — network/scalability:** Transformer entity processing + soft target selection + large team/target count transfer.
- **P0033 — exploration+pursuit predecessor:** fixed scouts continue exploration while fixed pursuers conduct multi-target pursuit.
- **P0036 / P0040 — physical/self-play frontier:** queued for R-LM-02.

## 4.2 Target selection, assignment and recruitment are different

Mandatory distinction:

`target preference/selection`
≠ `explicit resource-feasible assignment`
≠ `dynamic coalition/support recruitment`
≠ `capturability-aware recruitment`.

P0042 is the closest learned analogue to a classical assignment pipeline, but its target capacity is prescribed and combinatorially feasible, not inferred from current-state capture feasibility.

R-LM-01 found no coalition capturability certificate in the four closest learning papers.

## 4.3 Theory-guided learning bridge

READ-confirmed classical chain:

`P0019 reach-avoid semantics`
→ `P0024 pairwise certificate + matching`
→ `P0025 coalition certificate + assignment`.

Closest learned structural analogue:

`P0042 learned preference`
→ `fixed-capacity assignment`
→ `assignment-conditioned control`
→ `terminal spatial capture test`.

The remaining semantic gap is **capture-feasibility estimation under realistic/local uncertainty**.

Leading design hypothesis:

`C(S,j)=P(capture target j | coalition S, belief/state, dynamics, obstacles)`

and marginal recruitment value

`Δ_i(S,j)=C(S∪{i},j)-C(S,j)`.

This is a design hypothesis, not yet an established contribution.

---

# 5. Lifecycle / Persistent Mission Bridge

**Focused SEARCH status:** `SATURATED` at first-pass depth after FS-LIFE-01. Next step is SCREEN, not more broad search.

Canonical candidates: P0043–P0051.

## 5.1 Weak lifecycle novelty claims are now dead

FS-LIFE-01 found explicit antecedents for major individual edges:

- **P0046 Bradshaw 2008:** apprehension completion → explicit post-success behavior including `resume patrolling`.
- **P0043 Liu 2025:** task completion → temporary coalition dissolution → agents return to reusable uncommitted pool; destroyed targets are replaced by pop-up targets.
- **P0045 HECTOR 2026:** subtask completion → coalition dissolution → robot reassignment under continual random task arrivals.
- **P0048 Duarte 2014:** persistent patrol → local detection → temporary pursuit → return to patrol → repeated intruders, but pursuit termination is loss/exit rather than capture.
- **P0050 Chandler 2009:** persistent patrol with recurring Poisson alerts.
- **P0051 Bajaj 2023:** repeated arbitrary-time intruders + capture/defense.

Therefore do **not** claim standalone novelty for:
- post-capture/apprehension return to patrol;
- completion-triggered coalition dissolution;
- released agents becoming reusable resources;
- repeated threat arrivals;
- patrol→response→return cycles;
- continual task reassignment after completion.

## 5.2 Strongest lifecycle competitors

### P0043 — strongest structural resource-cycling analogue

Temporary UAV coalition forms for a target, strike completion dissolves the coalition, agents return to `uncommitted`, and destroyed targets are replaced by pop-up targets. Critical caveat: `uncommitted` is not area coverage/search, and the task is strike/neutralization rather than PE capture.

### P0044 — strongest capture-specific lifecycle competitor

KS-COAL combines exploration/detection, resource defense, dynamic capture coalitions, explicit local capture completion and continued online reassignment. SCREEN must verify the exact post-capture fate of the same capturing robots and communication/sensing assumptions.

### P0045 — strongest generic continual coalition-dissolution result

HECTOR explicitly dissolves coalitions on subtask completion and reassigns robots under continual random mission releases, including moving capture subtasks. It does not return robots specifically to nominal coverage and uses externally available moving-target positions.

### P0046 / P0047 — historical return-to-patrol anchors

P0046 explicitly specifies `intruder apprehended → resume patrolling`; P0047 gives a clean classical multi-UAV `perimeter patrol → alert response → return to coordinated patrol`, but without physical capture.

## 5.3 The lifecycle gap only partially survives

No FS-LIFE-01 candidate at SEARCH depth clearly closes the full same-pool loop:

`persistent area coverage/search`
→ `target-triggered temporary capture coalition`
→ `explicit capture completion`
→ `completion-triggered coalition release`
→ `same agents restore nominal area coverage`
→ `repeat under new arrivals`.

The isolated edges are not novel. The surviving candidate is their **same-resource-pool integration**, particularly when coupled to local/intermittent target belief and capturability-aware recruitment.

Current lifecycle status: **PARTIALLY SURVIVES**, pending S-LIFE-01 semantic verification.

---

# 6. Current CoCap Novelty Boundary

## 6.1 Standalone claims that are no longer defensible

Do not claim novelty from any one of:
- local sensing / finite range / FOV;
- target loss/reacquisition;
- range-only/noisy sensing;
- distributed/decentralized execution;
- multi-target pursuit;
- Transformer/attention/GNN;
- target preference/selection;
- fixed-capacity assignment;
- subgroup pursuit/control;
- generic dynamic coalition formation;
- generic capturability/capability-aware assignment;
- meaningful geometric multi-agent capture;
- no-escape/capture geometry;
- encirclement→physical interception;
- concurrent monitoring/scouting during pursuit;
- task completion→coalition dissolution;
- post-apprehension return to patrol;
- continual/repeated target arrivals;
- released-resource reassignment;
- real-UAV pursuit;
- continuous/physical actions;
- self-play or game geometry + RL by itself.

## 6.2 Surviving candidate gap after FS-LIFE-01

[AI判断] The most defensible current candidate is the **coupling**:

`persistent area coverage/search by one fungible swarm`
→ `genuinely local/intermittent target belief, not immediately globally reconstructed`
→ `uncertainty-aware coalition capturability C(S,j)`
→ `state-dependent support join/leave and adaptive coalition size`
→ `target-wise resource-feasible assignment`
→ `no-escape / physically meaningful capture`
→ `nonparticipants maintain coverage`
→ `capture completion releases the same agents`
→ `released agents restore nominal coverage`
→ `repeat under changing/new target arrivals`.

This is narrower than all earlier versions. It must not be phrased as “first post-capture recovery” or “first dynamic coalition.”

The strongest possible narrative, if S-LIFE-01 and later implementation evidence support it, is closer to:

> learn and use capture-feasibility structure under unresolved local target uncertainty to dynamically borrow agents from a persistent coverage swarm, then release them back after capture so the same resource pool repeatedly cycles between coverage and capture.

This remains a **candidate novelty**, not a frozen paper claim.

## 6.3 Leading method implications

Theory/literature currently motivates, but does not require:
- learned/probabilistic `C(S,j)` rather than fixed subgroup count;
- marginal support gain `Δ_i(S,j)`;
- coverage opportunity cost inside recruitment/allocation;
- adaptive target capacity based on estimated capture difficulty;
- explicit release criterion after terminal capture;
- persistent/repeated-arrival evaluation rather than one-shot episode termination.

---

# 7. Immediate Work Plan

## NEXT — S-LIFE-01 focused SCREEN

Screen P0043–P0051 only. Key questions:
- does capture/task completion actually trigger coalition dissolution?
- do the **same agents** resume nominal patrol/coverage, or merely become uncommitted/reassigned?
- is the nominal task true area coverage/search or only fixed patrol/alert servicing?
- are repeated arrivals exogenous/continual or merely many pre-existing tasks?
- are target states local/uncertain or effectively global/external?
- is capture physical/geometric/PE-like or simply a task label?

S-LIFE-01 should reduce the nine candidates to a minimal 2–5 paper READ set, if needed.

## THEN — MASTER lifecycle merge

Freeze whether the lifecycle gap is DEAD / PARTIALLY SURVIVES / STRONGLY SURVIVES and update the nearest-neighbor table.

## AFTERWARD — R-LM-02

P0036, P0040 remain queued to close physical-action/sim-to-real and strategic/self-play boundaries.

## Only after those steps

Decide whether to open a final CoCap-specific bridge search on:
- local/belief-aware coalition capturability;
- state-dependent coalition size and join/leave;
- constrained-communication target allocation;
- repeated-arrival persistent coverage↔capture.
