## Example of Using `$concat` in Aggregation

To concatenate the `maker` and `model` fields for cars made by Hyundai, use the following aggregation pipeline:


db.cars.aggregate([
    { $match: { maker: "Hyundai" } },
    { $project: { _id: 0, CarName: { $concat: ["$maker", " ", "$model"] } } }
])


**Result:**
[
  { CarName: 'HyundaiCreta' },
  { CarName: 'HyundaiVenue' },
  { CarName: 'Hyundaii20' },
  { CarName: 'HyundaiKona Electric' }
]



## Example of Using `$regex` in Aggregation

To find all cars where the model contains the substring "Eco", use the following aggregation pipeline:

performs a regular expression(regex) pattern matching and returns true or false
```javascript
db.cars.aggregate([
    { $match: { model: { $regex: /Eco/i } } }
])


## Regex Match Example

To check if the `fuel_type` field contains the substring "Dies", you can use the following aggregation pipeline:

```javascript
db.cars.aggregate([
  {
    $project: {
      _id: 0,
      model: 1,
      is_diesel: {
        $regexMatch: {
          input: "$fuel_type",
          regex: "Dies"
        }
      }
    }
  }
])


**Result:**
Match:{input:"$fuel_type",regex:"Dies"}}}}])
[
  { model: 'Creta', is_diesel: true },
  { model: 'Baleno', is_diesel: false },
  { model: 'XUV500', is_diesel: true },
  { model: 'City', is_diesel: false },
  { model: 'Nexon', is_diesel: false },
  { model: 'Venue', is_diesel: false },
  { model: 'i20', is_diesel: false },
  { model: 'Swift', is_diesel: false },
  { model: 'Harrier', is_diesel: true },
  { model: 'Amaze', is_diesel: true },
  { model: 'Nexon EV', is_diesel: false },
  { model: 'Kona Electric', is_diesel: false },
  { model: 'WagonR', is_diesel: false },
  { model: 'Amaze', is_diesel: false }
]


## `$out` Operator

The `$out` operator is used in MongoDB to write the results of an aggregation pipeline to a new collection. This operator is useful when you want to store the results of an aggregation operation for later use or further analysis.

### Syntax

```javascript
db.collection.aggregate([
    { /* your aggregation stages */ },
    { $out: "newCollectionName" }
]);



db.cars.aggregate([{$match:{maker:"Hyundai"}},{$project:{
... _id:0,
... Car_Name:{$toUpper:{$concat:["$maker"," ","$model"]}}}},{$out:"hyundai_C
ars"}])
