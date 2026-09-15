# R-PE-01 — CoCap-Relevant Pursuit–Evasion Theory Bridge

## Batch scope

本批 READ 只覆盖：P0016、P0019、P0024、P0025、P0028。目标不是再次摘要五篇论文，而是把它们连成一条可供 CoCap 方法设计讨论使用的理论骨架：

**reach-avoid semantics → capturability certificate → coalition feasibility → task assignment → no-escape encirclement → actual capture**。

证据标签：`[原文]`=上传正式 PDF/正文直接支持；`[AI判断]`=本批综合解释或 CoCap 映射。

---

## 1. PE 理论链最终应该怎样画？

### 1.1 Semantic layer — “可捕获”首先是一个量词命题

[P0019 原文] Reach-avoid 不是“存在一条能到 target 的轨迹”，而是：存在 non-anticipative strategy，使得对任意 competing input，都能命中 target 且在此之前不违反 avoid/state constraint。terminal-time version 的核心集合为

`RA(t,R,A)={x | ∃γ, ∀v, x(T)∈R ∧ ∀τ∈[t,T],x(τ)∉A}`，

并由 value `V` 的 zero sublevel set 表示：`RA={V≤0}`（P0019 Eq. (2)–(4), Proposition 1）。any-time version把命中时刻也纳入存在量词，并对应 `V~` 与 Eq. (11)。

[AI判断] 因而对一个 target，“可捕获”的理论本体不应该定义成“距离小于某阈值”，而应该先固定 game orientation 后问：

> **是否存在 pursuer/coalition strategy，使得对 target 的任意 admissible evasion strategy，都能在 escape/goal condition 发生前进入 capture set？**

这就是 capturability certificate 的语义核心。

### 1.2 Certificate layer — winning value / barrier / geometric primitive

同一个语义可由不同计算对象实现：

- **HJ/reach-avoid value certificate**（P0019/P0024）：`V(x)≤0`/`>0` 的 sign 表示某方 guaranteed reach-avoid，zero level set 是 feasibility boundary。优点是 dynamics/general constraints 通用；缺点是 joint-state dimension disaster。
- **Analytical barrier / winning-region certificate**（P0016/P0025）：在 simple motion、特定 convex geometry 下，直接构造 PWR/EWR/barrier，避免数值 HJI。
- **Dominance geometry**（P0016/P0025）：Voronoi/Apollonius/ER 只表示“谁先到某物理点”，是构造 barrier 的 primitive，不等于 winning region。
- **No-escape angular certificate**（P0028）：对 faster evader，用 speed-ratio-derived occupied angles 判断是否仍存在 escapable heading；这是 capture phase 的几何 certificate，但还必须配合 inward approach 才能最终 capture。

### 1.3 Decomposition layer — 从高维 multiplayer game 降到小规模 certificates

[P0024 原文] 一条路线是只计算 1v1 outcome，然后构造 defender-attacker bipartite graph；maximum matching size `m` 保证 defenders 至少能阻止 `m` 个 attackers，`N_A-m` 是能到 target 数量的 upper bound。这里是 **pairwise lower-bound guarantee**。

[P0025 原文] 另一条路线是在 certificate stage 就允许 coalition：先计算 coalition-vs-one-evader PWR，再把 feasible coalition-target pairs 放进 assignment。其特定模型下 Lemma 5 证明 `n_k≥3` coalition 若可赢，必有 2-pursuer subcoalition 也可赢，因此 reduced assignment 只需 size 1/2 coalitions；Theorem 5 的 0–1 program 在“最多 guaranteed intercepted evaders”意义下 global-optimal。

[AI判断] 所以正确图示不是“pairwise matching 之后再加 support”，而是两条层级不同的路线：

`low-D pair certificate → bipartite matching (conservative)`

与

`coalition certificate → coalition-target feasible edge/hyperedge → constrained assignment (stronger but more model-specific)`。

### 1.4 Execution layer — encirclement 必须升级为 no-escape + inward capture

