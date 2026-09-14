# LITERATURE MAP v0.2

> MASTER merge after first-wave Search rounds CE01 / PE01 / LM01, 2026-09-14.
> Status is **first-wave map**, not final screening or reading synthesis. Representative IDs below are indexed seeds; many additional candidates remain in Search handoffs.

## Map conventions
- Coverage: `UNSEARCHED / SEARCHING / PARTIAL / SATURATED`
- Evidence discipline: paper facts require `[原文]` or `[Web核验]`; map interpretation is `[AI判断]`.
- Encirclement, adversarial PE, allocation, and learning are kept distinct unless a paper explicitly bridges them.
- `MUST READ` in the index remains provisional until SCREEN confirms assumptions.

---

# 1. Multi-Agent / UAV Swarm Foundations
First-wave searches were task-centered rather than foundation-centered. These nodes remain intentionally open.

## 1.1 Distributed control & consensus
**Coverage:** UNSEARCHED

## 1.2 Formation / flocking
**Coverage:** UNSEARCHED

## 1.3 Coverage control / Voronoi / Lloyd
**Coverage:** UNSEARCHED
**Bridge seed:** P0011 uses Voronoi partitioning for dynamic target allocation + encirclement, but this is not a coverage-control genealogy search.

## 1.4 Communication & interaction topology
**Coverage:** UNSEARCHED
**Bridge seeds:** P0005, P0031, P0038.

## 1.5 Task allocation / coalition formation
**Coverage:** UNSEARCHED
**Bridge seeds:** P0011, P0024–P0027, P0037, P0042.

## 1.6 Collision avoidance / CBF / MPC
**Coverage:** UNSEARCHED
**Bridge seeds:** P0008, P0013, P0041.

---

# 2. Classical Encirclement / Enclosing / Circumnavigation

## 2.1 Static-target encirclement
**Coverage:** PARTIAL
**Representative papers:** P0002, P0003, P0004, P0007.
**Canonical concepts:** cyclic pursuit; distributed target enclosing; bearing/range-based surrounding; invariance/reachability arguments.
**Known assumptions:** many canonical papers use prescribed standoff radius/spacing and geometric enclosure rather than an adversarial escape game.
**Open bottleneck:** translate ring/enclosure guarantees into actual no-escape/capture conditions.

## 2.2 Moving-target encirclement
**Coverage:** PARTIAL
**Representative papers:** P0005, P0006, P0008, P0012.
**Canonical concepts:** moving-target observers/estimators, relative sensing, moving circular formation.
**Open bottleneck:** maneuvering adversaries with explicit strategic escape rather than exogenous motion.

## 2.3 Distributed / local-information encirclement
**Coverage:** PARTIAL
**Representative papers:** P0004, P0005, P0007, P0008, P0009, P0010.
**Known assumptions:** “distributed” ranges from local sensing/neighbor exchange to decentralized control with target estimates; it is not automatically equivalent to CoCap-style local enemy observability.
**Open bottleneck:** local FOV/occlusion + target loss + subgroup switching under constrained communication.

## 2.4 Obstacles / boundaries / safety
**Coverage:** PARTIAL
**Representative papers:** P0008, P0013.
**Finding:** first-wave literature is much stronger on inter-agent collision/connectivity safety than on using walls/boundaries/obstacles as strategic encirclement geometry.
**Open bottleneck:** boundary-assisted capture/escape-sector geometry in clutter.

## 2.5 Multi-target encirclement & allocation
**Coverage:** PARTIAL
**Representative paper:** P0011.
**Critical distinction:** aggregate/group-target enclosure (surround centroid/convex hull) ≠ true target-wise assignment/subgroup resource allocation.
**Open bottleneck:** dynamic recruitment, coalition sizing, reassignment after capture/loss/new arrivals.

## 2.6 Persistent / post-capture task continuation
**Coverage:** PARTIAL but weak
**Representative paper:** P0010.
**Finding:** persistent concurrent monitoring/patrol + encirclement exists; explicit `search/coverage → capture → post-capture recovery → resume coverage` was not found as a mature classical-control lineage.
**CoCap relevance:** this remains a potentially important problem-level gap.

## 2.7 Limited sensing / FOV / relative-only encirclement
**Coverage:** PARTIAL
**Representative papers:** P0006, P0007, P0009, P0012, P0013.
**Finding:** range-only, bearing-only, GPS-free and explicit FOV-constrained encirclement are real subliteratures; FOV genealogy is still shallow.

## 2.8 UAV / nonholonomic / realistic dynamics
**Coverage:** PARTIAL
**Representative papers:** P0004, P0007, P0008, P0009, P0012.
**Open bottleneck:** combine realistic UAV dynamics, strict local sensing, clutter, multi-target allocation and persistent tasks in one system.

---

# 3. Pursuit–Evasion (PE)

