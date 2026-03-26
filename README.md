
````markdown
# 📊 MLS Character Data Analytics & Quality Assurance

Understanding structured data is critical in real estate technology and MLS operations.  

This project simulates a **real-world MLS data workflow** using a fictional character dataset,
covering **data ingestion, API fetching, cleaning, SQL analysis, and interactive visualization**.

---

## 🎯 Project Objective
To demonstrate **end-to-end data management and analytics**, simulating MLS operations:

- Fetch structured data from an API and clean it in Python.  
- Store and normalize data in PostgreSQL.  
- Perform SQL-based exploratory analysis and generate key metrics.  
- Build an interactive dashboard using Streamlit for visualization and decision-making.  
- Highlight **data quality, normalization, and insights extraction**, applicable to real estate data pipelines.

---

## 🔍 Project Workflow (Step-by-Step)

### 1️⃣ Python API Data Fetching & Cleaning
- Used Python to fetch data from a REST API endpoint (simulating MLS/RETS/RESO feeds).  
- Converted nested JSON data into a **flat Pandas DataFrame** with fields: `id`, `first_name`, `middle_name`, `last_name`, `age`, `gender`, `species`, `homePlanet`, `occupation`, `image_url`.  
- Cleaned and normalized data:  
  - Converted ages to float.  
  - Standardized gender and species categories.  
  - Split nested fields into separate columns.  
  - Handled missing values and duplicates.  

![Python Data Cleaning Example](https://github.com/Abdulrasheed055/MLS-Character-Data-Analytics-Quality-Assurance)
![Python Data Cleaning Example](https://github.com/Abdulrasheed055/MLS-Character-Data-Analytics-Quality-Assurance)
---

### 2️⃣ Data Storage in PostgreSQL
- Created PostgreSQL database `mls_project` and table `characters` for structured data.  
```sql
CREATE DATABASE mls_project;

CREATE TABLE characters (
    id INTEGER PRIMARY KEY,
    first_name TEXT,
    middle_name TEXT,
    last_name TEXT,
    age FLOAT,
    gender TEXT,
    species TEXT,
    homeplanet TEXT,
    occupation TEXT,
    image_url TEXT
);
````

* Inserted cleaned data from Python into PostgreSQL for **SQL analysis**.

---

### 3️⃣ SQL Analysis

Performed key aggregations and insights extraction.

#### Total Records

```sql
SELECT COUNT(*) AS total_records FROM characters;
```

**Result:** 15

#### Gender Distribution

```sql
SELECT gender, COUNT(*) 
FROM characters 
GROUP BY gender;
```

* Male: 11
* Female: 4

#### Species Distribution

```sql
SELECT species, COUNT(*) 
FROM characters 
GROUP BY species;
```

* Human: 9
* Mutant: 1
* Robot: 1
* Martian: 1
* Decapodian: 1
* Omicronian: 1
* Amphibiosans: 1

#### Average Age by Species

```sql
SELECT species, ROUND(AVG(age), 2) AS avg_age
FROM characters
GROUP BY species
ORDER BY avg_age DESC;
```

* Highest avg_age: Human (53.14)
* Lowest avg_age: Others (25–40 range)

#### Maximum Age

```sql
SELECT MAX(age) AS max_age FROM characters;
```

* **Max Age:** 210

#### Oldest Character

```sql
SELECT first_name, last_name, age
FROM characters
ORDER BY age DESC
LIMIT 1;
```

* **Hubert Farnsworth, Age 210**

---

### 4️⃣ Streamlit Dashboard

* Built an **interactive dashboard** to explore and filter data.
* Features include:

  * Filters for **Gender** and **Species**
  * **Gender & Species Distribution** bar charts
  * **Average Age by Species** chart
  * Key metrics: Total Records, Average Age, Max Age

![Streamlit Dashboard Example](https://raw.githubusercontent.com/YourUsername/YourRepo/main/streamlit_dashboard.png)

---

## 📈 Key Insights

* **Total Dataset:** 15 records
* **Gender Balance:** Male 73%, Female 27%
* **Species Dominance:** Human (60%), others evenly distributed
* **Average Age:** 53.14
* **Maximum Age:** 210 (fictional extremes highlight need for data normalization)
* **Oldest Character:** Hubert Farnsworth

> Insights demonstrate importance of **data validation, normalization, and QA**, essential in MLS data pipelines.

---

## 💡 Business / MLS Relevance

* Simulates **MLS data ingestion & cleaning** from API feeds.
* Demonstrates **structured data validation** and QA processes.
* Supports **ETL workflows** by maintaining clean, usable datasets.
* SQL analytics provide **decision-ready metrics** for product and operational teams.
* Streamlit dashboard enables **interactive stakeholder insights** for data-driven decision-making.

---

## 🛠 Tools & Skills Used

* **Data Cleaning & Preprocessing:** Python (Pandas, NumPy)
* **Database & SQL Analysis:** PostgreSQL
* **Dashboarding:** Streamlit
* **Key Techniques:** ETL, Data Normalization, QA Checks, KPI Monitoring, Interactive Visualization

---

## ✅ Achievements / Metrics

* Successfully ingested and cleaned **15 records** from API.
* Standardized **10+ categorical fields** (gender, species, home planet).
* Derived **5+ actionable insights**: gender distribution, species distribution, average age, max age, oldest character.
* Built **interactive Streamlit dashboard** for visualization.
* Simulated **end-to-end MLS data pipeline** workflow: API → Python → SQL → Streamlit.

---

## 🔗 Next Steps / Enhancements

* Integrate **real MLS datasets** (RETS/RESO compliant).
* Expand dashboard with **property-level KPIs** (price trends, location analytics).
* Implement automated **data validation pipelines** for ongoing ETL workflows.
* Add **user authentication** for dashboard access.

```

---

