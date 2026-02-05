# Business Intelligence Case Study: AfriRetail Ltd Data Standardization
**Course:** DSA3050A - Power Query Lab   

## 1. Project Overview
AfriRetail Ltd, a mid-sized retailer in East Africa, faced significant challenges with data integrity. Sales reports were inconsistent with accounting records due to non-standard reporting templates and "dirty" raw data. This project involved building a robust, automated ETL (Extract, Transform, Load) pipeline using **Power Query** to transform raw Excel files into an analysis-ready Star Schema.

## 2. Identified Data Quality Issues
During the Data Profiling phase, the following critical issues were identified and resolved:
* **Logical Errors:** Negative and zero quantities in the sales records.
* **Format Inconsistency:** Mixed date formats and inconsistent casing (KE vs Kenya).
* **Structural Gaps:** Missing cost prices in the product reference file and null values in transaction dates.
* **Redundancy:** Duplicate entries in the product catalog and extra whitespace in text fields.

## 3. Transformation Logic & Business Rules
The following steps were taken to ensure the data is "Analysis-Ready":

### Data Cleaning (Task 3)
* **Text Standardization:** Applied `Trim`, `Clean`, and `Capitalize Each Word` to all string fields.
* **Date Handling:** Standardized dates using Locale (Kenya) and handled null values using a placeholder date (1/1/1900) to maintain model integrity.
* **Data Typing:** Enforced strict data types (Currency for financial values, Whole Number for quantities).

### Business Logic (Task 5)
* **Total Revenue:** Calculated as `[Quantity] * [Unit_Price]`.
* **Profitability:** Created a `Margin` metric: `[Total_Revenue] - ([Quantity] * [Cost_Price])`.
* **Performance Banding:** Transactions were categorized into "High", "Medium", and "Low" based on revenue thresholds to assist management in prioritizing large accounts.

## 4. Data Governance & Model Architecture
* **Star Schema:** Developed dimension tables (`Dim_Products`, `Dim_Regions`) and a central `Fact_Sales` table.
* **Audit Layer:** Created a `Review_Required_Records` query to isolate transactions with negative quantities or missing critical data.
* **Load Control:** Only finalized, cleaned tables are loaded into the data model; staging and audit queries are set to "Do Not Load" to optimize performance.

## 5. Submission Checklist
* [ ] **DSA3050A_PowerQuery_Lab.pbix** (Power BI File)
* [ ] **Screenshots Folder** (7 Required steps)
* [ ] **README.md** (Project Documentation)

---
*This project was completed entirely within Power Query Editor to ensure a repeatable and transparent data preparation process.*