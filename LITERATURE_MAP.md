# LITERATURE MAP v1.0

> MASTER first-stage closure after R-PE-01, R-LM-01, R-CE-01, FS-LIFE-01 → S-LIFE-01 → R-LIFE-01, and R-LM-02. Detailed evidence remains in `notes/reading/`, `notes/synthesis/`, and search/screening handoffs. Evidence labels: `[原文]`, `[Web核验]`, `[AI判断]`.

## Map conventions

Coverage status: `UNSEARCHED / ACTIVE / PARTIAL / SATURATED`.
Screening decisions: `MUST READ / MAP / ARCHIVE`.
A `MUST READ` paper is not automatically in the immediate READ queue; `READING_LEDGER.md` controls timing.

---

# 1. Project-level closure status

**First-stage CoCap-near literature map: BASICALLY CLOSED.**

Closed strongly enough for method design and novelty positioning:
- reach-avoid / capturability / coalition-feasibility / assignment theory;
- classical sensing, decentralization, persistence and encirclement→interception;
- closest learning competitors on local sensing, multi-target scale, allocation and subgroup control;
- lifecycle release/reuse/return/repeated-arrival boundary;
- physical-action / sim-to-real / real-UAV boundary;
- strategic learned-opponent / self-play boundary.

No new broad SEARCH is recommended.

Remaining work is **claim-triggered only**, not another literature wave.

---

# 2. Multi-Agent / UAV Swarm Foundations

These background branches remain intentionally underdeveloped because the project is problem-boundary driven rather than a general swarm-control survey.

- distributed control & consensus — `UNSEARCHED`
- formation / flocking — `UNSEARCHED`
- coverage / Voronoi / Lloyd — `UNSEARCHED`
- communication topology — `UNSEARCHED`
- generic MRTA / coalition formation — only CoCap-relevant slices searched
- collision avoidance / CBF / MPC — only encirclement/pursuit-relevant slices searched

Do not expand these unless a final method claim directly depends on them.

---

# 3. Classical Encirclement / Enclosing

**Coverage:** PARTIAL-to-strong on CoCap-relevant sensing, decentralization, persistence and interception after R-CE-01.

## 3.1 Geometric enclosing is mature and is not PE capture

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

P0003's `target-capturing` is a lexical false friend: it is a target-centered enclosing/tracking formation, not forced capture.

## 3.2 Distributed is not the same as partial observation

READ anchors: P0008, P0010, P0012.

Distinguish:
1. computation/decision decentralization;
2. raw measurement locality;
3. communication topology;
4. reconstructed target/global state;
5. residual uncertainty in each agent's decision-time belief.

P0008 is the canonical counterexample: decentralized computation reconstructs globally relevant target/frame quantities. P0012 similarly begins with local noisy ranges but filters them into target state before control.

## 3.3 Sensing ladder

1. direct local relative measurement;
2. finite range/FOV constraint;
3. actual intermittent loss/occlusion;
4. distributed/filtered global-state reconstruction;
5. unresolved local belief/uncertainty retained at decision time.

P0004/P0009 occupy level 2; P0034 demonstrates real loss/occlusion/reacquisition; P0008/P0012 show reconstruction. CoCap cannot claim novelty from local sensing/FOV/range-only sensing alone.

## 3.4 Persistence and physical interception are already classical capabilities

P0010 shows concurrent known-target encirclement + monitoring/safety optimization.

Therefore:

`monitoring/patrol + encirclement ≠ post-capture recovery`.

P0012 shows noisy range sensing → target estimation → encirclement → radius contraction → real-UAV direct-impact interception.

Therefore the claim “classical encirclement cannot transition to real interception” is false.

P0012 and P0028 are complementary:
- P0012: perception/control → physical interception;
- P0028: game geometry → no-escape / strategy-robust capture conditions.

---

# 4. Pursuit–Evasion Foundations

