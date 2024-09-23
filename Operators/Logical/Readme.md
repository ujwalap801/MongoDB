This document provides an example of how to query a MongoDB database using the `Logical` operator.

## Query: Find Cars Where Year Is Greater Than 2020 and Model Is "Nexon"

To find all cars where the year is greater than 2020 and the model is "Nexon," you can use the following MongoDB query:

```javascript
db.cars.find({ $and: [{ year: { $gt: 2020 } }, { model: "Nexon" }] })


## Query: Find Cars Where Year Is Greater Than 2020 or Model Is "Nexon"

To find all cars where the year is greater than 2020 or the model is "Nexon," you can use the following MongoDB query:

```javascript
db.cars.find({ $or: [{ year: { $gt: 2020 } }, { model: "Nexon" }] })




## Query: Find Cars Where Year Is Not Greater Than or Equal to 2020

To find all cars where the year is not greater than or equal to 2020, you can use the following MongoDB query:

```javascript
db.cars.find({ year: { $not: { $gte: 2020 } } })



## Query: Find Cars Where Year Is Not Greater Than 2020 and Model Is Not "Nexon"

To find all cars where the year is not greater than 2020 and the model is not "Nexon," you can use the following MongoDB query:

```javascript
db.cars.find({ $nor: [{ year: { $gt: 2020 } }, { model: "Nexon" }] })



## Query: Find Cars Where Color Field Exists

To find all cars where the `color` field exists, you can use the following MongoDB query:

```javascript
db.cars.find({ color: { $exists: true } })




# Query: Find Cars Where the Year Field Is of Type "int"

To find all cars where the `year` field is of the type `int`, you can use the following MongoDB query:

```javascript
db.cars.find({ year: { $type: "int" } })





## Query: Find Cars Where Features Array Contains Exactly 3 Elements

To find all cars where the `features` array contains exactly 3 elements, you can use the following MongoDB query:

```javascript
db.cars.find({ features: { $size: 3 } })



## Query: Find Cars Where Features Array Contains All Specified Elements

To find all cars where the `features` array contains both "Bluetooth" and "Sunroof," you can use the following MongoDB query:

```javascript
db.cars.find({ features: { $all: ["Bluetooth", "Sunroof"] } })