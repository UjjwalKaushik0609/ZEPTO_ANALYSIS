

# 🛒 Zepto E-commerce SQL Data Analyst Portfolio Project
![image alt]([Zepto-Brand-Journey.jpg])

This project simulates a **real-world data analyst portfolio** using a scraped inventory dataset from [Zepto](https://www.zeptonow.com/) — one of India's fastest-growing quick-commerce startups.

It walks through a full analytical workflow using **SQL**, from raw data ingestion to actionable business insights.

---

## 🚀 Who This Project Is For

- 📊 Data Analyst aspirants wanting a **solid portfolio project**
- 🧠 Learners building **SQL skills with real data**
- 💼 Candidates prepping for **analytics interviews** in retail, e-commerce, or product domains

---

## 📦 Dataset Overview

The dataset was sourced from [Kaggle](https://www.kaggle.com/datasets/palvinder2006/zepto-inventory-dataset/data?select=zepto_v2.csv) and mimics real-world product catalogs with multiple SKUs for the same product.

### 🧾 Columns:

| Column Name              | Description |
|--------------------------|-------------|
| `sku_id`                 | Unique product ID (synthetic primary key) |
| `name`                   | Product name on the app |
| `category`               | Product category (e.g. Fruits, Snacks) |
| `mrp`                    | Maximum Retail Price (converted to ₹) |
| `discountPercent`        | % discount applied |
| `discountedSellingPrice`| Final price after discount |
| `availableQuantity`      | Quantity in inventory |
| `weightInGms`            | Weight of product in grams |
| `outOfStock`             | Boolean for availability |
| `quantity`               | Units per pack (some mixed with grams) |

---

## 🔧 Project Workflow

### 1️⃣ Table Creation

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

---

### 2️⃣ Data Import (PostgreSQL)

```sql
\copy zepto(category,name,mrp,discountPercent,availableQuantity,
            discountedSellingPrice,weightInGms,outOfStock,quantity)
FROM 'data/zepto_v2.csv' WITH (FORMAT csv, HEADER true, DELIMITER ',', QUOTE '"', ENCODING 'UTF8');
```

*📌 UTF-8 encoding issue fixed by saving file as **CSV UTF-8**.*

---

### 3️⃣ Exploratory Data Analysis (EDA)

- Record count, null checks, distinct categories
- In-stock vs out-of-stock analysis
- Duplicate product name detection
- SKU mapping and variety analysis

---

### 4️⃣ Data Cleaning

- Removed rows with `mrp = 0` or `discountedSellingPrice = 0`
- Converted `mrp` and `discountedSellingPrice` from **paise to ₹**

---

## 📊 Business-Driven SQL Insights

- 🏷️ Top 10 best-value products (highest discounts)
- 🚫 High-MRP items currently out of stock
- 📈 Potential revenue per product category
- 💸 Premium products (MRP > ₹500) with low discounts
- 🥇 Top 5 categories by average discount
- ⚖️ Price-per-gram analysis (best value items)
- 📦 Inventory segmentation: **Low**, **Medium**, **Bulk**
- 🧮 Total weight in stock per category

---

## 🧠 Key Learnings

- Real-world SQL query writing and debugging
- Structuring EDA and cleaning workflows
- Deriving insights relevant to business teams (pricing, inventory, marketing)
- Hands-on data handling with PostgreSQL

---

## 🧰 Tools Used

- 🐘 PostgreSQL / pgAdmin
- 📑 CSV from Kaggle
- 🧠 SQL for querying and analysis
- 💻 Markdown for documentation

---

