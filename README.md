# Day 03 – PySpark Transformations Deep Dive 🚀

Part of the **Databricks 14 Days AI Challenge** by Indian Data Club.

This day focused on going beyond basic Spark syntax and working with PySpark the way it’s actually used in real data engineering pipelines.

---

## 🧠 What This Day Was About

The goal of Day 3 was to take a **real e-commerce clickstream dataset** and transform it into something analytics- and business-ready using PySpark.

Instead of toy examples, the work was done on a **full-scale dataset** with real-world complexity:
- Multiple event types
- Missing values
- Repeated records
- User and product behavior over time

---

## 📊 Dataset Overview

The dataset represents user interaction events in an e-commerce platform.

**Schema highlights:**
- `event_time` – Timestamp of the event  
- `event_type` – view / cart / purchase  
- `product_id` – Product identifier  
- `category_id`, `category_code` – Product categorization  
- `brand` – Product brand  
- `price` – Product price  
- `user_id` – User identifier  
- `user_session` – Session identifier  

This is a classic **event-level fact table** used in analytics engineering.

---

## 🛠️ What I Implemented

### 1️⃣ Data Loading
- Loaded the full CSV dataset into Databricks using PySpark
- Verified schema and data types
- Worked directly on large-scale data (not samples)

---

### 2️⃣ Event Segmentation
Split the raw events into logical subsets:
- Views
- Carts
- Purchases

This made downstream joins and funnel analysis much cleaner.

---

### 3️⃣ Joins (Core Focus 🔥)

Implemented **all major join types** using real business logic:

- **INNER JOIN**  
  Used to find strict matches (e.g., users who both viewed and purchased the same product)

- **LEFT JOIN**  
  Preserved all events while enriching with related data

- **RIGHT JOIN**  
  Identified entities that exist but have missing activity

- **FULL OUTER JOIN**  
  Used for data audits and reconciliation between datasets

Also implemented:
- Conditional joins
- Self joins (event-to-event comparisons)

---

### 4️⃣ Window Functions
Used Spark window functions to move from row-level data to sequence-based insights.

Examples:
- Ranking user events by time
- Tracking user activity over sessions
- Calculating running metrics without collapsing rows

This is a key concept for analytics and behavioral analysis.

---

### 5️⃣ Derived Metrics & Features
Created analytics-ready outputs such as:
- View → Purchase conversion counts
- Category-level performance metrics
- Aggregated event statistics

Turned raw logs into **decision-ready data**.

---

## 🚀 Tech Stack

- Apache Spark
- PySpark
- Databricks (Community Edition)
- Python

---

## 📌 Key Learnings

- Joins are not just SQL operations — they represent business questions
- Window functions are essential for behavioral analytics
- Event data needs structure before it becomes useful
- PySpark transformations scale only when logic is clean

---

## 🔗 Repository Structure

