# R-LIFE-01 — Lifecycle Closure READ

## Batch scope

本批 READ 只覆盖四篇已经由 S-LIFE-01 压缩出的 lifecycle MUST READ：

- **P0043** — Liu et al., *Construction of kill webs with heterogeneous UAV swarms in dynamic contested environments*
- **P0044** — Chen, Tang & Guo, *Accelerated K-Serial Stable Coalition for Dynamic Capture and Resource Defense*
- **P0046** — Bradshaw et al., *Coordination in Human-Agent-Robot Teamwork*
- **P0048** — Duarte et al., *Hybrid Control for Large Swarms of Aquatic Drones*

目标不是再次搜索，而是把 `Lifecycle novelty boundary v1` 封闭到可以供 MASTER 使用的强度。四篇均基于全文读取；P0044 的 arXiv 正式作者版本仅用于小范围核验其公开版本身份/结构，不开启新 SEARCH。

证据标签：
- `[原文]` — 上传正式全文直接支持；
- `[Web核验]` — 小规模正式/作者版本核验；
- `[AI判断]` — 本批综合、边界判断、CoCap 映射。

---

# 1. Executive conclusion — Lifecycle novelty boundary v1

[AI判断] **最终判断仍为 `PARTIALLY SURVIVES`，但比 SCREEN 阶段更窄、更清楚。**

四篇 READ 后，不能再把 lifecycle novelty 放在任何单独一条 transition 上：

- `apprehension/capture completion → patrol successor behavior` 已有历史前例（P0046）；
- `completion → explicit coalition dissolution → reusable pool` 已有非常直接的前例（P0043）；
- `true capture/immobilization → same capture resources reassigned to another target / defense task` 已有 simulation + hardware 前例（P0044）；
- `same homogeneous pool: patrol → local pursuit subgroup → same-agent Patrol restoration → repeated intruders` 已有清晰 state-machine 前例（P0048）。

但四篇全文仍没有任何一篇同时闭合：

`persistent area coverage/search by one fungible pool`
→ `target event under local/intermittent information`
→ `temporary capture coalition formed from that same pool`
→ `state-dependent/adaptive coalition size`
→ `terminal physically meaningful capture`
→ `completion-triggered release`
→ `the same captured-task agents restore nominal coverage`
→ `repeat for later target arrivals`.

结合 FS-LIFE-01 已接近饱和的 focused search 与 S-LIFE-01 screening，[AI判断] 可以写：

> **在当前已封闭的 lifecycle search branch 中，没有找到同时实现上述完整 same-pool capture↔coverage lifecycle 的工作。**

不能写：

> “此前从未有人做过。”

更不能写：

> “return to patrol / coalition dissolution / repeated arrivals / dynamic coalition 本身是新颖的。”

**真正剩下的 candidate gap 是 coupling，而不是 lifecycle primitive 本身。**

---

# 2. Four-paper unified lifecycle matrix

Legend:
- **Y** = directly established;
- **P** = partial/qualified;
- **N** = absent for the CoCap meaning;
- **?** = primary text insufficient for a strong claim.

