<!-- CREATED A DATABASE AS CARS_DEALERSHIP -->
use cars_dealership


<!-- CREATED CAR COLLECTION -->
db.createCollection("cars")


<!-- INSERTION THE DATA AS ONE -->
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


<!-- INSERTED DATA AS MANY -->
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


