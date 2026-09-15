# LITERATURE MAP v0.4

> MASTER state after first SEARCH wave + first SCREEN wave + completed R-PE-01 deep READ. Canonical decisions here supersede earlier scaffold wording. Evidence labels: `[原文]`, `[Web核验]`, `[AI判断]`.

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

**Overall coverage:** STRONG first CoCap-relevant theory skeleton after R-PE-01; not saturated.

## 3.1 Classical differential games
**Coverage:** PARTIAL

P0015 is retained as MAP-level genealogy organizer after SCREEN. R-PE-01 confirmed that useful PE guarantees are strategy-quantified statements, not static geometric labels.

## 3.2 HJI / reachability / reach-avoid / viability
**Coverage:** PARTIAL-to-strong

Representative nodes: P0018, P0019. P0019 has now been deeply read.

[原文 + AI判断] P0019 establishes the key semantic distinction:
- ordinary reachability asks whether target entry can be forced;
- reach-avoid asks whether target entry can be forced **while satisfying state/avoid constraints up to the hitting time**;
- the guarantee is quantified through a non-anticipative strategy against every admissible competing input;
- the zero-sublevel set of the reach-avoid value function is the guaranteed feasible set.

Therefore:

`reachable set ≠ reach-avoid set ≠ dominance region ≠ generic capture region`.

[AI判断] For CoCap, a low-dimensional reach-avoid value is best treated as an oracle/teacher for **escape feasibility / capturability**, not as an online many-UAV HJI solver.

## 3.3 Capture / winning / dominance / barrier geometry
**Coverage:** PARTIAL-to-strong

Representative screened/read nodes: P0020, P0021, P0025.

Keep distinct:
- joint-state winning/reach-avoid set;
- physical-space dominance region;
- barrier separating game outcomes;
- Apollonius/Voronoi geometry under simple-motion assumptions.

[AI判断] Dominance geometry is a useful primitive for certificates, but not a certificate by itself unless linked to a specific game objective and strategy guarantee.

## 3.4 Obstacles / constrained PE
**Coverage:** PARTIAL

Representative screened node: P0020.

[AI判断] Obstacles can alter strategic dominance/interception geometry itself; they are not merely a downstream collision-avoidance add-on. P0020 remains a deferred READ before any strong boundary-/obstacle-assisted capture claim.

## 3.5 Multi-pursuer / multi-evader allocation
**Coverage:** PARTIAL-to-strong, with READ-confirmed core bridge

Representative READ nodes: P0024, P0025; organizer P0016.

R-PE-01 confirms two complementary scalability routes:

1. **pairwise numerical HJI certificate → bipartite matching** (P0024)
   - each defender–attacker pair contributes a guaranteed outcome edge;
   - a maximum matching of size `m` guarantees at least `m` attackers can be stopped;
   - this is a conservative decomposition guarantee, not an exact joint-state multiplayer optimum.

2. **coalition winning certificate → coalition-target assignment** (P0025)
   - a coalition-target edge exists only when that coalition can guarantee interception under the paper's assumptions;
   - the assignment explicitly enforces target exclusivity and pursuer resource exclusivity;
   - in P0025's specific simple-motion/convex-domain setting, the reduced 0–1 assignment is globally optimal for maximizing guaranteed intercepted evaders.

[AI判断] The important abstraction for CoCap is therefore:

`certificate → feasible edge/hyperedge → resource-constrained assignment`,

not “nearest agents go to nearest target.”

## 3.6 Encirclement → capture bridge
**Coverage:** PARTIAL but READ-confirmed

Strong node: P0028.

R-PE-01 confirms that the valid bridge is:

`speed-aware angular closure / no escape gap`
→ `maintain enclosure geometry`
→ `radial/inward contraction`
→ `enter positive capture radius`
→ `capture`,

under explicit speed/cardinality/initial-geometry/safety conditions.

[原文 + AI判断] In P0028, group occupied angle `2π` means all escape headings are covered under the modeled speed ratios. It still does **not** imply finite-time capture without inward/radial hunting. Thus:

`ring formation ≠ no-escape enclosure ≠ actual capture`.

For CoCap evaluation, this suggests separating:
1. closure / escape-gap;
2. closure maintenance;
3. contraction toward capture set;
4. terminal capture.

## 3.7 3D / heterogeneous / nonholonomic certificate extensions
**Coverage:** PARTIAL, deferred

