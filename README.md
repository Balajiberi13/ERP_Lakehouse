# Multi-ERP Enterprise Data Lakehouse on Azure Databricks
![Databricks](https://img.shields.io/badge/Powered%20by-Databricks-Red?logo=databricks&logoColor=white)
## 📌 Project Overview
In modern manufacturing enterprises, data is fragmented across multiple disparate ERP (Enterprise Resource Planning) systems. This project implements a unified, scalable **Data Lakehouse Architecture** using **Azure Databricks** and **Delta Lake** to ingest, process, and model data from multiple manufacturing ERP systems. 

The lakehouse consolidates complex operational data into standardized, high-performance business entities—such as **Sales, Invoices, Purchases, and Inventory**—enabling robust downstream analytics, historical tracking, and business intelligence.

---

## 🏗️ Architecture & Data Flow
The project follows a modular Medallion Architecture (Bronze -> Silver -> Gold) to ensure data quality, reliability, and transactional integrity.

```text
[Multi-ERP Sources] ──(API / SQL Extract)──> [ADLS Gen2 (Raw)] 
                                                    │
                                             (Bronze Layer)
                                                    ▼
                                       [Delta Tables (Append Only)]
                                                    │
                                        (Silver Layer: Cleansed & Mapped)
                                                    ▼
                                    [Delta Tables (Enforced Schemas)]
                                                    │
                                         (Gold Layer: Business Logic)
                                                    ▼
                                 [Optimized Stored Procedures / Views]
                                   (Sales, Invoice, Purchase, Inventory)
