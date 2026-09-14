# SEARCH TASK v0.1 — Classical Encirclement

Date issued: 2026-09-14
Owner: child Search session
Parent: MASTER
Target output: `searches/classical-encirclement/SR-20260914-CE01.md`

## Mission

Map the **classical geometric encirclement / enclosing / circumnavigation** literature with high recall. The goal is to identify terminology, seminal lineages, representative control mechanisms, assumption families, and recent extensions. Do not turn this into a deep-reading session.

Primary taxonomy coverage:
- B1 static-target encirclement
- B2 moving-target encirclement
- B3 distributed / local-information encirclement
- B4 obstacle- / boundary-assisted encirclement
- B5 multi-target encirclement & allocation
- B6 persistent / post-capture continuation
- provisional B7 limited-sensing variants
- provisional B8 UAV/nonholonomic dynamics
- collect evidence relevant to F1 Encirclement ↔ PE, but do not merge the literatures

## Required conceptual boundary

Treat as **encirclement** work when the main object is geometric surrounding, enclosing, circumnavigation, spacing/phase regulation around a target, or a target-centered formation.

Do not silently classify a paper as encirclement when it only studies interception/capture in a pursuit–evasion game. Record crossover papers explicitly as bridge candidates.

## Search systems

Use a complementary mix, prioritizing:
1. Google Scholar
2. IEEE Xplore / publisher pages
3. Web of Science or Scopus if available
4. Semantic Scholar / OpenAlex
5. arXiv for recent extensions

Record every system actually used.

## Query families

Run multiple variants from each family; record exact queries in the handoff.

### Q1 — Core vocabulary
- `multi-agent encirclement target`
- `target encirclement cooperative control`
- `multi-robot target enclosing`
- `target surrounding distributed control`
- `circumnavigation target multi-agent`
- `cooperative target tracking formation encirclement`

### Q2 — Moving target / unknown motion
- `moving target encirclement multi-agent`
- `maneuvering target enclosing distributed`
- `unknown target velocity circumnavigation control`

### Q3 — Local information / sensing assumptions
- `distributed encirclement local information`
- `decentralized target enclosing neighbor information`
- `bearing-only target encirclement`
- `range-only circumnavigation target`
- `limited field of view encirclement multi-agent`

### Q4 — Dynamics / physical agents
- `UAV target encirclement control`
- `quadrotor target encirclement`
- `unicycle circumnavigation target`
- `nonholonomic target enclosing`
- `fixed-wing UAV encirclement target`

### Q5 — Obstacles / boundaries / safety
- `target encirclement obstacle avoidance`
- `encirclement bounded environment multi-agent`
- `circumnavigation collision avoidance multi-agent`

### Q6 — Multi-target / allocation
- `multi-target encirclement multi-agent`
- `target allocation encirclement multi-robot`
- `coalition formation target encirclement`

### Q7 — Reviews and genealogy
- `review multi-agent encirclement target`
- `survey circumnavigation target multi-agent`
- `review target enclosing cooperative control`

## Historical and recent policy

Do not impose a lower year cutoff for seminal work. For recent extensions, actively inspect roughly 2023–2026.

Classical candidates should be retained when they are repeatedly cited, field-defining, early introductions of a key mechanism/assumption, or parents of a clear later lineage.

Recent candidates should be retained based on technical relevance, venue/formal status, citation velocity when available, code/real experiments, and whether they address a recognized bottleneck. Low raw citations alone are not a rejection reason.

## Citation chaining requirement

For the strongest 3–5 seed papers or surveys discovered:
- inspect backward references for earlier canonical work;
- inspect forward citations for major extensions;
- follow at least the most recurrent author/lab or venue chain;
- note whether the same papers recur across independent query families.

This is a first wave, so do not claim saturation unless evidence is unusually strong. Usually report `NOT SATURATED` or `PARTIAL` with the specific remaining branches.

## Inclusion criteria

Retain papers that materially contribute to at least one of:
- geometry of surrounding/circumnavigation;
- distributed/local-information control;
- moving-target handling;
- multi-target allocation/coalitions;
- realistic vehicle dynamics;
- obstacle/boundary/safety handling;
- persistence or task continuation after enclosure;
- a strong survey that organizes the field.

## Exclusion / downgrade criteria

Usually ARCHIVE or leave outside this branch when:
- encirclement is only a loose metaphor and no surrounding geometry is present;
- the work is generic formation control with no target-centered enclosing objective;
- the paper is purely PE interception/capture without an encirclement formulation;
- the work is a weak duplicate of a stronger paper in the same lineage;
- metadata/publication status cannot be resolved after reasonable checking.

## What to extract at SEARCH stage

For each retained candidate, capture only enough to support later screening:
- title, authors, year, venue/status, DOI/arXiv/URL;
- candidate taxonomy node(s);
- one- or two-sentence reason it matters;
- likely method family;
- visible assumptions if easy to establish from abstract/metadata;
- citation count only when source + check date are recorded;
- whether it looks seminal, survey, representative, recent frontier, or bridge paper.

Do not derive detailed controller equations unless needed to disambiguate the paper.

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

Do not promote merely because a paper is highly similar to CoCap. A MUST READ candidate must state the structural node it represents, e.g. seminal distributed encirclement, canonical moving-target formulation, important survey, or major recent realism extension.

## Explicit non-goals

- Do not modify `LITERATURE_MAP.md`, `SEARCH_LOG.md`, `PAPER_INDEX.csv`, or `READING_LEDGER.md`.
- Do not assign permanent `Pxxxx` IDs.
- Do not start systematic PDF deep reading.
- Do not attempt to settle CoCap novelty in this session.
