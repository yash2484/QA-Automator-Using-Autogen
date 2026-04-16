# QA Testing Automation Framework (AutoGen + RAG + ChromaDB)

An **autonomous, multi-agent QA testing framework** that automates the entire testing lifecycle for a **User Registration API** using:

* 🤖 Microsoft AutoGen (multi-agent orchestration)
* 🧠 RAG (Retrieval-Augmented Generation)
* 🗂️ ChromaDB (vector database)
* 🧪 Pytest (test execution)

---

## 📌 Overview

This project implements a **fully autonomous QA pipeline** powered by **4 specialized AI agents**, each responsible for a specific stage of testing:

| Agent                   | Role                                             |
| ----------------------- | ------------------------------------------------ |
| **Data Architect**      | Generates synthetic test data + builds RAG index |
| **Test Case Generator** | Creates pytest scripts using RAG                 |
| **Validator**           | Ensures correctness via multi-pass validation    |
| **Test Runner**         | Executes tests and generates reports             |

The system produces a final output:

```
workspace/test_results.csv
```

Containing per-test:

* Expected vs Actual results
* Pass/Fail status
* Failure reasons

---

## 🧠 Architecture

```
SEED_MESSAGE
    │
    ▼
data_architect ──► pipeline_runner
                        │
                        ▼
          test_case_generator ──► validator
                   ▲                │
                   │◄───────────────┘
                        (max 3 iterations)
                        │
                        ▼
                   test_runner
                        │
                        ▼
                  TESTS_COMPLETE
```

---

## ⚙️ Tech Stack

* **AutoGen** – Multi-agent orchestration
* **ChromaDB** – Vector storage for RAG
* **Sentence Transformers** – Local embeddings
* **Pytest** – Test execution
* **Pandas** – Data handling
* **OpenAI GPT-4o** – Reasoning + validation

---

## 📂 Project Structure

```
QA-Testing-Automation/
├── __main__.py
├── requirements.txt
├── .env.example
├── .gitignore
└── workspace/
    ├── chroma_db/
    ├── registration_test_data.csv
    ├── test_registration_api.py
    └── test_results.csv
```

---

## 🚀 Features

* ✅ Fully autonomous QA pipeline
* 🔁 Multi-agent collaboration with state machine routing
* 🧠 RAG-powered test generation
* 🔍 3-pass validation loop for high accuracy
* 📊 Structured CSV test reports
* 💡 Deterministic execution with signal-based control

---

## 🛠️ Setup Instructions

### 1. Prerequisites

* Python 3.10+
* Git
* OpenAI API Key

---

### 2. Clone the Repository

```bash
git clone https://github.com/yash2484/QA-Testing-Automation.git
cd QA-Testing-Automation
```

---

### 3. Create Virtual Environment

```bash
python -m venv .venv

# Activate
# Windows
.venv\Scripts\activate

# Mac/Linux
source .venv/bin/activate
```

---

### 4. Install Dependencies

```bash
pip install -r requirements.txt
```

---

### 5. Configure Environment Variables

Create a `.env` file:

```
OPENAI_API_KEY=your_api_key_here
```

---

### 6. Run the Pipeline

```bash
python __main__.py
```

---

## 🔄 Pipeline Workflow

### Step 1 — Data Architect

* Generates synthetic dataset (20 rows)
* Stores embeddings in ChromaDB

### Step 2 — Test Case Generator

* Retrieves data via RAG
* Writes pytest automation script

### Step 3 — Validator

* Validates script using:

  * Column correctness
  * Business logic
  * Coverage
  * Assertions
  * Data alignment

### Step 4 — Test Runner

* Executes tests
* Generates `test_results.csv`

---

## 📊 Output Example

| test_id | expected_status | actual_status | outcome  |
| ------- | --------------- | ------------- | -------- |
| 1       | PASS            | PASS          | MATCH    |
| 2       | FAIL            | PASS          | MISMATCH |

---

## 🔁 Validation Loop

* Max **3 iterations**
* Controlled via signal words:

  * `SCRIPT_READY`
  * `REVISION_NEEDED`
  * `SCRIPT_VALIDATED`

---

## 🧩 Key Concepts

### 🔹 RAG (Retrieval-Augmented Generation)

* Agents retrieve relevant test data from ChromaDB
* Improves accuracy of generated test cases

### 🔹 State Machine Routing

* Deterministic agent flow
* Based on signal words like:

  * `DATA_INDEXED`
  * `SCRIPT_READY`
  * `TESTS_COMPLETE`

### 🔹 Autonomous Execution

* No human input required
* Fully self-correcting system

---

## ⚠️ Troubleshooting

| Issue             | Fix                                          |
| ----------------- | -------------------------------------------- |
| Infinite loop     | Ensure `TESTS_COMPLETE` is printed correctly |
| ChromaDB error    | Delete `workspace/chroma_db/`                |
| No results in CSV | Check pytest output parsing                  |
| Module errors     | Activate `.venv` and reinstall requirements  |

---

## 📈 Why This Project Matters

This project demonstrates:

* Multi-agent AI system design
* Real-world QA automation
* RAG integration in testing
* Autonomous decision-making pipelines

---

## 🔮 Future Improvements

* API integration (real endpoints instead of mock)
* CI/CD pipeline integration (GitHub Actions)
* Dashboard for test results (Streamlit)
* Support for multiple APIs
* Advanced failure analysis using LLMs


---
