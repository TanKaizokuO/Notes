
**Status:** #Incomplete  
**Tags:**  [[Backend]] [[Database]] [[MongoDB]] [[CRUD]] [[Mongoose]]

## Finding Documents

#### **1. `find()`**  


- **Syntax**:
    
    ```javascript
    Model.find(query, projection, options)
    ```
    
    - `query`: Specifies the filter criteria (e.g., `{ name: 'John' }`).
    - `projection`: (Optional) Specifies which fields to return (e.g., `{ name: 1, age: 1 }`).
    - `options`: (Optional) Additional options like sorting or limiting results.
- **Example**:
    
    ```javascript
    const users = await User.find({ age: { $gte: 18 } });
    console.log(users);
	//OR
	User. find({age: {$gt: 47}})
		.then((res) => {
		console.log(res)
		});
    ```
    

#### **2. `findOne()`**

- **Description**: Retrieves the first document that matches the query.
- **Syntax**:
    
    ```javascript
    Model.findOne(query, projection, options)
    ```
    
- **Example**:
    
    ```javascript
    const user = await User.findOne({ email: 'johndoe@example.com' });
    console.log(user);
    ```
    

#### **3. `findById()`**

- **Description**: Finds a document by its unique `_id` field.
- **Syntax**:
    
    ```javascript
    Model.findById(id, projection, options)
    ```
    
- **Example**:
    
    ```javascript
    const user = await User.findById('64abc123456def7890123456');
    console.log(user);
    ```
    

---

## **Updating Documents**

#### **1. `updateOne()`**

- **Description**: Updates the first document that matches the query.
- **Syntax**:
    
    ```javascript
    Model.updateOne(filter, update, options)
    ```
    
- **Example**:
    
    ```javascript
    
    await User.updateOne({ email: 'johndoe@example.com' }, { $set: { age: 30 } });
    
    ```
    

#### **2. `updateMany()`**

- **Description**: Updates all documents that match the query.
- **Syntax**:
    
    ```javascript
    Model.updateMany(filter, update, options)
    ```
    
- **Example**:
    
    ```javascript
    
    await User.updateMany({ age: { $lt: 18 } }, { $set: { status: 'minor' } });
    
    ```
    

#### **3. `findByIdAndUpdate()`**

- **Description**: Finds a document by its `_id` and updates it.
- **Syntax**:
    
    ```javascript
    Model.findByIdAndUpdate(id, update, options)
    ```
    
- **Example**:
    
    ```javascript
    const user = await User.findByIdAndUpdate(
      '64abc123456def7890123456',
      { $set: { age: 35 } },
      { new: true } // Returns the updated document
    );
    console.log(user);
    ```
    

#### **4. `findOneAndUpdate()`**

- **Description**: Finds a document that matches the query and updates it.
- **Syntax**:
    
    ```javascript
    Model.findOneAndUpdate(filter, update, options)
    ```
    
- **Example**:
    
    ```javascript
    const user = await User.findOneAndUpdate(
      { email: 'johndoe@example.com' },
      { $set: { active: true } },
      { new: true }
    );
    console.log(user);
    ```
    

---

### **Key Update Operators**

- **`$set`**: Updates specified fields with the provided values.
    
    ```javascript
    { $set: { name: 'John Doe' } }
    ```
    
- **`$unset`**: Removes a field from the document.
    
    ```javascript
    { $unset: { name: '' } }
    ```
    
- **`$inc`**: Increments a numeric field by a specified value.
    
    ```javascript
    { $inc: { age: 1 } }
    ```
    
- **`$push`**: Adds an element to an array.
    
    ```javascript
    { $push: { hobbies: 'reading' } }
    ```
    

---
### **Options for Updates**

- **`new`**:
    
    - Determines whether to return the updated document or the original document before the update.
    - **Default**: `false` (returns the original document).
    - **Example**:
        
        ```javascript
        const updatedDoc = await Model.findOneAndUpdate(
          { name: 'Alice' },
          { age: 30 },
          { new: true } // Returns the updated document
        );
        ```
        
- **`upsert`**:
    
    - Creates a new document if no document matches the query.
    - **Default**: `false` (does not create a new document).
    - **Example**:
        
        ```javascript
        const doc = await Model.updateOne(
          { name: 'Bob' },
          { $set: { age: 25 } },
          { upsert: true } // Creates a new document if 'Bob' is not found
        );
        ```

---

## Deleting Documents

#### 1. **Deleting Single Documents**

- Use `Model.deleteOne()` to delete a single document matching the filter criteria:
    
    ```javascript
    Model.deleteOne({ _id: id }, (err) => {
      if (err) console.error(err);
      else console.log("Document deleted");
    });
    //OR
    User.deleteOne({ name: "Bruce" }, (err, res) => {
		if (err) {
		    console.error(err);
	  } else {
		    console.log(res);
	  }
	});
```
#### 2. **Deleting Multiple Documents**

- Use `Model.deleteMany()` to delete all documents matching the filter criteria:
    
    ```javascript
    Model.deleteMany({ field: value }, (err) => {
      if (err) console.error(err);
      else console.log("Documents deleted");
    });
    ```
    

#### 3. **Find and Remove**

- Use `findOneAndDelete()` or `findByIdAndDelete()` for finding and deleting a document:
    
    ```javascript
    Model.findByIdAndDelete(id, (err, doc) => {
      if (err) console.error(err);
      else console.log("Deleted Document:", doc);
    });
    ```
    


