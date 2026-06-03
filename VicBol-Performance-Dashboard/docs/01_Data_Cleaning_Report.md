# Data Cleaning Report — FactCosts & FactExitClicks  
**Prepared by:** Olayinka Ogunneye  
**Project:** VicBol Performance Analytics Case Study  
**Scope:** Data Cleaning & Validation of Core Fact Tables  

---

## 1. Introduction
This report documents the data cleaning and validation steps performed on two core fact tables used in the VicBol analytics assignment:

- FactCosts  
- FactExitClicks  

The objective of the cleaning phase was to ensure that both tables were:

- structurally consistent  
- free of invalid or ambiguous values  
- standardized for modelling  
- aligned with best practices in data engineering  
- ready for integration into a star schema  

All transformations were performed in Power Query using a systematic, repeatable approach.

---

## 2. Cleaning Summary — FactCosts

The Costs table contains daily advertising spend across countries, channels, and currencies.

### 2.1 Data Type Validation
Correct data types were applied:

| Column     | Data Type       |
|------------|-----------------|
| date       | date            |
| country    | text            |
| channel_id | whole number    |
| currency   | text            |
| spend      | decimal number  |

### 2.2 Text Standardization
- Applied Trim and Clean  
- Converted country and currency to uppercase  
- Removed hidden whitespace  

### 2.3 Spend Validation
- All values numeric  
- No negative values  
- No nulls  
- No unexpected symbols  

### 2.4 Channel ID Validation
- All values numeric  
- No nulls  
- No placeholder values  

### 2.5 Duplicate Checks
- No full-row duplicates  
- Each row represents a unique combination of date, country, and channel  

### 2.6 Null Checks
- No nulls across any column  

### 2.7 Country & Date Integrity
- Country codes valid  
- Date range aligned with dataset  

**Outcome:** FactCosts is fully cleaned and ready for modelling.

---

## 3. Cleaning Summary — FactExitClicks

The FactExitClicks table contains daily click-out activity and revenue by channel and device type.

### 3.1 Data Type Validation

| Column       | Data Type       |
|--------------|-----------------|
| date         | date            |
| country      | text            |
| channel_id   | whole number    |
| device_type  | text            |
| exit_clicks  | whole number    |
| revenue_loc  | decimal number  |

### 3.2 Text Standardization
- Applied Trim and Clean  
- Standardized country to uppercase  
- Standardized device_type to lowercase  

### 3.3 Device Type Validation
- Only valid categories present: mobile, pc, tablet  
- No nulls  

### 3.4 Exit Clicks Validation
- All values whole numbers  
- No negatives  
- No nulls  

### 3.5 Revenue Validation
- All values numeric  
- No negatives  
- No nulls  
- No suspicious outliers  

### 3.6 Channel ID Integrity
- Identified 3 rows with null channel_id  
- Rows removed to prevent orphaned records  

### 3.7 Duplicate Checks
- No full-row duplicates  
- No partial duplicates  

### 3.8 Country & Date Integrity
- Country values valid  
- Date range consistent  

**Outcome:** FactExitClicks is fully cleaned and ready for modelling.

---

## 4. Overall Data Quality Assessment

After cleaning both fact tables:

- All key fields are complete  
- All text fields standardized  
- All numeric fields validated  
- No structural duplicates  
- No orphaned rows  
- Both tables ready for:  
  - relationship building  
  - currency conversion  
  - time intelligence  
  - accurate aggregations  
  - dashboard development  

**Final Result:** The cleaned fact tables form a reliable foundation for the VicBol performance analytics model.