[P0028 原文] 对 faster evader，单 pursuer occupied angle `θ_i=2asin(λ_i)`；group occupied angle `θ_G` 扣除 overlap 后才表示实际覆盖的 escape-heading fraction。`θ_G=2π` 表示没有 escapable angle。Theorem 2 再要求 evader 位于 pursuer polygon 内、critical polygon edges `<R_f≤2d_cλ_min`、安全距离参数满足 `R_o<R_b<R_c<R_f`，并用 radial hunting component 保持收缩，才给出“无论 evader strategy 最终 capture”的 sufficient guarantee。

[AI判断] 因此最终理论链应画为：

**Reach-avoid objective / escape condition**
→ **signed capturability certificate**
→ **coalition feasibility**
→ **resource-constrained target assignment/recruitment**
→ **speed-aware no-escape enclosure**
→ **maintain enclosure + inward contraction**
→ **capture radius reached**。

---

## 2. Capturability certificate 有哪几类？

### A. HJ signed value / reach-avoid margin
- [P0019 原文] `V≤0` 精确表征 reach-avoid membership；`V=0` 是 boundary。
- [AI判断] 适合作为 continuous teacher/margin，但 value magnitude 受 target/avoid implicit functions scaling 影响，跨任务必须 normalize。
- 强项：general dynamics、obstacles/state constraints、worst-case strategy semantics。
- 弱项：维数灾难、exact model/full state。

### B. Analytical barrier / PWR–EWR membership
- [P0016/P0025 原文] simple-motion 特定几何下可直接判断 evader initial state 是否在 coalition PWR。
- 强项：非常快、可解释，可直接生成 binary feasible edge。
- 弱项：assumptions 强，模型稍变公式可能失效。

### C. Dominance / interception geometry
- [P0016/P0025 原文] Voronoi、Apollonius、ER/BER 等。
- [AI判断] 它们更像低层 feature/certificate ingredient，不应直接等同 capturability；若没有 goal/avoid/strategy semantics，只能说明 race-to-point advantage。

### D. No-escape enclosure certificate
- [P0028 原文] `θ_E=2π-θ_G` 或最大 positive `ε_i,i+1` 衡量还剩多少 escape-heading gap。
- [AI判断] 它是 capture execution phase 的“封口” certificate；只有加 radial contraction/capture-radius condition，才能变成 actual capture guarantee。

### E. Binary vs soft/probabilistic certificate
- [原文] P0024/P0025 用 yes/no outcome 形成 graph/assignment。
- [AI判断] CoCap 更需要 `C(S,j)∈R` 或 `[0,1]` calibrated score：预测 coalition `S` 对 target `j` 的 robust/probabilistic capturability，再以 threshold/uncertainty 控制 recruitment。

---

## 3. Pairwise → coalition → assignment 的关系

### Pairwise
[P0024 原文] 对每个 `(defender i, attacker j)` 得到 1v1 outcome：如果 i 有 guaranteed winning control，就连 edge。maximum matching 只选择互不共享 endpoint 的 edges。

准确 guarantee：**matching cardinality `m` ⇒ 至少阻止 `m` 个 attackers ⇒ 至多 `N_A-m` 个能到 target**。论文没有为这句另设 numbered theorem；它位于 Sec. V-A Algorithm 2 后的正文。

### Coalition
[P0025 原文] coalition feasibility 的定义更强：`F(S,j)=1` iff `E_j` 位于 coalition `S` 的 PWR，即 `∃` coalition control, `∀` evader control，capture before target entry。

[P0025 原文] 在其 convex/simple-motion/faster-pursuer/point-capture model 中，Lemma 5 把任意 winning `|S|≥3` coalition 退化到 winning 2-pursuer subcoalition；这不是一般 PE 的 universal theorem。

### Assignment
[P0025 原文] Theorem 5 Eq. (50)：

`max c^T z`

s.t.

- `A1 z≤r`：只能选择 feasible coalition-target pairs；
- `A2 z≤1`：每个 target 最多一个 coalition；
- `A3 z≤1`：每个 pursuer 最多参加一个 coalition；
- `z∈{0,1}`。

因此 assignment 的数学本质不是“找最近的 agents”，而是：

