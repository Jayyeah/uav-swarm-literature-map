# PROJECT PROTOCOL v0.1

## 1. Project mission

Build a high-recall, evidence-grounded literature map from broad foundations to CoCap-near work:

1. Multi-agent / UAV swarm fundamentals
2. Classical encirclement / enclosing / circumnavigation
3. Pursuit–Evasion (PE) / differential games / reach-avoid
4. Learning-based pursuit / encirclement / MARL
5. CoCap-near problems: multi-UAV, multi-target, local sensing, decentralized execution, support/allocation, capture+coverage, recovery, obstacles, continuous control

The final outputs are:

- method genealogy;
- assumption genealogy;
- problem genealogy;
- frontier bottlenecks;
- CoCap's real novelty boundary and strongest alternatives.

## 2. Fixed workflow

Always separate three stages:

> **SEARCH → SCREEN → READ**

- **SEARCH**: maximize recall; collect candidates, surveys, seminal seeds, recent frontier work, backward/forward citations, author/lab chains.
- **SCREEN**: use metadata + abstract/full-text spot checks to decide map role and reading value.
- **READ**: deeply read only selected `MUST READ` papers.

Do not collapse the three stages into one.

## 3. Canonical source of truth (SSOT)

Canonical project state lives in this repository:

- `LITERATURE_MAP.md`
- `SEARCH_LOG.md`
- `PAPER_INDEX.csv`
- `READING_LEDGER.md`

Chat memory, Project files, and agent summaries are working context only. If they conflict with the latest repository state, the repository wins.

## 4. Single-writer rule

Only **MASTER** merges/edits the four canonical files.

Search, screening, and reading agents may write handoff notes under:

- `searches/`
- `notes/screening/`
- `notes/reading/`
- `notes/synthesis/`

Child agents must not independently rewrite the global index/map.

## 5. Paper identity and deduplication

Every paper admitted to the canonical index receives a permanent ID:

`P0001`, `P0002`, ...

Rules:

- Prefer the formally published version as canonical metadata when available.
- arXiv/preprint and later formal publication normally share one `paper_id` if they are substantively the same work.
- Record DOI/arXiv identifiers so duplicates can be detected.
- Never use title alone as a database primary key.

## 6. Evidence labels

All substantial notes should distinguish:

- `[原文]` — directly supported by the paper/PDF;
- `[Web核验]` — publication/citation/code/venue facts independently verified on the web;
- `[AI判断]` — interpretation, critique, novelty comparison, or inference.

Do not silently turn inference into paper fact.

## 7. Screening classes

Every indexed paper has one of three decisions:

### MUST READ
A paper is structurally important to the map because it is, for example:

- seminal / field-defining;
- a strong survey;
- a major method/theory turning point;
- a strong recent frontier work;
- a closest CoCap competitor / novelty threat.

### MAP
Must be known and positioned in the map, but not necessarily read deeply.

### ARCHIVE
Peripheral, redundant, weak, or currently low-value; retain metadata but do not spend reading time.

**No silent promotion:** `highly relevant` alone is not enough for `MUST READ`. State which historical/theoretical/method/frontier node the paper represents.

## 8. Classic vs recent screening policy

### Classics
Judge by:

- venue recognition;
- historical citation impact;
- repeated use by later surveys/papers;
- first/early introduction of an important idea;
- descendants / lasting lineage.

Older years are allowed when historically important.

### Recent/frontier papers
Default recent window: roughly 2023–present, adjusted by subfield.

Judge by:

- venue and formal publication status;
- citation velocity rather than only total citations;
- author/lab credibility as supporting evidence, never a substitute for technical merit;
- code/data/real experiments;
- whether the work addresses a recognized bottleneck;
- whether later papers already build on it.

Never reject a new paper solely because total citations are low.

## 9. Search provenance and saturation

Every search round must record:

- date;
- topic/taxonomy node;
- databases/search engines;
- exact queries;
- filters/date range;
- seed papers;
- backward citation chaining status;
- forward citation chaining status;
- author/lab/venue follow-up status;
- number of candidates reviewed;
- number of genuinely new high-value papers;
- saturation judgment.

Stop a branch only when repeated keyword, citation, author/lab, and survey expansion yields few new high-value nodes. Do not stop at an arbitrary paper count.

## 10. Required child-agent handoff

Every Search/Screen/Read child session ends with:

```text
NEW PAPERS
UPDATED PAPERS
MUST READ
MAP
ARCHIVE
TAXONOMY CHANGES
SEARCH GAPS
CONFLICTS / UNCERTAINTIES
```

Include enough bibliographic identity for MASTER to deduplicate candidates.

## 11. Assumption-first analysis

For technical comparison, prioritize assumptions before algorithms:

- pursuer/evader counts;
- single/multi-target;
- dynamics / action space;
- sensing range and observability;
- communication content/range;
- centralized/decentralized execution;
- map/obstacle knowledge;
- target/evader dynamics and strategic behavior;
- speed ratio;
- task termination/capture definition;
- theoretical guarantees;
- simulation vs real deployment.

## 12. Encirclement vs PE policy

Do not collapse the two literatures.

Track separately:

- geometric surrounding / formation / circumnavigation;
- capture reachability / winning regions / adversarial PE;
- multi-target task allocation;
- learning-based behavior.

A major synthesis goal is to identify when and how these branches connect.

## 13. CoCap comparison policy

For important papers explicitly answer:

1. What does this paper actually solve?
2. What assumptions make it easier/harder than CoCap?
3. What is directly reusable?
4. What is only conceptually relevant?
5. Does it threaten a claimed CoCap novelty?
6. What stronger baseline does it imply?

Do not treat network choice alone as a research contribution.

## 14. Repository hygiene

- Do not bulk-commit copyrighted PDFs.
- Store PDFs in Zotero / active ChatGPT Project unless redistribution is clearly permitted.
- Store metadata, notes, search logs, citations, and synthesis here.
- Keep canonical files concise; long per-paper notes belong under `notes/`.
- Prefer one logical commit per search/screen/read merge.

## 15. MASTER review cadence

After roughly 2–3 search themes or a substantial batch merge, run a **Map Review** answering:

- Which branches are mature/saturated?
- Which remain undercovered?
- Which papers form clear genealogies?
- Which initially promising directions are low-value?
- Which new keywords/terms emerged?
- What changed in the CoCap novelty boundary?

## 16. Project completion criterion

Success is not `N PDFs collected`.

Success means the project can explain, with evidence:

> what classical methods solved; what RL genuinely adds; how PE and encirclement connect; what the current bottlenecks are; and where CoCap sits relative to the strongest alternatives.
