
## 1. What is MongoDB, and how does it differ from relational databases?

Answer: MongoDB is a NoSQL, document-oriented database that stores data in flexible, JSON-like documents instead of rows and columns used in relational databases. Unlike SQL databases, MongoDB doesn’t require a predefined schema, which makes it suitable for handling unstructured data. It’s also highly scalable and supports a distributed architecture.


## 2. What is a Document in MongoDB?

Answer: In MongoDB, a document is a basic unit of data, stored in a JSON-like format called BSON (Binary JSON). Each document is a set of key-value pairs and can hold complex data types like arrays and nested documents, allowing for flexible data modeling.


## 3. What is a Collection in MongoDB?

Answer: A collection in MongoDB is similar to a table in relational databases. It’s a group of MongoDB documents. Collections do not enforce a schema, meaning documents within a collection can have different fields and data types.


## 4. What are the advantages of using MongoDB?

Answer: MongoDB offers several advantages:

Schema flexibility, allowing for unstructured data.

Horizontal scalability through sharding.

High performance for read and write operations.

Built-in replication for high availability.



## 5. How do you create and insert a document in MongoDB?

Answer:

// To create a collection and insert a document:
db.collectionName.insertOne({
  name: "John Doe",
  age: 25,
  profession: "Developer"
});

This code inserts a single document with fields name, age, and profession into the specified collection.


## 6. What is indexing in MongoDB, and why is it important?

Answer: Indexing in MongoDB improves the speed of data retrieval operations on a collection. Without indexes, MongoDB would need to scan every document in a collection to find the requested data, which can be inefficient for large datasets. Indexes make queries faster but come with a trade-off of additional storage and slower write operations.


## 7. Explain the difference between find() and findOne() in MongoDB.

Answer: find() returns all documents in a collection that match a query, whereas findOne() returns only the first document that matches the query. For example:

db.collectionName.find({ age: 25 }); // Returns all documents with age 25
db.collectionName.findOne({ age: 25 }); // Returns the first document with age 25


## 8. What is replication, and how does it work in MongoDB?

Answer: Replication in MongoDB involves synchronizing data across multiple servers to ensure data availability and redundancy. MongoDB uses replica sets, which are groups of mongod processes that maintain the same data. A replica set has a primary node that receives all write operations, and secondary nodes replicate the primary’s data, providing redundancy.


## 9. What is a primary and secondary node in a MongoDB replica set?

Answer: In a replica set, the primary node is the main server that handles all write operations, while secondary nodes are copies of the primary that replicate its data. If the primary node fails, an election takes place among secondary nodes to determine a new primary, ensuring high availability.


## 10. What is Sharding in MongoDB, and why is it used?

Answer: Sharding is MongoDB's method for distributing data across multiple servers, enabling horizontal scaling. Sharding is used to handle large datasets by distributing data evenly and allows MongoDB to perform operations faster on large collections. Each shard holds a subset of the data and operates as a mini MongoDB instance.


## 11. How do you delete documents in MongoDB?

Answer: MongoDB provides deleteOne and deleteMany methods. For example:

db.collectionName.deleteOne({ age: 25 }); // Deletes the first document with age 25
db.collectionName.deleteMany({ age: 25 }); // Deletes all documents with age 25


## 12. What is Aggregation in MongoDB?

Answer: Aggregation in MongoDB is a way to process data records and return computed results. It's similar to SQL’s GROUP BY clause. MongoDB uses an aggregation pipeline, where data passes through a series of stages that can filter, sort, or transform it.


## 13 What is the difference between SQL and NoSQL databases?

Answer: SQL databases are relational and use structured query language for defining and manipulating data, ensuring data integrity through ACID properties. They store data in tables with predefined schemas. NoSQL databases, like MongoDB, are non-relational and can store unstructured or semi-structured data. They allow for flexible schemas and can handle large volumes of diverse data types.

## 14.How does MongoDB handle data relationships?

Answer: MongoDB handles relationships in two primary ways:
Embedded Documents: Related data can be stored within a single document, which is useful for one-to-few relationships.
References: For one-to-many relationships, documents can reference other documents using their ObjectIDs. This allows for normalization but requires additional queries to retrieve related data.

## 15. What are some common operators used in MongoDB queries?

Common operators include:
Comparison Operators: $eq (equal), $ne (not equal), $gt (greater than), $lt (less than), $gte (greater than or equal to), $lte (less than or equal to).
Logical Operators: $and, $or, $not, $nor.
Element Operators: $exists (checks for the existence of a field), $type (checks the data type).


## 16.How would you use the aggregation framework to group data? Provide an example.


db.collectionName.aggregate([
  { $group: { _id: "$department", totalEmployees: { $sum: 1 } } }
]);
This example groups documents by the department field and counts the total number of employees in each department.


## 17.How do MongoDB queries differ from SQL queries?

Answer: MongoDB queries are written in a JSON-like format, while SQL queries use a structured query language. In MongoDB, data retrieval often involves using methods on collections, while SQL uses SELECT statements with clauses like WHERE, GROUP BY, and JOIN.



## 18. What is the purpose of the ObjectId in MongoDB?

Answer: The ObjectId is a unique identifier automatically generated by MongoDB for each document. It consists of a 12-byte value, ensuring uniqueness across collections and databases.


## 19.What is a stored procedure, and how does it differ in MongoDB compared to SQL databases?

Answer: In SQL databases, stored procedures are precompiled SQL code that can be executed as a single command. MongoDB does not have traditional stored procedures; instead, it uses JavaScript functions stored in the database. These functions can be executed with specific parameters, but they don't have the same level of performance optimization as SQL stored procedures.