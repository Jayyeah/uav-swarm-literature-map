# R-CE-01 — Classical Encirclement Boundary and Lifecycle

## Batch scope

本批只 READ 六篇 classical/control/optimization papers：

- P0003 — Kim & Sugie 2007
- P0004 — Lan, Yan & Lin 2010
- P0008 — Franchi, Stegagno & Oriolo 2016
- P0009 — Wen et al. 2024
- P0010 — Pichierri et al. 2026
- P0012 — Liu et al. 2026

本 synthesis 使用 R-PE-01 的理论尺子：

`reach-avoid → capturability certificate → coalition feasibility → assignment → no-escape → maintained contraction → capture`

并与 R-LM-01 的四个最强 comparison nodes 对接：

- P0042 — explicit assignment / subgroup / capture structural competitor
- P0034 — literal FOV/range/occlusion/loss-reacquisition competitor
- P0035 — Transformer/multi-target/scalability competitor
- P0033 — concurrent exploration+pursuit predecessor

证据标签：
- `[原文]`：六篇上传正式 PDF 直接支持；
- `[Web核验]`：仅沿用 repo 已核验的正式 bibliographic identity；
- `[AI判断]`：本批综合、边界判断与 CoCap 映射。

---

# 1. Unified assumption matrix

## 1.1 Task / dynamics / information assumptions

| Axis | P0003 | P0004 | P0008 | P0009 | P0010 | P0012 |
|---|---|---|---|---|---|---|
| Task semantics | geometric `target-capturing` / enclosing | fixed-target uniform enclosing | 3-D moving-target encirclement | moving-target enclose+track under FOV | concurrent static-target encirclement + fixed-spot monitoring + safe placement | protect target → detect/estimate hostile → encircle → intercept |
| Target number | 1 | 1 | 1 | 1 | 1 known common target | 2 entities: 1 protected + 1 hostile |
| Target static/moving | moving exogenous | **static** | moving | moving smooth | **static** | moving stochastic hostile |
| Strategic evader | **N** | **N** | **N** | **N** | **N** | **N/P** non-cooperative + aggressive stochastic maneuvers, but no minimax strategy |
| Agent dynamics | 3-D single integrator | planar bounded unicycle | theorem: 3-D single integrator; platform tracking layers | uncertain two-wheel nonholonomic | generic stabilized; quadrotor + unicycle realizations | discrete 3-D double integrator point-mass |
| Control/action | Cartesian velocity | linear/angular velocity | Cartesian velocity reference | wheel angular speeds | high-level setpoints + low-level thrust/rates or v/ω | 3-D acceleration |
| Raw target sensing | direct target-relative vector at every agent | target distance+bearing when in sensing region | one robot may directly know target/frame; others need not | claimed relative-position/onboard camera; math requires target motion/trajectory input | **none modeled**; target coordinate `b` is known task datum | each guardian noisy range to hostile; protected target shares full state |
| Finite sensing range | N | **Y** | hardware laser finite range implicitly; theory not key | not specified | N for target | not explicit |
| FOV | N | N | hardware laser 240° + 120° blind zone | **Y**, explicit `±β` | N | N |
| Occlusion | N | N | blind zone, not environmental occlusion | **N** | N | N |
| Target temporarily lost | N | close-range law prevents loss; no search | target state reconstructed despite blind-zone raw sensing | bad reference can violate FOV, but proposed law prevents loss; no recovery policy | N | no dropout model |
| Bearing/range-only | full relative vector | distance + bearing | laser relative positions / global-quantity estimates | relative-position + camera angle geometry | not target-sensing problem | **range-only noisy hostile measurement** |
| Neighbor communication | none | sensing-chain / local topology | **Y**, connected graph; multi-hop allowed | no explicit inter-agent algorithm | **Y**, event-triggered directed graph | **Y**, two guardians |
| Estimator | none | none | **Y**, consensus tracking of global quantities + hardware mutual localization | no target-state estimator | **Y**, aggregate/gradient trackers, not target estimator | **Y**, Kalman target-state estimator |
| Global state reconstruction | N | N | **Y** effectively: target/frame + relative team quantities | target motion/trajectory enters reference generator; acquisition mechanism unmodeled | macro aggregate reconstructed; target itself already known | **Y** hostile position+velocity estimate from ranges |
| Decentralized execution | **Y** | **Y** | **Y algorithmically** | per-robot tracking; no distributed-information theorem | **Y algorithmically** | cooperative two-guardian control; no central controller specified |
| External/global localization dependence | no absolute localization stated | no absolute position | hardware explicitly no external tracker; mutual localization | no hardware validation | **Y in real demo:** Vicon + workstation | model assumes common frame/onboard self-localization; experiment stack not fully enumerated |

## 1.2 Safety / lifecycle / capture / experimental evidence