Canonical seeds already present:
- P0026 — 3D heterogeneous multiplayer reach-avoid + matching;
- P0029 — homicidal-chauffeur/nonholonomic reach-avoid + pursuit enclosure functions.

R-PE-01 identifies these as the correct next theory extensions before launching a new broad theory search.

---

# 4. Learning-Based Pursuit / Encirclement

**Overall coverage:** PARTIAL

## 4.1 Organizing principle

[AI判断] Do not organize this branch primarily by backbone name. More informative pursuit-specific axes are **which classical assumption is relaxed or which system layer is learned**.

## 4.2 Decentralized policy execution under vehicle constraints
Representative: P0032 — MUST READ, but deferred.

[AI判断] Decentralized actors can still depend on globally complete training data, full teammate state, external localization, or offboard execution.

## 4.3 Search/tracking roles + multi-target UAV pursuit
Representative: P0033 — MUST READ / next batch.

[AI判断] Strong novelty-boundary predecessor, but roles are fixed and target state is propagated through communication; this is not dynamic coverage↔capture gating.

## 4.4 Literal local FOV / range / occlusion
Representative: P0034 — MUST READ / next batch.

[AI判断] Local enemy discovery with finite distance/view angle/building occlusion already exists. P0034 shares detected target coordinates team-wide and uses a global-state critic, so `local discovery` is not the same as `strictly local target knowledge at execution`.

## 4.5 Variable-cardinality multi-target encirclement / target prioritization
Representative: P0035 — MUST READ / next batch.

[AI判断] TERL is a major threat to broad claims about Transformer-based multi-target encirclement, target selection, or large-team generalization, but active targets are globally broadcast and evaders are heuristic.

## 4.6 Unknown clutter + physically meaningful actions + sim-to-real
Representative: P0036 — MUST READ, R-LM-02.

[AI判断] Strong baseline for physical action / deployment claims; weaker on multi-target allocation and strategic evaders.

## 4.7 Theory-/geometry-guided MARL
Representative: P0037 — MUST READ; P0038 — MAP.

[AI判断] Combining Apollonius/dominance geometry with MARL is already established. After R-PE-01, P0037 becomes especially relevant if CoCap adopts a learned capturability / escape-margin head, but it should be read after the closest-neighbor R-LM-01 batch establishes whether this bridge is central to the final story.

## 4.8 Strategic opponent learning / self-play
Representative: P0040 — MUST READ, preprint caveat.

[AI判断] Strong threat to claims around strategic learned evaders, self-play, and real-UAV pursuit; weak on swarm/multi-target allocation.

## 4.9 Explicit target allocation + subgroup pursuit/control
Representative: P0042 — MUST READ / next batch.

[AI判断] Cross-domain AUV work is structurally one of the closest competitors because it couples differentiable allocation, subgroup pursuit, local observation and capture geometry. UAV-only novelty searches are insufficient.

## 4.10 Learning review
Representative: P0030 — MAP after SCREEN.

---

# 5. Cross-Branch Bridges

## 5.1 Encirclement ↔ PE
**Coverage:** PARTIAL-to-strong first bridge

Strong nodes: P0012, P0028.

Current synthesis:
- geometric enclosure alone is insufficient;
- no-escape closure must be speed-aware and maintained;
- actual capture additionally needs contraction into the capture set;
- recent classical work already transitions from encirclement to interception, so novelty cannot rest on that transition alone.

## 5.2 Classical control / PE ↔ RL
**Coverage:** PARTIAL

Strong learning-side node: P0037; PE teacher structures now READ-confirmed from P0019/P0024/P0025/P0028.

[AI判断] A promising bridge is not “hard-code classical controller into RL,” but use theory to define stronger labels/features/priors:
- escape feasibility;
- coalition capturability;
- marginal value of a support agent;
- no-escape gap;
- near-barrier curriculum states.

RL is then tasked with relaxing exact-model, full-state, simple-motion and static-assignment assumptions.

## 5.3 PE certificate ↔ learned allocation
**Coverage:** PARTIAL-to-strong seed set

READ-confirmed chain:

`P0019 reach-avoid semantics`
→ `P0024 pairwise certificate + matching`
→ `P0025 coalition certificate + constrained assignment`
→ candidate learned approximation in CoCap.

[AI判断] Current strongest design hypothesis:

