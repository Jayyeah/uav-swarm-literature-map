# R-LM-02 — Physical Deployment / Strategic Opponent Frontier READ

## Batch scope

This READ covers only:

- **P0036** — Jiayu Chen et al. 2025, *Online Planning for Multi-UAV Pursuit-Evasion in Unknown Environments Using Deep Reinforcement Learning* (OPEN)
- **P0040** — Wenhao Tang et al. 2026, *AgilePE: Autonomous UAV Pursuit-Evasion via Self-Play Reinforcement Learning*

No broad MARL search was reopened. The comparison ruler is the already frozen project state from R-PE-01, R-LM-01, R-CE-01, and R-LIFE-01.

Evidence labels:
- `[原文]` — uploaded full paper/manuscript;
- `[Web核验]` — limited publication/version verification;
- `[AI判断]` — synthesis, boundary judgment, or CoCap implication.

---

# 1. Executive result

[AI判断] R-LM-02 closes two final standalone novelty fronts without materially damaging the current strongest CoCap candidate.

**Physical/deployment boundary:** learned UAV pursuit has already reached direct CTBR control and zero-shot real quadrotor deployment. P0036 does this with three physical pursuers, calibrated quadrotor dynamics, obstacle scenarios, mocap/offboard inference and a virtual evader. P0040 goes one step further on execution architecture by running policy inference onboard and using a physical learned evader, but still relies on external mocap and reports only 1v1 obstacle-free hardware validation.

**Strategic-opponent boundary:** P0040 already implements bilateral learned pursuit/evasion with current self-play, historical policy pools, FSP and failure-prioritized PFSP. Therefore `learned strategic evader`, `self-play pursuit`, and even `historical-population/PFSP pursuit` cannot carry CoCap novelty. However, P0040 does **not** establish low exploitability, Nash convergence, or robustness to independently trained unseen learned policies.

**Current CoCap novelty candidate:** unchanged in substance:

> **information + capturability + lifecycle coupling**

Neither paper has a fungible coverage pool, target-wise coalition/resource assignment, `C(S,j)`-like coalition feasibility, terminal capture release, coverage restoration, or repeated arrivals.

**Competitor map remains:**
- P0044 — strongest overall/lifecycle system competitor;
- P0042 — strongest direct learning/allocation-method competitor;
- P0034 — strongest local-information learning competitor;
- P0035 — strongest Transformer/scaling competitor;
- **P0036 — strongest CoCap-relevant multi-UAV physical-deployment competitor**;
- **P0040 — strongest strategic-opponent competitor**, with preprint caveat.

---

# 2. Unified comparison matrix