**Coverage:** STRONG first CoCap-relevant theory skeleton after R-PE-01; not globally saturated.

## 4.1 Reach-avoid semantics

READ anchor: P0019.

`reachable set ≠ reach-avoid set ≠ dominance region ≠ generic capture region`.

Reach-avoid is strategy-quantified: reach the target while respecting avoid/state constraints. Its value is useful to CoCap as a possible oracle/teacher for feasibility or escape margin, not as a direct many-UAV online solver.

## 4.2 Capturability certificate → assignment

READ anchors: P0024, P0025.

Confirmed abstraction:

`capturability certificate`
→ `feasible edge/hyperedge`
→ `resource-constrained assignment`.

P0024:
`pairwise HJI outcome → bipartite feasible edge → maximum matching`.
A matching of size `m` gives a conservative stopped-attacker guarantee, not an exact full multiplayer solution.

P0025:
`coalition winning certificate → coalition-target feasible hyperedge → constrained assignment`.
Within its model assumptions, assignment maximizes guaranteed intercepted evaders.

## 4.3 Encirclement → capture requires more than a ring

READ anchor: P0028.

Confirmed chain:

`speed-aware escape-gap closure`
→ `maintain closure`
→ `radial/inward contraction`
→ `positive capture radius`
→ `capture`.

Therefore:

`ring formation ≠ no-escape enclosure ≠ actual capture`.

## 4.4 Deferred theory extensions

Claim-triggered only:
- P0020 — obstacle-modified strategic dominance geometry;
- P0026 — 3-D heterogeneous multiplayer reach-avoid + matching;
- P0029 — nonholonomic/homicidal-chauffeur reach-avoid + pursuit enclosure functions.

---

# 5. Learning-Based Pursuit / Encirclement

**Coverage:** STRONG around current CoCap nearest-neighbor axes after R-LM-01 + R-LM-02.

Organize learning work by **which classical assumption/system layer is relaxed**, not by backbone name.

## 5.1 Strongest current competitors by axis

- **P0044 — strongest overall / lifecycle system-level competitor.** Persistent exploration + dynamic capture coalitions + real immobilizing capture + defense + post-capture resource reuse + hardware; decisive difference is fixed SCOUT/SWAT pools rather than one fungible coverage↔capture pool.
- **P0042 — strongest direct learning/allocation-method competitor.** Learned target preference + hard capacity assignment + subgroup-conditioned control + spatial capture; capacity is prescribed/resource-feasible, not current-state capturability-feasible.
- **P0034 — strongest local-information learning competitor.** Literal finite FOV/range/building occlusion + target loss/reacquisition; detected target coordinates then become team-wide.
- **P0035 — strongest Transformer/scaling competitor.** Multi-target entity processing + soft target selection + large count transfer; active targets are globally available.
- **P0036 — strongest CoCap-relevant multi-UAV physical-deployment competitor.** CTBR, calibrated 6-DOF dynamics, obstacle scenarios and three real pursuers; mocap/offboard inference/virtual target caveat.
- **P0040 — strongest strategic-opponent competitor.** Bilateral self-play → FSP → PFSP, historical policy pools, onboard inference and physical learned opponent; currently preprint/under review.
- **P0048 — closest same-pool lifecycle architecture near miss.** Homogeneous persistent patrol → local pursuit → same-agent patrol restoration → repeated intruders, but no terminal capture.
- **P0033 — fixed-role exploration+pursuit predecessor.** Important against broad “search + pursuit” claims, but no fungible role switching or constrained allocation.

## 5.2 Selection, assignment, recruitment and capturability are different

Mandatory distinction:

`target preference/selection`
≠ `explicit resource-feasible assignment`
≠ `dynamic coalition/support recruitment`
≠ `capturability-aware recruitment`.

P0042 is the closest learned analogue to a classical assignment pipeline, but its target capacity is prescribed rather than inferred from current-state capture feasibility.

