# MASTER — CoCap Novelty & Method Design Memo v1

Date: 2026-09-16

Status: first-stage literature-map consolidation after R-PE-01, R-LM-01, R-CE-01, R-LIFE-01 and R-LM-02.

This memo is project-facing synthesis. It is not a claim that the literature is globally exhaustive. It records what is supportable after the closed first-stage search/screen/read program in `Jayyeah/uav-swarm-literature-map`.

Evidence discipline:
- `[原文]` — direct paper evidence already recorded in reading notes;
- `[Web核验]` — publication/version/code verification;
- `[AI判断]` — project synthesis or method implication.

---

# 1. Executive position

[AI判断] CoCap should no longer be narrated as a paper whose novelty is any single one of:

- local sensing;
- limited FOV;
- multi-target pursuit;
- Transformer attention;
- target selection;
- dynamic coalition formation;
- capture-aware assignment in the broad sense;
- physical/geometric capture;
- post-capture return;
- repeated arrivals;
- continuous UAV control;
- sim-to-real;
- self-play.

All of these have meaningful antecedents.

The strongest remaining candidate is instead a **coupled decision problem**:

> **persistent same-pool coverage ↔ capture coordination under unresolved local/intermittent target information, where temporary capture resources are recruited according to current coalition capture feasibility and coverage opportunity cost, then explicitly released after terminal capture so the same swarm restores nominal coverage and remains ready for later arrivals.**

Short method-facing form:

> **A fungible UAV swarm borrows agents from persistent coverage only when their marginal contribution improves target capturability enough to justify coverage cost, then releases those same agents after confirmed capture to recover coverage under repeated arrivals.**

This is the current **candidate novelty boundary**, not a universal first-ever claim.

---

# 2. Strongest competitors by axis

| Axis | Strongest current comparator | What it already occupies | Decisive remaining distinction |
|---|---|---|---|
| overall / mission lifecycle | **P0044 KS-COAL** | exploration, dynamic capture coalitions, real immobilizing capture, defense, post-capture reuse, hardware | fixed SCOUT/SWAT pools; no same coverage agent → capture → coverage restoration; KSS ≠ capturability certificate |
| learned allocation/control | **P0042 Yang et al.** | learned preference, hard capacity assignment, subgroup-conditioned learned control, spatial capture | prescribed capacity; no current-state coalition capture-feasibility estimate; externally supported target state |
| local target information | **P0034 Peng et al.** | true finite FOV/range, building occlusion, loss/reacquisition | detected target coordinate becomes team-wide; single target; no persistent lifecycle |
| scaling / Transformer | **P0035 TERL** | variable-cardinality entity processing, multi-target encirclement, large count transfer | active targets globally available; soft selection rather than hard capturability-aware recruitment |
| same-pool lifecycle near miss | **P0048 Duarte et al.** | one homogeneous pool, patrol, local detection, temporary pursuit, same-agent Patrol return, repeated intruders | no terminal capture; return is loss/timeout driven; no target-wise/capturability allocation |
| physical multi-UAV deployment | **P0036 OPEN** | calibrated 6-DOF dynamics, CTBR, obstacles, zero-shot real 3-UAV execution | mocap + offboard inference + virtual evader; no allocation/lifecycle |
| strategic opponent | **P0040 AgilePE** | bilateral learned PE, historical pools, FSP/PFSP, physical learned opponent | 1v1; preprint; no unseen-policy exploitability; no coalition/lifecycle |
| classical capturability→assignment | **P0025 / P0024** | strategy-quantified coalition/pairwise feasibility feeding constrained assignment | clean model assumptions; not learned under unresolved local uncertainty |
| no-escape capture bridge | **P0028** | speed-aware angular closure + maintained contraction → capture | one-target/simple-motion theory; not persistent resource lifecycle |

[AI判断] Final paper positioning should explicitly compare against **both P0044 and P0042**. P0044 is the stronger system/lifecycle threat; P0042 is the stronger learned-allocation-method threat.

---

# 3. DEAD standalone novelty claims

Treat the following as unavailable as standalone contribution statements:

