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
