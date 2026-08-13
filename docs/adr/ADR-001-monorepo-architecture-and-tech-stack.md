# ADR-001: Selection of Modular Monorepo Architecture & Technology Stack

* **Status:** Accepted
* **Date:** 2026-08-13
* **Author:** Lead Systems Architect

---

## Context
**PitStrategy-X** requires high-frequency telemetry processing (60-100 Hz), complex parallel GPU computations (Monte Carlo simulations for tire wear and traffic scenarios), and enterprise-grade business workflow orchestration (pit stop approvals and inventory). 

We required a cohesive architecture that balances extreme computational performance with strict domain boundaries and rapid developer iteration.

---

## Decision

We decided to adopt a **Modular Monorepo pattern** organized into three primary domain tiers:

1. **Computation Tier (`services/engine-simulation`):** C, Cython, CUDA, and FastAPI wrapper. Selected for deterministic low-latency execution and GPU parallel acceleration.
2. **Streaming Tier (`services/streaming-telemetry`):** Apache Kafka and PySpark Structured Streaming. Selected for zero-drop ingestion at 100 Hz and windowed aggregations.
3. **Core Orchestration Tier (`services/core-orchestration`):** Java 21, Spring Boot 3 (Hexagonal Architecture), and Camunda BPMN. Selected for enterprise workflow governance, DDD domain clarity, and long-term maintainability.

---

## Consequences

### Positive
- Unified repository control for multi-language components (C, Python, Java).
- Single source of truth for telemetry schemas (`schemas/telemetry`).
- Clear separation between raw compute logic and domain orchestration rules.

### Negative / Trade-offs
- Requires multi-language build tooling (`CMake`, `Maven`, `pip/poetry`).
- Docker local environment demands higher hardware resources (GPU enablement + Kafka cluster).