## 3.1 Classical differential games
**Coverage:** PARTIAL-to-strong first-wave
**Representative papers:** P0014, P0015.
**Canonical concepts:** games of kind/degree, Isaacs condition, barriers, open-loop vs feedback solution concepts.
**Warning:** “capture” in PE means a strategic terminal event; it is not interchangeable with geometric enclosing.

## 3.2 Reach-avoid / HJI / viability
**Coverage:** PARTIAL-to-strong
**Representative papers:** P0018, P0019, P0024.
**Canonical concepts:** HJI reachable/winning sets; viscosity solutions; target-vs-avoid objectives; pairwise reachability decomposition.
**Open bottleneck:** high-dimensional/local-information/heterogeneous dynamics and viability genealogy remain incomplete.

## 3.3 Capture / winning / dominance regions
**Coverage:** PARTIAL-to-strong
**Representative papers:** P0020, P0021, P0023.
**Finding:** capture region, winning region, reach-avoid set and dominance region are not synonyms; information pattern and obstacles can change the claim.

## 3.4 Apollonius geometry / interception
**Coverage:** PARTIAL-to-strong
**Representative paper:** P0021.
**Finding:** clean Apollonius results depend strongly on simple motion, speed ratio, full information, obstacle-free geometry and capture-radius assumptions.
**Open bottleneck:** local/noisy sensing, nonholonomic vehicles, positive capture radius and obstacles.

## 3.5 Multi-pursuer single-evader
**Coverage:** PARTIAL-to-strong
**Representative papers:** P0022, P0023, P0028.
**Finding:** speed disadvantage is not by itself decisive: favorable initial enclosure/cardinality/environment topology can restore capture guarantees.

## 3.6 Multi-pursuer multi-evader
**Coverage:** PARTIAL-to-strong
**Representative papers:** P0024, P0026, P0027.
**Open bottleneck:** NvM + obstacles + partial information + realistic UAV dynamics.

## 3.7 PE task allocation / coalition assignment
**Coverage:** PARTIAL-to-strong
**Representative papers:** P0024, P0025, P0026, P0027, P0029.
**Clear genealogy:** pairwise winning/capture certificates → matching / binary assignment / coalition allocation → guidance.
**CoCap relevance:** strongest classical/theoretical source for principled support recruitment and target allocation.

## 3.8 Obstacles / constrained environments / environmental dynamics
**Coverage:** PARTIAL
**Representative papers:** P0020, P0022, P0024, P0029.
**Open bottleneck:** unknown/dynamic/nonconvex environments and asymmetric mobility constraints.

## 3.9 Partial / asymmetric information PE
**Coverage:** PARTIAL and NOT SATURATED
**Finding:** first-wave search validates this as a real branch, but local FOV, bearing/range-only, delays/noise, belief-state/incomplete-information, deception and communication-limited team guarantees need a dedicated round.

---

# 4. Learning-Based Pursuit / Encirclement

## 4.1 Value-based / minimax / distributional lineage
**Coverage:** PARTIAL
**Finding:** pursuit-specific Q-learning exists, but a structurally important IQN/distributional pursuit lineage was not established in LM01.
**Gap:** do not backfill with generic DQN/IQN papers.

## 4.2 Actor–critic: DDPG / SAC / related
**Coverage:** PARTIAL
**Representative papers:** P0031, P0032, P0039.
**Finding:** learning is used for continuous cooperative control, communication/opponent modeling and decentralized execution; TD3-specific structural lineage remains thin.

## 4.3 PPO / MAPPO and on-policy MARL
**Coverage:** PARTIAL
**Representative papers:** P0036.
**Finding:** useful for partially observed UAV pursuit and curriculum/environment adaptation; generic MAPPO use alone is not a contribution.

## 4.4 Value decomposition: QMIX / variants
**Coverage:** PARTIAL
**Representative papers:** P0037, P0038.
**Finding:** strongest pursuit-specific value-decomposition work injects game geometry/roles or local graph perception rather than merely replacing the backbone.

## 4.5 CTDE & centralized critics
**Coverage:** PARTIAL
**Representative papers:** P0031, P0034, P0038.
**Warning:** decentralized execution ≠ local sensing ≠ communication-free execution.

## 4.6 Graph / GNN / GAT MARL
**Coverage:** PARTIAL
**Representative papers:** P0034, P0038, P0042.
**Finding:** graph aggregation is increasingly used for variable neighborhoods/local observation and allocation.

## 4.7 Transformer / attention-based MARL
**Coverage:** PARTIAL
**Representative papers:** P0035, P0036.
**Finding:** Transformer/attention matters when it addresses variable team/target cardinality, prediction or entity aggregation; architecture choice alone is not sufficient novelty.

## 4.8 Learned communication / local messaging
**Coverage:** PARTIAL
**Representative papers:** P0031, P0039.
**Open bottleneck:** rigorous separation of message content/range from globally shared target state.

