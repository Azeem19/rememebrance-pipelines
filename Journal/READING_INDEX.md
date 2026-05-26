# Reading Index — Theoretical Foundations for Cypher Build

This index logs Tuesday Journal Club reflections with tags that map research
methodologies onto active artifacts. Claude Code should consult this file
before architecting new pipelines or proposing methodology changes.

When a tag matches the task at hand, apply the methodology — don't reinvent.

**Update protocol:** New entries appended weekly after Tuesday reading session.
Entries follow the schema documented at the bottom of this file.

---

## Wk4 | 5.24.26

### Evaluating and Addressing Demographic Disparities in Medical Large Language Models: A Systematic Review
- **Theme:** Explainable AI & Fairness
- **Tags:** demographic-bias, prisma, jbi-critical-appraisal, debiasing-algorithm, prompt-engineering, gender-bias, racial-bias, socioeconomic-bias, healthcare-llm, systematic-review
- **Source:** Omar, Sorin, Agbareia, Apakama, Soroush, Sakhuja, Freeman, Horowitz, Richardson, Nadkarni, Klang. *Evaluating and addressing demographic disparities in medical large language models: a systematic review.* [NEEDS DOI CONFIRMATION]
- **Applies to artifacts:**
  - Artifact #5 — Grant-Fit Scoring Agent (bias audit layer)
  - Artifact #4 — Ancestor Search RAG (demographic refusal logic)
  - Strategic — Community Data Council Agreement (bias-audit appendix)
- **Key methodology to adopt:**
  - PRISMA reporting checklist + JBI Critical Appraisal Tools for every Cypher LLM artifact audit
  - Three-track mitigation stack: (1) Prompt Engineering — iterative, segmented, contextualized, thematic, demographic-tailored; (2) Debiasing Algorithms — PCA gender debias, Legal-Context-Debias, Context-Debias; (3) Demographic stress-testing grid across gender × race × age × socioeconomic status × language
  - Numbers as reference points: 94% of studies found gender disparities, 91% racial/ethnic bias, 100% bias across cultural and combined demographic dimensions
- **Cypher principle reinforced:** Du Boisian rigor — bias is invisible until math makes it legible; we ship audits, not assurances.
- **Action for Claude Code:** Before any Cypher LLM artifact reaches a partner, run a demographic stress-test grid and write results to a PRISMA-style audit table; surface bias deltas as a first-class output line, not a footnote in the deck.

---

### Evaluation of Prompt Engineering on the Performance of a Large Language Model in Document Information Extraction
- **Theme:** LLM Evaluation, RAG, and Retrieval-Augmented Systems
- **Tags:** ape, automatic-prompt-engineering, ipc, instruction-prompt-calibration, ocr, textract, configuration-table, schema-drift, document-extraction, human-in-the-loop, rag
- **Source:** Chen, Weng, Pardeshi, Chen, Sheu, Pai. *Electronics* 2025, 14(11), 2145. https://doi.org/10.3390/electronics14112145
- **Applies to artifacts:**
  - Artifact #1 — Oral History Intake Form (schema handling)
  - Artifact #2 — Oral History Transcription Pipeline (extraction layer)
  - Artifact #5 — Grant-Fit Scoring Agent (prompt optimization core)
- **Key methodology to adopt:**
  - APE (Automatic Prompt Engineering) — treat prompt optimization as an ML problem: seed with task description + examples → generate candidates → evaluate on training subset → iterate
  - IPC (Instruction Prompt Calibration) — combine human + model evaluation so judgment stays in the loop
  - Configuration tables to absorb schema drift across partners and document types (KIPP cohort fields vs. Moorestown descendant records vs. grant LOIs)
  - Hybrid pipeline pattern: Textract (OCR) → Configuration Table → Prompt → LLM → Rule-based post-processing → Confidence scoring
- **Cypher principle reinforced:** Non-extraction with human-enabled loops — automation accelerates the pattern, discernment stays with the community.
- **Action for Claude Code:** Replace hardcoded prompts in the Grant-Fit Scoring Agent and Intake Pipeline with APE-style optimization runs; build a configuration table that handles partner-specific schemas and a confidence-score field on every extraction output.

---

### COSMIC: A Galaxy Cluster–Finding Algorithm Using Machine Learning
- **Theme:** Clustering / Latent Structure / Unsupervised Learning
- **Tags:** clustering, xgboost, cnn, resnet, decision-trees, computer-vision, completeness-purity, latent-pattern-discovery, hyperparameter-tuning
- **Source:** Tian, Yang, Wen, Xia. *COSMIC: A Galaxy Cluster–Finding Algorithm Using Machine Learning.* The Astrophysical Journal Supplement Series, 276, 21 (2025). DOI 10.3847/1538-4365/ad8bbd
- **Applies to artifacts:**
  - Artifact #3 — Cohort Learner Journey Clustering (LCA evaluation upgrade)
  - Artifact #7 — Generational Memory Forecast (pattern-first modeling)
  - Artifact #4 — Ancestor Search RAG (thematic clustering of oral histories)
- **Key methodology to adopt:**
  - Two-stage ML — XGBoost classifier for "is this a cluster" + ResNet-34 regression for "how rich is the surrounding field"
  - Evaluation metrics: completeness (recall of known clusters) and purity (precision of detections) — the only honest pair for pattern discovery
  - Hyperparameter optimization via cross-validation across multiple data subsets
  - Posture: learn patterns from the data rather than imposing theory-first taxonomies
