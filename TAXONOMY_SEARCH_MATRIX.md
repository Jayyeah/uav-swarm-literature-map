# TAXONOMY / SEARCH MATRIX v0.1

Date: 2026-09-14
Owner: MASTER
Status: planning artifact for first search wave

This document operationalizes `LITERATURE_MAP.md` into searchable branches. It does **not** replace the four canonical project-state files. Search agents use it to maximize recall; MASTER alone decides taxonomy changes and canonical merges.

## 1. Search principles

1. Keep **SEARCH → SCREEN → READ** separate.
2. Search by **problem / assumptions / mechanism**, not by algorithm names alone.
3. Keep geometric encirclement, adversarial pursuit–evasion, and learning-based pursuit as distinct literatures until evidence justifies a bridge.
4. Use both keyword expansion and genealogy expansion: surveys → seminal seeds → backward citations → forward citations → author/lab/venue chains.
5. Classics and frontier work use different evidence standards.
6. A branch is not saturated because a target paper count was reached. Saturation requires repeated keyword/citation/author/venue expansion to yield few new high-value nodes.

## 2. Cross-cutting comparison axes

Every branch should be searchable and later comparable along these axes:

- agent/target cardinality: 1v1, Nv1, NvM;
- target dynamics: static, prescribed moving, reactive, strategic/adversarial;
- pursuer dynamics/action: single/double integrator, unicycle, Dubins, UAV/quadrotor, velocity, acceleration, heading/yaw;
- observation: global state, local sensing, bearing-only, range-limited, FOV-limited, partial observability;
- communication: none, local, graph-neighbor, learned messaging, global broadcast;
- execution: centralized, distributed/decentralized, CTDE;
- environment: open plane, bounded domain, obstacles, urban/cluttered, boundary-assisted;
- objective: surround/circumnavigate, intercept/capture, reach-avoid, allocate, persistent monitoring/coverage;
- guarantees: asymptotic encirclement, finite-time capture, winning region, equilibrium, safety, none;
- deployment evidence: simulation only, HIL, robot/UAV experiment, field deployment.

## 3. Taxonomy v0.1

### A. Multi-Agent / UAV Swarm Foundations
A1. Distributed control & consensus
A2. Formation / flocking
A3. Coverage control / Voronoi / Lloyd
A4. Communication & interaction topology
A5. Task allocation / coalition formation
A6. Collision avoidance / CBF / MPC

### B. Classical Encirclement / Enclosing / Circumnavigation
B1. Static-target encirclement
B2. Moving-target encirclement
B3. Distributed / local-information encirclement
B4. Obstacle- / boundary-assisted encirclement
B5. Multi-target encirclement & allocation
B6. Persistent / post-capture task continuation
B7. Bearing-only / range-only / limited-FOV encirclement (provisional; promote only if search yield supports it)
B8. Fixed-wing / nonholonomic / UAV-dynamics encirclement (provisional)

### C. Pursuit–Evasion Foundations
C1. Classical differential games
C2. Reach-avoid / HJI / HJB / viability
C3. Capture, winning, dominance, and barrier regions
C4. Apollonius geometry / interception / dominance geometry
C5. Multi-pursuer single-evader
C6. Multi-pursuer multi-evader
C7. PE task allocation / coalition assignment
C8. Obstacles / constrained / bounded environments
C9. Partial-information / imperfect-information PE (provisional)

### D. Learning-Based Pursuit / Encirclement
D1. Value-based RL: DQN / distributional / IQN
D2. Actor–critic: DDPG / TD3 / SAC
D3. PPO / MAPPO and on-policy MARL
D4. Value decomposition: VDN / QMIX / variants
D5. CTDE / centralized critics
D6. Graph / GNN / GAT MARL
D7. Transformer / attention MARL
D8. Learned communication / local messaging
D9. Role / task / target allocation
D10. Hierarchical RL / options / modular policies
D11. Imitation / distillation / offline-to-online / pretraining
D12. Self-play / adversarial curriculum
D13. Sim-to-real / real UAV deployment
D14. Safety-constrained RL / CBF-MARL for pursuit (provisional)

### E. CoCap-Near Problems
E1. Multi-UAV + multi-target pursuit/encirclement
E2. Local enemy sensing / partial observability
E3. Decentralized execution + constrained communication
E4. Dynamic capture / support / coverage roles
E5. Target allocation + encirclement-gap allocation
E6. Search/coverage → detection → capture
E7. Capture → post-capture coverage recovery
E8. Obstacles / boundaries / escape sectors
E9. Action interfaces / physical executability
E10. Scalability / generalization / repeated arrivals

### F. Cross-Branch Bridges
F1. Encirclement ↔ PE: when does geometric enclosure imply capture/winning ability?
F2. Classical control ↔ RL: which structure is learned and which guarantees are retained/lost?
F3. PE geometry ↔ learned allocation: can winning/dominance geometry guide target assignment/support recruitment?
F4. Coverage ↔ pursuit switching: persistent search, detection, recruitment, capture, recovery.

## 4. Search matrix