## 4.9 Role / task / target allocation
**Coverage:** PARTIAL
**Representative papers:** P0033, P0035, P0037, P0042.
**Critical distinction:** heterogeneous fixed roles, learned target selection, deterministic external assignment and differentiable learned allocation must be tracked separately.

## 4.10 Hierarchical / modular policies
**Coverage:** PARTIAL
**Representative paper:** P0042 as an allocation/control modular competitor.
**Finding:** multiple pursuit papers now decompose allocation, maneuver and low-level control; the branch is real.

## 4.11 Imitation / self-supervision / pretraining
**Coverage:** PARTIAL
**Finding:** pursuit-specific examples exist, but first-wave indexed set prioritizes stronger structural nodes. Further screening should track whether pretraining solves sparse exploration/perception rather than just accelerates training.

## 4.12 Self-play / adversarial curriculum
**Coverage:** PARTIAL
**Representative paper:** P0040.
**Finding:** strategic learned opponents + real UAV execution are emerging, but usually 1v1; swarm/multi-target overlap is weak.

## 4.13 Sim-to-real / real UAV deployment
**Coverage:** PARTIAL
**Representative papers:** P0032, P0033, P0036, P0040.
**Open question:** onboard vs offboard inference, motion-capture/global target state and communications need SCREEN-level verification.

## 4.14 Safety-constrained / CBF-RL pursuit
**Coverage:** PARTIAL
**Representative paper:** P0041.
**Taxonomy action:** promoted from provisional to first-class node after independent pursuit-specific 2025–2026 evidence.

## 4.15 Model-based / world-model / opponent-modeling pursuit RL
**Coverage:** PARTIAL / provisional
**Representative paper:** P0039.
**Taxonomy action:** retain as provisional node; one strong 2026 multi-agent paper plus model-based interception evidence suggest a real frontier, but saturation is low.

---

# 5. CoCap-Near Problems

## 5.1 Multi-UAV + multi-target pursuit/encirclement
**Coverage:** PARTIAL
**Strongest indexed neighbors:** P0033, P0035; cross-domain P0042.
**Current reading hypothesis:** no first-wave paper yet combines CoCap's full assumption bundle.

## 5.2 Local enemy sensing / partial observability
**Coverage:** PARTIAL
**Strongest indexed neighbors:** P0009, P0034, P0038, P0036.
**Novelty risk:** local sensing itself is not novel; strict FOV/occlusion pursuit already exists.

## 5.3 Decentralized execution + constrained communication
**Coverage:** PARTIAL
**Strongest indexed neighbors:** P0032, P0033, P0038.
**Open issue:** SCREEN must normalize what each paper means by “decentralized.”

## 5.4 Dynamic capture / support / coverage roles
**Coverage:** PARTIAL but weak
**Closest seed:** P0033 has scout/tracker heterogeneity; it does not yet establish the full dynamic coverage-support-capture switching chain.
**Potential gap:** dynamic support recruitment while other agents continue coverage remains undercovered.

## 5.5 Target allocation + encirclement gap allocation
**Coverage:** PARTIAL
**Strongest indexed neighbors:** P0011, P0025, P0026, P0035, P0037, P0042.
**Research opportunity:** combine PE winning/capture certificates with learned/local target-support allocation.

## 5.6 Search / coverage → detection → capture
**Coverage:** PARTIAL but weak
**Closest indexed neighbor:** P0033.
**Finding:** local-FOV pursuit and scout/tracker roles exist separately; a persistent distributed coverage→detection→capture loop remains uncommon.

## 5.7 Capture → post-capture coverage recovery
**Coverage:** NOT SATURATED / very weak
**Closest indexed neighbor:** P0010 covers concurrent monitoring/patrol + encirclement, not the same post-capture recovery semantics.
**Candidate CoCap gap:** remains credible after first-wave Search, but must survive dedicated follow-up.

## 5.8 Obstacles / boundaries / escape sectors
**Coverage:** PARTIAL
**Strongest indexed neighbors:** P0020, P0022, P0034, P0036.
**Gap:** boundary/obstacle geometry as a strategic capture resource is much less mature than obstacle avoidance.

## 5.9 Action interfaces / physical executability
**Coverage:** PARTIAL
**Strongest indexed neighbors:** P0008, P0012, P0032, P0036, P0040.
**Finding:** real or hardware-aligned UAV dynamics are now established; abstract point-mass action space cannot be assumed representative.

## 5.10 Scalability / generalization / repeated arrivals
**Coverage:** PARTIAL
**Strongest indexed neighbors:** P0035, P0039, P0042.
**Gap:** repeated arrivals + local information + persistent multi-target role reassignment remains thin.

---

# 6. Cross-Branch Bridges

