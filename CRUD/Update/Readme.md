## Updating a Document

To update a single document in the `cars` collection, use the `updateOne()` method. The following command updates the color of the car with the model "Nexon":

```javascript
db.cars.updateOne(
    { model: "Nexon" },
    { $set: { color: "Red" } }
);


## Result of the Update

After executing the update command, the document in the `cars` collection now appears as follows:

```json
[
  {
    "_id": ObjectId("66f0ef074f663e882f9e4c38"),
    "maker": "Tata",
    "model": "Nexon",
    "fuel_type": "Petrol",
    "transmission": "Automatic",
    "engine": { "type": "Turbocharged", "cc": 1199, "torque": "170 Nm" },
    "features": [ "Touchscreen", "Reverse Camera", "Bluetooth Connectivity" ],
    "sunroof": false,
    "airbags": 2,
    "color": "Red"
  }
]



## Pushing New Data into a Nested Key

To add a new item to an array within a document in the `cars` collection, use the `$push` operator. The following command adds "Heated Seats" to the features of the car with the model "Nexon":

```javascript
db.cars.updateOne(
    { model: "Nexon" },   // Filter to find the specific document
    { $push: { features: "Heated Seats" } }
);


## Result of the Push Operation

After executing the push command, the document in the `cars` collection now appears as follows:

```json
[
  {
    "_id": ObjectId("66f0ef074f663e882f9e4c38"),
    "maker": "Tata",
    "model": "Nexon",
    "fuel_type": "Petrol",
    "transmission": "Automatic",
    "engine": { "type": "Turbocharged", "cc": 1199, "torque": "170 Nm" },
    "features": [
      "Touchscreen",
      "Reverse Camera",
      "Bluetooth Connectivity",
      "Heated Seats"
    ],
    "sunroof": false,
    "airbags": 2,
    "color": "Red"
  }
]


## Pulling Data to Remove It

To remove an item from an array within a document in the `cars` collection, use the `$pull` operator. The following command removes "Heated Seats" from the features of the car with the model "Nexon":

```javascript
db.cars.updateOne(
    { model: "Nexon" },
    { $pull: { features: "Heated Seats" } }
);


## Updating Nested Data

To update a specific field within a nested document in the `cars` collection, use the `$set` operator. The following command updates the torque value in the engine of the car with the model "Nexon":

```javascript
db.cars.updateOne(
    { model: "Nexon" },
    { $set: { "engine.torque": "270 Nm" } }
);

## Result of the Update Operation

After executing the update command, the document in the `cars` collection now appears as follows:

```json
{
  "_id": ObjectId("66f0ef074f663e882f9e4c38"),
  "maker": "Tata",
  "model": "Nexon",
  "fuel_type": "Petrol",
  "transmission": "Automatic",
  "engine": { "type": "Turbocharged", "cc": 1199, "torque": "270 Nm" },
  "features": [ "Touchscreen", "Reverse Camera", "Bluetooth Connectivity" ],
  "sunroof": false,
  "airbags": 2,
  "color": "Red"
}


## Updating Multiple Values in an Array

To add multiple values to an array within documents in the `cars` collection, use the `$push` operator with the `$each` modifier. The following command adds "Wireless charging" and "Voice control" to the features of all cars with the model "Nexon":

```javascript
db.cars.updateMany(
    { model: "Nexon" },
    { $push: { features: { $each: ["Wireless charging", "Voice control"] } } }
);

## Result of the Update Operation

After executing the update command to add multiple features, the document in the `cars` collection now appears as follows:

```json
{
  "_id": ObjectId("66f0ef074f663e882f9e4c38"),
  "maker": "Tata",
  "model": "Nexon",
  "fuel_type": "Petrol",
  "transmission": "Automatic",
  "engine": { "type": "Turbocharged", "cc": 1199, "torque": "270 Nm" },
  "features": [
    "Touchscreen",
    "Reverse Camera",
    "Bluetooth Connectivity",
    "Wireless charging",
    "Voice control"
  ],
  "sunroof": false,
  "airbags": 2,
  "color": "Red"
}

## Removing the Color from the Nexon Model

To remove the color field from the Nexon model, the following command was executed:

```javascript
db.cars.updateOne(
  { model: "Nexon" },
  { $unset: { color: "Red" } }
)


## Result

The document in the `cars` collection after the update operation appears as follows:

```json
{
  "_id": ObjectId("66f0ef074f663e882f9e4c38"),
  "maker": "Tata",
  "model": "Nexon",
  "fuel_type": "Petrol",
  "transmission": "Automatic",
  "engine": { "type": "Turbocharged", "cc": 1199, "torque": "270 Nm" },
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
## Update All Documents

To update the color of all documents in the `cars` collection to "Red", use the following command:

```javascript
db.cars.updateMany({}, {$set: {color: "Red"}});


## Upsert in MongoDB

In MongoDB, **upsert** is a feature that allows you to either update an existing document or insert a new one if no matching document is found. This is particularly useful when you want to ensure that a record is created or updated in a single operation.

### Example

To update the maker of the model "Venue" or insert it if it doesn't exist, use the following command:

```javascript
db.cars.updateOne(
    { model: "Venue" },
    { $set: { Maker: "Hyundai" } },
    { upsert: true }
);