| Axis | P0043 Liu | P0044 KS-COAL | P0046 Bradshaw | P0048 Duarte |
|---|---|---|---|---|
| Nominal task | uncommitted sneak-like movement | fixed SCOUT coverage/exploration; SWAT capture/defense | boundary security → area search; patrol only as successor example | **persistent area patrol/coverage** |
| Homogeneous / fungible pool | **N/P** heterogeneous type-constrained UAVs | **N across roles**; fungible only within SWAT capture/defense pool | **N/P** heterogeneous robots + humans/roles | **Y** same homogeneous drone population |
| Target event | identified/available target/task | SCOUT discovers target / task state changes | robot finds intruder | local camera sees intruder |
| Local detection | **P/?** “identified/recognized” targets but sensor model under-specified | **Y for SCOUT**, then target position delivered to SWAT | **Y** robot detection in field exercise | **Y**, ~100 m forward camera |
| Target information propagation | neighbor target-list exchange | SCOUT→SWAT target position; strong propagation | team/leader notification | local alert to neighbors within 200 m |
| Temporary subgroup | **Y**, temporary combat coalition | **Y**, task-specific SWAT coalition | **P**, dynamically modified team/subteam | **Y functionally**, local pursuit subgroup |
| Dynamic membership | **Y** before sticky lock | **Y**, switch-chain reassignment | **Y**, human/policy mediated | **Y**, alerted agents join; excess pursuers leave |
| Adaptive coalition size | **N/P**: member identity can change, but target demand prescribes type/count requirements | **Y/P**, utility-induced variable SWAT coalition; no fixed `q_j` | **N**, no autonomous size optimization | **P**, emergent behavior often leaves ~2 |
| Terminal capture | **N in PE sense**; synchronized strike/destruction | **Y**, target becomes immobilized | **Y**, successful apprehension | **N** |
| Capture semantics | destructive strike | moving-target capture + immobilization; Apollonius-based pursuit | apprehension | detection/tracking until exit/loss |
| Completion-triggered release | **Y, explicit** | **Y functionally**, capture triggers reassignment | **P**, completion notification triggers next task; no explicit coalition dissolve | **N for capture**; release is loss/timeout driven |
| Explicit coalition dissolution | **Y**, literal wording | **P**, functional task-switch/reallocation rather than highlighted “dissolve” state | **N** | **N formal coalition object** |
| Same-agent reuse | **Y** | **Y**, hardware demonstrates same SWAT reuse | **P**, successor behavior is role-dependent, no identity trace | **Y** |
| Same-agent return to nominal task | **N** | **N** for exploration/coverage | **P** policy-level `resume patrolling`; not traced | **Y**, same state machine returns to Patrol |
| Exact return destination | uncommitted sneak-like motion | another capture or resource encirclement/defense | role-appropriate task, e.g. base or patrol | Patrol |
| Nonparticipants continue nominal task | **P**, other coalitions/uncommitted agents continue | **Y** SCOUT exploration persists; other SWAT tasks continue | **P** teams continue assigned mission until success | **Y**, unaffected majority keeps patrolling |
| Repeated arrivals | **Y**, pop-up target replaces destroyed target | **? for target arrivals**; repeated captures, resources generated continuously | **N** | **Y**, 44 crossings over 24 h |
| Communication | finite-range adaptive neighbor network | mixed: SCOUT unlimited intra-team; SWAT limited/local; target coords propagated | wireless + policy services + human hierarchy | local ~200 m |
| Centralized / human involvement | distributed | distributed task coordination | **high human involvement** | decentralized behavior |
| Real experiment | **N** | **Y**, 11/13 robots | **Y**, Navy-pier field exercise | **N**, lifecycle simulation |
| Exact missing edge vs CoCap | no nominal coverage + no PE capture | fixed SCOUT/SWAT roles + no same-agent coverage restoration + no local capture belief | no autonomous swarm coalition/repeat/metric restoration | no terminal capture/capturability-aware assignment |

### Matrix interpretation

[AI判断] The four papers form a near-perfect **edge cover** of the CoCap lifecycle:

- P0043 covers the **release/reuse/repeat** side;
- P0044 covers the **real capture + dynamic coalition + post-capture reuse** side;
- P0046 kills the historical **post-apprehension patrol successor** claim;
- P0048 covers the **same fungible pool + persistent coverage + temporary pursuit + return + repeat** side.

What is not found is the **same system coupling all of them**—especially with a capture-feasibility mechanism and unresolved local information.

---

# 3. P0043 — how much lifecycle is already closed?

## 3.1 Edges that P0043 closes strongly

[原文, p.5/Fig.2] UAVs enter a temporary combat coalition in `sticky / orbiting wait`; when all members are in place they conduct synchronized strike; **after that, the coalition dissolves and each UAV returns to the uncommitted state**.

This closes:

`temporary coalition`
→ `local task completion`
→ `explicit coalition dissolution`
→ `reusable uncommitted resource`.

[原文, p.14] destroyed targets are replaced by same-type random **pop-up targets**, keeping target count unchanged. Therefore it also closes:

`release`
→ `future workload`
→ `resource can be recruited again`.

This is stronger than merely “multiple targets existed initially.”

## 3.2 Why uncommitted is not CoCap coverage

[原文, pp.5–6] `uncommitted` is **sneak-like movement without a selected target**. Its controller combines collision repulsion, attraction toward recognized target positions, and boundary bounce-back.

[AI判断] That is not:
- area coverage;
- search partition;
- patrol;
- coverage optimization;
- a measurable nominal spatial objective.

Therefore:

`completion → uncommitted`
≠
`completion → nominal coverage restored`.

This distinction remains mandatory.

## 3.3 Capture semantics correction

[原文] terminal event is synchronized strike/destruction.

[AI判断] It must not be silently mapped to:
- PE capture;
- apprehension;
- pursuit immobilization;
- no-escape enclosure.

**P0043 is strongest on lifecycle release semantics, not on pursuit-capture semantics.**

---

# 4. P0044 / KS-COAL — is it already almost complete CoCap?

## 4.1 Why it is the strongest lifecycle competitor