1. local sensing / finite range / FOV;
2. target loss and reacquisition;
3. range-only/noisy target sensing;
4. decentralized execution;
5. multi-target pursuit or encirclement;
6. Transformer/GNN/attention in pursuit;
7. target prioritization or selection;
8. fixed-capacity target assignment;
9. subgroup pursuit/control;
10. generic dynamic coalition formation;
11. generic capturability/capability-aware assignment;
12. adaptive capture-group cardinality in the broad sense;
13. meaningful spatial multi-agent capture;
14. no-escape/capture geometry;
15. encirclement → physical interception;
16. concurrent patrol/monitoring/scouting during pursuit;
17. completion-triggered coalition dissolution;
18. post-apprehension return to patrol;
19. post-capture resource reuse/reassignment;
20. repeated target/threat arrivals;
21. same-agent patrol → pursuit/response → patrol cycling;
22. persistent patrol/coverage + pursuit by itself;
23. real-UAV learned pursuit;
24. broad zero-shot sim-to-real pursuit;
25. CTBR / continuous physical UAV control;
26. trajectory-prediction-assisted pursuit;
27. broad unseen/variable-clutter pursuit;
28. learned strategic evader;
29. self-play pursuit;
30. historical-policy/FSP/PFSP pursuit;
31. game geometry + RL by itself.

The safe wording is not “first X”. The paper must explain **which assumptions and lifecycle/resource semantics are coupled together in a way the strongest predecessors do not couple**.

---

# 4. Surviving novelty hypothesis

## 4.1 Core problem formulation

[AI判断] The most defensible CoCap problem is:

`persistent coverage by one fungible swarm`
→ `local/intermittent target observation or belief`
→ `estimate coalition-target capture feasibility`
→ `decide whether and which coverage agents should be borrowed`
→ `resolve multi-target resource conflict`
→ `execute terminal physically meaningful capture`
→ `release the capture coalition`
→ `restore nominal coverage`
→ `repeat under later arrivals`.

The word **fungible** matters: the same agent should be able to occupy coverage, support/capture and recovery roles. This is a clean structural separator from P0044/P0033 fixed role pools.

## 4.2 Method-level object

A useful abstraction inherited from R-PE-01 is:

`C(S,j) = estimated robust/probabilistic capturability of coalition S for target j`

where `S` is a candidate coalition and `j` a target.

The marginal value of recruiting agent `i` is:

`Δ_i(S,j) = C(S∪{i},j) - C(S,j)`.

R-LIFE-01 adds the missing nominal-mission cost:

`U_i(S,j) = Δ_i(S,j) - λ · CoverageCost(i)`.

Equivalent constrained formulations are acceptable. The important point is that the gate/recruitment decision should depend jointly on:

- how much agent `i` changes capture feasibility;
- how expensive removing `i` is for coverage;
- target/resource competition;
- uncertainty in target state and capture difficulty.

## 4.3 What `C(S,j)` must not become

Do not relabel any arbitrary network score as “capturability”.

A useful `C(S,j)` should have an explicit operational semantic, for example:
- probability of terminal capture within horizon `H`;
- probability of reaching a no-escape/capture condition before target escape;
- robust lower quantile across target-motion hypotheses;
- learned approximation to a teacher/certificate in simplified states;
- monotonic or calibrated success score validated against rollout outcomes.

A critic Q-value is not automatically `C(S,j)`.

## 4.4 Opponent-robust extension if later needed

R-LM-02 suggests a possible extension:

`C_Π(S,j) = P(capture j | S, belief/state, π_e ~ Π)`

or a worst-case/lower-quantile form over an opponent policy distribution.

This is **not required** unless strategic robustness becomes a contribution. Do not add PFSP merely for fashion.

---

# 5. Lifecycle semantics that must be explicit

## 5.1 Role states

At minimum distinguish:
- `coverage`;
- `support/recruitable` if support is a distinct mode;
- `capture/pursuit`;
- `recovery/released` if the return-to-coverage transient matters.

Fungibility must be shown by actual role transitions, not assumed because all agents share one network.

## 5.2 Terminal capture

`ring formed` is insufficient.

Use a terminal condition that is physically meaningful for the task and is clearly separated from:
- temporary proximity;
- geometric surrounding only;
- target momentarily stationary;
- target briefly unseen.

