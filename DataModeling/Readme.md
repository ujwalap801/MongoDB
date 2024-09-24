# MongoDB Relationships

MongoDB is a NoSQL database that does not enforce strict schema relationships like foreign keys in relational databases. However, we can still model relationships between documents in MongoDB using a few approaches.

## Types of Relationships

### 1. Embedded Documents (Denormalization)

- **Example**:  
  ```plaintext
  UserA
    ├── orderA
    └── orderB


## Referenced Documents (Normalization)

### Types of Relationships

1. **One to One**  
   **Example**: `user -> Contact`

2. **One to Many**  
   **Example**: `User -> Posts`

3. **Many to Many**  
   **Example**: `Courses -> Students`




## MongoDB Aggregation Query

The following aggregation query uses the `$lookup` stage to perform a join between the `users` and `orders` collections:

```javascript
db.users.aggregate([
    {
        "$lookup": {
            "from": "orders",
            "localField": "_id",
            "foreignField": "user_id",
            "as": "orders"
        }
    }
])


## MongoDB Aggregation Output

The following is the output of the MongoDB aggregation query that performs a lookup between the `users` and `orders` collections:

```json
[
  {
    "_id": "user1",
    "name": "Amit Sharma",
    "email": "amit.sharma@example.com",
    "phone": "+91-987654210",
    "address": "MG Road, Mumbai, Maharashtra",
    "orders": [
      {
        "_id": "order1",
        "user_id": "user1",
        "product": "Laptop",
        "amount": 50000,
        "order_date": "2024-08-01"
      },
      {
        "_id": "order3",
        "user_id": "user1",
        "product": "Headphones",
        "amount": 2000,
        "order_date": "2024-08-10"
      }
    ]
  },
  {
    "_id": "user2",
    "name": "Priya Verma",
    "email": "priya.verma@example.com",
    "phone": "+91-987654211",
    "address": "Nehru Place, New Delhi, Delhi",
    "orders": [
      {
        "_id": "order2",
        "user_id": "user2",
        "product": "Mobile Phone",
        "amount": 15000,
        "order_date": "2024-08-05"
      }
    ]
  },
  {
    "_id": "user3",
    "name": "Rahul Singh",
    "email": "rahul.singh@example.com",
    "phone": "+91-987654212",
    "address": "Sector 18, Noida, Uttar Pradesh",
    "orders": [
      {
        "_id": "order4",
        "user_id": "user3",
        "product": "Tablet",
        "amount": 25000,
        "order_date": "2024-08-12"
      }
    ]
  },
  {
    "_id": "user4",
    "name": "Anjali Nair",
    "email": "anjali.nair@example.com",
    "phone": "+91-987654213",
    "address": "Marine Drive, Kochi, Kerala",
    "orders": [
      {
        "_id": "order5",
        "user_id": "user4",
        "product": "Smart Watch",
        "amount": 8000,
        "order_date": "2024-08-15"
      }
    ]
  },
  {
    "_id": "user5",
    "name": "Vikram Desai",
    "email": "vikram.desai@example.com",
    "phone": "+91-987654214",
    "address": "Park Street, Kolkata, West Bengal",
    "orders": []
  }
]
