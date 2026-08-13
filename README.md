# 🏎️ PitStrategy-X

**PitStrategy-X** is an enterprise-grade, high-frequency real-time telemetry processing and strategy simulation platform engineered for multi-category motorsport (Formula 1, WEC, IndyCar, MotoGP).

The system captures vehicle telemetry at **60-100 Hz**, executes GPU-accelerated Monte Carlo simulations (tire degradation, track traffic, stint deltas, Safety Car probability windows), and exposes optimal pit stop windows via a microservices architecture.

---

## 📊 Public Project Management & Documentation

This project follows strict software engineering and agile practices. All tracking and design decisions are public:

- 📋 **Jira Software (Kanban & Sprint Tracker):** [PitStrategy-X Jira Workspace](https://novavia2026.atlassian.net/jira/software/projects/PIT/list)
- 📚 **Confluence (Architecture, ADRs & Specs):** [PitStrategy-X Confluence Wiki](https://novavia2026.atlassian.net/wiki/spaces/PIT)
* 📄 **Public Offline Documentation:** All ADRs, C4 System Architecture diagrams, and telemetry specifications are publicly mirrored in the [`/docs`](./docs) folder of this repository.

---

## 🛠️ Technology Stack

- **Low-Level Compute Engine:** C, Cython, CUDA (GPU parallel computing for strategy simulation).
- **Processing & Numerical API:** Python 3.12+, FastAPI, NumPy, Pandas.
- **Big Data Streaming:** Apache Kafka, PySpark Structured Streaming.
- **Core Orchestration & Business:** Java 21, Spring Boot 3 (Hexagonal Architecture / DDD), Camunda BPMN 7/8.
- **Persistence & Spatial Data:** PostgreSQL 16, PostGIS (Circuit spatial mapping & lap sector tracking).
- **DevOps & Infrastructure:** Docker, Kubernetes (GPU pod scheduling), GitHub Actions.

---

## 🚀 Repository Architecture

```text
pitstrategy-x/
├── services/
│   ├── engine-simulation/      # C + CUDA + FastAPI simulation kernel
│   ├── core-orchestration/     # Java 21 Spring Boot + Camunda business service
│   └── streaming-telemetry/    # PySpark streaming processing pipeline
├── ingestion/                  # Adapters: FastF1, OpenF1, Local UDP, Synthetic
├── deployments/                # Docker Compose & Kubernetes manifests
└── docs/                       # Architecture Decision Records (ADRs) & C4 diagrams
```

---

## 🚦 Getting Started (Local Development)

### Prerequisites
- Docker Engine `>= 24.0` & Docker Compose `v2+`
- NVIDIA Container Toolkit (for GPU simulation support)
- Java OpenJDK `21`
- Python `3.12+`
- CMake `>= 3.22` & GCC/NVCC toolchain

### Quick Setup
```bash
# Clone repository
git clone https://github.com/your-username/pitstrategy-x.git
cd pitstrategy-x

# Spin up core infrastructure (Kafka, Postgres/PostGIS, Camunda)
docker compose -f deployments/docker-compose.yml up -d
```

---

## 📜 License
This project is released under the **MIT License**.