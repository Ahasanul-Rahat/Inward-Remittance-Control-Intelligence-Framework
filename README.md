# Inward-Remittance-Control-Intelligence-Framework
Module 1 — Operations SLA &amp; TAT Analytics (Power BI)

# 📊 Project Overview

* This project simulates a real-world banking operations analytics framework focused on Inward Remittance processing, inspired by global bank operations (HSBC-style).

* The objective is to monitor SLA adherence, turnaround time (TAT), operational bottlenecks, and officer performance using a bank-grade Power BI data model with multiple fact tables.


# 🎯 Business Objectives

* Monitor SLA adherence % for inward remittances

* Identify root causes of SLA breaches

* Measure end-to-end and stage-wise TAT

* Detect branch, officer, and process-level inefficiencies

* Enable data-driven operational control, not just reporting

🧱 Data Architecture

🔹 Fact Tables

* Fact_InwardRemittance (~20,000 rows)

* Grain: 1 row = 1 remittance transaction

* Stores end-to-end processing outcome

* Fact_Remittance_ProcessEvents (~87,000 rows)

* Grain: 1 row = 1 processing stage per transaction

* Enables micro-SLA and bottleneck analysis

🔹 Dimension Tables

* Dim_Date — Calendar & time intelligence

* Dim_SLA — SLA definition & targets

* Dim_Branch — Branch & hub/spoke structure

* Dim_OperationsStaff — Ops officers (maker/checker)

* 🔗 Power BI Data Model (Star + Dual Fact)
```
Dim_SLA        Dim_Branch        Dim_Date        Dim_OperationsStaff
   │               │                │                    │
   └───────────────┴────────────┬───┴────────────────────┘
                                 │
                     Fact_InwardRemittance
                                 │
                                 │ (Transaction_ID)
                                 ▼
                  Fact_Remittance_ProcessEvents
```

* Relationship Principles

* All relationships are 1 → many

* Single-direction filtering only

* Multiple date keys handled via active / inactive relationships

* No many-to-many or bidirectional ambiguity

# ⏱️ Key Metrics & KPIs - SLA & TAT

```
| **Metric**               | **Metric**                      |
| ------------------------ | ------------------------------- |
| SLA Adherence %          | Exception Rate %                |
| SLA Breach Count         | Clean vs Exception TAT          |
| Average TAT (Hours)      | Transactions per Officer        |
| P95 TAT                  | Branch-wise SLA %               |
| SLA Target vs Actual     | Avg Stage Duration              |
| Transactions per Officer | Bottleneck Stage Identification |

```

# 🧠 Business Problems Solved
```
1. SLA breaches without transaction volume increase
2. Chronic underperformance of specific branches
3. Exception-driven hidden delays
4. Officer-level performance blind spots
5. Each problem is backed by measures + visuals + drill-down capability.
```

# 📊 Dashboard Design (Module 1)
```
Executive SLA cockpit
Branch SLA heatmap
Officer performance distribution
Stage-wise bottleneck analyzer
Exception impact analysis
Built with Power BI best practices:
KPI cards with thresholds
Cross-filtering
Drill-through
Micro-SLA visibility
```

# 📊 Report (Module 1)
```
Report–1: Executive SLA Performance
```
<img width="1919" height="1019" alt="Screenshot 2026-02-07 203335" src="https://github.com/user-attachments/assets/58a8ec75-2260-4bbf-a532-b88135c7307f" />

