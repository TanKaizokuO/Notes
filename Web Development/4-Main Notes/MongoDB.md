
**Status:**  #Complete 
**Tags:**  [[Backend]]  [[Database]] [[CRUD]]

---


# Understanding BSON (Binary JSON)

## What is BSON?
**BSON** stands for **Binary JSON**. It is a binary-encoded serialization format used to store documents and make remote procedure calls in MongoDB. BSON extends the JSON model to provide additional data types and efficient encoding.

---

## Key Features of BSON
- **Rich Data Types:** Supports types not available in JSON, like `Date`, `Binary Data`, `Embedded Documents`, and `ObjectId`.
- **Efficient Encoding:** Optimized for fast encoding/decoding in memory and over the network.
- **Ordered Fields:** Fields maintain the order they are added to the document.
- **Size Information:** Each BSON document includes its size in bytes, making it easy to traverse.

---

## BSON Example

### Equivalent JSON Document:
```json
{
  "name": "Alice",
  "age": 25,
  "isStudent": true,
  "enrolledDate": "2023-01-19T12:00:00Z",
  "scores": [85, 90, 78]
}
````

### BSON Representation

- **16 bytes:** Total document size
- **02:** `"name"` field (string type)
- **"05":** Field length for `"name"`
- **"Alice":** String value
- ...

---

## BSON in MongoDB

1. **MongoDB uses BSON** as the storage and network data format.
2. Documents stored in MongoDB are BSON but are converted to JSON when accessed via drivers or the shell.

---

## Advantages of BSON

- **Compact and Fast:** Optimized for speed and space.
- **Rich Data Types:** Supports more data types than JSON.
- **Traversal Efficiency:** Allows skipping over entire documents or fields.

---

# MongoDB Shell CRUD Operations

## 1. Create (Insert)

To add documents to a collection, use the `insertOne()` or `insertMany()` methods.

### Commands

- **Insert One Document:**
    
    ```javascript
    db.collection.insertOne(document);
    ```
    
- **Insert Multiple Documents:**
    
    ```javascript
    db.collection.insertMany([document1, document2, ...]);
    ```
    

### Examples

- **Insert a single user:**
    
    ```javascript
    db.users.insertOne({ name: "Alice", age: 25, city: "New York" });
    ```
    
- **Insert multiple users:**
    
    ```javascript
    db.users.insertMany([
        { name: "Bob", age: 30, city: "San Francisco" },
        { name: "Charlie", age: 35, city: "Los Angeles" }
    ]);
    ```
    

---

## 2. Read (Query)

Retrieve documents using the `find()` method. You can filter results and include or exclude specific fields.

### Commands

- **Find All Documents:**
    
    ```javascript
    db.collection.find();
    ```
    
- **Find with Filters:**
    
    ```javascript
    db.collection.find(query);
    ```
    
- **Projection to Show Specific Fields:**
    
    ```javascript
    db.collection.find(query, projection);
    ```
    

### Query Selectors

For more details, refer to the [MongoDB Query Selectors Documentation](https://www.mongodb.com/docs/manual/reference/operator/query/).

---

## Examples

### Fetching Documents

- **Fetch all users:**
    
    ```javascript
    db.users.find();
    ```
    
- **Fetch users in a specific city:**
    
    ```javascript
    db.users.find({ city: "New York" });
    ```
    
- **Fetch users older than 25, showing only names and cities (exclude `_id`):**
    
    ```javascript
    db.users.find({ age: { $gt: 25 } }, { name: 1, city: 1, _id: 0 });
    ```
    

### Helper Commands

- **Fetch one document:**
    
    ```javascript
    db.collection.findOne(query);
    ```
    
- **Count matching documents:**
    
    ```javascript
    db.collection.countDocuments(query);
    ```
    

---

## 3. Update

Modify existing documents using `updateOne()`, `updateMany()`, or `replaceOne()` methods.

### Commands

- **Update One Document:**
    
    ```javascript
    db.collection.updateOne(filter, update, options);
    ```
    
- **Update Multiple Documents:**
    
    ```javascript
    db.collection.updateMany(filter, update, options);
    ```
    
- **Replace One Document:**
    
    ```javascript
    db.collection.replaceOne(filter, replacement, options);
    ```
    

### Examples

- **Update Alice's age:**
    
    ```javascript
    db.users.updateOne(
        { name: "Alice" },
        { $set: { age: 26 } }
    );
    ```
    
- **Update the state for all users in San Francisco:**
    
    ```javascript
    db.users.updateMany(
        { city: "San Francisco" },
        { $set: { state: "California" } }
    );
    ```
    
- **Replace Charlie's document entirely:**
    
    ```javascript
    db.users.replaceOne(
        { name: "Charlie" },
        { name: "Charlie", age: 36, city: "Las Vegas" }
    );
    ```
    

---

## 4. Delete

Remove documents using `deleteOne()` or `deleteMany()` methods.

### Commands

- **Delete One Document:**
    
    ```javascript
    db.collection.deleteOne(filter);
    ```
    
- **Delete Multiple Documents:**
    
    ```javascript
    db.collection.deleteMany(filter);
    ```
    

### Examples

- **Delete Alice's document:**
    
    ```javascript
    db.users.deleteOne({ name: "Alice" });
    ```
    
- **Delete all users in San Francisco:**
    
    ```javascript
    db.users.deleteMany({ city: "San Francisco" });
    ```
    

---

## Additional Notes

1. **Always verify documents** with `find()` before performing update or delete operations.
2. **Drop an entire collection:**
    
    ```javascript
    db.collection.drop();
    ```
    

---

## Tips for Better Usage

1. **Use indexes** for faster querying.
2. **Be cautious** with `updateMany()` and `deleteMany()` to avoid unintended modifications.
3. **Use projection** to minimize data transfer and improve readability of query results.

```

--- 

This structure ensures that the Markdown file is clean, consistent, and easy to read in any Markdown viewer or Obsidian.
```


## References