| Axis | P0003 | P0004 | P0008 | P0009 | P0010 | P0012 |
|---|---|---|---|---|---|---|
| Agent-agent collision safety | **Y theorem** | **P** close-range phase separation; full problem collision avoidance left future | **Y theorem** via safe radial controller | N | **Y** CBF layer | not a core theorem |
| Environmental obstacles | N | N | N | N | danger density/potential; not obstacle-capture geometry | N |
| Persistent patrol/monitoring | N | N | N | N | **Y/P** persistent fixed-point monitoring objective concurrently with encirclement | **P** persistent protection/orbit before hostile engagement, not coverage |
| Area coverage/search | N | N; far-range requires sensing path | N | N | **N** (fixed spot placement ≠ area coverage/search) | N |
| Dynamic subgroup | N | N (new robots can enter ring, but no target-specific subgroup) | **P** hardware tolerates add/remove robots; externally induced | N | N | N; fixed 2 guardians |
| Task switching | N | far→near controller switching | controller variants, not mission-role switching | variable-scale/reference adaptation | **N** objectives concurrent | **Y** protected-target → hostile encirclement → takedown |
| Post-task/capture release | N/A | N/A | N/A | N/A | N/A: no capture task completion | **N** |
| Return to coverage/search | N | N | N | N | N | N |
| Repeated target arrivals | N | N | N | N | N | N |
| Capture/interception semantics | geometric enclosing only | geometric enclosing only | encirclement only | enclosing/tracking only | no capture; optimization stationary point | formal capture when `r≤r_c`; real direct-impact neutralization |
| No-escape guarantee | N | N | N | N | N | **N** in PE sense |
| Theorem guarantee | global formation + collision | reachability/invariance + enclosing | exponential encirclement + decentralized estimation + collision | FOV-feasible reference + arbitrarily small tracking errors | convergence to stationary set/local minimum + no Zeno | uniform observability; bounded estimation/encirclement errors |
| Physical experiment | N | N | **Y**, Khepera ground | **N — SCREEN CORRECTION** | **Y**, ground + aerial | **Y**, UAV interception |
| Real UAV | N | N | N, UAV simulation only | N | **Y**, Crazyflie but Vicon/workstation | **Y**, direct-impact demo |
| Onboard/offboard caveat | simulation | simulation | onboard sensors/relative localization; broadcasts | simulation | Vicon + single workstation hosts robot comm nodes | onboard sensing/self-localization assumed; exact compute stack incompletely reported |

---

# 2. Classical encirclement 到底已经解决什么？

## 2.1 它早就不只是“画一个圈”

[原文 + AI判断] 六篇合起来说明 classical encirclement/control lineage 已经覆盖相当宽的工程边界：

1. **极简 local geometry + no communication**：P0003 仅用 target + one-successor relative vectors，就能形成 3-D target-centered regular formation，并给 agent collision guarantee。
2. **finite sensing + nonholonomic + visibility invariance**：P0004 用 bounded unicycles、distance/bearing、hybrid reachability/invariance，使 near-target visible region正不变，并在有 sensing path 时把 far agents逐步拉入 enclosing ring。
3. **moving 3-D target + decentralized estimation + collision safety**：P0008 不仅给 controller，还明确解决 global-quantity propagation、connected communication、finite-size collision；hardware甚至有 blind-zone lidar + mutual localization。
4. **FOV/motion constraints + uncertain nonholonomic tracking**：P0009 从 reference geometry 直接保证 target保持在 fixed camera FOV，再用 PPB控制。
5. **multiobjective persistence**：P0010 证明 classical distributed optimization 可以让 encirclement、fixed-spot monitoring、danger avoidance **concurrently** 存在，且有 real heterogeneous robots。
6. **noisy range perception → state estimation → interception**：P0012 把 range-only noisy sensing、active observability/KF、mode switching、radius contraction和 real UAV direct impact串起来。

因此，`classical = full-state static-target ring formation` 已经是错误的过度简化。

## 2.2 但经典“encirclement”的 terminal semantics 仍通常很弱

[AI判断] P0003/P0004/P0008/P0009 的终态核心仍是：
- 距目标一个设定 radius；
- angular separation/regular polygon；
- tracking/circular motion；
- visibility/safety。

这与 R-PE-01 的：
`no-escape closure → maintain closure → inward contraction → capture set`
不是同一层。

P0012 是本批明确的例外：它真正让系统从 encirclement 进入 interception/neutralization；但其 formal capture semantics 和 P0028 的 game guarantee仍不同。

---

# 3. Classical “local information”实际有多 local？

## 3.1 从强到弱不能只看论文是否写 distributed/local

### P0003 — raw local，但 target 对每台 robot 直接可见
[原文] 每台只测 target relative vector + one successor relative vector，无通信。  
[AI判断] 这是真正 local geometry，但不是 intermittent enemy knowledge；目标没有 discovery/loss。

