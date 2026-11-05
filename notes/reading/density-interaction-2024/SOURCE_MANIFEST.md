# Density Interaction：来源、版本与审计基准

核读日期：2026-11-05。本文献包供 MASTER 审阅与独立复现 Agent 查证；没有运行算法、训练或仿真。

## 1. 正式出版身份

| 字段 | 核验结果 | 依据 |
|---|---|---|
| 正式题名 | Self-organized swarm robot for multi-target trapping based on self-regulated density interaction | PDF p.1 |
| 作者（原顺序） | Yuchen Zhou; Yuan Tao; Xiaokang Lei; Xingguang Peng | PDF p.1，Peng 为通讯作者 |
| 年份、venue | 2024，Information Sciences | PDF p.1；出版社条目 |
| 卷、期、页码 | Volume 661，March 2024；article 120119；未列 issue。PDF 内页码 1–21，并非期刊连续页 1–21 | PDF 页眉及出版社条目 |
| DOI | [10.1016/j.ins.2024.120119](https://doi.org/10.1016/j.ins.2024.120119) | PDF p.1 |
| PII | S002002552400032X | 出版社条目 URL |
| 日期 | Received 2023-09-03；revised 2023-11-13；accepted 2024-01-06；available online 2024-01-11 | PDF p.1 |
| 正式入口 | [ScienceDirect](https://www.sciencedirect.com/science/article/pii/S002002552400032X) | 2026-11-05 搜索检索可见出版条目；直接打开返回 403 |
| 阅读版本 | 出版社正式排版全文（Version of Record 外观与出版标识）；不是摘要、预印本或作者接受稿 | 首页刊头、DOI、版权、完整公式与页码 |

[Web核验] 出版社检索条目独立支持题名、卷、月份、文章号、DOI。作者完整顺序与正文内容取自用户提供 PDF。没有声称重新从出版社下载了相同字节的 PDF，也没有对出版社文件进行二进制一致性认证。

## 2. 实际 PDF 来源与指纹

- 用户指定来源：`/home/yjq/rl/CoCap1/temp/BBB 2024 密度法自组织 非rl 多目标 Self-regulated Density Interaction.pdf`。
- 同一挂载可见路径：`/data/disk1/home/yjq/rl/CoCap1/temp/BBB 2024 密度法自组织 非rl 多目标 Self-regulated Density Interaction.pdf`。
- SHA256：`0b3e653d8948209957c152ad6f8c21037195a426d2726e20b2cbb5bec0b45fc9`。
- 文件大小：6,245,611 bytes；21 页；PDF 1.7；未加密。
- PDF metadata：Creator Elsevier；Author 字段仅 Yuchen Zhou（不能代替首页全作者名单）；Creation 2024-02-13 20:59:32 +08；Mod 2024-02-13 21:06:57 +08。文件制作日期不替代发表日期。
- 遵守仓库 `PROJECT_PROTOCOL.md` §14：不将版权 PDF 或整篇提取文本提交 GitHub。PDF 留在原位置。

## 3. 实际核读范围

**完整阅读 21/21 页**：p.1–3 引言、贡献、模型；p.3–4 目标动力学与指标；p.4–8 方法；p.8–16 仿真；p.16–19 实机；p.19–20 结论和声明；p.20–21 全部 45 条参考文献。逐项核对 Eq.(1)–(19)、Fig.1–17。论文没有编号表格、没有编号 Algorithm，也没有定理/证明章节。

文字采用 Poppler `pdftotext -layout` 提取；方法与实验页 p.3–19 渲染后直接目视核对，特别核对 Eq.(9)、(12)–(17)、Fig.1、4–13、15–17。笔记页码均为 PDF 页底页码，与 PDF 1-based 页序一致。

缺失范围：补充实验视频没有取得/观看；无作者源码、原始轨迹和数据文件；p.20 仅说明数据可按请求提供。未联系作者。正文已完整取得，**缺的不是正文页**。

## 4. 证据标签与置信边界

- `[原文]`：PDF 直接支持，标页码及式/图。
- `[Web核验]`：正式出版身份核验，保留外链。
- `[源码]`：固定 CoCap commit 的实际实现；不能视为论文事实。
- `[AI判断]`：本次推导、适配建议、反例或局限分析。
- `VERIFIED`、`PARTIALLY_VERIFIED`、`NOT_SPECIFIED`、`ADAPTATION_REQUIRED` 的用法见交接文档。

全文可读不代表所有实现细节都已规定。积分步长、积分器、饱和顺序、目标评分同值规则、零分母保护、精确初态/随机种子、统计分组识别规则等正文未充分规定。

## 5. 仓库恢复与隔离

两个本地仓库均执行 `git fetch origin`，不切换或修改现有 CoCap 工作树。GitHub 连接器独立查询远端仓库与分支。Literature Map 基准：

- `Jayyeah/uav-swarm-literature-map`，`origin/main = 0993bce0fca54b276e8c0224da799c44ab8fec10`。
- 阅读分支：`read/density-interaction-deep-read-20261105`。
- 独立 worktree：`/data/disk1/home/yjq/research/density-interaction-deep-read-20261105`。
- 新文件目录：`notes/reading/density-interaction-2024/`。
- 已检查 README、PROJECT_PROTOCOL、LITERATURE_MAP、PAPER_INDEX、SEARCH_LOG、READING_LEDGER、阅读模板与既有笔记目录。按 DOI、题名与 density 等检索，没有发现该篇既有独立记录；发现后续密度方法的信息条件审计，不视为本篇全文记录。
- 不抢占永久 `Pxxxx` 编号；不修改四个 canonical files 或旧笔记。由 MASTER 决定归档编号和索引更新。

## 6. CoCap 当前代码的版本分层

| 层级 | 远端 ref / commit | 本次用途 |
|---|---|---|
| main | `main` / `3a20b5adead4186aff728b7ef809eb661866d894` | 仓库默认线；不能当作最新 Relative-Z/R 实验实现 |
| Relative-Z/VXY9 科学实验起点 | `experiment/relative-z-vxy9-wr-20261026` / `0ba1e15d9617dc88303e5dca8b904f46bc1eb77e` | 追溯 W/R 动作和信息合同 |
| 本次主要源码基准 | `engineering/vxy9-integrated-training-20261104` / `5658b9fa75bc20e9f613c169471bc7a599fdfe80` | 逐行核查实际环境、token、Z、支援、捕获；已有本地 clean checkout |
| 更新中的运行报告 | `reports/relative-z-vxy9-wr-status-20261027` / `29de92619acfa2dfd5de8bfbc44f29fd419feac5` | 识别报告线；不把运行状态或旧性能文字当算法定义 |

基准本地目录：`/data/disk1/home/yjq/research/cocap-vxy9-integrated-20261104`。核查文件对 HEAD 无未提交差异。main 中未出现当前 `z_state` / `relative_z` 实现，且没有 `z_guided_support.py`；不是把研究分支声称为已合并 main。AW9、VXY9-W、VXY9-R 是不同动作合同；比较时分别披露。

### 可点击、固定 commit 的源码证据索引

以下链接均指主要源码基准；行号来自该 commit。

| 编号 | 来源 | 审计内容 |
|---|---|---|
| C1 | [voronoi_adjacency.py L217](https://github.com/Jayyeah/cocap-voradj/blob/5658b9fa75bc20e9f613c169471bc7a599fdfe80/src/cocap_voradj/envs/voronoi_adjacency.py#L217) | previous-state 同步 Z，direct=1，自衰减与邻居最大值竞争，hard zero |
| C2 | [同文件 L654](https://github.com/Jayyeah/cocap-voradj/blob/5658b9fa75bc20e9f613c169471bc7a599fdfe80/src/cocap_voradj/envs/voronoi_adjacency.py#L654) | 密度归一感知半径、surface clearance、直接目标列表 |
| C3 | [同文件 L1025](https://github.com/Jayyeah/cocap-voradj/blob/5658b9fa75bc20e9f613c169471bc7a599fdfe80/src/cocap_voradj/envs/voronoi_adjacency.py#L1025) | 全体 active sites，友机 VorAdj 图；VCT-LS 图排除敌人 sites |
| C4 | [同文件 L1339](https://github.com/Jayyeah/cocap-voradj/blob/5658b9fa75bc20e9f613c169471bc7a599fdfe80/src/cocap_voradj/envs/voronoi_adjacency.py#L1339) | policy token：self9、friend7、enemy7；物理排序、8-token 截断，无目标 ID 字段 |
| C5 | [z_guided_support.py](https://github.com/Jayyeah/cocap-voradj/blob/5658b9fa75bc20e9f613c169471bc7a599fdfe80/src/cocap_voradj/envs/z_guided_support.py#L10) | 相对 Z 选最高、近友机；`target_id` 指友机索引，非敌人 ID；ally progress |
| C6 | [voronoi_adjacency.py L594](https://github.com/Jayyeah/cocap-voradj/blob/5658b9fa75bc20e9f613c169471bc7a599fdfe80/src/cocap_voradj/envs/voronoi_adjacency.py#L594)；[L2681](https://github.com/Jayyeah/cocap-voradj/blob/5658b9fa75bc20e9f613c169471bc7a599fdfe80/src/cocap_voradj/envs/voronoi_adjacency.py#L2681) | 当前 Relative-Z role 优先级及支援奖励实际分支；旧 neighbor_visible 配置字段不是当前输入语义 |
| C7 | [base.py L1310](https://github.com/Jayyeah/cocap-voradj/blob/5658b9fa75bc20e9f613c169471bc7a599fdfe80/src/cocap_voradj/envs/base.py#L1310)；[调用 L2827](https://github.com/Jayyeah/cocap-voradj/blob/5658b9fa75bc20e9f613c169471bc7a599fdfe80/src/cocap_voradj/envs/voronoi_adjacency.py#L2827) | normal 对应原始 `loose` 角度/距离事件；stationary；目标失活与释放 |
| C8 | [density_sensing.py](https://github.com/Jayyeah/cocap-voradj/blob/5658b9fa75bc20e9f613c169471bc7a599fdfe80/src/cocap_voradj/envs/density_sensing.py) | `0.8715 sqrt(A_free/N)`，20m floor 触发尺度要求；保留 historical global-friendly |
| C9 | [W Stage1 resolved](https://github.com/Jayyeah/cocap-voradj/blob/5658b9fa75bc20e9f613c169471bc7a599fdfe80/configs/experiments/relative_z_vxy9_wr_20261026/W/stage1.resolved.yaml) | 120m 地图、速度、normal/stationary 阈值、token cap、信息开关、地图归一化合同 |
| C10 | [Relative-Z 科学合同](https://github.com/Jayyeah/cocap-voradj/blob/5658b9fa75bc20e9f613c169471bc7a599fdfe80/docs/experiments/relative_z_rnorm_20261017/RELATIVE_Z_SUPPORT_DESIGN_CONTRACT_ZH.md) | 无隐藏敌人/目标 ID；支援使用实际 policy token；Z 残留与释放 |
| C11 | [VXY9 W/R 合同](https://github.com/Jayyeah/cocap-voradj/blob/5658b9fa75bc20e9f613c169471bc7a599fdfe80/docs/experiments/relative_z_vxy9_wr_20261026/FINAL_TRAINING_CONTRACT_ZH.md)；[集成等价性报告](https://github.com/Jayyeah/cocap-voradj/blob/5658b9fa75bc20e9f613c169471bc7a599fdfe80/docs/engineering/vxy9_integrated_20261104/CONTRACT_EQUIVALENCE_ZH.md) | W/R 动作与伺服、工程集成保持科学合同；合同旧时态不代替最新运行报告 |

核心文件 Git blob：

```
voronoi_adjacency.py 6202225de5ce9d1a6e457f7cf02deee4a9e32ca4
base.py             2742f098ef71f807f18606c13bbbc812df353a9c
z_guided_support.py 0395f07ae2fcc9f2c09a2db2fc33366db0ea514a
density_sensing.py  5d5e913feaad3ce87b7b0a085e6d509ce6c645bc
W/stage1.resolved.yaml c82c4ab21ec02757fd50c7f38f0ff4f422f318db
```

## 7. 本次发现的不可静默消解事项

1. p.3 Eq.(5) 后写 `d0<0`，与先定义 `d0>0` 冲突；函数导数显示应讨论距离是否小于 d0。这是读者数学判断，不篡改原文。
2. p.7 Eq.(16) 同时给出 `r_ij=r_i-r_j` 与“unit vector from i to j”，方向相反；Eq.(13) 后梯度方向文字也有歧义。必须固定一种向量合同并披露。
3. p.5 Eq.(9) 的 “Cobie spline” 第二段原印 `(1-λ)^3/6`，在 1<λ≤2 为负，与核正值性质矛盾。实际采用 bell-shaped，不自行用常见样条公式替换后称原式。
4. p.16 默认实机参数印 `d0=150m`，p.18 Fig.16 说明明确 `150mm`；报告该冲突并优先将 150mm 作为有交叉证据的候选，不声称已获作者勘误。
5. p.15 Eq.(19) 正文列噪声到 50%；p.16 Fig.13 横轴另有 60%。不补造 60% 的实验说明。
6. p.4 成功标准为形态+距离趋稳；p.15 Fig.11 用追捕人数≤2作失败代理；Fig.13 改用角度判据。三套统计不能直接互换。
7. p.18–19 明确实机发生碰撞、翻转，实机两组均仅 5/6 目标围住，另一个仍被两机追逐；不能报告“所有目标成功”或“严格无碰撞”。
8. CoCap 旧配置仍有 `neighbor_visible`、`distance_normalization: map_diagonal` 等文字；当前 Relative-Z 支援实际走友机锚点，地图尺度由有效 `side_length_r` 消费路径决定。只记录差异，不改合同。
