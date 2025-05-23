# 🍕 Pizza Sales SQL Analysis Project

## 📘 Project Description

This project analyzes a dataset of pizza sales transactions over the past month. The goal is to uncover insights such as sales performance, revenue patterns, and customer behavior using SQL queries. The dataset was created for this project aiming to learn and test SQL concepts such as aggregation, grouping, and filtering.

---

## 🗃️ Dataset Description

The dataset `pizza_sales` includes the following columns:

| Column Name       | Description                               |
|-------------------|-------------------------------------------|
| sale_id           | Unique identifier for each sale           |
| date              | Date of the transaction (no time)         |
| pizza_type        | Type of pizza sold                        |
| quantity          | Number of pizzas sold in that transaction |
| price_per_item    | Price of one pizza in that sale           |
| store_location    | Location of the store                     |
| payment_method    | Payment method used                       |
| total_price       | Total sale amount (quantity × price)      |

---

## 🔍 SQL Analysis Questions and Queries

### 1. How many total sales transactions were recorded in the last month?
```sql
SELECT COUNT(*) AS total_sales
FROM pizza_sales;
```
###
### 2. What is the total revenue generated from all pizza sales?
```sql
SELECT SUM(total_price) AS total_revenue
FROM pizza_sales;
```
###
### 3.	Which type of pizza was sold in the highest quantity?
```sql
SELECT pizza_type, SUM(quantity) AS total_quantity
FROM pizza_sales
GROUP BY pizza_type
ORDER BY total_quantity DESC
LIMIT 1;
```
###
### 4.	How many sales were made using each payment method?
```sql
SELECT payment_method, COUNT(*) AS total_orders
FROM pizza_sales
GROUP BY payment_method;
```
###
### 5.	How many pizzas were sold at each store location?
```sql
SELECT store_location, SUM(quantity) AS total_quantity_sold
FROM pizza_sales
GROUP BY store_location;
```
###
### 6.	Which three days generated the highest total sales revenue?
```sql
SELECT date, SUM(total_price) AS daily_revenue
FROM pizza_sales
GROUP BY date
ORDER BY daily_revenue DESC
LIMIT 3;
```
###
### 7.	What is the average value of an order at each store location?
```sql
SELECT store_location, AVG(total_price) AS avg_order_value
FROM pizza_sales
GROUP BY store_location;
```
###
### 8.	How does the popularity of each pizza type vary across different dates?
```sql
SELECT date, pizza_type, SUM(quantity) AS quantity_sold
FROM pizza_sales
GROUP BY date, pizza_type
ORDER BY date, quantity_sold DESC;
```
###
### 9.	Which pizza types brought in the most revenue?
```sql
SELECT pizza_type, SUM(total_price) AS revenue
FROM pizza_sales
GROUP BY pizza_type
ORDER BY revenue DESC
LIMIT 1;
```
###
### 10.	Which payment method is associated with the highest average order value?
```sql
SELECT payment_method, AVG(total_price) AS avg_order_value
FROM pizza_sales
GROUP BY payment_method
ORDER BY avg_order_value DESC
LIMIT 1;
```
###