### P0004 — finite range是真的，但 connectivity 假设很强
[原文] 在 `D0` 内 target/others可感知；outside agent若不能直接看 target，也假设存在 multi-hop sensing chain 最终通到 target/inside agent。  
[AI判断] 它解决“有 sensing path 时的有限范围 enclosing”，而不是 unknown-target search。

### P0008 — decentralized computation，最终信息近似 global
[原文] 一个 informed robot知道 `(p_T,\dot p_T,R_T,\dot R_T)` 即可；Eq. (34) + Proposition 4 使所有 robot estimates 收敛到这些 global quantities。hardware里，laser只看240°，但 measurements+odometry broadcast 后 mutual localization重建 blind-zone agents/target。  
[AI判断] 这是最清楚的 evidence：**distributed ≠ partial observation**。

### P0009 — FOV是真的，但被当约束而非 observation process
[原文] target camera projection必须永远留在 `[-β,β]`；reference生成同时输入 target velocities/trajectory。  
[AI判断] target在坏 reference 下可出 FOV，但本文的解决方式是“设计不让它出 FOV”，而不是“出了以后如何在缺失信息下行动”。

### P0010 — local knowledge 指 optimization locality，不是 enemy locality
[原文] 每 robot只持 local cost与 local states，并经 neighbors tracking aggregate。target `b` 本身是 known static parameter。  
[AI判断] “local measurements”不能转写成“每台只知道自己局部发现的 target”。

### P0012 — raw observation最弱，但 estimator把它提升为 state estimate
[原文] hostile只给两台 guardian noisy range；经过 range difference + Kalman filter得到 3-D position/velocity estimate；两 guardian通信且有 common-frame/self-localization。  
[AI判断] 这是本批最强的 perception uncertainty classical competitor，但仍是 **partial raw sensing → global target-state estimate → control**，而不是持续在 unresolved local belief 上做 dynamic coalition decisions。

---

# 4. `distributed ≠ partial observation` 的 evidence chain

这是本轮必须固定到 canonical map 的 distinction。

### Evidence chain A — P0008
[原文] decentralized controller需要 global target/frame quantities → 只让一个 robot informed → distributed estimator Eq. (34)传播 → Proposition 4保证每台 local estimate收敛到 global quantity → controller按这些 reconstructed quantities执行。

[AI判断] 因此：
`no central controller`
≠
`each robot only knows locally visible target information`.

### Evidence chain B — P0010
[原文] distributed aggregative feedback optimization让每个 robot只存 local cost，但 auxiliary trackers `w,z` 的任务就是重建 `σ(x)` 和 global aggregate gradient；target coordinate又是 global fixed datum `b`。

[AI判断] 因此：
`neighbor-only message passing`
可以实现
`locally reconstructed macroscopic/global information`.

### Evidence chain C — P0012
[原文] raw sensor是 noisy ranges，但两 guardian通过通信与 Kalman filter估计 hostile full state。

[AI判断] partial **measurement modality** 也不等于 partial **controller state**。CoCap 的 observation novelty若要成立，必须描述“未直接看到时，agent/coalition的 belief 中究竟仍缺什么”。

---

# 5. P0009 vs P0034：FOV 语义有什么本质不同？

## P0009 — FOV as a geometric feasibility / keep-in-view constraint
[原文]
- fixed camera FOV；
- reference radius/orientation按 Eq. (17)/(21)–(23) 设计；
- 正确选择 `d` 后 target **continuously visible**；
- target motion/trajectory直接进入 reference generator；
- 无 occlusion、belief、last-seen、reacquisition；
- 全文 simulation only。

[AI判断] 它的问题是：
> “怎样让 robot trajectory 从一开始就不把 target 转出相机？”

## P0034 — FOV as actual partial observability
[R-LM-01]
- finite range；
- finite forward angle；
- building occlusion；
- target确实会 loss；
- 有 last-seen / suspect-area reacquisition；
- detection后 coordinate再 team-wide share。

[AI判断] 它的问题是：
> “target有时真的不可观测，policy怎样 search / lose / reacquire？”

### Novelty consequence
P0009 **杀死**：
- “FOV-constrained classical encirclement/reference design is new”。

P0009 **没有杀死**：
- “execution-time intermittent target knowledge + uncertainty + constrained propagation”。

P0034 已经进一步杀死“MARL首次有 FOV/occlusion/loss-reacquisition”，所以 CoCap remaining claim必须比两者都强：**strict target-information locality + uncertainty-aware coalition/lifecycle**。

---

# 6. P0010 是否已经覆盖 persistent coverage/patrol + encirclement？

## Short answer
**覆盖了“concurrent monitoring objective + encirclement”，但没有覆盖 CoCap 意义上的 persistent coverage/search lifecycle。**

### 它真正做了什么
[原文]
- O1：所有 robot共同 encircle **known static target**；
- O2：某些 robot靠近预先 assigned fixed points `s_l`；
- O3：远离 danger density；
- 三个 cost从始至终同时存在（Eq. (14)）；
- 没有 detection event、target arrival或 capture event。

