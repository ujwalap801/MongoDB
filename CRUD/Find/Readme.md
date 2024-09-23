
# MongoDB Querying and Projection

## 1. Basic Query
To retrieve documents from a collection based on a specified query, use the `find()` method.

### Syntax
```javascript
db.collection.find({ field: value })


## 2. Projection in MongoDB

In MongoDB, projection refers to selecting specific fields from a document when performing a query. This allows you to control which fields you want to include or exclude from the result set. By default, MongoDB returns all fields from a document when querying, but you can use projections to limit the output.

### Syntax
```javascript
db.collection.find(query, projection)


### Query and Projection Details

- **query**: The criteria used to filter the documents (e.g., `{ name: "John" }`).
- **projection**: Specifies the fields to include or exclude (e.g., `{ field1: 1, field2: 0 }`).

### Projection Example: Including Fields
- `1` means **include** the field.
- `0` means **exclude** the field.


### Example 1: Include Specific Fields

To include specific fields in your query, you can use the following syntax:

```javascript
db.cars.find({}, { make: 1, model: 1, _id: 0 })

### Explanation

- **{}**: No filter is applied, so it returns all documents.
- **{ make: 1, model: 1, _id: 0 }**: Includes the `make` and `model` fields, excludes the `_id` field.


### Result

```json
[
  { "make": "Tesla", "model": "Model S" },
  { "make": "Toyota", "model": "Camry" },
  { "make": "Ford", "model": "Mustang" }
]


# Accessing Nested Data in MongoDB

To find nested data in MongoDB, you can query specific fields inside a nested document by using dot notation. Dot notation allows you to refer to fields inside a nested document or array.

### Syntax for Accessing Nested Fields
```javascript
db.collection.find({ "parentField.childField": "value" })


### Querying Nested Fields

- **parentField**: The field that contains the nested document.
- **childField**: The field inside the nested document.
- **value**: The value you want to search for.

### Examples
1. ```javascript
   db.cars.find({ "specifications.battery": "100 kWh" })

### Example Query for Nested Fields

To find cars with specific nested specifications, you can use the following query:

```javascript
db.cars.find({
  "specifications.horsepower": { $gt: 500 },
  "specifications.range": "396 miles"
})