P0044 places in one system:
- [原文] SCOUT coverage/exploration;
- [原文] online target discovery;
- [原文] dynamic SWAT capture coalitions;
- [原文] moving evasive TARGET robots;
- [原文] Apollonius-based capture motion;
- [原文] positive-distance capture (`d_c`; 3 m in the main simulation) that makes the TARGET immobile;
- [原文] event-triggered re-coordination after capture;
- [原文] hardware post-capture reuse.

The first hardware sequence is especially damaging to loose novelty claims:

`SWAT 3,4 → capture TARGET0 at 70s`
→ `same SWAT 3,4 → switch to TARGET1`
→ `TARGET1 captured at 90s`
→ `all SWAT → return to resource encirclement`.

Therefore:
- “capture coalition resources can be reused after capture” is dead;
- “capture agents can switch to another task after capture” is dead;
- “dynamic capture coalitions plus non-capture mission tasks” is dead.

## 4.2 Fixed heterogeneous roles are the decisive lifecycle difference

[原文] SCOUT and SWAT are distinct capability teams.

- SCOUT: fast, long-range perception, workspace exploration;
- SWAT: short-range perception, capture, resource encirclement.

[AI判断] The critical point is **not** simply “heterogeneous robots exist.” The critical point is that the nominal coverage/search mission and capture mission are assigned to **different fixed resource classes**.

Thus P0044 does **not** implement:

`same agent was covering`
→ `borrowed into capture`
→ `same agent restores coverage`.

It implements instead:

`SCOUT continues exploration`
+
`SWAT dynamically cycles among capture / defense`.

This is structurally close but not the same lifecycle.

## 4.3 Is KS-COAL coalition feasibility a physical capturability certificate?

**No.**

### P0025 / R-PE-01
A coalition-target pair is feasible because current game state lies in a coalition winning region. The edge means a strategy-quantified capture guarantee under the model.

### P0042 / R-LM-01
Learned target preference is converted into a hard assignment with prescribed target capacity. It is combinatorially feasible, but capacity does not come from current-state capturability.

### P0044
[原文] KS-COAL maximizes task utilities through allowed robot-task switches and defines K-serial stability as the absence of an improving rooted switch chain of bounded length.

[原文] capture itself is physically informed through an Apollonius-based motion strategy, and coalition utility is task-specific.

[AI判断] But the theorem says:
- this **assignment is KSS / globally optimal under certain K** for the chosen utility,

not:
- coalition `S` can **force** capture of target `j` from this current uncertain state.

Therefore:

`task-allocation stability`
≠
`current-state physical capturability certificate`.

P0044 is more physically grounded than generic MRTA, but it does not erase the R-PE-01 semantic gap.

## 4.4 Coalition size / capacity

[原文 + AI判断] Unlike P0042’s fixed per-target `q_j`, P0044 allows coalition membership to emerge from utility and repeated switching; marginal utility can make extra SWAT participation unattractive.

So P0044 is a stronger comparator for **adaptive cardinality** than P0042.

However, cardinality is not selected by an explicit object such as:

`C(S,j) = robust/probabilistic capturability`.

Thus CoCap cannot claim “adaptive coalition size” alone, but can still investigate **capturability-conditioned adaptive size**.

## 4.5 Repeated targets: a remaining textual uncertainty

[原文] resources are explicitly generated repeatedly.

[原文] the main simulation initializes 50 TARGET robots yet later reports 234 captures in 200 time steps.

[AI判断] The journal body does not clearly specify a TARGET respawn/arrival rule that reconciles those statements. Therefore the safe claim is:

- P0044 demonstrates **continued/repeated capture workload**;
- P0044 does **not provide a cleanly specified recurring target-arrival process** in the primary text available here.

This uncertainty does not materially rescue broad CoCap novelty because P0043/P0048 independently establish true repeated arrivals.

---

# 5. P0046 — how strong is `resume patrolling` evidence?

## 5.1 What is unquestionably executed

[原文, Sec. 5.3]
- the Commander forms teams;
- teams secure boundaries;
- teams search;
- a robot finds the intruder;
- the Lieutenant requests tBot;
- the Commander dynamically reassigns tBot;
- **apprehension succeeds**.

This is a real field exercise.

## 5.2 What `resume patrolling` actually says

[原文, Sec. 6.2] once an intruder has been apprehended, team members are notified, and each robot begins the appropriate task it was designed to perform after successful completion, with examples including:

`return to base`
or
`resume patrolling`.

This supports a strong historical statement:

> **post-apprehension patrol resumption exists as an explicit policy/workflow successor action.**

