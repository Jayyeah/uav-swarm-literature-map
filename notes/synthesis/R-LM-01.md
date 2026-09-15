# R-LM-01 — Closest Multi-Target / Sensing / Allocation Competitors

## Scope and comparison frame

Batch papers: **P0033, P0034, P0035, P0042 only**.

This synthesis uses the R-PE-01 abstraction as the comparison ruler:

`reach-avoid semantics → capturability certificate → feasible pursuer/coalition-target edge → resource-constrained assignment → no-escape enclosure → maintained contraction → capture`.

The purpose is not to rank backbones. It is to determine which **classical assumptions learning has actually relaxed**, and which CoCap system/method gaps remain after the closest learning competitors are read in full.

---

# 1. Strongest unified assumption matrix

Legend: **Y** = explicitly covered; **P** = partial/qualified; **N** = not covered; **?** = not specified enough for a strong claim.

| Axis | P0033 Role-MADDPG | P0034 Limited-FOV NAGC | P0035 TERL | P0042 Dual-policy AUV |
|---|---|---|---|---|
| Task semantics | tracking + concurrent exploration | search→pursuit↔reacquisition→proximity capture | multi-target geometric encirclement | explicit allocation + 3-D spatially valid capture |
| Multi-target moving PE | **Y** (simulation) | **N** (one moving evader) | **Y** | **Y** |
| Persistent after one target | **P** fixed scouts continue while trackers track; no capture lifecycle | **N** episode ends on capture | **P** pursuers move to remaining evaders | **P** episode continues, but captured subgroup freezes |
| Genuine local enemy detection | **N/?** no finite FOV/range model | **Y** finite range/angle + building occlusion | **N** all active evaders globally available | **N** target positions externally supported/team-available |
| Post-detection target sharing | **Y** target location propagated to neighbors | **Y** detected coordinate shared team-wide | **Y** one-way target broadcast/global active-target state | **Y/external support** |
| Limited teammate communication | **P/?** neighbor network mentioned, details weak | **N** area-wide reliable comm in base task | **Y** no peer-to-peer comm, but target broadcast remains | **P** connectivity feature, but communication simplified |
| Decentralized actor/policy execution | **Y** MADDPG actors | **Y** CTDE actors | **Y** independent shared policy | **Y** CTDE actor factorization, with team allocation layer |
| Centralized critic/global training info | **Y** centralized critic | **Y** centralized critic/global evader state | **P** global reward/training info, value-based IQN rather than stated central critic | **Y** centralized critic |
| External/offboard/global localization evidence | **Y** real demo: external computer + UWB | simulation only | simulation only | simulation only |
| Dynamic role switching coverage↔capture | **N** role classes fixed by reward/count | **N** task phase changes, not agent role allocation | **N/P** target focus changes implicitly | **P** target assignments can be updated over contract intervals, but fixed capacities; no coverage role |
| Target selection / prioritization | **N** manual subteams | not applicable | **Y** attention-based | **Y** learned preference logits |
| Explicit target assignment matrix | **N** | **N** | **N** | **Y** binary \(Z\) |
| Capacity constraint | **N** | **N** | **P** soft crowding/count reward only | **Y** hard Sinkhorn/rounding with prescribed \(q_j\) |
| Dynamic coalition/support recruitment | **N** | **N** | **P** emergent redistribution, no membership variable | **P** explicit subgroup allocation, but fixed demand and no post-capture release |
| Capturability-aware recruitment | **N** | **N** | **N** | **N** |
| Coalition capturability certificate | **N** | **N** | **N** | **N** |
| Geometric multi-agent capture | **N** tracking/proximity | **N** any-one radius | **Y** ≥3 + angular gap/balance | **Y** convex hull + balance + closing advantage |
| No-escape / strategy guarantee | **N** | **N** | **N** terminal geometry only | **N** terminal geometry/dynamics only |
| Persistent coverage/search by nonparticipants | **P** fixed scouts concurrently explore | **P** only before first discovery / reacquisition | **N** | **N** |
| Post-capture return to coverage/search | **N** | **N** | **N** | **N**; subgroup holds/frozen |
| Repeated/new target arrivals | **N** | **N** | **N** | **N** |
| Obstacles | **Y** random static | **Y** buildings + occlusion | **Y** static + vortices | **N** in reported setup |
| Physically meaningful action | **N/P** MPE continuous 2-D | **P/Y** acceleration + yaw rate in AirSim | **P** 2-D discrete acceleration + angular rate | **Y/P** 3-D thrust/yaw/pitch, simplified AUV kinematics |
| Strategic/learned evader | **Y/P** evaders learn during competitive training | **P** separately pretrained DDPG evader among test policies | **N** APF heuristic | **N** reactive heuristic |
| Real deployment | **Y** Crazyflie, but UWB/offboard; single target | **N** | **N** | **N** |
| Count generalization | **N** demonstrated fixed compositions | **P** larger pursuer teams with fixed-input workaround | **Y** 15/4 training → 80/20 without retraining | **P** 8/2→12/3 scalability test; zero-shot not established |

