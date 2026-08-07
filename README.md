# E-Commerce Sales & Returns Analytics

## 📌 Project Overview
This project focuses on the End-to-End Data Cleaning, Transformation, and Exploratory Data Analysis (EDA) of an online retail dataset. The goal is to uncover actionable business insights regarding revenue drivers, product returns, and temporal sales patterns to optimize business decisions.

* **Dataset Source:** You can download the original raw dataset directly from [Kaggle - Online Retail Dataset](https://kaggle.com).

---

## 🛠️ Data Cleaning & Feature Engineering
The raw dataset contained **541,909 rows** and **8 columns**. To ensure data integrity, the following advanced cleaning pipeline was executed inside the provided notebook:
* **Handling Duplicates:** Identified and removed all duplicate rows using `drop_duplicates` to prevent skewed analysis.
* **Missing Value Imputation:** 
  * Missing product descriptions were filled with `"unknown"`.
  * Missing `CustomerID` values (**135,080 rows**) were filled with `0` to retain sales transaction records instead of dropping them.
* **Datatype Transformation:** Converted `InvoiceDate` from text to a proper `datetime64` format.
* **Feature Engineering:** Extracted `year`, `month`, and `day` attributes to perform time-series analysis.
* **Anomaly Handling & Revenue Isolation:**
  * Detected extreme negative values in `Quantity` (down to **-80,995**) representing cancellations and returns.
  * Separated data into independent metrics: `returns` (positive absolute quantity of returns) and `validQuantity` (true successful sales).
  * Filtered out negative or erroneous `UnitPrice` rows.
  * Calculated **`Clean_Revenue`** (`valid_UnitPrice` * `validQuantity`) to represent the exact net financial performance.

---

## 📊 Key Business Insights & Findings

### 1. Top 5 Countries by Net Revenue
* **United Kingdom:** Dominated the market significantly with a staggering net revenue of **~8.2M**.
* **Netherlands:** **285,446.34**
* **EIRE (Ireland):** **263,445.82**
* **Germany:** **228,678.40**
* **France:** **209,625.37**

### 2. High-Value Financial Drivers (Top Products by Revenue)
1. **DOTCOM POSTAGE:** **206,246.77** (Indicates substantial online shipping volumes).
2. **REGENCY CAKESTAND 3 TIER:** **174,161.64**
3. **PAPER CRAFT, LITTLE BIRDIE:** **168,469.60**
4. **WHITE HANGING HEART T-LIGHT HOLDER:** **106,282.72**
5. **PARTY BUNTING:** **99,445.23**

### 3. Critical Return Rate & Inventory Risk Insight
* **The Return Bug:** A major critical finding was discovered regarding the product **"PAPER CRAFT, LITTLE BIRDIE"**. While it was the 3rd highest product in sales volume (**80,995 units**), it was also the #1 most returned product with the exact same volume (**80,995 units**). 
* **Business Recommendation:** Net sales for this product dropped to exactly **zero**, indicating a massive order cancellation or logistics issue that requires immediate supply-chain investigation.

### 4. Peak Purchasing Times (Temporal Trend Analysis)
* **Annual Trend:** Fiscal year **2011** recorded **9,820,808.07** in revenue, far exceeding 2010 (which only contained December data).
* **Monthly Peak (Holiday Season Trend):** Sales heavily concentrated in **Q4** (Quarter 4). **November (#1 with 1.50M)**, **December (#2 with 1.45M)**, and **October (#3 with 1.15M)** were the highest grossing months due to Black Friday and winter holiday shopping.
* **Daily Peak:** Maximum transaction values occur on the **7th (532,030.05)** and **9th (515,802.30)** days of the month.

---

## 💻 Technologies Used
* **Python** (Core Analysis)
* **Pandas** (Data Manipulation & Cleaning)
* **Matplotlib** (Data Visualization)
* **Jupyter Notebook / Google Colab**

Dataset Source: You can download the dataset used in this project directly from [https://www.kaggle.com/datasets/tunguz/online-retail].
