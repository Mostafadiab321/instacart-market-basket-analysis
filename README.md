
### Dashboard Overview
<img width="1304" height="733" alt="Screenshot 2026-11-25 133821" src="https://github.com/user-attachments/assets/11dc2f3b-9e01-41cc-8d35-f0d7997f17c3" />



# Instacart Market Basket Analysis

An end-to-end Data Analytics project using the Instacart Market Basket Analysis dataset. This project combines Python, SQL Server, and Power BI to explore customer purchasing behavior, analyze product performance, identify reorder patterns, and develop interactive business intelligence dashboards.

---

## Project Overview

The objective of this project is to analyze Instacart's customer and product data to identify purchasing patterns, understand customer behavior, and evaluate product and department performance.

The project follows three main stages:

1. Python – Data Inspection and Exploratory Data Analysis (EDA).
2. SQL Server – Database Design, Data Analysis, and KPI Development.
3. Power BI – Interactive Dashboards and Business Intelligence Reporting.

## Tools & Technologies

- Python
- SQL Server
- Power BI
- Jupyter Notebook
- SQL
- DAX

## Dataset

**Source:** [Instacart Market Basket Analysis – Kaggle](https://www.kaggle.com/competitions/instacart-market-basket-analysis)

The dataset contains multiple related tables covering customer orders, products, aisles, departments, and order-product relationships.

### Dataset Tables

| Table | Rows |
|---|---:|
| Orders | 3,421,083 |
| Order Products Prior | 32,434,489 |
| Order Products Train | 1,384,617 |
| Products | 49,688 |
| Aisles | 134 |
| Departments | 21 |

---

# Project Workflow

## 1. Python – Data Inspection & Exploratory Data Analysis

Python was used to inspect the dataset, validate data quality, and perform exploratory data analysis before loading the data into SQL Server.

### Key Activities

- Loaded and inspected the six dataset tables.
- Reviewed dataset dimensions, column names, and data types.
- Checked for missing values and duplicate records.
- Analyzed order distribution by day of week and hour of day.
- Explored customer ordering patterns.
- Examined product reorder indicators.
- Checked table relationships and identifier ranges.

**Data Quality Note:**

The `days_since_prior_order` column contains 206,209 missing values, representing customers' first recorded orders. These values were retained without filling or deleting them.

Python was primarily used for data inspection, validation, and EDA.

## 2. SQL Server – Database Design & Analysis

The dataset was loaded into a SQL Server database named `Instacart_Analysis`.

### Database Tables

- `orders_cleaned`
- `order_products_prior_cleaned`
- `order_products_train_cleaned`
- `products_cleaned`
- `aisles_cleaned`
- `departments_cleaned`

### Database Design

- Created primary keys for the main tables.
- Established foreign key relationships.
- Used composite primary keys for order-product tables.
- Created relationships between orders, products, aisles, and departments.

### SQL Analysis

Developed SQL queries to analyze:

- Reordered products by department.
- Number of products by department.
- Number of orders by hour.
- Product and department performance.
- Customer and order behavior.

### SQL Concepts Used

- SELECT, WHERE, ORDER BY
- GROUP BY
- Aggregate Functions (COUNT, SUM, AVG)
- JOIN Operations
- SQL Views

### KPI & Chart Views

Created 16 KPI views and 4 chart views to support the Power BI dashboards.

Also created a summary named `Department Analysis Summary`, containing:

- Department ID
- Department Name
- Total Orders
- Total Products Ordered

## 3. Power BI – Interactive Dashboards

Power BI was used to develop four interactive dashboard pages to present the analytical findings.

### Dashboard 1 – Overview
<img width="1304" height="733" alt="Screenshot 2026-11-25 133821" src="https://github.com/user-attachments/assets/b5e88940-6807-49b2-86c5-cfeefc99d828" />


Provides a general overview of order activity and customer purchasing behavior.

**Key Performance Indicators (KPIs):**

- Total Orders: 3.42M
- Total Customers: 206K
- Repeat Order Percentage: 93.97%
- Average Order per Customer: 16.59
- Average Days Between Orders: 11.11

**Visualizations:**

- Orders by Day of Week
- Orders by Hour
- Orders by Order Number
- First Orders vs. Repeat Orders
- Total Orders by Order Frequency

**Filters:**

- Day Name
- Order Hour
- Order Number

### Dashboard 2 – Customer Analysis

<img width="1317" height="746" alt="Screenshot 2026-11-25 135123" src="https://github.com/user-attachments/assets/6aa239e9-6157-4776-8e24-028b3cdec0f9" />

Focuses on customer ordering behavior and purchasing frequency.

**Key Performance Indicators (KPIs):**

- Total Number of Customers: 206K
- Total Number of Orders: 3.42M
- Average Number of Orders per Customer: 16.59
- Average Days Between Orders: 11.11

**Visualizations:**

- Average Days Between Orders by Order Number
- Customers by Order Number
- Orders by Days Since Previous Order
- Unique Customers by Day of Week

**Filters:**

- Day Name
- Order Hour
- Order Number

### Dashboard 3 – Product Analysis
<img width="1322" height="737" alt="Screenshot 2026-11-25 135138" src="https://github.com/user-attachments/assets/46b7b0f9-f907-457a-97ce-75606cc87213" />

Analyzes product popularity, reorder rates, and product distribution across departments.

**Key Performance Indicators (KPIs):**

- Total Products: 49.7K
- Total Departments: 21
- Total Products Ordered: 33.8M
- Average Products per Order: 10.11

**Visualizations:**

- Top 10 Most Reordered Products
- Top 10 Highest Reorder Rate
- Bottom 10 Least Reordered Products
- Bottom 10 Lowest Reorder Rate
- Product Distribution by Department

### Dashboard 4 – Product Performance Analysis
<img width="1298" height="742" alt="Screenshot 2026-11-25 135157" src="https://github.com/user-attachments/assets/e1af4077-4a8a-42fc-81f6-29cba211ef08" />



Provides a detailed analysis of product ordering performance across departments and aisles.

**Key Performance Indicators (KPIs):**

- Total Products Ordered: 33.8M
- Overall Reorder Rate: 59.01%
- Total Unique Products Ordered: 49.7K
- Average Products per Order: 10.11
- Total Reordered Products: 19.96M

**Visualizations:**

- Total Orders by Department
- Total Orders vs. Total Products Ordered by Department
- Total Products by Department
- Total Products Ordered by Department

**Filters:**

- Department Name
- Aisle Name
- Day Name

### Power BI Development

- Created a dedicated `DAX Measures` table.
- Developed 10 DAX measures for customer and order analysis.
- Used SQL views as the main source for KPI and chart reporting.
- Used summarized SQL data to avoid importing the full 32-million-row prior-order table into Power BI.

---

## Key Business Questions

This project aims to answer the following business questions:

1. Which days and hours have the highest order activity?
2. How does customer ordering behavior change across order numbers?
3. How frequently do customers place orders?
4. Which products are reordered most frequently?
5. Which products have the highest and lowest reorder rates?
6. Which departments generate the highest order volume?
7. How are products distributed across departments?
8. What is the overall product reorder rate?

## Repository Structure

```text
instacart-market-basket-analysis/
│
├── notebooks/
│   ├── 01_load_orders.ipynb
│   ├── 02_load_order_products_prior.ipynb
│   ├── 03_load_order_products_train.ipynb
│   ├── 04_load_products.ipynb
│   ├── 05_load_aisles.ipynb
│   ├── 06_load_departments.ipynb
│   └── 07_relationship_checks.ipynb
│
├── sql/
│   ├── database_setup.sql
│   ├── table_relationships.sql
│   ├── analysis_queries.sql
│   └── views/
│
├── power-bi/
│   └── Instacart_Dashboard.pbix
│
├── documentation/
│   └── Instacart_Project_Documentation.pdf
│
└── README.md
```

## Project Deliverables

- Python notebooks for data inspection and EDA.
- SQL Server database design and relationships.
- SQL analysis queries and KPI views.
- Four interactive Power BI dashboard pages.
- Project documentation.

## Author

**Prepared by:** Mustafa Mohammad

**Program:** Data Analysis Diploma – Smart Investment Solution (SIS)

**Project:** Instacart Market Basket Analysis

---

**Thank you for visiting my project!**
