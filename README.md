**Store & Product Management System**

I was responsible for developing the **backend** part of the system using **Spring Boot**, **MySQL**, and **MongoDB**.  
My tasks included:
- Designing and implementing database models and entity relationships  
- Building RESTful APIs for product, store, inventory, order, and review management  
- Implementing business logic in service and controller layers  
- Integrating the backend with both MySQL and MongoDB databases  
- Writing stored procedures for monthly and aggregate sales reports  

The **frontend** part (UI design, HTML, CSS, JavaScript) was developed by another team member.  
I integrated the backend APIs to ensure full end-to-end functionality.

Features

- Store Management – Add and validate stores
- Product Management – Create, update, delete, and search products
- Inventory Management – Track product stock across multiple stores
- Order Handling – Process customer orders and update inventory automatically
- Review System – Manage product reviews stored in MongoDB
- Stored Procedures – Generate monthly and aggregate sales reports

| Layer        | Technology                   | Description                                          |
| ------------ | ---------------------------- | ---------------------------------------------------- |
| **Frontend** | HTML, CSS, JavaScript        | Handles user interface and requests to backend APIs  |
| **Backend**  | Spring Boot (REST, MVC, JPA) | Core business logic and database processing          |
| **Database** | MySQL + MongoDB              | Relational data (products, orders) + NoSQL (reviews) |

⚙️ Backend Modules

Part 1 — Database Configuration

Configured connection to MySQL and MongoDB in application.properties

Added dependencies: Spring Boot JPA, MongoDB, and Actuator

Part 2 — Model Layer

Defined entities with JPA annotations and relationships:

Customer, Store, Product, Inventory, OrderDetails, OrderItem (MySQL)

Review (MongoDB)

Part 3 — Repository & Service Layer

Used JpaRepository / MongoRepository for CRUD operations

Implemented custom queries for filtering by category, store, and product name

Business logic handled in OrderService and ServiceClass
(e.g., order creation, stock update, data validation)

Part 4 — Controller Layer

Exposed REST API endpoints:

/product : manage products 

/inventory : update & validate stock

/store : add stores & place orders

/reviews : fetch reviews with customer details

Global exception handling via GlobalExceptionHandler

Part 5 - Database Initialization
Load MySQL Data
create database inventory;
mysql -h {MYSQL_HOST} -uroot -p{MYSQL_PASSWORD} < insert_data.sql

Load MongoDB Data
mongoimport --uri="mongodb://root:{MONGODB_PASSWORD}@{MONGODB_HOST}/reviews?authSource=admin" \
--collection=reviews --file reviews.json --jsonArray

| Procedure                                      | Description                      |
| ---------------------------------------------- | -------------------------------- |
| `GetMonthlySalesForEachStore(year, month)`     | Monthly sales per store          |
| `GetAggregateSalesForCompany(year, month)`     | Total sales for company          |
| `GetTopSellingProductsByCategory(month, year)` | Top-selling product per category |
| `GetTopSellingProductByStore(month, year)`     | Top-selling product per store    |
