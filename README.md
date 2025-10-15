# 🏬 Global Superstore Data Warehouse

This project demonstrates the creation of a Data Warehouse using the Global Superstore dataset, showcasing the process of data cleaning, dimensional modeling (Star Schema), ETL implementation, and query-based analytics using Python and MySQL.

## 📊 Project Overview

The Global Superstore Data Warehouse project aims to transform transactional sales data into a dimensional model for analytical reporting.
It includes creating dimension tables (Customer, Product, Region, Date, Ship Mode) and a Fact table (Sales), enabling efficient querying and reporting.

## ⚙️ Tech Stack

* **Language:** Python (Jupyter Notebook)
* **Database:** MySQL
* **Libraries Used:**

  * pandas
  * sqlalchemy
  * pymysql
  * openpyxl
* **Data Source:** Global Superstore Dataset

## 🧩 Project Workflow

### 1️⃣ Data Extraction

* Downloaded the dataset from Kaggle.
* Loaded the data using Pandas and performed basic exploration (`df.info()`, `df.isna()`, `df.duplicated()`).

### 2️⃣ Data Cleaning

* Handled missing values (especially Postal Code).
* Standardized column names.
* Converted date columns (Order Date, Ship Date) into datetime format.

### 3️⃣ Schema Design — Star Schema

**Dimension Tables**

| Table         | Description                                                   |
| ------------- | ------------------------------------------------------------- |
| dim_customer  | Contains customer details like ID, name, segment              |
| dim_product   | Contains product-related data (category, sub-category)        |
| dim_region    | Holds geographical information (country, state, city, region) |
| dim_ship_mode | Includes shipping methods                                     |
| dim_date      | Stores date-related attributes for order and ship dates       |

**Fact Table**

| Table      | Description                                                                  |
| ---------- | ---------------------------------------------------------------------------- |
| fact_sales | Contains measurable metrics like sales amount, linked through surrogate keys |

## 🧮 Data Warehouse Connection

Connected Python (Jupyter Notebook) to MySQL using SQLAlchemy and PyMySQL:

```python
from sqlalchemy import create_engine

engine = create_engine("mysql+pymysql://root:your_password@localhost/global_superstore_dw")
```

Verified connection and loaded data into MySQL tables for further querying.

## 🧠 Example Analytical Queries

**1. View All Sales with Dimension Joins**

```sql
SELECT 
    fs.sales,
    dc.customer_name,
    dp.product_name,
    dr.region,
    dsm.ship_mode,
    dod.full_date AS order_date,
    dsd.full_date AS ship_date
FROM fact_sales fs
JOIN dim_customer dc ON fs.customer_sk = dc.customer_sk
JOIN dim_product dp ON fs.product_sk = dp.product_sk
JOIN dim_region dr ON fs.region_sk = dr.region_sk
JOIN dim_ship_mode dsm ON fs.ship_mode_sk = dsm.ship_mode_sk
JOIN dim_date dod ON fs.order_date_sk = dod.date_sk
JOIN dim_date dsd ON fs.ship_date_sk = dsd.date_sk
LIMIT 10;
```

**2. Total Sales by Region and Category**

```sql
SELECT 
    dr.region,
    dp.category,
    ROUND(SUM(fs.sales), 2) AS total_sales
FROM fact_sales fs
JOIN dim_product dp ON fs.product_sk = dp.product_sk
JOIN dim_region dr ON fs.region_sk = dr.region_sk
GROUP BY dr.region, dp.category
ORDER BY total_sales DESC;
```

## 📈 ER Diagram

The Star Schema consists of one Fact Table and five Dimension Tables.
**Note:** The ER diagram is provided as a PNG file in this repository (`ER_Diagram.png`) for reference.

## 💾 Setup Instructions

1. **Clone this repository:**

```bash
git clone https://github.com/JaydevGupta22/Global-SuperStore-Data-Warehouse.git
cd Global-SuperStore-Data-Warehouse


2. **Install required dependencies:**

```bash
pip install pandas sqlalchemy pymysql openpyxl
```

3. **Run Jupyter Notebook:**

```bash
jupyter notebook
```

4. Configure your MySQL credentials inside the notebook.

## 📊 Outcomes

* Implemented Star Schema successfully.
* Loaded clean data into MySQL for analytical querying.
* Executed SQL queries for business insights like sales by region, category, and segment.
* Built a reusable ETL pipeline connecting Python → MySQL.

## 🙌 Author

**Jaydev Gupta**
🎓 B.Tech in Artificial Intelligence and Data Science
💡 Machine Learning & Data Analytics Enthusiast

---

If you want, I can also **provide a perfectly aligned table for the “Dimension Tables” and “Fact Table” in GitHub Markdown style** so it looks **exactly the same on the README preview** without any misalignment.

Do you want me to do that?