P0044 allows utility-driven adaptive coalition cardinality, so **adaptive coalition size alone is not novel**. Its K-serial stability concerns allocation utility/stability, not a strategy-quantified current-state capture guarantee.

## 5.3 Theory-guided learning bridge

READ-confirmed theory:

`P0019 reach-avoid semantics`
→ `P0024 pairwise certificate + matching`
→ `P0025 coalition certificate + assignment`.

Closest learned structure:

`P0042 learned preference`
→ `fixed-capacity assignment`
→ `assignment-conditioned control`
→ `terminal spatial capture test`.

Leading CoCap design hypothesis:

`C(S,j)=P(capture target j | coalition S, belief/state, dynamics, obstacles)`

with marginal recruitment value

`Δ_i(S,j)=C(S∪{i},j)-C(S,j)`.

This is a **design hypothesis**, not an established novelty claim.

P0037 is claim-triggered: inspect it only if `C(S,j)` or a direct theory→RL bridge becomes method-central.

---

# 6. Lifecycle / Persistent Mission Bridge

**SEARCH:** `SATURATED / CLOSED` after FS-LIFE-01.

**SCREEN:** S-LIFE-01 completed.

**READ:** R-LIFE-01 completed.

READ anchors: P0043, P0044, P0046, P0048.

## 6.1 Lifecycle novelty boundary v1

**PARTIALLY SURVIVES — coupling-level only.**

Nearly every isolated lifecycle primitive has precedent:
- P0043: completion → explicit coalition dissolution → reusable pool → replacement targets;
- P0044: true capture → dynamic coalition → same capture resources reused/reassigned, including hardware;
- P0046: post-apprehension successor behavior can include `resume patrolling`;
- P0048: one homogeneous pool executes patrol → local pursuit subgroup → same-agent Patrol restoration → repeated intruders.

Therefore standalone novelty is dead for:
- post-capture/apprehension return to patrol;
- completion-triggered coalition dissolution;
- released-resource reuse;
- post-capture reassignment;
- same-agent patrol→pursuit→patrol;
- repeated arrivals;
- dynamic capture coalitions in a persistent mission;
- adaptive subgroup cardinality broadly;
- local detection triggering temporary response;
- persistent coverage/patrol + pursuit by itself.

## 6.2 Same-pool audit

Exact question:

> Are nominal coverage/search agents the **same fungible resources** temporarily borrowed into a capture coalition and, after terminal capture, released back to nominal coverage for later arrivals?

READ result:
- P0043: reusable yes; nominal coverage no; PE capture no.
- P0044: true capture/reuse yes; same exploration/capture pool no.
- P0046: apprehension + patrol successor yes; autonomous same-agent/repeated restoration unproven.
- P0048: same pool + coverage + return + repeat yes; terminal capture no.

**No exact closure was found in the closed lifecycle branch.** This is a bounded search conclusion, not a universal proof of nonexistence.

## 6.3 Lifecycle distinctions that must remain canonical

1. `reusable uncommitted pool ≠ nominal-task restoration`.
2. `post-capture reassignment ≠ same-agent return to coverage`.
3. `policy-level patrol successor ≠ quantitatively demonstrated coverage recovery`.
4. `task-allocation stability ≠ current-state capturability`.
5. `loss/timeout-triggered patrol return ≠ terminal-capture-triggered release`.
6. `behavioral pursuit subgroup ≠ explicit capture coalition`.
7. `fixed heterogeneous role pools ≠ fungible coverage↔capture resource pool`.

Lifecycle SEARCH stays closed by default.

---

# 7. Physical Deployment Boundary v1

READ anchors: P0036, P0040.

## 7.1 Deployment realism ladder

1. kinematic simulation;
2. vehicle-dynamic simulation;
3. noisy/delayed sensing + actuator abstraction;
4. SITL/HITL;
5. external-localization real UAV;
6. onboard-perception real UAV.

