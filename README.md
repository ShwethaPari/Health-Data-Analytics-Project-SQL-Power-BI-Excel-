# Health Data Analytics: OCD Patient Case Study

![SQL](https://shields.io)
![Power BI](https://shields.io)
![Excel](https://shields.io)

## 📋 Overview

This repository contains an end-to-end health data analytics case study focused on an **OCD (Obsessive-Compulsive Disorder) patient dataset**. The primary objective was to investigate patient demographics and clinical patterns—such as gender splits, ethnic distributions, obsession/compulsion varieties, and diagnosis trends over time.

To ensure analytical rigor, the study replicates the same business and clinical questions across **three complementary approaches**:
1. **SQL**: Used for direct database querying, data manipulation, and precise aggregations.
2. **Power BI**: Used to build an interactive dashboard tracking complex clinical relationships.
3. **Excel**: Used to create a lightweight, chart-based secondary dashboard.

### 🎯 Dual Purpose of Cross-Tool Analytics
* **Skill Application**: Practicing identical analytical questions across different environments to test platform-specific methodologies.
* **Cross-Validation**: Cross-checking numerical results between sources to catch data discrepancies and pipeline inconsistencies.

---

## 💾 Dataset Profile

The underlying dataset contains comprehensive clinical histories for individual patients, built around the following key fields:
* `Patient ID`: Unique identifier for each individual.
* `Gender`: Demographic classification (Male/Female).
* `Ethnicity`: Demographic groups (Caucasian, Hispanic, Asian, African).
* `OCD Diagnosis Date`: The timeline marker for case registration.
* `Obsession Type`: Clinical manifestation (Harm, Contamination, Hoarding, etc.).
* `Compulsion Type`: Behavioral manifestation (Washing, Counting, Checking, etc.).
* `Y-BOCS Score (Obsessions)`: Yale-Brown Obsessive Compulsive Scale rating severity.

---

## 🛠️ Tools & Purpose

| Tool | Purpose |
| :--- | :--- |
| **SQL (MySQL Workbench)** | High-performance querying, conditional logic pivoting, and raw dataset aggregation. |
| **Power BI Desktop** | Dynamic data modeling and interactive visual discovery of patient profiles. |
| **Microsoft Excel** | Fast pivot tables, static reporting, and lightweight multi-chart dashboard replication. |

---

## 🔄 Project Walkthrough & Process
1. **Data Preparation**
   * Migrated the raw OCD dataset into a local MySQL instance under `health_data.ocd_patient_dataset`.
   * Verified data types, missing schemas, and structural integrity of the columns.

2. **SQL Engineering**
   * Structured dedicated query blocks isolated by clinical business questions.
   * Utilized `GROUP BY`, `COUNT()`, `AVG()`, and `ROUND()` for mathematical precision.
   * Developed conditional `CASE WHEN` logic to pivot and compute gender distributions into percentages.
   * Implemented `DATE_FORMAT()` to bucket timelines into monthly granularities.

3. **Power BI Dashboard Build**
   * Established a direct connection to the underlying health database.
   * Configured 5 primary visual planes: A monthly patient-count trend line (2014–2022), a gender donut chart, an ethnicity bar chart, a compulsion-type bar chart, and a dual-axis combo chart mapping obsession types against average obsession scores.

4. **Excel Replay**
   * Configured an alternative, nimble reporting ecosystem replicating the main visuals (compulsion, ethnicity, obsession, gender, and a 9-year MoM trend line from Nov 2013 to Nov 2022).

5. **Cross-Validation Auditing**
   * Audit checks were systematically completed across all three output layers.
   * **Discrepancy Flagged**: Identified an ethnic distribution variance unique to the Power BI visual layer when cross-examined against SQL and Excel queries. This was preserved and flagged for systemic data pipeline debugging rather than silently manipulated.

6. **Synthesis**
   * Aggregated separate tool-specific outputs into a unified master report to evaluate where metrics aligned or diverged.

---

## 📊 Analytical Scope

### 💻 SQL Operations
* Total count, percent split, and average Y-BOCS score broken down by **Gender**.
* Volume tracking and average Y-BOCS obsession rating segmented by **Ethnicity**.
* Time-series trend analysis parsing patient volumes by **Diagnosis Month**.
* Frequency analysis evaluating the most prevalent **Obsession Types** vs. severity metrics.
* Frequency analysis evaluating the most prevalent **Compulsion Types** vs. severity metrics.

### 💛 Power BI Design
* 2014–2022 timeline tracking total patient counts.
* Demographic distribution via Gender (Donut Chart) and Ethnicity (Bar Chart).
* Behavioral distribution via Compulsion Type (Bar Chart).
* Bivariate relationships pairing obsession counts directly against Y-BOCS average severities.

### 🟢 Excel Architecture
* Horizontal Bar Chart tracking Compulsion Type volumes.
* Column Charts visualizing Ethnicity and Obsession Type breakdowns.
* 50/50 visual split representation via Gender Pie Chart.
* Full historical timeline Line Chart tracking 9 years of MoM intake (Nov 2013 – Nov 2022).

---

## 📈 Key Clinical & Analytical Findings

### 🧬 1. Demographic Integrity (Gender & Ethnicity)
* **Gender Neutrality**: The dataset displays an almost perfectly uniform gender split: **753 Male patients (50.2%)** vs. **747 Female patients (49.8%)**. This uniform distribution highlights a variance from traditional, skewed real-world clinical datasets.
* **Ethnic Parity**: Intake populations remain highly distributed across tracked segments: Caucasian (398), Hispanic (392), Asian (386), and African (324). 
* **Severity Equity**: Average Y-BOCS obsession scores remain narrow and tightly bounded between **19.76** (African) and **20.32** (Asian), demonstrating that clinical severity has no statistical variance across ethnic lines within this group.

### 🧠 2. Clinical Manifestations (Obsessions vs. Compulsions)
* **The Frequency-Severity Disconnect**:
  * **Harm-related** obsessions are the most frequent (**333 patients**), yet **Hoarding**—the rarest obsession variant (278 patients)—yielded the highest clinical severity score (**21.01**).
  * **Washing** is the most widely documented compulsion variant (**321 patients**), yet it correlates with the lowest overall Y-BOCS obsession score (**19.40**). Conversely, **Counting** behaviors (**316 patients**) recorded the highest average severity score (**20.41**).
* **Strategic Takeaway**: Frequency does not equal severity. While clinical workloads may be dominated by Harm obsessions and Washing compulsions, patients exhibiting Hoarding or Counting behaviors present higher clinical severity risks requiring prioritized treatment allocation.

### 📅 3. Intake & Timeline Trends
* **Historical Run-Run**: Over the long-range timeline (Nov 2013 – Nov 2022), monthly intake numbers consistently fluctuated inside a noisy but stable operational band between **5 and 30 patients per month**.
* **Trend Absence**: The time-series lacks seasonal spikes or structural upward/downward vectors. It behaves as a cyclical, steady-state intake stream rather than an accelerating epidemic curve.
* **End-of-Series Drop**: A minor decline appears near the tail-end of late 2022, indicating a classic data collection latency or incomplete reporting window rather than an actual clinical drop-off.

---

## 🏁 Summary Insight

This project successfully proves the analytical power of multi-tool cross-validation. The demographics show a balanced population free of systemic biases. Clinically, it provides actionable data for hospital resource planning: while volume is driven by common harm-related thoughts and washing behaviors, medical priority and intensive care resources should be directed toward hoarding and counting cases due to their higher clinical severity.

---

## 🛠️ Usage Instructions

### Running the Queries
To execute the backend data definitions and analytical queries, run the scripts found in the `/sql` directory inside your database environment:
```bash
mysql -u your_username -p health_data < sql/analysis_queries.sql
```

### Viewing Dashboards
* **Power BI**: Download and open the `.pbix` file in the `/dashboards` directory using Power BI Desktop.
