Enter command mongosh in command Prompt to start
to exit from it press crt+D

// Create and use a database and database will not created until we can atleast ine collection in it
use myDatabase

// Create a collection
db.createCollection("myCollection")

// Drop the collection
db.myCollection.drop()

// Drop the database
db.dropDatabase()


// To display all the databases in your MongoDB instance, use:
show dbs


// To display all the collections in the currently selected database, use:
show collections