# Creating a Database and Collection in MongoDB

## Step 1: Create a Database

To create a database named `cars_dealership`, use the following command:

```javascript
use cars_dealership


## Creating a Collection

To create a collection named `cars`, use the following command:

```javascript
db.createCollection("cars")


## Inserting Data into the Collection

To insert a single document into the `cars` collection, use the following command:

```javascript
db.cars.insertOne({
    make: "Tesla",
    model: "Model S",
    year: 2022,
    specifications: {
        battery: "100 kWh",
        range: "396 miles",
        horsepower: 1020,
        features: ["Autopilot", "All-Wheel Drive", "Fast Charging"]
    },
    owner: {
        name: "John Doe",
        purchaseDate: "2023-01-15",
        contact: {
            email: "johndoe@example.com",
            phone: "123-456-7890"
        }
    }
})



## Inserting Multiple Documents into the Collection

To insert multiple documents into the `cars` collection, use the following command:

```javascript
db.cars.insertMany([
    {
        make: "Tesla",
        model: "Model S",
        year: 2022,
        specifications: {
            battery: "100 kWh",
            range: "396 miles",
            horsepower: 1020,
            features: ["Autopilot", "All-Wheel Drive", "Fast Charging"]
        },
        owner: {
            name: "John Doe",
            purchaseDate: "2023-01-15",
            contact: {
                email: "johndoe@example.com",
                phone: "123-456-7890"
            }
        }
    }
])