| Axis | P0036 OPEN | P0040 AgilePE |
|---|---|---|
| task | cooperative pursuit in variable 3-D clutter | adversarial 1v1 aerial PE/tracking |
| pursuer count | **3** reported | **1** |
| evader count | **1** | **1** |
| multi-target? | No | No |
| strategic evader? | **No**; reactive potential-field heuristic | **Yes**; learned evader |
| self-play? | No | **Yes**; naive SP → FSP → PFSP |
| historical opponent pool? | No | **Yes**, both pursuer and evader pools |
| PFSP? | No | **Yes**, failure-rate-prioritized historical sampling |
| observation | self attitude/velocity + teammates + 3 nearest obstacles + target relative state/prediction | own pose/attitude/velocity/action history + temporal opponent state window |
| target visibility | LOS blocked by obstacles; target masked if no team member detects | conical FOV + simulated occlusion; state masked when invisible |
| communication | detected target can be passed to teammates | no teammate comm issue in 1v1; mocap infrastructure in real test |
| CTDE | MAPPO/Dec-POMDP shared policy; exact critic privilege not fully separated in text | MAPPO adversarial training; frozen historical opponent policies |
| action interface | **CTBR** → low-level PID → motors | **CTBR** → PX4 / simulated response backend |
| vehicle dynamics | calibrated 6-DOF rigid body + motor first-order response | 6-DOF/CTBR state propagation with RK4 + calibrated response delay/noise |
| obstacles | **Yes**; 4–5 cylinders; obstacle layouts varied | formulation supports occlusion, but reported experiments are **obstacle-free** |
| unknown map | unseen/variable obstacle configurations; no SLAM/map belief | No demonstrated unknown-map problem |
| trajectory prediction | **Yes**, LSTM EPN | No dedicated trajectory predictor |
| capture semantics | any-one UAV within radius 0.3 | primary objective/metric is distance + in-FOV tracking; close contact is collision/safety termination; clean capture semantics underspecified |
| safety/collision | collision penalty; collision-rate metric; obstacle/agent safety distance | overspeed, boundary, proximity/collision, action smoothness penalties |
| sim-to-real | **zero-shot** | **zero-shot** |
| localization | external motion capture | external motion capture + onboard IMU fusion |
| perception | state-based target/obstacle inputs; no onboard vision mapping | state-based observations / software FOV; no onboard vision |
| onboard/offboard compute | actor + EPN on **local/offboard computer** | policy inference **onboard Jetson Orin NX** |
| real-UAV scale | **3 physical pursuer UAVs** | **2 physical UAVs**, 1 pursuer + 1 evader |
| physical target | **No**; virtual evader | **Yes**; physical evader UAV |
| experiment repetitions | **5 repeats per real scenario**; sim 300 episodes per scenario | hardware trial count/statistics not reported; qualitative case studies |
| lifecycle after capture | none; capture terminates task | none |
| repeated arrivals | No | No |
| dynamic coalition recruitment | No; all pursuers permanent | N/A, 1v1 |
| adaptive subgroup size | No | N/A |
| target-wise allocation | No | N/A |
| capturability object | No | No |
| relevance to CoCap | strongest physical-action/deployment reference for swarm pursuit | strongest strategic-opponent/self-play reference |
| strongest limitation | virtual target + mocap + offboard inference + heuristic evader + any-one capture | preprint + 1v1 + mocap/state-based + obstacle-free real validation + no unseen learned-opponent exploitability test |

---

# 3. P0036 physical / sim-to-real contribution — what is actually proven?

## 3.1 What is genuinely strong

[原文] OPEN does not merely output waypoints or planar velocities. Its actor outputs `Collective Thrust and Body Rates (CTBR)` and training includes a calibrated quadrotor model with attitude, angular rate and motor-response dynamics.

[原文] Simulation evaluation is also nontrivial: three slower pursuer quadrotors chase a faster evader through obstacle configurations; unseen layouts and target speeds are tested; target occlusion is modeled; all four principal scenarios use hundreds of simulation episodes.

[原文] The final policy is transferred zero-shot to three physical Crazyflie 2.1 pursuers, and the two-stage smoothness refinement is empirically necessary: the unsmoothed policy causes unstable/crash behavior in real flight.

[AI判断] This is a real physical-control milestone for learning-based multi-UAV pursuit. It is substantially more realistic than CoCap-style point-mass or abstract `a,ω / v_x,v_y` simulation if CoCap does not model vehicle dynamics, actuator constraints, delay or a deployable command stack.

## 3.2 What “real-UAV autonomy” it does **not** prove

[原文, Sec. V-F]
- quadrotor state comes from external mocap;
- evader is **virtual**;
- true evader state is injected into actor/EPN after software detection;
- policy/EPN inference runs on a local computer;
- commands are radioed to vehicles.

[AI判断] Therefore the correct statement is:

> **P0036 proves zero-shot transfer of a sim-trained, body-level CTBR multi-UAV pursuit controller through an external-state/offboard-compute infrastructure.**

It does **not** prove:
- onboard target perception;
- onboard obstacle perception/map building;
- onboard localization;
- onboard policy inference;
- pursuit of a physical evasive target.

## 3.3 “Unknown environment” boundary

[原文] environment/task parameters vary obstacle number/positions and initial states; actor sees the three nearest obstacle relative positions; target can be occluded.

[AI判断] The paper occupies:

`unseen/variable clutter + partial obstacle list + target occlusion`

not:

`unknown physical map + online SLAM/perception + uncertain belief-state planning`.

