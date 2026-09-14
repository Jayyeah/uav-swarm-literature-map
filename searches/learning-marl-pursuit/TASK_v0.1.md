# SEARCH TASK v0.1 — Learning / MARL Pursuit

Date issued: 2026-09-14
Owner: child Search session
Parent: MASTER
Target output: `searches/learning-marl-pursuit/SR-20260914-LM01.md`

## Mission

Map the **learning-based pursuit / encirclement / MARL** literature with emphasis on what learning actually contributes beyond classical control and PE theory: partial observability, scalable coordination, target allocation, adaptive roles, communication, continuous control, obstacles, self-play/curriculum, and real deployment. This is a SEARCH pass, not a large-scale PDF reading pass.

Primary taxonomy coverage:
- D1 value-based RL
- D2 actor–critic: DDPG / TD3 / SAC families
- D3 PPO / MAPPO
- D4 value decomposition: VDN / QMIX / variants
- D5 CTDE / centralized critics
- D6 graph / GNN / GAT MARL
- D7 Transformer / attention MARL
- D8 learned communication / local messaging
- D9 role / task / target allocation
- D10 hierarchical / modular policies
- D11 imitation / pretraining / offline-to-online
- D12 self-play / adversarial curriculum
- D13 sim-to-real / real UAV deployment
- provisional D14 safety-constrained RL / CBF-MARL
- collect early candidates for E1–E3 and bridge evidence for F2/F3

## Required conceptual boundary

Prioritize papers where **pursuit, evasion, encirclement, target capture, predator-prey, or multi-UAV interception** is the actual task.

Do not fill the map with generic MARL algorithm papers merely because MADDPG/MAPPO/QMIX/etc. are used later. Generic algorithm foundations may be listed as genealogy references only when they are repeatedly necessary to interpret pursuit papers; they should not dominate this search handoff.

Differentiate:
- scripted/reactive evader vs learned/strategic evader;
- global observation vs local sensing / POMDP;
- centralized policy vs CTDE vs fully decentralized learning/execution;
- single-target vs multi-target;
- target assignment vs low-level capture control;
- benchmark predator-prey vs UAV/robot dynamics and deployment.

## Search systems

Use a complementary mix, prioritizing:
1. Google Scholar
2. IEEE Xplore / ACM / Elsevier / Springer / publisher pages
3. Web of Science or Scopus if available
4. Semantic Scholar / OpenAlex
5. arXiv for 2023–2026 frontier work and version tracing
6. GitHub/project pages for code verification only after the paper identity is established

Record every system actually used and exact queries.

## Query families

### Q1 — Broad learning-based pursuit
- `multi-agent reinforcement learning pursuit evasion`
- `cooperative pursuit multi-agent reinforcement learning`
- `reinforcement learning target encirclement multi-agent`
- `multi-robot pursuit reinforcement learning`
- `predator prey multi-agent reinforcement learning pursuit`

### Q2 — UAV / physically meaningful pursuit
- `multi-UAV cooperative pursuit reinforcement learning`
- `UAV swarm pursuit multi-agent reinforcement learning`
- `multi-UAV target encirclement reinforcement learning`
- `UAV pursuit evasion deep reinforcement learning`
- `multi-UAV multi-target pursuit reinforcement learning`

### Q3 — CTDE / actor–critic / value decomposition
- `CTDE pursuit multi-agent reinforcement learning`
- `centralized critic cooperative pursuit`
- `MADDPG pursuit evasion UAV`
- `TD3 multi-agent pursuit`
- `SAC multi-agent pursuit`
- `MAPPO pursuit evasion`
- `QMIX pursuit evasion`
- `VDN cooperative pursuit`

### Q4 — Local sensing / partial observability / communication
- `local observation multi-agent pursuit reinforcement learning`
- `limited sensing UAV pursuit reinforcement learning`
- `limited field of view multi-UAV pursuit MARL`
- `partial observability cooperative pursuit MARL`
- `communication multi-agent pursuit reinforcement learning`
- `message passing pursuit MARL`

### Q5 — Graph / attention / Transformer
- `graph neural network multi-agent pursuit reinforcement learning`
- `GAT cooperative pursuit MARL`
- `attention multi-agent pursuit reinforcement learning`
- `Transformer multi-agent pursuit UAV`
- `Transformer encirclement reinforcement learning`

### Q6 — Role / target allocation / hierarchy
- `target assignment multi-agent reinforcement learning pursuit`
- `role assignment cooperative pursuit MARL`
- `multi-target pursuit task allocation reinforcement learning`
- `hierarchical reinforcement learning pursuit multi-agent`
- `coalition formation reinforcement learning pursuit`

