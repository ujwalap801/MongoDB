## Count Documents in MongoDB

To count the number of documents that match a specific query in a MongoDB collection, you can use the `count()` method.

### Example

To count the number of cars that are made by Tesla, use the following command:

```javascript
db.cars.find({ make: "Tesla" }).count();

## Sort Documents in MongoDB

To sort documents in a MongoDB collection, you can use the `sort()` method. This allows you to order the results either in ascending or descending order.

### Example

#### Sort in Ascending Order

To sort the documents by the `model` field in ascending order, you can use the following command:

```javascript
db.cars.find({}, { _id: 0, model: 1 }).sort({ model: 1 }); // Ascending

## Sort in Descending Order

To sort the documents by the `year` field in descending order, use the following command:

```javascript
db.cars.find().sort({ year: -1 }); // Sort by year in descending order


## Limit the Number of Documents

To limit the number of documents returned by a cursor in MongoDB, you can use the `limit()` method.

### Example

To limit the results to 5 documents, use the following command:

```javascript
db.cars.find().limit(5);


## Skip Documents

To skip a specified number of documents in MongoDB, you can use the `skip()` method.

### Example

To skip the first 10 documents and return the rest, use the following command:

```javascript
db.cars.find().skip(10);
