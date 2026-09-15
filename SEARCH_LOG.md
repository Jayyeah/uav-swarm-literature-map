# SEARCH LOG

This file records reproducible search history and saturation evidence.

## Status vocabulary
- `UNSEARCHED`
- `ACTIVE`
- `PARTIAL`
- `SATURATED`
- `REOPENED`

---

# Search rounds

## SR-20260914-CE01 — Classical Encirclement

**Taxonomy node(s):** B1–B8; F1 bridge candidates  
**Status before round:** UNSEARCHED  
**Search date:** 2026-09-14  
**Agent/session:** Classical Encirclement Search child

### Databases / search systems
- Broad scholarly web/index discovery
- ScienceDirect / Elsevier
- IEEE Xplore
- Wiley / IET
- Taylor & Francis
- Springer Nature
- Cambridge Core / SAGE / PubMed
- arXiv
- Semantic Scholar / OpenAlex-derived metadata (supplementary)
- Direct Google Scholar / Web of Science / Scopus: not available in this round

### Query families
- `multi-agent encirclement / target enclosing / surrounding / circumnavigation`
- moving-target + distributed/local information
- bearing-only / range-only / limited FOV
- UAV / fixed-wing / nonholonomic / 3D
- obstacle / collision / connectivity / safety
- multi-target / target allocation / coalition / dynamic reorganization
- persistent monitoring / patrol + encirclement
- survey / citation / author / venue chains

Exact queries are preserved in `searches/classical-encirclement/SR-20260914-CE01.md`.

### Filters
- Classics: no lower year cutoff
- Frontier emphasis: 2023–2026
- English
- Geometric enclosing/circumnavigation retained; pure PE/interception excluded unless explicit bridge

### Citation chaining
- Backward references: PARTIAL
- Forward citations: PARTIAL
- Related-paper graph: PARTIAL
- Key author/lab follow-up: PARTIAL
- Key venue follow-up: PARTIAL

### Yield
- Candidates reviewed: ~90 after obvious duplicates/off-topic filtering
- Retained in child handoff: 51
- Child preliminary MUST READ: 14
- Child preliminary MAP: 34
- Child preliminary ARCHIVE: 3
- MASTER admitted to canonical first-screening index: 13 structural seeds
- Cross-branch duplicate/transfer handled: learning-based encirclement candidate routed to LM branch rather than duplicated

### New terminology / keywords
`target fencing`; `target-capturing`; `circular formation`; `standoff tracking`; `encirclement hunting`; `whole-group encirclement`; `balanced fencing`; `dynamic radius`; `relative-position-only`; `communication-free circumnavigation`.

### Gaps / uncertainties
- literal environment/boundary-assisted encirclement
- post-capture recovery/return-to-coverage
- true target-wise coalition allocation vs group-centroid enclosure
- historical FOV-specific genealogy
- one-paper combination of clutter + local sensing + multi-target + realistic UAV dynamics

### Saturation judgment
`PARTIAL`

Reason: coherent genealogy recovered, but B4/B5/B6/B7 still yield clear gaps and 2024–2026 searches were still producing high-value nodes.

### Handoff
`searches/classical-encirclement/SR-20260914-CE01.md`

---

## SR-20260914-PE01 — Pursuit–Evasion Foundations

**Taxonomy node(s):** C1–C9; F1 and F3 bridges  
**Status before round:** UNSEARCHED  
**Search date:** 2026-09-14  
**Agent/session:** PE Foundations Search child

### Databases / search systems
- SIAM / IEEE Xplore / ScienceDirect / Springer / Frontiers / Taylor & Francis
- arXiv
- OpenAlex / DBLP / PubMed / CiNii / institutional pages
- Scopus citation counts only when surfaced via institutional pages
- Direct Web of Science: not available

### Query families
- Isaacs / differential games / pursuit games
- HJI / HJB / reachability / reach-avoid / viability
- capture / winning / dominance / barriers
- Apollonius / interception geometry
- multi-pursuer single-evader
- multi-pursuer multi-evader
- analytical barriers / matching / task allocation
- obstacles / bounded arenas / flow fields
- limited/asymmetric observations
- encirclement/containment → capture bridges

Exact queries are preserved in `searches/pursuit-evasion/SR-20260914-PE01.md`.

### Citation chaining
- Backward references: PARTIAL but substantive
- Forward citations: PARTIAL
- Related-paper graph: PARTIAL
- Key author/lab follow-up: DONE at SEARCH depth for four major lineages
- Key venue follow-up: PARTIAL

