# Forggith Pharmaceuticals — Sales & Marketing Performance Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-FAE100?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-blue?style=for-the-badge)
![Power Query](https://img.shields.io/badge/Power%20Query-4CAF50?style=for-the-badge&logo=microsoft&logoColor=white)
![SQL](https://img.shields.io/badge/SQL-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)
![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)


Forggith Pharmaceuticals is a Germany‑based pharmaceutical manufacturing company that distributes medical products exclusively through independent distributors.  
Although Forggith does not sell directly to retailers or end‑users, the company maintains strong relationships with retail outlets through its Sales and Marketing teams.

This Power BI project transforms raw distributor submissions into a unified, analytics‑ready model and an interactive dashboard that supports strategic, tactical, and operational decision‑making.

---

## 📌 Project Objectives

Forggith needed a reporting solution that could answer critical commercial questions:

- Are we meeting revenue and volume targets?
- Which teams, sales reps, and regions are driving growth?
- How are products performing across channels and sub‑channels?
- What trends exist across months, quarters, and years?
- Where should Sales and Marketing focus their efforts?

This project delivers a complete Power BI solution that addresses these needs through automated ETL, a clean star schema, and robust DAX measures.

---

## 📊 Key Reporting Features

### **Sales Performance Overview**
Slicers: Year, Month, Quarter, Team

- Total Revenue  
- Total Revenue YTD  
- Total Revenue SPLY  
- Total Target  
- Target YTD  
- Actual vs Target YTD  
- Month‑on‑Month % Change  
- Revenue by City  
- Revenue by Channel  
- Revenue by Product Class  

### **Marketing Performance Overview**
Slicers: Year, Quarter, Month, Product Category, Team

- Revenue vs Target  
- Volume vs Target  
- Revenue by Sales Rep  
- Target Achievement %  
- Team Performance  
- Product Performance  

---

## 🧩 Data Model Overview

The model follows a **star schema** for performance and clarity.

### **Fact Table**
- FactSales (combined from Sales2022 + Sales2023‑2025)

### **Dimension Tables**
- DimProducts  
- DimEmployees  
- DimChannels  
- DimSubChannel  
- DimLocation  
- DimDate  
- Targets  

### **Measures Table**
- _Measures (all DAX KPIs)

Full model documentation in: 

`/docs/model_documentation.md`

---

## 🔧 ETL Process Summary

The ETL pipeline (Power Query) performs:

- Extraction from Excel workbooks  
- Header promotion and type enforcement  
- Cleaning and standardization  
- Creation of dimension tables  
- Combination of multi‑year sales tables  
- Validation of keys and dates  
- Loading into the semantic model  

Full ETL documentation in:

`/docs/etl_documentation.md`

---

## 📚 Data Dictionary

A complete description of all columns across all tables is available here:

`/docs/data_dictionary.md`

---

## 🔍 Insights Summary

Key insights from the dashboard include:

- February recorded the highest month‑to‑month revenue increase.  
- Butzbach is the top‑performing city with $94M in revenue.  
- Analgesics and Antiseptics dominate product class revenue.  
- Charlie team leads performance with 59% revenue achievement.  
- Abigail Thompson contributed 20.55% of total revenue.  
- Actual Revenue ($11.12bn) exceeded Target Revenue ($8.45bn) by 31%.  

Full insights summary: `/docs/insights_summary.md`

---

## 📁 Project Structure

Forggith/
│
├── Forggith project.pbip
├── Forggith project.Report/
├── Forggith project.SemanticModel/
│
├── docs/
│   ├── data_dictionary.md
│   ├── etl_documentation.md
│   ├── model_documentation.md
│   └── insights_summary.md
│
└── README.md



---

## 🚀 How to Use This Project

1. Clone the repository  
2. Open the folder in Power BI Desktop (PBIP mode)  
3. Ensure the `/Data` folder contains the Excel source files  
4. Refresh the model  
5. Explore the Sales & Marketing dashboards  

---

## 🖌 Branding & Design

Forggith’s official brand colors and logo (from the Assets folder) were applied consistently across:

- KPIs  
- Charts  
- Navigation  
- Page backgrounds  
- Buttons  

---

## 🌐 View the Live Dashboard

You can explore the fully interactive Power BI dashboard using the link below:

👉 **Live Dashboard:** *[https://app.fabric.microsoft.com/view?r=eyJrIjoiNjlmZmUwMDEtODdhZi00MDYyLTg2MzAtMGEyMmYwNjBkNjA3IiwidCI6ImFjMDZkNWY1LTNiMWYtNGVkNy05NGY4LTRlODUzOGUwYjdlYSJ9]*

If the report requires access permissions, ensure your Power BI account has been granted viewer rights.

## 📈 Skills Demonstrated

- Power BI (Advanced)  
- Data Modeling (Star Schema)  
- Power Query (ETL)  
- DAX (Time Intelligence, KPI Logic)  
- Data Visualization & UX  
- GitHub Version Control (PBIP workflow)  

---

## 👤 Author

**Olayinka Ogunneye**  
Analytics Consultant & Data Engineer  
Power BI | SQL | Python | Data Modeling  

---

This project is part of a professional Power BI portfolio demonstrating end‑to‑end BI engineering capability.