If simulation deterministically removes/deactivates a captured target, that can provide a clean first terminal event, but the paper should state its abstraction limits.

## 5.3 Release

Recommended first semantics:

`release = confirmed terminal capture/removal/deactivation`
AND
`no remaining capture-safety responsibility for that agent`.

If capture detection is noisy, use a confidence/hold criterion rather than one reward spike.

## 5.4 Recovery

Do not describe “agents switch back to coverage” as evidence of successful lifecycle recovery.

Recovery is complete only when the nominal coverage objective actually returns to an operational threshold.

---

# 6. Minimum evaluation matrix

## 6.1 Capture metrics

Report at least:
- terminal capture success rate;
- time-to-capture;
- per-target capture rate in multi-target scenarios;
- collision/safety failures;
- coalition size at capture;
- agent-seconds committed to capture;
- failures caused by under-recruitment vs over-recruitment.

## 6.2 Coverage/lifecycle metrics

At minimum:
1. pre-event nominal coverage baseline `C_pre`;
2. peak coverage deficit;
3. integrated coverage debt `∫[C_pre-C(t)]_+ dt`;
4. borrowed-agent cost;
5. capture→release latency;
6. release→coverage-recovery time;
7. recovered steady-state coverage ratio;
8. nonparticipant coverage continuity;
9. recovery-before-next-arrival rate;
10. repeated-arrival degradation;
11. long-horizon fraction of agents/time in coverage/support/capture/recovery states.

## 6.3 Repeated-arrival benchmark

At least one long-horizon benchmark should explicitly execute:

`coverage → arrival1 → capture → release → recovery → arrival2 → ...`

Vary inter-arrival time across:
- full-recovery regime;
- next arrival during recovery;
- sustained/high-load regime.

This benchmark is more important for the CoCap lifecycle claim than another one-shot success-rate table.

## 6.4 Opponent robustness

If strategic robustness is not headline novelty:
- randomized/reactive heuristic targets;
- at least one separately trained learned evader;
- preferably one held-out learned opponent not used during pursuer training.

If strategic robustness becomes a claim:
- historical/population or otherwise diverse training;
- unseen learned-policy cross-evaluation;
- best-response/exploitability evidence before using equilibrium language.

## 6.5 Physical realism

If simulation-only:
- explicitly state the deployment level;
- do not imply sim-to-real or onboard autonomy;
- if feasible add actuator lag/noise, observation delay/dropout, dynamics randomization and strict action/rate limits.

The paper can still be strong as a coordination/resource-allocation contribution without real hardware if the scope is honest.

---

# 7. Minimum ablation set for the method claim

The exact architecture can change, but the paper should isolate the claimed coupling.

Recommended ablations:

### A. Fixed coalition size vs adaptive recruitment
- fixed `K` nearest/relevant agents;
- adaptive learned gate/recruitment.

Purpose: show that variable cardinality itself is useful.

### B. Distance/preference recruitment vs capturability-aware recruitment
- nearest/distance-only utility;
- generic learned target preference;
- `C(S,j)` / `Δ_i`-aware variant.

Purpose: isolate the semantic gain beyond P0042-like preference/fixed-capacity logic.

### C. Capturability-only vs capturability + coverage cost
- recruit solely for capture success;
- full objective with `CoverageCost` or coverage constraint.

Purpose: prove the method solves the **joint mission trade-off**, not just pursuit.

### D. Fixed role pools vs fungible same-pool roles
- fixed coverage/capture role partition if implementable;
- shared fungible resource pool.

Purpose: directly expose the structural difference from P0044/P0033.

### E. One-shot termination vs lifecycle continuation
- capture terminates episode;
- capture releases resources and episode continues.

Purpose: prove the lifecycle is not just narrative.

### F. Perfect/global target information vs local/intermittent information
- globally broadcast target state;
- intended local/intermittent observation/belief regime.

Purpose: separate the information contribution from the allocation/lifecycle contribution.

---

# 8. Baseline hierarchy

Do not attempt to reproduce every paper.

Use baselines that answer the paper's causal questions.

## 8.1 Internal/implementable baselines

