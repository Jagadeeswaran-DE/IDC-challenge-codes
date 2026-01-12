# Day 04 – Delta Lake Introduction 🧊

Part of the **Databricks 14 Days AI Challenge** by **Indian Data Club**

On Day 04, the focus was on understanding **why Delta Lake exists** and how it upgrades a traditional data lake into a **reliable, production-ready system**.

This day connects theory with hands-on practice using real e-commerce data.

---

## 🧠 What This Day Is About

In real-world data pipelines:
- Multiple jobs write data at the same time
- Bad data can silently break dashboards
- Duplicate records slowly corrupt analytics

Delta Lake solves these problems.

---

## 📚 Concepts Covered

### 1. What is Delta Lake?
Delta Lake is an open table format built on top of Parquet that adds:
- Transaction logs
- Data versioning
- Reliability guarantees

Think of it as:
> **Parquet + database-like behavior**

---

### 2. ACID Transactions
Delta Lake supports full ACID transactions:
- **Atomicity** – all or nothing writes
- **Consistency** – schema rules are enforced
- **Isolation** – concurrent jobs don’t clash
- **Durability** – committed data is safe

This makes it suitable for production pipelines.

---

### 3. Schema Enforcement
Delta Lake blocks data that doesn’t match the table schema.

If a column expects an integer and receives a string:
- ❌ Write fails
- ✅ Data quality is protected

No silent failures.

---

### 4. Delta Lake vs Parquet

| Feature | Parquet | Delta Lake |
|------|--------|-----------|
| ACID Transactions | ❌ | ✅ |
| Schema Enforcement | ❌ | ✅ |
| Schema Evolution | ❌ | ✅ |
| Time Travel | ❌ | ✅ |
| Concurrent Writes | ❌ | ✅ |

---

## 🛠️ Hands-On Tasks Completed

### 1. Convert CSV to Delta Format
Raw e-commerce CSV files were read using Spark and written as Delta tables.

```python
events.write.format("delta") \
    .mode("overwrite") \
    .save("/delta/events")
