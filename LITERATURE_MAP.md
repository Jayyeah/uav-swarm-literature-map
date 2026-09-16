# LITERATURE MAP v0.9

> MASTER state after first SEARCH + SCREEN waves, completed R-PE-01 / R-LM-01 / R-CE-01 / R-LIFE-01 READ batches, and the closed FS-LIFE-01 → S-LIFE-01 lifecycle branch. Detailed evidence remains in `notes/reading/`, `notes/synthesis/`, and search/screening handoffs. Evidence labels: `[原文]`, `[Web核验]`, `[AI判断]`.

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

Concurrent persistence is old. Lifecycle novelty, if any, must be tied to how the same resource pool is reallocated and restored after terminal completion.

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

- **P0042 — strongest direct learning/allocation-method competitor:** learned target preference + hard capacity-constrained assignment + subgroup-conditioned pursuit + spatial multi-agent capture.
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

with marginal recruitment value

`Δ_i(S,j)=C(S∪{i},j)-C(S,j)`.

This is a design hypothesis, not yet an established contribution.

---

# 5. Lifecycle / Persistent Mission Bridge

**Focused SEARCH status:** `SATURATED / CLOSED` after FS-LIFE-01. Do not reopen broad lifecycle SEARCH by default.

**SCREEN status:** S-LIFE-01 completed 2026-09-16.

**READ status:** R-LIFE-01 completed 2026-09-16.

READ anchors: P0043, P0044, P0046, P0048.

## 5.1 Lifecycle novelty boundary v1

[AI判断] **PARTIALLY SURVIVES — coupling-level only.**

R-LIFE-01 confirms that essentially every isolated lifecycle transition already has a precedent:

- **P0043:** completion → explicit coalition dissolution → return to a reusable uncommitted pool → pop-up replacement targets;
- **P0044:** true capture/immobilization → dynamic SWAT coalition → same capture resources reassigned to another target/defense task, with hardware evidence;
- **P0046:** successful apprehension followed by role-appropriate post-success behavior including `resume patrolling` at policy/workflow level;
- **P0048:** one homogeneous pool executes persistent patrol → local pursuit subgroup → same-agent Patrol restoration → repeated intruders, but no terminal capture.

Therefore standalone novelty is dead for:
- post-capture/apprehension return to patrol;
- completion-triggered coalition dissolution;
- released resources becoming reusable;
- post-capture resource reassignment;
- same-agent patrol → pursuit/response → patrol;
- repeated target/intruder arrivals;
- dynamic capture coalitions in a persistent mixed mission;
- adaptive subgroup cardinality in a broad sense;
- local target detection triggering temporary response;
- persistent coverage/patrol + pursuit as an isolated system combination.

## 5.2 The four READ papers form an edge cover

### P0043 — strongest release/reuse/repeat analogue

Temporary type-constrained coalitions conduct synchronized strike. The paper literally states that after strike the coalition dissolves and each UAV returns to `uncommitted`; destroyed targets are replaced by pop-up targets.

Mandatory distinction:

`completion → uncommitted reusable pool`
≠
`completion → nominal coverage restored`.

The terminal event is strike/destruction, not PE capture.

### P0044 — strongest lifecycle / overall system-level competitor

KS-COAL integrates:
- SCOUT coverage/exploration;
- online target discovery;
- dynamic SWAT capture coalitions;
- moving evasive targets;
- Apollonius-based pursuit;
- positive-radius capture causing target immobilization;
- event-triggered re-coordination;
- hardware post-capture reuse.

Hardware shows the same SWAT resources capture one target, switch to another, and then return to resource encirclement/defense.

This kills broad claims about:
- first dynamic capture coalition;
- first post-capture resource reuse;
- first capture agents switching to another mission task.

Its decisive CoCap difference is **fixed SCOUT/SWAT capability pools**:

`SCOUT continues exploration`
+
`SWAT cycles among capture / defense`

rather than:

