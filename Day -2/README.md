# 📘 Day 02 – Apache Spark Fundamentals

Part of **Databricks 14 Days AI Challenge** by **Indian Data Club** in collaboration with **Databricks** & **Codebasics** 🚀

---

## 🧠 Overview

Day 2 was all about understanding **how Spark actually works**—not just running code, but knowing *why* and *when* Spark executes things.

This day focused on Spark internals, DataFrames, lazy execution, and hands-on data analysis using **PySpark** and **Spark SQL** on Databricks.

---

## 📌 Topics Covered

* Spark Architecture

  * Driver
  * Executors
  * DAG (Directed Acyclic Graph)
* DataFrames vs RDDs
* Lazy Evaluation (Transformations vs Actions)
* Databricks Notebook Magic Commands

  * `%python`
  * `%sql`
  * `%fs`

---

## 🛠️ Hands-on Tasks Completed

* Uploaded real-world **e-commerce CSV data** to Databricks Volumes
* Explored files using `%fs`
* Loaded CSV into Spark DataFrame with schema inference
* Performed core DataFrame operations:

  * `select()`
  * `filter()`
  * `groupBy()`
  * `orderBy()`
* Identified:

  * High-priced products
  * Top brands by event count
* Ran analytics using **both PySpark and Spark SQL**
* Exported and documented results

---

## 🧪 Sample Operations

```python
# Read CSV
ecom_oct_df = spark.read.csv(
    "/Volumes/idc/idc_kaggle/ecom_data/2019-Oct.csv",
    header=True,
    inferSchema=True
)

# Basic transformations
ecom_oct_df.select("event_type", "brand", "price").show()

ecom_oct_df.filter("price > 1000").count()

ecom_oct_df.groupBy("brand").count().orderBy("count", ascending=False).limit(5)
```

```sql
-- Create temp view
CREATE OR REPLACE TEMP VIEW ecom_oct
USING csv
OPTIONS (
  path '/Volumes/idc/idc_kaggle/ecom_data/2019-Oct.csv',
  header 'true',
  inferSchema 'true'
);

-- SQL analytics
SELECT brand, COUNT(*)
FROM ecom_oct
GROUP BY brand
ORDER BY COUNT(*) DESC
LIMIT 5;
```

---

## 🎯 Key Takeaways

* Spark is **lazy by design**, not slow
* Driver plans, Executors execute, DAG optimizes
* DataFrames > RDDs for most real-world use cases
* PySpark + Spark SQL together = powerful combo

---

## 🚀 What’s Next

**Day 03 – PySpark Transformations (Deep Dive)**

More transformations, more optimization, more scale 💪

---

## 🙏 Credits

Huge thanks to:

* **Databricks**
* **Indian Data Club**
* **Codebasics**

for designing a challenge that values **hands-on learning + consistency**.
