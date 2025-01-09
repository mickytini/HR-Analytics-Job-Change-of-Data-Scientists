# HR Analytics: Job Change of Data Scientists

## Overview

This project focuses on analyzing HR data related to job changes among data scientists. The analysis includes extracting, transforming, and loading data from multiple sources into a SQLite database for further analysis.

---

## Data Sources

### **1. Enrollies' Data**
- **Description:** Contains data submitted via Google Forms by enrollees.
- **Columns:**
  - `enrollee_id`: Unique ID of an enrollee.
  - `full_name`: Full name of an enrollee.
  - `city`: Name of the enrollee's city.
  - `gender`: Gender of an enrollee.
- **Source:** [Google Sheet](https://docs.google.com/spreadsheets/d/1VCkHwBjJGRJ21asd9pxW4_0z2PWuKhbLR3gUHm-p4GI/edit?usp=sharing)

---

### **2. Enrollies' Education**
- **Description:** Contains manually collected data on enrollees' education.
- **Columns:**
  - `enrollee_id`: Unique identifier for each enrollee.
  - `enrolled_university`: Enrollment status (e.g., No enrollment, Part-time course, Full-time course).
  - `education_level`: Highest level of education attained (e.g., Graduate, Masters).
  - `major_discipline`: Primary field of study (e.g., STEM, Business Degree).
- **Source:** [Excel File](https://assets.swisscoding.edu.vn/company_course/enrollies_education.xlsx)

---

### **3. Enrollies' Working Experience**
- **Description:** Survey data on working experience.
- **Columns:**
  - `enrollee_id`: Unique identifier for each enrollee.
  - `relevent_experience`: Indicates whether the enrollee has relevant work experience.
  - `experience`: Years of work experience (e.g., >20, <1).
  - `company_size`: Size of the company (e.g., 50-99, 100-500).
  - `company_type`: Type of the company (e.g., Pvt Ltd, Funded Startup).
  - `last_new_job`: Years since the last job change.
- **Source:** [CSV File](https://assets.swisscoding.edu.vn/company_course/work_experience.csv)

---

### **4. Training Hours**
- **Description:** Data on training hours completed by each student.
- **Source:** MySQL Database
  - **Host:** `112.213.86.31`
  - **Port:** `3360`
  - **Login:** `etl_practice`
  - **Password:** `550814`
  - **Database Name:** `company_course`
  - **Table Name:** `training_hours`

---

### **5. City Development Index**
- **Description:** Measures the level of development in cities.
- **Columns:** Development indices of various cities.
- **Source:** [City Development Index](https://sca-programming-school.github.io/city_development_index/index.html)

---

### **6. Employment**
- **Description:** Indicates employment status after course completion.
- **Source:** MySQL Database
  - **Host:** `112.213.86.31`
  - **Port:** `3360`
  - **Login:** `etl_practice`
  - **Password:** `550814`
  - **Database Name:** `company_course`
  - **Table Name:** `employment`

---

## Steps in the Analysis

### **1. Extract Data**
Data is sourced from:
- Google Sheets
- Remote Excel and CSV files
- MySQL database
- HTML web pages

Each dataset is checked for proper loading before transformation.

---

### **2. Transform Data**
Data cleaning and transformation include:
- Fixing data types for consistency.
- Handling missing values by filling them with appropriate values (e.g., mode or placeholder).
- Converting columns to suitable types such as `category` or `string`.

**Example Transformation:**
- `gender` column in `Enrollies` dataset:
  - Missing values filled with mode (`fillna`).
  - Converted to `category` type.

---

### **3. Load Data**
The cleaned datasets are loaded into a SQLite database as a Data Warehouse for further analysis:
- Database file: `data_warehouse.db`
- Tables:
  - `Enrollies`
  - `Education`
  - `Working_Experience`
  - `Training_Hours`
  - `Cities`
  - `Employment`

---

## Technologies Used
- **Libraries:** 
  - `pandas`, `numpy`, `sqlalchemy`, `requests`, `pymysql`
- **Tools:**
  - Google Colab
  - MySQL
  - SQLite
- **Programming Language:** Python

---