So broad “unknown-environment pursuit” wording is unsafe, but onboard unknown-map autonomy remains a materially stronger concept.

---

# 4. P0040 self-play/PFSP — how strong is it?

## 4.1 Exact opponent-training hierarchy

### Naive SP
[原文] latest pursuer vs latest evader, synchronously updated. No historical opponent overhead. The paper shows strategy oscillation / eventual unilateral evader collapse.

### FSP
[原文] maintain historical policy pools for both sides. During a training round, current pursuer/evader learners face frozen historical opponent checkpoints sampled uniformly from the opposite pool; each new optimized policy is archived.

### PFSP
[原文, Sec. IV-A3] historical opponents are sampled with probability proportional to the **current agent’s failure rate** against them, so training concentrates on bottleneck opponents.

[AI判断] This is meaningfully stronger than:

`trained against one learned evader`

and stronger than:

`current-policy-only self-play`.

It reaches the project’s **historical/population self-play** level.

## 4.2 What robustness is actually demonstrated?

[原文]
- historical cross-play payoff matrices for FSP/PFSP;
- later policies face multiple earlier policies;
- scripted-opponent evaluations;
- interpretable case studies against direct-tracking and fast-spinning opponents;
- naive-SP multi-seed curves expose collapse.

[AI判断] This is credible evidence of:
- reduced forgetting;
- broader robustness across the **training lineage’s historical policies**;
- some transfer to hand-defined heterogeneous opponent behavior.

It is **not** evidence of:
- robustness to independently trained unseen learned opponents;
- exploitability bounds;
- best-response resistance;
- a Nash-equilibrium certificate;
- general strategic optimality.

The paper’s phrases such as “robust policy equilibria” should therefore remain author claims, not the map’s conclusion.

## 4.3 PFSP wording ambiguity

[原文] an earlier prose summary of who gets prioritized is awkward and can be read inconsistently with the later algorithm explanation.

[AI判断] Normalize PFSP from the explicit Sec. IV-A3 mechanism: sampling probability is driven by **failure against a historical candidate**, i.e. hard/bottleneck opponents are prioritized. Do not reverse this based on one summary sentence.

---

# 5. Execution-time information assumptions

## P0036

[原文]
- self orientation/velocity;
- relative positions to all teammates;
- exact relative positions of the three nearest obstacles;
- target relative position whenever any team member detects the evader;
- target position is then shareable team-wide;
- EPN uses historical positions of all pursuers plus evader position/velocity when available.

[AI判断] P0036 has real occlusion, but not strict local target belief after detection. It should not be used as evidence that each agent executes only from its own locally sensed target state.

## P0040

[原文]
- self position/attitude/velocity/action history;
- exact opponent state while inside software FOV/unoccluded;
- masked opponent state otherwise;
- real deployment state originates from mocap+IMU.

[AI判断] AgilePE’s strategic sophistication is learned under **state-based perception and strong localization**. It relaxes opponent-model stationarity, not low-level perception uncertainty. Its information assumption is therefore still stronger than a fully onboard local-vision CoCap setting.

---

# 6. Physical deployment boundary v1

Use six layers:

1. **Kinematic simulation** — point mass / simple motion / high-level action.
2. **Vehicle-dynamic simulation** — 6-DOF or otherwise physically constrained platform dynamics.
3. **Noisy/delayed sensing + actuator abstraction** — response latency, noise, perturbation, actuator constraints.
4. **SITL/HITL** — flight stack/hardware loop without free physical vehicle mission execution.
5. **External-localization real UAV** — physical UAV flight, but mocap/GPS/external state infrastructure remains.
6. **Onboard-perception real UAV** — onboard target/obstacle perception and onboard decision/control without external tracking as the task-state oracle.

### Where the two READ papers sit

- **P0036:** Level 5, but specifically `external localization + offboard inference + virtual target`; strong Level-2 dynamics, partial Level-3 physical regularization.
- **P0040:** Level 5, specifically `external localization + onboard inference + physical learned opponent`; stronger Level-3 latency/noise modeling, but hardware evaluation is 1v1 obstacle-free and mostly qualitative.
- **Neither reaches Level 6.**