- **Cypher principle reinforced:** Sankofa — look back at what is already in the archive to inherit forward; let community patterns surface their own latent structure rather than fitting elder testimony into outside categories.
- **Action for Claude Code:** For Artifact #3, log completeness and purity alongside any LCA cluster solution; for Artifact #4, prototype an XGBoost-on-vector-embeddings classifier that surfaces thematic clusters in oral histories without imposing predefined codes.
  
---

## Wk3 | 5.12.26

### Attribution Crisis in LLM Search Results — Estimating Ecosystem Exploitation
- **Theme:** RAG / LLM Evaluation
- **Tags:** attribution, audit, non-extraction, RAG, hurdle-model, citation-gap
- **Source:** Data & Policy (2026), 8: e15 — doi:10.1017/dap.2026.10064
- **Applies to artifacts:**
  - Artifact #4 — Ancestor Search RAG (citation-required outputs)
  - Artifact #5 — Grant-Fit Scoring Agent (auditable attribution)
  - Cypher Impact Lab QA framework
- **Key methodology to adopt:**
  - Hurdle Model for measuring attribution gap (binary occurrence + continuous intensity)
  - Two-question framing: (1) Is there a gap? (2) How large is the gap?
  - Required telemetry: search trace, citation logs, standardized output
- **Three exploitation patterns to defend against:**
  1. No-search (relying on pretrained data without disclosure) — 15–35% occurrence
  2. No-citation (high consumption, zero attribution) — ~30%
  3. High-volume / low-credit (querying many sites, citing few) — Perplexity pattern
- **Cypher principle reinforced:** Citation IS consent. RAG without attribution = extraction.
- **Action for Claude Code:** Every retrieval-based pipeline must log source IDs alongside
  generated output. Build attribution gap measurement into Artifact #4's QA layer.

---

### Cognitive Presence + ENA in GenAI-Integrated Six-Hat Thinking
- **Theme:** Clustering / Learning Analytics
- **Tags:** clustering, learning-analytics, MOOCs, ENA, cognitive-presence, Impact-Lab-QA, six-hat
- **Source:** Yu et al. — Int J Educ Technol High Educ — doi.org/10.1186/s41239-025-00545-x
- **Applies to artifacts:**
  - Artifact #3 — Cohort Learner Journey Clustering
  - Cypher Impact Lab™ measurement upgrade
  - Future: Community Remembrance Circle facilitation tooling
- **Key methodology to adopt:**
  - Epistemic Network Analysis (ENA) via ENA Webkit — app.epistemicnetwork.org
  - Coding scheme: Triggering → Exploration → Integration → Resolution
  - Sliding window co-occurrence for measuring cognitive flow
- **Instruments referenced:** TTCT (Torrance Test for Creativity), SCCT, ENA Webkit
- **Cypher principle reinforced:** Structured cognitive scaffolding produces measurable
  community knowledge production. Frequency alone undersells the work.
- **Critical observation:** GenAI is a springboard for high-creativity users AND a crutch
  for low-creativity users. Cypher facilitation must elevate, not flatten.
- **Action for Claude Code:** When designing Impact Lab tooling, structure conversational
  data capture to allow downstream ENA analysis. Tag conversation segments by cognitive phase.

---

### VogFashion — AI-Driven Intelligent System (CLIP + NEO4j + Microservices)
- **Theme:** RAG / Knowledge Graphs
- **Tags:** RAG, knowledge-graphs, NEO4j, CLIP, microservices, CSUQ, QA, metacognition
- **Source:** Chen, Gao, Guo, Liu, Liu, Zheng, Wang — Wuhan Textile University
- **Applies to artifacts:**
  - Artifact #4 — Ancestor Search RAG (Graph RAG architecture)
  - Cypher Impact Lab — community feedback as QA
  - Future: Multi-agent collaboration prototype
- **Key methodology to adopt:**
  - CSUQ (Computer System Usability Questionnaire) as user-satisfaction QA for GenAI tools
  - NEO4j knowledge graph for relating "how" (tasks) to "what" (memory/assets)
  - Metacognition framework: generate → measure semantic relevance → iterate if below threshold
- **Cypher principle reinforced:** Community feedback IS the QA layer — not artificial
  metrics alone. MEL practice (Monitoring, Evaluation, Learning) maps directly to GenAI QA.
- **Action for Claude Code:** Architect Ancestor Search RAG with a knowledge graph layer
  (consider NEO4j or Neo4j-equivalent) for relationship-aware retrieval, not just vector similarity.

---

## Index Conventions

- **Theme:** One of three — Clustering / RAG / Explainable AI & Fairness
- **Tags:** Searchable keywords for code-task matching
- **Applies to artifacts:** Specific Cypher Build artifacts (#1–#7) or strategic areas
- **Key methodology to adopt:** Concrete technical practices to implement
- **Cypher principle reinforced:** Mission alignment — why this matters for non-extraction
- **Action for Claude Code:** Direct instruction for AI-assisted coding sessions

---

## How Claude Code Should Use This Index

Before scaffolding any new pipeline:
1. Scan tags for matches with the current task.
2. If a methodology applies, propose it explicitly in the plan.
3. Cite the reflection (Wk# + paper title) in code comments where the method is implemented.
4. If no methodology applies, note that this is greenfield design — flag for owner review.

The reading is the architecture. The code is the inheritance.
