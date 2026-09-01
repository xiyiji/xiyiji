## Hi, I'm Mengyun 👋

I'm an AI Engineer at Meta, based in Seattle — working on **model evaluation**, **calibration**, and **ML systems that hold up under distribution shift**.

I work on the part of machine learning that decides whether a model is actually fit to ship. Each repository documents what is known to be wrong with it before it documents what works.

---

### What I build

- 🧪 **Offline evaluation** — measuring exposure bias on real recommendation logs, so "it looks good offline" means something (GroundTruth)
- 📐 **Calibration under shift** — separating what a model gets right (ranking) from what silently breaks (probabilities) once traffic changes
- 🚀 **Deployable ML services** — FastAPI · Docker · CI, with leakage-safe features, cost-aware model selection and drift monitoring (Cognitive Shorts)
- ⚙️ **LLM serving infrastructure** — an OpenAI-compatible inference gateway with adaptive routing, dynamic batching, prefix caching and canary releases, paired with a Ray Serve + vLLM engine layer (LLM Serving Platform · InferenceGateway)
- 📚 **Interview-prep tooling** — a daily-updated question bank for ML engineers with reference answers and built-in AI walkthroughs (MLE Prep)
- ✍️ **Writing** — notes on AI engineering, agents and evaluation at [xiyiji.github.io/blogs](https://xiyiji.github.io/blogs/)

---

### Featured projects

| Project | What it does | Stack |
|---|---|---|
| [LLM Serving Platform](https://github.com/xiyiji/llm-serving-platform) ([live demo](https://llm-serving-platform.vercel.app)) | A self-hosted serving layer for LLM inference: OpenAI-compatible gateway with SSE streaming, latency-aware routing, dynamic micro-batching, prefix caching (**94.7%** hit rate under repeated-prompt load), warm-pool cold-start management, canary releases with **auto-rollback**, and a Next.js ops console. Pairs with [InferenceGateway](https://github.com/xiyiji/InferenceGateway) (Ray Serve + vLLM) as the engine layer. `27 tests` · CI · Docker/K8s/Terraform | Python · FastAPI · Next.js · TypeScript · Prometheus |
| [Cognitive Shorts](https://github.com/PSCRedefine) | An engagement-prediction model taken from notebook to four deployable services: [Single Prediction](https://github.com/PSCRedefine/SinglePrediction) · [Batch Prediction](https://github.com/PSCRedefine/BatchPrediction) · [Model Info](https://github.com/PSCRedefine/ModelInfo) · [Analytics Dashboard](https://github.com/PSCRedefine/AnalyticsDashboard). Four candidates finished statistically tied, so operating cost broke the tie — the shipped artefact is **1,958× smaller** and 35× faster than the runner-up. `292 tests` · CI on Python 3.11–3.13 | Python · FastAPI · Docker · scikit-learn |
| [GroundTruth](https://github.com/PSCRedefine/groundtruth) | Unbiased offline evaluation on real Kuaishou short-video logs (2.6M interactions). Ranking survives the exposure shift almost intact; calibration collapses — the model is **2×** as confident as reality on traffic it did not select. Every figure reproduces from a committed JSON artefact. `ROC-AUC 0.8811` | Python · pandas · scikit-learn · LightGBM |
| [MLE Prep](https://mle-prep-pi.vercel.app/) ([source](https://github.com/xiyiji/mle-prep)) | A growing machine-learning-engineer interview question bank, updated daily: 360+ questions across ML coding, theory, LLMs & agents, ML systems, MLOps, recommender systems, AI safety, multimodal and behavioural, filterable by category and difficulty. Reference answers give an answer framework, key points, common follow-ups and further reading, and any question can be handed to Claude or ChatGPT for a walkthrough. In Chinese. | HTML · JavaScript · KaTeX · Vercel |

---

### Tech stack

**ML & evaluation**
`scikit-learn` `LightGBM` `pandas` `NumPy` `paired bootstrap` `calibration`

**Serving & operations**
`FastAPI` `Docker` `Kubernetes` `Prometheus` `Grafana` `pytest` `GitHub Actions`

**Languages & web**
`Python` `JavaScript` `HTML/CSS` `Vercel` `GitHub Pages`

<!-- TODO: add the frameworks and infrastructure you use day to day that are not visible in your public repos (e.g. PyTorch, Spark, cloud platforms). Only what you actually use. -->

---

### Writing

I write about what I actually build and measure — the negative results included.

- 📝 [MCP is not dead — it is just not a personal-productivity tool](https://xiyiji.github.io/blogs/mcp-is-not-dead.html) — the CLI-versus-MCP argument is really an ownership question
- 📚 [All posts](https://xiyiji.github.io/blogs/) — daily notes on AI engineering and evaluation

---

### Currently

- 🔨 Building: [MLE Prep](https://mle-prep-pi.vercel.app/) — new questions and reference answers added daily
- 📖 Writing: daily notes on AI engineering and evaluation
<!-- TODO (optional): a "🔍 Open to: …" line if you want to signal roles you are interested in. Delete this comment if not. -->

---

📍 Seattle  |  💼 [LinkedIn](https://www.linkedin.com/in/mengyunwang)  |  🌐 [xiyiji.github.io](https://xiyiji.github.io/)  |  📫 mengyun_wang_ai@outlook.com
