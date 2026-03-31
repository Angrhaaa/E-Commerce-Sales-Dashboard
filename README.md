# 📊 E-Commerce Sales Dashboard (Power BI)

## 🚀 Project Overview
This project presents an interactive Power BI dashboard built to analyze sales performance for an eCommerce business.  
The dashboard provides insights into sales trends, product performance, and customer behavior using real-world data.

---

## 🎯 Objective
To design a comprehensive dashboard that:
- Tracks key business metrics  
- Identifies top-performing products and categories  
- Segments customers based on spending behavior  
- Enables dynamic filtering for better decision-making  

---

## 🧰 Tools & Technologies
- Power BI (Dashboard & Data Modeling)  
- DAX (Data Analysis Expressions)  
- Excel / CSV (Data Source)  
- Power Query (Data Cleaning)  

---

## 📂 Dataset Description
The dataset includes:
- Transaction ID  
- Date  
- Customer ID  
- Gender & Age  
- Product Category  
- Quantity  
- Price per Unit  
- Total Amount (Revenue)  

---

## 🧹 Data Cleaning & Preparation
Steps performed:
- Removed duplicate records using Transaction ID  
- Converted Date column to proper format  
- Validated Total Amount = Quantity × Price  
- Created additional fields:
  - Month-Year  
  - Age Group  
  - Customer Spend  

---

## 🧠 Data Modeling
- Created a Date Table for time-based analysis  
- Established relationship:
  - DateTable[Date] → SalesData[Date]  
- Enabled proper filtering across visuals  

---

## 📐 DAX Measures

### 💰 Total Sales
```DAX

Total Sales = SUM(SalesData[Total Amount])

```

📦 Total Orders

```
Total Orders = DISTINCTCOUNT(SalesData[Transaction ID])

```
👥 Total Customers

```
Total Customers = DISTINCTCOUNT(SalesData[Customer ID])

```

📊 Average Order Value

```

Avg Order Value = DIVIDE([Total Sales], [Total Orders])

```
💵 Customer Spend

```
Customer Spend = 
CALCULATE(
    SUM(SalesData[Total Amount]),
    ALLEXCEPT(SalesData, SalesData[Customer ID])
)

```

🏷 Customer Segment

```

Customer Segment = 
SWITCH(
    TRUE(),
    [Customer Spend] < 100, "Low",
    [Customer Spend] <= 500, "Medium",
    "High"
)

```

## 📊 Dashboard Features

### 🔝 KPI Cards
- Total Sales  
- Total Orders  
- Total Customers  
- Average Order Value  

### 📈 Sales Trend Analysis
- Line chart showing monthly sales performance  

### 📊 Category Performance
- Bar chart comparing revenue across categories  

### 🥧 Category Share
- Pie chart showing contribution of each category  

### 👥 Customer Segmentation
- Visualizes Low, Medium, High spenders  

### 📋 Top Customers
- Table showing highest-value customers  

### 🎛 Filters (Slicers)
- Date Range  
- Product Category  
- Gender  
- Age Group  

---

## 📌 Key Insights
- Electronics generates the highest revenue  
- Sales peak mid-year (seasonality)  
- Majority customers are low spenders  
- High-value customers contribute most revenue  