### 它没有做什么
[原文 + AI判断]
- 没有 area coverage/search metric；
- 没有“平时全队 coverage”；
- 没有 target encounter触发 role change；
- 没有从 whole team中动态抽出 capture subgroup；
- 没有 target completion；
- 没有 coalition release；
- 没有 return-to-patrol/coverage。

### P0010 vs P0033
- **P0010:** known static target + all-team encirclement objective + fixed sensitive-spot monitoring，concurrent continuous optimization。
- **P0033:** fixed scout/pursuer role classes；scouts继续 exploration，pursuers追 multi-target；target information传播，但 role counts/classes预定义。
- **共同缺口:** target-triggered dynamic join/leave + post-capture release。

[AI判断] 所以 broad novelty `encirclement while other monitoring continues` 已经死亡；但 `coverage → encounter → dynamically recruit → capture → release → coverage` 仍活着。

---

# 7. 是否存在真正的 post-capture release / return-to-coverage？

## Batch answer: **没有**

逐篇看：
- P0003/P0004/P0008/P0009：没有 physical/terminal capture，自然没有 post-capture。
- P0010：没有 capture completion；目标持续存在，steady-state objectives一直同时优化。
- P0012：有 interception/neutralization，但论文在完成 engagement 后结束，没有 guardians解除 coalition并返回 patrol/coverage。

### 需要特别排除的 false positives

**P0008 add/remove robots ≠ coalition release.**  
[原文] hardware可以人工 add/remove/kidnap robot后自动重建 ring。  
[AI判断] 这是 dynamic cardinality robustness，不是因为 target captured而让某 subgroup主动离队去恢复 coverage。

**P0010 monitoring + encirclement ≠ recovery.**  
它是同一时刻的 cost tradeoff，没有任务完成边界。

**P0012 protection→interception switching ≠ post-capture recovery.**  
它有前半段 lifecycle switching，但缺最后的 `release → resume`。

因此当前最值得 focused search 的 lifecycle node仍是：

`terminal capture/task completion`
→ `coalition dissolution/release`
→ `return to patrol/coverage`
→ `ready for repeated arrivals`.

---

# 8. P0012 把 encirclement→interception 做到了什么程度？

## 8.1 Sensing / estimation
[原文]
- hostile state不共享；
- 两 guardian各自 noisy range；
- range difference形成 LTV linear observation Eq. (9)；
- Kalman filter Eqs. (10)–(13)估计 3-D position/velocity；
- AS “vibrating string” motion确保 guardian baseline persistent excitation；
- Theorem 1给 hostile estimation mean-square bounded exponential convergence。

这是比“target position always known”明显更强的 classical perception result。

## 8.2 Hybrid encirclement → interception
[原文]
- far zone：围 protected target；
- warning zone：转围 hostile target；
- takedown zone：继续 hostile encirclement并逐步把 radius `r` 收到 `r_c`（Eq. (16)）；
- Definition 2：`r≤r_c` 定义 captured/taken down。

所以 transition不是一句应用愿景，而是 controller中的显式 mode switch + contraction。

## 8.3 Formal guarantee 的边界
[原文]
- Theorem 2：protected-target AS encirclement error bounded；
- Theorem 3：hostile-target AS encirclement error bounded；
- uniform observability / KF error有严格分析。

[AI判断]
- 没有 `∀ admissible hostile control` 的 winning/capture theorem；
- hostile acceleration是 stochastic heavy-tail，而不是 strategic best response；
- Definition 2 把“capture”绑定到 commanded encirclement radius，小于 `r_c` 并不等价于一般 PE no-escape theorem。

## 8.4 Physical evidence
[原文] real UAV demo中两 guardians 最终 **direct impact** neutralize hostile。  
因此，“classical encirclement只能围，不能转实际 interception”已经彻底不成立。

---

# 9. P0012 vs P0028：control/interception bridge vs game/capture bridge

| Dimension | P0012 | P0028 / R-PE-01 |
|---|---|---|
| Core bottleneck | noisy perception + estimation + physical engagement | faster evader 的 speed-aware no-escape + guaranteed capture |
| Target state | noisy range → KF full-state estimate | target geometry/state用于 no-escape control |
| Opponent | non-cooperative stochastic maneuvering | free-moving evader；theorem针对任意 strategy under assumptions |
| Encirclement certificate | AS opposite geometry + bounded error | occupied-angle / escape-gap closure |
| Transition to capture | zone switch + scheduled radius contraction | maintain no-gap enclosure + radial hunting |
| Capture semantics | `r≤r_c`; hardware direct impact | positive capture radius under sufficient geometric/speed conditions |
| Formal guarantee | estimation + encirclement convergence | no-escape/capture sufficient guarantee |
| Best CoCap lesson | perception uncertainty can be classical and actively managed | capture feasibility must distinguish ring from no-escape |

