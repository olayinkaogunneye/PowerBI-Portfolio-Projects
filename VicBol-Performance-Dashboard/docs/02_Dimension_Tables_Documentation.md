# Dimension Table Documentation — DimCountry & DimChannel  
**Prepared by:** Olayinka Ogunneye  
**Project:** VicBol Performance Analytics Case Study  
**Scope:** Construction & Validation of Dimension Tables  

---

## 1. Introduction
This document outlines the creation and validation of two key dimension tables used in the VicBol analytics model:

- DimCountry  
- DimChannel  

Both dimensions were derived from the cleaned fact tables and serve as lookup tables in the star schema.

---

## 2. DimCountry — Construction & Cleaning Summary

### 2.1 Source & Extraction
DimCountry was created by:

- Referencing the cleaned fact tables  
- Selecting the country column  
- Removing duplicates  
- Sorting alphabetically  

### 2.2 Text Standardization
- Applied Trim and Clean  
- Converted all country codes to uppercase  
- Verified no hidden whitespace  

### 2.3 Surrogate Key Creation
- Added `country_id` using Index Column From 1  

### 2.4 Final Structure

| Column      | Description                     |
|-------------|---------------------------------|
| country_id  | surrogate key                   |
| country     | cleaned, uppercase country code |

**Outcome:** DimCountry is clean, minimal, and ready for use.

---

## 3. DimChannel — Construction & Cleaning Summary

### 3.1 Source & Extraction
DimChannel was created by:

- Appending channel_id values from both fact tables  
- Removing duplicates  
- Sorting ascending  

### 3.2 Channel ID Integrity Check
- Verified no mismatches between fact tables  

### 3.3 Text Standardization
- Applied Trim and Clean  
- Standardized naming conventions  

**Outcome:** DimChannel is validated and ready for use.

---

## 4. Overall Dimension Quality Assessment
Both dimensions:

- Contain only unique, standardized values  
- Include surrogate keys  
- Are derived directly from cleaned fact tables  
- Ensure consistent filtering  
- Support a robust star schema  