`same coverage agent → temporarily borrowed into capture → same agent restores coverage`.

Also:

`K-serial allocation stability ≠ current-state physical capturability certificate`.

P0044 allows utility-induced changing SWAT cardinality, so CoCap cannot claim adaptive coalition size alone. The remaining method-level opportunity is **capturability-conditioned adaptive cardinality**.

### P0046 — historical patrol-successor correction

The Navy-pier exercise truly reaches successful apprehension. The paper then states that after apprehension each robot starts an appropriate successor task, with examples including `return to base` or `resume patrolling`.

Safe statement:

> post-apprehension patrol resumption has a historical policy/workflow precedent.

Unsafe statement:

> P0046 quantitatively demonstrates the same capturer restoring patrol/coverage.

No identity-traced restoration metric or repeated intruder loop is shown.

### P0048 — closest same-pool lifecycle near miss

P0048 already has:

`one homogeneous pool`
→ `persistent patrol/coverage`
→ `local camera detection`
→ `local neighbor alert`
→ `temporary pursuit subgroup`
→ `excess pursuers leave`
→ `same agents return to Patrol`
→ `44 repeated crossings over 24 h`.

Nonparticipants keep patrolling.

The decisive missing edge is **terminal capture**: return is loss/timeout driven, not capture-completion driven.

If a genuine terminal capture replaced that trigger, the lifecycle state-machine skeleton would be very close to CoCap. What would still remain methodologically distinct is capturability-aware recruitment, target-wise resource conflict/assignment, and uncertainty-aware capture feasibility.

## 5.3 Same-pool lifecycle audit

Exact question:

> Are the agents maintaining nominal coverage/search the same fungible resources temporarily borrowed into a capture coalition and then, after terminal capture, released back into nominal coverage for later arrivals?

READ result:
- P0043: reusable yes; nominal coverage no; PE capture no.
- P0044: true capture and reuse yes; same exploration/capture pool no.
- P0046: apprehension and patrol successor yes; autonomous same-agent/repeated loop unproven.
- P0048: same pool + coverage + return + repeat yes; terminal capture no.

[AI判断] **No exact closure among the four READ papers.** Combined with the saturated focused branch, the exact integrated loop remains unfound. This is a bounded literature-search conclusion, not a theorem that no prior work exists.

## 5.4 Strongest competitors after R-LIFE-01

- **Strongest lifecycle / overall system-level competitor: P0044 KS-COAL.**
- **Closest same-pool lifecycle architecture: P0048 Duarte et al.**
- **Strongest direct learning/allocation-method competitor: P0042 Yang et al.**
- **Strongest local-information learning competitor: P0034 Peng et al.**

P0044 is now more important than P0042 for the **overall novelty boundary**, while P0042 remains more important for the **learned allocation/control mechanism** comparison.

## 5.5 Lifecycle SEARCH stays closed

No R-LIFE-01 paper exposed a citation chain that plausibly closes the exact remaining same-pool terminal-capture/restoration intersection.

Record-only named precision chain from P0046:
- Johnson et al., ICRA 2008 — *Human-robot coordination through dynamic regulation*;
- Johnson et al., DHMS 2008 — *Coordinated operations in mixed teams of humans and robots*.

Do not reopen lifecycle SEARCH unless final historical wording requires identity-level proof of patrol resumption.

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
- adaptive capture subgroup size in the broad sense;
- meaningful geometric multi-agent capture;
- no-escape/capture geometry;
- encirclement→physical interception;
- concurrent monitoring/scouting during pursuit;
- task completion→coalition dissolution;
- post-apprehension return to patrol;
- post-capture resource reassignment;
- continual/repeated target arrivals;
- released-resource reuse;
- same-agent patrol→response/pursuit→patrol cycling;
- persistent coverage/patrol + pursuit by itself;
- real-UAV pursuit;
- continuous/physical actions;
- self-play or game geometry + RL by itself.

## 6.2 What survives after R-LIFE-01

