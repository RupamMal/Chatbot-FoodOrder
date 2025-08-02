# Dialogflow Chatbot with MySQL Backend

This project is a food ordering chatbot integrated with Dialogflow and a Python backend using MySQL.

## Features

- Add, remove, and complete food orders
- Track order status
- Store and fetch data using MySQL procedures/functions

## Files

- `main.py` – Handles webhook requests from Dialogflow
- `db_helper.py` – Manages database operations
- `generic_helper.py` – Utility functions for formatting and session handling

## Setup

1. Install dependencies:
   ```bash
   pip install mysql-connector-python
Configure your MySQL connection in db_helper.py.

Ensure Dialogflow intents call the webhook and match:

order.add

order.remove

order.complete

track.order

License
MIT
