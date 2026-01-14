# 🏗️ Medallion Architecture using Databricks (Day 6)

This project demonstrates the **Medallion Architecture (Bronze → Silver → Gold)** pattern using **Apache Spark and Delta Lake on Databricks**.

It shows how raw ecommerce event data is ingested, cleaned, validated, and finally transformed into business-ready insights.

Built as part of the **14 Days AI Challenge – Day 6** by **Indian Data Club × Codebasics**, sponsored by **Databricks**.

---

## 📌 What is Medallion Architecture?

Medallion Architecture is a **layered data design approach** that organizes data based on its level of refinement and usability.

Each layer has a clear responsibility:

* **Bronze** → Raw, immutable data
* **Silver** → Cleaned, validated, enriched data
* **Gold** → Aggregated, business-level metrics

This approach improves **data quality, scalability, and maintainability**.

---

## 🧠 Architecture Flow

```
Raw Source Data
      ↓
Bronze Layer (Raw Ingestion)
      ↓
Silver Layer (Cleaning & Validation)
      ↓
Gold Layer (Business Aggregates)
```

---

## 🟤 Bronze Layer – Raw Ingestion

### Objective

* Preserve raw data exactly as received
* Enable reprocessing and debugging
* Maintain data lineage

### What happens in this layer?

* Raw CSV ecommerce data is read using Spark
* Schema is inferred automatically
* An `ingestion_time` column is added
* Data is stored in **Delta format**

### Outcome

* No data loss
* No transformations
* Acts as the **single source of truth**

---

## ⚪ Silver Layer – Cleaning & Validation

### Objective

* Improve data quality
* Prepare data for analytics and aggregation

### Transformations Applied

* Filtered invalid prices (outside expected range)
* Removed duplicate records using `user_session` and `event_time`
* Handled null values
* Added derived columns:

  * `event_date` from event timestamp
  * `price_tier` (budget, affordable, expensive, luxury)

### Outcome

* Clean, reliable, analytics-ready data
* Consistent schema and validated values

---

## 🟡 Gold Layer – Business Aggregates

### Objective

* Convert cleaned data into business insights
* Support dashboards, reporting, and analytics

### Aggregations Performed

* Total product views
* Total product purchases
* Total revenue per product
* Conversion rate calculation

### Example Business Questions Answered

* Which products get the most views?
* Which products generate the highest revenue?
* What is the conversion rate per product?

### Outcome

* Business-ready datasets
* Optimized for consumption by BI tools and stakeholders

---

## 🚀 Why Use Medallion Architecture?

* Clear separation of concerns between layers
* Easy debugging and reprocessing
* Scales well with growing data volume
* Industry-standard pattern in modern data platforms

**Delta Lake ensures reliability.**
**Medallion Architecture ensures structure.**

---

## 🛠️ Technology Stack

* Apache Spark (PySpark)
* Delta Lake
* Databricks
* Python

---

## 📂 Logical Data Organization

```
/bronze   → Raw ingested data
/silver   → Cleaned and validated data
/gold     → Aggregated business data
```

---

## 📈 Future Enhancements

* Incremental data processing
* Performance optimization (partitioning, Z-ORDER)
* Data quality checks
* Workflow orchestration using Airflow or Databricks Jobs

---

## 🙌 Acknowledgements

* **Indian Data Club × Codebasics**
* Sponsored by **Databricks**

---

⭐ If this repository helped you understand Medallion Architecture, consider starring it!
