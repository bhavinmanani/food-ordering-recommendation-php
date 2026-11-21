# Restaurant Food Ordering Website

A web-based food ordering system developed as a bachelor's degree project. The application allows users to browse restaurants and dishes, add food items to a shopping cart, place orders, and view their previous orders.

The system also includes an administrator section for managing restaurants, food items, users, categories, and customer orders.

> **Original Project Title:** Recommendation-Based Food Ordering Website\
> **Project Type:** Bachelor's Degree Project

---

## Project Overview

The main purpose of this project was to develop a simple online platform where customers can explore restaurants and food items and place food orders through a web interface.

The system contains two main parts:

1. **Customer/User Website**
2. **Administrator Panel**

The customer side focuses on browsing restaurants and dishes and placing orders, while the administrator side provides basic management functionality for the application.

---

## Main Features

### Customer Features

- User registration
- User login and logout
- Browse restaurants
- Browse restaurants by category
- View available dishes
- View dish prices and descriptions
- Add dishes to shopping cart
- Increase or decrease item quantities
- Place food orders
- View previous orders
- Delete orders where supported
- Session-based cart management

### Administrator Features

- Administrator login
- Administrator registration using an admin code
- Dashboard
- Manage restaurants
- Add, edit and delete restaurants
- Manage restaurant categories
- Manage dishes/menu items
- Add, edit and delete dishes
- Manage registered users
- Update and delete users
- View customer orders
- Update order status
- Add remarks to orders

---

## Technologies Used

### Frontend

- HTML
- CSS
- Bootstrap
- JavaScript
- jQuery

### Backend

- PHP
- MySQL/MariaDB

### Other

- PHP Sessions
- MySQLi
- SQL database
- Local PHP development server

---

## System Architecture

The project follows a simple three-layer structure:

```text
User Interface
      │
      ▼
PHP Application
      │
      ▼
MySQL Database
```

The PHP files handle the application logic and communicate with the MySQL database using MySQLi.

---

## Database

The application uses a database named:

```text
online_rest
```

Main database tables include:

```text
admin
admin_codes
users
restaurant
res_category
dishes
users_orders
remark
```

Basic relationship:

```text
Restaurant Category
        │
        ▼
    Restaurant
        │
        ▼
      Dishes


      Users
        │
        ▼
   Users Orders
        │
        ▼
      Remarks
```

---

## How the Ordering Process Works

```text
User
 │
 ├── Register / Login
 │
 ▼
Browse Restaurants
 │
 ▼
Select Restaurant
 │
 ▼
View Dishes
 │
 ▼
Add Food to Cart
 │
 ▼
Review Cart
 │
 ▼
Checkout
 │
 ▼
Order Stored in Database
 │
 ▼
Admin Views Order
 │
 ▼
Admin Updates Order Status
 │
 ▼
User Views Order Status
```

---

## Installation

### Requirements

The original project was designed to run using a local PHP/MySQL environment such as XAMPP, WAMP, MAMP or LAMP.

For a modern macOS development environment, PHP and MySQL can also be installed separately.

Required components:

- PHP
- MySQL
- Web browser

---

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR-USERNAME/restaurant-food-ordering-website.git
cd restaurant-food-ordering-website
```

---

### 2. Create the Database

Create a MySQL database named:

```text
online_rest
```

Then import the SQL file located in:

```text
database/online_rest.sql
```

For example:

```bash
mysql -u root online_rest < database/online_rest.sql
```

---

### 3. Configure Database Connection

Open:

```text
connection/connect.php
```

Update the database settings if required:

```php
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "online_rest";
```

The exact values may depend on your local MySQL installation.

---

### 4. Start the PHP Server

From the project directory:

```bash
php -S localhost:8000
```

Then open:

```text
http://localhost:8000
```

---

## Project Structure

```text
restaurant-food-ordering-website/
│
├── admin/               # Administrator panel
├── connection/          # Database connection
├── css/                 # Stylesheets
├── js/                  # JavaScript files
├── scss/                # SCSS source
├── images/              # Website and food images
├── fonts/               # Font resources
├── database/            # SQL database files
│
├── index.php            # Homepage
├── login.php            # User login
├── registration.php     # User registration
├── restaurants.php      # Restaurant listing
├── dishes.php           # Restaurant dishes
├── product-action.php   # Cart operations
├── checkout.php         # Order placement
├── your_orders.php      # User order history
└── README.md
```

---

## Project Workflow

The basic application workflow is:

```text
Registration
     ↓
Login
     ↓
Browse Restaurants
     ↓
Select Restaurant
     ↓
Browse Dishes
     ↓
Add Items to Cart
     ↓
Checkout
     ↓
Order Created
     ↓
Admin Processes Order
     ↓
Order Status Updated
     ↓
User Checks Order
```

---

## Important Note About Recommendations

The original project was titled **Recommendation-Based Food Ordering Website**.

The current implementation contains a "Popular Dishes" section and restaurant/category-based browsing, but it does not contain a machine-learning recommendation model or a personalized recommendation algorithm.

Therefore, this repository describes the implemented functionality rather than claiming an AI/ML recommendation system that is not present in the code.

---

## Limitations

This project was developed as a bachelor's-level academic project and was not designed as a production-ready commercial application.

Some limitations include:

- Basic PHP architecture
- Limited input validation
- Older PHP coding practices
- Simple session-based shopping cart
- Basic order management
- No payment gateway
- No real-time delivery tracking
- No advanced recommendation algorithm
- No automated testing framework
- No production deployment configuration

---

## Future Improvements

Possible future improvements include:

- Password hashing using modern algorithms
- Prepared statements throughout the application
- Improved input validation
- Better error handling
- Responsive UI improvements
- Online payment integration
- Restaurant search
- Food search and filtering
- User ratings and reviews
- Personalized food recommendations
- REST API integration
- Automated testing
- Modern PHP architecture
- Deployment to a cloud server

---

## Academic Context

This project was created as part of my bachelor's degree studies to gain practical experience in:

- Web development
- PHP programming
- Database design
- SQL
- User authentication
- CRUD operations
- Session management
- E-commerce/order workflows
- Frontend development

---

## Author

**Bhavin Manani**

This repository contains an academic project developed during my bachelor's degree.
