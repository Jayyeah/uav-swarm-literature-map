# Density Interaction 全文精读包（待 MASTER 审阅）

论文：Zhou / Tao / Lei / Peng，*Self-organized swarm robot for multi-target trapping based on self-regulated density interaction*，Information Sciences 661 (2024), 120119，DOI [10.1016/j.ins.2024.120119](https://doi.org/10.1016/j.ins.2024.120119)。核读日期2026-11-05。

| 文件 | 用途 |
|---|---|
| [SHORT_ZH.md](SHORT_ZH.md) | 10分钟总览 |
| [MEDIUM_ZH.md](MEDIUM_ZH.md) | 30–60分钟技术路线 |
| [LONG_ZH.md](LONG_ZH.md) | Eq.1–19、Fig.1–17、逐节精读与推导边界 |
| [COCAP_RELEVANCE_AND_ADAPTATION_ZH.md](COCAP_RELEVANCE_AND_ADAPTATION_ZH.md) | 13维源码对照、局部支援饱和、A/B/C三版本、4个可证伪方向 |
| [REPRODUCTION_HANDOFF_ZH.md](REPRODUCTION_HANDOFF_ZH.md) | 原文模块、参数与状态化缺项，供独立复现Agent使用 |
| [SOURCE_MANIFEST.md](SOURCE_MANIFEST.md) | 正式身份、PDF路径/SHA256、实际核读范围、CoCap固定commit与源码链接 |

此包完整核读21页正文、声明与参考文献，不包含补充视频、作者数据或源码。仅新增文档，不提交版权PDF，不修改CoCap源码/配置，不启动训练或仿真。

## MASTER handoff（遵循 PROJECT_PROTOCOL §10）

- **NEW PAPERS**：上述DOI对应本篇；截至所审计main未找到该篇独立记录。请MASTER分配永久Pxxxx，不以标题作主键。
- **UPDATED PAPERS**：无；不覆盖已有阅读笔记。
- **MUST READ**：建议归为CoCap近邻的传统多目标分群/几何围困机制节点，本轮用户已指定全文READ；正式索引决定由MASTER执行。
- **MAP**：前驱[39] Lei等密度交互、[40] collective fission、[41–44] SPH/密度控制作为谱系候选，仅核实它们出现在本篇参考文献，未另行全文精读。
- **ARCHIVE**：无新增建议。
- **TAXONOMY CHANGES**：建议明确“局部感知密度分群”节点，并分开记录理想无显式消息、实机动捕广播、未知搜索与生命周期覆盖边界；此包不改canonical taxonomy。
- **SEARCH GAPS**：作者代码/数据/视频；Eq.13/16方向；Eq.9备选样条；积分/限幅/零分母细节；实机ρ0与d0单位；Fig.13的60%档位；目标分群统计实现。
- **CONFLICTS / UNCERTAINTIES**：全文有几何形态指标但非CoCap normal；理想无通信而实机全局广播；初始不全知但未构成完整未知搜索；实机均5/6围住；CoCap研究分支Relative-Z/R未等同main，V2仍保留global-friendly VorAdj。

## 阅读包核验

- 六项指定交付齐全；另加本导航文件，全部位于本目录。
- 三个阅读层级独立可读，公式/图页码统一；长版包含额外推导、逐图解读和数值疑点，不靠复制中版扩充。
- 原文事实、源码事实和适配推断显式区分；关键缺项不补造。
- 只新增7个Markdown文件；四个canonical files、旧笔记与CoCap工作文件均不改动。
- 推送与Draft PR状态以GitHub远端核验及本任务最终交付回执为准；本文不提前声称已经同步。

审阅前不开始代码实现。
