# Star Schema Relationship Documentation  
**Prepared by:** Olayinka Ogunneye  
**Project:** VicBol Performance Analytics Case Study  
**Scope:** Data Model Relationship Design & Validation  

---

## 1. Introduction
This document outlines the star schema relationships used in the VicBol analytics model.

---

## 2. Overview of the Star Schema

### Fact Tables
- FactCosts  
- FactExitClicks  

### Dimension Tables
- DimDate  
- DimCountry  
- DimChannel  
- DimDevice  

All relationships are single‑direction, many‑to‑one.

---

## 3. Relationship Definitions

### 3.1 FactCosts Relationships

| Fact Column | Dimension Table | Dimension Column | Cardinality   | Direction |
|-------------|-----------------|------------------|----------------|-----------|
| date        | DimDate         | Date             | Many-to-One    | Single    |
| country     | DimCountry      | Country          | Many-to-One    | Single    |
| channel_id  | DimChannel      | Channel_id       | Many-to-One    | Single    |

### 3.2 FactExitClicks Relationships

| Fact Column | Dimension Table | Dimension Column | Cardinality   | Direction |
|-------------|-----------------|------------------|----------------|-----------|
| date        | DimDate         | Date             | Many-to-One    | Single    |
| country     | DimCountry      | Country          | Many-to-One    | Single    |
| channel_id  | DimChannel      | Channel_id       | Many-to-One    | Single    |
| device_type | DimDevice       | device_type      | Many-to-One    | Single    |

---

## 4. Relationship Design Principles
- Single-direction filtering  
- No bidirectional relationships  
- No many-to-many joins  
- Shared dimensions across fact tables  

---

## 5. Validation Checks
- No orphaned rows  
- All keys match  
- DimDate covers full range  
- Channel IDs consistent  
- Device types validated  

---

## 6. Outcome
The schema is:

- clean  
- validated  
- optimized  
- ready for DAX and dashboard development  