### Yield
- Candidates reviewed: 90+
- Retained in child handoff: 38
- Child preliminary MUST READ: 16
- Child preliminary MAP: 22
- MASTER admitted to canonical first-screening index: 16 structural seeds

### New terminology / corrections
- `capture region`, `winning region`, `reach-avoid set`, `dominance region` are not interchangeable
- `barrier` and `separatrix` need paper-specific definitions
- dominance-region claims depend on information pattern
- positive capture radius may require Cartesian-oval rather than simple Apollonius geometry
- `pursuit enclosure` in reach-avoid theory is not automatically geometric ring encirclement

### Gaps / uncertainties
- older Soviet/Russian many-pursuer genealogy
- viability/discriminating-kernel lineage
- nonholonomic/fixed-wing/3D PE
- partial/incomplete information C9
- nonconvex/dynamic/unknown obstacles
- NvM + obstacles + partial information
- graph/search PE boundary vs physical capture PE

### Saturation judgment
`PARTIAL`

Reason: first-wave skeleton is strong, but forward searches were still yielding important 2024–2026 nodes, especially information-pattern, Dubins and faster-evader containment results.

### Handoff
`searches/pursuit-evasion/SR-20260914-PE01.md`

---

## SR-20260914-LM01 — Learning / MARL Pursuit

**Taxonomy node(s):** D1–D14; early E1–E10; F2/F3  
**Status before round:** UNSEARCHED  
**Search date:** 2026-09-14  
**Agent/session:** Learning / MARL Pursuit Search child

### Databases / search systems
- ScienceDirect / IEEE / IEEE-CAA JAS / Wiley / MDPI / PubMed / DBLP / DOAJ
- institutional publication pages
- arXiv / alphaXiv
- citation/index mirrors for snapshots
- GitHub/project pages for code verification
- Direct Google Scholar / Web of Science / Scopus UI not available

### Query families
- pursuit-specific Q-learning / DQN
- DDPG / TD3 / SAC
- PPO / MAPPO
- VDN / QMIX
- CTDE / centralized critic
- local observation / limited sensing / FOV
- communication / message passing
- GNN / GAT / graph MARL
- Transformer / attention
- target/role/task allocation
- hierarchy / modular policies
- self-play / curriculum / imitation / pretraining
- CBF / safe RL
- sim-to-real / real UAV pursuit
- recent 2023–2026 formal-publication tracing

Exact queries are preserved in `searches/learning-marl-pursuit/SR-20260914-LM01.md`.

### Citation chaining
- Backward references: PARTIAL
- Forward citations: PARTIAL
- Related-paper graph: PARTIAL
- Key author/lab follow-up: PARTIAL
- Key venue follow-up: PARTIAL

### Yield
- Result records/snippets inspected: 100+
- Child handoff contains 31 numbered retained candidates (the summary count says 29; MASTER preserves this internal inconsistency as a handoff issue rather than silently rewriting it)
- Child preliminary MUST READ: 11
- Child MAP list includes additional near-MUST papers
- MASTER admitted to canonical first-screening index: 13 structural/frontier seeds

### Noise-filter rule
Generic MARL papers and benchmark-only predator–prey work were not promoted unless learning changed a pursuit-specific bottleneck such as sensing, target strategy, communication, assignment, dynamics, safety, scalability or deployment.

### Taxonomy changes accepted by MASTER
- D14 safety-constrained / CBF-RL pursuit: promoted to stable branch.
- D15 model-based / world-model / opponent-modeling pursuit: retained as provisional branch.
- theory/knowledge-guided RL: cross-cutting F2 tag rather than a separate branch.
- D9 should distinguish fixed roles, deterministic assignment, learned target selection and differentiable allocation.

### Gaps / uncertainties
- pursuit-specific VDN and TD3 lineages remain weak
- post-capture coverage/recovery almost absent
- complete coverage→detection→capture loop with local sensing remains rare
- multi-target + local FOV + constrained communication + decentralized execution + real UAV deployment not found as one mature formal work
- strategic learned evader + swarm/multi-target + real UAV rarely coincide
- “decentralized” and “real-world” claims need SCREEN-level normalization
- formal publication remains open for some recent preprints

### Saturation judgment
`PARTIAL`

Reason: strong frontier clusters were recovered, but multiple task-defining gaps remain and recent author/citation chains are still active.

### Handoff
`searches/learning-marl-pursuit/SR-20260914-LM01.md`

---

# MASTER merge note — 2026-09-14

