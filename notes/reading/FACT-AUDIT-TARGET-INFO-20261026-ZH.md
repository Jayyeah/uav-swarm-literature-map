# CoCap 文献地图事实审核：目标信息、通信、分配与围捕

日期：2026-10-26  
范围：按原文核对 TERL、Role-based MADDPG、KS-COAL，以及 Huang 等人在 RAS、AIS、RA-L 的三篇不同论文；另核对 TR-11（Rao 等，JAS 2026）。本文是独立证据备忘，不改文献地图主索引，也未运行实验。

## 状态标记

- **原文明确支持**：原论文正文、公式、图或补充材料直接写明。
- **需要进一步核查**：目前可访问的原文不足以确认细节；不把推断写成事实。
- **原先理解存在错误**：若旧摘要把“局部感知”或“分布式”直接等同于“没有目标坐标传播”，该概括不成立；应按各文的信息通路分别表述。

## 核心纠偏

“局部感知”“分布式执行”“不通信”是不同假设。目标位置可能由局部传感器直接看到，也可能由邻居传播，也可能在没有队间通信的情况下直接出现在每个策略的输入中。TERL 明确属于第三种：队友和障碍物受感知半径限制，但每个 pursuer 的输入含有所有未围捕 evader 的位置与速度，且文中明确说这些 evader 不论距离都可观测。Role-based MADDPG 明确假设目标位置经通信网络传给邻居。KS-COAL 的分布式联盟消息沿邻居链传播；应用段还说 SWAT 收到 Scout 传来的目标位置。AIS PGM 则明确写了通信禁用，只用个体局部感知。不能从 “local/distributed” 单词反推目标坐标一定未传播。

## 感知、发现与目标信息传播

