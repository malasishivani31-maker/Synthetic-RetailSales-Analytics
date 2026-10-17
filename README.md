# 🛍️ RetailPulse – Retail Sales Analytics Dashboard

📊 **RetailPulse – AI-Powered Customer Analytics & Demand Forecasting Platform** is a retail data analytics project developed using **Microsoft Power BI**. It transforms retail data into meaningful business insights through interactive dashboards, key performance indicators (KPIs), and data visualizations.

The project focuses on sales performance, product trends, customer behaviour, revenue, profitability, and inventory risks to support data-driven business decisions.

---

## 🎯 Project Objectives

- 📈 Analyze overall retail sales and revenue performance.
- 🏆 Identify top-performing products and brands.
- 👥 Understand customer purchasing behaviour.
- 🏙️ Compare sales performance across cities.
- 📦 Monitor inventory levels and potential stock risks.
- 📊 Develop interactive dashboards for business analysis.
- 💡 Support data-driven decision-making.

## 🛠️ Tools & Technologies

-  **Microsoft Power BI** – Dashboard development and visualization
-  **Power Query** – Data cleaning and transformation
-  **DAX** – KPI calculations and analytical measures
-  **CSV / Excel** – Data storage and preparation
-  **GitHub** – Project hosting and documentation

## 📂 Dataset Description

The project uses a synthetic retail transaction dataset and related business information.

The dataset includes:

- 🧾 Sales transactions
- 👤 Customer information
- 🏷️ Product and brand details
- 🏬 Store and city information
- 🎁 Promotion details
- 📦 Inventory and stock information

## 📊 Dashboard Overview

RetailPulse includes 12 dashboards designed to analyze different aspects of retail business performance.

| No. | Dashboard | Purpose |
|---:|---|---|
| 1 | Executive Summary | Overall business performance and KPIs |
| 2 | Sales Trend Analysis | Sales patterns and trends over time |
| 3 | Product Performance | Product-wise sales and revenue |
| 4 | Customer Analytics | Customer activity and purchasing metrics |
| 5 | City Analysis | Compare sales performance across cities |
| 6 | Monthly & Seasonal Analysis | Monthly and seasonal sales patterns |
| 7 | Customer Behaviour | Customer purchasing patterns |
| 8 | Profit & Revenue | Revenue and profitability analysis |
| 9 | Inventory Risk | Stock levels and potential inventory risks |
| 10 | Order & Transaction | Order activity and transaction details |
| 11 | Advanced Analytics | Deeper analysis using interactive visualizations |
| 12 | Interactive Filters | Explore data using slicers and filters |

## 🖼️ Dashboard Screenshots

Explore the interactive dashboards developed for the RetailPulse project using Microsoft Power BI.

### 1. Executive Summary
<img width="1157" height="652" alt="Executive Dashboard" src="https://github.com/user-attachments/assets/618d586b-32a1-472d-aa63-b5b24b977666" />

### 2. Sales Trend Analysis
<img width="1155" height="642" alt="Sales Trend Analysis" src="https://github.com/user-attachments/assets/0122ba78-6a2f-44c0-9d20-8a6cfd9ede30" />

### 3. Customer Performance
<img width="1176" height="642" alt="Customer Insights" src="https://github.com/user-attachments/assets/76028905-0e14-4083-a6e7-6d3ae468d21c" />

### 4. Inventory Analytics
<img width="1158" height="643" alt="Inventory Risk Analytics" src="https://github.com/user-attachments/assets/ed2bc333-230d-4b7f-8c2a-c5a2614630fe" />

### 5. Advanced Analytics
<img width="1158" height="643" alt="Advance Analytics" src="https://github.com/user-attachments/assets/9ba65d16-865a-408c-990c-0f8731fb8ce9" />



## 📌 Key Performance Indicators (KPIs)

The project uses DAX measures to calculate important retail metrics:

- Total Revenue
- Total Profit
- Total Quantity Sold
- Total Orders
- Average Order Value
- Total Brands
- Total Products
- Inventory Risk Percentage
- Last Restock Date
- Low-Stock Products

## 🧮 DAX Measures

The following DAX measures are used for KPI calculations and dashboard analysis in Power BI.

### 1. Total Revenue

```dax
Total Revenue =
SUM(sales_transactions[total_value])
```

### 2. Total Profit

```dax
Total Profit =
SUM(sales_transactions[profit])
```

### 3. Total Quantity Sold

```dax
Total Quantity =
SUM(sales_transactions[quantity])
```

### 4. Average Order Value

```dax
Average Order Value =
DIVIDE(
    [Total Revenue],
    [Total Orders],
    0
)
```

### 5. Total Orders

```dax
Total Orders =
DISTINCTCOUNT(sales_transactions[receipt_id])
```

### 6. Total Products

```dax
Total Products =
DISTINCTCOUNT(sku_master[sku_id])
```

### 7. Month-over-Month Sales Growth

This measure calculates the percentage change in revenue compared with the previous month. It requires a properly configured Calendar table related to the sales date.

```dax
Previous Month Sales =
CALCULATE(
    [Total Revenue],
    DATEADD('Calendar'[Date], -1, MONTH)
)
```

```dax
MoM Sales Growth % =
DIVIDE(
    [Total Revenue] - [Previous Month Sales],
    [Previous Month Sales],
    0
) * 100
```

### 8. Products Below Reorder Level

This measure counts distinct products whose stock is below their reorder level.

```dax
Products Below Reorder Level =
CALCULATE(
    DISTINCTCOUNT(inventory_snapshot[sku_id]),
    FILTER(
        inventory_snapshot,
        inventory_snapshot[stock_quantity]
            < inventory_snapshot[reorder_level]
    )
)
```


## 🔄 Project Workflow

1. Import retail datasets into Power BI.
2. Clean missing values, duplicates, and inconsistent records where appropriate.
3. Transform data using Power Query.
4. Establish relationships between relevant tables.
5. Create DAX measures for KPI calculations.
6. Design interactive dashboards and visualizations.
7. Analyze results and identify meaningful business insights.

## 🗂️ Repository Structure

```text
RetailPulse/
│
├── Dataset/
│   └── Retail dataset files
│
├── PowerBI/
│   └── RetailPulse.pbix
│
├── Screenshots/
│   ├── Executive_Summary.png
│   ├── Sales_Trend_Analysis.png
│   ├── Product_Performance.png
│   └── Other_Dashboard_Screenshots.png
│
└── README.md
```



## 🚀 How to Run the Project

1. 📥 Clone or download this repository.
2. 💻 Install Microsoft Power BI Desktop.
3. 📂 Open the `RetailPulse.pbix` file.
4. 🔗 Update dataset file paths if required.
5. 🔄 Refresh the data and verify model relationships.
6. 📊 Explore dashboards using available slicers, filters, and visualizations.

## 📈 Results & Insights

RetailPulse provides a consolidated view of retail business performance through interactive dashboards. It helps users:

- Monitor key performance indicators.
- Identify sales trends and product performance.
- Understand customer purchasing activity.
- Compare performance across cities and time periods.
- Examine inventory levels and potential stock risks.
- Make informed decisions using data-driven insights.

## ⚠️ Limitations & 🔮 Future Scope

The current implementation primarily focuses on historical data analysis and interactive reporting. Results depend on the quality and completeness of the available dataset.

Future enhancements may include:

-  Sales and demand forecasting using Prophet or LSTM
-  Customer segmentation using clustering algorithms
-  Customer churn prediction
-  Automated inventory alerts and replenishment recommendations
-  Cloud integration and automated data refresh
-  Advanced analytics using Python and machine learning


## 👩‍💻 Author

**Shivani Malasi**

📊 Aspiring Data Analyst | Power BI | SQL | Python | Excel
