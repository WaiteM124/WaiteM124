# Miles Waite

AI systems architect.

I build governed, evaluation-driven AI systems that reason over operational data and take actions only under auditable human control.

## Selected work

### [Aegis Global Intelligence](https://github.com/WaiteM124/aegis-global-intelligence)

**Problem.** External events can affect clients and live projects, but relevance, evidence, and risk need to be assessed consistently rather than as one-off judgements.

**Architecture.** A FastAPI service accepts an event and returns `202 Accepted`. An async worker then normalises and classifies the event, retrieves evidence, generates schema-validated assessment text, and assigns a deterministic risk score. Business decisions (matching, classification, scoring) are not left to the model. Persistence and messaging sit behind port interfaces, with SQLite and an in-memory bus for local use, and Firestore / Pub/Sub adapters for Google Cloud Run.

**Outcome.** The repository contains the working pipeline, a React dashboard, unit, integration, contract, and evaluation tests, and deployment manifests. A Cloud Run API is deployed and, as of 20 November 2026, 09:47 Europe/London, `/health` reported healthy using the deterministic model provider with 29 indexed knowledge-base documents. This is a platform in active development, not a claim of production traffic or measured model quality.

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

Python, FastAPI, Pydantic, pytest, ruff, React, TypeScript, Vite, Qdrant, Docker, Google Cloud Run, Firestore, and Pub/Sub.

## Links

- Site: [ai.mileswaite.net](https://ai.mileswaite.net)
- LinkedIn: [Miles Waite](https://www.linkedin.com/in/miles-waite-46628a3b2/)
- Email: [waite.miles@proton.me](mailto:waite.miles@proton.me)
