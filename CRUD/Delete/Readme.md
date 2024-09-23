## Deleting Documents in MongoDB

### 1. `deleteOne()`
To delete a single document that matches a specified filter, use the `deleteOne()` method.

```javascript
db.collection.deleteOne({ <filter> });


### 2. `deleteMany()`

To delete multiple documents that match a specified filter, use the `deleteMany()` method.

```javascript
db.collection.deleteMany({ <filter> });

