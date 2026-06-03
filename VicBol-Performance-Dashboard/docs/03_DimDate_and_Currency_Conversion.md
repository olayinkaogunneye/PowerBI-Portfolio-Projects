# DimDate & Currency Conversion Documentation  
**Prepared by:** Olayinka Ogunneye  
**Project:** VicBol Performance Analytics Case Study  
**Scope:** Construction of DimDate & Standardization of Currency Values  

---

## 1. Introduction
This document outlines two essential components of the VicBol analytical model:

- DimDate  
- Currency Conversion  

---

## 2. DimDate — Construction & Validation

### 2.1 Date Range Identification
Min and max dates were identified across both fact tables.

### 2.2 DimDate Creation (DAX)
A continuous date table was generated with:

- Year  
- Quarter  
- Month  
- Month name  
- YearMonth  
- Week  
- Day  
- Day name  
- Surrogate key (DateID)  

### 2.3 Marking as Official Date Table
Enabled:

- YTD  
- MTD  
- QTD  
- YoY  
- Rolling averages  

### 2.4 Final Structure

| Column     | Description               |
|------------|---------------------------|
| DateID     | Surrogate key             |
| Date       | Continuous daily date     |
| Year       | Calendar year             |
| Quarter    | Calendar quarter          |
| Month      | Month number              |
| Monthname  | Full month name           |
| YearMonth  | YYYYMM format             |
| Week       | Week number               |
| Day        | Day number                |
| Dayname    | Full day name             |

---

## 3. Currency Conversion — FactCosts

### 3.1 Exchange Rate Merge
Merged FactCosts with ExchangeRates on:

- date  
- currency  

### 3.2 Spend Conversion
`spend_czk = spend * exchange_rate`

### 3.3 Validation Checks
- No null exchange rates  
- No failed matches  
- No negative or zero rates  

### 3.4 FactExitClicks Currency Handling
Revenue already in CZK → no conversion needed.

---

## 4. Overall Assessment
- All fact tables aligned to DimDate  
- All monetary values standardized  
- Model ready for relationships and DAX  