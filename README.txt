
# Dialogflow Chatbot with MySQL Backend

This repository contains a Dialogflow-integrated chatbot backed by a Python service that connects to a MySQL database. It allows users to place, modify, and track food orders via conversational interface.

## 🛠 Features

- Add food items to an order with specified quantities
- Remove items from the current order
- Complete an order and get the total price
- Track the status of a placed order
- Integrates with MySQL using stored procedures and functions

## 🧱 Tech Stack

- **Dialogflow CX/ES** — for intent detection and conversation flow
- **Python 3** — backend logic and webhook handler
- **MySQL** — stores orders, tracks status, and calculates totals

## 📂 File Overview

- `main.py` — Handles Dialogflow webhook requests and routes intents
- `db_helper.py` — Manages MySQL connection, inserts, and queries
- `generic_helper.py` — Contains utility functions for session parsing and formatting

## ⚙️ Setup Instructions

### 1. Clone the Repository
```bash
git clone https://github.com/your-username/your-repo-name.git
cd your-repo-name
````

### 2. Install Dependencies

```bash
pip install mysql-connector-python
```

### 3. Configure Database

Ensure a MySQL database named `food_order` is available with the required tables, stored procedures, and functions. Update credentials in `db_helper.py`:

```python
cnx = mysql.connector.connect(
    host="localhost",
    user="your_username",
    password="your_password",
    database="food_order"
)
```

### 4. Dialogflow Setup

Create and configure intents in Dialogflow with webhook fulfillment:

* `order.add - context: ongoing-order`
* `order.remove - context: ongoing-order`
* `order.complete - context: ongoing-order`
* `track.order - context: ongoing-tracking`

Point the webhook to your deployed Python server.

## ✅ Example Stored Procedure & Function

```sql
-- Stored Procedure
DELIMITER //
CREATE PROCEDURE insert_order_item (
    IN food_item VARCHAR(255),
    IN quantity INT,
    IN order_id INT
)
BEGIN
    INSERT INTO orders (order_id, food_item, quantity)
    VALUES (order_id, food_item, quantity);
END //
DELIMITER ;

-- Function
CREATE FUNCTION get_total_order_price(order_id INT)
RETURNS DECIMAL(10,2)
BEGIN
    DECLARE total DECIMAL(10,2);
    SELECT SUM(quantity * price) INTO total
    FROM orders
    JOIN menu ON orders.food_item = menu.food_item
    WHERE orders.order_id = order_id;
    RETURN total;
END;
```

## 🚀 Deployment (Optional with FastAPI)

Wrap `handle_request()` inside a FastAPI route for live deployment.

## 📄 License

MIT License

```

--- 

You can copy and paste this content into a file named `README.md` in your repository. Let me know if you want to include deployment or testing instructions as well.
```
