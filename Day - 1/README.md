📘 PHASE 1: FOUNDATION (Days 1–4)

📘 Day 01 – Platform Setup & First Steps

Part of Databricks 14 Days AI Challenge by Indian Data Club in collaboration with Databricks & Codebasics 🚀

🧠 Overview

Day 1 was focused on setting the foundation. The goal wasn’t writing complex Spark code, but understanding why Databricks exists, how it differs from traditional tools, and getting comfortable with the platform.

This day was about environment setup, platform navigation, and running the very first PySpark commands.

📌 Topics Covered

Why Databricks over Pandas & Hadoop

Lakehouse Architecture basics

Databricks Workspace structure

Real-world industry use cases:

Netflix

Shell

Comcast

🛠️ Hands-on Tasks Completed

Created Databricks Community Edition account

Explored Databricks UI:

Workspace

Compute

Data Explorer

Created the first notebook

Ran basic PySpark commands to validate setup

🧪 Sample Operations

data = [
    ("Junior data engineer", 0.5),
    ("Data Engineer Intern", 1.0),
    ("Engineering student", 4.0)
]

exp_df = spark.createDataFrame(data,["job_title", "experience"])

exp_df.show()

exp_df.filter(exp_df.experience >= 1.0).show()


🎯 Key Takeaways

Databricks simplifies big data workflows compared to Pandas & Hadoop

Lakehouse combines data lakes + data warehouses

Understanding the platform is as important as writing code

Environment setup is the first real win

🙏 Credits

Huge thanks to:

Databricks

Indian Data Club

Codebasics

for designing a challenge that values hands-on learning + consistency.