### Immediate interpretation

[AI判断] The four papers jointly cover **many individual pieces** of the CoCap story, but none implements the full chain:

`strictly local/intermittent target knowledge`
→ `uncertain coalition capturability`
→ `dynamic support recruitment`
→ `resource-constrained target-wise allocation`
→ `meaningful capture`
→ `release to persistent coverage`
→ `repeated arrivals`.

The strongest gap now lies in the **coupling between these pieces**, not in any one backbone or task primitive.

---

# 2. Strongest predecessor by axis

- **Literal local FOV / occlusion / reacquisition:** **P0034**. [原文] 200 m range, 120° forward FOV, building occlusion, target loss, lost-point memory and suspect-area reacquisition.
- **Concurrent exploration + pursuit:** **P0033**. [原文] scouts continue Voronoi exploration while pursuers track targets; [AI判断] roles are fixed rather than dynamically gated.
- **Multi-target scale / variable-cardinality policy:** **P0035 TERL**. [原文] 15P/4E training → 80P/20E evaluation without retraining.
- **Target selection / prioritization:** **P0035** for scalable soft selection; **P0042** for explicit team assignment.
- **Explicit assignment / capacity:** **P0042** by a wide margin. [原文] binary one-target-per-AUV matrix + prescribed per-target capacities enforced by Sinkhorn/rounding.
- **Subgroup-conditioned control:** **P0042**. [原文] assignment-aware relational re-encoding and control actor conditioned on subgroup structure.
- **Capture geometry:** **P0042** strongest: convex-hull enclosure + formation balance + positive closing advantage; **P0035** runner-up with ≥3 pursuers and angular-gap/balance criterion.
- **Learned/strategic target:** **P0033** strongest in this batch because evaders learn in the competitive training setting; P0034 tests a separately pretrained DDPG evader.
- **Real UAV evidence:** **P0033**, with an important caveat: physical validation is single-target and uses UWB localization + external computer/radio.
- **Obstacles + sensing realism:** **P0034** strongest because buildings affect both collision constraints and line of sight.

### Overall strongest CoCap competitor

**P0042 is the strongest structural competitor.**

[AI判断] It threatens the most important method-level claims: explicit learned target assignment, hard capacity, subgroup formation, assignment-conditioned pursuit and meaningful capture. P0034 is the strongest **information-assumption** competitor, while P0035 is the strongest **network/scalability** competitor.

---

# 3. What learning actually relaxes relative to classical PE/control

R-PE-01 showed that classical methods can supply strong certificates/guarantees under narrow models. R-LM-01 shows that learning's strongest contributions are elsewhere.

## 3.1 Partial/occluded sensing and target-loss memory
[原文] P0034 removes the classical convenience that target state is always known. Search and reacquisition are learned under FOV/range/building occlusion.

[AI判断] The relaxation is real, but incomplete because team-wide communication makes a detected coordinate globally available.

## 3.2 Unknown/high-dimensional coordination rules
[原文] P0033 learns concurrent exploration/tracking behavior; P0035 learns large-team relational coordination; P0042 learns assignment-conditioned 3-D maneuvering.

[AI判断] Learning replaces hand-designed low-level coordination laws effectively, especially when the joint interaction structure is too complicated for a compact analytic controller.

## 3.3 Variable entity cardinality / scale
[原文] TERL's entity-wise attention architecture scales from 15/4 training to 80/20 evaluation without retraining.

[AI判断] This is a genuine advantage over fixed-dimensional joint-state controllers/critics, but it does not by itself solve resource feasibility.

## 3.4 Coupled discrete allocation + continuous control
[原文] P0042 learns allocation preferences and continuous pursuit together under one RL objective, rather than solving an allocation module and a controller independently.

[AI判断] This is the closest learning paper to the classical assignment layer, but it relaxes **controller/module design**, not the semantics of capture feasibility.

## 3.5 Learned opponent behavior
[原文] P0033 trains learning evaders and pursuers in a competitive setting; P0034 also tests a pretrained learned evader.