The three Search handoffs contain 120 nominal numbered entries if LM01's actual numbering is used (51 + 38 + 31), while LM01's own summary says 29 retained. MASTER did **not** treat these counts as a clean deduplicated corpus.

Identity merge policy used:
1. DOI first;
2. formal publication preferred over substantively identical arXiv/preprint;
3. title/author/year used only as supporting identity evidence;
4. cross-branch lexical overlaps were assigned one canonical `paper_id` only when the same work was admitted;
5. first canonical admission is limited to **42 structural seeds** selected for screening, not every high-recall Search candidate.

This keeps `PAPER_INDEX.csv` useful rather than turning a first-wave high-recall candidate pool into an unreviewed canonical database.

---

## SR-20260915-LIFE01 — Focused Lifecycle Recovery

**Taxonomy node(s):** persistent mission lifecycle; dynamic coalition formation/release; patrol/coverage↔capture bridge; continual/repeated threats  
**Status before round:** focused gap opened after R-CE-01  
**Search date:** 2026-09-15  
**Agent/session:** FS-LIFE-01 focused Search child

### Narrow research question
Has prior work implemented or formally analyzed:

`persistent patrol/coverage/search`
→ `target/threat detection`
→ `temporary pursuit/capture subgroup`
→ `capture/task completion`
→ `coalition/role dissolution or resource release`
→ `return to patrol/coverage`
→ `ready for repeated/changing arrivals`?

### Query families
- post-capture return / resume / rejoin patrol or coverage
- coalition dissolution / release / reassignment after capture
- temporary coalition + pursuit/capture completion
- persistent patrol/surveillance + repeated/recurring intruders
- pop-up targets / stochastic alerts / recurring threats
- return-to-search / redeployment / resource release synonyms

Exact query strings, candidate-specific verification and chaining are preserved in `searches/lifecycle-recovery/SR-20260915-LIFE01.md`.

### Yield and MASTER admission
- **0** papers found that clearly close the entire seven-stage lifecycle in one system using the same fungible resource pool.
- **1** strict historical direct hit for an explicit apprehension-completion → resume-patrol transition: Bradshaw et al. 2008.
- **2** additional strong completion→dissolution/reuse structural hits: Liu et al. 2025 and HECTOR 2026.
- Strong repeated-event/repeated-threat evidence from Liu, HECTOR, Duarte, Chandler and Bajaj.
- MASTER admitted **9 screening candidates** as P0043–P0051; false-positive/duplicate publications remain only in the handoff.

### Key boundary corrections
- `post-capture return to patrol` by itself is **not novel**.
- `task completion → coalition dissolution → reusable agents` is **not novel**.
- `persistent patrol → pursuit → return → repeated intruders` exists without successful capture.
- repeated stochastic/arbitrary threat arrivals under patrol/defense are established.
- no retained paper at SEARCH depth clearly combines the full same-pool loop with nominal area coverage restoration after capture.

### Closest candidate roles
- P0043 — strongest structural completion→dissolve→reusable-pool + pop-up-target analogue.
- P0044 — strongest capture-specific exploration/defense + dynamic coalition competitor.
- P0045 — strongest continual-task completion→coalition-dissolution→reassignment result.
- P0046 — clearest literal apprehension→resume-patrol historical precedent.
- P0047 — clean classical patrol→event-response→return edge.
- P0048–P0051 — supporting near-miss/repeated-arrival nodes.

### Citation chaining / saturation
Backward/forward and synonym sweeps converged on the same kill-web/coalition, patrol-return, repeated-alert and perimeter-defense lineages. New results increasingly became:
1. remaining-target reassignment;
2. generic dynamic MRTA without capture-triggered transitions;
3. patrol→response without capture or without return;
4. capture→episode termination.

### Saturation judgment
`SATURATED` for this focused branch at first-pass SEARCH depth.

Reason: remaining uncertainty is now paper-internal lifecycle semantics in a small retained set, which is a SCREEN problem rather than a recall/search problem.

### Current gap judgment
`PARTIALLY SURVIVES`.

The surviving intersection is not an isolated lifecycle edge. It is the integrated coupling of:

`same fungible pool`
+ `persistent area coverage/search`
+ `target-triggered temporary capture coalition`
+ `explicit capture completion`
+ `completion-triggered release`
+ `same-agent restoration of nominal coverage`
+ `repeated arrivals`,

especially when combined with local/intermittent target belief and capturability-aware recruitment.

### Handoff
`searches/lifecycle-recovery/SR-20260915-LIFE01.md`
