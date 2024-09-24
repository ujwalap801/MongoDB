
 ### Aggregation Example

To group cars by their maker, you can use the following aggregation query:

```javascript
db.cars.aggregate([{$group: {_id: "$maker"}}])
**Result:**

[
  { _id: 'Hyundai' },
  { _id: 'Mahindra' },
  { _id: 'Maruti Suzuki' },
  { _id: 'Honda' },
  { _id: 'Tata' }
]



**Aggregation Example: Count Total Cars by Maker**

```javascript
db.cars.aggregate([
  { $group: { _id: "$maker", TotalCars: { $sum: 1 } } }
])

**Result:**
[
  { _id: 'Hyundai', TotalCars: 4 },
  { _id: 'Honda', TotalCars: 3 },
  { _id: 'Maruti Suzuki', TotalCars: 3 },
  { _id: 'Mahindra', TotalCars: 1 },
  { _id: 'Tata', TotalCars: 3 }
]


## `$match` Example

The `$match` stage in MongoDB's aggregation framework is used to filter documents that match specific criteria. It's similar to a query, where only the documents that fulfill the given condition are passed to the next stage of the aggregation pipeline.

### Example: Find all cars where the `maker` is "Tata".

```javascript
db.cars.aggregate([
  { $match: { maker: "Tata" } }
])


**Result:**
[
  {
    "_id": ObjectId("66f0ef074f663e882f9e4c38"),
    "maker": "Tata",
    "model": "Nexon",
    "fuel_type": "Petrol",
    "transmission": "Automatic",
    "engine": {
      "type": "Turbocharged",
      "cc": 1199,
      "torque": "270 Nm"
    },
    "features": [
      "Touchscreen",
      "Reverse Camera",
      "Bluetooth Connectivity",
      "Wireless charging",
      "Voice container"
    ],
    "sunroof": false,
    "airbags": 2
  }
]


## `$match` and `$count` Example

The `$match` stage is used to filter documents based on a condition, and the `$count` stage is used to count the number of documents that pass through the previous stages of the aggregation pipeline.

### Example: Find the total number of cars where the `maker` is "Hyundai".

```javascript
db.cars.aggregate([
  { $match: { maker: "Hyundai" } },
  { $count: "Total_Cars" }
])

**Result:**
[
  { "Total_Cars": 4 }
]


## `$match` and `$group` Example

The `$match` stage is used to filter documents based on a condition, and the `$group` stage is used to group documents by a specified field.

### Example: Find distinct fuel types for cars where the `maker` is "Hyundai".

```javascript
db.cars.aggregate([
  { $match: { maker: "Hyundai" } },
  { $group: { _id: "$fuel_type" } }
])

**Result:**
[
  { "_id": "Petrol" },
  { "_id": "Diesel" }
]




## `$match` and `$project` Example

The `$match` stage is used to filter documents, and the `$project` stage is used to reshape documents, allowing you to include or exclude specific fields.

### Example: Retrieve the `maker`, `model`, and `fuel_type` of cars where the `maker` is "Hyundai".

```javascript
db.cars.aggregate([
  { $match: { maker: "Hyundai" } },
  { $project: {
      _id: 0,
      maker: 1,
      model: 1,
      fuel_type: 1
    }
  }
])

**Result:**
[
  { "maker": "Hyundai", "model": "i20", "fuel_type": "Petrol" },
  { "maker": "Hyundai", "model": "Creta", "fuel_type": "Diesel" }
]


### MongoDB Aggregation Example

The following command retrieves all cars made by Hyundai, projecting only the maker, model, and fuel type fields, and sorts the results by model name in ascending order:

```javascript
db.cars.aggregate([
    { $match: { maker: "Hyundai" } },
    { $project: { _id: 0, maker: 1, model: 1, fuel_type: 1 } },
    { $sort: { model: 1 } }
])


## Aggregation Example: Sort by Count

To sort documents by the count of occurrences of the `maker` field, use the following aggregation command:

```javascript
db.cars.aggregate({ $sortByCount: "$maker" })

**Result:**
[
  { _id: 'Hyundai', count: 4 },
  { _id: 'Maruti Suzuki', count: 3 },
  { _id: 'Honda', count: 3 },
  { _id: 'Tata', count: 3 },
  { _id: 'Mahindra', count: 1 }
]


## Example of `$unwind`

In MongoDB, the `$unwind` operator is used to deconstruct an array field from the input documents to output a document for each element. This is particularly useful when you want to transform a document with an array into multiple documents, each containing a single element from the array.

### Sample Document

Assuming we have the following document in the `cars` collection:

```json
{
  "_id": ObjectId("60c72b2f9b1e8e3d88a0e1a1"),
  "maker": "Hyundai",
  "models": ["Elantra", "Creta", "Kona"]
}

**Result:**
[
  {
    "_id": ObjectId("60c72b2f9b1e8e3d88a0e1a1"),
    "maker": "Hyundai",
    "models": "Elantra"
  },
  {
    "_id": ObjectId("60c72b2f9b1e8e3d88a0e1a1"),
    "maker": "Hyundai",
    "models": "Creta"
  },
  {
    "_id": ObjectId("60c72b2f9b1e8e3d88a0e1a1"),
    "maker": "Hyundai",
    "models": "Kona"
  }
]
