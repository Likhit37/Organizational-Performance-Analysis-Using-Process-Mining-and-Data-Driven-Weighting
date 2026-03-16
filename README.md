# Data-Driven Workplace Performance Measurement Using Process Mining and Machine Learning

> Analysis of Multi-Entity Purchase Order Processes

---

## 📋 Overview

This project addresses the limitations of traditional workplace monitoring by building a comprehensive **Performance Analysis Model** for complex business processes involving multiple interrelated entities — users, vendors, and purchase orders.

We leverage real-world industrial event data from a multinational company to analyze workflows, detect inefficiencies, and measure performance KPIs across interconnected business entities using **Process Mining** and **Machine Learning**.

---

## 🔍 Problem Statement

Traditional workplace monitoring tools fall short when dealing with multi-dimensional business processes. They cannot effectively:
- Query multi-entity relationships across sequential logs
- Perform temporal sequence querying in relational databases
- Combine structural and temporal analysis in a unified model

**Our goal:** Extend the graph-based event data model (from the base paper) beyond descriptive modeling — implementing performance analysis using ML for anomaly detection, efficiency measurement, and diagnostic insights.

---

## 📦 Dataset

**Source:** Multinational Company (Netherlands) — BPI Challenge 2015 (BPIC15)  
Purchase order handling processes across ~60 subsidiaries.

> 📥 **The full dataset (raw + processed) is publicly available on Kaggle:**  
> [BPIC15 Event Log Dataset (Processed and Raw)](https://www.kaggle.com/datasets/likhitsagar/bpic15-event-log-dataset-processed-and-raw)

| Metric | Value |
|---|---|
| Cases (Items) | 251,734 |
| Purchase Documents | 76,349 |
| Event Nodes | 1.6M+ |
| Resources | 627 |
| Activity Types | 42 |

### Data Formats Available
| File | Description |
|---|---|
| `Neo4j.dump` | Graph database dump for direct Neo4j import |
| `GraphML` (compressed) | For graph analysis tools (NetworkX, etc.) |
| Processed CSVs | Pre-cleaned tabular event logs ready for ML |
| Raw XES / logs | Original unprocessed BPIC15 event logs |

### Graph-Based Data Model
The dataset is modeled as a **labeled property graph** with:
- **Event Nodes** — Activity name & timestamp
- **Entity Nodes** — Items, vendors, users
- **Class Nodes** — Activity types (42 unique)
- **Log Nodes** — Event aggregation across entities

---

## 🏗️ Methodology

```
Data Preprocessing → Process Mining → ML Analysis → Visualization
```

### 1. Data Preprocessing
- Loading and parsing Neo4j / GraphML data
- Entity resolution and graph construction
- Feature engineering for downstream tasks

### 2. Process Mining
- Workflow pattern discovery
- Bottleneck identification
- Cycle time analysis
- Resource utilization metrics

### 3. Machine Learning Analysis
- **Anomaly detection** — Identify abnormal process executions
- **Performance clustering** — Group similar process behaviors
- **Execution classification** — Label process runs by performance tier
- **Pattern recognition** — Surface recurring workflow patterns

### 4. Visualization & Dashboards
- Interactive process flow visualizations
- KPI measurement dashboard for managers
- Anomaly highlighting and drill-down views

---

## 📐 Foundation & Base Paper

This project extends the work from:

> **"Graph-Based Data Model for Multi-Dimensional Event Data"**  
> arXiv: [2005.14552](https://arxiv.org/abs/2005.14552)

**Key contributions from the base paper:**
- Unified graph model for multi-entity event data
- Generic queries for synchronous & asynchronous interactions
- Efficient Cypher query execution framework
- Demonstrated descriptive model creation

**Our extension** builds on top of this foundation by adding performance analysis, ML-driven anomaly detection, and actionable diagnostic insights.

---

## 🎯 Expected Deliverables

- ✅ End-to-end **Performance Analysis Pipeline**
- ✅ **Process visualizations** (workflow maps, bottleneck graphs)
- ✅ **Anomaly detection** module for abnormal process executions
- ✅ **KPI dashboard** for business managers (cycle time, resource efficiency)

---

## 🛠️ Tech Stack

| Layer | Tools |
|---|---|
| Graph Database | Neo4j, Cypher |
| Graph Analysis | GraphML, NetworkX |
| Process Mining | PM4Py (or equivalent) |
| Machine Learning | scikit-learn, Python |
| Visualization | Plotly / Dash / similar |

---

## 🚀 Getting Started

### Prerequisites
- Python 3.8+
- Neo4j Desktop or AuraDB (for graph-based workflows)
- Kaggle account (to download the dataset)
- Required Python packages (see `requirements.txt`)

### 1. Clone the Repository
```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
pip install -r requirements.txt
```

### 2. Download the Dataset from Kaggle

**Option A — Kaggle Web UI:**  
Visit the dataset page and click **Download**:  
🔗 https://www.kaggle.com/datasets/likhitsagar/bpic15-event-log-dataset-processed-and-raw

**Option B — Kaggle API (recommended):**
```bash
# Install the Kaggle CLI if you haven't already
pip install kaggle

# Make sure your API token is set up at ~/.kaggle/kaggle.json
# Download the dataset into the data/ folder
kaggle datasets download -d likhitsagar/bpic15-event-log-dataset-processed-and-raw -p data/ --unzip
```

### 3. Load the Graph Database (Neo4j)
```bash
# Import the Neo4j dump
neo4j-admin database load --from=data/neo4j.dump --database=neo4j

# Start Neo4j and open the browser at http://localhost:7474
```

### 4. Run the Pipeline
```bash
# Preprocessing
python src/preprocessing/preprocess.py

# Process Mining
python src/process_mining/analyze.py

# ML Analysis
python src/ml/anomaly_detection.py

# Launch Dashboard
python src/visualization/dashboard.py
```

---

## 📁 Project Structure

```
├── data/                  # Raw dataset files (Neo4j dump, GraphML)
├── notebooks/             # Exploratory analysis & experiments
├── src/
│   ├── preprocessing/     # Data loading and graph construction
│   ├── process_mining/    # Workflow discovery and bottleneck analysis
│   ├── ml/                # Anomaly detection and clustering models
│   └── visualization/     # Dashboard and plot generation
├── reports/               # Presentations and documentation
└── README.md
```


## 📄 License

This project is for academic and research purposes.  
The dataset is publicly hosted on Kaggle and is subject to the terms of the original BPIC15 data provider. Please cite appropriately if used in research.
