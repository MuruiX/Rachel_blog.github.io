---
LINK:
  - Database
  - "[[NoSQL]]"
  - "[[MongoDB]]"
---
# Node.js Connect MongoDB


Example:

```
const { MongoClient } = require('mongodb');

async function main() {
    // MongoDB connect URL
    const uri = "mongodb://localhost:27017"; 

    // create new MongoClient
    const client = new MongoClient(uri, { useNewUrlParser: true, useUnifiedTopology: true });

    try {
        // connect to MongoDB server
        await client.connect();

        console.log("Connected successfully to server");

  
    } finally {
        // close the connect after finish
        await client.close();
    }
}

main().catch(console.error);
```

will output: `Connected successfully to server`

parameter:

- MongoClient: client used to connect to database
- url: `mongodb://[username:password@]host1[:port1][,...hostN[:portN]][/[defaultauthdb][?options]]`。


## Create Database


```
const { MongoClient } = require('mongodb');
 
async function main() {
    // MongoDB connect URI
    const uri = "mongodb://localhost:27017"; 
 
    // Create new MongoClient
    const client = new MongoClient(uri, { useNewUrlParser: true, useUnifiedTopology: true });
 
    try {
        await client.connect();
 
        console.log("Successful connection to the server");
 
        // Specify database
        const database = client.db('runoob');
 
        // operation
        const collection = database.collection('exampleCollection');
        const doc = { name: "Example", type: "Test" };
        const result = await collection.insertOne(doc);
 
        console.log(`new document has created，ID is: ${result.insertedId}`);
    } finally {
        // close connection
        await client.close();
    }
}
 
main().catch(console.error);
```
