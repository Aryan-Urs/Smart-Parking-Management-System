# Smart Parking Management System

A comprehensive parking management solution built with a MySQL database and a Streamlit web interface. This system allows administrators to manage users, book reservations, and handle billing.

---
## 🚀 Features

* **Dashboard**: A real-time, color-coded visual grid of all parking spaces, showing their status as 'Available' or 'Occupied'.
* **User Management**: Full **CRUD** (Create, Read, Update, Delete) functionality for managing users (Students, Faculty, Staff).
    * Prevents deactivation of users with pending payments.
    * Prevents deletion of users with pending payments.
* **Reservation System**:
    * Book a parking space for a specific user and time slot.
    * The system only shows 'Available' spaces for new bookings.
    * Automatically marks the space as 'Occupied' on the dashboard.
    * Prevents 'Inactive' users from making new reservations.
* **Billing & Release**:
    * A "Release Reservation" feature to complete a booking.
    * Automatically generates a 'Pending' bill in the `PAYMENT` table.
    * Automatically creates a log entry in the `OCCUPANCY_LOG`.
    * Updates the parking space status back to 'Available'.
* **Payment Portal**:
    * View all pending bills and payment history for any user.
    * Allows an admin to "Mark as Paid" to complete a billing cycle.

---

## 💻 Tech Stack

* **Frontend**: Streamlit
* **Backend**: Python
* **Database**: MySQL
* **Python Libraries**: `streamlit`, `mysql-connector-python`, `pandas`

---

## 📂 Project Structure
```bash
smart-parking-project/
├── .streamlit/
│   └── secrets.toml        
├── db/
│   ├── schema.sql            
│   └── smart_parking_logic.sql 
├── app.py                 
├── er_diagram.png         
├── requirements.txt       
└── README.md              

```
---

## 🔧 Setup and Installation

Follow these steps to run the project locally.

### 1. Database Setup

1.  Ensure you have a MySQL server running.
2.  Open your MySQL client (like MySQL Workbench) and run the `smart_parking_final.sql` file (the one with the `CREATE TABLE` statements) to create the database schema.
3.  Next, run the `smart_parking_logic_v4.sql` file (or the latest version) to create all the necessary stored procedures, functions, and triggers.

### 2. Python Environment

1.  **Clone the repository:**
    ```bash
    git clone <your-github-repo-url>
    cd smart-parking-project
    ```

2.  **Create a virtual environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3.  **Install the required packages:**
    ```bash
    pip install -r requirements.txt
    ```

### 3. Configure Credentials

1.  Create a new folder named `.streamlit` in the project's root directory.
2.  Inside this folder, create a file named `secrets.toml`.
3.  Add your MySQL credentials to this file. **(This file is in .gitignore and should NOT be pushed to GitHub)**.

    ```toml
    # .streamlit/secrets.toml

    [mysql]
    host = "localhost"
    user = "your_mysql_user"
    password = "your_mysql_password"
    database = "smart_parking_final"
    ```

### 4. Run the Application

Once your database is set up and your `secrets.toml` file is in place, run the following command in your terminal:

```bash
streamlit run app.py
