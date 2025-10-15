🏬 Global Superstore Data Warehouse

This project demonstrates the creation of a Data Warehouse using the Global Superstore dataset, showcasing the process of data cleaning, dimensional modeling (Star Schema), ETL implementation, and query-based analytics using Python and MySQL.

📊 Project Overview

The Global Superstore Data Warehouse project aims to transform transactional sales data into a dimensional model for analytical reporting.
It includes creating dimension tables (Customer, Product, Region, Date, Ship Mode) and a Fact table (Sales), enabling efficient querying and reporting.

⚙️ Tech Stack

Language: Python (Jupyter Notebook)

Database: MySQL

Libraries Used:

pandas

sqlalchemy

pymysql

openpyxl

Data Source: Global Superstore Dataset

🧩 Project Workflow
1️⃣ Data Extraction

Downloaded the dataset from Kaggle.

Loaded the data using Pandas and performed basic exploration (df.info(), df.isna(), df.duplicated()).

2️⃣ Data Cleaning

Handled missing values (especially Postal Code).

Standardized column names.

Converted date columns (Order Date, Ship Date) into datetime format.

3️⃣ Schema Design — Star Schema

Created the following tables:

Dimension Tables
Table	               Description
dim_customer      	Contains customer details like ID, name, and segment
dim_product	        Contains product-related data such as category and sub-category
dim_region	        Holds geographical information (country, state, city, region)
dim_ship_mode	    Includes shipping methods
dim_date	        Stores date-related attributes for both order and ship dates

Fact Table
Table	               Description
fact_sales	        Contains measurable metrics like sales amount, linked through surrogate keys
🧮 Data Warehouse Connection

Connected Python (Jupyter Notebook) to MySQL using SQLAlchemy and PyMySQL:

from sqlalchemy import create_engine

engine = create_engine("mysql+pymysql://root:your_password@localhost/global_superstore_dw")


Verified connection and loaded data into MySQL tables for further querying.

📈 ER Diagram: The ER diagram will be given in png format in the other file

💾 Setup Instructions

Clone this repository:

git clone https://github.com/<your-username>/global-superstore-dw.git
cd global-superstore-dw


Install required dependencies:

pip install pandas sqlalchemy pymysql openpyxl


Run Jupyter Notebook:

jupyter notebook


Configure your MySQL credentials inside the notebook.

📊 Outcomes

Implemented Star Schema successfully.

Loaded clean data into MySQL for analytical querying.

Executed SQL queries for business insights like sales by region, category, and segment.

Built a reusable ETL pipeline connecting Python → MySQL.

🙌 Author

Jaydev Gupta
🎓 B.Tech in Artificial Intelligence and Data Science
💡 Machine Learning & Data Analytics Enthusiast