[AI判断] This begins to relax fixed heuristic opponents, though this batch does not yet establish robust self-play equilibrium/opponent-population learning.

## What learning has *not* replaced

None of the four papers produces the R-PE-01 object:

> **A certificate that coalition \(S\), from the current state/information, can force or robustly achieve capture of target \(j\).**

Selection logits, attention weights, nearest-target distances, capacity \(q_j\), and terminal geometry are all useful, but they are **not capturability certificates**.

---

# 4. Target selection vs assignment vs coalition recruitment

This distinction is now mandatory for the literature map.

## 4.1 Target selection / prioritization
Definition: an agent computes which target deserves attention/preference, without necessarily enforcing team-level exclusivity or capacity.

- **P0035:** target-attention weights over evader representations. Soft preference; no binary assignment; no resource exclusivity.
- **P0033:** does not even reach this level formally; subteams are split for targets.

## 4.2 Explicit assignment
Definition: team-level decision says who is assigned to what, with constraints.

- **P0042:** explicit binary \(Z\), each AUV exactly one target, each target exactly prescribed demand \(q_j\) after hard capacity rounding.
- This is a real assignment layer.

## 4.3 Coalition/support recruitment
Definition: decide **which and how many** agents should join/leave a target-specific coalition according to target difficulty/current state and opportunity cost elsewhere.

- None of the four fully solves this.
- P0042 is closest, but subgroup size is an externally specified capacity rather than a state-dependent decision.
- TERL has emergent redistribution but no explicit coalition membership/feasibility object.

## 4.4 Capturability-aware recruitment
Definition: recruitment depends on whether an added/removed agent changes the probability/robustness/guarantee of capture.

- None of the four implements this.
- **No coalition capturability certificate appears in R-LM-01.**

---

# 5. Is P0042 a learned equivalent of classical `capturability → assignment`?

**No. It is the closest structural analog, but an important semantic layer is missing.**

### P0025 / R-PE-01
`coalition winning certificate`
→ `feasible coalition-target pair`
→ `resource-constrained assignment`.

The assignment graph/hypergraph is built only from pairs that are known, under the model, to be winning/feasible.

### P0042
`learned AUV-target preference logits`
→ `hard prescribed-capacity assignment`
→ `assignment-conditioned learned control`
→ `spatially valid terminal capture test`.

[AI判断] Sinkhorn makes the assignment **combinatorially feasible**, not **capture-feasible**. Fixed \(q_j=4\) says how many AUVs must be sent, but not whether those four are sufficient from the current positions, velocities, uncertainty, target policy and free-space geometry.

This distinction is precisely where a CoCap method contribution can still exist:

\[
C(S,j)=\text{robust/probabilistic capturability of coalition }S\text{ for target }j,
\]

\[
\Delta_i(S,j)=C(S\cup\{i\},j)-C(S,j).
\]

The recruitment/assignment objective can then trade \(\Delta_i\) against coverage loss, alternative target needs, collision risk and communication cost.

---

# 6. CoCap novelty audit

## A. Novelty claims that are now dead / should not be used standalone

1. **“Local/FOV-limited UAV pursuit sensing.”** P0034 directly covers finite range, finite angle and building occlusion.
2. **“Search + pursuit + lost-target reacquisition with MARL.”** P0034 already implements this lifecycle within a single pursuit episode.
3. **“Concurrent exploration/scouting + multi-target pursuit.”** P0033 already does this with fixed heterogeneous roles.
4. **“Transformer-based multi-target encirclement / target selection / large-team scaling.”** P0035 directly covers all three and demonstrates 80/20 zero-shot scale transfer.
5. **“Learned explicit target allocation + capacity-constrained subgroup pursuit.”** P0042 directly covers this structure.
6. **“Geometrically meaningful multi-agent capture criterion.”** P0035 and especially P0042 already go beyond distance-only capture.
7. **“Agents continue after one target is completed.”** TERL sends pursuers on to remaining targets; this alone is not novel.

## B. Partially covered, but differences remain

### Local sensing
- P0034: local **discovery**, but then target coordinates are shared team-wide.
- P0035: teammates/obstacles local, targets global.
- P0042: actor called local, but target positions are externally supported/team-available.

**Surviving distinction:** strict/intermittent target knowledge at execution, with uncertainty and constrained propagation.

### Persistent task lifecycle
- P0033: fixed scouts continue exploring while pursuers track.
- P0034: initial search and reacquisition, but capture terminates.
- P0035: after one target, agents pursue remaining targets; no coverage/search.
- P0042: captured subgroup freezes; no resource release.