Current anchors:
- **P0036:** Level 5 variant — three physical pursuers, calibrated 6-DOF dynamics and CTBR, but external mocap + offboard actor/EPN + virtual evader.
- **P0040:** Level 5 variant — external mocap + onboard inference + physical learned opponent; 1v1, obstacle-free reported hardware, qualitative evidence.
- **Neither reaches Level 6.**

## 7.2 Boundary statement

Learned UAV pursuit already occupies:
- real-UAV execution;
- broad zero-shot sim-to-real;
- direct CTBR control;
- calibrated vehicle dynamics;
- trajectory-prediction-assisted pursuit;
- unseen/variable-clutter pursuit in the broad layout-generalization sense.

Therefore do **not** use these as standalone CoCap novelty claims.

The stronger unclosed deployment frontier is full onboard sensing→decision→control without external target/localization infrastructure.

If CoCap remains simulation-only, say so explicitly. The most valuable simulation-only realism upgrade is Level-3-style delay/noise/dynamics perturbation, not superficial deployment language.

---

# 8. Strategic-Opponent Boundary v1

READ anchor: P0040; supporting comparisons P0034/P0033/P0036.

## 8.1 Opponent realism ladder

1. fixed scripted evader;
2. randomized/reactive heuristic distribution;
3. separately trained learned evader;
4. current-policy self-play;
5. historical/population self-play (FSP/PFSP);
6. unseen-policy generalization / exploitability-oriented evaluation.

Placement:
- P0036: Level 2 at best;
- P0034: Level 3 in evaluation via separately trained DDPG evader;
- P0033: learned competitors but no historical population machinery;
- **P0040: Level 5 training frontier**.

P0040 shows current self-play, historical policy pools, FSP and failure-prioritized PFSP. It does **not** show low exploitability, Nash convergence, or robustness to independently trained unseen learned policies.

Therefore standalone novelty is dead/occupied for:
- learned strategic evader;
- self-play pursuit;
- historical-policy/FSP/PFSP pursuit.

If strategic robustness is not CoCap's headline, a reasonable minimum is randomized heuristics + at least one separately trained learned evader, with a held-out learned policy in evaluation. A single deterministic scripted evader is now an avoidable weakness.

---

# 9. Current CoCap Novelty Boundary v1

## 9.1 Standalone claims that are no longer defensible

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
- adaptive capture subgroup size broadly;
- meaningful geometric multi-agent capture;
- no-escape/capture geometry;
- encirclement→physical interception;
- concurrent monitoring/scouting during pursuit;
- task completion→coalition dissolution;
- post-apprehension return to patrol;
- post-capture resource reassignment;
- repeated target arrivals;
- released-resource reuse;
- same-agent patrol→response/pursuit→patrol cycling;
- persistent coverage/patrol + pursuit by itself;
- real-UAV pursuit;
- zero-shot sim-to-real pursuit broadly;
- continuous/physical/CTBR control;
- trajectory-prediction-assisted pursuit;
- unknown/unseen-clutter pursuit broadly;
- learned strategic evaders;
- self-play pursuit;
- historical-policy/FSP/PFSP pursuit;
- game geometry + RL by itself.

## 9.2 Strongest surviving candidate

Capturability by itself is old.

Local sensing by itself is old.

Lifecycle by itself is old.

Physical realism by itself is old.

Self-play by itself is old.

The strongest remaining candidate is the **information + capturability + lifecycle coupling**:

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

Recommended non-`first` novelty wording:

> **CoCap addresses a persistent same-pool coverage–capture coordination problem in which UAVs operating under local/intermittent target information are temporarily recruited from nominal coverage according to capture-feasibility and mission opportunity cost, execute terminal capture, and are explicitly released back to restore coverage for subsequent target arrivals. The candidate novelty lies in coupling local information, coalition capturability and lifecycle-aware resource reuse, rather than in sensing, physical control, self-play, capture, coalition formation or post-capture return individually.**

