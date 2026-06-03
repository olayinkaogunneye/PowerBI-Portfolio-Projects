# Forggith Model Documentation
(Data Model, Relationships, and DAX Measures)

This document describes the semantic model used in the Forggith Pharmaceuticals Power BI solution.
It includes the star schema, table definitions, relationships, and all DAX measures used for KPI calculations.

---

### 1. Data Model Overview

The Forggith model follows a star schema, optimized for:

- High‑performance aggregations

- Time intelligence

- Clear business logic

- Easy extensibility

- The model consists of:

**Fact Table**

FactSales (combined from Sales2022 + Sales2023‑2025)

**Dimension Tables**

- DimDate

- DimProducts

- DimSalesRep

- DimChannel

- DimSubChannel

- DimLocation

**Targets** (acts as a factless dimension for target metrics)

Measures Table
`_Measures` (contains all DAX KPIs)

---

### 2.Star Schema Structure

                   DimDate
                      |
                      | (Date)
                      |
                 FactSales
                /    |     \
               /     |      \
      DimProducts  DimSalesRep  DimLocation
             |          |             |
      DimSubChannel — DimChannel — Targets

---

### Key relationships:

| From Table   | Column       | To Table     | Column      | Type         |
|--------------|--------------|--------------|-------------|--------------|
| FactSales    | ProductID    | DimProducts  | ProductID   | Many-to-One  |
| FactSales    | SalesRepID   | DimSalesRep  | ID          | Many-to-One  |
| FactSales    | LocationID   | DimLocation  | LocationID  | Many-to-One  |
| FactSales    | SubChannelID | DimSubChannel| SubChannelID| Many-to-One  |
| DimSubChannel| ChannelID    | DimChannel   | ChannelID   | Many-to-One  |
| FactSales    | MonthYear    | DimDate      | Date        | Many-to-One  |
| Targets      | ProductID    | DimProducts  | ProductID   | Many-to-One  |
| Targets      | SalesRepID   | DimSalesRep  | ID          | Many-to-One  |


### 3. Fact Table: FactSales

Contains all sales transactions from 2022–2025.

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

**Notes:**

- Quantity is aggregated using SUM

- MonthYear is linked to DimDate for time intelligence

- ProductID links to DimProducts for pricing and product class

---

### 4. Dimension Tables

#### 4.1 DimProducts

- ProductID

- ProductName

- ProductClass

- ProductPrice

Used for revenue calculations and product segmentation.

#### 4.2 DimSalesRep

- ID

- Name

- Manager

- Team

Used for team performance, rep performance, and marketing KPIs.

#### 4.3 DimChannel & DimSubChannel

- ChannelID

- Channel

- SubChannelID

- SubChannel

- ChannelID (relationship to DimChannel)

Used for channel performance analysis.

#### 4.4 DimLocation

- LocationID

- City

- Latitude

- Longitude

Used for geographic revenue analysis.

#### 4.5 DimDate

Standard date table supporting:

- YTD

- SPLY

- MoM

- Previous Year

- Previous Month

#### 4.6 Targets Table

Contains:

- TargetQty

- ProductID

- SalesRepID

- MonthYear

Used for:

- Target Revenue

- Target Quantity

- Achievement %

---

### 5. DAX Measures Documentation

Below is a complete list of all measures in your _Measures table, rewritten in clean documentation format.

#### 5.1 Revenue Measures

**Actual Revenue**
```
SUMX('Actual sales', 'Actual sales'[Quantity] * RELATED(DimProducts[ProductPrice]))

```
Calculates actual revenue based on quantity × product price.

**Target Revenue**
```
SUMX('Targets', 'Targets'[TargetQty] * RELATED(DimProducts[ProductPrice]))

```
Calculates target revenue based on target quantity × product price.

**Total Revenue**
```
[Actual Revenue] + [Target Revenue]

```
Combined actual + target revenue.

**Total Revenue SPLY**
```
CALCULATE([Total Revenue], SAMEPERIODLASTYEAR(DimDate[Date]))

```
Revenue for the same period last year.

**Actual Revenue YTD**
```
TOTALYTD([Actual Revenue], DimDate[Date])

```

**Target Revenue YTD**
```
TOTALYTD([Target Revenue], DimDate[Date])

```
**Total Revenue YTD**
```
TOTALYTD([Total Revenue], DimDate[Date])

```
#### 5.2 Quantity Measures

**Actual Quantity**
```
SUM('Actual sales'[Quantity])

```

**Target Quantity**
```
SUM(Targets[TargetQty])

```

#### 5.3 Transaction Measures

**Total Transactions**
```
COUNT('Actual sales'[Sales ID])

```
#### 5.4 Time Intelligence Measures

**Previous Month Revenue**
```
CALCULATE([Actual Revenue], PREVIOUSMONTH(DimDate[Date]))

```
**% Actual Revenue Change**
```
DIVIDE([Actual Revenue], [Previous month revenue], BLANK()) - 0

```
Month‑over‑month revenue change.

**Actual Revenue Previous Year**
```
CALCULATE([Actual Revenue], PREVIOUSYEAR(DimDate[Date]))

```
**Target Revenue Previous Year**
```
CALCULATE([Target Revenue], PREVIOUSYEAR(DimDate[Date]))

```
#### 5.5 Achievement Measures

**% Revenue Achievement**
```
VAR Revenueachievement =
    [Actual Revenue] - [Target Revenue]
RETURN
    DIVIDE(Revenueachievement, [Target Revenue]) * 100

```

**% Volume Achievement**
```
VAR volumeachievement =
    [Actual Quantity] - [Target Quantity]
RETURN
    DIVIDE(volumeachievement, [Target Quantity]) * 100

```
---

### 6. Model Strengths

- Fully optimized star schema

- Clean separation of facts and dimensions

- Robust time intelligence

- Flexible for slicing by team, product, channel, location, and time

- Supports both Sales and Marketing KPIs

- Measures table centralizes all business logic

---

### 7. Future Enhancements

Add incremental refresh for FactSales

Move Excel sources into a Dataflow or Lakehouse

Add row‑level security (RLS) for Sales Reps and Teams

Add composite models for real‑time distributor data