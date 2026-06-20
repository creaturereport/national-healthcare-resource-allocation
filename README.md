# National Healthcare Resource Allocation
**Data Analyst:** Symone Thompson  
**Client/Sponsor:** National Maternal Health Organization  

---

## 🎯 Purpose
The purpose of this project is to address critical resource and staffing shortages in high-volume maternal healthcare facilities across the United States. Recent public health data reflects significant regional fluctuations in annual birth rates, leading to operational bottlenecks in localized hospitals. By analyzing historical CDC natality logs and birth metrics, this project will isolate the precise geographic regions experiencing the highest density of total births. This analysis will provide public health development and logistics teams with actionable insights to optimally allocate specialized medical staff, target prenatal funding, and protect patient care quality.

---

## 🚫 Out of Scope (Project Exclusions)
* **Total County Populations:** This analysis strictly measures raw birth volumes (`Births`) rather than calculating per capita birth rates against the total population of each county.
* **Gender Distinctions:** The scope isolates total infant delivery counts without filtering or segregating data based on the sex assigned at birth.
* **Stillborn and Mortality Metrics:** The dataset exclusively records live natality events; fetal deaths, stillbirths, and infant mortality tracking are completely excluded from this scope.

---

## 📦 Deliverables
* **SQL Data Sorting Script:** A clean, production-ready, and well-commented `.sql` script demonstrating data ingestion, schema validation, and descending sorting parameters using BigQuery standard SQL syntax.
* **Analytical Dashboard:** A highly visual dashboard focusing on regional birth concentrations across the major US geographic sectors (Northeast, South, Midwest, and West) to easily identify regional spikes and distribution anomalies.
* **Executive Summary Report:** A brief presentation deck translating the top 10 high-priority county findings into clear resource allocation recommendations for healthcare stakeholders.

---

## 🗓️ Schedule Overview & Project Milestones
*Project execution is structured across highly focused technical milestones.*

* **Phase 1: Ingestion & Validation** | Access the BigQuery console sandbox environment, connect to the CDC natality dataset, and audit the table schemas to ensure column metric alignment.
* **Phase 2: SQL Development** | Draft, test, and execute the standard SQL sorting syntax using `ORDER BY DESC` constraints to finalize the high-volume target data frame.
* **Phase 3: Visualization & Closure** | Synthesize query findings into the analytical dashboard format and deploy finalized code assets directly to GitHub.

---

## 🎯 Estimated Completion & The Analytical Imperative
Final delivery, asset deployment, and repository verification are scheduled for completion ahead of target milestones.

**The Analytical Imperative:**  
In healthcare logistics, data is directly tied to human outcomes. This analysis transcends simple numbers on a screen; by uncovering a clear, year-over-year baseline in high-volume sectors like Los Angeles County, it provides decision-makers with the proactive runway required to shift medical funding, optimize hospital bed capacities, and ensure that maternal care resources are precisely deployed *before* local medical infrastructure faces critical bottlenecks. True data maturity turns historical logs into protective, life-saving strategies.

----------------------------------------------------------------
*   **The Insight:** Verified core columns including `Year`, `County_of_Residence`, and `Births`, ensuring the data types were correct and ready for aggregation.

#### **Scenario 1: Baseline Structural Audit (Unsorted Exploration)**
*   **Objective:** Ingest the raw CDC births data to understand the underlying table schema and row layout without manipulating the record distribution.
*   **The SQL Logic:**
```sql
SELECT 
* -- select all columns to audit the schema
FROM 
`bigquery-public-data.sdoh_cdc_wonder_natality.county_natality` -- targeting the core natality table
LIMIT 
1000 -- limiting rows for initial structural inspection
```

----------------------------------------------------------------
*   **The Insight:** Verified core columns including `Year`, `County_of_Residence`, and `Births`, ensuring the data types were correct and ready for aggregation.

#### **Scenario 2: Low-Volume Regional Identification (Default Ascending)**
*   **Objective:** Observe the default sorting behavior of the workspace to identify the areas with the absolute lowest volume of live births.
*   **The SQL Logic:**
```sql
SELECT
*
FROM
`bigquery-public-data.sdoh_cdc_wonder_natality.county_natality`
ORDER BY
Births -- defaulting to ascending order (smallest to largest)
LIMIT
10
```
-----------------------------------------------
*   **The Critical Finding:** Uncovered that Los Angeles County, CA holds the highest volume in the dataset (surpassing 123,000 births in 2016). More importantly, identified a visible year-over-year *decline* in births within that exact hotspot from 2016 down to 2018, proving a shifting trend that requires proactive medical funding adjustments.

#### **Scenario 3: High-Priority Hotspot Isolation (Descending Target)**
*   **Objective:** Rearrange the dataset to instantly surface the highest-volume birth regions in the United States to address the client's primary staffing and resource allocation bottleneck.
*   **The SQL Logic:**
  ```sql
SELECT 
* 
FROM 
`bigquery-public-data.sdoh_cdc_wonder_natality.county_natality`
ORDER BY 
Births DESC -- forcing the largest delivery counts to the top
LIMIT 
10 -- isolating the top 10 highest-volume targets
```
---