**Surviving distinction:** `coverage/search → recruit → capture → release → return to coverage`, while nonparticipants maintain coverage and new targets may arrive.

### Assignment semantics
- P0035: soft target preference.
- P0042: hard assignment/capacity.

**Surviving distinction:** capacity based on **estimated capture feasibility**, not fixed cardinality or reward-induced crowding.

### Capture semantics
- P0042: strong instantaneous spatial/dynamic validity.
- P0035: strong 2-D angular enclosure.

**Surviving distinction:** connect current geometry to **future no-escape / robust capturability**, especially under uncertain target state and obstacles. “Meaningful capture” by itself is no longer novel.

## C. Surviving candidate gap

The original chain survives only in a narrowed, integrated form:

`persistent coverage/search`
→ `genuinely local/intermittent target detection + belief/uncertainty`
→ `learned uncertainty-aware coalition capturability`
→ `dynamic capture/support recruitment and join/leave`
→ `target-wise resource allocation`
→ `no-escape / physically meaningful capture`
→ `nonparticipants keep covering`
→ `capturing coalition is released back to coverage`
→ `repeated/changing target arrivals`.

[AI判断] No R-LM-01 paper covers this full lifecycle. However, several individual links are already occupied; CoCap's defensible novelty is the **information + coalition-feasibility + persistent lifecycle coupling**, not the parts in isolation.

---

# 7. Method implications for CoCap

## Directly reusable

1. **P0034 phase semantics and belief seed:** search / pursuit / lost-target reacquisition, last-seen point and expanding suspect region. Reuse as a target-memory/belief scaffold, but not with area-wide broadcast.
2. **P0035 variable-cardinality entity encoder:** keep entities as tokens, mask/pad variable counts, use relational attention and target-specific representations. This is useful engineering, not novelty.
3. **P0042 allocation/control decomposition:** explicit high-level allocation plus assignment-conditioned low-level control is a strong structural baseline.
4. **P0042 hard capacity projection:** Sinkhorn/rounding is useful if CoCap needs a resource-feasible assignment operator; capacity should become adaptive rather than fixed.
5. **P0042/P0035 capture diagnostics:** angular balance, convex-hull enclosure and closing margin can supplement CoCap's current success metrics and curriculum labels.

## Theory-guided extension

The strongest design hypothesis after R-PE-01 + R-LM-01 is:

\[
C(S,j)=P(\text{capture target }j\mid S,\text{belief/state, dynamics, obstacles})
\]

or a robust margin approximating a classical winning certificate.

Then:

\[
\Delta_i=C(S\cup\{i\},j)-C(S,j)
\]

becomes a **support-agent marginal capturability gain**.

A practical recruitment utility should subtract:
- coverage opportunity cost of agent \(i\);
- value of alternative targets;
- safety/collision cost;
- communication/uncertainty cost.

[AI判断] This is stronger than copying P0035 target attention or P0042 fixed-capacity assignment because it makes **how many/support whom** depend on capture feasibility.

## Do not copy

- P0033 fixed scout/tracker identities and manually split target subteams.
- P0034 area-wide reliable communication / instant target-coordinate broadcast.
- P0035 global active-target broadcast.
- P0042 externally supported target positions, exact total supply=demand, fixed \(q_j\), and frozen post-capture subgroups.
- Any terminal geometric condition treated as though it were a classical strategy guarantee.

---

# 8. Focused search decision

**Yes, but only a narrow focused search is now justified; do not reopen broad MARL pursuit search.**

Highest-value search gaps:
1. partial-observation / belief-space **coalition capturability + assignment**;
2. dynamic learned coalition formation with **join/leave/release** and state-dependent coalition size;
3. multi-target capture/resource allocation under **constrained target-state communication** and repeated arrivals.

Before launching these, MASTER should first inspect existing canonical seeds where applicable (e.g. P0026/P0029 for richer classical certificates and P0037/P0038 only in their scheduled batch).

---

# 9. Strongest CoCap competitors

1. **P0042 — strongest overall structural competitor:** explicit learned allocation, hard capacity, subgroup-conditioned pursuit, spatially valid capture.
2. **P0034 — strongest sensing/task-assumption competitor:** literal finite FOV/range/occlusion + search/reacquisition.
3. **P0035 — strongest scaling/network competitor:** Transformer relational reasoning + target prioritization + 15/4→80/20 zero-shot scaling.
4. **P0033 — strongest concurrent exploration/tracking + real-UAV predecessor:** but with fixed roles/manual subteams and offboard/UWB deployment.

