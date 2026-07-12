# 🏥 Health Data Analytics Project (SQL + Power BI + Excel)

## 📋 Overview
This project is a health analytics case study built around an OCD (Obsessive-Compulsive Disorder) patient dataset. The goal was to explore patient demographics and clinical patterns — gender, ethnicity, obsession types, compulsion types, and diagnosis trends over time — using three complementary approaches: **SQL** for direct querying and aggregation, and **Power BI** and **Excel** for interactive/visual dashboard reporting on the same underlying data.

Using three tools on one dataset served two purposes: practicing the same analytical questions across different platforms, and cross-checking results between sources to catch inconsistencies.

## 🗂️ Dataset
**Key fields:** Patient ID, Gender, Ethnicity, OCD Diagnosis Date, Obsession Type, Compulsion Type, Y-BOCS Score (Obsessions)

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| SQL (MySQL Workbench) | Querying, aggregating, and analyzing the raw patient dataset |
| Power BI | Interactive dashboard for visualizing demographics and clinical patterns |
| Excel | Secondary dashboard/chart-based reporting view of the same dataset |

## 🔄 Process

1. **Data Preparation**
   - Loaded the OCD patient dataset into a MySQL database as `health_data.ocd_patient_dataset`
   - Confirmed key fields: Patient ID, Gender, Ethnicity, OCD Diagnosis Date, Obsession Type, Compulsion Type, Y-BOCS Score (Obsessions)

2. **SQL Analysis**
   - Wrote a series of query blocks, each targeting one specific business/clinical question
   - Used `GROUP BY`, `COUNT()`, `AVG()`, `ROUND()`, and `CASE WHEN` logic to pivot gender counts into percentages
   - Used `DATE_FORMAT()` to bucket diagnosis dates into monthly periods for trend analysis
   - Ordered and grouped results to identify most/least common categories at a glance

3. **Power BI Dashboard Build**
   - Connected Power BI to the same dataset
   - Built five visuals: a monthly patient-count trend line, a gender donut chart, an ethnicity bar chart, a compulsion-type bar chart, and a combo chart comparing obsession type counts against average obsession score

4. **Excel Dashboard Build**
   - Replicated a similar set of visuals in Excel (compulsion type, ethnicity, obsession type, gender, and a diagnosis month-over-month trend line) as a lightweight alternative to the Power BI dashboard

5. **Cross-Validation**
   - Compared results across all three tools for the same metrics (e.g., gender split, ethnicity counts)
   - Identified a discrepancy in ethnicity distribution between the Power BI view and the SQL/Excel views, flagged for follow-up rather than silently resolved

6. **Synthesis**
   - Compiled findings from each tool into separate findings documents, then combined them into a single overview to highlight where all three sources agree and where they diverge

---

## 💻 SQL Code & Queries

Below are the SQL scripts executed in MySQL Workbench to extract the clinical and demographic insights.

### 1. Gender Demographics & Severity
```sql
-- Insert your SQL query for gender count, percentages, and average Y-BOCS scores here
```

### 2. Ethnic Distribution & Severity
```sql
-- Insert your SQL query for patient counts and average obsession scores by ethnicity here
```

### 3. Diagnosis Timeline Trends
```sql
-- Insert your SQL query for patient volume bucketed by diagnosis month here
```

### 4. Obsession Type Prevalence & Severity
```sql
-- Insert your SQL query ranking obsession types by frequency and average score here
```

### 5. Compulsion Type Prevalence & Severity
```sql
-- Insert your SQL query ranking compulsion types by frequency and average score here
```

---

## 📊 Dashboards & Visualizations





hi
Hello! How can I help you today?
If you are looking for assistance, please let me know:
What topic you want to discuss
Any specific questions you have
How I can best assist you
Let me know what you need, and we can get started!




Give me the space for the image and also for the code 

# 🏥 Health Data Analytics Project (SQL + Power BI + Excel)

## 📋 Overview

This project is a health analytics case study built around an OCD (Obsessive-Compulsive Disorder) patient dataset. The goal was to explore patient demographics and clinical patterns — gender, ethnicity, obsession types, compulsion types, and diagnosis trends over time — using three complementary approaches: **SQL** for direct querying and aggregation, and **Power BI** and **Excel** for interactive/visual dashboard reporting on the same underlying data.

Using three tools on one dataset served two purposes: practicing the same analytical questions across different platforms, and cross-checking results between sources to catch inconsistencies.

## 🗂️ Dataset

**Key fields:** Patient ID, Gender, Ethnicity, OCD Diagnosis Date, Obsession Type, Compulsion Type, Y-BOCS Score (Obsessions)

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| SQL (MySQL Workbench) | Querying, aggregating, and analyzing the raw patient dataset |
| Power BI | Interactive dashboard for visualizing demographics and clinical patterns |
| Excel | Secondary dashboard/chart-based reporting view of the same dataset |

## 🔄 Process

1. **Data Preparation**
   - Loaded the OCD patient dataset into a MySQL database as `health_data.ocd_patient_dataset`
   - Confirmed key fields: Patient ID, Gender, Ethnicity, OCD Diagnosis Date, Obsession Type, Compulsion Type, Y-BOCS Score (Obsessions)

2. **SQL Analysis**
   - Wrote a series of query blocks, each targeting one specific business/clinical question
   - Used `GROUP BY`, `COUNT()`, `AVG()`, `ROUND()`, and `CASE WHEN` logic to pivot gender counts into percentages
   - Used `DATE_FORMAT()` to bucket diagnosis dates into monthly periods for trend analysis
   - Ordered and grouped results to identify most/least common categories at a glance

