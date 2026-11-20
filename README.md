# Miles Waite

AI systems architect.

I build governed, evaluation-driven AI systems that reason over operational data and take actions only under auditable human control.

## Selected work

### Aegis Global Intelligence — Fragility & Convexity Intelligence Platform

**Problem.** External events can expose structural weaknesses in organisations and live projects. Conventional risk scoring focuses on event severity and geographical exposure, often overlooking the underlying characteristics that determine whether an organisation can absorb, adapt to, or benefit from disruption. Aegis addresses this through organisational fragility characterisation: understanding dependencies, concentration, substitutability, operational slack, nonlinear thresholds and interdependencies. Drawing on Taleb's concepts of fragility, concavity and convexity, the objective is to understand not simply what might happen, but why an organisation may be structurally vulnerable to it.

**Architecture.** A FastAPI service accepts external events and returns `202 Accepted`. An asynchronous worker normalises and classifies events, retrieves supporting evidence, generates schema-validated shock profiles and evaluates their interaction with persistent, client-specific Fragility Registers. Structured intelligence models characterise organisational dependencies, resilience capacity, potential concavity, convexity and critical thresholds. A deterministic stress-testing engine evaluates nonlinear response functions, slack depletion, threshold crossings and potential cascading consequences. LLMs support evidence interpretation, profile elicitation and consequence analysis, while business decisions and mathematical calculations remain independently testable and deterministic. Persistence and messaging sit behind port interfaces, with SQLite and an in-memory bus for local development, and Firestore / Pub/Sub adapters for Google Cloud Run.

**Outcome.** The repository contains the working event-processing pipeline, a React dashboard, unit, integration, contract and evaluation tests, and deployment manifests. A Cloud Run API is deployed and, as of 20 November 2026, 09:47 Europe/London, `/health` reported healthy using the deterministic model provider with 29 indexed knowledge-base documents. The existing infrastructure provides the foundation for evolving Aegis into a continuous organisational fragility characterisation and event-driven stress-testing platform. This is a platform in active development; nonlinear fragility measurement, convexity characterisation and antifragility assessment remain areas for implementation and empirical validation.

### [AP Automation — Governed Agentic Invoice Coding](https://github.com/WaiteM124/ap-automation-public)

**Problem.** Non-PO invoice coding is repetitive, but a wrong posting is a financial error. AI can help only if it never holds authority to post.

**Architecture.** The first proving ground for a governed enterprise agentic AI platform: models provide evidence, policy owns decisions, and humans keep authority over financial actions. Vendor-scoped hybrid retrieval and master data feed specialist entity, VAT and cost-centre agents. A routine model makes a provisional recommendation and Claude is consulted only on configured conflicts. A versioned, fail-closed policy engine selects the strictest state (`AUTO_POST` shadow-only, `HUMAN_REVIEW`, `REJECT`, `INSUFFICIENT_EVIDENCE`), and an idempotent write-back boundary rechecks authorisation before any ERP action. See the [architecture write-up](https://github.com/WaiteM124/ap-automation-public/blob/main/ARCHITECTURE.md) and [strategy deck](https://github.com/WaiteM124/ap-automation-public/blob/main/docs/architecture-strategy.pdf).

**Outcome.** A working proof of concept with FastAPI, LangGraph orchestration, SAP and Xero posting adapters, and an offline suite of 347 passing tests in CI. Published results use synthetic and public data only.

### [VaR Agent — Natural-Language Risk Analysis for a Synthetic Energy Book](https://github.com/WaiteM124/var-agent)

**Problem.** Risk desks get the same questions repeatedly — what is book VaR, who is concentrated, is anyone over a limit — but an LLM must not invent the numbers or pretend to be a live risk engine.

**Architecture.** A deterministic risk package filters a 15-position synthetic energy book, aggregates pre-computed 1-day VaR, runs a seeded correlated Monte Carlo, and checks illustrative notional and VaR limits, all without cloud credentials. A LangGraph agent, served by FastAPI and a Streamlit UI, answers natural-language questions by calling those tools and retrieving methodology notes from Azure AI Search. Azure clients are created only when `/query` is called. See the [worked example](https://github.com/WaiteM124/var-agent/blob/main/examples/output/summary.md) and [P&L chart](https://github.com/WaiteM124/var-agent/blob/main/examples/output/pnl_distribution.png).

**Outcome.** A public proof of concept with 27 tests and ruff in CI, plus a committed Monte Carlo run (seed 42, 20,000 paths) showing a diversified 95% VaR of $970,831 against a $41.35m notional book. This is a demo, not a production ETRM.

### [Miles RAG](https://github.com/WaiteM124/miles-rag)

**Problem.** A retrieval-augmented assistant needs to find the right context, refuse when it cannot, and be evaluated honestly.

**Architecture.** Hybrid BM25 and dense retrieval are fused with weighted RRF, filtered by a score threshold, then optionally re-ranked by a cross-encoder. Grounded generation with Claude cites sources and emits a structured refusal when no chunk clears the threshold, so the model is not asked to answer from empty context. An offline evaluation harness runs without an API key.

**Outcome.** The public repository is an explicit proof of concept: three sample ERP/FP&A chunks and a 35-question golden set. Offline retrieval evaluation recorded a hit rate @ 8 of 100% and MRR of 1.000 on that tiny corpus; the README explains why those scores should be expected to fall on a larger collection. CI (ruff and pytest) is in place and has been passing. LLM-judged quality metrics have not been published yet.

### [Governed Agent Toolkit](https://github.com/WaiteM124/governed-agent-toolkit)

**Problem.** An agent can propose a write to a downstream system. That proposal must not become a transaction without validation, duplicate checks, and human approval.

**Architecture.** A small Python library enforces a fixed pipeline: Pydantic tool-schema validation, idempotent replay, fuzzy duplicate detection, and an approval-gate state machine. Execution happens only after approval. Self-approval is rejected; schema failures create no governance state.

**Outcome.** A dependency-light reference implementation with an in-memory demo and an offline pytest suite covering the state machine, scorer, schemas, and composed write path. Persistence, async execution, and multi-tenancy are intentionally out of scope.

Further case studies, including operational invoice-coding work, are on [ai.mileswaite.net](https://ai.mileswaite.net).

## Stack

Python, FastAPI, LangGraph, Pydantic, pytest, ruff, React, TypeScript, Vite, Qdrant, Docker, Google Cloud Run, Firestore, and Pub/Sub.

## Links

- Site: [ai.mileswaite.net](https://ai.mileswaite.net)
- LinkedIn: [Miles Waite](https://www.linkedin.com/in/miles-waite-46628a3b2/)
- Email: [waite.miles@proton.me](mailto:waite.miles@proton.me)
