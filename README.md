# 🚀 **Domino’s Pizza Sales Analysis – SQL Case Study**

A comprehensive SQL-driven analysis of Domino’s pizza sales, customer behavior, product performance, and operational insights.
This project demonstrates strong analytical thinking, data modeling, business understanding, and advanced SQL proficiency—ideal for Data Analyst & Business Analyst roles.

---

## 📊 **Project Overview**

This project explores the complete Domino’s pizza ordering dataset to uncover actionable business insights.
Using SQL, I analyzed customer order patterns, top-performing pizzas, revenue drivers, time-based trends, and operational KPIs.

The goal is to replicate real-world analytics used by product, marketing, and operations teams.

---

## 🧩 **Dataset Description**

The project is based on six interconnected CSV files:

| File                  | Description                        |
| --------------------- | ---------------------------------- |
| **customers.csv**     | Customer details                   |
| **orders.csv**        | Order metadata (dates, timestamps) |
| **order_details.csv** | Line-item details for each order   |
| **pizzas.csv**        | Pizza size & pricing info          |
| **pizza_types.csv**   | Pizza categories & names           |
| **SQL Queries.txt**   | All project queries                |

The schema shows full relational mapping between customers, orders, pizzas, and order items.

---

## 🛠️ **Skills & Concepts Applied**

* Joins (INNER, LEFT)
* Aggregations & Grouping
* Window Functions (LAG, LEAD, RANK, CUME_DIST)
* CTEs for modular analysis
* Date/Time functions (daily, weekly, monthly trends)
* Running totals & cumulative metrics
* Segmentation (customer-level insights)
* KPI building for business teams
* Ranking & product-level performance analytics

---

## 📌 **Key Business Questions Solved**

### **✔ Sales & Growth**

* Monthly & yearly order trends
* Month-over-month (MoM) & year-over-year (YoY) growth
* Daily order patterns (weekday vs weekend)

### **✔ Customer Insights**

* Average orders per customer
* Top repeat customers
* High-value customer identification

### **✔ Product & Menu Insights**

* Top 5 best-selling pizzas
* Category-wise demand (Veg, Classic, Supreme, Chicken)
* Pizza size revenue contribution (S, M, L, XL, XXL)

### **✔ Operational Metrics**

* Cumulative orders
* Peak-order hours
* Daily demand forecasting (linear trend)

---

## 🧠 **Highlighted SQL Queries**

### 🔹 Top 5 Best-Selling Pizzas

```sql
SELECT 
    pt.name AS pizza_name,
    SUM(od.quantity) AS total_quantity_sold
FROM pizza_types pt
JOIN pizzas p ON pt.pizza_type_id = p.pizza_type_id
JOIN order_details od ON od.pizza_id = p.pizza_id
GROUP BY pt.name
ORDER BY total_quantity_sold DESC
LIMIT 5;
```

### 🔹 Average Orders per Customer

```sql
WITH t AS (
    SELECT c.custid, COUNT(o.order_id) AS total_orders
    FROM customers c
    LEFT JOIN orders o ON c.custid = o.custid
    GROUP BY c.custid
)
SELECT ROUND(AVG(total_orders), 2) AS avg_orders_per_customer
FROM t;
```

### 🔹 Daily Cumulative Sales

```sql
SELECT 
    order_date,
    COUNT(order_id) AS daily_orders,
    SUM(COUNT(order_id)) OVER(ORDER BY order_date) AS cumulative_orders
FROM orders
GROUP BY order_date
ORDER BY order_date;
```

---

## 📈 **Key Insights Generated**

* **Large pizzas contribute the highest revenue**, signaling customer preference for bigger sizes.
* **Weekends show significantly higher order volume**, ideal for targeted promotions.
* **A small segment of repeat customers drives majority of orders**, useful for loyalty programs.
* **Classic & Veg pizzas dominate demand**, aligning inventory planning.
* **Steady month-over-month growth** indicates improving customer retention.

---

## 🧰 **Tools Used**

* **PostgreSQL** (Primary analysis)
* **Excel / CSV** (Data Storage)
* **Git & GitHub** (Version control)

---

## 🙋‍♂️ **About Me – Hitesh Moota**
📧 **Email:** [hiteshmoota1@gmail.com](mailto:hiteshdataman@gmail.com)



