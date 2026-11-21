# Project Documentation

## 1. Introduction

This project is a web-based restaurant and food ordering system developed as part of my bachelor's degree project.

The purpose of the application is to provide users with a simple way to browse restaurants and food items and place orders through a website.

The project also provides an administrator panel for managing restaurants, dishes, users and customer orders.

---

## 2. Project Objective

The main objectives of the project were:

- To develop a functional web application using PHP.
- To understand how a website communicates with a relational database.
- To implement user registration and authentication.
- To implement restaurant and food management.
- To develop a basic shopping cart.
- To implement an online ordering workflow.
- To create an administrator section for managing application data.

---

## 3. Problem Statement

Traditional food ordering through restaurants can require customers to contact restaurants directly or visit them physically.

The project attempts to provide a simple online alternative where customers can:

1. Browse restaurants.
2. View available dishes.
3. Select food items.
4. Add items to a cart.
5. Place an order.
6. View their order information.

---

## 4. Proposed Solution

The proposed solution is a PHP-based web application connected to a MySQL database.

The application is divided into:

- Customer interface
- Administrator interface
- Database

The customer interface handles food browsing and ordering.

The administrator interface handles the management of restaurants, dishes, users and orders.

---

## 5. Technologies

### Frontend

- HTML
- CSS
- Bootstrap
- JavaScript
- jQuery

### Backend

- PHP

### Database

- MySQL

### Development Environment

The original project was designed for a local PHP/MySQL environment.

---

## 6. Functional Requirements

### Customer

The customer should be able to:

- Create an account.
- Login to the system.
- View restaurants.
- View dishes.
- Add food to the cart.
- Change item quantities.
- Checkout.
- View previous orders.

### Administrator

The administrator should be able to:

- Login.
- Manage users.
- Manage restaurants.
- Manage restaurant categories.
- Manage dishes.
- View customer orders.
- Change order status.
- Add order remarks.

---

## 7. Non-Functional Requirements

At the level of this academic project, the system should:

- Provide a simple user interface.
- Respond to normal user actions.
- Store application data in a relational database.
- Maintain user sessions.
- Allow the administrator to manage application data.

---

## 8. Database Design

The system uses the following major entities:

```text
User
Restaurant Category
Restaurant
Dish
Order
Order Remark
Administrator
```

The database stores customer information, restaurant information, menu information and order information.

---

## 9. Implementation

The project uses PHP pages to implement individual parts of the application.

Examples include:

```text
index.php
login.php
registration.php
restaurants.php
dishes.php
product-action.php
checkout.php
your_orders.php
```

The administrator functionality is contained in the `admin` directory.

The database connection is handled through:

```text
connection/connect.php
```

---

## 10. Shopping Cart Implementation

The shopping cart is implemented using PHP sessions.

When a customer selects a dish, the application retrieves the dish information from the database and stores the selected item in the session cart.

The quantity can then be updated before checkout.

---

## 11. Order Processing

When the customer completes checkout, the selected cart items are inserted into the `users_orders` database table.

The administrator can then view the order and update its status.

The application also stores remarks associated with order processing.

---

## 12. Testing

The project was tested locally by running the PHP application and MySQL database.

The following major workflows were checked:

| Test                  | Expected Result                   |
| --------------------- | --------------------------------- |
| User registration     | New user is created               |
| User login            | User can access the application   |
| Restaurant browsing   | Restaurants are displayed         |
| Dish browsing         | Restaurant dishes are displayed   |
| Add to cart           | Item is added to session cart     |
| Quantity update       | Cart quantity changes             |
| Checkout              | Order is created                  |
| Order history         | User can view orders              |
| Admin login           | Admin panel is accessible         |
| Restaurant management | Restaurant records can be managed |
| Dish management       | Dish records can be managed       |
| User management       | User records can be managed       |
| Order management      | Admin can update order status     |

---

## 13. Limitations

The project was developed primarily for academic learning and demonstration.

Some limitations of the implementation include:

- The application uses an older PHP coding style.
- Security practices could be improved.
- Passwords use an older MD5-based implementation.
- Some database queries are constructed directly from user input.
- There is no online payment integration.
- There is no live delivery tracking.
- There is no automated testing framework.
- There is no production deployment configuration.
- The current "popular dishes" functionality is not a machine-learning recommendation system.

---

## 14. Future Improvements

The project could be improved by:

- Replacing MD5 with password hashing such as `password_hash()`.
- Using prepared statements consistently.
- Improving validation and error handling.
- Adding food and restaurant search.
- Adding ratings and reviews.
- Adding online payment.
- Adding delivery tracking.
- Adding email or notification functionality.
- Developing a personalized recommendation system.
- Adding automated tests.
- Migrating to a more modern PHP framework.
- Improving the frontend design.
- Deploying the application to a cloud platform.

---

## 15. Learning Outcomes

Through this project, I gained practical experience with:

- PHP web development.
- MySQL database usage.
- SQL queries.
- HTML and CSS.
- Bootstrap.
- JavaScript and jQuery.
- User authentication.
- PHP sessions.
- CRUD operations.
- Database-driven web applications.
- Basic system design.
- Debugging and local application deployment.

---

## 16. Conclusion

The project demonstrates the development of a basic database-driven food ordering website using PHP and MySQL.

Although the system is not intended to represent a production-level commercial platform, it provided practical experience in developing a complete web application from user registration through food selection, cart management and order processing.

The project can also serve as a foundation for future improvements such as modern security practices, automated testing, payment integration and personalized food recommendations.
