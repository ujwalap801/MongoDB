# Database Overview

## What is a Database?
A database is an organized collection of data that allows for efficient manipulation and access.


### Key Concepts

- **Collections**: A collection is a group of MongoDB documents, similar to a table in relational databases. It acts as a container for documents.

- **Documents**: A document is a set of key-value pairs, analogous to a row in a table. It is represented as a JSON-like record within a collection.

- **Fields**: A field is a key-value pair within a document, comparable to a column in a relational database.

# MySQL
### MySQL is a relational database management system (RDBMS) that stores data in structured tables using rows and columns.
### It follows the SQL (Structured Query Language) standard and uses a fixed schema, meaning the structure of the data (columns) must be defined before inserting any data.
### MySQL enforces relationships between tables using foreign keys and supports complex queries involving joins.

# MongoDB

### MongoDB, on the other hand, is a NoSQL database that stores data in a flexible, document-oriented format. 
### Instead of tables, MongoDB stores data in JSON-like documents called BSON (Binary JSON).
### MongoDB does not require a predefined schema, allowing for more flexibility, which makes it suitable for applications with rapidly changing data structures or unstructured data.



## Key Differences:
## Data Structure:
MySQL: Data is stored in tables with rows and columns (structured).
MongoDB: Data is stored in documents, which are collections of key-value pairs (semi-structured).

## Schema:

MySQL: Schema is fixed, and you need to define the structure before inserting data.
MongoDB: Schema is flexible, meaning documents in the same collection can have different structures


# MySQL Example: Users and Orders Relationship

This example demonstrates how to store information about users and their orders using **MySQL** with two related tables: `Users` and `Orders`. The relationship is established using a **foreign key**.

### Users Table
The `Users` table stores user information such as `id`, `name`, and `email`.


CREATE TABLE Users (
    id INT PRIMARY KEY,
    name VARCHAR(50),
    email VARCHAR(100)
);



# Orders Table in MySQL

This example demonstrates the creation of an `Orders` table in **MySQL**, which establishes a relationship with the `Users` table using a **foreign key**. This enforces a structured relationship between users and their orders.

### SQL Code:
CREATE TABLE Orders (
    id INT PRIMARY KEY,
    user_id INT,
    product_name VARCHAR(100),
    FOREIGN KEY (user_id) REFERENCES Users(id)
);


This example demonstrates the creation of an `Orders` table in **MySQL**, which establishes a relationship with the `Users` table using a **foreign key**. This enforces a structured relationship between users and their orders.

SQL Code:
``sql
CREATE TABLE Orders (
    id INT PRIMARY KEY,
    user_id INT,
    product_name VARCHAR(100),
    FOREIGN KEY (user_id) REFERENCES Users(id)
);


# MongoDB: The same data can be stored in a more flexible way, where each user document can include their orders directly within the same document (denormalized).

### Document Example:

### JSON Document:
``json
{
    "_id": 1,
    "name": "John Doe",
    "email": "john@example.com",
    "orders": [
        { "product_name": "Laptop" },
        { "product_name": "Mouse" }
    ]
}


# MongoDB Atlas is a cloud database service provided by MongoDB. It allows you to deploy, manage, and scale MongoDB databases easily in the cloud. With Atlas, you can create clusters, monitor performance, automate backups, and ensure high availability without the complexities of managing the underlying infrastructure. 
# It's available on major cloud providers like AWS, Google Cloud, and Azure, making it convenient for developers to build and scale applications without worrying about database management.