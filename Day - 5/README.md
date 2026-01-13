# Day 5 – Delta Lake Advanced 🚀

This repository documents **Day 5** of the **14 Days AI Challenge** by Indian Data Club, focused on **advanced Delta Lake concepts** used in real-world data engineering pipelines.

The goal of this day was to understand how Delta Lake handles **changing data, performance optimization, and storage cleanup** in production systems.

---

## 📌 What I Learned

### 1️⃣ Time Travel (Version History)

Delta Lake maintains a transaction log that allows querying older versions of a table.

**Why it matters:**

* Debugging incorrect data
* Comparing metrics before and after updates
* Auditing changes

Example:

```sql
DESCRIBE HISTORY delta.`/delta/events`;

SELECT *
FROM delta.`/delta/events`
VERSION AS OF 2;
```

---

### 2️⃣ MERGE Operations (Upserts)

Event-based data often arrives late or changes over time.

**Problem:**

* Duplicate rows when inserting incremental data

**Solution:**
Use `MERGE` to update existing records and insert new ones.

Example:

```python
from delta.tables import DeltaTable

deltaTable = DeltaTable.forPath(spark, "/delta/events")

updates = spark.read.csv(
    "/path/to/new_data.csv",
    header=True,
    inferSchema=True
)

deltaTable.alias("t").merge(
    updates.alias("s"),
    "t.user_session = s.user_session AND t.event_time = s.event_time"
).whenMatchedUpdateAll() \
 .whenNotMatchedInsertAll() \
 .execute()
```

---

### 3️⃣ OPTIMIZE & ZORDER (Performance Optimization)

As Delta tables grow, small files and poor data layout slow down queries.

**OPTIMIZE** compacts small files.
**ZORDER** organizes data based on frequently filtered columns.

Example:

```sql
OPTIMIZE events_table
ZORDER BY (event_type, user_id);
```

**Result:**

* Faster queries
* Reduced I/O
* Better performance without extra compute

---

### 4️⃣ VACUUM (Storage Cleanup)

Delta Lake keeps old files to support time travel, but storage must be managed.

Example:

```sql
VACUUM events_table RETAIN 168 HOURS;
```

This:

* Removes unused files older than 7 days
* Keeps recent versions safe for rollback

---

## 🛠️ Tasks Completed

* Implemented incremental MERGE for event data
* Queried historical versions using Time Travel
* Optimized Delta tables using OPTIMIZE & ZORDER
* Cleaned old files using VACUUM

---

## 📊 Dataset Used

* Event-based e-commerce data (views, carts, purchases)
* Incremental ingestion pattern
* Session-based updates

---

## 🎯 Key Takeaway

Delta Lake is not just a storage format.

It provides:

* Reliability through ACID transactions
* Flexibility through MERGE and Time Travel
* Performance through OPTIMIZE and ZORDER
* Cost control through VACUUM

This is how modern **Lakehouse architectures** stay production-ready.

---

## 🔗 References

* Delta Lake Time Travel – Databricks Blog
* Delta MERGE Documentation
* OPTIMIZE & ZORDER Best Practices
* VACUUM Guidelines

---

## 🏁 Challenge Progress

✅ Day 5 completed as part of the **14 Days AI Challenge**

Sharing my learning publicly to build consistency and real-world understanding.

#DatabricksWithIDC #DeltaLake #DataEngineering #LearningInPublic