### Boundary statement

[AI判断]

> **Real-UAV learned pursuit, zero-shot sim-to-real, and CTBR-level physical control are already occupied. The remaining deployment frontier is not “real UAV” by itself, but progressively removing external state/perception infrastructure and validating the complete sensing→decision→control loop under physical targets/clutter.**

### Strongest physical competitor

**P0036** is the strongest **CoCap-relevant multi-UAV physical-deployment competitor** because it combines three physical pursuers, obstacle scenarios, quantitative repeated trials, CTBR and a formal RA-L publication.

**P0040 is stronger on one deployment sub-axis:** onboard inference and a physical learned opponent. It does not displace P0036 for the swarm/multi-UAV comparison because it is 1v1, obstacle-free in reported experiments, quantitatively thin, and preprint-only.

---

# 7. Strategic-opponent boundary v1

Recommended opponent ladder:

1. fixed scripted evader;
2. randomized/reactive heuristic distribution;
3. separately trained learned evader;
4. current-policy self-play;
5. historical/population self-play (FSP/PFSP);
6. unseen-policy generalization / exploitability-oriented evaluation.

### Current map placement

- P0036: Level 2 at best; one reactive heuristic family with speed OOD.
- P0034: reaches Level 3 in evaluation through a separately trained DDPG evader.
- P0033: learned competitors, but no historical-population machinery.
- **P0040: Level 5 training frontier.**
- P0040 does **not** close Level 6.

### Boundary statement

[AI判断]

> **For UAV PE, historical-policy population training and PFSP are no longer a safe novelty claim. The unresolved robustness frontier is evaluation against strategically distinct, independently trained/unseen policies and/or exploitability-style best-response tests, not merely having self-play.**

### Strongest strategic competitor

**P0040 AgilePE**, with explicit evidence-status caveat: technically strongest on this axis, but currently only an under-review arXiv preprint.

---

# 8. Standalone novelty-claim audit

| Claim | R-LM-02 status | Reason |
|---|---|---|
| real-UAV pursuit | **DEAD** | P0036 and P0040 both have real UAV execution; earlier map already had other physical predecessors |
| sim-to-real pursuit | **DEAD in broad form** | both claim zero-shot transfer; scope/infrastructure must be specified |
| continuous / physical control | **DEAD** | direct CTBR is already demonstrated |
| unknown-environment pursuit | **DEAD only in broad unseen-clutter sense** | P0036 handles unseen/variable obstacle layouts; onboard unknown-map/SLAM belief remains stronger and unproven here |
| trajectory-prediction-assisted pursuit | **DEAD** | P0036 EPN directly occupies it |
| self-play pursuit | **DEAD** | P0040 |
| strategic learned evader | **DEAD** | P0040; also weaker predecessors exist |
| PFSP for UAV pursuit | **OCCUPIED / do not claim** | P0040 directly uses PFSP, although currently preprint-only |
| robust pursuit against opponent distributions | **QUALIFIED** | historical-pool robustness shown; unseen independent learned-policy/exploitability robustness not shown |
| onboard-perception real pursuit | **NOT CLOSED by these two** | both depend on external state/localization; P0036 future work explicitly points to vision |

[AI判断] These are novelty-boundary statements for CoCap wording, not universal priority claims over the entire literature.

---

# 9. Lifecycle connection

Neither paper materially changes R-LIFE-01.

## P0036
- persistent nominal mission before target: No;
- dynamic coalition recruitment: No; all pursuers are permanent;
- target-wise allocation: No;
- terminal capture: yes, but any-one proximity;
- post-capture continuation/release: No; capture ends the task;
- return to patrol/coverage: No;
- repeated arrivals: No.

## P0040
- persistent nominal mission: No;
- coalition/recruitment: N/A, 1v1;
- clear CoCap-style terminal capture lifecycle: No;
- post-event release/coverage: No;
- repeated arrivals: No.

**Conclusion:**

[AI判断]

> P0036/P0040 enhance **pursuit policy realism / vehicle realism / opponent realism**, not lifecycle closure.

