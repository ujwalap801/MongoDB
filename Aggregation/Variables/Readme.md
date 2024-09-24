## System-Defined and User-Defined Variables in MongoDB Aggregation

In MongoDB aggregation pipelines, variables can be categorized into two types: **system-defined variables** and **user-defined variables**. Understanding these variables helps in crafting more efficient and readable aggregation queries.

### 1. System-Defined Variables

System-defined variables are built-in variables that MongoDB provides for use within aggregation pipelines. These variables can be used directly in aggregation expressions. Some common system-defined variables include:

 db.cars.aggregate({$project:{_id:0,model:1,date:"$$NOW"}})




 ## User-Defined Variables

User-defined variables in MongoDB aggregation allow you to store values and reuse them within the same pipeline. This capability enhances the readability and efficiency of your aggregation queries in certain scenarios.

### Benefits of User-Defined Variables

- **Reusability**: You can define a value once and reference it multiple times within the same pipeline, reducing redundancy.
- **Improved Readability**: Using descriptive variable names makes the aggregation pipeline easier to understand for other developers and for future maintenance.
- **Complex Calculations**: User-defined variables enable you to break down complex calculations into manageable parts, facilitating better organization of your logic.

### Example

Here’s a simple example demonstrating the use of user-defined variables:

```javascript
db.cars.aggregate([
    {
        $project: {
            model: 1,
            price: 1,
            discountedPrice: {
                $let: {
                    vars: {
                        discount: 0.1, // Define a variable for the discount
                        priceAfterDiscount: { $multiply: ["$price", 0.9] } // Calculate the price after discount
                    },
                    in: "$$priceAfterDiscount" // Use the variable in the result
                }
            }
        }
    }
]);


# Electric Vehicle Models

This document provides information on various electric vehicle models, including their original prices and discounted prices.

## Models Overview

| Model     | Original Price | Discounted Price |
|-----------|----------------|------------------|
| Model S   | $80,000        | $72,000          |
| Model 3   | $35,000        | $31,500          |
| Model X   | $90,000        | $81,000          |
| Model Y   | $60,000        | $54,000          |

## Summary
The table above lists the models, their original prices, and the discounted prices for each electric vehicle. 
