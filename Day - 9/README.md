# Day 09 – SQL Analytics & Dashboards 📊

Day 9 focuses on **turning data into business insights**.
After building pipelines and governance, this day is about **making data usable for analysts, managers, and decision-makers**.

---

## 🎯 Objective

Learn how to:

* Query curated (Gold) data using SQL
* Use SQL Warehouses for fast analytics
* Build interactive dashboards
* Share insights through visualizations

This is where data engineering meets **business impact**.

---

## 🧠 Concepts Covered

### 1. SQL Warehouse

A **SQL Warehouse** is a compute layer optimized for:

* SQL queries
* Dashboards
* Concurrent users

**Why it matters:**

* Faster query performance
* Stable dashboards
* Separation of analytics from ETL workloads

**Real-world analogy:**

* Spark clusters = data factories
* SQL warehouses = reporting engines

---

### 2. Analytical SQL Queries

Instead of simple selects, analytical SQL answers business questions such as:

* How is revenue changing over time?
* Which products perform best?
* Where do users drop off in the funnel?

Common techniques used:

* Aggregations (`SUM`, `COUNT`, `AVG`)
* Grouping by time (daily / monthly trends)
* Conditional logic for funnels

---

### 3. Dashboard Creation

Dashboards were built using SQL query results and visualized as:

* Line charts (revenue trends)
* Bar charts (top products)
* Funnel charts (user journey)

Dashboards help **non-technical users** understand data without writing SQL.

---

### 4. Filters & Interactivity

Dashboards include filters such as:

* Date range
* Product
* Category

This allows users to explore data dynamically without modifying queries.

---

### 5. Scheduled Refresh

Dashboards can be configured to refresh automatically:

* Hourly
* Daily
* Weekly

This ensures insights are always up to date without manual execution.

---

## 🛠️ Tasks Completed

* Created a SQL Warehouse
* Wrote analytical SQL queries
* Built dashboards on top of Gold tables
* Added filters for user interaction
* Scheduled automatic dashboard refresh

---

## 🎯 Key Takeaway

> Data pipelines build the foundation.
> **Dashboards deliver the value.**

This day highlights how data engineering supports real business decisions.

---

## 🧑‍💼 Business Perspective

Dashboards enable:

* Faster decision-making
* Clear visibility into performance
* Reduced dependency on engineers for insights

They are a critical layer in modern data platforms.

---

## 🙏 Acknowledgements

* Indian Data Club
* Codebasics
* Sponsored by Databricks
