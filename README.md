#  Aggregation

1. Table Creation and Data Insertion
```sql
CREATE TABLE Orders (
    order_id INT PRIMARY KEY,
    user_name VARCHAR(50),
    total_amount DECIMAL(10, 2),
    order_date DATE
);

INSERT INTO Orders (order_id, user_name, total_amount, order_date) VALUES
(101, 'Rahul', 1250.00, '2026-09-01'),
(102, 'Priya', 850.50, '2026-09-02'),
(103, 'Rahul', 2100.00, '2026-09-05'),
(104, 'Amit', NULL, '2026-09-10'),
(105, 'Priya', 450.00, '2026-09-12');

Orders Placed ..
SELECT 
    user_name, 
    COUNT(order_id) AS order_count
FROM Orders
GROUP BY user_name;

Average Total Amount of All Orders

SELECT 
    AVG(total_amount) AS average_order_amount
FROM Orders;

Highest and Lowest Order Amounts

SELECT 
    MAX(total_amount) AS highest_order_amount,
    MIN(total_amount) AS lowest_order_amount
FROM Orders;

Total Sales (Excluding NULL Values)

SELECT 
    SUM(total_amount) AS total_sales
FROM Orders
WHERE total_amount IS NOT NULL;
