# Forggith Pharmaceuticals — ETL Documentation
This document describes the full Extract–Transform–Load (ETL) process used to prepare Forggith Pharmaceuticals’ Sales & Marketing dataset for reporting in Power BI.  
It outlines how raw Excel files are ingested, cleaned, standardized, and modeled into a star schema.

---

## 1. ETL Pipeline Overview
Forggith provided two Excel workbooks:

- **PharmDataset‑230517‑152700.xlsx** → Sales, Products, Channels, Locations  
- **PharmTargets‑230519‑175734.xlsx** → Target quantities by product, rep, and date  

The ETL pipeline performs:

1. **Extract**  
   - Load Excel sheets into Power Query  
   - Promote headers  
   - Apply correct data types  

2. **Transform**  
   - Clean text fields  
   - Standardize naming  
   - Validate keys  
   - Create dimension tables  
   - Append sales tables into a unified fact table  

3. **Load**  
   - Load cleaned tables into the semantic model  
   - Create relationships  
   - Build DAX measures  

---

## 2. Extract Phase

All tables are imported using:

```m
Excel.Workbook(File.Contents("…PharmDataset-230517-152700.xlsx"), null, true)

Each sheet is accessed via:

Source{[Item="SheetName", Kind="Sheet"]}[Data]