[AI判断] 两者不是谁替代谁，而是两条正交 bridge：
- P0012：**perception/control → real interception**
- P0028：**game geometry → strategy-robust capture**

CoCap若要更强，应该把二者的优点连接到 `belief/uncertainty-aware capturability + dynamic coalition lifecycle`，而不是再声称“从 encirclement 到 capture”。

---

# 10. 三个 terminology boundary 必须进入 canonical map

## 10.1 `distributed ≠ partial observation`
- P0008/P0010 是直接反例；
- distributed algorithm可以通过 local communication重建 global/macroscopic quantities；
- 所以 paper写“distributed/decentralized”时，必须另查 target information到底从哪来。

## 10.2 `monitoring/patrol + encirclement ≠ post-capture recovery`
- P0010同时优化 monitoring + encirclement；
- 但没有 task completion、release或 return。
- 因而“并发任务”与“完整 mission lifecycle”必须分栏。

## 10.3 `enclosing / target-capturing ≠ PE capture`
- P0003/P0004 中 `capture` 主要指目标中心均匀环绕；
- P0008甚至把 “escape window” 用作巡环间隔，不是 target escape feasibility；
- P0012有 physical interception，但 formal guarantee仍不是 P0028 的 strategy-quantified no-escape capture。

---

# 11. Classical Boundary Corrections

### Correction 1 — P0009 physical evidence
**SCREEN CORRECTION.**  
S-CE-01 将 P0009 标为有 mobile-robot experiment。完整 PDF 只有 Sec. VI `SIMULATION STUDIES`，无 physical experiment。Abstract 的 “Experimental results” 不能替代正文 evidence classification。

### Correction 2 — “local sensing”必须至少拆成四级
[AI判断] 本批需要把此前一个宽标签拆为：
1. raw local relative measurement；
2. finite sensing/FOV constraint；
3. actual intermittent target loss/occlusion；
4. distributed/filtered reconstruction of global target state。

P0003/P0004/P0008/P0009/P0012分别占据不同层，不能统一叫 “local”.

### Correction 3 — P0004 的 far-range 不是空白，但也不是 search
[原文] Sec. 4确实给了 outside-`D0` rooted-forest/neighbor-tracking construction。  
[AI判断] 它比 SCREEN 的一句“引用 existing methods”更完整；但前提仍是 sensing graph有 path通到 target/near group，因此仍不是 unknown-target exploration。

### Correction 4 — P0008 有 dynamic cardinality，非 dynamic coalition lifecycle
[原文] hardware能 add/remove/kidnap robot后恢复 ring。  
[AI判断] 这说明 classical encirclement可对成员数变化鲁棒，但不能写成 dynamic target-wise subgroup/release。

### Correction 5 — P0012 使“classical不能 actual interception”失效
[原文] 有 real UAV direct-impact neutralization。  
[AI判断] 之后只能比较 guarantee、information、coalition与 lifecycle 强度，不能把“interception existence”当空白。

---

# 12. Lifecycle Audit

把 CoCap candidate chain重新逐项审：

`persistent coverage/search`
→ `local/intermittent detection + uncertainty`
→ `capturability estimate`
→ `dynamic support recruitment`
→ `target-wise allocation`
→ `no-escape capture`
→ `nonparticipants keep covering`
→ `capture coalition release`
→ `return to coverage`
→ `repeated arrivals`

### What classical R-CE-01 occupies
- **persistent monitoring concurrent with encirclement:** P0010，**但只是 fixed-spot monitoring，不是 area search**。
- **finite sensing / visibility management:** P0004/P0009。
- **raw partial noisy sensing + estimation:** P0012。
- **decentralized reconstruction:** P0008/P0010。
- **encirclement → actual interception:** P0012。
- **dynamic team cardinality robustness:** P0008。

### What remains unoccupied by this batch
- area coverage/search作为正常稳态 mission；
- unknown/intermittent target discovery coupled to capture；
- state-dependent coalition size / support join-leave；
- target-wise allocation under capturability；
- nonparticipants持续 coverage + participants capture；
- **capture completion后 coalition release**；
- **return to coverage**；
- repeated/new target arrivals。

### Lifecycle conclusion
[AI判断] R-CE-01 没有找到对 `capture → release → return-to-coverage` 的反例。  
这个 gap **survives and becomes more precise**：不是“classical没有 persistence”，而是“已有 persistence 主要是 concurrent monitoring steady state；缺的是 task-completion-triggered resource release/recovery”。

---

# 13. Sensing/Decentralization Audit

### Strong classical results that already kill weak sensing claims
- finite sensing range + visibility invariance — P0004；
- direct local/no-communication target-relative control — P0003；
- FOV-constrained tracking — P0009；
- onboard blind-zone relative sensing + distributed mutual localization — P0008；
- noisy range-only hostile estimation — P0012。

