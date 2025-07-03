# TASK-7 Creating and Using Views in SQL
Objective: Understand how to create, use, and manage SQL views with simple examples.

🛠 Tools Used
DB-Fiddle.com (with MySQL 8.0)

🧾 What is a View?
A view is a saved SQL query that acts like a virtual table.
It does not store actual data but shows data from real tables in a simple way.

🧪 What We Did4331
0
✅ 1. Created Tables
We created two tables:

Customers: Holds customer details like ID, name, and city

Orders: Holds order details like order ID, amount, and date

✅ 2. Inserted Sample Data
We added example records to both tables for testing.

✅ 3. Created a View: CustomerOrderSummary
sql
Copy
Edit
CREATE VIEW CustomerOrderSummary AS
SELECT c.customer_id, c.name, c.city, o.order_id, o.total_amount
FROM Customers c
JOIN Orders o ON c.customer_id = o.customer_id;
🔎 This view combines customer and order data in one place, so we don’t have to write the full JOIN every time.

✅ 4. Queried the View
sql
Copy
Edit
SELECT * FROM CustomerOrderSummary;
SELECT * FROM CustomerOrderSummary WHERE city = 'Mumbai';
These queries showed the combined data and filtered it based on city.

✅ 5. Updated the Original Table
sql
Copy
Edit
UPDATE Customers
SET city = 'Pune'
WHERE customer_id = 2;
We updated the city of a customer directly in the original Customers table.
This change was also reflected in the view.

✅ 6. Created Another View: CustomerTotalOrders
sql
Copy
Edit
CREATE VIEW CustomerTotalOrders AS
SELECT c.customer_id, c.name, SUM(o.total_amount) AS total_spent
FROM Customers c
JOIN Orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_id, c.name;
📊 This view gives total amount spent by each customer.

🎯 Key Learnings
Views are useful for simplifying complex queries

You cannot update a view based on multiple tables

You can filter and reuse views like regular tables

Views help in data security and abstraction
