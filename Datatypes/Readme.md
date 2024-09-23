# MongoDB and BSON

MongoDB stores data in **BSON** (Binary JSON). BSON is a binary representation of JSON-like documents, providing the following benefits over regular JSON:

### Benefits of BSON

- **Efficient storage**:  
  BSON supports data types like `Date`, `Binary`, and `ObjectId`, which aren't natively available in JSON, making it more efficient for storage and retrieval.

- **Fast traversing**:  
  Since it's a binary format, BSON is optimized for faster parsing and traversing during queries and other database operations.

- **Rich data types**:  
  BSON includes additional data types such as `int`, `long`, `double`, and `boolean`, which allows MongoDB to represent data types that JSON cannot efficiently express.

### Summary

While MongoDB documents resemble JSON, they are stored internally as BSON for better performance and flexibility.




# Example MongoDB Document

```json
{
  "_id": ObjectId("650fdee57d6f3b8f2f435ab3"),        // ObjectId
  "name": "John Doe",                                  // String
  "age": 30,                                           // Integer (int32)
  "salary": 75000.50,                                  // Double
  "isEmployed": true,                                  // Boolean
  "skills": ["JavaScript", "Python", "MongoDB"],       // Array
  "address": {                                         // Embedded Document (Object)
    "street": "123 Main St",
    "city": "New York",
    "zip": 10001
  },
  "joinDate": ISODate("2023-09-20T10:00:00Z"),         // Date
  "profilePicture": BinData(0, "BASE64_ENCODED_DATA"), // Binary Data
  "contact": null,                                     // Null
  "lastLogin": Timestamp(1692878400, 1),               // Timestamp
  "regexPattern": /abc/i,                              // Regular Expression
  "bonus": NumberDecimal("1500.75"),                   // Decimal128
  "customScript": {                                    // JavaScript Code
    "$code": "function() { return this.age >= 18; }",
    "$scope": {}
  },
  "minExample": MinKey(),                              // MinKey
  "maxExample": MaxKey()                               // MaxKey
}




## MongoDB Document Field Types Breakdown

- **ObjectId**:  
  `_id` field stores a unique ObjectId.
  
- **String**:  
  `name` is a text field.
  
- **Integer**:  
  `age` is a 32-bit integer.
  
- **Double**:  
  `salary` is a floating-point number.
  
- **Boolean**:  
  `isEmployed` is a true/false value.
  
- **Array**:  
  `skills` stores an array of strings.
  
- **Embedded Document**:  
  `address` stores a nested document with keys `street`, `city`, and `zip`.
  
- **Date**:  
  `joinDate` uses an ISODate to store date and time.
  
- **Binary Data**:  
  `profilePicture` contains binary data (e.g., an image, encoded in Base64).
  
- **Null**:  
  `contact` is set to `null` to indicate the absence of a value.
  
- **Timestamp**:  
  `lastLogin` stores a timestamp for when the user last logged in.
  
- **Regular Expression**:  
  `regexPattern` stores a regular expression for pattern matching.
  
- **Decimal128**:  
  `bonus` uses Decimal128 for precise financial calculations.
  
- **JavaScript Code**:  
  `customScript` stores a JavaScript function that checks if the user is 18 or older.
  
- **MinKey/MaxKey**:  
  `minExample` and `maxExample` are special BSON types that compare lower/higher than all other values.