But the paper does **not** show:
- a plot/trajectory of the specific apprehending robot returning to patrol;
- all robots returning to patrol;
- restoration of a patrol formation or coverage metric;
- another intruder arriving after recovery.

Therefore the evidence level is:

**policy/workflow-level + field-exercise-linked**, not **quantitatively demonstrated same-agent restoration**.

## 5.3 Novelty consequence

[AI判断] The claim:

> “post-capture return to patrol has prior precedent”

is defensible **with this qualifier**.

The claim:

> “P0046 already demonstrates the full same-agent autonomous patrol→capture→patrol loop”

is not defensible.

Standalone novelty of “resume patrol after apprehension” must nevertheless be removed.

---

# 6. P0048 — if `loss/exit → return` became `capture → return`, how much gap remains?

## 6.1 On lifecycle architecture: very little

P0048 already has:

`same homogeneous pool`
→ `persistent coverage/patrol`
→ `local camera detection`
→ `local neighbor alert`
→ `temporary pursuit subgroup`
→ `excess pursuers leave`
→ `same agents return to Patrol`
→ `44 repeated crossings over 24 h`.

It also keeps nonparticipants patrolling.

[AI判断] If its pursuit terminal were replaced by a genuine capture event, P0048 would close almost the entire **lifecycle state-machine skeleton** that CoCap originally appeared to own.

## 6.2 But method-level gap would still remain

Even after replacing the terminal trigger, P0048 still lacks:

1. **capturability-aware recruitment** — agents join because they are locally alerted, not because their marginal contribution changes capture feasibility;
2. **target-wise assignment/resource conflict** — no explicit multi-target assignment layer;
3. **no-escape / physically meaningful terminal capture** — not present in the actual paper;
4. **uncertainty-aware coalition decision** — camera detection is local, but no belief/capture-probability object controls recruitment;
5. **capture-triggered release policy** — current release is target loss/no-intruder timeout.

Therefore P0048 is a **near miss for lifecycle integration**, not a replacement for the information+capturability coupling.

## 6.3 Exact return condition correction

[原文] two statements must be separated:
- the pursuit behavior stops following when the intruder exits and agents adjust to neighbors;
- the explicit high-level `Pursue Intruder → Patrol` state transition is `no intruder for 5 min`.

[AI判断] The normalized transition is **loss/timeout-driven return**, not immediate capture completion and not even strictly immediate exit-triggered state change.

---

# 7. Same-pool lifecycle audit

The exact same-pool question is:

> Is there a single system in which the agents maintaining nominal area coverage/search are the **same fungible resources** temporarily borrowed into a capture coalition and then, after terminal capture, released back into that nominal coverage/search process for future arrivals?

### P0043
- reusable: yes;
- same pool: only type-constrained;
- nominal coverage: no;
- terminal PE capture: no;
- return to coverage: no.

### P0044
- reusable: yes;
- true capture: yes;
- persistent exploration exists: yes;
- **same pool across exploration/capture: no** because SCOUT/SWAT split;
- return of capturers to exploration: no.

### P0046
- successful apprehension: yes;
- successor patrol exists in policy: yes;
- same-agent trace: unproven;
- autonomous fungible swarm pool: no;
- repeated arrivals: no.

### P0048
- same homogeneous pool: yes;
- persistent coverage: yes;
- local temporary subgroup: yes;
- same-agent Patrol restoration: yes;
- repeated arrivals: yes;
- **terminal capture: no**.

[AI判断] **No exact closure among the four READ papers.** Combined with the saturated focused branch, the integrated same-pool loop remains unfound, but should be described as a search result rather than a universal theorem of novelty.

---

# 8. Integration with R-PE-01, R-LM-01 and R-CE-01

## 8.1 Capturability itself is not the gap

R-PE-01 already established:

`reach-avoid semantics`
→ `capturability certificate`
→ `coalition feasibility`
→ `resource-constrained assignment`
→ `no-escape`
→ `maintained contraction`
→ `capture`.

P0025 in particular already gives a clean model-specific coalition-winning-certificate→assignment construction.

Therefore CoCap cannot claim capturability or capturability-aware assignment as a general first principle.

## 8.2 Local sensing itself is not the gap

R-CE-01 and R-LM-01 already killed:
- finite sensing/FOV novelty;
- range-only sensing novelty;
- target loss/reacquisition novelty;
- decentralized control novelty.

P0034 is already a strong local FOV/occlusion/loss-reacquisition learning comparator.

Therefore “local sensing” alone is not CoCap novelty.

## 8.3 Lifecycle itself is not the gap

