# Pizza Sales Analysis with Google BigQuery and Power BI

## 📊 Project Overview
This project analyzes pizza sales data to provide insights into business performance using **Google BigQuery** for SQL queries and **Power BI** for visualization. It focuses on key performance indicators (KPIs) and detailed analysis of sales trends, product performance, and revenue distribution.

## 💡 Problem Statement
The aim of this project is to evaluate the performance of a pizza business by analyzing:
1. **Total Revenue**: The sum of all pizza orders.
2. **Average Order Value**: The average revenue per order.
3. **Total Pizzas Sold**: Total quantities of pizzas sold.
4. **Total Orders**: Number of unique orders placed.
5. **Average Pizzas Per Order**: Average number of pizzas in each order.

## 🚀 Features
- **KPI Calculations**:
  - Total Revenue
  - Average Order Value
  - Total Pizzas Sold
  - Total Orders
  - Average Pizzas Per Order
- **Trends Analysis**:
  - Daily and Monthly Trends for Orders
- **Category and Size Analysis**:
  - Percentage of Sales by Pizza Category and Size
- **Performance Metrics**:
  - Top and Bottom Pizzas by Revenue, Quantity, and Total Orders

## 🛠️ Tools & Technologies
- **Google BigQuery**: For executing SQL queries to extract and process data.
- **Power BI**: For designing interactive dashboards and visualizing insights.

## 🗂️ SQL Queries
### KPI Queries
- **Total Revenue**:
  ```sql
  SELECT SUM(total_price) AS Total_Revenue FROM `pizza-sales-439307.PizzaSales.PizzaSalesTable`;
  ```
- **Average Order Value**:
  ```sql
  SELECT SUM(total_price)/COUNT(DISTINCT order_id) AS Average_Order_Value FROM `pizza-sales-439307.PizzaSales.PizzaSalesTable`;
  ```
- **Total Pizzas Sold**:
  ```sql
  SELECT SUM(quantity) AS Total_Pizza_sold FROM `pizza-sales-439307.PizzaSales.PizzaSalesTable`;
  ```
- **Total Orders**:
  ```sql
  SELECT COUNT(DISTINCT order_id) AS Total_Order FROM `pizza-sales-439307.PizzaSales.PizzaSalesTable`;
  ```
- **Average Pizzas Per Order**:
  ```sql
  SELECT ROUND(CAST(SUM(quantity) AS FLOAT64)/CAST(COUNT(DISTINCT order_id) AS FLOAT64), 2) AS Avg_Pizza_Per_Order FROM `pizza-sales-439307.PizzaSales.PizzaSalesTable`;
  ```

### Trend Analysis
- **Daily Orders Trend**:
  ```sql
  SELECT FORMAT_DATE('%A', order_date) AS order_day, COUNT(DISTINCT order_id) AS Total_orders FROM `pizza-sales-439307.PizzaSales.PizzaSalesTable` GROUP BY FORMAT_DATE('%A', order_date);
  ```
- **Monthly Orders Trend**:
  ```sql
  SELECT FORMAT_DATE('%B', order_date) AS Month_Name, COUNT(DISTINCT order_id) AS Total_orders FROM `pizza-sales-439307.PizzaSales.PizzaSalesTable` GROUP BY FORMAT_DATE('%B', order_date) ORDER BY Total_orders DESC;
  ```

### Performance Queries
- **Top 5 Pizzas by Revenue**:
  ```sql
  SELECT pizza_name, SUM(total_price) AS Total_Revenue FROM `pizza-sales-439307.PizzaSales.PizzaSalesTable` GROUP BY pizza_name ORDER BY Total_Revenue DESC LIMIT 5;
  ```
- **Bottom 5 Pizzas by Revenue**:
  ```sql
  SELECT pizza_name, SUM(total_price) AS Total_Revenue FROM `pizza-sales-439307.PizzaSales.PizzaSalesTable` GROUP BY pizza_name ORDER BY Total_Revenue LIMIT 5;
  ```
- **Top 5 Pizzas by Quantity**:
  ```sql
  SELECT pizza_name, SUM(quantity) AS Total_Quantity_Sold FROM `pizza-sales-439307.PizzaSales.PizzaSalesTable` GROUP BY pizza_name ORDER BY Total_Quantity_Sold DESC LIMIT 5;
  ```

*(Refer to the [uploaded script](#) for all SQL queries.)*

## 📈 Dashboards
### **Best/Worst Sellers Dashboard**
- **Top and Bottom 5 Pizzas by Revenue, Quantity, and Total Orders**
![Best/Worst Sellers Dashboard](dashboard%20best_worst%20sellers%20page.jpg)

### **Home Dashboard**
- **Daily and Monthly Trends**
- **Sales by Pizza Category and Size**
![Home Dashboard](dashboard%20home%20page.jpg)

## 🔑 Insights
- **Revenue Insights**:
  - The Thai Chicken Pizza generates the highest revenue.
  - Brie Carre Pizza contributes the least to revenue and orders.
- **Sales Trends**:
  - Orders are highest during weekends and evenings, especially in July and January.
  - Large-sized pizzas drive maximum sales.
- **Category Insights**:
  - The Classic category accounts for most sales and orders.

## 📥 Installation & Usage
1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo-name/pizza-sales-analysis.git
   ```
2. Open the SQL queries in **Google BigQuery** and run them on the dataset.
3. Import the **Power BI dashboards** to view insights interactively.

## 📚 References
- Dataset: [Pizza Sales Dataset](https://www.kaggle.com/)
- Tools: [Google BigQuery](https://cloud.google.com/bigquery), [Power BI](https://powerbi.microsoft.com/)

---

Would you like me to make any edits or enhancements to this README?
