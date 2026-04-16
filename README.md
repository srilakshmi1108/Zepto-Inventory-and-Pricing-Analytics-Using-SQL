## 🛒 Zepto Inventory and Pricing Analytics Using SQL

This project is an end-to-end data analysis case study built on an e-commerce inventory dataset sourced from Zepto, one of India’s fast-growing quick-commerce platforms. It simulates how a data analyst works with raw data to generate business insights using SQL.

---

## 📌 Project Overview

The goal of this project is to replicate real-world analyst workflows in an e-commerce environment. The analysis focuses on:

- Structuring and storing raw inventory data  
- Exploring product distribution, pricing, and stock availability  
- Cleaning inconsistent and invalid data  
- Writing SQL queries to extract actionable business insights  

---

## 🧠 Analytical Approach

The project follows a structured workflow:

1. Data ingestion and schema design  
2. Exploratory data analysis (EDA)  
3. Data cleaning and transformation  
4. Business-focused SQL analysis  
5. Insight generation for decision-making  

---

## 📁 Dataset Overview

The dataset was sourced from Kaggle and represents product listings originally scraped from Zepto. It closely resembles real-world e-commerce catalog data.

Each record corresponds to a unique SKU (Stock Keeping Unit). The same product may appear multiple times due to differences in packaging, size, or discounts.

### 🧾 Columns Description

- **sku_id**: Unique identifier for each product  
- **name**: Product name  
- **category**: Product category (Fruits, Snacks, Beverages, etc.)  
- **mrp**: Maximum Retail Price (converted from paise to ₹)  
- **discountPercent**: Discount applied  
- **discountedSellingPrice**: Final price after discount (₹)  
- **availableQuantity**: Units available in stock  
- **weightInGms**: Product weight  
- **outOfStock**: Stock availability flag  
- **quantity**: Units per package  

---

## 🔧 Project Workflow

### 1. Database and Table Creation

```sql
CREATE TABLE zepto (
  sku_id SERIAL PRIMARY KEY,
  category VARCHAR(120),
  name VARCHAR(150) NOT NULL,
  mrp NUMERIC(8,2),
  discountPercent NUMERIC(5,2),
  availableQuantity INTEGER,
  discountedSellingPrice NUMERIC(8,2),
  weightInGms INTEGER,
  outOfStock BOOLEAN,
  quantity INTEGER
);
```

### 2. Data import 
The dataset was loaded into PostgreSQL using pgAdmin’s import functionality.

In cases where import issues occurred, the \copy command was used as an alternative:

```sql
\copy zepto(category,name,mrp,discountPercent,availableQuantity,
            discountedSellingPrice,weightInGms,outOfStock,quantity)
FROM 'data/zepto_v2.csv'
WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');
```

### 3. Data Exploration
Counted total records
Inspected sample data
Identified null values
Analyzed product categories
Compared in-stock vs out-of-stock items
Detected duplicate SKUs across product variations
### 4. Data Cleaning
Removed records with zero pricing values
Converted pricing from paise to rupees
Standardized numeric fields for analysis
### 5. Key Business Insights
High discount products (>40%) were concentrated in a few categories, indicating aggressive pricing strategies
Several high-MRP products were out of stock, suggesting potential lost revenue opportunities
A small number of categories contributed significantly to total estimated revenue
Premium products (MRP > ₹500) generally had lower discounts, indicating margin-focused pricing
Price-per-gram analysis revealed inconsistencies in value across similar products
Bulk items contributed heavily to inventory weight but not proportionally to revenue
### 6. Business Analysis Performed
Top products based on discount percentage
Out-of-stock analysis for high-value items
Revenue estimation by category
Discount distribution across categories
Price-per-unit (gram) evaluation
Product segmentation based on weight
Inventory weight contribution by category
🛠️ Tech Stack
SQL (PostgreSQL)
pgAdmin
Kaggle Dataset

###  🛠️ How to Run
1. Clone the repository  
2. Create a PostgreSQL database  
3. Run the SQL script to create tables  
4. Import the dataset (ensure UTF-8 encoding)  
5. Execute queries to reproduce analysis  
```
Encoding issues were resolved by converting the CSV file to UTF-8 format before loading.


