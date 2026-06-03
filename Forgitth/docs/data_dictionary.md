# Forggith Pharmaceuticals — Data Dictionary

This document describes all columns used across the Forggith Sales & Marketing Performance dataset.  
It supports data governance, model transparency, and consistent interpretation of metrics.

---

## 📁 Location & Geography Tables

| Column Name | Meaning |
|-------------|---------|
| **LocationID** | Unique identifier for each customer location; also used as a reference key. |
| **City** | Name of the city where the customer is located. |
| **Latitude** | Geographic latitude of the customer location (distance from the equator). |
| **Longitude** | Geographic longitude of the customer location (distance from the equator). |

---

## 📁 Channel & Sub‑Channel Tables

| Column Name | Meaning |
|-------------|---------|
| **SubchannelID** | Distinct numeric identifier for each sub‑channel; reference key. |
| **ChannelID** | Distinct numeric identifier for each channel; reference key. |
| **Subchannel** | Name of the sub‑channel (e.g., Retail, Private, Government). |
| **Channel** | Name of the channel (e.g., Pharmacy, Hospital). |

---

## 📁 Product Table

| Column Name | Meaning |
|-------------|---------|
| **ProductID** | Unique numeric identifier for each product; reference key. |
| **ProductName** | Name of the product sold. |
| **ProductClass** | Classification/category of the product (e.g., Analgesics, Antibiotics). |
| **ProductPrice** | Actual selling price of each product. |

---

## 📁 Sales Representative Table

| Column Name | Meaning |
|-------------|---------|
| **ID** | Unique identifier for each sales representative; reference key. |
| **Name** | Full name of the sales representative. |
| **Manager** | Name of the manager supervising the sales representative. |
| **Team** | Team assignment (e.g., Alfa, Bravo, Charlie, Delta). |

---

## 📁 Sales Fact Table

| Column Name | Meaning |
|-------------|---------|
| **Sales ID** | Unique identifier for each sales transaction. |
| **MonthYear** | Date of the sales transaction (Month + Year). |
| **Distributor** | Name of the distributor responsible for the sale. |
| **Customer Name** | Name of the customer purchasing the product. |
| **Quantity** | Number of units sold in the transaction. |

---

## ✔ Notes
- All key columns (LocationID, ProductID, ChannelID, SubchannelID, SalesRepID) support the star schema design.
- Text fields are standardized during ETL to ensure consistency.
- Date fields are converted to proper date types for time intelligence DAX.

---

This file is part of the Forggith documentation suite located in the `/docs` folder.