R-LIFE-01 remains frozen: P0044 is still the strongest overall lifecycle/system competitor and P0048 the closest same-pool lifecycle near miss.

---

# 10. Capturability connection

## P0036

- scalar critic value is not a coalition-target capturability certificate;
- all three agents are always in the pursuit team;
- no subset `S`, no marginal agent value, no target competition;
- terminal criterion is any-one proximity rather than strategy-quantified coalition feasibility.

## P0040

- 1v1 self-play value/win/in-FOV metrics are not `C(S,j)`;
- no coalition size/marginal pursuer variable exists;
- historical opponent robustness is about policy evolution, not team resource feasibility.

### Legitimate bridge for CoCap

[AI判断] P0040 suggests a **robustness dimension** for a future `C(S,j)` if CoCap makes it central:

`C_Π(S,j)=P(capture target j | S, belief/state, π_e ~ Π)`

or a lower-quantile/worst-case version over an opponent policy distribution.

This is **our design inference**, not something AgilePE already implements.

---

# 11. Placement in the current competitor map

## Does P0036 become strongest physical deployment competitor?

**Yes, for the CoCap-relevant multi-UAV swarm-pursuit physical axis.**

Its combination of 3 real pursuers + obstacle scenarios + CTBR + repeated hardware trials + formal RA-L evidence is currently the best match to a future physical CoCap comparison.

P0040 has a stronger onboard-compute/physical-opponent stack, but its 1v1/preprint/qualitative obstacle-free hardware scope makes it a different frontier node rather than a replacement.

## Does P0040 become strongest strategic-opponent competitor?

**Yes.** It is the only current READ anchor with bilateral historical-policy population training and PFSP.

## Do either become closer overall than P0044?

**No.** P0044 remains closer to CoCap’s integrated system because it already combines persistent exploration, dynamic capture coalitions, moving targets, real capture, post-capture reuse and hardware validation.

## Do either displace P0042 as direct learning/allocation competitor?

**No.** Neither P0036 nor P0040 has multi-target assignment, subgroup allocation, or resource capacity. P0042 remains the direct learning/allocation baseline.

## Do they change the candidate gap?

**No substantive change.** They eliminate physical-action and self-play escape routes for novelty wording, which actually makes the current coupling claim cleaner:

`local/intermittent information`
+
`coalition capture-feasibility estimation`
+
`target-wise resource recruitment/assignment`
+
`persistent same-pool coverage↔capture lifecycle`.

---

# 12. Recommended opponent-realism ladder for CoCap

If opponent robustness is **not** the headline contribution:

- training minimum: **Level 3** — at least one separately trained learned evader, plus Level-2 randomized heuristics for diversity;
- evaluation minimum: include a **held-out learned policy not used to train the pursuer**, i.e. move the evaluation toward Level 6 even if training does not use PFSP;
- report capture success, time-to-capture, coverage debt/recovery, and coalition size across opponent classes separately.

If CoCap **claims strategic robustness**:

- training should reach **Level 5** (historical/population self-play or a comparably diverse opponent distribution);
- evaluation should add Level-6-style unseen learned opponents / cross-seed or cross-algorithm policies;
- avoid equilibrium language unless exploitability/best-response evidence exists.

[AI判断] CoCap does **not** need to copy PFSP merely to be publishable if strategic-opponent robustness is not central. But using only one deterministic scripted evader would now be an obvious evaluation weakness.

---

# 13. Recommended deployment-realism ladder for CoCap

### Minimum honest reporting

Whatever the implementation level, state it explicitly:

- if CoCap remains kinematic: **Level 1 simulation**, no sim-to-real/physical-autonomy claim;
- if acceleration/velocity dynamics are modeled: **Level 2** only if vehicle constraints are actually represented;
- if feasible, add **Level 3** actuator/sensing delay/noise/randomization as the most valuable simulation-only realism upgrade.

### If no real-UAV experiment is planned

Recommended disclaimer:

> **The evaluation validates multi-agent coordination and mission lifecycle in simulation; it does not validate sim-to-real transfer, onboard perception/localization, or hardware-safe flight. The action/dynamics model should therefore be interpreted as a mission-level abstraction rather than a demonstrated flight-control stack.**