> **在 capability constraints 与 resource conflicts 下，选一组互相兼容的 feasible coalition-target assignments，使 guaranteed covered targets 最大。**

### CoCap translation
[AI判断] 对 CoCap 最自然的 soft version 是：

`C(S,j) = estimated capturability margin of coalition S for target j`

而候选 support agent i 对已有 coalition `S_j` 的边际价值：

`Δ_i(S_j,j)=C(S_j∪{i},j)-C(S_j,j)`。

最终 utility 还应扣除：coverage loss、其他 target opportunity cost、collision/communication cost。

这比当前仅依赖 `agent-target distance` 或“邻居数够不够”的 `U_ij` 更接近 classical PE 的能力语义。

---

## 4. Encirclement → capture 需要哪些额外条件？

### 4.1 普通 ring 不够
[AI判断] “pursuers 围在 target 四周”只说明方位分散；如果 slower pursuers 留下一个 speed-aware escape gap，faster evader 仍可穿出。

[P0028 原文] 真正的 angular closure 要用 occupied angle `θ_i=2asin(V_i/V_e)` 与 adjacent coverage gap `ε_i,i+1`。只有所有 escape directions 被覆盖（`θ_G=2π`）才叫 no-gap enclosure。

### 4.2 `θ_G=2π` 仍不自动意味着 finite-time capture
[P0028 原文] 因此作者专门把每个 pursuer velocity 拆成 tangential surrounding 与 radial hunting；`h_i>0` 使 radial distance 下降。纯 surrounding 可以保持 ring/no-gap，却没有理由进入 `d_c`。

### 4.3 要维持 closure，而不是瞬时 closure
[P0028 原文] Theorem 2 用 n-pursuer polygon distance maintenance 保证 critical edge lengths 始终受限，从而 no-gap property 对 moving faster evader 保持；同时有 intercollision lower bound。

### 4.4 Positive capture radius 是关键
[P0028 原文] core theorem 使用 `d_c>0`；较慢 pursuers 的 point capture 不适用同样结果。edge threshold 与 `2d_cλ_min` 直接相连。

### 4.5 Cardinality 与速度/尺度耦合
[P0028 原文] same-speed-ratio case 至少需要足够多 pursuers 使 speed-derived angular capability cover 2π；Theorem 2 geometry 下还有

`n > π / arcsin(d_c λ_min / R_p)`

的 sufficient count relation（Eq. (49)）。

### 4.6 CoCap capture evaluation 应拆成四层
[AI判断] 不再只记录“3+ agents around target”或 ring count，而分开：

1. **closure**：最大 escape gap / `θ_E`；
2. **maintenance**：closure 连续维持多久；
3. **contraction**：coalition radial distance / capture-set margin 是否单调改善；
4. **terminal capture**：是否进入严格 capture condition。

这对当前 capture consolidation/collision audit 特别有诊断价值：能区分“不会围”“能围但有 gap”“能封口但不收缩”“收缩时碰撞/破环”。

---

## 5. 哪些结构最值得 CoCap 借鉴？

### 1. Learned coalition capturability margin
[AI判断] 优先级最高。把 P0019 的 signed value / P0025 的 PWR membership 变成一个 learned local estimator `C(S,j)`。它可以是 actor/critic encoder 上的 auxiliary head，而不是硬 HJI solver。

### 2. Recruitment based on **marginal capturability gain**
[AI判断] support agent 的价值不应等于 target distance；更合理是 `Δ_i=C(S∪{i},j)-C(S,j)`，再减 coverage opportunity cost。这样天然能表达“最近 agent 几何冗余、较远 agent 反而补 escape sector”。

### 3. Certificate-aware dynamic assignment
[AI判断] 借 P0024 的 online rematching 与 P0025 的 resource constraints：target selection 不只输出目标 id，还应维护“当前 target coalition 是否足够、是否还需 support、何时 release”。

### 4. Escape-gap geometry as state/reward/evaluation feature
[AI判断] P0028 的 `θ_E` / max positive adjacent gap 比纯角度均匀性更直接对应 faster-target escape feasibility。适合作为 state feature、dense shaping 或 evaluation；若 speed estimate unreliable，应做 robust bound。

