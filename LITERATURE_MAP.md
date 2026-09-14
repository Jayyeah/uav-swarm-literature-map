# LITERATURE MAP v0.1

> Status: scaffold only. MASTER updates this file after merging child-agent handoffs.

## Map conventions

For each node maintain:

- **Core question**
- **Canonical concepts/methods**
- **Representative papers** (`paper_id` only after indexing)
- **Known assumptions**
- **Open bottlenecks**
- **Links to neighboring nodes**
- **CoCap relevance**
- **Coverage status**: `UNSEARCHED / SEARCHING / PARTIAL / SATURATED`

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

## 2.1 Static-target encirclement
**Coverage:** UNSEARCHED

## 2.2 Moving-target encirclement
**Coverage:** UNSEARCHED

## 2.3 Distributed / local-information encirclement
**Coverage:** UNSEARCHED

## 2.4 Obstacle- / boundary-assisted encirclement
**Coverage:** UNSEARCHED

## 2.5 Multi-target encirclement & allocation
**Coverage:** UNSEARCHED

## 2.6 Persistent / post-capture task continuation
**Coverage:** UNSEARCHED

---

# 3. Pursuit–Evasion (PE)

## 3.1 Classical differential games
**Coverage:** UNSEARCHED

## 3.2 Reach-avoid / HJI / HJB / viability
**Coverage:** UNSEARCHED

## 3.3 Capture / winning / dominance regions
**Coverage:** UNSEARCHED

## 3.4 Apollonius geometry / interception
**Coverage:** UNSEARCHED

## 3.5 Multi-pursuer single-evader
**Coverage:** UNSEARCHED

## 3.6 Multi-pursuer multi-evader
**Coverage:** UNSEARCHED

## 3.7 PE task allocation / coalition assignment
**Coverage:** UNSEARCHED

## 3.8 Obstacles / environments / constrained PE
**Coverage:** UNSEARCHED

---

# 4. Learning-Based Pursuit / Encirclement

## 4.1 Value-based RL: DQN / distributional / IQN
**Coverage:** UNSEARCHED

## 4.2 Actor–critic: DDPG / TD3 / SAC
**Coverage:** UNSEARCHED

## 4.3 PPO / MAPPO and on-policy MARL
**Coverage:** UNSEARCHED

## 4.4 Value decomposition: VDN / QMIX / variants
**Coverage:** UNSEARCHED

## 4.5 CTDE & centralized critics
**Coverage:** UNSEARCHED

## 4.6 Graph / GNN / GAT MARL
**Coverage:** UNSEARCHED

## 4.7 Transformer / attention-based MARL
**Coverage:** UNSEARCHED

## 4.8 Learned communication / local messaging
**Coverage:** UNSEARCHED

## 4.9 Role / task / target allocation
**Coverage:** UNSEARCHED

## 4.10 Hierarchical RL / options / modular policies
**Coverage:** UNSEARCHED

## 4.11 Imitation / distillation / offline-to-online / pretraining
**Coverage:** UNSEARCHED

## 4.12 Self-play / adversarial curriculum
**Coverage:** UNSEARCHED

## 4.13 Sim-to-real / real UAV deployment
**Coverage:** UNSEARCHED

---

# 5. CoCap-Near Problems

## 5.1 Multi-UAV + multi-target pursuit/encirclement
**Coverage:** UNSEARCHED

## 5.2 Local enemy sensing / partial observability
**Coverage:** UNSEARCHED

## 5.3 Decentralized execution + constrained communication
**Coverage:** UNSEARCHED

## 5.4 Dynamic capture / support / coverage roles
**Coverage:** UNSEARCHED

## 5.5 Target allocation + encirclement gap allocation
**Coverage:** UNSEARCHED

## 5.6 Search / coverage → detection → capture
**Coverage:** UNSEARCHED

## 5.7 Capture → post-capture coverage recovery
**Coverage:** UNSEARCHED

## 5.8 Obstacles / boundaries / escape sectors
**Coverage:** UNSEARCHED

## 5.9 Action interfaces / physical executability
**Coverage:** UNSEARCHED

## 5.10 Scalability / generalization / repeated arrivals
**Coverage:** UNSEARCHED

---

# 6. Cross-Branch Bridges

## 6.1 Encirclement ↔ PE
Questions:
- When is geometric enclosure sufficient for actual capture/winning guarantees?
- How do speed ratio, escape sectors, and interception geometry modify ring-based encirclement?

**Coverage:** UNSEARCHED

## 6.2 Classical control ↔ RL
Questions:
- Which modules are replaced by learning?
- Which guarantees are lost or gained?
- Where do geometric/control priors improve sample efficiency or safety?

**Coverage:** UNSEARCHED

## 6.3 PE geometry ↔ learned allocation
Questions:
- Can Apollonius / capture-region / escape-gap ideas guide target assignment or support recruitment?

**Coverage:** UNSEARCHED

---

# 7. Current CoCap Position

> MASTER updates only after evidence accumulates.

## 7.1 Strongest nearest neighbors
TBD

## 7.2 Strongest classical alternatives / baselines
TBD

## 7.3 Potential novelty threats
TBD

## 7.4 Candidate research gaps
TBD

## 7.5 Claims currently unsupported
TBD
