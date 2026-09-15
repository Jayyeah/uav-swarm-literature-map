# TASK — FS-LIFE-01 — Post-Capture Release / Return-to-Coverage Lifecycle Search

## Role
Focused SEARCH child task for the UAV Swarm Pursuit / Encirclement Literature Map.

This is **not** a new broad encirclement or MARL search. R-PE-01, R-LM-01 and R-CE-01 already establish the main theory, closest-learning and classical-control boundaries.

## Core research question

Has prior work already implemented or formally analyzed the event-driven lifecycle:

`persistent patrol/coverage/search`
→ `target/threat detection`
→ `temporary pursuit/capture subgroup formation`
→ `capture/task completion`
→ `coalition/role dissolution or resource release`
→ `return to patrol/coverage`
→ `ready for repeated/changing target arrivals`?

The crucial distinction is **task-completion-triggered resource cycling**, not merely concurrent monitoring and pursuit.

## Primary search themes

### A. Post-capture release / return to patrol
- multi-robot post-capture return to patrol
- pursuit task completion coalition release coverage
- target capture resume surveillance multi-robot
- encirclement completion return to coverage
- interception completion resume patrol swarm
- capture then resume monitoring multi-agent

### B. Coalition / role dissolution and reassignment
- dynamic coalition formation dissolution pursuit capture
- role release after target capture multi-agent
- reassignment after interception multi-robot
- task-triggered subgroup join leave pursuit
- coalition dissolution after target neutralization robot
- dynamic pursuer allocation after capture

### C. Repeated / recurring threats
- persistent swarm defense repeated intruders
- patrol pursuit repeated target arrivals multi-robot
- persistent surveillance intrusion interception repeated
- coverage interception recurring targets
- repeated target appearance multi-robot pursuit patrol
- persistent perimeter defense robot pursuit intruder

## Cross-domain terms allowed

Do not restrict to UAV only. Include, when structurally relevant:
- multi-robot systems
- UGV / USV / AUV
- swarm surveillance / guarding / perimeter defense
- persistent monitoring
- intrusion response
- dynamic task allocation / coalition formation

Cross-domain papers are valuable if the lifecycle semantics match.

## Must distinguish

Do not count the following as success unless the missing lifecycle links are explicit:

1. `monitoring + encirclement concurrently` without task completion — P0010 already covers this class.
2. fixed scouts continuing exploration while fixed pursuers track — P0033 already covers this class.
3. agents moving to another already-known target after encirclement — P0035 already covers this class.
4. dynamic team cardinality robustness — P0008 already covers add/remove robustness.
5. one-shot interception/capture ending the episode — P0012/P0034 class.
6. generic task allocation without capture-triggered release.
7. generic patrol-to-pursuit switching without a return/recovery transition.

A strong hit should contain at least one of:
- explicit capture/completion event;
- subgroup/role resource release after completion;
- return/resume patrol/coverage/search;
- repeated threat/task arrivals with repeated cycling.

## Metadata / evidence to capture

For every retained candidate:
- exact task lifecycle;
- target count / arrivals;
- whether capture is terminal locally or globally;
- whether nonparticipants keep patrolling/covering;
- how pursuit subgroup is formed;
- whether subgroup size/membership is dynamic;
- what happens immediately after capture;
- whether resources are released/reassigned;
- whether return-to-patrol/coverage is explicit;
- repeated/new target support;
- sensing/communication assumptions;
- classical/optimization/behavior-based/RL method family;
- simulation / real experiment;
- structural relevance to CoCap;
- exact evidence location where possible.

## Search discipline

- Maximize recall inside this narrow lifecycle intersection.
- Use publisher databases, IEEE/ScienceDirect/Springer/arXiv/Google Scholar-style web search, backward/forward chaining.
- Search synonyms aggressively: patrol, surveillance, monitoring, guarding, coverage, intrusion response, capture, intercept, neutralize, task completion, release, dissolve, reassignment, resume.
- Do not drift into generic target tracking or generic multi-robot task allocation.
- Record exact queries and source provenance.
- Deduplicate by DOI/arXiv/bibliographic identity.
- Do not assign `Pxxxx`.
- Do not edit canonical files.
- Do not deep READ papers in this SEARCH round.

## Stop condition

Stop when:
- multiple query families/chaining rounds return mostly already-seen papers or false-positive lifecycle patterns; and
- the presence/absence of explicit post-capture release/recovery has a defensible first-pass boundary.

Do not stop merely after finding a fixed number of papers.

## Output

Write one SEARCH handoff under:

`searches/lifecycle-recovery/`

Suggested path:

`searches/lifecycle-recovery/SR-20260915-LIFE01.md`

Use the latest SEARCH handoff template if present.

The handoff must include:
- search provenance and exact queries;
- candidate table;
- explicit lifecycle fields;
- strongest direct hits;
- important near-misses / false positives;
- preliminary MUST READ / MAP / ARCHIVE suggestions (not canonical decisions);
- whether post-capture release/return-to-coverage appears mature, rare, or still unclosed;
- recommended SCREEN queue;
- remaining gaps / saturation assessment.

Final chat report:
- handoff path;
- commit SHA;
- strongest 3–8 lifecycle hits;
- whether any paper directly threatens `capture → release → return to coverage → repeated arrivals`;
- recommended SCREEN subset.

Stop after SEARCH. Do not start SCREEN or READ.