### Q7 — Curriculum / self-play / adversarial training
- `self-play pursuit evasion multi-agent reinforcement learning`
- `adversarial training pursuit evasion MARL`
- `curriculum learning cooperative pursuit`
- `population based training pursuit evasion`

### Q8 — Obstacles / safety / deployment
- `obstacle avoidance multi-UAV pursuit reinforcement learning`
- `urban airspace multi-UAV pursuit reinforcement learning`
- `safe multi-agent reinforcement learning pursuit UAV`
- `CBF multi-agent reinforcement learning pursuit`
- `real UAV cooperative pursuit reinforcement learning`
- `sim-to-real multi-UAV pursuit reinforcement learning`

### Q9 — Recent surveys / closest-neighbor discovery
- `survey multi-agent reinforcement learning pursuit evasion`
- `review UAV pursuit reinforcement learning`
- `review cooperative pursuit MARL`
- `multi-target pursuit MARL survey`

## Time policy

Search historically important learning-based pursuit work without a hard lower cutoff, but place active emphasis on **2023–2026** for frontier methods and nearest CoCap competitors.

For recent papers, do not reject based on low total citations. Record formal publication status, venue, citation source/date, code/real experiment evidence, and whether follow-on papers already exist.

## Citation chaining requirement

For the strongest 3–5 pursuit-specific seeds or surveys:
- inspect backward references to identify earlier pursuit-specific learning methods;
- inspect forward citations for graph/attention/communication/role/allocation/realism extensions;
- inspect author/lab chains when a group repeatedly works on the same pursuit setting;
- trace preprint → formal publication where applicable;
- verify code claims from a project/repository page rather than assuming from paper text.

## Inclusion criteria

Retain work that materially contributes to at least one of:
- pursuit/encirclement under local/partial observations;
- multi-agent coordination under CTDE or decentralized execution;
- multi-target pursuit and allocation;
- dynamic roles, recruitment, support, or hierarchy;
- learned communication / graph / attention / Transformer coordination;
- continuous control or realistic UAV/robot dynamics;
- adversarial/self-play/curriculum treatment of evaders;
- obstacles/safety constraints;
- scalability/generalization;
- real robot/UAV experiment or sim-to-real;
- a strong review that structures learning-based pursuit.

## Exclusion / downgrade criteria

Usually ARCHIVE or leave outside this branch when:
- it is generic MARL with pursuit used only as one tiny benchmark and no pursuit-specific insight;
- dynamics/observations are so abstract that no distinct pursuit problem is studied and a stronger canonical source exists;
- the paper is a near-duplicate incremental architecture swap with weak evidence;
- it makes real-UAV/local-sensing/decentralized claims not supported by the actual setup;
- publication identity is unresolved.

## What to extract at SEARCH stage

For each retained candidate:
- title, authors, year, venue/status, DOI/arXiv/URL;
- candidate taxonomy node(s);
- one- or two-sentence reason it matters;
- algorithm family and pursuit-specific mechanism;
- visible information assumptions: observation, communication, CTDE/decentralization;
- target setting and evader behavior;
- simulation vs real deployment; code availability when verified;
- citation count only with source + checked date;
- likely role: seminal application, method turning point, recent frontier, nearest competitor, survey, bridge.

Do not reconstruct full reward functions/network diagrams during this pass unless necessary to distinguish two papers.

## Specific CoCap-near flags

Tag candidates for MASTER attention when they combine two or more of:
- multi-UAV;
- multi-target;
- local enemy sensing / limited FOV;
- decentralized execution;
- constrained/local communication;
- target allocation;
- explicit pursuit/support roles;
- search or coverage before detection;
- post-capture task recovery;
- obstacles/boundaries;
- continuous physically executable action;
- scalability/generalization to varying team/target counts.

These flags indicate screening priority, **not automatic MUST READ promotion**.

## Required handoff structure

Follow `templates/SEARCH_HANDOFF_TEMPLATE.md` and end with exactly these sections:

NEW PAPERS
UPDATED PAPERS
MUST READ
MAP
ARCHIVE
TAXONOMY CHANGES
SEARCH GAPS
CONFLICTS / UNCERTAINTIES
Saturation assessment

### MUST READ discipline

A MUST READ candidate must represent a structural node: seminal pursuit-specific RL/MARL, a major coordination/partial-observation/allocation advance, strong recent frontier work, authoritative survey, real-deployment milestone, or closest credible CoCap novelty threat.

## Explicit non-goals

- Do not modify the four canonical files.
- Do not assign permanent `Pxxxx` IDs.
- Do not deep-read large PDF batches.
- Do not compare every generic MARL algorithm in detail.
- Do not settle CoCap novelty in this session.
