# MongoDB Validation Rules

MongoDB uses a JSON Schema format to define validation rules for collections. This allows you to specify various constraints and rules for your documents, such as:

- Required fields
- Field types
- Value ranges

## Adding Validation on Collection Creation

You can add validation rules while creating a collection to ensure that all documents adhere to the specified schema. This helps maintain data integrity and consistency within your database.

### Example of Adding Validation During Collection Creation

To add validation rules when creating a collection, you can use the following command:

```javascript
db.createCollection("yourCollectionName", {
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["field1", "field2"],
      properties: {
        field1: {
          bsonType: "string",
          description: "must be a string and is required"
        },
        field2: {
          bsonType: "int",
          minimum: 0,
          description: "must be an integer greater than or equal to 0 and is required"
        }
      }
    }
  }
});


# MongoDB Collection Validation

This section describes how to update the `cars` collection in MongoDB to enforce validation rules using a JSON schema.

## Update Collection Validation

To modify the `cars` collection and add validation rules, you can run the following command in the MongoDB shell:

db.runCommand({
  collMod: "cars",
  validator: {
    $jsonSchema: {
      bsonType: "object",
      required: ["make", "model", "year"],
      properties: {
        make: {
          bsonType: "string",
          description: "must be a string and is required"
        },
        model: {
          bsonType: "string",
          description: "must be a string and is required"
        },
        year: {
          bsonType: "int",
          minimum: 1886,
          maximum: 2024,
          description: "must be an integer in [1886, 2024] and is required"
        },
        color: {
          bsonType: "string",
          description: "must be a string if the field exists"
        }
      }
    }
  },
  validationAction: "error" // or "warn" depending on your preference
});
