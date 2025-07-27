# 🛍️ E-Commerce Sales Data Analysis Dashboard

This project presents an interactive Power BI dashboard that analyzes key performance metrics in an e-commerce business, including sales, customer behavior, product performance, and profitability. The dashboard helps stakeholders identify trends, optimize operations, and make data-driven decisions.

<br/>

## 📊 Dashboard Overview

The dashboard is divided into two main pages, each designed to analyze different business dimensions and customer insights.



### 1. **Sales Performance Overview**
- **Total Revenue, Quantity Sold, Profit, and AOV**
- **Sales Revenue by State**
- **Order Quantity by Payment Mode**
- **Monthly Profit Trends**
- **Sales Conversion Efficiency by Product Sub-Category**
- **Profit Contribution by Product Sub-Category**

**📖 Storyline:**  
This page provides a snapshot of overall business performance, helping assess which states and products are driving revenue and profit. It also evaluates how different payment modes influence order quantity and highlights the **most efficient sub-categories** in converting potential into actual sales. Seasonal trends in monthly profits are visualized to uncover high and low-performing periods.



### 2. **Customer and Product Insights**
- **Customer Lifetime Value (CLTV) by Customer**
- **Top Customers by Purchase Amount**
- **Product Category Distribution by Quantity**
- **Moving Average Profit and Monthly Profit Comparison**

**📖 Storyline:**  
This section dives into customer-level analytics to identify **top revenue-generating customers** and product preferences. CLTV helps in understanding the most valuable long-term customers. Product category insights show what customers are purchasing most (e.g., clothing), while moving average profit trends offer a **smoothed view of financial performance**, aiding in strategic planning.

<br/>

## 📌 Key Insights

- **Total Revenue:** ₹438K | **Total Quantity Sold:** 5615 | **Total Profit:** ₹37K | **Average Order Value:** ₹121K
- **Maharashtra and Madhya Pradesh** are top-performing states by revenue.
- **Cash on Delivery (COD)** is the most used payment mode.
- **Tables and Bookcases** have the highest sales conversion efficiency.
- **Printers and Sarees** contribute the most to profit.
- **Clothing** dominates in product quantity sold, followed by electronics and furniture.
- **Harivansh, Madhav, and Madan Mohan** are the top customers by purchase amount.

<br/>

## 🧮 DAX Measures Used 





1. CLTV = 
CALCULATE(
    SUM(Details[Amount]),
    ALLEXCEPT(Orders, Orders[CustomerName])
)



2. Moving Avg Profit = 
AVERAGEX(
    DATESINPERIOD(
        Orders[Order Date], 
        MAX(Orders[Order Date]), 
        -3, 
        MONTH
    ),
    CALCULATE(SUM(Details[Profit]))
)


3. Sales Conversion Efficiency = 
VAR TotalQty = CALCULATE(SUM(Details[Quantity]))
VAR TotalProfit = CALCULATE(SUM(Details[Profit]))
VAR ConversionScore = 
    SWITCH(TRUE(),
        TotalQty = 0, BLANK(), 
        TotalProfit < 0, -1,
        TRUE(), TotalProfit / TotalQty
    )
RETURN ConversionScore

<br/>

## 🖼️ Dashboard Snapshots

<br/>

<div align="center">
<img width="763" height="430" alt="image" src="https://github.com/user-attachments/assets/23a8341f-faac-4c94-b8d2-946bd09f168d" />


</div>
<br/>

<div align="center">
<img width="748" height="413" alt="image" src="https://github.com/user-attachments/assets/d0665487-6b03-4d15-b867-d0e2f4ba55aa" />

</div>




