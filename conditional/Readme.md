## `$cond` Operator

The `$cond` operator in MongoDB is a conditional operator that evaluates a specified condition and returns one of two values based on whether the condition is true or false. This operator is useful for implementing conditional logic within aggregation pipelines.

### Syntax

```javascript
{ $cond: [ <condition>, <trueResult>, <falseResult> ] }

## Categorizing Car Prices

In this section, we will use the `$cond` operator to categorize cars based on their prices. The goal is to classify each car as either "Expensive" or "Affordable" depending on whether the price exceeds 50,000.

### Example Aggregation

The following aggregation pipeline projects the `model`, `price`, and a new field `priceCategory` based on the price of each car:

```javascript
db.cars.aggregate([
    {
        $project: {
            model: 1, // Include the model field
            price: 1, // Include the price field
            priceCategory: {
                $cond: {
                    if: { $gt: ["$price", 50000] }, // Condition: price greater than 50,000
                    then: "Expensive",              // Result if true
                    else: "Affordable"              // Result if false
                }
            }
        }
    }
]);


## `$switch` Operator

The `$switch` operator in MongoDB is used to evaluate multiple conditions and return different values based on which condition is true. It is similar to a switch-case statement in programming languages, making it useful for implementing complex conditional logic within aggregation pipelines.

### Syntax

```javascript
{
    $switch: {
        branches: [
            { case: <condition1>, then: <result1> },
            { case: <condition2>, then: <result2> },
            ...
        ],
        default: <defaultResult> // Optional default result if no conditions are met
    }
}



## Categorizing Car Prices with `$switch`

In this section, we will use the `$switch` operator to categorize cars based on their prices into different categories: "Luxury," "Expensive," "Moderate," and "Affordable." 

### Example Aggregation

The following aggregation pipeline projects the `model`, `price`, and a new field `priceCategory` based on the price of each car:

```javascript
db.cars.aggregate([
    {
        $project: {
            model: 1, // Include the model field
            price: 1, // Include the price field
            priceCategory: {
                $switch: {
                    branches: [
                        { case: { $gt: ["$price", 70000] }, then: "Luxury" },         // Price greater than 70,000
                        { case: { $gt: ["$price", 50000] }, then: "Expensive" },      // Price between 50,001 and 70,000
                        { case: { $gt: ["$price", 30000] }, then: "Moderate" },       // Price between 30,001 and 50,000
                    ],
                    default: "Affordable" // Price 30,000 or below
                }
            }
        }
    }
]);