### 5. Theory-guided curriculum / offline teacher
[AI判断] 用 low-dimensional exact/analytical certificate 生成 curriculum：deep winning → near barrier → partial sensing → dynamics mismatch → multi-target/repeated arrivals。这样 classical theory 提供 supervision，但 final policy仍学习对强 assumptions 的放松。

---

## 6. 哪些 classical assumptions 是 CoCap 真正需要学习方法来放松的？

| Classical assumption | 本批来源 | CoCap 需要的 relaxation |
|---|---|---|
| Full/current state known | P0016/P0025，P0028 target position always available | local detection、intermittent target visibility、neighbor communication、belief/uncertainty |
| Exact known dynamics/input bounds | P0019/P0024 | learned/strategic evader、model mismatch、uncertain speed |
| Simple-motion / instantaneous heading | P0016/P0025/P0028 | UAV acceleration/turn-rate/velocity dynamics、collision constraints |
| Pursuer faster | P0016/P0025 | equal/faster evader；多人 synergy |
| Convex/clean geometry | P0025 | obstacles、boundaries、nonconvex free space、boundary-assisted capture |
| One-shot/static assignment | P0025 | dynamic support join/leave、reassignment、target appearance/disappearance |
| Pairwise sufficiency | P0024 | true coalition synergy / hyperedge feasibility |
| One target in capture execution | P0028 | concurrent multiple targets / coalition competition |
| 2D enclosure | P0028 | 3D UAV no-escape geometry or task-specific 2.5D approximation |
| No persistent noncapture duty | P0024/P0025/P0028 | coverage/search continues for nonparticipants, post-capture return, repeated lifecycle |

[AI判断] 这张表也界定了 learning 的合理叙事：**不是用 MARL 重做一个已有解析问题，而是学习 classical certificate 在 partial information、unknown dynamics、dynamic lifecycle 与 realistic UAV constraints 下的近似/鲁棒版本。**

---

## 7. Focused search gaps exposed by READ

### Gap A — local/partial-information coalition capturability
本批没有回答：仅靠 local observation + neighbor messages，怎样估计 `C(S,j)` 并给出 calibration/robustness？这是最直接的 theory→MARL bridge。

### Gap B — dynamic coalition recruitment/release with guarantees
P0024 有 online rematching，但只有 1v1；P0025 有 coalition feasibility，但基本是 snapshot/one-shot assignment。二者之间缺一个：**在线多人 support join/leave + resource reallocation + capture guarantee/monotonicity**。

### Gap C — persistent lifecycle task allocation
本批 classical papers 几乎不处理：未参与者继续 coverage/search、capture 后回 coverage、新 target 重复到达。P0016 反而把 sequential capture/spatio-temporal coupling 明确列为 open limitation。

### Gap D — obstacle/boundary-aware encirclement-to-capture
P0028 的 guarantee 无 environmental obstacles；CoCap 当前又有 boundary/obstacle-assisted stationary capture。需要 focused search：obstacle-assisted enclosure、barrier/no-escape geometry、CBF/MPC safety + cooperative capture。

### Gap E — 3D / nonholonomic / higher-order certificate
P0025/P0028 的 strongest formulas 都是 2D simple motion。P0026/P0029 已在 canonical map 中提供部分 3D heterogeneous / nonholonomic extension，应优先 READ/SCREEN 后再决定是否开新 search。

---

## 8. Novelty impact

[AI判断] 本批 READ **没有推翻** CoCap 当前 candidate gap，但明显收紧了 novelty 表述。

不能再宽泛声称：
- “我们首次根据 pursuit capability 做 target assignment”——P0024/P0025 已明确覆盖；
- “我们首次让多个 pursuers 组成 coalition 才能拦住 target”——P0025 已有 exact coalition certificate + assignment；
- “我们首次把 encirclement 转成 capture”——P0028 已有 faster-evader sufficient capture theorem；
- “用 target distance + support number 就是合理 recruitment theory”——classical work表明这最多是很弱 proxy。

