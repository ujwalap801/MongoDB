


// To display all the collections in the currently selected database, use:
show collections


## MongoDB Command Line Interface

1. **Start the MongoDB Shell**  
   Enter the following command in Command Prompt to start:

   ```bash
   mongosh

## Creating and Using a Database in MongoDB

To create and use a database, use the following command. Note that the database will not be created until at least one collection is added to it.

```javascript
use myDatabase


## MongoDB Collection and Database Operations

### Create a Collection
To create a collection in MongoDB, use the following command:
```javascript
db.createCollection("myCollection")

### Drop a Collection

To drop (delete) a collection from the database, use the following command:

```javascript
db.myCollection.drop()


### Drop the Database

To drop (delete) the current database, use the following command:

```javascript
db.dropDatabase()

give this text in readme.md format

### Display All Collections in the Current Database

To list all the collections in the currently selected MongoDB database, use the following command:

```javascript
show collections