---

# 10. Novelty impact

[AI判断] The CoCap story must shrink from a broad “multi-UAV local-sensing Transformer with target selection and capture” claim to a more precise systems/method statement:

> **learn capture-feasibility structure online under genuinely local/intermittent target information, use it to recruit/release target-wise coalitions while preserving persistent coverage, and execute meaningful capture under dynamic arrivals.**

This is still a **candidate gap**, not yet a proven novelty claim. The focused search above is needed before freezing paper-level novelty wording.

---

# 11. FOLLOW-UP PAPERS

No new paper is promoted directly into the canonical queue by this READ. Candidate leads for MASTER/future focused SCREEN only:

- **Yang et al., 2023, “Large scale pursuit-evasion under collision avoidance using deep reinforcement learning” (IROS 2023)** — direct TERL predecessor for large-scale multi-target PE.
- **Du et al. [P0034 ref. 43], communication-constrained multi-UAV pursuit in urban obstacles** — bibliographic normalization deferred; inspect only if constrained communication becomes a primary claim.
- **Goarin & Loianno (2024) graph-based goal assignment** and **Dai et al. (2025) RL heterogeneous task allocation** — citation leads from P0042; inspect only in a focused allocation/recruitment search.

---

# 12. PROJECT_PROTOCOL handoff

## NEW PAPERS
- None added to canonical index in this child READ.

## UPDATED PAPERS
- P0033 — deep READ complete; fixed role classes/manual subteams and tracking semantics confirmed.
- P0034 — deep READ complete; literal FOV/occlusion and team-wide post-detection sharing confirmed.
- P0035 — deep READ complete; global active-target broadcast, soft target selection and zero-shot scale generalization confirmed.
- P0042 — deep READ complete; hard capacity assignment, allocation-conditioned control and spatial capture criterion confirmed.

## MUST READ
- P0033, P0034, P0035, P0042 — **completed in R-LM-01**. MASTER should update canonical reading states.

## MAP
- P0033: concurrent fixed-role exploration + multi-target tracking predecessor.
- P0034: limited-FOV search/reacquisition predecessor.
- P0035: scalable multi-target Transformer/selection predecessor.
- P0042: explicit capacity assignment + subgroup-control predecessor.

## ARCHIVE
- None.

## TAXONOMY CHANGES
- Add explicit separation of:
  1. `local detection` vs `post-detection target knowledge`;
  2. `target selection/preference` vs `explicit assignment` vs `coalition recruitment`;
  3. `capacity-feasible assignment` vs `capturability-feasible assignment`;
  4. `instantaneous geometric capture condition` vs `strategy-guaranteed capturability/no-escape`;
  5. `continue to remaining targets` vs `post-capture release/return to coverage`.

## SEARCH GAPS
- belief/uncertainty-aware coalition capturability under local sensing;
- dynamic join/leave coalition formation with state-dependent capacity;
- constrained-communication multi-target assignment/capture with repeated arrivals.

## CONFLICTS / UNCERTAINTIES
- **P0033 wording:** paper calls its method “autonomous heterogeneous role assignments,” but implementation exposes predefined role classes/rewards and fixed counts; no dynamic gating/role-switch mechanism was found. Treat as terminology inflation unless new evidence appears.
- **P0035 \(r_{percept}\):** fixed perceptual radius is defined, but no numeric value was identified in the main paper. Do not invent one.
- **P0042 SCREEN CORRECTION:** strict target-sensing assumption is no longer unresolved. Full text Assumption 1 says target positions are available through external support, so “local observation” must not be interpreted as local target sensing.
- **P0042 count scaling:** 8/2→12/3 scalability is reported, but unlike TERL the paper does not explicitly say this is zero-shot without retraining. Do not claim zero-shot generalization without further evidence.

## Strongest CoCap competitors
- Overall: P0042.
- Sensing: P0034.
- Scale/Transformer: P0035.
- Concurrent exploration + real UAV: P0033.

## Method implications
- Keep \(C(S,j)\) / \(\Delta_i\) as the leading theory-guided extension hypothesis.
- Use P0042 as the strongest allocation/control baseline concept, but replace fixed \(q_j\) with capturability-aware adaptive demand/recruitment.
- Treat Transformer/GAT/Sinkhorn as implementation components, not headline novelty.

## FOLLOW-UP PAPERS
- See Section 11. No follow-up was searched or queued in this child session.
