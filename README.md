# Real Estate Management System

A Real Estate Management System built with Python and SQLite for managing properties, clients, and transactions. This project demonstrates CRUD operations with database connectivity using SQLite.

## Table of Contents
- [Web App Features](#web-app-features)
- [Prerequisites](#prerequisites)
- [Project Structure](#project-structure)
- [Setup Instructions](#setup-instructions)
- [Running the Project](#running-the-project)
- [Usage](#usage)
- [Troubleshooting](#troubleshooting)

## Web App Features

The application provides the following features:

1. **User Authentication**:
   - Secure login and registration for users.
   - Role-based access control (Admin/Agent/Client).

2. **Property Management**:
   - Add, update, and delete property listings with details such as location, type, price, and size.
   - Search and filter properties by criteria such as location, price range, and property type.

3. **Client Management**:
   - Add and manage client information.
   - Assign clients to agents and track interactions.

4. **Transaction Management**:
   - Record property transactions (sales and rentals).
   - View transaction history with filtering options.

5. **Dashboard**:
   - Displays key metrics such as total properties, recent transactions, and client interactions.

6. **Responsive Design**:
   - Optimized for use on desktops, tablets, and mobile devices.

## Prerequisites

Before you can run the project, make sure you have the following installed:

1. **Python**: Version 3.6 or higher.
2. **SQLite**: Pre-installed with most Python distributions.
3. **Python Libraries**:
   - Install the required libraries listed in `requirements.txt`.

## Project Structure

The project is organized as follows:

```
RealEstateManagementSystem/
├── src/
│   ├── main/
│   │   ├── dao/              # Data Access Objects (for database operations)
│   │   ├── model/            # Database models (e.g., Property, Client, Transaction)
│   │   ├── util/             # Utility classes (e.g., DBConnection)
│   │   └── main.py           # Main file for running the project
├── static/                   # Static files (CSS, JavaScript, images)
├── templates/                # HTML templates for the web app
├── db/                       # Database setup script
│   └── real_estate_db.sql    # SQL script to set up the database
├── requirements.txt          # Required Python libraries
└── README.md                 # Project documentation
```

- **`dao/`**: Contains classes for database operations.
- **`model/`**: Contains Python classes representing the `Property`, `Client`, and `Transaction` tables.
- **`util/`**: Contains utility classes such as `DBConnection` for managing database connections.
- **`db/`**: Contains SQL script to set up the SQLite database and tables.

## Setup Instructions

Follow these steps to set up and run the project:

### 1. Clone or Download the Project
- Clone the repository or download the project files.

### 2. Set Up the Database

1. Open a terminal and navigate to the `db/` directory.
2. Run the SQL script located at `db/real_estate_db.sql` to create the necessary database and tables:

    ```sql
    -- Use this SQL script to set up the database
    CREATE TABLE IF NOT EXISTS Property (
        property_id INTEGER PRIMARY KEY AUTOINCREMENT,
        address TEXT NOT NULL,
        type TEXT NOT NULL,
        price REAL NOT NULL,
        size INTEGER NOT NULL
    );

    CREATE TABLE IF NOT EXISTS Client (
        client_id INTEGER PRIMARY KEY AUTOINCREMENT,
        name TEXT NOT NULL,
        email TEXT NOT NULL,
        phone TEXT NOT NULL
    );

    CREATE TABLE IF NOT EXISTS Transaction (
        transaction_id INTEGER PRIMARY KEY AUTOINCREMENT,
        property_id INTEGER,
        client_id INTEGER,
        transaction_type TEXT NOT NULL,
        transaction_date TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
        FOREIGN KEY (property_id) REFERENCES Property(property_id),
        FOREIGN KEY (client_id) REFERENCES Client(client_id)
    );
    ```

### 3. Install Dependencies

Install the required Python libraries:

```bash
pip install -r requirements.txt
```

### 4. Configure Database Connection

The SQLite database is configured by default in `util/DBConnection.py`. No further setup is required unless you want to use a different database.

## Running the Project

1. **Navigate to the Project Directory**:
   ```bash
   cd src/main/
   ```

2. **Run the Application**:
   ```bash
   python main.py
   ```

3. Access the application in your web browser at `http://localhost:5000`.

## Usage

Once the project is running, you can:

1. **Log In or Register**:
   - Admin: Manage properties, clients, and view reports.
   - Agent: Manage assigned properties and clients.
   - Client: Browse property listings and initiate transactions.

2. **Add Properties**:
   - Enter property details such as address, type, price, and size.

3. **Manage Clients**:
   - Add and update client details and assign clients to agents.

4. **Record Transactions**:
   - Choose a property, client, and transaction type (sale/rental).

5. **View Dashboard**:
   - Monitor key metrics and view recent transactions.

## Troubleshooting

- **Database Connection Error**:
    - Ensure the SQLite database file is present and correctly configured in `DBConnection.py`.

- **Missing Dependencies**:
    - Install missing libraries using `pip install -r requirements.txt`.

- **Port Already in Use**:
    - Stop any other application running on port 5000 or change the port in `main.py`.

---

This guide should help you set up and use the Real Estate Management System. For further assistance, please consult the project's documentation or contact the development team.