### What still distinguishes the candidate CoCap problem
[AI判断]
1. target can be **truly unknown/unseen for an agent** at execution；
2. information传播不自动让所有人获得 exact/global target state；
3. belief retains uncertainty/age/occlusion semantics；
4. recruitment/assignment decisions直接依赖这种 uncertainty；
5. target information quality改变 required coalition/support capacity。

因此，不应再写：
> “CoCap uses local sensing, unlike classical methods.”

更准确的候选 wording 是：
> “CoCap targets coalition recruitment and capture under **intermittent, non-globally reconstructed target beliefs**, while classical encirclement often either maintains visibility or reconstructs the needed target/macroscopic state through sensing/communication/estimation.”

这仍是 `[AI判断]`，需 focused literature closure 后再冻结。

---

# 14. R-LM-01 对接：Classical literature 又侵占了哪些 gap？

## P0010 vs P0033 — exploration/patrol persistence
- P0033 已说明 fixed scouts可在 pursuers tracking时继续 explore。
- P0010 又说明 non-RL distributed optimization可在 encirclement时持续 fixed-spot monitoring。
- [AI判断] 因此 **“pursuit/encirclement期间仍保留其他巡逻/监测目标”不是 CoCap novelty**。
- surviving distinction：动态 role recruitment/release + area coverage recovery，而不是 concurrent objectives本身。

## P0009 vs P0034 — FOV/local sensing
- P0009占据 classical FOV-feasible control；
- P0034占据 RL finite FOV/range/occlusion/loss-reacquisition。
- [AI判断] standalone `local sensing`, `FOV`, `target loss/reacquisition` 都不能作为 CoCap主 novelty。
- surviving distinction：post-detection也不做 global exact broadcast的 belief/uncertainty + coalition decision coupling。

## P0012 vs P0035/P0042 — meaningful capture/interception
- P0035/P0042 已有几何 meaningful capture；
- P0012又给 classical physical UAV interception；
- P0028已有 no-escape theorem bridge。
- [AI判断] `meaningful capture`、`physical interception`、`encirclement→capture` 都已不能独立承载 novelty。
- surviving distinction：**capturability-aware dynamic coalition + information uncertainty + persistent resource lifecycle**。

---

# 15. Novelty Impact

## Standalone novelty statements that further die after R-CE-01
[AI判断]
- “classical encirclement assumes global/full target sensing” — false；
- “finite sensing/FOV-constrained encirclement is new” — false；
- “decentralized encirclement means each agent only has local enemy knowledge” — false as a comparison premise；
- “persistent monitoring together with encirclement is new” — false；
- “classical encirclement cannot transition to actual interception” — false；
- “range-only/noisy local sensing cannot support actual aerial interception without RL” — false；
- “dynamic number of encircling robots is inherently a learning-only capability” — false (P0008 hardware shows add/remove robustness)。

## Surviving candidate gap after R-PE-01 + R-LM-01 + R-CE-01
[AI判断]

`persistent area coverage/search`
→ `genuinely local/intermittent target beliefs, not immediately globally reconstructed`
→ `uncertainty-aware coalition capturability C(S,j)`
→ `dynamic support join/leave and adaptive capacity`
→ `target-wise resource-feasible assignment`
→ `no-escape / physical capture`
→ `nonparticipants maintain coverage`
→ **`capture completion → coalition release → return to coverage`**
→ **`repeated/changing target arrivals`**.

这个 gap 比 R-LM-01 后更窄：  
**“concurrent persistence”已部分被 P0010 占据；“classical interception”已被 P0012 占据。现在 lifecycle novelty真正集中在 event-driven resource cycling 和 belief-aware coalition feasibility。**

---

# 16. 是否必须开 focused search？

## Decision: **YES，但只开 lifecycle-focused search，不再做 broad classical encirclement search。**

R-CE-01 已经把 local sensing/FOV/decen/interception boundary 压得足够清楚；当前最大 unknown 不再是“classical能不能 local/FOV/intercept”，而是：

> 是否已经有人系统实现过 **target-triggered coalition formation → capture completion → coalition dissolution/release → resume coverage/patrol → repeated threats**？

如果不查这个 node，就不能把 post-capture lifecycle 当作 defensible novelty。

---

# 17. Recommended Focused Searches

以下只给 query themes；**本 READ 会话不自行搜索。**

### FS-LIFE-01 — post-capture release / return-to-coverage
Core concepts:
- `multi-robot post-capture return to patrol`
- `pursuit task completion coalition release coverage`
- `target capture resume surveillance multi-robot`
- `encirclement completion return to coverage`

Goal: 找明确有 **terminal task event + resources re-enter coverage/patrol** 的系统，而不是 concurrent steady-state monitoring。

### FS-LIFE-02 — dynamic role/coalition dissolution after capture
Core concepts:
- `dynamic coalition formation dissolution pursuit capture`
- `role release after target capture multi-agent`
- `reassignment after interception multi-robot`
- `task-triggered subgroup join leave pursuit`

Goal: 判断 dynamic support recruitment/release 是否已有 classical/distributed lineage。

