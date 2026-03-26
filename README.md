````markdown
# 📊 MLS Character Data Analytics & Quality Assurance

Understanding and maintaining structured data is essential in real estate technology and MLS operations.  

This project focuses on data ingestion, validation, normalization, and analytics of a fictional character dataset, simulating real-world MLS data processes.

---

## 🎯 Project Aim
To answer the key business question:  
*"How can structured character/MLS data be ingested, cleaned, validated, and analyzed to generate actionable insights and maintain high data quality standards?"*

---

## 🔍 Process (Step-by-Step)

### 1️⃣ Data Ingestion & Database Setup
- Created PostgreSQL database `mls_project` to store structured data.  
```sql
CREATE DATABASE mls_project;
\c mls_project;
````

* Defined structured table `characters` with fields for ID, name, age, gender, species, home planet, occupation, and image URL.

```sql
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
```

---

### 2️⃣ Data Cleaning & Normalization

* Processed **15 character records** to remove missing or inconsistent values.
* Standardized **gender and species categories** to ensure consistency.
* Converted age values to **FLOAT**, verified text fields, and normalized names (`first_name`, `last_name`).
* Eliminated duplicates and ensured all key fields were non-null.

---

### 3️⃣ Data Validation

* Ensured no missing `id`, `first_name`, `last_name`, or `age` values.
* Verified categorical consistency for `gender` (Male/Female) and `species` (Human, Robot, Mutant, Martian, etc.).
* Confirmed dataset reliability for SQL analysis and reporting.

---

### 4️⃣ SQL Analysis

#### Total Records

```sql
SELECT COUNT(*) AS total_records FROM characters;
```

**Result:** 15 records

#### Gender Distribution

```sql
SELECT gender, COUNT(*) 
FROM characters 
GROUP BY gender;
```

**Result:**

* Male: 11 (73%)
* Female: 4 (27%)

#### Species Distribution

```sql
SELECT species, COUNT(*) 
FROM characters 
GROUP BY species;
```

**Result:**

* Human: 9 (60%)
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

**Results:**

* Highest avg_age: Human (53.14)
* Lowest avg_age: Other species (25–40 range)

#### Maximum Age

```sql
SELECT MAX(age) AS max_age FROM characters;
```

**Result:** 210

#### Oldest Character

```sql
SELECT first_name, last_name, age
FROM characters
ORDER BY age DESC
LIMIT 1;
```

**Result:** Hubert Farnsworth – Age 210

---

## 📈 Key Insights

* **Total Dataset:** 15 records
* **Gender Balance:** Male 73%, Female 27%
* **Species Balance:** Human dominates (60%), others evenly distributed
* **Average Age:** 53.14
* **Maximum Age:** 210 (fictional extremes present)
* **Oldest Character:** Hubert Farnsworth, Age 210

> Insights highlight the need for normalization, validation, and attention to outliers in structured datasets.

---

## 💡 Business / MLS Relevance

* Simulates **MLS data ingestion and cleaning** for property or listing records.
* Demonstrates **structured data validation** techniques and QA workflows.
* Supports **ETL pipeline operations** by maintaining accurate, clean, and analyzable datasets.
* Provides **SQL-based insight generation**, critical for decision-making in real estate platforms.

---

## 🛠 Tools & Skills Used

* **Database Analysis:** SQL (PostgreSQL)
* **Data Cleaning & Normalization:** Structured preprocessing, categorical standard
