# 给复现 Agent：Density Interaction 原文交接

对象：*Self-organized swarm robot for multi-target trapping based on self-regulated density interaction*，Zhou / Tao / Lei / Peng，Information Sciences 661 (2024), 120119，DOI [10.1016/j.ins.2024.120119](https://doi.org/10.1016/j.ins.2024.120119)。依据为完整21页正式排版PDF。文件位置、SHA256见 [SOURCE_MANIFEST](SOURCE_MANIFEST.md)。本文件**只列原文事实和缺项，不替复现 Agent 选择工程补丁或 CoCap 适配方案**。

## 状态定义

- `VERIFIED`：正文/公式/图能直接确认该项，不表示已经执行代码验证。
- `PARTIALLY_VERIFIED`：主要机制有证据，但方向、单位或实现细节有冲突/缺口。
- `NOT_SPECIFIED`：全文没有给出足以直接复现的定义；不可当作数值0或默认支持。
- `ADAPTATION_REQUIRED`：请求的CoCap能力或环境不属于原文原生，需要另立适配；不是已存在的原文模块。

## 1. 模块与关键公式（保留原编号）

| 状态 | 原文模块 | 原始依据与可确认计算 | 限制 |
|---|---|---|---|
| VERIFIED | 二阶运动模型 | p.3 Eq.(1) `m_i vdot_i=F_i`；Eq.(2) `rdot_i=v_i, vdot_i=F_i/m_i`；m_i默认1 | 有速度/加速度限制，积分方法未给 |
| VERIFIED | prey合力 | p.3 Eq.(3) `F_k=F_self+F_esp+F_rep` | 原生逃逸者不是CoCap APF |
| VERIFIED | prey自推进 | p.3 Eq.(4) `(α_k-ζ||v_k||²)v_k` | 零速时此项为0；不要仅凭文字承诺能自行启动 |
| PARTIALLY_VERIFIED | prey逃逸项 | p.3 Eq.(5) `-k_esp Σ_{i∈N_k} [d_ik/(d_ik+d0)²] hat r_ik`；r_ik=r_i-r_k，为prey指向hunter | 正文先定d0>0，后印d0<0，与距离段落矛盾 |
| VERIFIED | prey间排斥 | p.3 Eq.(6) `-k_rep Σ_{i∈P_k} hat r_ik/d_ik³` | N_k为可见hunters，P_k为可见其他prey |
| VERIFIED | 形态指标 | p.4 Eq.(7) `θ_rest=max θ_e`；Fig.1的防御半圆直径=5×自身体长 | 不是相邻中心角gap；完整几何计算代码未给 |
| VERIFIED | 最近距离 | p.4 Eq.(8) `d_kt=min_{i∈N_k}||r_ik||` | 无邻居时如何编码未给 |
| PARTIALLY_VERIFIED | 候选SPH核 | p.5 Eq.(9)列bell、quadratic、“Cobie spline” | 样条第二段原印负值问题；实际不使用该候选 |
| VERIFIED | 实际使用的核 | p.5 Eq.(10) `W(λ)=(R_i/R_sen)(1+3λ)(1-λ)³`，0≤λ≤1；λ>1为0；λ=d/R_sen | 后续W(d)记法省略了归一输入，不要把米直接当λ |
| VERIFIED | 本体密度 | p.5 Eq.(11) `ρ_i=W(0)+Σ_{j∈N_i}W(r_ij)` | 密度源只有hunters含自身，非prey |
| PARTIALLY_VERIFIED | 本机密度场 | p.6 Eq.(12) `Q_i(x_i)=W(||x_i||)+Σ_{j∈N_i(x_i)}W(||x_i-r_j||)` | 文字为本机可见hunters；N_i(x_i)无进一步形式定义，本机为原点 |
| PARTIALLY_VERIFIED | 密度负反馈 | p.6 Eq.(13) `F_col=k_col[1-(ρ_i/ρ0)³]Σ∇W(r_ij)`；p.7：低密度吸引、高密度排斥 | 梯度求导变量/方向与文字需统一披露，不能默改 |
| VERIFIED | 目标评分 | p.7 Eq.(14) `press_i(k)=β1 Q_i(r_k)+β2 r_ik, k∈P_i`；选当前最低press的p_choose | 同值、切换频率、滞回未给 |
| PARTIALLY_VERIFIED | 目标吸引 | p.7 Eq.(15) `F_tar=k_tar ρ_i/Q_i(r_pchoose) * hat r_i,pchoose`；单位向量指向目标 | Q=0/极小时如何处理未给 |
| PARTIALLY_VERIFIED | hunter对实体排斥 | p.7 Eq.(16) `F_rep=-k_rep Σ_{j∈(N_i,P_i)} hat r_ij/||r_ij||³`；对hunters/prey均排斥 | 原写r_i-r_j又称单位方向from i to j，二者冲突 |
| VERIFIED | hunter自推进 | p.7 Eq.(17) `(α_i-ζ||v_i||²)v_i` | 只用本体速度；没有随机搜索策略 |
| VERIFIED | hunter总力 | p.8 Eq.(18) `F_i=F_col+F_tar+F_rep+F_self` | 无可见目标F_tar=0由p.10 Fig.7(a1)说明 |
| VERIFIED | 距离噪声 | p.15 Eq.(19) `r_ij^noise=(1+ξδ)r_ij, δ~U(-1,1)` | 不含方向噪声；噪声时序相关性/每项独立采样细节未给 |

完整公式转写、变量解释与读者推导在 [LONG_ZH §2–3](LONG_ZH.md)。其中核导数、评分差、密度比偏导是阅读者推导，不新增“论文公式(20)”或作者稳定性证明。

## 2. 原始参数

### 2.1 仿真默认参数：VERIFIED（p.8）

| 参数 | hunters | prey |
|---|---:|---:|
| R | 0.2m | 0.2m |
| R_sen / R_ksen | 7m | 7m |
| k_rep | 5 | 5 |
| k_col | 20 | 不适用 |
| k_tar | 7 | 不适用 |
| k_esp | 不适用 | 0.5 |
| α | 0.1 | 0.1 |
| ζ | 2 | 2 |
| β1 | 20 | 不适用 |
| β2 | 0.2 | 不适用 |
| ρ0 | 0.2 | 不适用 |
| d0 | 不适用 | 1m |
| vmax | 5m/s | 3m/s |
| Fmax | 5N | 5N |

`m=1`来自p.3。仿真ρ0控制实验会覆盖默认值，见下；不能让所有图都沿用0.2。

### 2.2 实机默认参数：VERIFIED / PARTIALLY_VERIFIED（p.16、18）

| 参数 | hunters | prey | 状态 |
|---|---:|---:|---|
| R | 30mm | 30mm | VERIFIED |
| 感知半径 | 1000mm | 1000mm | VERIFIED |
| k_rep | 1.3 | 1.5 | VERIFIED |
| k_col | 10 | — | VERIFIED |
| k_tar | 80 | — | VERIFIED |
| k_esp | — | 1.5 | VERIFIED |
| α,ζ | 0.6,0.1 | 0.6,0.1 | VERIFIED |
| β1,β2 | 35,2 | — | VERIFIED |
| vmax | 20mm/s | 10mm/s | VERIFIED |
| amax | 50mm/s² | 50mm/s² | VERIFIED |
| d0 | — | p.16原印150m，p.18明确150mm | PARTIALLY_VERIFIED：后者有量纲交叉证据，非作者正式勘误 |
| 多目标ρ0 | 未明确重列 | — | NOT_SPECIFIED：不要自动套用仿真默认 |

`VERIFIED`（p.16）：差速控制Δt=0.2s、ω=Δθ/Δt、角速度上限47.75deg/s；线速度按v_d区间映射为20、10、5、0mm/s（区间详见LONG §5.0）。这不是仿真的时间步长。

## 3. 原生感知、通信输入与身份

| 状态 | 项目 | 原文依据 |
|---|---|---|
| VERIFIED | 理想算法每机使用自身圆盘范围内实体位置分布，能区分hunter/prey | p.3；p.8；Eq.(11)–(16) |
| VERIFIED | 需要目标相对位置、距离和方向；友机相对位置；本体速度 | Eq.(4)、(10)–(17) |
| VERIFIED | 理想算法不额外交换机器人消息；没有坐标/ID或标量传播模块 | p.3、8 |
| NOT_SPECIFIED | 传感器硬件如何本地完成识别、遮挡、漏检、速度估计 | 实机用动捕替代 |
| NOT_SPECIFIED | 全局一致target ID、跨机器人同目标判定与永久track ID | k仅为公式中的实体索引 |
| VERIFIED | 无需预先全目标可见；Fig.9初始仅一个目标入视野 | p.11–12 |
| VERIFIED | 实机NOKOV获取全体位置与朝向，2.4G RF向所有机器人广播全局信息，各机截取局部信息 | p.16 Fig.14及文字 |
| NOT_SPECIFIED | RF消息字段格式、通信半径、精确局部过滤审计、时延数值 | p.16仅描述架构；p.18列时延噪声来源 |

[原文＋必要解释] Q_i(r_k)取决于目标相对坐标，但不要求跨机共享目标身份。用当前本机目标与友机相对坐标之差求它们距离，是局部坐标实现的数学展开；不是额外全局坐标输入。

## 4. 发现、选择与执行顺序

| 状态 | 环节 | 原文依据与缺项 |
|---|---|---|
| VERIFIED | 初始布置 | 默认原点5m圆盘随机分布（p.8）；实机hunters在中心、prey外部（p.17） |
| NOT_SPECIFIED | 精确初始速度/朝向、随机分布采样律/seed、最小间距 | 图有初态但没有全量数值 |
| VERIFIED | 目标进入感知范围成为P_i当前候选 | p.3；Eq.14；Fig.9 |
| VERIFIED | 本地构建ρ_i、Q_i，按press最小选一个可见目标 | Eq.11–15 |
| VERIFIED | 无目标时F_tar=0，其他力仍存在 | p.10 Fig.7(a1) |
| VERIFIED | 无预分组、固定角色、统一人数配额或任务协商 | p.7、15 |
| NOT_SPECIFIED | 目标评分同值、目标切换滞回、重计算频率 | 未提供Algorithm或源码 |
| PARTIALLY_VERIFIED | 合力受限后运动更新 | Eq.1–2、18与p.3/8约束；顺序、Δt、积分器未给 |
| NOT_SPECIFIED | 全部目标不可见时的系统搜索覆盖、搜索终止/完备性 | Eq.17自推进不是完整搜索模块 |
| NOT_SPECIFIED | 捕获后移除目标、释放机器人、回覆盖、重复到达 | 正文展示持续围困，没有生命周期协议 |
| ADAPTATION_REQUIRED | CoCap Z支援、AW9/VXY9动作、APF对手、normal、post-capture recovery | 都属于原文以外环境/机制；本文件不替Agent设计 |

## 5. 捕获与评价口径

| 状态 | 口径 | 证据及注意事项 |
|---|---|---|
| VERIFIED | 通常成功形态 | p.4 Eq.7–8、Fig.1：θ_rest<30°且最近距离趋稳到d0以内 |
| NOT_SPECIFIED | 统一可执行成功判定 | 无趋稳容差、hold步数、首次完成时刻或终止移除定义；半圆并集算法未给 |
| VERIFIED | Fig.11失败比例 | p.15：0/1/2追捕者算失败目标，P_fail=失败目标/总目标；每条件50次 |
| PARTIALLY_VERIFIED | n_trap | p.15为每目标最终群规模；识别成员/距离阈值未给 |
| VERIFIED | Fig.13噪声成功 | p.15改为θ_rest<30°形态判据；每噪声条件100次 |
| NOT_SPECIFIED | 平均完成时间、碰撞率和同行baseline对比 | 没有相应定量表；实机明确有碰撞 |
| ADAPTATION_REQUIRED | CoCap normal/stationary | 原文30°是防御区遮挡后的剩余角，不能替换成中心角gap或CoCap阈值 |

## 6. 原生场景与可查图

| 状态 | 场景 | 复现应核对的原生现象 |
|---|---|---|
| VERIFIED | Fig.3 p.6：focal+19邻居，R=0.2、R_sen=7；负反馈场示例ρ0=0.1 | 局部密度场与反馈示意 |
| VERIFIED | Fig.4 p.8–9：50机无目标；ρ0=1,.8,.6,.5,.4,.3,.2,.1,.05 | 降低ρ0，群体尺度增大 |
| VERIFIED | Fig.5 p.9–10：50机，每300 iterations改ρ0 | .5→.3→.2→.1→.2→.3→.5的响应与超调 |
| VERIFIED | Fig.6 p.10：N=5,10,20,30,40,50对单目标 | 多机时近目标饱和与冗余外围个体 |
| VERIFIED | Fig.7 p.11：20机单目标 | 三个不同局部视角的目标可见性/密度比 |
| VERIFIED | Fig.8 p.11–12：3机1目标 | θ_rest降至阈值内，d_kt约0.85m |
| VERIFIED | Fig.9 p.11–13：10机3静止目标，初始仅见1个 | 新目标入视野、改选、分3群 |
| PARTIALLY_VERIFIED | Fig.10 p.13：5运动目标典型轨迹 | 5目标围困、d_kt约0.9m；正文图注未直接标hunter总数 |
| VERIFIED | Fig.11 p.14–15：N=30/50、M=2…10，各50次 | N=30且M>6出现失败，50改善；N/M为参考而非输入配额 |
| VERIFIED | Fig.12 p.14–15 | 中间目标因局部高密度被忽略的失败案例 |
| PARTIALLY_VERIFIED | Fig.13 p.15–16：20机4目标，各100次 | 文本ξ=5,10,20,30,35,40,50%；图另有60%；35%以内失败低于12%为正文描述 |
| VERIFIED | Fig.15 p.17：30实机无目标 | 80秒前ρ0=.1，之后.5 |
| VERIFIED | Fig.16 p.17–18：24猎手6目标 | 围住5个，另1个两机追逐；实机碰撞存在 |
| VERIFIED | Fig.17 p.18–19：24猎手6目标，5车停机 | 剩19围5、追1，不是全目标成功 |

## 7. 尚无法核实与禁止默补

- `NOT_SPECIFIED`：仿真积分器、仿真Δt、总时长、力/加速度/速度饱和次序、浮点精度；不能拿实机0.2s填入仿真。
- `PARTIALLY_VERIFIED`：Eq.13/16方向文字；必须写清选定的方向解释，不能悄悄修正文后称唯一原生实现。
- `NOT_SPECIFIED`：目标在感知边界导致Q=0时的分母保护、d=0时方向与斥力、空集合评价值。
- `NOT_SPECIFIED`：物理实体碰撞响应、仿真重叠处理、严格安全距离；奇异力不是输入受限系统的安全证明。
- `NOT_SPECIFIED`：局部遮挡、消息丢失、方向噪声、跨时目标关联；Eq.19只有距离扰动。
- `PARTIALLY_VERIFIED`：实机d0单位150m/150mm，噪声正文与60%图轴不一致。
- `NOT_SPECIFIED`：实机多目标实验ρ0、baseline公平比较、平均完成时间和完整参数敏感性。
- `NOT_SPECIFIED`：数据/作者代码和补充视频内容；本轮未取得。p.20只说数据可请求。
- `ADAPTATION_REQUIRED`：在CoCap信息合同、动作、对手和捕获/恢复任务中使用本方法；须与A原生复现分开命名，适配设计由复现Agent/主Agent另行审定。

全文未给收敛、严格避碰或无逃逸定理。本交接的VERIFIED指“原文有依据”，不是数学保证或代码已经通过测试。