更可信的 candidate gap 应收敛到：

> **在 multi-UAV、multi-target、局部/间歇 sensing 与 constrained communication 下，学习一个动态 coalition capturability / escape-margin approximation，用它驱动 support recruitment 与 target allocation；同时让未参与者维持 coverage/search，capture 后释放 coalition 并回到 coverage，对 repeated/changing target arrivals 持续运行，并在 realistic UAV dynamics、obstacles/boundaries、strategic evaders 下验证。**

这仍然是一个组合型 lifecycle gap，而不是某一个 classical primitive 的首创。

---

# PROJECT_PROTOCOL HANDOFF

## NEW PAPERS
- 本批未新增 canonical paper ID。READ 中发现的 lineage papers 以 `FOLLOW-UP PAPERS` 记录，由 MASTER 决定是否纳入后续队列。

## UPDATED PAPERS
- P0016 — READ complete：理论 vocabulary/genealogy、barrier/winning/dominance/task-allocation assumptions 已抽取。
- P0019 — READ complete：terminal/any-time reach-avoid、non-anticipative quantifiers、value/HJ equations 已核实。
- P0024 — READ complete：pairwise HJI/path-defense、maximum matching guarantee 强度已核实。
- P0025 — READ complete：Assumptions 2/3、coalition barriers、Lemma 5、Theorem 5 Eq. (50) global-optimality scope 已核实。
- P0028 — READ complete：occupied angle、no-escape semantics、radial hunting、Theorem 2 capture conditions 已核实。

## MUST READ
- 本批 5 篇均建议继续保留 MUST READ；READ 已完成。
- 若后续专门设计 CoCap support/capturability head，优先二次引用：P0019、P0025、P0028。

## MAP
- P0016：PE foundations / theory organizer。
- P0019：reach-avoid semantics / HJ signed certificate root。
- P0024：pairwise certificate → matching lower-bound guarantee。
- P0025：coalition certificate → constrained optimal assignment（under strong assumptions）。
- P0028：speed-aware enclosure → no-escape maintenance → capture。

## ARCHIVE
- 无。

## TAXONOMY CHANGES
建议 MASTER 后续 merge 时显式区分以下层级：
1. `Reachability / BRS`
2. `Reach-Avoid set / value`
3. `Dominance geometry (Voronoi / Apollonius / ER)`
4. `Winning region / barrier / capturability certificate`
5. `Pairwise feasibility`
6. `Coalition feasibility`
7. `Assignment / matching / resource constraints`
8. `Encirclement geometry`
9. `No-escape closure`
10. `Inward contraction / terminal capture`

不要再把 `winning region = dominance region`、`reach-avoid = reachable set`、`ring = capture` 混写。

## SEARCH GAPS
- local/partial-information learned capturability certificate；
- dynamic coalition recruitment/release with guarantees；
- persistent coverage↔capture lifecycle + repeated arrivals；
- obstacle/boundary-assisted no-escape/capture；
- 3D/nonholonomic/higher-order certificate；
- uncertainty-calibrated/robust assignment margins。

## CONFLICTS / UNCERTAINTIES
1. **P0024 matching guarantee theorem number**：未找到编号 theorem/proposition；准确 guarantee 是 Sec. V-A Algorithm 2 后正文：“matching size m ⇒ prevent at least m attackers; `N_A-m` upper bound reach target”。不要伪造 theorem number。
2. **P0025 global optimality**：只在本文 assumptions 与“最多 guaranteed intercepted evaders” objective 下成立；不能外推为一般 multiplayer PE global optimum。
3. **P0028 `P=θ_G/2π`**：作者称 group success rate，但数学上是 occupied-heading fraction；不应在 CoCap 中无校准地解释为 capture probability。
4. **P0028 Theorem 1 vs Theorem 2**：Theorem 1 是 angular encirclement/no-gap mechanism；free-moving faster evader 的 final capture guarantee 应引用 Theorem 2 的 polygon/distance/capture-radius conditions。
5. **HJI value magnitude**：zero level/sign 有明确 reach-avoid membership 语义，但不同 `l,h` scaling 下绝对 margin 不可直接横向比较。

