 End-to-End ETL Pipeline: Multi-Source to Star Schema DWH

📖 Project Overview
This project demonstrates a complete ETL (Extract, Transform, Load) workflow designed to process diverse business data into a structured Data Warehouse. The goal was to build a scalable pipeline that handles various file formats, ensures data quality, and organizes data into a **Star Schema** optimized for BI tools like Power BI.

🏗️ Data Architecture
The pipeline is divided into three distinct logical phases:

 1. ODS Layer (Operational Data Store)
    Sources: Excel, XML, and CSV files.
    Objective: Standardize and unify data. 
    Logic: Used `Union All` to merge sources and `Data Conversion` to handle encoding (Unicode vs. Non-Unicode) and data types.

 2. Staging & Dimensional Loading
    Strategy: Truncate-and-Load.
    Execution: Used Sequence Containers to group related tasks.
    Parallelism: Dimensions (Dim_Emp, Dim_Dept, Dim_Loc, Dim_date,Dim_gender ) are loaded in parallel to minimize execution time.

 3. Fact Table Ingestion
  Lookup Logic: A chain of Lookup Transformations was used to replace natural keys with surrogate keys from the dimension tables.
  Business Logic:Implemented Derived Columns to calculate metrics on the fly, such as transforming `BirthDate` into `Age` using SQL expressions.

🛠️ Tech Stack & Tools
  Orchestration: SQL Server Integration Services (SSIS).
  Storage: Microsoft SQL Server (T-SQL).
  Environment: Visual Studio (SSDT).
  Modeling: Star Schema (1 Fact Table, 5 Dimension Tables).

 🚀 Key Features & Optimizations
  Dynamic Truncate: A centralized Execute SQL Task clears staging tables before every run to prevent data duplication.
  Bulk Loading: Enabled Fast Load on OLE DB Destinations for high-speed data ingestion.
  Modular Design: Used Sequence Containers to separate Dimension and Fact loading phases, ensuring referential integrity.

- **Dim_Emp / Dim_Dept / Dim_Loc / Dim_Gender:** Descriptive attributes for filtering and grouping.


<img width="1041" height="478" alt="Screenshot 2026-03-10 220655" src="https://github.com/user-attachments/assets/510a79b1-7f83-43c0-a023-184f31e322ff" />
<img width="1257" height="518" alt="Screenshot 2026-03-10 221039" src="https://github.com/user-attachments/assets/d96c7e4b-52c2-4803-bd82-8307e8f2ad76" />
<img width="1121" height="468" alt="Screenshot 2026-03-10 221102" src="https://github.com/user-attachments/assets/bd946249-e63b-4b14-a7c4-0e8f30d664e2" />
<img width="1243" height="815" alt="Screenshot 2026-03-10 221159" src="https://github.com/user-attachments/assets/a2e7a7a7-ee16-40d6-8b07-23ea54079984" />






---