R-LIFE-01 now kills:
- dynamic coalition release;
- post-capture resource reuse;
- post-apprehension patrol resumption;
- same-agent patrol→pursuit→patrol;
- repeated arrivals.

Therefore “lifecycle” alone is also not a safe contribution.

## 8.4 What survives: the coupling

[AI判断] The strongest remaining conceptual intersection is:

**information + capturability + lifecycle coupling**

More concretely:

`persistent coverage by one fungible pool`
→ `execution-time local/intermittent target belief`
→ `estimate current coalition capture feasibility`
→ `borrow only agents with positive marginal capturability value relative to coverage opportunity cost`
→ `execute meaningful capture`
→ `confirm terminal state`
→ `release the same agents`
→ `measure recovery of nominal coverage`
→ `repeat under later arrivals`.

This is where the earlier three READ batches and R-LIFE-01 actually meet.

---

# 9. DEAD claims

The following claims should now be treated as dead as standalone novelty statements:

1. **“First to return to patrol after capture/apprehension.”**  
   P0046 supplies a prior policy/workflow precedent.

2. **“First completion-triggered coalition dissolution.”**  
   P0043 states this explicitly.

3. **“First to reuse capturing resources after a capture.”**  
   P0044 demonstrates same SWAT resources taking subsequent tasks after terminal capture.

4. **“First dynamic capture coalition in a persistent multi-task mission.”**  
   P0044 is already a direct competitor.

5. **“First same-agent patrol → pursuit → patrol cycle.”**  
   P0048 has an explicit state machine.

6. **“First repeated-intruder persistent pursuit lifecycle.”**  
   P0048 runs 44 repeated crossings; P0043 independently has replacement pop-up targets.

7. **“First adaptive capture subgroup size.”**  
   Too broad: P0044 allows utility-driven changing SWAT coalition membership/cardinality; P0048 has excess pursuers cease pursuit.

8. **“First local target detection triggering temporary response.”**  
   P0048 directly does this.

9. **“First persistent coverage + pursuit in one system.”**  
   P0048 already does same-pool patrol+pursuit; P0033 already covers fixed-role concurrent exploration+pursuit.

10. **“First capture + exploration/coverage + resource allocation.”**  
    P0044 already integrates fixed-role exploration with dynamic capture/defense.

---

# 10. SURVIVING claims

Only combination-level claims remain defensible, and wording should avoid “first” unless a later publication-stage search supports it.

## 10.1 Strongest candidate method/system claim

[AI判断]

> **CoCap studies a persistent multi-UAV mission in which one fungible swarm maintains nominal coverage, temporarily reallocates agents into target-specific capture coalitions according to state/information-dependent capture feasibility and coverage opportunity cost, and after confirmed terminal capture releases those same agents to restore coverage for later arrivals.**

If local-information handling is genuinely implemented:

> **The distinctive coupling is between unresolved local/intermittent target information, coalition capturability estimation, and the coverage↔capture resource lifecycle—not any one of those components in isolation.**

## 10.2 What makes this more than an implementation combination

[AI判断] If CoCap only implements:

`if enemy detected: send K agents`
→ `if captured: switch their reward back to coverage`,

then the surviving novelty is vulnerable to being described as a **systems integration combination**, because P0044/P0048 together already cover most lifecycle structure.

To strengthen a method contribution, the lifecycle should enter the decision mathematically/algorithmically through at least:
- `C(S,j)` or equivalent capture-feasibility score;
- marginal recruitment value `Δ_i`;
- coverage opportunity cost / coverage debt;
- explicit release confidence/terminal condition;
- dynamic target-wise resource constraints.

The novelty candidate then becomes the **decision coupling between mission states**, not the mere existence of states.

---

# 11. Evidence strength / novelty wording discipline

### Clearly absent in the four READ papers
- exact same fungible coverage pool + terminal capture + completion-triggered same-agent coverage restoration + repeated arrivals;
- belief-aware capturability controlling join/leave in that lifecycle.

### Not found after saturated search + SCREEN + READ
- a single prior paper closing the full integrated loop above.

### Already theoretically established elsewhere
- reach-avoid/capturability;
- coalition feasibility and resource-constrained assignment under specific PE models;
- no-escape/capture conditions.

Therefore **do not** label those theoretical objects as new merely because CoCap learns/approximates them.

### Potentially “merely implementation combination”
- coverage + capture + finite-state switching;
- dynamic gate without a new feasibility/opportunity-cost object;
- release-to-coverage based only on a hard event.

[AI判断] A final paper should phrase novelty as a **new coupled decision problem / learned coordination mechanism under specific information and lifecycle constraints**, not as universal theoretical novelty.

---

