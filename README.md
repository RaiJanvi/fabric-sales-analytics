# Microsoft Fabric Sales Analytics Pipeline 

## Overview 
End-to-end data engineering pipeline built on Microsoft Fabric using the AdventureWorks OLTP dataset. Implements a Bronze/Silver/Gold medallion architecture with SCD Type 2 history tracking and a DirectLake Power BI dashboard. 

## Architecture 

<img width="1171" height="657" alt="Screenshot 2026-03-30 051455" src="https://github.com/user-attachments/assets/427e6fdc-853f-4c6c-9c4e-aaaeddfe6201" />

| Layer  | Tool             | Purpose                          | 
|--------|------------------|----------------------------------| 
| Bronze | PySpark Notebook | Raw OLTP ingestion (7 tables)    | 
| Silver | PySpark + MERGE  | Cleansing + SCD Type 2           | 
| Gold   | PySpark        | Star schema (fact + 4 dims)      | 
| Report | Power BI         | DirectLake dashboard             | 

## Key Technical Highlights 
- SCD Type 2 on Production.Product using Delta Lake MERGE 
- Point-in-time accurate revenue via date-range join in gold fact 
- DAX measures: Revenue, Gross Margin %, Revenue at Historic Price, Gross Profit
- Orchestrated daily via Fabric Data Pipeline with retry and alerts 

## Dataset 
Source: AdventureWorks OLTP (Microsoft sample database) 
Tables used: SalesOrderHeader, SalesOrderDetail, Product, ProductCategory, ProductSubcategory, Customer, SalesTerritory 

## How to Run 
1. Create a Microsoft Fabric workspace and Lakehouse (SalesLakehouse) 
2. Upload CSVs to Files/raw/adventureworks/ 
3. Run notebooks in order: Bronze → Silver → Gold 
4. Create semantic model on Gold tables 
5. Build Power BI report in DirectLake mode 

## Skills Demonstrated 
Microsoft Fabric | PySpark | Delta Lake | SCD Type 2 | Medallion Architecture | Spark SQL | DAX | Power BI DirectLake | Fabric Data Pipelines | Git 