[AI判断] This is sufficient if CoCap’s contribution is clearly positioned as coordination/resource reasoning, not deployment. Trying to imply “realistic UAV autonomy” without P0036/P0040-level hardware evidence would invite an avoidable comparison.

### Most useful realism upgrade without hardware

If compute/time permits, target Level 3 rather than attempting superficial hardware claims:
- actuator lag/noise;
- observation delay/dropout;
- dynamics parameter randomization;
- strict body/acceleration/rate limits;
- evaluate policy sensitivity to these perturbations.

---

# 14. Answers to the 14 mandatory synthesis questions

### 1. P0036 真正的 physical/sim-to-real contribution 是什么？
A learned multi-UAV pursuit controller operating directly at CTBR level, trained with calibrated quadrotor dynamics and transferred zero-shot to three physical pursuers; target prediction, adaptive environment generation and two-stage action smoothing support the transfer.

### 2. P0036 real-UAV autonomy 到底在哪一层？
**Deployment ladder Level 5**, but a constrained subtype: external mocap localization + offboard policy/prediction compute + virtual evader. It is not onboard-perception autonomy.

### 3. P0040 self-play/PFSP 到底有多强？
It reaches historical-population training: current-current SP baseline, historical FSP, then failure-prioritized PFSP with archived policies for both sides. This is materially stronger than a single learned evader or naive self-play.

### 4. P0040 是否真正提高 strategic / unseen opponent robustness？
**Strategic/historical robustness: yes, with evidence. Unseen learned-policy robustness: not established.** Historical cross-play and scripted/heterogeneous cases support reduced forgetting, but no exploitability or independent unseen learned-policy suite is reported.

### 5. 两篇 execution-time information assumptions 分别是什么？
P0036: exact self/team-relative state, exact nearest-obstacle positions, team-shared target state after any detection, prediction from team/target history. P0040: exact state variables when target visible, software FOV/occlusion masking, strong global localization; real state comes from mocap+IMU. Neither is onboard raw-perception autonomy.

### 6. 谁是 strongest physical deployment competitor？
**P0036 for CoCap-relevant multi-UAV pursuit deployment.** P0040 is stronger specifically on onboard inference + physical learned opponent.

### 7. 谁是 strongest strategic-opponent competitor？
**P0040 AgilePE**, with preprint/under-review evidence caveat.

### 8. 是否改变 P0044 = strongest overall system competitor？
**No.** P0044 remains the strongest overall/lifecycle system competitor.

### 9. 是否改变 P0042 = strongest direct learning/allocation competitor？
**No.** Neither R-LM-02 paper has multi-target resource allocation or coalition recruitment.

### 10. 是否改变 `information + capturability + lifecycle coupling` novelty candidate？
**No.** It survives. R-LM-02 only removes physical-action and self-play as possible standalone novelty escape routes.

### 11. CoCap 最终至少需要什么 opponent robustness evaluation？
If strategic robustness is not central: at least one separately trained learned evader plus randomized heuristics, and a held-out learned opponent at evaluation. If strategic robustness is claimed: historical/population training plus unseen-policy cross-evaluation.

### 12. CoCap 最终至少需要什么 physical-realism / deployment disclaimer？
Explicitly locate the paper on the deployment ladder and avoid sim-to-real/hardware-autonomy language unless supported. If simulation-only, label the dynamics/action as mission-level abstraction and state that onboard perception/localization and hardware safety are unvalidated.

### 13. 第一阶段 literature map 是否可以在本轮后视为基本闭合？
**Yes — for the declared CoCap-near novelty axes.** The map now has theory, closest learning, classical sensing/interception, lifecycle, physical deployment and strategic-opponent boundaries. Remaining reads should be claim-triggered, not another broad wave.

### 14. 是否立即 READ P0037？
**No.** Keep P0037 deferred. Read it only if `C(S,j)` / theory-guided capturability becomes a concrete method core that needs a direct geometry→RL predecessor comparison.

---

# 15. First-stage closure judgment

[AI判断] **The first-stage literature map can now be treated as basically closed.**

