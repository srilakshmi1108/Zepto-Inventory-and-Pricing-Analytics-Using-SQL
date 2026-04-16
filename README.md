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