# 12. Strongest competitors after R-LIFE-01

## Strongest lifecycle competitor: **P0044**

Reason:
- true capture/immobilization;
- dynamic task-specific coalitions;
- exploration and non-capture defense in the same overall mission;
- post-capture same-resource reuse;
- simulation + hardware.

Its decisive CoCap gap is the fixed SCOUT/SWAT split.

## Closest same-pool lifecycle architecture: **P0048**

Reason:
- homogeneous/fungible pool;
- persistent coverage;
- local event detection;
- temporary pursuit;
- dynamic reduction in pursuer count;
- explicit same-agent return to Patrol;
- repeated arrivals.

Its decisive missing edge is terminal capture.

## P0042 vs P0044 — strongest overall CoCap competitor

[AI判断] **P0044 now becomes the stronger overall novelty-boundary competitor for CoCap’s integrated system story.**

Why:
- it reaches beyond a learned assignment module into a full persistent mission with exploration, capture, defense, online coalition switching, terminal capture and post-capture reuse;
- it has hardware evidence;
- it directly threatens lifecycle language.

However:
- **P0042 remains the strongest direct learning/method competitor** for `learned target preference → explicit hard assignment → subgroup-conditioned learned control → meaningful capture`.
- P0044’s KSS is model-based allocation stability, not a learned capturability-aware actor/allocation mechanism.

Thus final positioning should use both:
- P0044 for **mission/lifecycle competitor**;
- P0042 for **learning/allocation architecture competitor**.

---

# 13. CoCap method implications

## 13.1 Fungible resource pool should be explicit

[AI判断] Yes. This should become an explicit assumption/design property:

> the same UAV is not born as a “coverage UAV” or “capture UAV”; it can serve nominal coverage, temporarily become support/capture, and return to coverage after release.

This is the cleanest structural separator from P0044 and P0033 fixed-role systems.

A paper should report actual role-transition traces/occupancy, not infer fungibility from a shared network.

## 13.2 Release semantics should be explicit and conservative

Recommended first definition:

`release = confirmed terminal capture/removal/deactivation`
**AND**
`no remaining capture-safety requirement for that agent`.

Do not use:
- “target briefly unseen”;
- “ring formed”;
- “capture reward fired once” without confirmation;

as equivalent release criteria.

If capture is noisy/probabilistic, a confidence/hold-time criterion is preferable. If target removal is deterministic in simulation, terminal removal is a clean first benchmark.

## 13.3 Coverage restoration must be measured, not narrated

Recommended metrics:

1. **Pre-event nominal coverage baseline** `C_pre`.
2. **Peak coverage deficit** during capture: `max_t(C_pre - C(t))`.
3. **Integrated coverage debt** during event/recovery: `∫[C_pre-C(t)]_+ dt`.
4. **Post-capture release latency**: terminal capture → capture coalition actually released.
5. **Coverage recovery time**: capture/release → coverage returns to a threshold such as 90–95% of `C_pre`.
6. **Recovered steady-state coverage ratio** over a fixed post-event window.
7. **Nonparticipant coverage continuity** during capture.
8. **Borrowed-agent cost**: agent-seconds removed from nominal coverage per successful capture.
9. **Repeated-event degradation**: capture success, mean coverage, coverage debt and recovery time as event frequency rises.
10. **Recovery-before-next-event rate**: fraction of events for which the swarm restores nominal coverage before the next target arrives.
11. **Long-horizon state occupancy**: fractions of time/agents in coverage, support, capture and recovery modes, analogous to P0048’s state-occupancy plot.

## 13.4 Repeated-arrival benchmark should become first-class

[AI判断] Yes. One-shot episodes hide the exact lifecycle claim.

At least one evaluation should use a long horizon:

`coverage`
→ `arrival 1`
→ `capture`
→ `release`
→ `coverage recovery`
→ `arrival 2`
→ `...`

and vary inter-arrival time so the system can be tested under:
- fully recovered before next event;
- overlapping recovery and next event;
- sustained high-load regime.

The important outcome is not only capture rate but **mission resilience**: how much coverage performance is lost and whether it recovers.

## 13.5 Recruitment should internalize coverage opportunity cost

A natural continuation of R-PE-01 is:

`Δ_i(S,j) = C(S∪{i},j) - C(S,j)`

but R-LIFE-01 adds the missing cost term:

`U_i = Δ_i(S,j) - λ * CoverageCost(i)`

or an equivalent constrained formulation.

[AI判断] This is the mathematically meaningful way to turn “fungible resource pool” from narrative into method.

---

# 14. Named follow-up chains

## P0046 companion chain — record, do not reopen by default

