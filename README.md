## Hi, I'm Mengyun 👋

I'm a Software Engineer at Meta, based in Bellevue, WA — working on **model evaluation**, **calibration**, and **ML systems that hold up under distribution shift**.

I work on the part of machine learning that decides whether a model is actually fit to ship. Each repository documents what is known to be wrong with it before it documents what works.

📍 Seattle  |  💼 [LinkedIn](https://www.linkedin.com/in/mengyunwang)  |  🌐 [xiyiji.github.io](https://xiyiji.github.io/)  |  📫 mengyun_wang_ai@outlook.com

---

### What I build

- 🔁 **Coding-agent harness** — typed tools, read-before-write gating, Docker sandbox, subagents, context compaction; **96% on a 25-exercise polyglot benchmark subset** (mini-harness)
- 🧵 **Durable agent runtime** — an event journal that lets a run **resume after `kill -9` with exactly-once effects**, a context budget that shrinks, summarises and pins, hybrid retrieval with reranking, and a namespace + cgroup sandbox that **held against 13 escape attempts** (Loomwork)
- 🧪 **Evaluation harnesses with regression gates** — recorded baselines re-scored in CI without an API key, deterministic scoring, LLM-as-judge reported but never gating; the harness is built first and the behaviour is changed against it (Loomwork · LLM Gateway · GroundTruth)
- 🤝 **Multi-agent execution with a human approval gate** — five agents, one orchestrator that owns every state change, replayable from the database (Atlas)
- ⚙️ **LLM serving infrastructure** — an OpenAI-compatible inference gateway with adaptive routing, dynamic batching, prefix caching and canary releases, paired with a Ray Serve + vLLM engine layer (LLM Serving Platform · InferenceGateway)
- 🚀 **Deployable ML services** — FastAPI · Docker · CI, with leakage-safe features and cost-aware model selection (Cognitive Shorts)
- 📚 **Interview-prep tooling** — a daily-updated question bank for ML engineers with reference answers and built-in AI walkthroughs (MLE Prep)

---

### Featured projects


| Project | What it does | Stack |
|---|---|---|
| [mini-harness](https://github.com/xiyiji/mini-harness) | A coding-agent harness in ~1,800 lines of Python: **nine Pydantic-typed tools**, **read-before-write gating** on every edit, a **no-network Docker sandbox**, subagents, context compaction, request retries and a Textual TUI. **Solves 24 of 25 exercises (96%)** from Aider's polyglot benchmark with claude-haiku-4-5 — Python 12/12, Go 11/12 — scored by each exercise's own test suite. Per-task turn cap, resumable benchmark driver. `16 offline tests` · fake model server · CI on Python 3.12–3.13 | Python · Pydantic · OpenAI SDK · Docker · Textual · pytest |
| [Loomwork](https://github.com/xiyiji/loomwork) | A durable agent runtime. An append-only SQLite journal lets a run **resume after `SIGKILL` with exactly-once side effects** — the test kills a real child process mid-run and counts twelve effects, not thirteen. Context compaction that shrinks, summarises and pins keeps a step-3 fact alive through a 40-step run on a 4k-token budget. Structure-aware chunking + BM25 + embeddings + RRF + cross-encoder rerank, judged on **67 real vLLM issue-tracker questions** against the maintainers' own answers: **R@5 0.51 vs 0.43** for keyword search. A bubblewrap + cgroup sandbox that **held against 13 escape attempts** (fork bomb, `/etc/shadow`, network, symlinks…). Two agents on it, 22 eval tasks, a **committed baseline re-scored in CI behind a regression gate**, no API key needed. MCP server over the tools; Next.js trace viewer. `104 tests` · CI | Python · SQLite · bubblewrap · cgroups · ONNX Runtime · FastMCP · Next.js |
| [Atlas](https://github.com/xiyiji/atlas-llm-execution-agent) ([live demo](https://xiyiji.github.io/projects/atlas-demo.html)) | Five agents — Planner, Safety, Coder, Browser, Verifier — run by **one orchestrator that owns every state change** and never calls a model itself. Plans are scored twice, by the Safety agent and by fixed rules, and anything over the line **waits for a person before it runs**. Every event is in the database before it reaches the UI, so a task **survives a restart and can be replayed**. Code runs in a network-less container with dropped capabilities; fetches are validated hop by hop against SSRF. Runs end-to-end with no model keys. `46 tests` · ruff · pip-audit · CI | Python · FastAPI · Celery · PostgreSQL · SSE |
| [LLM Gateway](https://github.com/xiyiji/llm-gateway) | Model routing improved against a graded benchmark: **46 tasks across three verification regimes** (exact-match math, sandboxed code, model-graded QA) with a cached result set, so every change to decision logic is scored on the same suite before it ships. Four generations of policy behind one interface — rules, a weighted score, logistic regression, and a from-scratch **PPO policy optimising quality − λ·cost** — hot-swappable at runtime. The learned policy held multi-step agent accuracy while **cutting cost 67% and latency 42%**; on held-out evals, **100% of large-model quality at 48% of the cost**, 803 RPS at P95 80 ms. | Python · FastAPI · PyTorch · SQLite |
| [LLM Serving Platform](https://github.com/xiyiji/llm-serving-platform) ([live demo](https://llm-serving-platform.vercel.app)) | A self-hosted serving layer for LLM inference: OpenAI-compatible gateway with SSE streaming, latency-aware routing, dynamic micro-batching, prefix caching (**94.7%** hit rate under repeated-prompt load), warm-pool cold-start management, canary releases with **auto-rollback**, and a Next.js ops console. Pairs with [InferenceGateway](https://github.com/xiyiji/InferenceGateway) (Ray Serve + vLLM) as the engine layer. `27 tests` · CI · Docker/K8s/Terraform | Python · FastAPI · Next.js · TypeScript · Prometheus |
| [Cognitive Shorts](https://github.com/PSCRedefine) | An engagement-prediction model taken from notebook to four deployable services: [Single Prediction](https://github.com/PSCRedefine/SinglePrediction) · [Batch Prediction](https://github.com/PSCRedefine/BatchPrediction) · [Model Info](https://github.com/PSCRedefine/ModelInfo) · [Analytics Dashboard](https://github.com/PSCRedefine/AnalyticsDashboard). Four candidates finished statistically tied, so operating cost broke the tie — the shipped artefact is **1,958× smaller** and 35× faster than the runner-up. `292 tests` · CI on Python 3.11–3.13 | Python · FastAPI · Docker · scikit-learn |
| [GroundTruth](https://github.com/PSCRedefine/groundtruth) | Unbiased offline evaluation on real Kuaishou short-video logs (2.6M interactions). Ranking survives the exposure shift almost intact; calibration collapses — the model is **2×** as confident as reality on traffic it did not select. Every figure reproduces from a committed JSON artefact. `ROC-AUC 0.8811` | Python · pandas · scikit-learn · LightGBM |
| [MLE Prep](https://mle-prep-pi.vercel.app/) ([source](https://github.com/xiyiji/mle-prep)) | A growing machine-learning-engineer interview question bank, updated daily: 360+ questions across ML coding, theory, LLMs & agents, ML systems, MLOps, recommender systems, AI safety, multimodal and behavioural, filterable by category and difficulty. Reference answers give an answer framework, key points, common follow-ups and further reading, and any question can be handed to Claude or ChatGPT for a walkthrough. In Chinese. | HTML · JavaScript · KaTeX · Vercel |

How each of these was built, and what broke along the way: xiyiji.github.io/blogs.


---

### Tech stack

**LLM & agents**
`agent runtime` `agent harness` `tool calling` `MCP` `multi-agent orchestration` `context compaction` `event sourcing / replay` `sandboxed execution (bubblewrap · cgroups · Docker)` `RAG` `BM25` `embeddings` `RRF fusion` `cross-encoder reranking` `model routing` `Anthropic API` `OpenAI API` `vLLM` `Ray Serve` `ONNX Runtime`

**Evaluation**
`eval harnesses` `golden datasets` `regression gates` `replayable eval runs` `LLM-as-judge` `polyglot benchmark` `trajectory-level failure analysis` `offline evaluation` `off-policy evaluation (IPS / SNIPS / DR)` `paired bootstrap` `calibration`

**ML & data**
`PyTorch` `Hugging Face` `scikit-learn` `LightGBM` `pandas` `NumPy` `DuckDB` `Parquet` `two-tower rankers` `PPO` `fine-tuning data curation`

**Backend & distributed systems**
`Python` `Java` `C++` `FastAPI` `gRPC` `Spring Boot` `Kafka` `Redis Streams` `stream processing` `exactly-once delivery` `idempotency` `PostgreSQL` `MySQL` `SQLite` `Celery` `SSE`

**Serving & operations**
`AWS` `Docker` `Kubernetes` `Terraform` `canary / staged rollout` `Prometheus` `Grafana` `OpenTelemetry` `pytest` `GitHub Actions` `uv`

**Web**
`TypeScript` `Next.js` `Textual` `Vercel` `GitHub Pages`


---

### Writing

I write about what I actually build.
 
- 📚 [All posts](https://xiyiji.github.io/blogs/) — daily notes on AI engineering learning.

---

### Currently

- 🔨 Building: [MLE Prep](https://mle-prep-pi.vercel.app/) — new questions and reference answers added daily
- 📖 Writing: daily notes on AI engineering and evaluation
<!-- TODO (optional): a "🔍 Open to: …" line if you want to signal roles you are interested in. Delete this comment if not. -->