| Branch | Core question | Primary term families | Required distinctions | High-value discovery routes | First-wave priority |
|---|---|---|---|---|---|
| A Foundations | What swarm-control primitives underlie pursuit systems? | distributed control, consensus, formation, flocking, Voronoi coverage, task allocation, coalition, CBF, MPC | control primitive vs pursuit-specific method | surveys, canonical textbooks/reviews, heavily reused control papers | Later wave |
| B Classical Encirclement | How do multiple agents geometrically surround/circumnavigate a target under realistic information/dynamics? | encirclement, enclosing, surrounding, circumnavigation, target enclosing, target tracking formation | surround vs capture; static vs moving; global vs local sensing; single vs multi-target | surveys/reviews; early control papers; IEEE TAC/Automatica/TRO/RAL/TCST chains | **Wave 1** |
| C PE Foundations | Under what conditions can pursuers guarantee interception/capture against a strategic evader? | pursuit-evasion, differential game, reach-avoid, HJI/HJB, viability, winning region, capture region, barrier, dominance region, Apollonius | geometric enclosure vs game-theoretic capture; 1v1 vs Nv1 vs NvM; open vs constrained domains | foundational books/papers; surveys; theory genealogy; forward citations into robotics | **Wave 1** |
| D Learning/MARL Pursuit | What uncertainty/scalability/adaptation does learning actually solve beyond classical control/game methods? | MARL pursuit, multi-agent pursuit-evasion, cooperative pursuit, UAV pursuit RL, encirclement RL, predator-prey MARL | generic MARL benchmark vs physically meaningful pursuit; centralized training vs execution; strategic vs scripted evaders | recent surveys; 2023–2026 frontier; code/real experiments; strong venue chains | **Wave 1** |
| E CoCap-near | Which papers already combine the assumptions CoCap cares about? | multi-UAV multi-target pursuit, local sensing, limited FOV, decentralized pursuit, target allocation, support role, coverage pursuit, post-capture | true overlap vs one-axis similarity | nearest-neighbor chaining from B/C/D | Wave 2 |
| F Bridges | Which theoretical/control ideas connect otherwise separate literatures? | encirclement capture guarantee, pursuit geometry allocation, coverage-pursuit switching, control-informed RL | analogy vs formally demonstrated bridge | citation crossovers and synthesis papers | Wave 2–3 |

## 5. Query-family design

Search agents should combine one **task term**, one **mechanism/theory term**, and optionally one **assumption term**.

### B — Classical Encirclement
Task terms:
- `multi-agent encirclement`
- `target encirclement`
- `target enclosing`
- `target surrounding`
- `circumnavigation target`
- `cooperative target tracking formation`

Mechanism/assumption expansions:
- distributed / decentralized / local information / neighbor-based
- moving target / unknown velocity / maneuvering target
- limited sensing / bearing-only / range-only / limited field of view
- obstacle / boundary / collision avoidance
- multi-target / task allocation / coalition
- UAV / quadrotor / unicycle / nonholonomic / fixed-wing

### C — PE Foundations
Task/theory terms:
- `pursuit evasion differential game`
- `multi-pursuer single-evader`
- `multi-pursuer multi-evader`
- `reach avoid pursuit evasion`
- `HJI pursuit evasion` / `HJB pursuit evasion`
- `winning region pursuit evasion`
- `capture region pursuit evasion`
- `barrier surface pursuit evasion`
- `dominance region pursuit evasion`
- `Apollonius circle pursuit evasion`

Assumption expansions:
- bounded domain / obstacle / convex environment
- speed ratio / equal speed / faster evader
- task assignment / coalition / matching
- partial information / limited sensing
- Dubins / nonholonomic / UAV

### D — Learning/MARL Pursuit
Task terms:
- `multi-agent reinforcement learning pursuit evasion`
- `multi-UAV cooperative pursuit reinforcement learning`
- `multi-target pursuit multi-agent reinforcement learning`
- `encirclement reinforcement learning UAV`
- `cooperative pursuit MARL`

Method/assumption expansions:
- CTDE / centralized critic / decentralized execution
- MADDPG / MATD3 / MASAC / MAPPO / QMIX / VDN
- graph neural network / GAT / Transformer / attention
- communication / message passing / limited communication
- local observation / partial observability / limited visual field
- role assignment / target assignment / coalition / hierarchical
- self-play / curriculum / adversarial training
- obstacle / urban / collision avoidance
- real UAV / sim-to-real

## 6. Database/search-system strategy

Use complementary systems rather than a single ranking source:

1. **Google Scholar** — broad recall, citation chains, historical coverage.
2. **Web of Science / Scopus** — venue/citation metadata and controlled filtering when accessible.
3. **IEEE Xplore / ACM / publisher platforms** — canonical publication records and robotics/control venues.
4. **Semantic Scholar / OpenAlex** — related-paper and citation-graph expansion; citation counts must record source/date.
5. **arXiv** — recent work and version history; verify later formal publication separately.
6. **Crossref/DOI/publisher pages** — bibliographic disambiguation.

## 7. First-wave search order

Run three independent Search sessions in parallel or near-parallel:

1. `Classical Encirclement` → B1–B8, F1 inputs.
2. `PE Foundations` → C1–C9, F1/F3 inputs.
3. `Learning / MARL Pursuit` → D1–D14, early E1–E3 candidates, F2/F3 inputs.

Do **not** start systematic deep reading in this wave. The goal is candidate discovery, terminology discovery, genealogy seeds, and search-gap detection. MASTER will deduplicate and decide the first screening batch afterward.

## 8. Promotion / revision rules for taxonomy

A provisional node is promoted when at least one of the following is observed across the search wave:

- multiple independent papers explicitly organize around that assumption/problem;
- a survey/review treats it as a recognizable subtopic;
- it forms a distinct method/assumption genealogy relevant to CoCap.

Otherwise, fold it into the nearest stable node. New taxonomy terms from child sessions must be reported under `TAXONOMY CHANGES`; child agents do not edit the global map directly.
