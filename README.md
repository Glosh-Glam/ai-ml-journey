# AI & ML Engineering: Self-Paced Program

A free, 16-week, ~20 h/week plan that covers every topic and project in the
[TripleTen AI & Machine Learning syllabus (2026)](https://tripleten.com/usa-documents/syllabuses/aiml-syllabus-2026.pdf).
That program costs about $17k. This plan does the same work with free courses and videos, and Claude Code reviews each week's work.

**Goal:** finish with 5 production-style projects that combine into one deployed AI product.

| # | Project | Weeks | Hours | Folder |
|---|---------|-------|-------|--------|
| 1 | **Pulse:** PRD → data pipeline → trained & tracked model | 1–5 | 100 | [`projects/01-pulse`](projects/01-pulse) |
| 2 | **Pulse in production:** model as a service (FastAPI, Docker, K8s, AWS) | 6–8 | 60 | [`projects/02-pulse-service`](projects/02-pulse-service) |
| 3 | **CareScribe:** fine-tune an open LLM with LoRA/QLoRA | 9–11 | 60 | [`projects/03-carescribe`](projects/03-carescribe) |
| 4 | **Resolve:** RAG + LangGraph support agent with guardrails | 12–14 | 60 | [`projects/04-resolve`](projects/04-resolve) |
| 5 | **Atlas:** capstone SaaS dashboard, deployed | 15–16 | 40 | [`projects/05-atlas`](projects/05-atlas) |

TripleTen budgets ~404 h. This plan has 320 h, so it saves time in three ways: theory comes from focused videos instead of long lesson series, Kubernetes runs locally, and the paid AWS services (SageMaker, Bedrock AgentCore) are optional stretch goals.

---

## How each week works (20 h)

| Block | Hours | What |
|-------|-------|------|
| Theory | ~6 | The videos and readings listed for that week. Take notes in `notes/weekNN.md`. |
| Build | ~12 | The week's milestone in the project folder. |
| Ship + review | ~2 | Push your work, then ask Claude Code to evaluate it (see [EVALUATION.md](EVALUATION.md)). |

Suggested rhythm: 2 h on each weekday evening (theory and small tasks), plus 5 h on each weekend day (building).

---

## Week-by-week plan

### Week 0 (optional, before you start): check your foundations
If any of these feel shaky, take a few days on them first: Python functions and classes, git, the terminal, basic SQL, and pandas.
- 📺 [CS50P Python](https://cs50.harvard.edu/python/) (only the lectures you need)
- 📺 [Kaggle Learn: Python, Pandas, SQL](https://www.kaggle.com/learn) (short and hands-on)
- 📖 [Missing Semester (shell, git)](https://missing.csail.mit.edu/)

---

### Project 1: Pulse (Weeks 1–5)

**Week 1: Spec, Claude Code, data from the web**
- 📺 [Claude Code in Action (Anthropic Academy, free)](https://anthropic.skilljar.com/) + [Claude Code docs](https://docs.anthropic.com/en/docs/claude-code/overview): CLAUDE.md, the draft→verify workflow
- 📖 [Google: Rules of ML, rules 1–20](https://developers.google.com/machine-learning/guides/rules-of-ml): framing, metrics, baselines
- 📖 [MBTA V3 API docs](https://api-v3.mbta.com/docs/swagger/index.html) (get a free API key)
- 🛠 Milestone: `SPEC.md` (PRD → ML spec), a CLAUDE.md for the repo, and a script that pulls live MBTA predictions/vehicles

**Week 2: Ingestion pipeline (API → validation → PostgreSQL)**
- 📺 [Postgres in Docker + SQL basics (DataTalksClub DE Zoomcamp, module 1)](https://github.com/DataTalksClub/data-engineering-zoomcamp)
- 📖 [Pydantic docs](https://docs.pydantic.dev/latest/) for validation · [Postgres `INSERT … ON CONFLICT`](https://www.postgresql.org/docs/current/sql-insert.html) for idempotent upserts
- 🛠 Milestone: a `stop_events` table filled by a re-runnable ingest job; running it twice adds no duplicates

**Week 3: Regression & classification with scikit-learn**
- 📺 [StatQuest](https://www.youtube.com/@statquest): Linear Regression, Logistic Regression, Bias/Variance, Cross-Validation, ROC & AUC, Confusion Matrix, Precision/Recall
- 📺 [Andrew Ng ML Specialization, Course 1 (audit free)](https://www.coursera.org/specializations/machine-learning-introduction)
- 📖 [scikit-learn: Pipelines, ColumnTransformer, encoding & scaling](https://scikit-learn.org/stable/modules/compose.html)
- 🛠 Milestone: a regressor that predicts delay minutes and a classifier for "late > 5 min?", each compared against a dumb baseline

**Week 4: Metrics, thresholds, class imbalance**
- 📺 [Google ML Crash Course: classification & metrics](https://developers.google.com/machine-learning/crash-course)
- 📖 [sklearn: precision-recall curves, threshold tuning](https://scikit-learn.org/stable/modules/classification_threshold.html)
- 🛠 Milestone: ROC/PR curves, a threshold chosen for the business goal in SPEC.md, imbalance handled (class weights or resampling), and an MLflow run logged for every experiment
- 📖 [MLflow tracking quickstart](https://mlflow.org/docs/latest/getting-started/)

**Week 5: Neural networks & PyTorch**
- 📺 [3Blue1Brown: Neural Networks, ch. 1–4](https://www.3blue1brown.com/topics/neural-networks)
- 📺 [Karpathy: micrograd, "The spelled-out intro to neural networks"](https://karpathy.ai/zero-to-hero.html)
- 📖 [PyTorch: Learn the Basics](https://pytorch.org/tutorials/beginner/basics/intro.html) · [learnpytorch.io ch. 0–2](https://www.learnpytorch.io/)
- 🛠 Milestone: a PyTorch MLP on the same features (train/val loop, early stopping, optimizer/loss comparison) logged to MLflow, plus a `RESULTS.md` that says which model wins and why

### Project 2: Pulse in production (Weeks 6–8)

**Week 6: FastAPI + model serialization**
- 📖 [FastAPI tutorial (official)](https://fastapi.tiangolo.com/tutorial/)
- 📖 [Made With ML: Serving & Testing](https://madewithml.com/)
- 📖 [sklearn model persistence and its security notes](https://scikit-learn.org/stable/model_persistence.html) (the "joblib traps")
- 🛠 Milestone: `/predict` with a Pydantic schema, API-key auth, rate limiting, `/health`, a versioned model loaded at startup, and pytest tests

**Week 7: Docker, Compose, Kubernetes**
- 📺 [TechWorld with Nana: Docker crash course & Kubernetes crash course](https://www.youtube.com/@TechWorldwithNana)
- 📖 [kind (local K8s cluster)](https://kind.sigs.k8s.io/)
- 🛠 Milestone: a Dockerfile (multi-stage, non-root), docker-compose (api + postgres), and K8s manifests (Deployment, Service, ConfigMap/Secret, readiness/liveness probes, HPA) running on kind with a zero-downtime rollout demoed

**Week 8: AWS + async inference + observability**
- 📺 [AWS Cloud Practitioner full course (freeCodeCamp, Andrew Brown)](https://www.youtube.com/@freecodecamp): IAM, S3, EC2, ECR, ECS, SQS, SNS, Lambda, DynamoDB
- 📖 [AWS Skill Builder (free tier courses)](https://skillbuilder.aws/)
- 📺 [DataTalksClub MLOps Zoomcamp: deployment & monitoring modules](https://github.com/DataTalksClub/mlops-zoomcamp)
- 🛠 Milestone: image pushed to ECR and running on ECS, an API → SQS → Lambda worker → DynamoDB flow for batch predictions, structured logs + metrics, and a `DESIGN.md` architecture diagram
- ⚠️ **Set an AWS billing alarm at $5 before you start.** Tear down everything you create at the end of the week.

### Project 3: CareScribe (Weeks 9–11)

**Week 9: Transformers & LLM fundamentals**
- 📺 [3Blue1Brown: Transformers & Attention, ch. 5–7](https://www.3blue1brown.com/topics/neural-networks)
- 📺 [Karpathy: "Let's build GPT from scratch"](https://karpathy.ai/zero-to-hero.html)
- 📖 [The Illustrated Transformer](https://jalammar.github.io/illustrated-transformer/) · [The Illustrated BERT](https://jalammar.github.io/illustrated-bert/)
- 📖 [Hugging Face LLM Course, ch. 1–3](https://huggingface.co/learn/llm-course)
- 🛠 Milestone: a notebook that runs a small model with different temperature, top-p, and repetition-penalty settings and shows the effect side by side, plus JSON-structured output

**Week 10: Data curation + LoRA/QLoRA**
- 📖 [HF PEFT docs: LoRA](https://huggingface.co/docs/peft) · [QLoRA + bitsandbytes guide](https://huggingface.co/docs/transformers/quantization/bitsandbytes)
- 📖 [Unsloth fine-tuning notebooks (free Colab T4)](https://github.com/unslothai/unsloth)
- 🛠 Milestone: a cleaned and de-identified dataset (e.g. [MTSamples on Kaggle](https://www.kaggle.com/datasets/tboyle10/medicaltranscriptions); strip names, dates, and IDs with regex or [Presidio](https://microsoft.github.io/presidio/)), plus a QLoRA fine-tune of a 1–3B model on Colab or Kaggle GPUs
- 💡 Free GPUs: Google Colab (T4) and Kaggle (30 h/week). SageMaker is an optional stretch goal.

**Week 11: LLM evaluation**
- 📖 [HF LLM Course: evaluation chapter](https://huggingface.co/learn/llm-course) · [Anthropic: define success & build evals](https://docs.anthropic.com/en/docs/test-and-evaluate/develop-tests)
- 🛠 Milestone: a clinician-style rubric (accuracy, completeness, no hallucinated meds, style), base vs. fine-tuned compared on 30+ held-out notes, the adapter pushed to the Hugging Face Hub, and a `RESULTS.md`

### Project 4: Resolve (Weeks 12–14)

**Week 12: Prompt engineering + RAG with OpenSearch**
- 📖 [Anthropic interactive prompt engineering tutorial](https://github.com/anthropics/prompt-eng-interactive-tutorial) · [Anthropic courses repo](https://github.com/anthropics/courses)
- 📺 [DeepLearning.AI short courses (free)](https://www.deeplearning.ai/short-courses/): "Building and Evaluating Advanced RAG"
- 📖 [OpenSearch vector search docs](https://opensearch.org/docs/latest/vector-search/) (run it locally with Docker)
- 🛠 Milestone: a knowledge base (any public product docs) chunked, embedded, and indexed in OpenSearch, with a RAG answer function that cites its sources

**Week 13: Agents, LangGraph, MCP, tool calling**
- 📺 [LangChain Academy: Intro to LangGraph (free)](https://academy.langchain.com/)
- 📺 DeepLearning.AI: "AI Agents in LangGraph" and "MCP: Build Rich-Context AI Apps with Anthropic"
- 📖 [Model Context Protocol docs](https://modelcontextprotocol.io/)
- 🛠 Milestone: a support-ticket graph (classify → injection screen → retrieve → draft → output guardrail → escalate), tools exposed through an MCP server (a mock Jira/Confluence, or the free Atlassian cloud sandbox), and LangSmith tracing turned on

**Week 14: Evaluation, hallucination, OWASP, red teaming**
- 📖 [OWASP Top 10 for LLM Applications](https://genai.owasp.org/llm-top-10/)
- 🎮 [Lakera Gandalf](https://gandalf.lakera.ai/) for prompt-injection practice
- 📖 [Ragas metrics (faithfulness, answer relevancy)](https://docs.ragas.io/) · [LangSmith evaluation](https://docs.smith.langchain.com/)
- 🛠 Milestone: a 30-question eval set, LLM-as-a-judge scores, a red-team suite of 20+ attacks with pass/fail, and a `THREAT_MODEL.md` mapped to the OWASP Top 10
- 💡 Bedrock AgentCore is an optional stretch goal. The free path uses the Claude API (~$5 of credits) or a local model through [Ollama](https://ollama.com/).

### Project 5: Atlas (Weeks 15–16)

**Week 15: Scope and integrate**
- 📺 [Full Stack Deep Learning 2022: lectures on deployment and product](https://fullstackdeeplearning.com/course/2022/)
- 📖 [Streamlit docs](https://docs.streamlit.io/) (fastest) or Next.js if you want a real frontend
- 🛠 Milestone: a `FEATURES.md` that decides, for each feature, whether it should be deterministic or use generative AI (with cost and latency estimates), and a dashboard that calls the Pulse API, the CareScribe adapter, and the Resolve agent

**Week 16: Deploy and present**
- 🛠 Milestone: deployed on AWS (ECS/App Runner) or a free host (Render / Fly / HF Spaces), with a README hero section, architecture diagram, 3-minute Loom demo, and a resume bullet for each project
- Final review: a full portfolio evaluation by Claude Code

---

## Expected costs
| Item | Cost |
|------|------|
| All courses and videos above | $0 (audit Coursera for free) |
| AWS (free tier, with a billing alarm) | $0–15 |
| LLM API credits (Claude) | ~$5–20, or $0 with Ollama |
| GPUs | $0 (Colab/Kaggle) |

## Progress
Claude Code updates the scoreboard in [EVALUATION.md](EVALUATION.md) after each weekly review.