1. fixed-K nearest pursuers/supporters;
2. all available agents pursue detected target;
3. target preference/attention without explicit resource constraint;
4. fixed capacity per target;
5. learned gate without capturability semantic;
6. full capturability + coverage-cost recruitment;
7. no post-capture continuation / one-shot task;
8. fixed heterogeneous role partition if feasible.

## 8.2 Literature comparators for discussion or reproduction where practical

- P0044 — mission/lifecycle and adaptive capture coalition comparison;
- P0042 — learned assignment/subgroup-control comparison;
- P0035 — Transformer/scaling comparison;
- P0034 — local-FOV assumption comparison;
- P0048 — same-pool patrol/pursuit/recovery state-machine comparison;
- P0036 — physical-action/deployment realism reference;
- P0040 — strategic-opponent realism reference.

Only implement an external baseline if code/task alignment and engineering cost justify it.

---

# 9. Narrative architecture for a future paper

A defensible introduction can be structured as:

1. Persistent UAV coverage and cooperative target capture are individually mature.
2. Classical PE gives capture-feasibility and assignment structure under clean model/state assumptions.
3. Learning methods relax sensing/dynamics/cardinality assumptions, but closest methods typically assume global/shared target state, fixed capacities/roles, one-shot capture tasks, or separate resource pools.
4. Persistent lifecycle work separately establishes coalition release, resource reuse, patrol return and repeated arrivals.
5. The unresolved coordination problem is therefore **not any one primitive**, but deciding when a fungible coverage resource should be borrowed for capture and returned, under uncertain/local target information and multi-target resource conflict.
6. CoCap addresses that coupled coordination problem with an explicit capture-feasibility vs coverage-cost mechanism and long-horizon lifecycle evaluation.

Avoid claiming universal priority. Prefer:
- “we address”;
- “we formulate”;
- “we couple”;
- “in the literature branch surveyed here, we did not find...”

over:
- “for the first time”.

---

# 10. Current implementation alignment gates

Before freezing the final method, audit the latest CoCap code/experiment branch against this memo.

Required questions:

1. Is the final task still one fungible swarm, or have implementation shortcuts accidentally created fixed coverage/capture roles?
2. Does capture terminate the whole episode, or can the final system release and recover coverage?
3. Is target knowledge genuinely local/intermittent at execution, or reconstructed/broadcast globally?
4. Is support recruitment a fixed count / distance rule, or does it encode state-dependent capture difficulty?
5. Is coverage opportunity cost present in recruitment/allocation, not merely as a separate reward term?
6. Is terminal capture semantically stronger than temporary geometry/reward threshold?
7. Are multi-target resource conflicts explicit?
8. Are lifecycle metrics logged?
9. Does the evaluation include repeated arrivals?
10. Is opponent evaluation stronger than one deterministic scripted evader?
11. Are deployment claims matched to the actual dynamics/perception stack?

[AI判断] If the current training stage is temporarily capture-only, that is compatible with development, but the final paper-facing experiment must eventually restore the coverage/release/recovery lifecycle if this memo's novelty narrative is retained.

---

# 11. Claim-triggered future READ gates

Do not reopen broad search.

### Read P0037 only if
`C(S,j)` or an explicit theory-guided geometry→RL object becomes method-central.

### Read P0020 only if
obstacles materially alter the claimed capturability mechanism rather than merely being environmental clutter.

### Read P0026/P0029 only if
3-D heterogeneous or nonholonomic formal capture certificates become part of the final theoretical claim.

### Read unseen-opponent/exploitability literature only if
strategic robustness becomes a paper contribution rather than an evaluation-strengthening dimension.

### Read P0032 only if
historical decentralized learned-pursuit genealogy is needed for final writing.

---

# 12. Decision checkpoint after first-stage closure

**Do not launch another literature wave now.**

The next high-value work is to compare this memo against the latest CoCap implementation and decide whether the method should explicitly elevate:

- `C(S,j)` / coalition capturability estimation;
- marginal recruitment `Δ_i`;
- coverage opportunity cost;
- adaptive target capacity;
- explicit release/recovery state;
- repeated-arrival evaluation.

After that implementation/method decision, reopen only the specific claim-triggered paper branch required by the chosen design.
