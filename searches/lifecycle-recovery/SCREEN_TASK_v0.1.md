# S-LIFE-01 — Focused Lifecycle Screening Task v0.1

## Purpose

SCREEN the nine FS-LIFE-01 candidates admitted as P0043–P0051. This is not a new search and not a full READ batch.

The decision to close is whether CoCap's lifecycle gap is `DEAD`, `PARTIALLY SURVIVES`, or `STRONGLY SURVIVES` after verifying paper-internal semantics.

## Papers

- P0043 — Liu 2025, *Construction of kill webs with heterogeneous UAV swarms in dynamic contested environments*
- P0044 — Chen, Tang & Guo 2024, *Accelerated K-Serial Stable Coalition for Dynamic Capture and Resource Defense*
- P0045 — Wang et al. 2026, *HECTOR: Human-Centric Hierarchical Coordination and Supervision of Robotic Fleets Under Continual Temporal Tasks*
- P0046 — Bradshaw et al. 2008, *Coordination in Human-Agent-Robot Teamwork*
- P0047 — Paley, Techy & Woolsey 2009, *Coordinated Perimeter Patrol with Minimum-Time Alert Response*
- P0048 — Duarte, Oliveira & Christensen 2014, *Hybrid Control for Large Swarms of Aquatic Drones*
- P0049 — Wright et al. 2008, *Layered Mode Selection Logic for Unstructured Environments*
- P0050 — Chandler et al. 2009, *Optimal Perimeter Patrol Alert Servicing with Poisson Arrival Rate*
- P0051 — Bajaj et al. 2023, *Competitive perimeter defense with a turret and a mobile vehicle*

## Mandatory normalization

For every paper record:
- nominal mission before any target/threat event;
- whether nominal mission is area coverage/search, path patrol, point monitoring, generic task pool, resource defense, or uncommitted state;
- event/detection trigger;
- coalition/subgroup formation mechanism;
- whether the same robots are fungible across nominal/capture roles;
- capture/task-completion definition;
- whether completion is local or ends the whole episode;
- exact post-completion robot fate;
- explicit coalition dissolution yes/no;
- explicit same-agent return to nominal patrol/coverage yes/no;
- nonparticipant behavior during capture;
- repeated/new arrival model;
- sensing and target-information propagation;
- communication assumptions;
- centralized/distributed execution;
- capture semantics strength;
- simulation/real evidence;
- CoCap overlap and missing links.

## Critical false-positive rules

Do not equate:
- `uncommitted` with coverage;
- generic reassignment with return-to-coverage;
- many pre-existing tasks with exogenous repeated arrivals;
- patrol alert servicing with target capture;
- a mode named `Capture` with terminal capture;
- heterogeneous fixed roles with a fungible same-agent resource pool;
- coalition dissolution with coverage restoration;
- task-local capture labels with PE/no-escape capture guarantees.

## Key paper-specific checks

### P0043
Verify the exact wording and mechanism for synchronized strike completion, coalition dissolution, `uncommitted` state, pop-up target replacement, and what uncommitted UAVs actually do.

### P0044
Verify whether the capturing SWAT coalition explicitly dissolves after capture; exact robot fate after target becomes immobile; whether the same SWAT resources are reassigned; SCOUT/SWAT fungibility; communication and target-sharing assumptions; hardware scope.

### P0045
Verify exact `subtask completion → coalition dissolution → reassignment` semantics; whether capture subtasks are true interception/capture or generic temporal-task actions; target-state availability; continual arrival model.

### P0046
Verify whether `resume patrolling` is an actually demonstrated field-exercise transition or only a policy specification; identify role/coalition autonomy and sensing assumptions.

### P0047
Verify explicit return to coordinated patrol after alert response; no capture semantics should be silently inferred.

### P0048
Verify repeated intruder schedule, local alert radius, pursuer-number reduction, and exact return trigger; classify explicitly as loss/exit/timeout-driven rather than capture-driven if confirmed.

### P0049
Resolve the tension between state-machine Patrol/Capture/Pursue recovery and the prototype statement that capturers remain with the intruder until further instructions.

### P0050
Verify Poisson arrival model and patrol/service continuation; this is supporting repeated-event lineage, not presumed capture.

### P0051
Verify arbitrary-time intruder arrival and capture semantics; determine whether defender reuse is merely continued online defense or an explicit return/release lifecycle.

## Decision discipline

Use `MUST READ / MAP / ARCHIVE`.

A paper is `MUST READ` only if it is needed to close one of these exact boundaries:
1. capture completion → coalition dissolution/release;
2. same-agent return to patrol/coverage;
3. persistent nominal mission + repeated arrivals;
4. dynamic capture coalition + continued resource reuse;
5. strongest direct novelty threat to CoCap's same-pool coverage↔capture lifecycle.

Target a minimal READ set of roughly 2–5 papers, not all nine.

## Required synthesis

The screening note must answer:
1. Is isolated `post-capture return to patrol` already clearly anteceded?
2. Is capture-triggered coalition dissolution clearly anteceded?
3. Is repeated-arrival resource reuse clearly anteceded?
4. Does any paper implement the full same-pool `coverage/search → temporary capture coalition → capture → release → same agents restore coverage → repeat` loop?
5. Which candidate is the strongest structural competitor?
6. Which is the strongest capture-specific competitor?
7. Which is the cleanest return-to-patrol predecessor?
8. After SCREEN, is the lifecycle gap `DEAD / PARTIALLY SURVIVES / STRONGLY SURVIVES`?
9. What exact minimal papers should enter READ?
10. Should lifecycle SEARCH remain closed or reopen only via a named citation chain?

## Output

Write only a screening handoff under `notes/screening/`, preferably:

`notes/screening/SC-20260915-LIFE01.md`

Do not edit canonical files. Do not assign new IDs. Do not start READ.

Commit only the screening handoff, then report path and commit SHA.