| 论文 | 是否直接观察全部目标位置；目标如何进入任务 | 发现后传播什么信息 | 通信拓扑 | 原文证据（页码／公式／段落） |
|---|---|---|---|---|
| **TERL**，IROS 2025 | **原文明确支持：**是。策略观测包含全部未 encircle 的 evader，位置、速度等要素按实体组织；目标无须先由搜索器发现。每个 episode 开始时 evader 已被初始化。 | 当前实现不靠通信传播目标位置，因为 actor 输入本身就有所有未围捕目标状态。文中提到 one-way target broadcasting 是可选的实际替代方案，不是该仿真执行设置。 | 明确写明 pursuer 间无通信；执行时各自用本地 teammate/obstacle 观察和共享策略。注意“局部”只描述部分实体输入，不限制 evader 坐标输入。 | [arXiv 原文 PDF](https://arxiv.org/pdf/2503.12395)：PDF p.2，§III-A、§III-C、encirclement Eq. (1)；PDF p.3，观测向量与 CTDE；PDF p.5，§V-A episode 初始化和 entity 数。Eq. (1)：每个目标至少 3 个 pursuer 在 `d_encircle` 内，并满足角间隙限制；正文给 `max φ≤π`、`max φ≤3 min φ`。 |
| **Role-based MADDPG**，ICRA 2023 | **原文明确支持：**不是“所有 pursuer 直接观测全体目标”的充分证据。论文假设目标位置可经网络传播到相邻 agents；仿真目标在 episode 初始化时存在，所谓 scouting 是探索盲区／寻找 prospective targets，不是目标生成机制。 | 原文明确说传播 **target location**；没有把速度、置信度、目标 ID、时间戳或目标轨迹列为消息字段。 | 邻居经通信网络传播；正文没有给定通信半径、网络直径或多跳/全队广播保证。不可据此称中央广播或队内全联通。 | [ICRA 2023 论文 PDF](https://applied-complexity.org/docs/ICRA-2023.pdf)：印刷页 3291（PDF p.3），§IV 两项假设 `(b)`；该页同时说明集中式 critic 只用于训练。目标是否由任何 actor 直接获得完整坐标列表，正文证据不足，列为**需要进一步核查**。 |
| **KS-COAL**，RA-L 2024 | **原文明确支持：**没有全局直观测假设。各机器人只在自己的 sensing radius 内观测；Scout 在线覆盖并发现 target robots/resources。目标群初始空间分布对 Scout/SWAT 未知，但实验一开始已有目标实体（50 个）；不是目标出生即给所有机器人全坐标。 | 正文应用段明确说 SWAT 从 Scout 收到 **target robot positions**。联盟算法消息则含局部初始分配 `ν₀`、链变换 `Ξ`、`kᵢ`，以及邻居所知最佳 assignment/utility。 | Scout 队内、Target 队内无距离限制通信；不能窃听其他队。SWAT 仅限距离邻居，整体网络“无限次保持连通”。Scout→SWAT 位置交付在结果段明确，但正文没有说明具体跨队转发机制，与前述不能跨队窃听的建模句之间需核对补充材料/实现。 | [arXiv 原文 PDF](https://arxiv.org/pdf/2305.15729)：PDF p.2，§II-A（局部感知、队伍能力和连通假设）；PDF p.3，§III-A（Scout 在线检测）；PDF p.4，§III-B Eq. (4)–(7)（邻居消息、局部分配/最佳 assignment）；PDF p.6，§IV-B（SWAT 收到 Scout 的目标位置、任务切换）。期刊版 DOI [10.1109/LRA.2023.3332796](https://doi.org/10.1109/LRA.2023.3332796)。 |
| **Huang et al., RAS 2025**，*Hierarchical probabilistic graphical models for multi-UAV cooperative pursuit in dynamic environments* | **原文明确支持（可访问的出版方正文摘录）：**问题设为 N 架 UAV 对一个非合作目标；pursuer 有受限感知半径。不是“全体多目标位置”问题。目标在问题定义中已存在，是否须先发现、何时进入传感器范围要以完整正文核对。 | 当前可访问正文摘录没有说明目标发现后是否转发坐标。**不得**因该文讲 local perception/自组织就写成无通信。 | **需要进一步核查：**没有获得足以确认其 agent 通信假设的原文页段。 | [ScienceDirect 原文条目](https://www.sciencedirect.com/science/article/pii/S0921889024002744)，DOI [10.1016/j.robot.2024.104890](https://doi.org/10.1016/j.robot.2024.104890)：§3 Problem Statement / Kinematic Model 摘录支持“一个 target、受限感知半径”；该刊使用文章号 104890，网页摘录没有可核实的 PDF 分页。其余信息通路待取得完整 PDF 核对。 |
| **Huang et al., AIS 2025**，*Self-Organized Multitarget Pursuit … via Hierarchical PGM* | **原文明确支持：**不直接获得全部目标坐标。每架 UAV 只感知其感知半径内实体；实验把 targets 放在 pursuer 检测半径之外，再由 UAV 搜索、检测、围捕。目标实体从初始场景就存在，属于“存在但尚未被本机发现”，不是在线生成。 | **明确不做 agent 间显式通信／坐标转发**。个体利用局部目标相对位置、邻居/目标空间密度；搜索阶段另记录由自身运动产生的局部信息素痕迹。该痕迹是否被其他个体读取，原文通信禁用的设定不支持把它描述成无线消息。 | 通信禁用；本机有限感知范围。不是一跳或全联通。 | [Wiley 原文](https://advanced.onlinelibrary.wiley.com/doi/10.1002/aisy.202401110)：§3 Problem Statement；§3.3 Proposition 1（Apollonius circles）；§3.4 Eq. (7)、Definition 1；§4.2 Eq. (10)；§4.3.2（search/pheromone）；§4.4 Eq. (19)–(24)；§4.5 Algorithm 1；§5 实验初始位置；§5 真实实验硬件架构。Wiley 网页为 eLocator 2401110，当前可访问 HTML 不暴露 PDF 页断，因此**PDF 页码需补核**。 |
| **Huang et al., RA-L 2025**，*Density-Based Probabilistic Graphical Models for Adaptive Multi-Target Encirclement of AAV Swarm* | **需要进一步核查：**公开摘要支持 local spatial density 与实时 perception update；没有正文证据说明每架 AAV 是否收到所有 evader 坐标、目标是否先搜索发现、初始目标清单如何给定。 | 摘要没有明确报告队间是否传递坐标，也没有报通信消息字段。不得从 DB-PGM 或局部密度自行补齐。 | **需要进一步核查：**摘要不足以证明通信禁用、邻居通信或广播；AIS 的通信假设不能移植到 RA-L 版本。 | [IEEE DOI](https://doi.org/10.1109/LRA.2025.3583457)，期刊页码 8228–8235。当前只能核到摘要级别；页码范围可定位文章，但无法把上述信息权限主张落到某一原文页／公式，待取得全文 PDF。 |
| **TR-11 / Rao et al., JAS 2026**，*Dynamic Robust Pursuit of Multiple Evaders Under State Measurement Uncertainty in Obstacle Environments* | **原文明确支持（摘要＋补充图）：**方法输入端含多个 evaders 的 positions，并据此做动态 pursuer allocation；没有搜索/侦察/目标发现模块的描述。因此本轮能确认的是 allocation 使用目标位置输入；**不能确认**这些位置是每架 pursuer 直接全观测、某节点估计后输入，还是由局部网络传播。目标进入系统时机待核。 | 补充材料 Fig. S1 将 “Positions of Evaders” 接到 “Local Network For Auction”；说明分配环节处于局部网络 auction 中。坐标、目标 ID、标量 bid/成本中哪些实际在链路上传输，摘要和图无法判定。 | **原文明确支持：**存在 local network for auction；拓扑半径、跳数、邻居关系刷新频率和 auction 消息格式仍需论文/补充文本核对。 | [JAS 正文 DOI 页面](https://www.ieee-jas.net/en/article/doi/10.1109/JAS.2025.125684)：印刷 pp. 989–991；摘要称 distributed dynamic pursuit/allocation、state measurement noise。Fig. 1（印刷 p.989）题注说明 Euclidean distance 与 A* path length 分配对比。[官方补充材料](https://www.ieee-jas.net/fileZDHXBEN/journal/article/file/d5633e16-678c-4d80-8337-3da4303ecd23.pdf)：Fig. S1（“Positions of Evaders”→“Local Network For Auction”）；§S2 给 chance constraint 推导。 |

## 角色、任务分配、目标函数与“成功”语义

| 论文 | 固定角色？显式分配器／联盟优化器？多目标优化目标 | 探索与围捕是否争用同一资源 | 文中“成功”具体是什么 | 原文证据（页码／公式／段落） |
|---|---|---|---|---|
| **TERL** | 没有 scout/tracker 等固定异质角色。**有策略内显式 target-selection 模块**，但没有单独的组合分配器/联盟求解器。多目标的目标平衡通过奖励减少过度拥挤：按每个目标周围 pursuer 数 `P` 给合作奖励/惩罚 Eq. (5)；另有 encirclement completion reward。它优化的是策略累计奖励，不是文中另行求解的 assignment objective。 | 没有探索任务/搜索者，故无探索与围捕之间的异质资源分配。存在不同目标间 pursuer 过度集中惩罚。 | **目标级环绕并 immobilize**，不是只跟踪、接近或发生碰撞。至少 3 架满足半径与角分布条件才算 encircled；全体 evader 都被围住才算任务成功。 | [原文 PDF](https://arxiv.org/pdf/2503.12395)：PDF p.2，§III-A Eq. (1)；PDF p.3，§IV-A Eq. (5) 和 completion reward；PDF p.5，§V-A/V-B success 定义（所有 evaders 被 encircle）。 |
| **Role-based MADDPG** | 两类 reward role：track known targets 与 scout prospective targets；论文没有给出在线 role-switching/联盟优化器。结果中预先设 5 pursuers + 5 scouts。不是永久角色定理；准确说是实验配置中固定异质 reward。没有显式任务指派器。多目标追踪使用距离惩罚；scout 使用最小化最大 Voronoi cell 面积的探索奖励。 | 论文确实把 exploration vs tracking 称为 trade-off，但实验通过不同角色并行处理；未见同一资源池用优化器在 exploration 与 capture 间动态竞价。故“存在探索行为”明确，“有探索-围捕资源联合分配”不支持。 | 主目标是 tracking；奖励中的 “successful attack” 被定义为与 evader 碰撞。论文没有目标级环绕、关停或捕获后移除条件；报告距离指标而非 capture/encirclement 完成条件。 | [ICRA PDF](https://applied-complexity.org/docs/ICRA-2023.pdf)：印刷 p.3291，§V，Eq. (3)–(5)、Algorithm 1；印刷 p.3292，仿真配置和 tracking 距离指标；印刷 p.3293，Crazyflie 实验由外部电脑计算/下发控制。 |
| **KS-COAL** | **有显式分布式联盟优化器 KS-COAL**，并由 HGAN neural accelerator 选 K/初始解。任务可重分配；SWAT 会在 capture 与 resource defense 间切换。总体任务目标：最大化“捕获 target robot 数 − target team 获取资源数”。联盟 assignment 本身优化 coalition mean utility `ρ(ν)=Σ f(Rₘ,ωₘ)/M`（Eq. (2)）；`f` 的各任务细节/时间效用部分放在补充材料，不能只拿主目标代替联盟 solver 目标。KSS 是有限 K 的稳定解；不是无条件全局最优。 | **有真实任务资源竞争**：同一 SWAT 队在捕获目标与守资源间动态分配；Scout 的探索单独分队。任务目标也把捕获与目标队取资源作净效用。 | Target robot 在捕获后 immobilized；SWAT 捕获由 Apollonius-circle 交集策略触发，实验给 SWAT/target capture ranges。不要把“资源 encirclement”当成目标捕获。 | [原文 PDF](https://arxiv.org/pdf/2305.15729)：PDF p.2，§II-C 全局任务目标；PDF p.3，§III-B coalition structure Eq. (1)、mean utility Eq. (2)、KSS Def. 5；PDF p.4，Alg. 1 Eq. (4)–(7)；PDF p.6，实验配置；PDF p.6–7，任务动态切换/捕获结果。 |
| **Huang et al., RAS** | 只涉及单目标，因而多目标分配不适用。可访问的摘要/问题定义支持分阶段 pursuit 和 PGM 决策；allocator、coalition optimizer、固定角色均不能据摘要判定。 | 单目标任务摘要没有展示探索与围捕的资源竞价；是否显式搜索阶段需正文确认。 | 标题/摘要说 pursuit/capture；具体成功判据、环绕与接近的关系待原文全文确认。 | [ScienceDirect 原文](https://www.sciencedirect.com/science/article/pii/S0921889024002744)，文章号 104890。可访问摘要/§3 摘录没有全文公式分页；该行相关问题均标**需要进一步核查**。 |
| **Huang et al., AIS** | **没有显式任务分配器或联盟 optimizer**；各 UAV 用 PD-PGM 条件概率和 MAP 选择动作，目标级距离由 Eq. (7) 定义。个体被 capture 后会自行转去搜索/捕获剩余目标，但不是全局任务指派求解。 | 搜索、围捕、捕获是每架 UAV 顺序执行的阶段（search→encircle→capture）；有个体模式切换，但没有在同一队内优化探索和捕获资源配额。 | 不止 tracking。成功 encirclement 用相邻 Apollonius circles 相切/相交等几何条件；任务定义再要求 `D_i^T(t)→0` 于有限时间，即目标被捕获。 | [Wiley 原文](https://advanced.onlinelibrary.wiley.com/doi/10.1002/aisy.202401110)：§3.3 Proposition 1；§3.4 Eq. (7)、Definition 1；§4.2 Table 1/Eq. (10)；§4.3–4.5 MAP/Algorithm 1；§5.2 real-world experiment 的检测、encircle、capture 时序。PDF 页码在 HTML 中不可见，待补核。 |
| **Huang et al., RA-L** | 摘要明确 DB-PGM/MAP 与本地密度估计；没有正文证据确认固定角色、目标分配器或联盟优化目标。 | 摘要没说探索任务与围捕任务是否争用同一批 AAV；待全文。 | 摘要级支持“成功 encircle 多个 evaders”；几何判定、捕获后状态及实验成功定义待全文 PDF。 | [IEEE DOI](https://doi.org/10.1109/LRA.2025.3583457)：期刊 pp. 8228–8235。正文无法访问，所有详细判断待核。 |
| **TR-11 / Rao et al.** | **有显式动态 pursuer allocation**；摘要确认根据 A* path length 做分配比较，Fig. 1 对比 Euclidean distance 与 A* path length。**需要进一步核查** auction 的全局目标函数究竟是最小化总路径长、局部出价还是其他效用，且不得仅由 A* 标题/图注补公式。没有固定异质角色证据。 | 目前原文摘要/框图是 evader pursuit + allocation + collision avoidance；没有探索任务，不形成探索-捕获联合分配。 | 摘要与仿真图称 capture；具体捕获距离、target 是否停机/从任务中移除，需正文算法段核对。C3AVC 保证的是 chance-constrained collision avoidance，不等同于目标捕获判据。 | [JAS 原文页](https://www.ieee-jas.net/en/article/doi/10.1109/JAS.2025.125684)：pp. 989–991，Abstract、Fig. 1；[官方补充材料](https://www.ieee-jas.net/fileZDHXBEN/journal/article/file/d5633e16-678c-4d80-8337-3da4303ecd23.pdf)：Fig. S1、§S2。 |

## 本轮可直接引用的纠错结论

1. **“局部感知 = 不传播目标坐标”是错误等式。** Role-based MADDPG 明说邻居间传播 target location；KS-COAL 明说 Scout 将 target position 交给 SWAT，并通过 K-hop neighbor chain 传播 assignment/utility 消息；TERL 则在无 agent-to-agent 通信时让策略直接看到所有非 encircled evader 的状态。
2. **“分布式 = 没有中心信息源／没有坐标输入”也不能成立。** TERL 训练有 global reward 信息，执行没有 agent 间通信，但执行 actor 仍有全体未围捕目标状态。TR-11 的框图把 Positions of Evaders 接到 Local Network For Auction；具体坐标是直接观测还是经估计/邻居输入，还要看正文。
3. **“角色”不自动意味着永久角色，也不自动意味着动态角色。** Role-based MADDPG 的 scout/tracker 是分 reward 配置；文中结果按固定数量实验。KS-COAL 固定机器人能力队伍，但 SWAT 的任务在 capture/defense 间动态变化。AIS PGM 使用 search/encircle/capture 阶段，不是固定异质 agent 编组。
4. **“capture / encirclement / tracking”不能混写。** TERL 是满足几何条件后 immobilize；Role-based MADDPG 的主结果是 tracking，collision 只作为 successful-attack 奖励事件；KS-COAL target 捕获后 immobilize，资源任务才是 formation/encirclement；AIS PGM 将环绕判据与有限时间距离趋零的捕获定义分开；TR-11 和 RAS/RA-L 的最终物理捕获判据需要全文确认。
5. **Huang 三篇不可相互代填信息权限。** RAS 是单目标 2025 文章；AIS 是 communication-denied 多目标 PGM 文章；RA-L 是另一篇 DB-PGM 多目标围捕文章。AIS 明写无通信，不能把该限制自动套到 RAS 或 RA-L。

## 待补的原文证据

- TR-11 正文 pp. 989–991 的完整公式/auction 字段、局部网络连通设定、capture criterion；当前已用官方摘要、Fig. 1 题注和官方补充 Fig. S1，不把缺失细节猜成事实。
- RAS 文章号 104890 和 AIS eLocator 2401110 的可访问网页没有 PDF 页断；可用段落/公式定位，但正式 PDF 页码应补。
- RA-L pp. 8228–8235 的官方全文 PDF 未取得；现有结论只限摘要级方法描述，不作为其坐标传播/任务分配/捕获判据的证据。
- KS-COAL 主文把 SWAT 收到 Scout 目标位置写得明确，但跨队消息路径与 §II-A “不能窃听其他队”之间的接口应查看补充材料或实现；主文已足以确认存在位置交付，不能据此虚构拓扑。