Capturability by itself is old.

Local sensing by itself is old.

Lifecycle transitions by themselves are old.

[AI判断] The strongest remaining candidate is the **information + capturability + lifecycle coupling**:

`persistent coverage by one fungible swarm`
→ `execution-time local/intermittent target belief`
→ `estimate current coalition capture feasibility`
→ `state-dependent support join/leave and adaptive coalition size`
→ `target-wise resource-feasible assignment`
→ `borrow agents only when marginal capture value justifies coverage opportunity cost`
→ `terminal physically meaningful capture`
→ `explicit release`
→ `same agents restore nominal coverage`
→ `repeat under later arrivals`.

Recommended non-`first` novelty wording v1:

> **CoCap addresses a persistent same-pool coverage–capture coordination problem in which UAVs operating under local/intermittent target information are temporarily recruited from nominal coverage according to capture-feasibility and mission opportunity cost, execute terminal capture, and are explicitly released back to restore coverage for subsequent target arrivals. The candidate novelty lies in coupling local information, coalition capturability and lifecycle-aware resource reuse, rather than in coverage, capture, coalition formation or post-capture return individually.**

Shorter method-facing wording:

> **A fungible UAV swarm dynamically borrows agents from persistent coverage only when they improve target capturability, then releases the same agents after confirmed capture to recover coverage under repeated target arrivals.**

This remains a **candidate novelty**, not a universal priority claim.

## 6.3 Risk of collapsing into systems integration

If the final method is only:

`enemy detected → send K agents → capture → switch them back to coverage`,

then P0044 + P0048 already cover most of the lifecycle structure and the contribution risks being judged as implementation integration.

To support a stronger method claim, lifecycle/resource coupling should enter the decision rule through at least some of:
- `C(S,j)` or equivalent capture-feasibility score;
- marginal support gain `Δ_i`;
- coverage opportunity cost / coverage debt;
- state-dependent/adaptive target capacity;
- explicit terminal capture/release confidence;
- target-wise resource constraints.

A natural abstraction is:

`U_i(S,j)=Δ_i(S,j)-λ·CoverageCost(i)`

or an equivalent constrained formulation.

## 6.4 Evaluation implications from R-LIFE-01

Coverage restoration must be measured, not narrated.

Recommended lifecycle metrics:
1. pre-event nominal coverage baseline;
2. peak event-conditioned coverage deficit;
3. integrated coverage debt;
4. borrowed-agent cost / agent-seconds removed from coverage;
5. terminal capture → release latency;
6. release → coverage-recovery time;
7. recovered steady-state coverage ratio;
8. nonparticipant coverage continuity during capture;
9. repeated-arrival degradation as arrival frequency rises;
10. recovery-before-next-event rate;
11. long-horizon occupancy of coverage/support/capture/recovery modes.

At least one benchmark should be long-horizon rather than one-shot:

`coverage → arrival → capture → release → recovery → next arrival → ...`

with inter-arrival times varied across fully recovered, overlapping-recovery and sustained-load regimes.

---

# 7. Immediate Work Plan

## NEXT — R-LM-02

Deep-read:
- P0036 — unknown-environment / CTBR / real-UAV deployment boundary;
- P0040 — strategic self-play / real-UAV frontier.

Purpose:
- close physical-action / sim-to-real / real-UAV claims;
- close strategic-opponent / self-play claims;
- test whether either materially changes the current **information + capturability + lifecycle** candidate narrative.

## After R-LM-02

MASTER should assess whether the first literature-map phase is sufficiently closed to produce a consolidated CoCap novelty/method-design memo.

Only open a final focused bridge READ/search if it is directly required by the chosen method claim, especially:
- P0037 if learned/theory-guided `C(S,j)` becomes central;
- P0020 if obstacle-modified capturability becomes central;
- P0026/P0029 if final claims require 3-D/nonholonomic/higher-order capture certificates.

Do not reopen broad SEARCH by default.
