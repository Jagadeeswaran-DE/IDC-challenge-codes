# Day 07 – Workflows & Job Orchestration 🚀

This day focuses on moving from **manual notebook execution** to **production-ready, automated data pipelines** using Databricks Jobs and Workflows.

---

## 🎯 Objective

Learn how real-world data systems are orchestrated:

* Multiple steps
* Clear execution order
* Automatic scheduling
* Failure handling

Instead of clicking **Run** manually, the goal is to let pipelines run **reliably on autopilot**.

---

## 🧠 Concepts Covered

### 1. Notebooks vs Jobs

| Notebook                       | Job                              |
| ------------------------------ | -------------------------------- |
| Used for development & testing | Used for automation & production |
| Manually executed              | Runs on schedule or trigger      |
| Single unit of work            | Orchestrates multiple tasks      |

> Notebook = writing a recipe
> Job = running a kitchen every day

---

### 2. Multi-Task Workflows

A workflow connects multiple tasks (notebooks) with **dependencies**.

Implemented pipeline:

```
Bronze  →  Silver  →  Gold
```

Each task:

* Runs only after the previous task succeeds
* Stops downstream execution if it fails

---

### 3. Parameters (Widgets)

Widgets allow notebooks to accept **runtime inputs**, making them reusable.

Examples of parameters:

* Source file path
* Layer name (bronze / silver / gold)

This avoids hardcoding values and supports different executions using the same notebook.

---

### 4. Scheduling & Error Handling

* Jobs can be scheduled to run at a fixed time (daily, hourly, etc.)
* Failures are visible in the Job UI
* Downstream tasks are automatically blocked on failure

This ensures:

* Reliability
* Observability
* Production readiness

---

## 🛠️ What Was Built

### Parameterized Notebook

* Widgets created for input control
* Same notebook used for multiple layers

### Bronze Layer

* Ingest raw data
* Add ingestion timestamp
* Store data in Delta format

### Silver Layer

* Filter invalid records
* Remove duplicates
* Enrich data with derived columns

### Gold Layer

* Aggregate business metrics
* Generate analytics-ready tables

### Databricks Job

* Multi-task workflow
* Dependencies: Bronze → Silver → Gold
* Scheduled execution
* Monitoring via graph view

---

## 🎯 Key Takeaway

> Writing Spark code is only the first step.
> Designing **reliable, automated workflows** is what makes data engineering production-ready.

This day marked the shift from:

**"I can run notebooks"**
➡️ **"I can build and operate pipelines"**

---

## 📌 Next Up

**Day 08 – Unity Catalog & Governance**
Managing access, security, and data governance at scale.

---

🙏 Acknowledgements

* Indian Data Club
* Codebasics
* Sponsored by Databricks


