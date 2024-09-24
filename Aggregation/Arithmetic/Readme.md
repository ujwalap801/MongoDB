## Aggregation with `$project`

The `$project` stage in MongoDB's aggregation framework is used to reshape documents by including, excluding, or adding new fields. You can use it to perform operations on existing fields, such as calculations or transformations.

### Example

To add 50,000 to the `price` field of each document while including the `model` and excluding the `_id` field, use the following command:

```javascript
db.cars.aggregate([
    {
        $project: {
            model: 1,
            _id: 0,
            price: { $add: ["$price", 50000] } // Add 50,000 to the price
        }
    }
]);


**Result:**
[
  { model: 'Creta', price: 1550000 },
  { model: 'Baleno', price: 850000 },
  { model: 'XUV500', price: 1850000 },
  { model: 'City', price: 1250000 },
  { model: 'Nexon', price: 1150000 },
  { model: 'Venue', price: 1250000 },
  { model: 'i20', price: 950000 },
  { model: 'Swift', price: 800000 },
  { model: 'Harrier', price: 2050000 },
  { model: 'Amaze', price: 1050000 },
  { model: 'Nexon EV', price: 1450000 },
  { model: 'Kona Electric', price: 2350000 },
  { model: 'WagonR', price: 650000 },
  { model: 'Amaze', price: 850000 }
]


## `$addFields` Stage

The `$addFields` stage in MongoDB's aggregation framework is used to add new fields to documents or update existing fields with new values. This operator allows you to create new fields based on the values of existing fields.

### Syntax

```javascript
db.collection.aggregate([
    { $addFields: { newField: <expression>, ... } }
]);

db.cars.aggregate([
    {
        $addFields: {
            totalPrice: { $add: ["$price", 50000] } // Add 50,000 to the price
        }
    }
]);


## `$divide` Operator

The `$divide` operator in MongoDB is used to divide one number by another. It returns the result of the division, which can be useful in aggregation operations for calculations involving numeric fields.

### Syntax

```javascript
{ $divide: [ <dividend>, <divisor> ] }


db.cars.aggregate([
    {
        $group: {
            _id: null,
            totalPrice: { $sum: "$price" },  // Calculate the total price
            count: { $sum: 1 }                // Count the number of cars
        }
    },
    {
        $project: {
            averagePrice: { $divide: ["$totalPrice", "$count"] } // Calculate average price
        }
    }
]);


## `$round` Operator

The `$round` operator in MongoDB is used to round a numeric value to the nearest integer or to a specified number of decimal places. This operator is useful when you need to control the precision of numerical values in your documents.

### Syntax

```javascript
{ $round: [ <number>, <decimalPlaces> ] }


db.cars.aggregate([
    {
        $project: {
            model: 1,
            price: 1,
            roundedPrice: { $round: ["$price"] } // Round the price to the nearest integer
        }
    }
]);

## `$set` Operator

The `$set` operator in MongoDB is used to add new fields or update existing fields in documents. This operator can be used in both update operations and aggregation pipelines to modify the content of documents.

### Syntax

```javascript
{ $set: { <field1>: <value1>, <field2>: <value2>, ... } }

db.cars.aggregate([
    {
        $set: {
            discountedPrice: { $multiply: ["$price", 0.9] } // Add discountedPrice to documents
        }
    }
]);
