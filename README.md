# Uncovering Profitability: A Power BI Case Study

**Turning raw business data into actionable profit: uncovering $724K in hidden value with executive dashboards and sharp analytics.**

---

## Table of Contents

- [Quick Highlights](#quick-highlights)
- [Project Overview](#project-overview)
- [Methodology & Phases](#methodology--phases)
  - [1. Data Engineering & Cleaning (ETL)](#1-data-engineering--cleaning-etl)
  - [2. Data Modeling & Validation](#2-data-modeling--validation)
  - [3. Strategic Storytelling & Visualization](#3-strategic-storytelling--visualization)
- [Key Insights & Results](#key-insights--results)
- [Technical Implementation Examples](#technical-implementation-examples)
- [Technical Skills Demonstrated](#technical-skills-demonstrated)
- [Dashboard Previews](#dashboard-previews)
- [Testimonials](#testimonials)
- [Conclusion & Learnings](#conclusion--learnings)
- [Contact](#contact)

---

## Quick Highlights

- 💡 **Uncovered $724K profit & $283K in recoverable losses**
- 🔗 **Built end-to-end data pipeline:** Excel → SQL → Power BI
- 📊 **Designed interactive, executive-level dashboards**
- 🛠️ **Tools:** SQL, DAX, Power Query, Power BI, Excel
- ⭐ **Endorsed by global clients & business leaders**

---

## Why Hire Me?

As a data analyst, I bridge the gap between complex data and business action. I pinpoint profit opportunities, flag risks, and deliver insights executives use to make smarter, faster decisions. My work transforms “just data” into real business impact—every time.

---

## Project Overview

This project demonstrates a rigorous, end-to-end analytics workflow—from raw Excel exports to polished, interactive Power BI dashboards. My analysis surfaced the company’s true profitability, challenged legacy KPIs, and equipped leadership with actionable, C-level recommendations.

**Outcome:**
- Identified $724K profit from $1.07M revenue
- Pinpointed $283K in avoidable client losses
- Delivered clear, data-backed recommendations for portfolio review

---

## Methodology & Phases

### 1. Data Engineering & Cleaning (ETL)
- **Extraction & Loading:** Raw Excel data → SQL database
- **Date Normalization:** Converted NVARCHAR dates to DATE (`TRY_CAST(TRIM(...))`) for reliable time-series analytics
- **Anomaly Resolution:**  
  - Systematic removal of legacy “phantom” employee ID (005Un000002ZnXnIAK) across 4 tables
  - Imputed missing service type and country fields, flagged for audit

### 2. Data Modeling & Validation
- **Star Schema Design:** Linked INVOICE_CUSTOMER, INVOICE_EMPLOYEE, TIME_ENTRIES in Power BI for robust, scalable analysis
- **Custom Metrics:** Built DAX measures for unseen metrics (Profit, Total Revenue)
- **Assumption Testing:** Exploratory analysis disproved revenue-hour correlation; profit redefined as true KPI

### 3. Strategic Storytelling & Visualization
- **Executive Dashboard Flow:** High-level summary → granular workforce & financial drilldowns
- **Actionable Insights:** Highlighted loss-driving clients (BookNook, ecofi) and projects (Audaces), with recommendations
- **Transparent Anomaly Reporting:** Surfaced issues (e.g., Jorge Ramirez’s –$30,839 profit) for business action

---

## Key Insights & Results

- **Strong Profitability:**  
  - **$724K** in profit  
  - **$1.07M** in total revenue
- **Client Losses:**  
  - BookNook (**–$149K**)  
  - ecofi (**–$134K**)
- **Top Performer:**  
  - Axel Chaves (**$557K** profit)
- **Anomaly Detection:**  
  - Jorge Ramirez logged **–$30,839** profit for 1 hour—flagged for review
- **Payroll Hotspots:**  
  - Costa Rica (**$193K**) and Argentina (**$54K**)
- **Business Model Shift:**  
  - Profit, not hours, is the decisive metric for performance

---

## Technical Implementation Examples

### 1. SQL for Data Cleaning & Aggregation

This query joins time entry data with customer data to audit unassigned labor costs, ensuring no relevant data is ignored:

```sql
-- Join time entries with client info to audit unassigned labor costs
SELECT
    TE.employee_id,
    TE.time_worked,
    IC.client_name,
    -- Use CASE to flag unassigned efforts
    CASE
        WHEN IC.client_name IS NULL THEN '⚠️  Unassigned client effort'
        ELSE '✓ Assigned to client'
    END AS audit_flag
FROM
    dbo.TIME_ENTRIES AS TE
LEFT JOIN
    dbo.INVOICE_CUSTOMER AS IC
ON
    TE.customer_id = IC.customer_id;
```

---

### 2. DAX for Key Performance Indicators (KPIs)

This DAX measure defines Profit, enabling precise business analysis beyond raw transactional data:

```DAX
Profit = 
VAR TotalRevenue = SUM('INVOICE_CUSTOMER'[INVOICE_AMOUNT])
VAR TotalPayroll = SUM('INVOICE_EMPLOYEE'[PAYROLL_COST])
RETURN
    TotalRevenue - TotalPayroll
```

---

### 3. Power Query (M Language) for Data Transformation

A key transformation step to standardize date formats for reliable time-series analysis:

```m
let
    Source = Csv.Document(...),
    #"Changed Type" = Table.TransformColumnTypes(Source,{
        {"Date", type datetime},
        {"Employee ID", type text}
        // ... other columns
    }),
    #"Standardized Dates" = Table.TransformColumns(
        #"Changed Type", {{"Date", DateTime.Date}}
    )
in
    #"Standardized Dates"
```

---

## Technical Skills Demonstrated

| Tool         | Use Case                       |
|--------------|-------------------------------|
| **SQL**      | Data extraction, cleaning      |
| **Power Query** | Data transformation        |
| **Power BI** | Data modeling, visualization   |
| **DAX**      | KPI, metric calculation        |
| **Excel**    | Initial data source            |

- **Data Extraction & ETL:** End-to-end pipeline from Excel to SQL
- **Data Modeling:** Star schema, relationship design in Power BI
- **DAX & Power Query:** Advanced metric calculation and transformation
- **Data Visualization:** Interactive dashboards for C-level review
- **Anomaly & Outlier Detection:** Proactive quality control

---

## Dashboard Previews

### Executive Summary  
Key KPIs, profit leaders, and loss-driving clients.  
![Executive Dashboard](https://github.com/user-attachments/assets/495b501a-cfba-4233-aa02-bae172928999)

### Workforce Insights  
Employee performance, payroll breakdown, and anomaly flags.
<img width="1429" height="803" alt="Captura de pantalla 2025-08-01 002239" src="https://github.com/user-attachments/assets/ec57aff1-bd85-45d8-b6eb-caeaf53af64a" />

### Finance Deep Dive  
Detailed financial analytics, scatter plot disproving revenue-hour link, and loss-making projects.  
![Finance Deep Dive](https://github.com/user-attachments/assets/9de90c1b-2944-4133-910a-259aed629c67)

---

## Testimonials

> ⭐⭐⭐⭐⭐ “Laura was super efficient!!! Her communication was excellent. Her professionalism, her ability to understand the job and the extra mile she goes to exceed the expectations of the client is truly remarkable!!! We are looking forward to doing a lot more work with her.”  
> — Shanil, Tourism Manager (Australia)

> ⭐⭐⭐⭐⭐ “I really enjoyed working with Laura, she is very responsible and has a very good way of working. Recommended 100%”  
> — Josue Viera, CEO & Founder, SocialLit (Chile)

> ⭐⭐⭐⭐⭐ “I had to ask her to create a dashboard to be delivered in 24 hours, and she did it very satisfactorily. At all times, she kept in communication, showed progress, explained every procedure, and made requested modifications with no problem—always professional and respectful. I absolutely recommend her!”  
> — Fluchtenberg, Web Developer, Fiverr (Argentina)
- [Source](https://es.fiverr.com/laura155555?public_mode=true)
---

## Conclusion & Learnings

This project proves that rigorous data validation and a critical mindset can shatter assumptions and reveal the true drivers of business success. By redefining KPIs and building actionable dashboards, I empowered leadership to make data-driven, profitable decisions.

---

## Contact

**Ready to help your company turn data into profit—remotely, from day one. Let’s connect!**  
- [LinkedIn](https://www.linkedin.com/in/laura-m-3a878b212/)  - [Email](mailto:lauminagui@gmail.com)  - [GitHub](https://github.com/lauraminayaa)
---

**Authorized to work from Peru. Fluent in English & Spanish. Available for remote data analyst roles.**

---
