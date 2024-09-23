### 1. `$eq (Equal to)`

This operator is used to find documents where the value of a field equals the specified value.

#### Example:

Find all cars where the `model` is equal to "Nexon".

```javascript
db.cars.find({ model: { $eq: "Nexon" } })




### 2. $gt (Greater than)
Find all cars where the year is greater than 2020.

```javascript
db.cars.find({ year: { $gt: 2020 } })

### 3. $lt (Less than)
## Query: Find Cars with Price Less Than $30,000

To find all cars where the price is less than $30,000, you can use the following MongoDB query:

```javascript
db.cars.find({ price: { $lt: 30000 } })


### 4. $gte (Greater than or Equal to)
## Query: Find Cars with Horsepower Greater Than or Equal to 300

To find all cars where the horsepower is greater than or equal to 300, you can use the following MongoDB query:

```javascript
db.cars.find({ "specifications.horsepower": { $gte: 300 } })



### 5. $lte (Less than or Equal to)
## Query: Find Cars with Mileage Less Than or Equal to 10,000 Miles

To find all cars where the mileage is less than or equal to 10,000 miles, you can use the following MongoDB query:

```javascript
db.cars.find({ mileage: { $lte: 10000 } })


### 6. $lte (Not Equal to)
## Query: Find Cars Where Fuel Type Is Not "Electric"

To find all cars where the fuel type is not "Electric," you can use the following MongoDB query:

```javascript
db.cars.find({ fuel_type: { $ne: "Electric" } })


### 7. $in () (Matches any of the values specified in an array)
## Query: Find Cars Where Model Is Either "Nexon" or "Model S"

To find all cars where the model is either "Nexon" or "Model S," you can use the following MongoDB query:

```javascript
db.cars.find({ model: { $in: ["Nexon", "Model S"] } })


### 8. $nin (Does not match any of the values specified in an array)
## Query: Find Cars Where Color Is Not "Red" or "Blue"

To find all cars where the color is not "Red" or "Blue," you can use the following MongoDB query:

```javascript
db.cars.find({ color: { $nin: ["Red", "Blue"] } })