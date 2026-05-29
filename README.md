🚀 AdventureWorks 2022: Modern Data Warehouse on Azure
![alt text](https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoft-azure&logoColor=white)

![alt text](https://img.shields.io/badge/Databricks-FF3621?style=for-the-badge&logo=databricks&logoColor=white)

![alt text](https://img.shields.io/badge/Apache_Spark-E25A1C?style=for-the-badge&logo=apache-spark&logoColor=white)

![alt text](https://img.shields.io/badge/Power_BI-F2C811?style=for-the-badge&logo=power-bi&logoColor=black)
An end-to-end Modern Data Warehouse solution built on Azure Cloud, implementing Medallion Architecture to transform raw operational data from AdventureWorks 2022 (On-premise SQL Server) into actionable business insights.
🏗️ Architecture Overview
The project follows the Data Lakehouse paradigm, combining the flexibility of a Data Lake with the performance and structure of a Data Warehouse.
![alt text](https://img.shields.io/badge/Architecture-Medallion_Lakehouse-blue?style=flat-square)
Source: On-Premise Microsoft SQL Server (AdventureWorks 2022).
Ingestion: Azure Data Factory (ADF) via Self-hosted Integration Runtime (SHIR).
Storage: Azure Data Lake Storage Gen2 (ADLS Gen2).
Processing: Azure Databricks (PySpark) using the Medallion Pattern.
Serving: Azure Synapse Analytics (Serverless SQL Pool).
Visualization: Power BI Desktop & Service.
🛠️ Tech Stack & Tools
Category	Technology	Purpose
Cloud Provider	Microsoft Azure	Core Infrastructure
Orchestration	Azure Data Factory	ETL Pipelines & Workflow management
Data Lake	ADLS Gen2	Scalable storage for Bronze, Silver, Gold layers
Compute	Azure Databricks	High-performance Spark processing & Delta Lake
Data Warehouse	Azure Synapse	Serving layer via Serverless SQL views
Visualization	Power BI	Business Intelligence & KPI Dashboards
Security	Key Vault / Entra ID	Secret management & RBAC
DevOps	GitHub	Version control & CI/CD integration
💎 Data Modeling (Medallion Architecture)
🥉 Bronze Layer (Raw)
Format: Parquet
Structure: bronze/{source_system}/{table_name}/yyyy/mm/dd/
Description: Immutable historical record of source data.
🥈 Silver Layer (Cleaned)
Format: Delta Table
Processing: Schema enforcement, data type casting, handling NULLs, deduplication.
Description: Single source of truth for downstream analytics.
🥇 Gold Layer (Curated)
Format: Delta Table (Star Schema)
Model: Fact & Dimension tables (e.g., fact_sales, dim_product).
Description: Aggregated data optimized for reporting and business logic (KPIs).
🚀 Project Workflow
Phase 1: Business Analysis & Planning
Requirement Gathering: Mapped Sales, Inventory, and HR processes.
KPI Definition: Established core metrics: Net Sales, Profit Margin, YoY Growth.
Source Survey: Identified and mapped SQL Server tables to business needs.
Phase 2: Implementation & Infrastructure
Infrastructure as Code: Provisioned Azure resources with consistent naming conventions.
Connectivity: Configured SHIR to securely bridge On-Premise SQL to Azure.
Ingestion: Built dynamic ADF pipelines to copy data into the Bronze layer.
Phase 3: Transformation (Spark ETL)
Silver Logic: Standardized timestamps, cleaned string formats, and handled data quality issues.
Gold Logic: Implemented Star Schema. Created dimension tables for Products, Customers, and Territory. Built Fact tables for Sales and Transactions.
Phase 4: Serving & Visualization
Synapse Integration: Created External Tables/Views on top of Gold Delta tables.
Power BI: Built a robust data model with DAX measures and interactive dashboards.
🔐 Security & Governance
Azure Key Vault: Centralized storage for SQL connection strings and Databricks tokens. No plain-text secrets in code.
Managed Identity (MSI): Used for seamless and secure authentication between ADF, Databricks, and ADLS Gen2.
RBAC: Role-Based Access Control implemented via Microsoft Entra ID.
📐 Best Practices Applied
Naming Convention:
Resources: [service]-[project]-[env]-[region]
Storage: lowercase_snake_case
Coding Standards:
Python: PEP 8 compliant.
SQL: Comma-first formatting with capitalized keywords.
Version Control: Git Flow strategy with clear, prefix-based commit messages (e.g., [Feat], [Fix], [Docs]).
📊 Key Insights from Dashboard
Sales Performance: Real-time tracking of revenue against targets.
Customer Segmentation: Identifying high-value customers and buying patterns.
Inventory Efficiency: Monitoring stock levels and turnover rates.
📂 Project Structure
code
Bash
├── adf/                # Azure Data Factory Pipelines (JSON)
├── databricks/         # PySpark Notebooks (Bronze to Gold)
│   ├── silver/
│   └── gold/
├── sql/                # Synapse Serverless Views & DDL
├── pbi/                # Power BI Desktop Files (.pbix)
├── docs/               # Business Requirement Document (BRD) & Mapping
└── README.md
📧 Contact
[Phan Trong Qui] - [[Link LinkedIn](https://www.linkedin.com/in/tr%E1%BB%8Dng-qu%C3%AD-phan-40174a392/)] - [phanqui72@gmail.com]
Generated with ❤️ for Data Engineering Excellence.
