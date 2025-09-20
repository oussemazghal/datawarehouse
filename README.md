# 📊 Medical Data Warehouse Project

[![Python](https://img.shields.io/badge/Made%20with-Python-blue)](https://www.python.org/) [![MySQL](https://img.shields.io/badge/Database-MySQL-orange)](https://www.mysql.com/) [![Power BI](https://img.shields.io/badge/BI-Power%20BI-yellow)](https://powerbi.microsoft.com/)

---

## 📌 Introduction
This project aims to design and implement a **medical data warehouse**, integrating heterogeneous sources (Access, CSV, JSON) to facilitate data analysis and decision-making.

The project covers all stages, from **star schema design**, **ETL processing**, **fact and dimension table creation**, **OLAP cube modeling**, to **data analysis using Power BI and Excel**.

---

## 📚 Table of Contents
- [1. Project Context & Objectives](#1-project-context--objectives)
- [2. Step 0: Data Warehouse Design](#2-step-0-data-warehouse-design)
- [3. Step 1: Data Filtering & Extraction](#3-step-1-data-filtering--extraction)
- [4. Step 2: Dimensions Extraction & MySQL Loading](#4-step-2-dimensions-extraction--mysql-loading)
- [5. Step 3: Fact Table Creation](#5-step-3-fact-table-creation)
- [6. Step 4: OLAP Cube Creation](#6-step-4-olap-cube-creation)
- [7. Step 5: Analysis with Power BI & Excel](#7-step-5-analysis-with-power-bi--excel)
- [8. Conclusion & Results](#8-conclusion--results)
- [9. Technologies Used](#9-technologies-used)

---

## 1. Project Context & Objectives
- **Consolidate data** from multiple sources (Access 2024, JSON 2023, CSV 2020–2022).
- **Enable decision-making analysis** through a star schema (dimensions: Patient, Doctor, Location, Time; fact table: Consultation).
- **Provide tools for business intelligence** with Power BI and Excel for visual insights.

---

## 2. Step 0: Data Warehouse Design
- Requirement analysis and source identification.
- **Star schema modeling**:
  - **Fact Table**: Consultation (Price, Duration)
  - **Dimensions**: Patient, Doctor, Location, Time
- Conceptual schema created using PowerPoint.

![Conceptual Schema](img/schema.png)

---

## 3. Step 1: Data Filtering & Extraction
Two approaches were used:

- **Talend Open Studio**:
  - Transform columns (boolean conversion, normalization)
  - Merge datasets with `tMap` and `tUnite`
  - ![Talend Transformation](img/talend_transformation.png)

- **Python scripts**:
  - Filter and clean data
  - Merge datasets into a single file (`tous.csv`)
  - ![Python Script Example](img/python_script.png)

📌 **Output**: A clean, unified dataset ready for loading into MySQL.

---

## 4. Step 2: Dimensions Extraction & MySQL Loading
- **Patient Dimension**: full name, age group, normalized weight
- **Doctor Dimension**: full name, age group, specialty
- **Location Dimension**: hospital, city, country
- **Time Dimension**: year, month, weekday
- Added `id` primary keys for all dimensions
- Used `tUniqRow` in Talend to remove duplicates

![MySQL Tables](img/mysql_tables.png)

---

## 5. Step 3: Fact Table Creation
- Using Talend:
  - Load consolidated dataset (`tous.csv`)
  - Join with dimension tables via `tMap`
  - Create **Consultation fact table** with foreign keys (ID_patient, ID_doctor, ID_location, ID_time) and measures (Price, Duration)
- Fact table loaded into **MySQL**

![Fact Table](img/fact_table.png)

---

## 6. Step 4: OLAP Cube Creation
- Migrated MySQL data to **SQL Server Analysis Services (SSAS)**
- Created dimensions and hierarchies (Patient, Doctor, Location, Time)
- Defined measures (number of consultations, revenue)
- Built aggregations and deployed the cube

🔎 **Example analyses**:
- **Slice**: consultations by month
- **Dice**: revenue by doctor and hospital
- **Roll-up / Drill-down**: trends across years and months

![OLAP Cube](img/olap_cube.png)

---

## 7. Step 5: Analysis with Power BI & Excel

- **Power BI**:
  - Created **interactive graphs and charts** (bar charts, pie charts, trend lines)
  - Explored consultations and revenue data dynamically
  - ![Power BI Charts](img/powerbi_charts.png)

- **Excel**:
  - Connected to OLAP cube
  - Created **pivot tables** for multi-dimensional analysis
  - ![Excel Pivot Table](img/excel_pivot.png)

---

## 8. Conclusion & Results
✅ The project successfully delivered:
- A **robust medical data warehouse**
- A **high-performance OLAP cube** using SSAS
- **Interactive insights** using Power BI and Excel (charts, graphs, pivot tables)

🚀 **Impact**:
- Improved understanding of medical activity trends
- Optimized hospital resource management
- Enhanced tracking of patient and doctor performance

---

## 9. Technologies Used
- **ETL**: Talend Open Studio, Python
- **Database**: MySQL
- **OLAP**: SQL Server Analysis Services (SSAS)
- **BI Tools**: Power BI, Excel
- **Data Sources**: Access, JSON, CSV