P0046 explicitly cites two 2008 companion papers from the same program/field scenario:

- Johnson, Feltovich, Bradshaw & Bunch — **Human-robot coordination through dynamic regulation** (ICRA 2008);
- Johnson et al. — **Coordinated operations in mixed teams of humans and robots** (DHMS 2008), described as an overview of the whole system/scenario.

[AI判断] These may contain more execution detail about whether a particular robot physically resumed patrol after the apprehension. They do not, from P0046’s citation context, suggest repeated intruders or an autonomous same-pool coverage→capture→coverage lifecycle.

**Decision:** record as `NAMED FOLLOW-UP CHAIN`; **do not reopen lifecycle SEARCH**. A one-paper targeted verification is only justified later if the exact historical claim “same capturer physically resumed patrol” becomes critical to final wording.

No other READ paper exposed a named predecessor/follow-up chain that plausibly closes the exact remaining intersection.

---

# 15. Answers to the 11 mandatory R-LIFE-01 questions

### 1. P0043 已经覆盖 lifecycle 哪些 edge？
[AI判断] `identified task → dynamic temporary coalition → synchronized strike/destruction → explicit coalition dissolution → return to reusable uncommitted pool → replacement pop-up target`. It does **not** cover nominal coverage restoration or PE capture.

### 2. P0044 是否已经接近完整 CoCap lifecycle？
**非常接近 capture/reuse 侧，但不完整。** It has exploration, dynamic capture coalitions, terminal immobilizing capture, post-capture reassignment and hardware evidence. The decisive missing edge is `same coverage agent → capture → same agent restores coverage`; SCOUT and SWAT are fixed capability classes.

### 3. P0046 的 `resume patrolling` evidence 到底有多强？
Strong enough to establish a **policy/workflow-level post-apprehension patrol-resumption precedent** linked to a real field exercise. Not strong enough to claim that the paper experimentally traces the same capturer restoring patrol/coverage. Standalone “first return to patrol after capture” novelty must die.

### 4. P0048 缺少 terminal capture 后还剩多少 gap？
For the **lifecycle state machine**, very little: it already has same-pool coverage, local detection/recruitment, temporary pursuit, return, nonparticipant patrol and repeated arrivals. For the **method contribution**, significant gaps remain: no capturability-aware recruitment, no target-wise assignment, no no-escape capture, and release is loss/timeout driven.

### 5. 是否已有完整：
`same fungible pool + nominal coverage + temporary capture coalition + terminal capture + release + same-agent coverage restoration + repeat`？
**No in the closed READ branch; not found after the saturated focused lifecycle search/screen/read sequence.** This is a search conclusion, not a proof of global nonexistence.

### 6. lifecycle gap 最终是否仍为 `PARTIALLY SURVIVES`？
**Yes.** It survives only as an integrated same-pool/capture-completion/restoration loop, not as any isolated lifecycle edge.

### 7. 是否需要 reopen lifecycle SEARCH？
**No.** Default remains closed. Only the P0046 same-program companion papers are recorded as a named chain for optional later precision checking.

### 8. current strongest lifecycle competitor 是谁？
**P0044**. P0048 is the closest same-pool lifecycle near miss.

### 9. current strongest overall CoCap competitor 是否仍是 P0042，还是 P0044 已经更重要？
[AI判断] **P0044 is now more important for the overall novelty boundary**, because it threatens the integrated mission/lifecycle narrative and has real hardware. **P0042 remains the strongest learning/allocation-method competitor.**

### 10. CoCap 最准确的 novelty wording v1 是什么？
Recommended non-“first” wording:

> **CoCap addresses a persistent same-pool coverage–capture coordination problem in which UAVs operating under local/intermittent target information are temporarily recruited from nominal coverage according to capture-feasibility and mission opportunity cost, execute terminal capture, and are explicitly released back to restore coverage for subsequent target arrivals. The candidate novelty lies in coupling local information, coalition capturability and lifecycle-aware resource reuse, rather than in coverage, capture, coalition formation or post-capture return individually.**

Shorter paper-facing form:

> **A fungible UAV swarm dynamically borrows agents from persistent coverage only when they improve target capturability, then releases the same agents after confirmed capture to recover coverage under repeated target arrivals.**

### 11. CoCap evaluation 应新增哪些 lifecycle metrics？
At minimum:
- event-conditioned coverage deficit / coverage debt;
- capture-time borrowed-agent cost;
- capture→release latency;
- release→coverage-recovery time;
- recovered steady-state coverage ratio;
- nonparticipant coverage continuity;
- repeated-arrival degradation / recovery-before-next-event rate;
- long-horizon agent state occupancy.

