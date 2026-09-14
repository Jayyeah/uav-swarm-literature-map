# SEARCH TASK v0.1 — Pursuit–Evasion Foundations

Date issued: 2026-09-14
Owner: child Search session
Parent: MASTER
Target output: `searches/pursuit-evasion/SR-20260914-PE01.md`

## Mission

Map the **Pursuit–Evasion foundations** literature from classical differential games through reach-avoid, winning/capture regions, Apollonius/dominance geometry, and multi-pursuer extensions. The purpose is to recover the theoretical genealogy that tells us when capture is possible, not to deep-read all mathematics in this pass.

Primary taxonomy coverage:
- C1 classical differential games
- C2 reach-avoid / HJI / HJB / viability
- C3 capture / winning / dominance / barrier regions
- C4 Apollonius geometry / interception
- C5 multi-pursuer single-evader
- C6 multi-pursuer multi-evader
- C7 PE task allocation / coalition assignment
- C8 obstacles / constrained / bounded environments
- provisional C9 partial-information PE
- collect evidence for F1 Encirclement ↔ PE and F3 PE geometry ↔ learned allocation

## Required conceptual boundary

This branch is about **adversarial capture/reachability**: strategic pursuer and evader interaction, capture guarantees, winning sets, interception geometry, game value, barriers, or reach-avoid formulations.

Do not merge it with geometric encirclement. If a paper uses surrounding as a mechanism but the theorem/objective is capture against an evader, record it as a bridge candidate.

## Search systems

Use a complementary mix, prioritizing:
1. Google Scholar
2. publisher pages / Springer / SIAM / IEEE / Elsevier as appropriate
3. Web of Science or Scopus if available
4. Semantic Scholar / OpenAlex
5. arXiv for newer robotics/control extensions

Record every system actually used and exact queries.

## Query families

### Q1 — Classical differential games
- `pursuit evasion differential games seminal`
- `pursuit evasion differential game survey`
- `game of pursuit and evasion capture`
- `differential games pursuit evasion Isaacs`

### Q2 — Reachability / HJI / HJB / viability
- `pursuit evasion reachability HJI`
- `pursuit evasion HJB capture region`
- `reach avoid game pursuit evasion`
- `Hamilton Jacobi reachability pursuit evasion`
- `viability pursuit evasion capture`

### Q3 — Winning / capture / barrier / dominance regions
- `winning region pursuit evasion`
- `capture region pursuit evasion`
- `barrier surface pursuit evasion`
- `dominance region pursuit evasion`
- `pursuit evasion separatrix barrier`

### Q4 — Apollonius / interception geometry
- `Apollonius circle pursuit evasion`
- `Apollonius pursuit evasion multi pursuer`
- `dominance geometry pursuit evasion`
- `interception geometry pursuer evader`

### Q5 — Multi-pursuer single-evader
- `multi pursuer single evader differential game`
- `multiple pursuers one evader capture`
- `cooperative pursuit evasion multiple pursuers`
- `multi pursuer pursuit evasion winning region`

### Q6 — Multi-pursuer multi-evader / assignment
- `multi pursuer multi evader pursuit evasion`
- `pursuit evasion task assignment multi pursuer multi evader`
- `matching assignment pursuit evasion game`
- `coalition pursuit evasion multiple evaders`

### Q7 — Constrained environments
- `pursuit evasion bounded domain obstacles`
- `pursuit evasion convex environment barrier`
- `pursuit evasion obstacle environment reach avoid`
- `pursuit evasion urban environment control`

### Q8 — Dynamics / information assumptions
- `Dubins pursuit evasion`
- `nonholonomic pursuit evasion differential game`
- `UAV pursuit evasion differential game`
- `partial information pursuit evasion`
- `limited sensing pursuit evasion game`

### Q9 — Surveys / books / genealogy
- `survey pursuit evasion games robotics`
- `review multi pursuer pursuit evasion`
- `pursuit evasion differential games book`
- `reachability pursuit evasion review`

## Historical and recent policy

No lower year cutoff for foundations. Explicitly recover historically canonical theory even when old. At the same time inspect recent surveys and robotics/control developments, especially where classical geometry is adapted to multi-agent systems, constraints, assignment, or computational reachability.

Classics are judged by field-defining role, historical reuse, genealogy, and recognized venue/book status. Recent work is judged by technical importance and evidence, not raw citation count alone.

## Citation chaining requirement

For the strongest theoretical seeds/surveys:
- trace backward to the earliest canonical formulation actually used by later work;
- trace forward into robotics/multi-agent extensions;
- identify which concepts recur under different names (capture region, winning set, dominance region, barrier, reach-avoid set, etc.);
- follow major author/lab chains when they clearly define a subliterature.

The handoff should explicitly flag terminology collisions or concept equivalences as `CONFLICTS / UNCERTAINTIES` rather than asserting equivalence without evidence.

## Inclusion criteria

Retain work that materially contributes to one or more of:
- pursuit-evasion differential-game formulation;
- capture/winning condition or region;
- HJI/HJB/reachability/viability formulation;
- Apollonius/dominance/interception geometry;
- multi-pursuer cooperation;
- multi-evader assignment/coalition;
- obstacles/bounded environments;
- information/dynamics constraints relevant to robotic/UAV PE;
- a strong survey/book that organizes the theory.

## Exclusion / downgrade criteria

Usually ARCHIVE or leave outside this branch when:
- the paper is only generic path planning with a moving obstacle called an evader;
- no strategic/adversarial capture or reachability question exists;
- it is pure geometric encirclement without capture/winning analysis;
- it is a weak application paper that adds no distinct theory/problem node;
- metadata cannot be reliably resolved.

## What to extract at SEARCH stage

For each retained candidate:
- title, authors, year, venue/status, DOI/arXiv/URL;
- candidate taxonomy node(s);
- why it matters in the theoretical genealogy;
- likely formulation: differential game, reachability, geometric capture, assignment, etc.;
- visible assumptions: pursuer/evader counts, speed relation, dynamics, environment, information;
- citation count only with source + checked date;
- likely role: seminal, survey, theory turning point, bridge, recent extension.

Do not derive HJI/HJB equations or proofs in this search pass unless required only to identify the formulation.

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

A MUST READ candidate must represent a structural theory node: foundational PE formulation, canonical reachability framework, important multi-pursuer result, decisive geometry concept, authoritative survey/book, or a strong bridge into robotics.

## Explicit non-goals

- Do not modify the four canonical files.
- Do not assign permanent `Pxxxx` IDs.
- Do not deep-read proofs systematically.
- Do not force a unified theory between encirclement and PE yet.
- Do not settle CoCap novelty in this session.