---

## CoCap Theory Takeaways
1. **把 `U_ij` 从“距离/邻居启发式”升级为 capturability margin**：更合理的 support value 是加入 agent 后 coalition guaranteed/likely capture feasibility 的边际增益。
2. **assignment 应消费 certificate，而不是自己发明 capability**：先估计 `C(S,j)`，再做 target allocation/recruitment；P0024/P0025 清晰验证了这种模块化结构。
3. **capture reward/evaluation 应拆分 no-escape 与 inward contraction**：`ring` 不是 capture；先封 speed-aware escape gaps，再保持 closure 并缩小半径。
4. **classical theory 最适合做 teacher/prior/curriculum，而不是在线硬 solver**：HJI/barrier 的强 assumptions 正是 CoCap 用 learning 放松的部分。
5. **CoCap 的 novelty 更像 lifecycle + assumption relaxation**：local sensing、dynamic coalition、multi-target conflicts、coverage coexistence、post-capture return、repeated arrivals、real UAV/obstacles 的组合，而非单个 PE primitive。

## Formula / theorem shortlist
- **P0019 Eq. (2), Proposition 1**：terminal reach-avoid quantifiers；`RA={V≤0}`。
- **P0019 Eq. (3)–(4), Theorem 1**：target/avoid max-value 与 HJ variational equation。
- **P0019 Eq. (5), Eq. (11), Proposition 2/Theorem 2**：any-time reach-avoid 与 freezing formulation。
- **P0024 Sec. V-A Algorithm 2 + following guarantee**：matching size `m` ⇒ at least `m` attackers prevented（无编号 theorem）。
- **P0024 Sec. V-B Algorithm 3**：continuous rematching under winning pair controls ⇒ maximum matching size nondecreasing。
- **P0025 Lemma 5 + Remark 4**：winning coalition `|S|≥3` degenerates to winning 2-pursuer subcoalition under paper assumptions；reduced matching preserves global optimum in captured-count sense。
- **P0025 Theorem 5, Eq. (50)**：feasibility + target exclusivity + pursuer exclusivity 0–1 assignment。
- **P0028 Eq. (4)–(5)**：`θ_i=2asin(λ_i)` occupied angle。
- **P0028 Eq. (8)–(11)**：escape gap / group occupied angle；`θ_E=2π-θ_G`。
- **P0028 Theorem 2 + Eq. (49)**：polygon edge `<2d_cλ_min`、safety/distance conditions + inward law ⇒ strategy-independent eventual capture；cardinality-speed-radius relation。

## Novelty impact
- Candidate gap：**survives but narrows**。
- Stronger narrative：从“我们也做 multi-UAV capture/assignment”改为“我们学习并在线使用 classical capturability structure，在 local sensing、dynamic coalition 与 persistent coverage/capture lifecycle 中放松 classical assumptions”。
- 需要避免的 novelty claim：generic task assignment、generic coalition capture、generic encirclement-to-capture。

## FOLLOW-UP PAPERS
由 MASTER 决定是否开 focused READ/SCREEN：
1. **P0026** — Yan et al., 2022, *Matching-based capture strategies for 3D heterogeneous multiplayer reach-avoid differential games*：直接检查 3D、heterogeneous speed、positive capture radius 是否提供更适合 CoCap 的 coalition margin。
2. **P0029** — Yan et al., 2024, *Multiplayer Homicidal Chauffeur reach-avoid games: A pursuit enclosure function approach*：检查 nonholonomic dynamics 下 barrier/enclosure function，连接 UAV action constraints。
3. **C. Wang et al., 2013, “A new approach of multi-robot cooperative pursuit,” Chinese Control Conference**：P0028 的 overlapping-angle predecessor，仅在需要追溯 occupied-angle genealogy 时补读。
4. focused search topic（不是具体 paper）：`partial-observation / belief-space reach-avoid + coalition assignment`, `dynamic coalition formation pursuit evasion`, `obstacle-assisted cooperative capture / boundary capture`。
