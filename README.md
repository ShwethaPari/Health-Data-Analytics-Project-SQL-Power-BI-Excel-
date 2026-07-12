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

**1. Count and percentage of Female vs. Male patients, with average Obsession Score by gender**
```sql
use health_data;

# -- 1. Count & Pct of F vs M that have OCD & -- Average Obsession Score by Gender

with data as (
    SELECT
        Gender,
        count(`Patient ID`) as patient_count,
        round(avg(`Y-BOCS Score (Obsessions)`),2) as avg_obs_score
    FROM health_data.ocd_patient_dataset
    Group By 1
    Order by 2
)

select
    sum(case when Gender = 'Female' then patient_count else 0 end) as count_female,
    sum(case when Gender = 'Male' then patient_count else 0 end) as count_male,
    round(sum(case when Gender = 'Female' then patient_count else 0 end) / sum(patient_count) * 100, 2) as pct_female,
    round(sum(case when Gender = 'Male' then patient_count else 0 end) / sum(patient_count) * 100, 2) as pct_male
from data;
```

![Query 1 - Gender count and percentage](assets/sql/query1_gender.png)

**2. Count of patients by Ethnicity and their respective average Obsession Score**
```sql
# -- 2. Count of Patients by Ethnicity and their respective Average Obsession Score

select
    Ethnicity,
    count(`Patient ID`) as patient_count,
    avg(`Y-BOCS Score (Obsessions)`) as obs_score
From health_data.ocd_patient_dataset
Group by 1
Order by 2;
```

![Query 2 - Ethnicity breakdown](assets/sql/query2_ethnicity.png)

**3. Count of patients by diagnosis month (time trend)**
```sql
select
    date_format(`OCD Diagnosis Date`, '%Y-%m-01 00:00:00') as month,
    -- `OCD Diagnosis Date`
    count(`Patient ID`) patient_count
from health_data.ocd_patient_dataset
group by 1
Order by 1;
```

![Query 3 - Diagnosis trend by month](assets/sql/query3_monthly_trend.png)

**4. Most common Obsession Type (count) and its average Obsession Score**
```sql
# -- 4. What is the most common Obsession Type (Count) & it's respective Average Obsession Score

Select
    `Obsession Type`,
    count(`Patient ID`) as patient_count,
    round(avg(`Y-BOCS Score (Obsessions)`),2) as obs_score
from health_data.ocd_patient_dataset
group by 1
Order by 2;
```

![Query 4 - Obsession type breakdown](assets/sql/query4_obsession_type.png)

**5. Most common Compulsion Type (count) and its average Obsession Score**
```sql
# -- 5. What is the most common Compulsion type (Count) & it's respective Average Obsession Score

Select
    `Compulsion Type`,
    count(`Patient ID`) as patient_count,
    round(avg(`Y-BOCS Score (Obsessions)`),2) as obs_score
from health_data.ocd_patient_dataset
group by 1
Order by 2;
```

![Query 5 - Compulsion type breakdown](assets/sql/query5_compulsion_type.png)

### Power BI Dashboard
- Sum of patient count by month (2014–2022 trend line)
- Sum of patient count by Gender (donut chart)
- Sum of patient count by Ethnicity (bar chart)
- Sum of patient count by Compulsion Type (bar chart)
- Obsession count against average Obsession Score by Obsession Type

  ![Query 2 - Ethnicity breakdown](assets/sql/query2_ethnicity.png)

### Excel Dashboard
- Compulsion Type distribution (bar chart)
- Ethnicity distribution (column chart)
- Obsession Type distribution (column chart)
- Gender split (pie chart)
- Diagnosis month-over-month trend (line chart, Nov 2013 – Nov 2022)

  ![Query 2 - Ethnicity breakdown](assets/sql/query2_ethnicity.png)

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

---

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

**Summary Insight:** The dashboard reinforces that this OCD patient population is demographically balanced (gender and ethnicity), while clinically, harm-related obsessions and washing/counting compulsions are the most prevalent presentations. Diagnosis volume has stayed relatively steady over nearly a decade with no major long-term trend, indicating consistent (rather than growing or shrinking) patient intake over time.

---

### Health Analytics Dashboard (Power BI)

**1. Patient Count Trend by Month**
- Monthly diagnosis counts fluctuate consistently between roughly 5 and 20+ patients across the full 2014–2022 period, with no sustained long-term upward or downward trend.
- The pattern is cyclical and noisy rather than seasonal — sharp month-to-month spikes and dips repeat throughout the whole timeframe, pointing to steady, ongoing patient intake rather than accelerating or declining case volume.
- There's a visible dip right at the very end of the series (late 2022), though this likely reflects incomplete data for the most recent period rather than an actual drop in diagnoses.

**2. Gender Distribution**
- The patient base is almost perfectly split by gender: 753 Male (50.2%) vs. 747 Female (49.8%) — confirming no meaningful gender skew in this OCD population.

**3. Ethnicity Breakdown**
- Caucasian patients form the largest group (~398), followed closely by Hispanic (~392) and Asian (~386).
- African patients are the smallest group (~324) — noticeably lower than the other three, which are all clustered close together near 390–400.

**4. Compulsion Type**
- Washing is the most common compulsion type (~320 patients), followed by Counting (~316).
- Checking (~292), Praying (~286), and Ordering (~285) are all less common and fairly close to one another.
- The overall spread shows a gradual decline from Washing down to Ordering rather than one dominant outlier.

**5. Obsession Type vs. Average Obsession Score**
- Ranked by patient count, Harm-related obsessions are the most common, followed by Contamination, Religious, Symmetry, and Hoarding (least common).
- The average obsession score line stays relatively flat and low across all obsession types, indicating that obsession severity doesn't vary much by type — the differences between obsession types are driven mainly by how common they are, not by how severe they tend to be.

**Summary Insight:** This dashboard confirms the OCD patient population is demographically balanced by gender, with only African patients under-represented relative to other ethnic groups. Clinically, Washing and Counting are the dominant compulsions, and Harm-related obsessions are the most frequent presentation, while obsession severity scores stay fairly consistent regardless of type — suggesting prevalence, not severity, is what differentiates these categories. Diagnosis volume has remained steady over nearly a decade with no major structural trend.

## ✅ Highlights Across All Three Tools

- **Gender** is almost perfectly balanced: 753 Male (50.2%) vs. 747 Female (49.8%), consistent across SQL, Power BI, and Excel.
- **Ethnicity** distribution differs slightly by source: the SQL query and Excel dashboard show all four ethnic groups fairly close together, while the Power BI dashboard shows African patients clearly under-represented relative to Caucasian, Hispanic, and Asian — worth reconciling before reporting a single figure.
- **Washing** and **Counting** are the most common compulsion types, consistently across all three views, while Ordering and Praying are the least common.
- **Harm-related obsessions** are the most common obsession type, but **Hoarding** (least common) is tied to the highest average obsession severity score in the SQL analysis — indicating frequency and severity don't move together.
- **Diagnosis volume** has stayed relatively steady over time (2013/2014–2022), fluctuating cyclically month to month with no clear long-term upward or downward trend, aside from a possible data-completeness dip at the very end of the series.