`C(S,j) = robust/probabilistic capturability of coalition S for target j`,

with support-agent marginal value

`Δ_i(S,j)=C(S∪{i},j)-C(S,j)`.

A practical CoCap utility would additionally account for coverage loss, alternative targets, collision/safety, and communication cost. This remains a **design hypothesis**, not yet an established method contribution.

---

# 6. Current CoCap Position after R-PE-01

## 6.1 Claims that are no longer defensible as standalone novelty

- local sensing / limited FOV by itself;
- decentralized execution by itself;
- multi-target pursuit by itself;
- Transformer/attention for pursuit by itself;
- graph/GAT aggregation by itself;
- target selection/allocation by itself;
- generic capability-aware assignment by itself;
- generic coalition capture by itself;
- generic encirclement-to-capture by itself;
- obstacles by themselves;
- continuous/physical UAV actions by themselves;
- real-UAV pursuit deployment by itself;
- Apollonius/game geometry + RL by itself.

## 6.2 Strongest current novelty threats / nearest neighbors

- P0033 — heterogeneous scout/tracker + multi-target UAV pursuit;
- P0034 — literal FOV/range/urban occlusion;
- P0035 — Transformer + multi-target encirclement + scale generalization;
- P0036 — unknown clutter + CTBR + real-UAV deployment;
- P0040 — strategic self-play + real UAV;
- P0042 — explicit allocation + subgroup pursuit + spatial capture geometry;
- P0010 — concurrent patrol/monitoring + encirclement classical alternative;
- P0012 — encirclement → interception classical bridge;
- P0024/P0025 — classical capability/certificate-based assignment already exists;
- P0028 — formal no-escape encirclement→capture already exists under strong assumptions.

## 6.3 Candidate CoCap gap that survives R-PE-01

[AI判断] The candidate gap **survives, but is narrower and more theory-aware**. The strongest remaining story is a lifecycle/system combination:

`persistent coverage/search`
→ `genuinely local / intermittent enemy detection`
→ `learned or uncertainty-aware capturability estimation`
→ `dynamic capture/support recruitment`
→ `target-wise resource allocation`
→ `geometrically meaningful no-escape + capture execution`
→ `non-participants continue coverage`
→ `post-capture return to coverage`
→ `repeated / changing target arrivals`

under constrained communication, realistic UAV actions, obstacles, and possibly strategic evaders.

The stronger potential narrative is no longer:

> “we introduce assignment/capture to multi-UAV pursuit.”

It is closer to:

> “we relax classical capturability/assignment assumptions by learning and using capture-feasibility structure online under local sensing, dynamic coalitions and a persistent coverage↔capture lifecycle.”

This remains a **candidate novelty**, not a proven claim.

## 6.4 Classical assumptions that learning may need to relax

R-PE-01 makes the following assumption gap explicit:

| Classical assumption | CoCap-side relaxation candidate |
|---|---|
| exact/full current state | local/intermittent detection + neighbor information + uncertainty |
| exact known dynamics/input bounds | model mismatch / learned or strategic evaders |
| simple motion / instant heading | acceleration/turn-rate/UAV action constraints |
| clean convex geometry | obstacles, boundaries, nonconvex free space |
| static one-shot assignment | dynamic join/leave, reassignment, repeated arrivals |
| binary deterministic certificate | robust/probabilistic learned score |
| independent subgames | collision, resource, coverage and communication coupling |

## 6.5 Focused gaps exposed by READ

Do not launch broad search yet. Preserve as focused follow-up questions:
- partial-observation / belief-space reach-avoid + coalition assignment;
- robust/probabilistic capturability under local sensing and model mismatch;
- dynamic coalition formation under target appearance/disappearance;
- obstacle/boundary-assisted cooperative capture;
- 3D/nonholonomic/higher-order coalition certificates.

Before searching the last item broadly, inspect existing canonical P0026/P0029.

## 6.6 Immediate next validation step

R-LM-01 should now test whether the closest learning papers already approximate any of the above structure in practice:
- P0033 — fixed scout/tracker vs true dynamic recruitment;
- P0034 — local detection vs target sharing/global critic;
- P0035 — target prioritization vs explicit coalition feasibility;
- P0042 — differentiable allocation/subgroup pursuit vs true capturability-aware dynamic recruitment.

Only after that comparison should MASTER decide whether a focused theory↔RL or partial-observation capturability search is justified.
