# LITERATURE MAP v0.3

> MASTER state after first SEARCH wave + first SCREEN wave. Canonical decisions here supersede earlier scaffold wording. Evidence labels: `[原文]`, `[Web核验]`, `[AI判断]`.

## Map conventions

Coverage status: `UNSEARCHED / ACTIVE / PARTIAL / SATURATED`.

Screening decisions: `MUST READ / MAP / ARCHIVE`.

A `MUST READ` paper is not automatically in the immediate READ queue; `READING_LEDGER.md` controls queue timing.

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

**Overall coverage:** PARTIAL

## 2.1 Static-target encirclement
**Coverage:** PARTIAL

Representative screened nodes: P0003, P0004.

[AI判断] Classical literature already contains distributed/local relative-measurement enclosing and formal convergence. Important lexical correction: `target-capturing` in P0003 means geometric enclosing formation, not PE-style winning/capture.

## 2.2 Moving-target encirclement
**Coverage:** PARTIAL

Representative screened nodes: P0008, P0009, P0012.

## 2.3 Distributed / local-information encirclement
**Coverage:** PARTIAL

Representative screened nodes: P0004, P0008, P0009.

[AI判断] “distributed” and “partial observation” must remain separate axes. P0008 is decentralized but reconstructs globally relevant quantities through distributed estimation. P0004 contains genuine finite sensing-range structure, but does not solve unknown-target exploration.

## 2.4 Obstacles / safety / boundaries
**Coverage:** PARTIAL

Representative screened node: P0013.

[AI判断] Current encirclement search has stronger evidence for inter-agent collision/safety than for obstacles or boundaries used as strategic enclosure geometry. Literal boundary-assisted capture remains undercovered.

## 2.5 Multi-target encirclement & allocation
**Coverage:** PARTIAL

Representative screened node: P0011.

[AI判断] Split this branch into:
- **aggregate / whole-group enclosure** — surround a target set, centroid, polygon, or outer group;
- **target-wise allocation / subgroup recruitment** — assign agents or coalitions to individual targets.

P0011 is valuable but does not by itself settle the target-wise dynamic subgroup problem.

## 2.6 Persistent / post-capture continuation
**Coverage:** PARTIAL but weak

Representative screened node: P0010.

[AI判断] P0010 is strong evidence for **concurrent patrol/monitoring + encirclement**, but not for `capture → finish → return to coverage/search`. Post-capture recovery remains a genuine gap candidate.

## 2.7 Limited sensing / FOV / bearing / range
**Coverage:** PARTIAL

Representative screened nodes: P0004, P0009, P0012.

[AI判断] Any claim that local sensing/FOV-constrained encirclement is new is untenable. The open question is the harder combination of intermittent target discovery, constrained communication, multi-target allocation, strategic evasion, and persistent task switching.

## 2.8 Realistic / nonholonomic / UAV dynamics
**Coverage:** PARTIAL

Representative screened nodes: P0004, P0008, P0009, P0012.

---

# 3. Pursuit–Evasion Foundations

**Overall coverage:** PARTIAL-to-strong first skeleton; not saturated.

## 3.1 Classical differential games
**Coverage:** PARTIAL

P0015 is retained as MAP-level genealogy organizer after SCREEN.

## 3.2 HJI / reachability / reach-avoid / viability
**Coverage:** PARTIAL-to-strong

Representative screened nodes: P0018, P0019.

[AI判断] Corrected structure:
- P0018: backward reachable set / force target entry;
- P0019: reach target while satisfying avoid/state constraints.

`reachable set` and `reach-avoid set` are not synonyms.

## 3.3 Capture / winning / dominance / barrier geometry
**Coverage:** PARTIAL-to-strong

Representative screened nodes: P0020, P0021, P0025.

[AI判断] Keep distinct:
- joint-state winning/reach-avoid set;
- physical-space dominance region;
- barrier separating game outcomes;
- Apollonius geometry under simple-motion assumptions.

P0021 is MAP after SCREEN: useful precision theorem, not a universal capture certificate.

## 3.4 Obstacles / constrained PE
**Coverage:** PARTIAL

Representative screened node: P0020.

[AI判断] Obstacles can alter strategic dominance/interception geometry itself; they are not merely a downstream collision-avoidance add-on.

## 3.5 Multi-pursuer / multi-evader allocation
**Coverage:** PARTIAL-to-strong

Representative screened nodes: P0024, P0025.

Two complementary branches are now explicit:
1. **pairwise numerical HJI certificates → matching** (P0024);
2. **analytical barriers / coalition winning regions → assignment** (P0025).

These are the strongest theory sources for CoCap-style support recruitment / allocation abstractions, but their guarantees assume much cleaner information and dynamics than CoCap.

## 3.6 Encirclement → capture bridge
**Coverage:** PARTIAL but real

Representative screened node: P0028.

[AI判断] The valid bridge is not `ring formation → capture`. P0028 supports:

`closed angular enclosure + maintained geometry + positive capture radius + suitable speed/cardinality/initial-condition assumptions + inward approach → guaranteed capture`.

This is directly relevant to escape-gap blocking and capture-support logic.

---

# 4. Learning-Based Pursuit / Encirclement

**Overall coverage:** PARTIAL

## 4.1 Organizing principle

[AI判断] Do not organize this branch primarily by backbone name. More informative pursuit-specific axes are **which classical assumption is relaxed or which system layer is learned**.

## 4.2 Decentralized policy execution under vehicle constraints
Representative: P0032 — MUST READ, but not immediate first-wave queue.

[AI判断] Decentralized actors can still depend on globally complete training data, full teammate state, external localization, or offboard execution.

