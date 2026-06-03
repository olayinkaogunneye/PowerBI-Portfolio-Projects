# 05_KPI_Definitions

**Prepared by:** Olayinka Ogunneye  
**Project:** FAVI Performance Analytics Case Study  
**Scope:** KPI Definitions & Business Logic  

---

## 1. Introduction

This document defines all Key Performance Indicators (KPIs) used in the FAVI Performance Dashboard.  
Each KPI includes:

- A clear definition  
- The business purpose  
- The DAX logic  
- Interpretation notes  

These KPIs form the analytical foundation of the dashboard and support executive‑level decision‑making.

---

## 2. Core Financial KPIs

### 2.1 Total Spend (CZK)

**Definition:**  
Total advertising spend across all channels, converted to CZK.

**DAX:**
Total Spend CZK = SUM(FactCosts[spend_czk])

**Purpose:** 
Measures total marketing investment.

**Interpretation:** Spend should ideally correlate with exit clicks and revenue

### 2.2 Total Revenue (CZK)

**Definition:**  
Total revenue generated from exit clicks.

**DAX:**
Total Revenue CZK = SUM(FactExitClicks[revenue_loc])

**Purpose:**  
Measures monetary return from user click‑outs.

**Interpretation:**  Revenue follows seasonal patterns (e.g., November peak).


### 2.3 Profit (CZK)

**Definition:** 
Revenue minus Spend.

**DAX:**
Total Revenue CZK = SUM(FactExitClicks[revenue_loc])

**Purpose:** 
Shows whether marketing activities are profitable.

**Interpretation:** Profit is negative across all months because Spend > Revenue.

### 2.4 ROI (Return on Investment)

**Definition:**
Measures the efficiency of marketing spend.

**DAX:**
ROI = DIVIDE([Profit], [Total Spend CZK])

**Purpose:** Shows how much return is generated per CZK spent.

**Interpretation:** Negative ROI indicates inefficient spend or low revenue response.

### Traffic KPIs
3.1 Total Exit Clicks

**Definition:** Total number of click outs from FAVI to partner websites.

**DAX:**
Total Exit Clicks = SUM(FactExitClicks[exit_clicks])

**Purpose:** Measures user engagement and traffic volume.

**Interpretation:** Exit clicks follow the same seasonal pattern as spend.

### 3.2 Cost Per Click (CPC)

**Definition:** Average cost to generate one exit click.

**DAX**
CPC = DIVIDE([Total Spend CZK], [Total Exit Clicks])

**Purpose:** Evaluates traffic acquisition efficiency.

**Interpretation:** Lower CPC indicates more efficient spend.

### 4. Month over Month (MoM) KPIs
MoM indicators were created using reusable DAX UDFs to ensure consistency and reduce code duplication.

### 4.1 MoM % Change

***Definition:** Percentage change from previous month.

**DAX:**
MOMGrowth(CurrentValue, LastMonthValue)

**Purpose:** Highlights trends and performance shifts.

### 4.2 MoM Display (Arrow + %)

**Definition:** Combined indicator used in the dashboard.

**Formula:** MOMDisplay(CurrentValue, LastMonthValue)

**Purpose:** Creates a clean, executive friendly MoM label.

### 5. KPI Selection Rationale
The KPIs included in the dashboard were chosen because they:

Reflect core business performance

Support spend efficiency analysis

Highlight seasonal trends

Enable channel‑level comparison

Provide actionable insights for marketing decisions

KPIs like Profit and ROI reveal the imbalance between Spend and Revenue, while Exit Clicks and CPC show traffic efficiency.

### 6. Summary
The KPIs defined in this document form the analytical backbone of the FAVI Performance Dashboard.
They provide a balanced view of:

Investment

Traffic

Revenue

Efficiency

Month‑over‑month performance

Together, they enable a clear and actionable understanding of FAVI’s marketing performance.