---

# 16. Lifecycle novelty boundary v1

## DEAD claims
- first post-capture/apprehension return to patrol;
- first completion-triggered coalition dissolution;
- first post-capture resource reuse;
- first same-agent patrol→pursuit→patrol;
- first repeated-arrival patrol/pursuit loop;
- first dynamic capture coalition in a mixed persistent mission;
- first adaptive capture subgroup cardinality in any sense;
- first exploration/coverage + capture integration.

## SURVIVING claims
[AI判断] The narrow surviving candidate is:

> **one fungible resource pool repeatedly cycling between persistent nominal coverage and target-specific terminal capture, with capture-coalition recruitment/release coupled to unresolved local target information, current-state capture feasibility, and coverage opportunity cost.**

## Evidence strength
- exact loop: **clearly absent in the four deep-read lifecycle papers**;
- full integrated loop: **not found after the saturated FS-LIFE-01 + S-LIFE-01 + R-LIFE-01 branch**;
- theoretical novelty: **not established and should not be claimed**;
- lifecycle-only combination: **at risk of being seen as systems integration** unless CoCap formalizes the information/capturability/opportunity-cost coupling.

---

# 17. Final PROJECT_PROTOCOL handoff

## NEW PAPERS
None. R-LIFE-01 did not reopen SEARCH.

## UPDATED PAPERS
- P0043 — READ complete; explicit dissolution/reusable-pool/replacement-target semantics confirmed.
- P0044 — READ complete; terminal immobilizing capture, dynamic SWAT coalitions and hardware post-capture reuse confirmed; KSS correctly scoped as allocation stability, not capturability.
- P0046 — READ complete; `resume patrolling` downgraded from any possible “demonstrated same-agent restoration” reading to policy/workflow-level successor-action evidence linked to a real apprehension exercise.
- P0048 — READ complete; exact `Pursue→Patrol` timeout state transition, same-pool fungibility and 44 repeated crossings confirmed; terminal capture absent.

## MUST READ
No new promotions. These four MUST READ papers are now completed.

## MAP
No canonical decision changes proposed by the READ child session.

## ARCHIVE
No changes.

## TAXONOMY CHANGES
Recommend MASTER preserve/add the following distinctions:
1. `reusable uncommitted pool` ≠ `nominal-task restoration`;
2. `post-capture reassignment` ≠ `same-agent return to coverage`;
3. `policy-level patrol successor` ≠ `physically demonstrated coverage recovery`;
4. `task-allocation stability` ≠ `current-state capturability`;
5. `loss/timeout-triggered patrol return` ≠ `terminal-capture-triggered release`;
6. `behavioral pursuit subgroup` ≠ `explicit capture coalition`;
7. `fixed heterogeneous role pools` ≠ `fungible coverage↔capture resource pool`.

## SEARCH GAPS
No lifecycle broad-search gap warrants reopening. A narrow optional precision check exists for the P0046 same-program Johnson et al. 2008 companion papers if final historical wording requires proof that patrol resumption was physically executed.

## CONFLICTS / UNCERTAINTIES
1. P0044 reports 50 initial TARGET robots but 234 captures over 200 time steps without an explicit TARGET regeneration rule in the journal body; do not convert this into a stated stochastic target-arrival model.
2. P0046’s `resume patrolling` is explicit successor-policy wording, but not a traced same-agent post-apprehension trajectory.
3. P0043 records identified/recognized targets and distributed propagation but does not define a strong onboard detection model; do not treat it as a local-sensing benchmark.
4. P0048’s pursuit stops on target exit, while its high-level state transition back to Patrol is specifically `no intruder for 5 min`; normalize this as loss/timeout-driven restoration.

---

# 18. Final R-LIFE-01 stance

**Lifecycle novelty boundary v1:** `PARTIALLY SURVIVES — coupling-level only`.

**Strongest lifecycle competitor:** **P0044 KS-COAL**.

**Closest same-pool lifecycle near miss:** **P0048 Duarte et al.**

**Same-pool lifecycle audit:** no READ-confirmed paper closes `coverage → temporary capture coalition → terminal capture → release → same-agent coverage restoration → repeated arrivals` with one fungible pool.

**CoCap method implication:** make fungibility, capturability-aware borrowing, explicit terminal release and measured coverage restoration first-class method/evaluation objects; otherwise the lifecycle contribution risks collapsing into an implementation combination of already-known primitives.

**Named follow-up chains:** P0046 → Johnson et al. ICRA 2008 / DHMS 2008 companion papers; record only, do not reopen lifecycle SEARCH by default.
