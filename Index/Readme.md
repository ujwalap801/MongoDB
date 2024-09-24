# MongoDB Indexing

An index is a data structure that improves the speed of query operations by allowing the database to quickly locate and access the required data without scanning every document in a collection.

Indexes store the indexed fields in a **sorted order**, along with pointers to the actual documents in the collection. This enables MongoDB to retrieve data much faster for queries involving those fields.

## Creating an Index

To create an index on a field, use the following command:

```javascript
db.collectionName.createIndex({ field: 1 })
```javascript
db.collectionName.getIndexes()
```javascript
db.collectionName.dropIndex("indexName")