### FS-LIFE-03 — persistent defense with repeated arrivals
Core concepts:
- `persistent swarm defense repeated intruders`
- `patrol pursuit repeated target arrivals multi-robot`
- `persistent surveillance intrusion interception repeated`
- `coverage interception recurring targets`

Goal: 验证 CoCap 最后一个 lifecycle link `ready again for new targets` 是否已有成熟 lineage。

### FS-INFO-COAL-01 — local sensing + dynamic coalition capture
只在 MASTER 认为 capturability head 是核心贡献时开：
- `local sensing dynamic coalition pursuit capture`
- `uncertain target state coalition formation interception`
- `belief-aware multi-robot pursuit assignment`
- `distributed target belief coalition recruitment`

Goal: 不再搜 generic local sensing，而是搜 **information uncertainty直接决定 coalition size/membership** 的交叉点。

---

# 18. Current answers to the 11 mandatory R-CE-01 questions

1. **Classical encirclement 到底已经解决什么？**  
   [AI判断] 已覆盖 geometric enclosing、moving target、bounded nonholonomic control、finite sensing/visibility invariance、decentralized global-state estimation、collision safety、FOV feasibility、multiobjective monitoring、noisy-range estimation和 actual UAV interception；远不止静态/full-state ring。

2. **Classical “local information”实际有多 local？**  
   从 P0003 direct local sensing 到 P0012 noisy range都有，但多数要么保持 continuous visibility，要么通过 communication/estimator重建 target/global quantities；严格 intermittent unresolved beliefs 并非常态。

3. **`distributed ≠ partial observation` evidence chain？**  
   P0008 和 P0010 已明确证实；P0012又证明 partial measurement可被 filter升级为 full-state estimate。

4. **P0009 和 P0034 的 FOV 语义本质不同？**  
   P0009 = keep-in-view geometric constraint；P0034 = target observation availability会真实 loss/occlude/reacquire。

5. **P0010 是否覆盖 persistent coverage/patrol + encirclement？**  
   只覆盖 concurrent fixed-spot monitoring + known-target encirclement；不覆盖 area coverage/search或 event-driven mission lifecycle。

6. **是否存在真正 post-capture release/return-to-coverage？**  
   本批 **没有**。

7. **P0012 encirclement→interception 到什么程度？**  
   做到 noisy-range estimation、active observability、显式 zone switching、radius contraction、real UAV direct impact；但 formal theorem不是 strategy-robust capture theorem。

8. **P0012 vs P0028？**  
   P0012是 perception/control/interception bridge；P0028是 no-escape/game/capture-guarantee bridge。

9. **哪些 CoCap novelty statements 进一步死亡？**  
   generic classical full-state assumption、FOV classical novelty、concurrent monitoring+encirclement、classical cannot intercept、range-only actual interception、dynamic-cardinality-only novelty。

10. **当前 surviving lifecycle gap？**  
    event-driven `coverage/search → encounter → recruit → capture → release → coverage → repeated arrivals`，且 recruitment 需与 uncertain local belief/capturability连接。

11. **是否必须开 focused search？**  
    **是。** 优先 lifecycle/release/repeated-arrival，不再 broad 搜 FOV/local sensing。

---

# 19. Conflicts / uncertainty notes

- **P0009 abstract vs body:** Abstract写 “Experimental results”，但正文只有 `SIMULATION STUDIES`；本批按正文 evidence将 physical experiment纠正为 No。
- **P0009 information pipeline:** Introduction强调 onboard relative-position sensing，但 Sec. III reference generator显式输入 target velocities/trajectory；全文没有 estimator。准确表述应是“FOV-aware reference tracking with relative-position motivation”，不应宣称已解决 intermittent target-state estimation。
- **P0004 collision wording:** close-range Theorem/Remark有 separation-based no-collision性质，但 conclusion仍把 collision avoidance列 future work；因此只标 **partial/local-scope safety**, 不写完整 global hard-safety solution。
- **P0012 onboard/offboard:** paper model/claims支持 onboard range + onboard self-localization、无 external ground guidance；real experiment section未完整暴露 compute/localization stack，所以不额外推断 fully onboard autonomy。
- **P0012 capture theorem:** physical direct impact是实验事实；formal theorem是 estimation/encirclement bounded convergence，不能静默升级为 `∀ strategic evader` capture guarantee。

---

# NEW PAPERS

None. 本批严格没有扩展到六篇之外的新 CE papers。

# UPDATED PAPERS

- P0003 — READ complete；确认 `target-capturing` = geometric enclosing/tracking；补充 successor temporary invisibility simulation。
- P0004 — READ complete；确认 finite sensing + visibility invariance + rooted sensing-chain global entry，不是 unknown-target search。
- P0008 — READ complete；确认 one-informed-robot → distributed global-quantity reconstruction；补充 blind-zone lidar + broadcast mutual localization与 add/remove robustness。
- P0009 — READ complete；**SCREEN CORRECTION:** physical experiment → simulation only；FOV = keep-in-view geometric constraint。
- P0010 — READ complete；确认 concurrent fixed-spot monitoring + known-target encirclement，不是 post-capture lifecycle；real demo依赖 Vicon/workstation。
- P0012 — READ complete；确认 noisy-range/KF + hybrid encirclement→interception + real direct-impact UAV；formal guarantee非 strategic capture。