What is closed strongly enough for method design:
- reach-avoid / capturability / assignment theory;
- classical sensing/decentralization/interception;
- closest learning target-selection/allocation/scaling competitors;
- lifecycle recovery/reuse/repeated-arrival boundary;
- physical action / sim-to-real / real-UAV boundary;
- strategic learned-opponent / self-play boundary.

What remains conditional, not an immediate search obligation:
- P0037 if `C(S,j)` becomes method-central;
- P0020 if obstacle-modified capturability becomes central;
- P0026/P0029 if final claims require 3-D/nonholonomic formal capture certificates;
- a very narrow unseen-opponent/exploitability chain only if strategic robustness becomes a claimed contribution.

**No new broad SEARCH is recommended now.**

---

# 16. Physical deployment boundary v1

**Occupied:**
- real quadrotor learned pursuit;
- zero-shot sim-to-real pursuit;
- direct CTBR pursuit control;
- calibrated vehicle dynamics;
- external-mocap real flight;
- offboard inference with multiple real pursuers (P0036);
- onboard inference with a physical learned adversary (P0040).

**Not closed by these papers:**
- onboard vision/local target perception as the pursuit-state source;
- onboard obstacle perception / online mapping in unknown clutter;
- fully infrastructure-free local-perception pursuit;
- a single study combining multi-UAV swarm capture, physical adversary, clutter, onboard perception, allocation, and lifecycle.

**Strongest physical competitor:** **P0036**, scoped to CoCap’s multi-UAV pursuit/deployment axis.

---

# 17. Strategic-opponent boundary v1

**Occupied:**
- learned evader;
- bilateral current-policy self-play;
- historical policy pools;
- FSP;
- PFSP/hard-opponent sampling;
- historical cross-play analysis;
- physical learned pursuer/evader execution.

**Not closed by P0040:**
- independently trained unseen learned-opponent generalization;
- exploitability / best-response gap;
- formal equilibrium evidence;
- multi-pursuer/multi-evader population self-play with allocation/coalitions;
- strategic-opponent robustness coupled to persistent coverage/resource lifecycle.

**Strongest strategic competitor:** **P0040 AgilePE**, but currently preprint/under review.

---

# 18. Impact on current CoCap novelty wording

R-LIFE-01 wording survives. R-LM-02 recommends one additional defensive clause: do not let physical realism or strategic-opponent realism become implicit novelty claims.

Recommended wording remains:

> **CoCap addresses a persistent same-pool coverage–capture coordination problem in which UAVs operating under local/intermittent target information are temporarily recruited from nominal coverage according to capture-feasibility and mission opportunity cost, execute terminal capture, and are explicitly released back to restore coverage for subsequent target arrivals. The candidate novelty lies in coupling local information, coalition capturability and lifecycle-aware resource reuse, rather than in sensing, self-play, physical control, capture, coalition formation or post-capture return individually.**

Short method-facing form:

> **A fungible UAV swarm borrows agents from persistent coverage only when their marginal contribution improves target capturability enough to justify coverage cost, then releases them after confirmed capture to recover coverage under repeated arrivals.**

---

# 19. Named follow-up chains

No named chain from these two papers plausibly forces reopening the current novelty boundary.

Record-only methodology chains:

1. **P0036 → Chen et al. 2025, _What Matters in Learning a Zero-Shot Sim-to-Real RL Policy for Quadrotor Control? A Comprehensive Study_** — inspect only if CoCap makes sim-to-real/control methodology a central experimental claim.
2. **P0040 → VolleyBots / hierarchical co-self-play multi-drone volleyball (2025)** — inspect only if population/hierarchical strategic training becomes a CoCap method component; these do not currently close the CoCap PE/lifecycle intersection.

No new paper is queued from this READ.

---

# 20. PROJECT_PROTOCOL handoff

## NEW PAPERS
None. No SEARCH was opened.

## UPDATED PAPERS
- **P0036** — READ complete. Formal RA-L identity confirmed; physical audit corrected the naive “real autonomous pursuit” reading to `3 real pursuers + mocap + offboard inference + virtual evader`, while preserving its strong CTBR/sim-to-real role.
- **P0040** — READ complete. Preprint/under-review status confirmed; SP→FSP→PFSP mechanics, historical pool scope, onboard-compute/mocap deployment and robustness limits normalized.