Short method-facing wording:

> **A fungible UAV swarm borrows agents from persistent coverage only when their marginal contribution improves target capturability enough to justify coverage cost, then releases the same agents after confirmed capture to recover coverage under repeated arrivals.**

This remains a **candidate novelty**, not a universal priority claim.

## 9.3 Risk of collapsing into systems integration

If the final method is only:

`enemy detected → send K agents → capture → switch them back to coverage`,

then P0044 + P0048 already cover most lifecycle structure and the contribution risks looking like systems integration.

To support a stronger method claim, put the coupling into the decision rule through at least some of:
- `C(S,j)` or equivalent capture-feasibility score;
- marginal support value `Δ_i`;
- coverage opportunity cost / coverage debt;
- adaptive target capacity;
- target-wise resource constraints;
- explicit capture-confidence / release criterion.

A natural abstraction is:

`U_i(S,j)=Δ_i(S,j)-λ·CoverageCost(i)`

or an equivalent constrained formulation.

---

# 10. Evaluation Implications

## 10.1 Lifecycle metrics

Coverage restoration must be measured, not narrated.

Track at minimum:
1. pre-event nominal coverage baseline;
2. peak event-conditioned coverage deficit;
3. integrated coverage debt;
4. borrowed-agent cost / agent-seconds removed from coverage;
5. capture→release latency;
6. release→coverage-recovery time;
7. recovered steady-state coverage ratio;
8. nonparticipant coverage continuity during capture;
9. repeated-arrival degradation as arrival frequency rises;
10. recovery-before-next-event rate;
11. long-horizon occupancy of coverage/support/capture/recovery modes.

At least one long-horizon benchmark should use:

`coverage → arrival → capture → release → recovery → next arrival → ...`

with inter-arrival time varied across recovered, overlapping-recovery and sustained-load regimes.

## 10.2 Opponent robustness

If strategic robustness is not headline novelty:
- randomized/reactive heuristic diversity;
- at least one separately trained learned evader;
- preferably a held-out learned policy not used for pursuer training.

If strategic robustness becomes a claim:
- historical/population training or comparably diverse training;
- unseen-policy cross-evaluation;
- avoid equilibrium language without exploitability/best-response evidence.

## 10.3 Deployment realism

If simulation-only:
- state the action/dynamics model as mission-level abstraction unless vehicle dynamics are truly represented;
- do not imply sim-to-real/onboard autonomy;
- if feasible add actuator lag/noise, observation delay/dropout, parameter randomization and strict rate/acceleration constraints.

---

# 11. Claim-Triggered Future READ Gates

Do **not** promote automatically.

- **P0037** — READ if `C(S,j)` / theory-guided capturability becomes a concrete central method claim.
- **P0020** — READ if obstacle-modified capture feasibility becomes central.
- **P0026** — READ if 3-D heterogeneous coalition certificates are needed for a formal claim.
- **P0029** — READ if nonholonomic/higher-order pursuit-enclosure certificates become central.
- **P0032** — READ only if historical decentralized-pursuit genealogy becomes necessary in writing.
- **P0018** — READ only if computational HJI machinery itself becomes method-relevant.
- unseen-opponent/exploitability literature — only if strategic robustness becomes a contribution.

---

# 12. Immediate Work Plan

## NEXT — MASTER CoCap Novelty & Method Design Memo v1

Synthesize the closed first-stage map into a project-facing memo fixing:
- strongest competitors by axis;
- dead vs surviving claims;
- exact non-`first` novelty wording;
- method hypothesis around `C(S,j)`, `Δ_i`, coverage opportunity cost and release semantics;
- minimum baseline/ablation/evaluation matrix;
- which current CoCap implementation choices are structurally aligned or misaligned with the literature-derived problem definition;
- claim-triggered future READ gates.

Do not launch another paper wave before this consolidation.