# MUST READ

R-CE-01 六篇全部完成。建议维持六篇 `MUST READ` map role。

# MAP

本批不改变其他 paper decision。无新增 MAP。

# ARCHIVE

None.

# TAXONOMY CHANGES

[AI判断] 建议 MASTER 合并时把以下 distinctions 固化到 canonical map：

1. `distributed/decentralized execution` vs `partial target observation`;
2. `raw local sensing` vs `distributed/filtered global-state reconstruction`;
3. `FOV geometric keep-in-view constraint` vs `actual target-loss/occlusion/reacquisition`;
4. `finite sensing with a target-rooted sensing path` vs `unknown-target search`;
5. `concurrent monitoring + encirclement` vs `post-capture release/recovery`;
6. `dynamic cardinality robustness` vs `dynamic target-wise coalition membership`;
7. `geometric enclosing/target-capturing` vs `physical interception` vs `strategy-guaranteed PE capture`.

# SEARCH GAPS

Highest-priority unresolved nodes:
- post-capture coalition release + return to coverage/patrol;
- task-triggered dynamic join/leave after target completion;
- persistent coverage/defense under repeated target arrivals;
- local/intermittent target belief directly coupled to dynamic coalition size/capturability。

Broad searches for generic FOV/local sensing/encirclement→interception are **not** justified by this batch。

# CONFLICTS / UNCERTAINTIES

- P0009 SCREEN physical-experiment classification corrected。
- P0009 target-information acquisition mechanism is underspecified relative to its “onboard relative position” claim。
- P0004 collision guarantee is scoped；do not promote to full global safety。
- P0012 experiment infrastructure does not justify stronger onboard-compute claims than paper states。
- No evidence in these six papers of post-capture resource release/recovery。

---

# Classical Boundary Corrections

1. `target-capturing` in P0003/P0004 is enclosing terminology, not PE capture。
2. classical local sensing ranges from raw local vectors to finite sensing/FOV/noisy range；“classical assumes global target state” is untenable。
3. P0008/P0010 prove `distributed ≠ partial observation`。
4. P0010 proves concurrent monitoring + encirclement, but not recovery lifecycle。
5. P0012 proves real classical encirclement→interception；only guarantee semantics remain distinct from P0028。

# Lifecycle Audit

**Survives:**  
`persistent coverage/search → target encounter → dynamic recruitment → capture → coalition release → return to coverage → repeated arrivals`。

**Partially occupied:** concurrent monitoring during encirclement (P0010), fixed scouts during pursuit (P0033), pre-interception protection switching (P0012)。

**Still not found:** terminal-capture-triggered coalition dissolution/re-entry。

# Sensing/Decentralization Audit

- P0003: direct target + one neighbor, no comm。
- P0004: finite range, but target-rooted sensing path assumed。
- P0008: local raw sensor + connected communication → effectively global reconstructed quantities。
- P0009: FOV kept valid by reference design；no intermittent belief。
- P0010: distributed optimization locality, known target。
- P0012: noisy range-only raw sensing → KF full target-state estimate。

**Canonical takeaway:** target-information topology must be tracked separately from controller centralization。

# Novelty Impact

CoCap can no longer rely on:
- generic local sensing/FOV；
- distributed encirclement；
- persistent monitoring during encirclement；
- encirclement→interception；
- noisy range-based aerial interception；
- dynamic team-size tolerance。

The candidate contribution must be integrated:
**strict/intermittent information + uncertainty-aware coalition feasibility + dynamic join/leave + persistent capture/recovery lifecycle**。

# Recommended Focused Searches

Priority:
1. **FS-LIFE-01:** post-capture return-to-coverage / patrol recovery；
2. **FS-LIFE-02:** dynamic role/coalition release after capture；
3. **FS-LIFE-03:** repeated intruder arrivals / persistent swarm defense；
4. **FS-INFO-COAL-01:** local uncertain sensing + state-dependent coalition recruitment, only if MASTER keeps `C(S,j)` central。

Do **not** launch broad CE/FOV/interception search from this READ session。

# FOLLOW-UP PAPERS

No new paper added or searched。

For future MASTER comparison only, reuse already indexed/read nodes:
- P0033 — concurrent exploration+pursuit；
- P0034 — literal FOV/occlusion/loss-reacquisition；
- P0035 — multi-target/scalability；
- P0042 — explicit assignment/subgroup capture；
- P0028 — no-escape→capture guarantee。

This READ session stops here and does not open R-LM-02 or any Search.
