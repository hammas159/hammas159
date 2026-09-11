# Muhammad Hammas

**AI Engineer — retrieval, agents, and the parts that have to not break.**

Based in Pakistan. I build systems that are measured rather than demoed: every repository
below states what it does, what it refuses to do, and the numbers behind both.

**20 repositories · 1,027 tests · every dataset public and cited.**

---

### What I work on

**Retrieval** that cites its sources and declines when the evidence is thin.
**Agents** whose limits are enforced by the runtime rather than requested in a prompt.
**Generative AI** as an engineering problem — fine-tuning, routing, cost, and the evaluation
that tells you whether any of it helped.
**Applied ML and statistics**, where the usual failure is not the model but the question.
**Urdu NLP**, because tooling for 240 million speakers should not have to be rewritten from
scratch by every project that needs it.

---

## Projects

### Retrieval and RAG

| | What it is | The interesting part |
|---|---|---|
| **[rag-forge](https://github.com/hammas159/rag-forge)** | Production RAG — hybrid retrieval, cross-encoder reranking, span-level citations | Every quote is **located in the real source** before it becomes a citation. A quote that cannot be found is dropped, and that drop is a hallucination signal. |
| **[context-bench](https://github.com/hammas159/context-bench)** | RAG vs CAG vs MAG, measured on real data with ground-truth answers | Where the cost crossover actually sits, and why **prompt caching** — not retrieval quality — is what decides it. |
| **[pak-law-assistant](https://github.com/hammas159/pak-law-assistant)** | Legal QA over Pakistani statutes | It **will not cite a repealed provision**. Temporal corpus, citation parsing for statutory/subordinate/reported forms, and four explicit refusal conditions. |
| **[deep-research-agent](https://github.com/hammas159/deep-research-agent)** | A research agent that reports disagreement | Deduplicates republished copies **before** counting corroboration — otherwise one wire story reprinted twelve times reads as twelve sources agreeing. |

### Agents

| | What it is | The interesting part |
|---|---|---|
| **[bounded-agent-runtime](https://github.com/hammas159/bounded-agent-runtime)** | An agent runtime that enforces its own ceilings | A chaos suite replaces the agent with something guaranteed to misbehave, then asserts the irreversible action **did not happen** — not that the runtime said it stopped. |
| **[sql-analyst-agent](https://github.com/hammas159/sql-analyst-agent)** | English → SQL over a real Postgres | Three safety layers, and **the prompt is the weakest**. CI attempts five real writes as the agent's role on every push and fails the build if any succeeds. |
| **[enterprise-ops-crew](https://github.com/hammas159/enterprise-ops-crew)** | Multi-agent back office across four mock enterprise systems | It stops before anything irreversible. Business-hours SLAs, playbook execution, approval gates, full audit trail. |

### Generative AI and LLM platform

| | What it is | The interesting part |
|---|---|---|
| **[qlora-finetune-suite](https://github.com/hammas159/qlora-finetune-suite)** | The parts of fine-tuning that go wrong **before** the GPU is touched | Loss masking that stops the model learning to generate prompts, VRAM budgeting, leak-free splits. Runs without a GPU. |
| **[llm-gateway](https://github.com/hammas159/llm-gateway)** | One entry point for every LLM call | Routing by difficulty, per-tenant budgets, fallback chains, and guardrails that **redact secrets before they leave**. |
| **[llm-observability-platform](https://github.com/hammas159/llm-observability-platform)** | Monitoring built for LLM applications | Cost per *success* rather than per call, latency percentiles that exclude cache hits, and prompt drift detected by PSI **without ever storing a prompt**. |
| **[model-serving-platform](https://github.com/hammas159/model-serving-platform)** | Multi-model serving with A/B, canary and shadow traffic | Auto-rollback that knows the difference between a bad canary and an upstream outage — the distinction that decides whether rolling back helps. |

### Machine learning and statistics

| | What it is | The interesting part |
|---|---|---|
| **[machine-learning](https://github.com/hammas159/machine-learning)** | **Twenty** projects on public data, each built around the mistake that makes its answer wrong | 846 trading rules on *shuffled* S&P 500 beat the best rule on the real one. A column of random integers, target-encoded, lifts test AUC from 0.567 to 0.652. |
| **[credit-risk-engine](https://github.com/hammas159/credit-risk-engine)** | A scorecard that explains every decline in points | WoE/IV binning with leakage detection, adverse-action reason codes, and a fairness audit reporting **all four incompatible measures** rather than the flattering one. |
| **[demand-forecast-platform](https://github.com/hammas159/demand-forecast-platform)** | Hierarchical forecasting where the numbers add up | Reconciliation with coherence *asserted*, Croston for intermittent demand, rolling-origin backtest that provably cannot leak. |
| **[insurance-mlops](https://github.com/hammas159/insurance-mlops)** | The four things that break a deployed model | Point-in-time feature leakage, training/serving skew, undocumented models, unlawful data reuse. A release gate that **refuses rather than warns**. |

### Operations and documents

| | What it is | The interesting part |
|---|---|---|
| **[incident-copilot](https://github.com/hammas159/incident-copilot)** | AIOps — log templates, anomaly detection, alert correlation | Turns forty alarms into one incident with a suspect. The anomaly detector is robust to the outliers it is looking for. |
| **[doc-intelligence-api](https://github.com/hammas159/doc-intelligence-api)** | Document processing that sends a human **one question, not one document** | Cross-field arithmetic validation catches what OCR confidence never will. Pakistani formats: CNIC, NTN, STRN, PK IBAN. |
| **[urdu-nlp-toolkit](https://github.com/hammas159/urdu-nlp-toolkit)** | Urdu and Roman Urdu text processing | The same Urdu word has several byte encodings that render identically. Without normalising them, every downstream model learns three versions of one word. |

### Computational biology

| | What it is | The interesting part |
|---|---|---|
| **[clcuv-surveillance](https://github.com/hammas159/clcuv-surveillance)** | Genomic surveillance for Cotton Leaf Curl Virus, on real NCBI sequences | Collapsing clonal duplicates turned **9 "emerging variants" into 0**. The signal was the same isolate sequenced repeatedly. |
| **[primer-designer](https://github.com/hammas159/primer-designer)** | Diagnostic PCR primers that survive viral drift | Alerts when a deployed assay starts going blind because a mutation landed at the 3′ end. Nearest-neighbour thermodynamics, degenerate primers. |

---

### How I build

**Measured, not claimed.** No number appears in a README until it has been produced on a
machine. Where a result disagreed with what I expected, the README says so — several of
these projects exist because the first answer was wrong.

**Failure is a feature.** A RAG system that cannot say "I don't know" cannot be trusted with
the answers it does give. An agent that cannot be stopped is not autonomous, it is
unsupervised. Refusal rates and containment are scored metrics, not edge cases.

**Enforced, not requested.** Safety that lives in a prompt is a suggestion. It belongs in a
database role, a parse tree, or a budget the agent cannot reach.

**Limits stated plainly.** Every README has a section on what the project does not do. A tool
that overclaims wastes the time of everyone who tries it.

---

### Stack

`Python` · `FastAPI` · `PostgreSQL + pgvector` · `Redis` · `Docker` · `uv` · `PyTorch` ·
`scikit-learn` · `pandas` / `NumPy` / `statsmodels` · `sentence-transformers` ·
`Ollama` / `Claude` / `HuggingFace` behind one interface · `GitHub Actions`

---

📫 Open to AI/ML engineering roles.