## MUST READ
- P0036 — completed; retain MUST READ as physical-deployment anchor.
- P0040 — completed; retain MUST READ as strategic-opponent frontier anchor, with preprint caveat.

No new MUST READ promotion.

## MAP
No canonical decision changes proposed by this child READ.

## ARCHIVE
None.

## TAXONOMY CHANGES
Recommend MASTER preserve/add:

1. deployment ladder: `kinematic sim → vehicle dynamics → delay/noise abstraction → SITL/HITL → external-localization real UAV → onboard-perception real UAV`;
2. split real deployment by **localization source**, **target physicality**, and **onboard/offboard policy compute**;
3. split `unknown environment` into unseen-layout generalization vs online map/perception uncertainty;
4. opponent ladder: `scripted → randomized heuristic → separately trained → current SP → historical/population SP → unseen-policy/exploitability`;
5. distinguish historical-policy cross-play from equilibrium/exploitability evidence;
6. `critic/value ≠ coalition capturability C(S,j)` unless coalition-target feasibility semantics are explicit.

## SEARCH GAPS
No immediate broad gap.

Only claim-triggered future work:
- P0037 if learned capturability becomes method core;
- unseen learned-opponent/exploitability evaluation literature only if CoCap claims strategic robustness;
- P0020/P0026/P0029 only if the final method requires those formal certificate extensions.

## CONFLICTS / UNCERTAINTIES

1. **P0040 publication status:** arXiv v1 dated 2026-08-14, comments “Under review”; no formal venue verified as of 2026-09-16.
2. **P0040 PFSP wording:** one high-level description is awkward relative to explicit Sec. IV-A3 failure-rate prioritization; use the explicit mechanism.
3. **P0040 metric semantics:** Table II is In-FOV Rate, while surrounding prose sometimes uses survival/win/capture language inconsistently. Do not reinterpret it as calibrated capture probability.
4. **P0040 physical statistics:** no hardware repetition count/success-rate table found; real evidence should be described as qualitative tactical validation.
5. **P0036 CTDE critic scope:** MAPPO is clear, but the main text does not expose a clean separate privileged-global-state critic vector; avoid inventing one.
6. **P0036 unknown environment:** no SLAM/map-building/onboard obstacle-perception evidence; “unknown” means variable/unseen layouts with nearest-obstacle state features and target occlusion.
7. **P0036 real target:** virtual evader; do not describe the experiment as a fully physical pursuer-vs-evader engagement.

---

# 21. Final R-LM-02 stance

**Physical deployment boundary v1:** CTBR-level learned pursuit and Level-5 external-localization real-UAV deployment are occupied; Level-6 onboard-perception pursuit remains outside these two papers.

**Strategic-opponent boundary v1:** historical/population self-play and PFSP are occupied by P0040; unseen learned-policy/exploitability robustness remains open.

**Strongest physical competitor:** **P0036 OPEN** for the CoCap-relevant multi-UAV deployment axis; P0040 is stronger on onboard inference/physical-opponent sub-axis.

**Strongest strategic competitor:** **P0040 AgilePE**, preprint caveat.

**Impact on current CoCap novelty wording:** no structural change. `information + capturability + lifecycle coupling` remains the strongest candidate; physical realism and self-play are explicitly excluded as standalone novelty.

**Recommended opponent-realism ladder:** `scripted → randomized heuristic → separately trained → current SP → historical/PFSP → unseen-policy/exploitability`.

**Recommended deployment-realism ladder:** `kinematic sim → vehicle dynamics → delay/noise abstraction → SITL/HITL → external-localization real UAV → onboard-perception real UAV`.

**Named follow-up chains:** record-only sim-to-real and aerial self-play methodology chains above; no new SEARCH or immediate READ.

**First-stage map status:** **basically closed after R-LM-02**. Next action should be MASTER consolidation / CoCap novelty-method-design memo, not another broad literature wave.
