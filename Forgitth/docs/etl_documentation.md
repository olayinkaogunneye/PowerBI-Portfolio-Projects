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

```

Each sheet is accessed via:n Source{[Item="SheetName", Kind="Sheet"]}[Data]

### Extracted Table

| Excel Sheet     | Power BI Table        |
|-----------------|------------------------|
| Sales2022       | Actual sales (part 1)  |
| Sales2023‑2025  | Actual sales (part 2)  |
| DimChannel      | DimChannels            |
| DimSubChannel   | DimSubChannel          |
| Products        | DimProducts            |
| Employees       | DimEmployees           |
| Locations       | DimLocation            |
| Targets         | Targets                |

---

### 3. Transform Phase

#### 3.1 Promote Headers

`m
Table.PromoteHeaders(Source, [PromoteAllScalars = true])
`

#### 3.2 Apply Data Types

- IDs → Int64.Type

- Dates → type date

- Text → type text

- Quantities → Int64.Type

- Prices → type number

This ensures:

- DAX time intelligence works

- Numeric aggregations behave correctly

- Relationships are valid

---

### 4. Dimension Table Transformations

#### 4.1 DimChannels

**Columns:**

- ChannelID

- Channel

**Transformations:**

- Promote headers

- Convert ChannelID → whole number

- Clean text values

#### 4.2 DimSubChannel

**Columns:**

- SubChannelID

- ChannelID

- SubChannel

**Transformations:**

- Promote headers

- Convert IDs → whole number

- Standardize sub‑channel names

#### 4.3 DimProducts

**Columns:**

- ProductID

- ProductName

- ProductClass

- ProductPrice

**Transformations:**

- Clean product names

- Ensure ProductPrice is numeric

- Validate ProductClass categories

#### 4.4 DimEmployees

**Columns:**

- ID

- Name

- Manager

- Team

- Transformations:

- Trim and clean text

- Validate team names (Alfa, Bravo, Charlie, Delta)

#### 4.5 DimLocation

**Columns:**

- LocationID

- City

- Latitude

- Longitude

- Transformations:

- Validate coordinates

- Standardize city names

#### 4.6 DimDate

Generated using a Date Table Template:

**Columns:**

- Date

- Year

- Month

- Quarter

- MonthName

- YearMonth

Supports all time intelligence measures.

---

### 5. Fact Table Transformations

#### 5.1 Actual sales (Sales2022 + Sales2023‑2025)

**Columns:**

- Sales ID

- MonthYear

- SalesRepID

- Distributor

- Customer Name

- LocationID

- SubChannelID

- ProductID

- Quantity

**Transformations:**

- Promote headers

- Convert MonthYear → date

- Convert Quantity → whole number

- Validate foreign keys

- Remove blank rows

#### 5.2 Combine Sales Tables
`m
FactSales = Table.Combine({Sales2022, Sales2023_2025})
This creates a unified fact table for all years.
`
---

### 6. Targets Table Transformations

**Columns:**

- TargetQty

- ProductID

- SalesRepID

- MonthYear

**Transformations:**

- Promote headers

- Convert TargetQty → whole number

- Convert MonthYear → date

- Validate ProductID and SalesRepID

---

### 7. Data Quality Checks

#### 7.1 Key Integrity

- No missing ProductID

- No missing LocationID

- No missing SubChannelID

- No missing SalesRepID

All ProductID and SalesRepID in Targets must exist in DimProducts and DimEmployees

#### 7.2 Date Validation

- All MonthYear values must be valid dates

- All dates must fall within 2022–2025

#### 7.3 Duplicate Detection

- Sales ID must be unique

#### 7.4 Price Validation

- ProductPrice must be > 0

---

### 8. Load Phase

**After transformation:**

- All dimension tables are loaded into the semantic model

- FactSales is loaded as the central fact table

- Targets is loaded as a target fact/dimension

- Relationships are created in Model View

- DAX measures are defined in the _Measures table

---

### 9. ETL Summary Table

| Table          | Source   | Key Steps                                   | Output            |
|----------------|----------|----------------------------------------------|-------------------|
| DimChannels    | Excel    | Promote headers, type enforcement            | Clean dimension   |
| DimSubChannel  | Excel    | Standardize names                            | Clean dimension   |
| DimProducts    | Excel    | Clean names, enforce price types             | Clean dimension   |
| DimEmployees   | Excel    | Clean text, validate teams                   | Clean dimension   |
| DimLocation    | Excel    | Validate coordinates, standardize cities     | Clean dimension   |
| Sales2022      | Excel    | Promote headers, type enforcement            | Fact part 1       |
| Sales2023‑2025 | Excel    | Promote headers, type enforcement            | Fact part 2       |
| Targets        | Excel    | Clean target data, enforce key types         | Target table      |
| FactSales      | Combined | Append tables, validate keys, clean rows     | Final fact table  |

---

### 10. Future Enhancements
Replace local Excel paths with relative paths for GitHub portability

Move data to Fabric Lakehouse or Dataflow Gen2

Add incremental refresh for FactSales

Add RLS for Sales Reps and Teams