## 6.1 Encirclement ↔ PE
**Coverage:** PARTIAL, genuine bridge family found
**Representative papers:** P0012, P0028, P0029.
**Key result:** geometric enclosure can become a sufficient capture mechanism only under explicit speed/cardinality/initial-geometry/dynamics assumptions. “Encirclement” alone is not a PE guarantee.
**Terminology warning:** `target-capturing`, `hunting`, `fencing`, `enclosure` and `interception` are lexical false friends unless the terminal objective/guarantee is checked.

## 6.2 Classical control / game structure ↔ RL
**Coverage:** PARTIAL
**Representative papers:** P0037, P0038, P0041.
**Finding:** the strongest bridge is not “RL replaces controller,” but classical geometry, capture certificates, CBF constraints or expert guidance shaping learning.

## 6.3 PE geometry ↔ learned allocation
**Coverage:** PARTIAL-to-strong seed set
**Representative papers:** classical P0024–P0026; learning P0037, P0038, P0042.
**Research question:** can pairwise winning/capture certificates or escape-gap geometry guide decentralized target/support recruitment under local sensing?

---

# 7. First Map Review — 2026-09-14

## 7.1 Mature enough for screening
- Classical distributed/local-information encirclement skeleton.
- HJI/reach-avoid + dominance/Apollonius PE skeleton.
- PE geometry→matching/task-assignment genealogy.
- Pursuit-specific MARL frontier around local perception, graph aggregation, target allocation and real-UAV deployment.

None is marked `SATURATED`; all three Search agents were still finding meaningful new nodes.

## 7.2 Most undercovered branches
1. Foundation layer: distributed control, coverage/Voronoi, general task allocation, collision avoidance/CBF/MPC.
2. PE partial/incomplete information with local/noisy sensing and communication limits.
3. Classical encirclement with literal boundaries/strategic obstacles.
4. Full `coverage/search → detection → support/capture → post-capture recovery` task loops.
5. Multi-target + local FOV + constrained communication + decentralized execution + real UAVs in one system.
6. Repeated arrivals and online subgroup reallocation.

## 7.3 Clear genealogies
- Cyclic pursuit → target enclosing → local/moving/nonholonomic encirclement: P0003 → P0004/P0005 → P0007/P0008.
- HJI/reach-avoid → pairwise outcomes → matching/allocation: P0018/P0019 → P0024 → P0025/P0026/P0027.
- Encirclement as geometry → formal capture bridge: P0003/P0004 → P0028/P0012.
- Pursuit MARL realism: P0032/P0033 → P0034/P0036/P0038/P0040.
- Classical geometry → theory-guided MARL: P0021/P0025 → P0037/P0038/P0042.

## 7.4 Strongest CoCap-near novelty threats / neighbors to SCREEN first
- P0033: heterogeneous multi-UAV multi-target pursuit with scout/tracker roles and real UAV demonstration.
- P0034: strict limited-FOV/occlusion multi-UAV pursuit.
- P0035: Transformer + target selection + large-scale multi-target encirclement.
- P0036: partial observation + unknown obstacles + real-UAV zero-shot deployment.
- P0038: local observation + limited communication + graph/QMIX + Apollonius structure.
- P0042: explicit differentiable target allocation + subgroup pursuit + meaningful capture geometry (AUV domain).
- P0011: classical dynamic allocation + whole-group multi-target encirclement.
- P0010: persistent monitoring/patrol + encirclement.
- P0012/P0028: strongest current encirclement→actual capture bridges.

## 7.5 Current provisional CoCap boundary
[AI判断] After Search only, CoCap should **not** claim novelty from any single ingredient: local sensing, decentralized execution, multi-target pursuit, Transformer/GNN aggregation, target allocation, obstacles, continuous UAV control, or real deployment all have precedents.

[AI判断] More defensible potential contribution space is the **combination and task semantics**:
- persistent local-information coverage/search;
- detection-triggered dynamic support/capture role recruitment;
- target-wise allocation under incomplete sensing;
- geometrically valid encirclement/capture rather than mere proximity;
- non-participating agents maintaining coverage;
- post-capture recovery/resumption;
- repeated arrivals and decentralized scalability.

This is a hypothesis for screening, not a novelty claim.

## 7.6 Claims currently unsupported
- “No prior work uses local sensing for multi-UAV pursuit.”
- “No prior work combines task allocation and encirclement.”
- “Transformer/GNN pursuit is novel.”
- “Decentralized MARL pursuit has no real-UAV precedent.”
- “Encirclement itself guarantees capture.”
- “Post-capture coverage recovery is novel” — currently **undercovered**, not proven absent.

## 7.7 Immediate next action
Complete three small screening batches listed in `READING_LEDGER.md`. Do not start broad PDF reading until those screens normalize observation, communication, target strategy, capture definition, dynamics, deployment and publication status.