3. **Power BI Dashboard Build**
   - Connected Power BI to the same dataset
   - Built five visuals: a monthly patient-count trend line, a gender donut chart, an ethnicity bar chart, a compulsion-type bar chart, and a combo chart comparing obsession type counts against average obsession score

4. **Excel Dashboard Build**
   - Replicated a similar set of visuals in Excel (compulsion type, ethnicity, obsession type, gender, and a diagnosis month-over-month trend line) as a lightweight alternative to the Power BI dashboard

5. **Cross-Validation**
   - Compared results across all three tools for the same metrics (e.g., gender split, ethnicity counts)
   - Identified a discrepancy in ethnicity distribution between the Power BI view and the SQL/Excel views, flagged for follow-up rather than silently resolved

6. **Synthesis**
   - Compiled findings from each tool into separate findings documents, then combined them into a single overview to highlight where all three sources agree and where they diverge

## 📊 Analysis Performed

### SQL
1. Count and percentage of Female vs. Male patients, with average Obsession Score by gender
2. Count of patients by Ethnicity and their respective average Obsession Score
3. Count of patients by diagnosis month (time trend)
4. Most common Obsession Type (count) and its average Obsession Score
5. Most common Compulsion Type (count) and its average Obsession Score

### Power BI Dashboard
- Sum of patient count by month (2014–2022 trend line)
- Sum of patient count by Gender (donut chart)
- Sum of patient count by Ethnicity (bar chart)
- Sum of patient count by Compulsion Type (bar chart)
- Obsession count against average Obsession Score by Obsession Type

### Excel Dashboard
- Compulsion Type distribution (bar chart)
- Ethnicity distribution (column chart)
- Obsession Type distribution (column chart)
- Gender split (pie chart)
- Diagnosis month-over-month trend (line chart, Nov 2013 – Nov 2022)

## 🔍 Key Findings

### Health Analytics (SQL)

**1. Gender Distribution**
- The patient population is almost perfectly split by gender: 753 male patients (50.2%) vs. 747 female patients (49.8%).
- This near-even split suggests OCD diagnoses in this dataset are not gender-skewed, unlike some real-world clinical data trends.

**2. Ethnicity Breakdown**
- Patient counts are fairly evenly distributed across ethnic groups: Caucasian (398), Hispanic (392), Asian (386), and African (324).
- Average Y-BOCS Obsession scores are also similar across ethnicities, ranging narrowly from 19.76 (African) to 20.32 (Asian) — indicating obsession severity does not vary meaningfully by ethnicity in this dataset.

**3. Diagnosis Trend Over Time**
- Monthly new-patient diagnosis counts from late 2013 through mid-2014 stayed in a narrow band of roughly 9–15 patients per month, with a slight peak in March 2014 (15 patients).
- No strong seasonal spike is evident in this window — diagnosis volume appears relatively stable month-to-month.

**4. Most Common Obsession Types**
- Harm-related obsessions are the most common (333 patients), followed by Contamination (306) and Compulsion-adjacent counting (316, see below).
- Hoarding, while the least common obsession type (278 patients), has the highest average obsession severity score (21.01) — suggesting that although fewer patients present with hoarding, it tends to be more severe when it occurs.

**5. Most Common Compulsion Types**
- Washing is the most common compulsion type (321 patients), followed closely by Counting (316) and Checking (292).
- Counting compulsions have the highest average obsession score (20.41), while Washing has the lowest (19.40) — meaning the most frequent compulsion (washing) is associated with comparatively milder obsession severity.

**Summary Insight:** This OCD patient population is demographically balanced (gender and ethnicity show no major skew or severity differences), while the clinical patterns are more telling: harm-related obsessions and washing compulsions are most prevalent, but hoarding and counting are linked to higher average obsession severity despite being less common — a useful distinction between frequency and severity for treatment prioritization.

### Health Analytics Dashboard (Excel)

**1. Compulsion Type**
- Washing is the most common compulsion (~320 patients), followed closely by Counting (~316).
- Checking, Praying, and Ordering are less common, each in the 285–292 range.
- The gap between the most and least common compulsion types is relatively narrow, meaning no single compulsion type dominates the patient population.

**2. Ethnicity**
- Patient counts are fairly balanced across ethnic groups, with Caucasian (~398) and Hispanic (~392) slightly ahead of Asian (~386) and African (~324).
- No ethnic group is dramatically over- or under-represented, suggesting a demographically diverse patient base.

**3. Obsession Type**
- Harm-related obsessions are clearly the most common (~333 patients), notably higher than all other types.
- Contamination (~306) and Religious (~303) obsessions are the next most frequent.
- Hoarding (~278) and Symmetry (~280) are the least common obsession types.

**4. Gender**
- The patient base is almost perfectly split by gender — the pie chart shows Female and Male at essentially 50/50, confirming no gender skew in OCD diagnoses within this dataset.

**5. Diagnosis Trend Over Time (Nov 2013 – Nov 2022)**
- Monthly diagnosis counts fluctuate consistently between roughly 5 and 30 patients over the full ~9-year period, with no clear long-term upward or downward trend.
- The pattern is cyclical/noisy rather than seasonal or trending — diagnosis volume rises and falls sharply month to month without a sustained growth pattern, suggesting steady, ongoing intake rather than accelerating case volume.
- A slight decline is visible right at the very end of the series (into late 2022), though this may reflect incomplete data for the most recent period rather than a genuine drop.

**Summary Insight:** The dashboard reinforces that this OCD patient population is demographically balanced (gender and ethnicity), while clinically, harm-related obsessions and washing/counting compulsions are the most prevalent presentations.
