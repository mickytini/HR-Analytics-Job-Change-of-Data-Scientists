# HR Analytics: Job Change of Data Scientists

## Project Overview

This project aims to analyze HR data to understand factors influencing job changes among data scientists. By integrating data from multiple sources, cleaning and transforming it, and storing it in a centralized database, we create a comprehensive dataset ready for analysis. The project also demonstrates how to schedule and automate the ETL process on a platform.

---

## Data Overview

### Data Sources

1. **Enrollies' Data**
   - **Description:** Contains basic information about enrollees.
   - **Source:** [Google Sheet](https://docs.google.com/spreadsheets/d/1VCkHwBjJGRJ21asd9pxW4_0z2PWuKhbLR3gUHm-p4GI/edit?usp=sharing)

2. **Enrollies' Education**
   - **Description:** Details about education background.
   - **Source:** [Excel File](https://assets.swisscoding.edu.vn/company_course/enrollies_education.xlsx)

3. **Enrollies' Working Experience**
   - **Description:** Information on work experience.
   - **Source:** [CSV File](https://assets.swisscoding.edu.vn/company_course/work_experience.csv)

4. **Training Hours**
   - **Description:** Data on training hours completed by enrollees.
   - **Source:** MySQL database.

5. **City Development Index**
   - **Description:** Development indices of various cities.
   - **Source:** [City Development Index](https://sca-programming-school.github.io/city_development_index/index.html)

6. **Employment**
   - **Description:** Employment status of enrollees.
   - **Source:** MySQL database.

---

## Steps in the Process

### **1. Data Extraction**
- Extracted data from various sources:
  - **Google Sheets:** Using the `gspread` library for direct access.
  - **Excel/CSV Files:** Downloaded and read into Pandas DataFrames.
  - **MySQL Database:** Connected using `pymysql` and retrieved data via SQL queries.
  - **HTML Pages:** Scraped using Python's `requests` library.

**Decision:** Using different extraction methods ensures compatibility with diverse data formats.

---

### **2. Data Cleaning and Transformation**
Key transformations:
- **Handling Missing Values:**
  - Example: For the `gender` column in `Enrollies' Data`, missing values were replaced with the mode (most common value).
- **Standardizing Data Types:**
  - Example: Converted `company_size` in `Working Experience` dataset to categorical for optimized storage and processing.
- **Combining Datasets:**
  - Joined data on `enrollee_id` for a consolidated view.
- **Data Validation:**
  - Checked for duplicates and removed inconsistencies across all datasets.

**Decision:** Cleaning focused on ensuring data consistency, accuracy, and compatibility for integration.

---

### **3. Data Loading**
- Cleaned data was loaded into a SQLite database (`data_warehouse.db`) to serve as a centralized Data Warehouse.
- Database Tables:
  - `Enrollies`
  - `Education`
  - `Working_Experience`
  - `Training_Hours`
  - `Cities`
  - `Employment`

**Decision:** SQLite was chosen for its simplicity and compatibility with Python for ETL operations.

---

### **4. Scheduling the ETL Process**
The ETL process is automated and scheduled using Windows Task Scheduler. 

#### Instructions for Scheduling on Windows:
1. **Save the Script:**
   - Save your ETL Python script as `etl_process.py`.

2. **Create a Batch File:**
   - Create a `.bat` file with the following content:
     ```batch
     python "C:\path\to\etl_process.py"
     ```

3. **Open Task Scheduler:**
   - Search for "Task Scheduler" in the Windows search bar and open it.

4. **Create a New Task:**
   - Click **Create Task**.
   - Provide a name for your task (e.g., "HR ETL Process").

5. **Set Trigger:**
   - Go to the **Triggers** tab.
   - Click **New** and set a schedule (e.g., daily at 2:00 AM).

6. **Set Action:**
   - Go to the **Actions** tab.
   - Click **New** and select **Start a Program**.
   - Browse to the `.bat` file you created.

7. **Save and Run:**
   - Save the task and test it by running it manually.

**Decision:** Windows Task Scheduler was chosen for its accessibility and ease of use on most systems.

---
