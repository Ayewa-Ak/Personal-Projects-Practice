# Hospital Readmissions SQL Analysis

##  Project Overview
This project performs an end-to-end data cleaning, transformation, and exploratory data analysis (EDA) on a healthcare dataset tracking diabetic patient hospital encounters. The objective is to identify key clinical and demographic drivers of 30-day hospital readmissions to help improve patient care workflows.

##  Tech Stack & Skills Demonstrated
* **Database Management:** MySQL
* **Data Cleaning & Preprocessing:** Handling missing values, removing duplicates based on primary encounters, standardizing categorical features.
* **Advanced SQL Techniques:** Common Table Expressions (CTEs), Window Functions (`ROW_NUMBER`, `RANK`, `NTILE`), Case Statements, and Complex Joins.
* **Healthcare Domain Logic:** ICD-9 diagnostic grouping, discharge disposition filtering (filtering out deceased/hospice patients), and medication burden tiering.

##  Key Steps & Methodology
1. **Data Preparation & Cleaning:** Replaced placeholder question marks (`?`) with SQL `NULL` values and quantified missing data percentages.
2. **Deduplication:** Isolated unique patients by their first recorded hospital encounter to prevent bias in readmission modeling.
3. **Filtering Outliers:** Excluded patient records where the discharge disposition indicated death or hospice care.
4. **Feature Engineering:** 
   * Created numerical `age_midpoint` tiers.
   * Built compound medication and diagnosis complexity tiers.
   * Categorized ICD-9 codes into broad clinical systems (Circulatory, Respiratory, Diabetes, etc.).
5. **Advanced Analytics & Window Functions:** Applied `RANK()` and `NTILE()` to evaluate patient risk quartiles and medication burdens across age groups.

##  Key Findings & Insights
* **Top Readmission Drivers:** Patients admitted through emergency routes and those with primary diagnoses related to circulatory and respiratory systems showed significantly higher 30-day readmission rates.
* **Medication & Testing:** Higher medication burden correlates closely with increased clinical complexity and readmission risk, though specific discharge medication changes reveal distinct behavioral patterns.
* **Discharge Disposition:** Specific post-discharge destinations (e.g., transfers to skilled nursing or short-term facilities) heavily dictate the probability of an early return to the hospital.
* **30-Day Readmission Trends:** A significant portion of patient readmissions occur within the critical 30-day window, heavily concentrated among patients with prior emergency or inpatient visits in the preceding year.
* **Length of Stay vs. Readmission:** Analysis shows that longer hospital stays (ranging up to 14 days) do not necessarily correlate with lower readmission rates; patient complexity and primary diagnosis play a far heavier role.
* **Medication Management:** Patients undergoing changes in their diabetes medications during their encounter exhibited distinct readmission patterns compared to those whose medication regimens remained stable.
* **Impact of Lab Procedures:** High frequencies of lab and diagnostic procedures strongly correlated with specific demographic cohorts and more severe primary admission diagnoses (`diag_1`).
* **Demographic Risk Factors:** Certain age brackets (particularly older cohorts) and specific admission sources (such as emergency room transfers) experience a higher baseline risk for early readmission.

##  How to Run the Code
1. Clone the repository: `git clone https://github.com/your-username/hospital-readmissions-sql-analysis.git`
2. Import `diabetic_data.csv` and `IDS_mapping.csv` into your local MySQL environment.
3. Run the script inside the `scripts/` folder.
