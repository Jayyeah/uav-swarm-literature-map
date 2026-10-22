# CoCap 定向文献补漏审计 — 2026-10-22

从 [REVIEW_ZH.md](REVIEW_ZH.md) 阅读。它更新此前八篇选型建议，重点纠正局部密度方法、FSC2 和覆盖/捕获生命周期的遗漏；不宣称全领域检索完备。

- [COLLECTION.csv](COLLECTION.csv)：29 篇精选，含新收集及旧库仍有用的条目；稳定 ID 对应根目录 PAPER_INDEX.csv。
- [SOURCE_MANIFEST.csv](SOURCE_MANIFEST.csv)：实际取得的 25 篇原文及 JAS 补充材料（26 条来源记录）、版本、来源、字节数、SHA-256、主审范围。23 篇 PDF + 2 篇正文网页，另 1 份补充 PDF；3 篇仅子 agent 全文筛查。
- [逐篇阅读卡](../../notes/reading)：22 张 `*-GAP20261022.md`；MASTER 已核查原文，没有运行作者代码。
- [SEARCH_PROVENANCE.md](SEARCH_PROVENANCE.md)：检索与筛查过程、精确检索式和停止边界。
- [UNRESOLVED.md](UNRESOLVED.md)：全文未取得、待澄清实现及不能承载的结论。
- [NEXT_STEPS_ZH.md](NEXT_STEPS_ZH.md)：论文推进与后续 agent 工作流程。

旧 51 个 ID 保留。新增 P0052–P0075，其中此前八篇的 KS-COAL 复用 P0044，不重复入库。修复旧 CSV 七行多余空字段造成的状态列错位，修正 P0033 第一作者拼写；不刷新旧引文统计，不伪造新文献引用量。

仓库只提交元数据、阅读笔记和综述，不批量提交受版权保护 PDF、完整网页正文或私有项目代码。主审来源可根据清单定位，PDF 的本地取得与公开可再分发是不同事项。
