# LITERATURE MAP v0.8

> MASTER state after first SEARCH + SCREEN waves, completed R-PE-01 / R-LM-01 / R-CE-01 READ batches, FS-LIFE-01 focused SEARCH, and S-LIFE-01 focused SCREEN. Detailed evidence remains in `notes/reading/`, `notes/synthesis/`, and search/screening handoffs. Evidence labels: `[原文]`, `[Web核验]`, `[AI判断]`.

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

P0004/P0009 occupy level 2; P0034 occupies true loss/occlusion/reacquisition; P0008/P0012 show reconstruction. CoCap can no longer claim novelty from local sensing/FOV/range-only sensing alone.

## 2.4 Persistence already exists, but task-completion recovery is different

READ anchor: P0010.

P0010 proves that distributed classical optimization can concurrently maintain known-target encirclement, fixed-spot monitoring and safety objectives.

Therefore:

`monitoring/patrol + encirclement ≠ post-capture recovery`.

Concurrent persistence is old. Lifecycle novelty, if any, must be tied to completion-triggered resource cycling rather than simultaneous objectives.

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

**Focused SEARCH status:** `SATURATED` at first-pass depth. FS-LIFE-01 is closed; reopen only through a named citation chain exposed by READ.

**SCREEN status:** S-LIFE-01 completed 2026-09-16.

Canonical lifecycle candidates: P0043–P0051.

## 5.1 Lifecycle gap judgment after SCREEN

[AI判断] **PARTIALLY SURVIVES.**

S-LIFE-01 verifies that nearly every isolated lifecycle edge already has an antecedent:

- **P0046:** successful apprehension followed by post-success behavior including `resume patrolling`;
- **P0043:** completion-triggered temporary coalition dissolution, return to a reusable uncommitted pool, and replacement/pop-up targets;
- **P0044:** true capture/immobilization followed by continued reuse/reassignment of the capturing SWAT pool;
- **P0048:** same homogeneous agents execute patrol → local temporary pursuit → patrol recovery under repeated intruders;
- **P0050:** persistent patrol under repeated Poisson alert arrivals;
- **P0051:** online true capture/defense against arbitrary-time repeated intruders.

Therefore standalone novelty is dead for:
- post-capture/apprehension return to patrol;
- completion-triggered coalition dissolution;
- reusable released resources;
- repeated target/threat arrivals;
- same-agent patrol → response/pursuit → patrol cycles;
- capture followed by continued resource reassignment.

## 5.2 Strongest lifecycle competitors after SCREEN

### P0043 — strongest explicit completion→dissolve→reuse→repeat analogue

A temporary combat coalition conducts synchronized strike; the coalition explicitly dissolves and UAVs return to `uncommitted`; destroyed targets are replaced by pop-up targets. The key distinction is semantic: `uncommitted` performs sneak-like movement and is **not** nominal area coverage/search.

### P0044 — strongest capture-specific lifecycle competitor

KS-COAL uses fixed SCOUT/SWAT capability roles. SWAT robots form dynamic task-specific capture coalitions, captured targets become immobile, and hardware scenarios show the same SWAT resources subsequently capturing another target or returning to resource encirclement/defense. It is the strongest threat to broad claims about dynamic capture coalitions and post-capture resource reuse. Its decisive difference from CoCap is that exploration and capture are assigned to fixed heterogeneous role pools rather than one fungible coverage↔capture swarm.

### P0046 — cleanest post-apprehension return-to-patrol predecessor

The field exercise reports successful apprehension and policy-level post-success tasks including `resume patrolling`. This kills any claim of being first to return to patrol after apprehension, even though the transition is human/policy-mediated rather than an autonomous distributed coalition lifecycle.

### P0048 — closest same-pool persistent-loop near miss

The same homogeneous aquatic-drone swarm maintains patrol, locally detects intruders, temporarily recruits pursuers, lets excess pursuers drop out, returns the same agents to `Patrol`, and experiences repeated intruder crossings. Its missing edge is decisive: pursuit ends on target exit/loss/timeout rather than terminal capture.

## 5.3 Important negative controls

- **P0045 HECTOR — MAP:** generic subtask completion → coalition dissolution → reassignment under continual arrivals is established, but generic reassignment is not return-to-coverage and its `capture` semantics are not PE/immobilizing capture.
- **P0047 — MAP:** same-agent patrol → alert response → patrol is old, but no terminal capture or temporary coalition.
- **P0049 — ARCHIVE:** `Capture` is a state-name false friend; prototype capturers remain with the intruder rather than being released.
- **P0050 — MAP:** repeated-alert patrol/service lineage, not capture.
- **P0051 — MAP:** repeated online true capture with fixed defenders, not a temporary coalition-release lifecycle.

## 5.4 Integrated lifecycle gap that survives

No screened paper closes the full same-resource-pool loop:

`persistent area coverage/search by one fungible swarm`
→ `target-triggered temporary capture coalition`
→ `terminal capture/completion`
→ `completion-triggered coalition/resource release`
→ `the same agents restore nominal area coverage/search`
→ `repeat under changing/new arrivals`.

The remaining lifecycle candidate is therefore **integration**, not an isolated transition.

When coupled with the earlier PE and learning results, the stronger candidate becomes:

`persistent coverage/search by one fungible swarm`
→ `genuinely local/intermittent target belief, not immediately globally reconstructed`
→ `uncertainty-aware coalition capturability C(S,j)`
→ `state-dependent support join/leave and adaptive coalition size`
→ `target-wise resource-feasible assignment`
→ `no-escape / physically meaningful capture`
→ `nonparticipants maintain coverage`
→ `terminal capture releases the same agents`
→ `released agents restore nominal coverage`
→ `repeat under new arrivals`.

This remains a **candidate novelty**, not a frozen paper claim, until R-LIFE-01 deep READ closes the four strongest lifecycle predecessors.

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
- patrol→response/pursuit→patrol cycling;
- real-UAV pursuit;
- continuous/physical actions;
- self-play or game geometry + RL by itself.

## 6.2 Surviving candidate gap after S-LIFE-01

[AI判断] The most defensible current candidate is the **information + capturability + lifecycle coupling**:

> learn and use capture-feasibility structure under unresolved local target uncertainty to dynamically borrow agents from a persistent coverage swarm, execute meaningful capture, and release those same agents back to coverage so one fungible resource pool repeatedly cycles between coverage and capture.

This wording is intentionally narrower than “first dynamic coalition,” “first post-capture recovery,” or “first repeated pursuit.”

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

## NEXT — R-LIFE-01 lifecycle closure READ

Deep-read only:
- P0043;
- P0044;
- P0046;
- P0048.

Purpose: freeze the lifecycle novelty boundary with paper-internal evidence on resource fungibility, capture/completion semantics, exact post-completion robot fate, coverage/patrol restoration, repeated arrivals, sensing/communication assumptions and autonomy.

## THEN — MASTER lifecycle synthesis

Freeze `Lifecycle novelty boundary v1` and decide whether any named citation chain justifies reopening lifecycle SEARCH. Default is **do not reopen**.

## AFTERWARD — R-LM-02

P0036 and P0040 remain queued to close:
- physical-action / sim-to-real / real-UAV boundary;
- strategic-opponent / self-play boundary.

## Only after those steps

Decide whether a final focused bridge READ/search is needed around:
- P0037 / theory-guided MARL if `C(S,j)` becomes a central method claim;
- local/belief-aware coalition capturability;
- state-dependent coalition size and constrained communication;
- 3D/nonholonomic certificate extensions if required by final method narrative.
