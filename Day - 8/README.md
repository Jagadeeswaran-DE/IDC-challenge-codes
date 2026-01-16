# Day 08 – Unity Catalog Governance 🔐

Day 8 focuses on **data governance** — controlling access, organization, and trust in data once pipelines are already running.

While Day 7 was about *automation*, Day 8 is about *responsibility*.

---

## 🎯 Objective

Understand how Databricks Unity Catalog helps:

* Organize data assets
* Control who can access what
* Track data lineage
* Apply enterprise-grade governance

This is a core requirement for **real-world data platforms**.

---

## 🧠 Concepts Covered

### 1. Catalog → Schema → Table Hierarchy

Unity Catalog enforces a strict 3-level hierarchy:

```
Catalog
 └── Schema
      └── Table / View
```

**Real-world analogy:**

* Catalog → Company / Business domain
* Schema → Team or data layer (Bronze, Silver, Gold)
* Table/View → Actual dataset

This structure avoids chaos and improves discoverability.

---

### 2. Managed vs External Tables

| Type     | Description                                  |
| -------- | -------------------------------------------- |
| Managed  | Databricks controls storage and lifecycle    |
| External | Databricks references data stored externally |

In this exercise:

* Existing Delta files were **registered** as tables
* No data was duplicated

---

### 3. Registering Existing Delta Tables

When Delta files already exist, Unity Catalog tables can be created on top of them:

```sql
CREATE TABLE schema.table
USING DELTA
LOCATION 'dbfs:/path/to/delta';
```

This enables governance, lineage, and SQL access without rewriting data.

---

### 4. Access Control (GRANT / REVOKE)

Unity Catalog supports fine-grained permissions:

* Table-level access
* Schema-level access
* View-based access

Examples practiced:

* Granting SELECT access on tables
* Granting ALL privileges on schemas
* Verifying permissions using `SHOW GRANTS`

> Note: In Databricks Free Edition, enforcement is limited to a single user, but governance concepts and syntax are fully valid.

---

### 5. Views for Controlled Access

Views were created to:

* Expose only required columns
* Filter sensitive data
* Provide safe access to downstream users

This is a common enterprise pattern for secure data sharing.

---

### 6. Data Lineage

Unity Catalog automatically tracks:

* Source tables
* Transformations
* Downstream dependencies

This helps answer:

> "Where did this data come from?"
> "What breaks if this changes?"

---

## 🛠️ What Was Implemented

* Created catalog and schemas
* Registered Delta tables under Unity Catalog
* Differentiated managed vs external tables
* Applied access control using GRANT
* Verified permissions with SHOW GRANTS
* Built secure views for consumption
* Queried governed objects successfully

---

## 🎯 Key Takeaway

> Pipelines move data.
> **Governance builds trust in data.**

This day marked the shift from building data systems to **operating them responsibly**.

---

## 📌 Notes on Free Edition

* Custom catalogs may be limited
* Default `main` catalog can be used
* User-level permission enforcement is restricted
* Concepts, structure, and SQL remain production-relevant

---

## 🙏 Acknowledgements

* Indian Data Club
* Codebasics
* Sponsored by Databricks