## 4.3 Search/tracking roles + multi-target UAV pursuit
Representative: P0033 — MUST READ.

[AI判断] Strong novelty-boundary predecessor, but roles are fixed and target state is propagated through communication; this is not dynamic coverage↔capture gating.

## 4.4 Literal local FOV / range / occlusion
Representative: P0034 — MUST READ.

[AI判断] Local enemy discovery with finite distance/view angle/building occlusion already exists. P0034 shares detected target coordinates team-wide and uses a global-state critic, so `local discovery` is not the same as `strictly local target knowledge at execution`.

## 4.5 Variable-cardinality multi-target encirclement / target prioritization
Representative: P0035 — MUST READ.

[AI判断] TERL is a major threat to broad claims about Transformer-based multi-target encirclement, target selection, or large-team generalization, but active targets are globally broadcast and evaders are heuristic.

## 4.6 Unknown clutter + physically meaningful actions + sim-to-real
Representative: P0036 — MUST READ.

[AI判断] Strong baseline for physical action / deployment claims; weaker on multi-target allocation and strategic evaders.

## 4.7 Theory-/geometry-guided MARL
Representative: P0037 — MUST READ; P0038 — MAP.

[AI判断] Combining Apollonius/dominance geometry with MARL is already established. Novelty, if any, must lie in harder assumptions or lifecycle integration rather than geometry-plus-RL alone.

## 4.8 Strategic opponent learning / self-play
Representative: P0040 — MUST READ, preprint caveat.

[AI判断] Strong threat to claims around strategic learned evaders, self-play, and real-UAV pursuit; weak on swarm/multi-target allocation.

## 4.9 Explicit target allocation + subgroup pursuit/control
Representative: P0042 — MUST READ.

[AI判断] Cross-domain AUV work is structurally one of the closest competitors because it couples differentiable allocation, subgroup pursuit, local observation and capture geometry. UAV-only novelty searches are insufficient.

## 4.10 Learning review
Representative: P0030 — MAP after SCREEN.

---

# 5. Cross-Branch Bridges

## 5.1 Encirclement ↔ PE
**Coverage:** PARTIAL

Strong nodes: P0012, P0028.

Current synthesis:
- geometric enclosure alone is insufficient;
- actual capture depends on escape-direction closure plus dynamics/speed/capture-radius/initial geometry;
- recent classical work already transitions from encirclement to interception, so novelty cannot rest on that transition alone.

## 5.2 Classical control / PE ↔ RL
**Coverage:** PARTIAL

Strong nodes: P0037 and supporting evidence from P0038.

[AI判断] Classical theory contributes structured certificates/priors; RL contributes most where exact models and full information break down.

## 5.3 PE geometry ↔ learned allocation
**Coverage:** PARTIAL-to-strong seed set

Strong chain: P0019 → P0024/P0025 → P0037/P0042.

[AI判断] Candidate CoCap direction: replace brittle binary capturable/not-capturable edges with robust learned or uncertainty-aware capture-support scores informed by reach-avoid/escape geometry.

---

# 6. Current CoCap Position after first SCREEN wave

## 6.1 Claims that are no longer defensible as standalone novelty

- local sensing / limited FOV by itself;
- decentralized execution by itself;
- multi-target pursuit by itself;
- Transformer/attention for pursuit by itself;
- graph/GAT aggregation by itself;
- target selection/allocation by itself;
- obstacles by themselves;
- continuous/physical UAV actions by themselves;
- real-UAV pursuit deployment by itself;
- Apollonius/game geometry + RL by itself.

## 6.2 Strongest screened novelty threats / nearest neighbors

- P0033 — heterogeneous scout/tracker + multi-target UAV pursuit;
- P0034 — literal FOV/range/urban occlusion;
- P0035 — Transformer + multi-target encirclement + scale generalization;
- P0036 — unknown clutter + CTBR + real-UAV deployment;
- P0040 — strategic self-play + real UAV;
- P0042 — explicit allocation + subgroup pursuit + spatial capture geometry;
- P0010 — concurrent patrol/monitoring + encirclement classical alternative;
- P0012 — encirclement → interception classical bridge.

## 6.3 Candidate CoCap gap that survives SCREEN

[AI判断] The strongest surviving gap is a **task-lifecycle combination**, not one isolated algorithmic ingredient:

`persistent coverage/search`
→ `genuinely local enemy detection`
→ `dynamic capture/support recruitment`
→ `target-wise allocation`
→ `geometrically meaningful multi-agent capture`
→ `non-participants continue coverage`
→ `post-capture return to coverage`
→ `repeated / changing target arrivals`

under constrained communication, realistic UAV actions, obstacles, and possibly strategic evaders.

This remains a **candidate gap, not a proven novelty claim** until the READ phase and targeted follow-up searches close the strongest uncertainties.

## 6.4 Main unresolved assumptions for READ

- exact sensing/communication stack in P0008/P0009/P0010/P0012;
- theorem assumptions and team-level guarantees in P0024/P0025/P0028;
- exact communication payload/decentralization semantics in P0033;
- exact capture criterion and critic/global-state dependence in P0034;
- target broadcast / assignment semantics in P0035;
- real deployment stack in P0036/P0040;
- allocation constraints and capture definition in P0042.

## 6.5 Search gaps still open

- post-capture coverage recovery;
- strict local enemy sensing + multi-target + constrained communication + real UAV in one mature paper;
- strategic learned evaders combined with swarm/multi-target pursuit;
- local-information NvM PE guarantees;
- boundary-assisted capture / strategic obstacle geometry;
- dynamic coalition recruitment under changing/repeated targets.
