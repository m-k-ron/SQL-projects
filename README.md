# SQL guided project Maven Analytics restaurant order analytics SQL database

## Project overview

database in SQL (https://github.com/m-k-ron/SQL_projects/blob/eb2598ce42233c20da0c0513cbd45cc08f72e247/create_restaurant_db.sql)

```sql
1. View the menu_items table.
SELECT * FROM menu_items;

2. Find the number of items on the menu.
SELECT COUNT(*)
FROM menu_items;

3. What are the least and most expensive items on the menu?
SELECT *
FROM menu_items
WHERE price = (SELECT MAX(price) FROM menu_items) OR price = (SELECT MIN(price) FROM menu_items);

4. How many Italian dishes are on the menu?
SELECT COUNT(*)
FROM menu_items
WHERE category = 'Italian';

5. What are the least and most expensive Italian dishes on the menu?
SELECT *
FROM menu_items
WHERE category = 'Italian'
ORDER BY price DESC;

6. How many dishes are in each category?
SELECT COUNT(menu_item_id) AS count, category
FROM menu_items
GROUP BY category;

7. What is the average dish price within each category?
SELECT category, AVG(price) AS average_price
FROM menu_items
GROUP BY category;


1. View the order_details table.
SELECT * FROM order_details;

2. What is the date range of the table?
SELECT  MIN(order_date), MAX(order_date)
FROM order_details;

3. How many Irders were made within this date range?
SELECT COUNT(DISTINCT order_id) 
FROM order_details;

4. How many items were ordered within this date range?
SELECT COUNT(item_id) 
FROM order_details;

5. Which orders had the most number of items?
SELECT order_id, COUNT(item_id)
FROM order_details
GROUP BY order_id
ORDER BY COUNT(item_id) DESC;

6. How many orders had more than 12 items?
SELECT COUNT(*) FROM
(SELECT order_id, COUNT(item_id)
FROM order_details
GROUP BY order_id
HAVING COUNT(item_id) > 12) AS num_orders;

7. What is the average number of items ordered per order?
SELECT AVG(num_items) FROM
(SELECT order_id, COUNT(item_id) AS num_items
FROM order_details
GROUP BY order_id) AS avg_items;


1. Combine the menu_items and order_details tables into a single table.
SELECT * FROM menu_items;
SELECT * FROM order_details;
SELECT * FROM order_details od
FULL JOIN menu_items mi
ON od.item_id = mi.menu_item_id;

2. What were the least and most ordered items? What categories were they in?
SELECT * FROM order_details od
FULL JOIN menu_items mi
ON od.item_id = mi.menu_item_id
WHERE 

3. Ifat were the top 5 orders that spent the most money?


4. View the details of the highest spend order. What insights can you gather from the results?


5. View the details of the top 5 highest spend orders. What insights can you gather from the results?
