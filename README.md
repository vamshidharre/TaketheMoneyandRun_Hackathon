# Rivyn: AI Log Intelligence Platform

[![Hackathon Winner](https://img.shields.io/badge/MHP_Hackathon-1st_Place_Winner_🏆-gold.svg)](https://github.com/rivyn-labs/rivyn)
[![START Stuttgart](https://img.shields.io/badge/START_Stuttgart-AI_Hackathon-blueviolet.svg)](https://github.com/rivyn-labs/rivyn)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115+-009688.svg?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com)
[![PyArrow](https://img.shields.io/badge/PyArrow-Columnar_Parquet-teal.svg)](https://arrow.apache.org/docs/python/)
[![Scikit-Learn](https://img.shields.io/badge/Scikit_Learn-Isolation_Forest-F7931E.svg?logo=scikitlearn&logoColor=white)](https://scikit-learn.org)
[![OpenAI GPT-4o](https://img.shields.io/badge/OpenAI-GPT--4o_LLM-412991.svg?logo=openai&logoColor=white)](https://openai.com)
[![Tests](https://img.shields.io/badge/pytest-31_passed-brightgreen.svg)](https://pytest.org)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

> [!IMPORTANT]
> ### 🚀 Repository Migration Notice
> This repository (`vamshidharre/TaketheMoneyandRun_Hackathon`) preserves the original winning submission from the **MHP Hackathon ("Take the Money and Run")** hosted by **START Stuttgart** at **MHP – A Porsche Company** in Ludwigsburg, Germany.
> 
> **All active development, production releases, enterprise features, and roadmap tracking have officially moved to our organization repository:**
> ### 👉 **[https://github.com/rivyn-labs/rivyn](https://github.com/rivyn-labs/rivyn)** (Organization: **[rivyn-labs](https://github.com/rivyn-labs)**)
> 
> *Please star, fork, clone, and follow our progress on the new repository!*

---

<div align="center">
  <img src="assets/brand/rivyn/rivyn-logo-transparent.png" alt="Rivyn Logo" width="380">
  <p><strong>Turn Multi-Gigabyte Raw Log Floods into Resolved Incidents in Seconds.</strong></p>
</div>

**Rivyn** is an enterprise AI log intelligence and noise-suppression platform. It transforms multi-gigabyte unformatted raw system logs into structured columnar binary storage (**Apache Parquet**), uncovers rare behavioral shifts using **Multi-Tier AI Anomaly Detection**, and clusters alert floods into root-cause incident tickets, measured at **88% to 99.9% alert noise reduction** across heterogeneous production datasets.

---

## Key Interfaces

Rivyn provides a dual-interface experience:

1. **Product Marketing & Commercial Website (`/` or `/product`):**
   - High-converting B2B SaaS landing page designed to showcase the platform to enterprise customers and evaluators.
   - **Interactive ROI & Cost Savings Calculator**: Real-time modeling of monthly cloud storage savings ($) and SRE triage hours reclaimed based on daily log volume and team size.
   - **Interactive 4-Tab Product Tour**: Live simulations of the Incident Board, Grounded AI Copilot, Temporal Anomaly Timeline, and Vectorized Parquet Explorer.
   - **Full Commercial Pricing & Enterprise Security**: Community Core, Pro Team, and Air-Gapped Enterprise plans.

2. **Operational Tool Console (`/app` or `/console`):**
   - Live Incident Board prioritizing correlated incidents with grounded confidence scores and step-by-step remediation checklists.
   - Interactive Log Explorer with zero-copy vectorized filtering and Drain template IDs.
   - Grounded Natural-Language AI Copilot citing exact log lines (`[Line <id> @ <timestamp>]`).
   - Interactive file upload and bounded bulk streaming importer.
   - Seamless one-click return link (`← Product Overview`) to the product website.

---

## Architecture: Parse & Store Once, Detect & Query at Binary Speed

```
 RAW LOG INGESTION (Syslog, OpenStack, HDFS, Spark, Custom)
        │
        ▼
 ┌─────────────────────────────────────────────────────────┐
 │ 1. Single-Pass Regex Drain3 Tree Parser                 │
 │    • Dynamic regex-masked parameter extraction          │
 │    • Semantic template mining (6k – 13k+ lines/sec)     │
 │    • Automated PII & credential scrubbing               │
 └─────────────────────────────────────────────────────────┘
        │
        ▼
 ┌─────────────────────────────────────────────────────────┐
 │ 2. Columnar Binary Engine (Apache Parquet + Snappy)     │
 │    • Schema: {timestamp, template_id, params, level...} │
 │    • 60% – 89.3% storage reduction vs raw text          │
 │    • Zero-copy SIMD columnar pushdown scans             │
 └─────────────────────────────────────────────────────────┘
        │
        ▼
 ┌─────────────────────────────────────────────────────────┐
 │ 3. Multi-Tier AI Anomaly Detection Engine               │
 │    • Tier 1: Statistical Template Rarity Lookup (<1%)   │
 │    • Tier 2: Scikit-learn Isolation Forest on Features  │
 │    • Tier 3: Markov Sequence Transition Mining          │
 └─────────────────────────────────────────────────────────┘
        │
        ▼
 ┌─────────────────────────────────────────────────────────┐
 │ 4. Temporal & Topological Incident Correlator           │
 │    • Sliding time-window correlation (Δt ≤ 60s/120s)    │
 │    • Topological entity graph co-occurrence             │
 │    • 88% – 99.9% measured alert noise reduction         │
 └─────────────────────────────────────────────────────────┘
        │
        ▼
 ┌─────────────────────────────────────────────────────────┐
 │ 5. Grounded Copilot & Interactive Incident Board        │
 │    • Dense sentence vector index (all-MiniLM-L6-v2)     │
 │    • Root-cause synthesis with exact line citations     │
 │    • 100% offline deterministic rule-based fallback     │
 └─────────────────────────────────────────────────────────┘
```

---

## Production Benchmark Results (2.7M+ Lines Across 7 LogHub Datasets)

Evaluated across **all 7 heterogeneous LogHub production datasets** (Total: **2,701,198 lines**):

| Metric | Linux | OpenStack | ZooKeeper | Hadoop | Spark | BGL (Supercomputer) | HDFS |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **System Category** | OS / Syslog | Cloud IaaS | Coordination | Big Data YARN | Analytics Engine | 131k-Core HPC Cluster | Distributed Storage |
| **Lines Processed** | **25,567** | **207,820** | **74,380** | **393,431** | **500,000** | **500,000** | **1,000,000** |
| **Detected Dialect** | `syslog` | `openstack` | `zookeeper` | `hadoop` | `spark` | `bgl` | `hdfs` |
| **Templates Discovered** | 452 | 122 | 89 | 1,712 | 720 | 132 | 36 |
| **Drain Parse Speed** | **11,520 lines/s** | **6,143 lines/s** | **12,601 lines/s** | **13,372 lines/s** | **12,223 lines/s** | **9,190 lines/s** | **9,984 lines/s** |
| **Anomalies Flagged** | 15,361 | 5,379 | 53,972 | 166,780 | 103,995 | 274,030 | 94,523 |
| **Correlated Incidents** | 1,811 | 137 | 437 | 5,767 | 2,153 | 530 | 24 |
| **Alert Noise Reduction** | **88.21%** | **97.45%** | **99.19%** | **96.54%** | **97.93%** | **99.81%** | **99.90%** |
| **Triage Velocity Speedup** | **105.9x** | **391.8x** | **1,522.2x** | **359.6x** | **592.4x** | **5,888.2x** | **9,502.3x** |
| **Raw Text Size** | 2.21 MB | 58.40 MB | 9.79 MB | 45.40 MB | 51.35 MB | 64.91 MB | 132.35 MB |
| **Parquet Binary Size** | **0.75 MB** | **22.62 MB** | **1.15 MB** | **8.11 MB** | **11.55 MB** | **6.94 MB** | **53.82 MB** |
| **Storage Saved (%)** | **66.25%** | **61.27%** | **88.22%** | **82.13%** | **77.50%** | **89.30%** | **59.33%** |
| **Storage Reduction** | **3.0x** | **2.6x** | **8.5x** | **5.6x** | **4.4x** | **9.3x** | **2.5x** |

*All benchmark results are automatically reproducible via `python scripts/benchmark_all_datasets.py` and stored in `data/benchmark_all_datasets.json`.*

---

## Ingestion Modes: Interactive & Bounded Bulk Streaming

Rivyn supports two distinct ingestion architectures:

1. **Interactive In-Memory Ingestion:**
   - Designed for live interactive testing and uploads up to ~2M lines.
   - Real-time Drain template clustering, Isolation Forest feature training, and grounded LLM incident synthesis.
2. **Bounded-Memory Bulk Streaming (up to 26+ GiB):**
   - Disk-first streaming processor (`backend/ingestion/streaming.py`).
   - Parses bounded chunks and appends compressed Parquet row groups under `data/streaming/<job-id>/`.
   - Never builds a multi-gigabyte log list in application RAM, preventing Out-Of-Memory (OOM) crashes on large files.

---

## Engineering Talent & Architecture Guides

Detailed documentation for technical onboarding, candidates, and architects:

* 📄 **[Rivyn Product & Engineering Talent Guide (PDF)](docs/Rivyn_Product_Engineering_Guide.pdf)** — 5-page publication whitepaper detailing the origin story, 5-stage architecture, LogHub benchmarks, 2026–2027 roadmap, and engineering culture.
* 📝 **[LaTeX Source](docs/Rivyn_Product_Engineering_Guide.tex)** — Full LaTeX document compilable with `python docs/compile_guide_pdf.py`.
* 💼 **[Internshala Job Postings (Word Document)](docs/Rivyn_Internshala_Job_Postings.docx)** — Complete recruitment postings for Bachelor's student interns (UI/UX Developer and Core Systems/Python Developer).

---

## Quickstart Guide

### 1. Prerequisites
- Python 3.10+ (tested on Python 3.10 through 3.14)
- Git

### 2. Installation
```bash
git clone git@github.com:rivyn-labs/rivyn.git
cd rivyn

python -m venv .venv
# Windows:
.venv\Scripts\activate
# Linux/macOS:
source .venv/bin/activate

pip install -r requirements.txt
```

### 3. Run the Application
```bash
python -m uvicorn backend.app:app --host 127.0.0.1 --port 8000 --reload
```
Open **`http://localhost:8000`** in your browser:
- **`http://localhost:8000/`**: View the **Product Marketing Website** (ROI calculator, benchmarks, feature tours).
- **`http://localhost:8000/app`**: Launch the **Live Tool Console** (ingest logs, explore Drain templates, query the AI Copilot).

### 4. Run Automated Tests
```bash
python -m pytest tests/ -v
```

---

## REST API Specification

| Method | Endpoint | Description |
| :--- | :--- | :--- |
| `GET` | `/` | Product Marketing Website (`frontend/marketing.html`) |
| `GET` | `/app` | Operational Tool Console (`frontend/index.html`) |
| `GET` | `/health` | Application health and status check |
| `GET` | `/api/datasets` | List available authoritative datasets |
| `POST` | `/api/ingest/sample` | Ingest and analyze a dataset from disk |
| `POST` | `/api/ingest/upload` | Upload and analyze a custom raw log file |
| `GET` | `/api/ingest/jobs/{job_id}` | Poll background ingestion job status and progress |
| `GET` | `/api/analysis/overview` | Active dataset KPIs, templates, and noise reduction stats |
| `GET` | `/api/analysis/incidents` | Correlated incident reports with root-cause summaries |
| `GET` | `/api/analysis/logs` | Searchable, paginated log stream |
| `GET` | `/api/analysis/timeline` | Incident distribution across temporal buckets |
| `GET` | `/api/storage/binary-stats`| Parquet binary size, compression ratio, and scan throughput |
| `POST` | `/api/investigate/query` | Grounded natural language Q&A with line citations |
| `GET` | `/api/metrics/benchmark` | Run cross-dataset evaluation benchmark |

---

## Continued Development

All active updates, contributions, and discussions are now hosted at:  
👉 **[https://github.com/rivyn-labs/rivyn](https://github.com/rivyn-labs/rivyn)**

---

## License

This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.
