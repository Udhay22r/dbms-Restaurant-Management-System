
# 🍽️ Restaurant Management System

A simple and efficient Python-based restaurant management system that helps you manage orders, menu items, and customer data using MySQL database.


## ✨ Features

- 📋 **Menu Management** - Display menu items with descriptions and prices
- 🛒 **Order Creation** - Create new orders with multiple items
- 📊 **Order Tracking** - View all orders and their details
- 👥 **Customer Management** - Track customer information and table assignments
- 💾 **Database Storage** - Secure MySQL database for data persistence


Restaurant Management System
1. Display menu
2. Create order
3. Display orders
4. Display order details
5. Exit
```

### Menu Options

| Option | Description |
|--------|-------------|
| **1** | View all available menu items with prices |
| **2** | Create a new order by selecting items and quantities |
| **3** | View all existing orders |
| **4** | View detailed information for a specific order |
| **5** | Exit the application |

## 🗄️ Database Schema

The system uses three main tables with the following structure:

### 📋 Menu Table
Stores all available menu items with their details.

| Column | Type | Description |
|--------|------|-------------|
| `item_id` | INT AUTO_INCREMENT PRIMARY KEY | Unique identifier for each menu item |
| `item_name` | VARCHAR(50) NOT NULL | Name of the menu item |
| `item_description` | TEXT | Detailed description of the item |
| `item_price` | DECIMAL(5,2) NOT NULL | Price of the item |

**Sample Data:**
```
| item_id | item_name           | item_description                                    | item_price |
|---------|---------------------|-----------------------------------------------------|------------|
| 1       | Cheeseburger        | Juicy beef patty with melted cheese                 | 9.99       |
| 2       | Margherita Pizza    | Classic pizza with tomato sauce and fresh mozzarella| 11.99      |
| 3       | Caesar Salad        | Crisp romaine lettuce with Parmesan cheese and croutons| 7.99    |
| 4       | Spaghetti Bolognese | Hearty meat sauce served over al dente spaghetti     | 12.99      |
| 5       | Grilled Salmon      | Fresh Atlantic salmon grilled to perfection          | 18.99      |
```

### 🛒 Orders Table
Tracks customer orders and timestamps.

| Column | Type | Description |
|--------|------|-------------|
| `order_id` | INT AUTO_INCREMENT PRIMARY KEY | Unique identifier for each order |
| `customer_name` | VARCHAR(50) NOT NULL | Name of the customer |
| `order_timestamp` | TIMESTAMP DEFAULT CURRENT_TIMESTAMP | When the order was placed |

**Sample Data:**
```
| order_id | customer_name | order_timestamp        |
|----------|---------------|------------------------|
| 1        | John Smith    | 2024-01-15 14:30:25    |
| 2        | Jane Doe      | 2024-01-15 15:45:12    |
| 3        | Mike Johnson  | 2024-01-15 16:20:08    |
```

### 📊 Order Details Table
Links orders to specific menu items with quantities.

| Column | Type | Description |
|--------|------|-------------|
| `order_id` | INT NOT NULL | References the order |
| `item_id` | INT NOT NULL | References the menu item |
| `quantity` | INT NOT NULL | Number of items ordered |
| **PRIMARY KEY** | `(order_id, item_id)` | Composite primary key |
| **FOREIGN KEY** | `order_id` → `orders(order_id)` | Links to orders table |
| **FOREIGN KEY** | `item_id` → `menu(item_id)` | Links to menu table |

**Sample Data:**
```
| order_id | item_id | quantity |
|----------|---------|----------|
| 1        | 1       | 2        |
| 1        | 3       | 1        |
| 2        | 2       | 1        |
| 2        | 4       | 2        |
| 3        | 5       | 1        |
```

**Key Relationships:**
- One menu item can be in multiple orders (one-to-many)
- One order can contain multiple menu items (one-to-many)
- Order details table acts as a junction table between orders and menu items

## 🚀 Quick Start

### Prerequisites

- **Python 3.x** - [Download here](https://www.python.org/downloads/)
- **MySQL Server** - [Download here](https://dev.mysql.com/downloads/mysql/)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/your_username/restaurant-management.git
   cd restaurant-management
   ```

2. **Install Python dependencies**
   ```bash
   pip install mysql-connector-python pymysql tabulate faker
   ```

3. **Setup MySQL Database**
   - Install MySQL Server
   - Create a database named `restaurant`
   - Update database credentials in the Python files

4. **Initialize the database**
   ```bash
   python create_database.py
   python populate_database.py
   ```

5. **Run the application**
   ```bash
   python main.py
   ```


## 🔧 Configuration

Before running the application, update the database connection details in:

- `main.py` (lines 4-7)
- `create_database.py` (lines 4-6)
- `populate_database.py` (lines 6-8)



