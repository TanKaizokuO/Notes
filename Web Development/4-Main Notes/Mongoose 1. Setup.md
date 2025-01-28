**Status:**  #Incomplete 
**Tags:**  [[Backend]] [[MongoDB]]  [[Mongoose]]
**Reference:** [Mongoose Docs](https://www.npmjs.com/package/mongoose)

---
# **Mongoose**

## **What is Mongoose?**

- **Definition**:  
    Mongoose is a library that establishes a connection between **MongoDB** and the **Node.js JavaScript runtime environment**.
    
- **Type**:  
    Mongoose is an **ODM (Object Data Modeling)** library.
    
## **Purpose**

- Simplifies the process of working with MongoDB in Node.js by providing a structured way to define, validate, and interact with data.

---
# **Installing and Setting Up Mongoose**

## **1. Installation**

To use Mongoose in a Node.js application, it must first be installed.

### **Command to Install**

```bash
npm install mongoose
```

---

## **2. Setting Up Mongoose**

#### **2.1 Import Mongoose**

Use the `require` function to include Mongoose in your project:

```javascript
const mongoose = require('mongoose');
import mongoose from 'mongoose'
```

#### **2.2 Connect to MongoDB**

Your provided code has a few syntax errors. Below is the corrected version of the code, along with **Obsidian-style notes** for setting up Mongoose with an asynchronous approach:

---

## **Setting Up Mongoose with Async/Await**

#### **Correct Code Example**

```javascript
const mongoose = require('mongoose');

main()
  .then(() => {
    console.log("Connection successful");
  })
  .catch((err) => {
    console.error(err);
  });

async function main() {
  await mongoose.connect("mongodb://127.0.0.1:27017/test", {
    useNewUrlParser: true,     // Avoid deprecation warnings
    useUnifiedTopology: true, // Uses the new server discovery and monitoring engine
  });
}
```

---

### **Explanation**

##### **1. `require('mongoose')`**

- Imports the Mongoose library into the project.

##### **2. `main()` Function**

- Defines an **asynchronous function** that connects to the MongoDB database.
- Uses `await mongoose.connect()` to wait for the connection to complete.

##### **3. `mongoose.connect()`**

- **Connection String**: `mongodb://127.0.0.1:27017/test`
    - `127.0.0.1`: Refers to the local MongoDB server.
    - `27017`: Default port for MongoDB.
    - `test`: The database name (can be replaced with your desired database name).
- **Options**:
    - `useNewUrlParser`: Ensures the connection string is parsed using the new parser.
    - `useUnifiedTopology`: Enables the unified topology for better performance and monitoring.

##### **4. `.then()` and `.catch()`**

- **`.then()`**: Executes if the connection is successful.
- **`.catch()`**: Handles any errors that occur during the connection.

---

### **Key Points**

- **Async/Await**:
    - Allows for writing asynchronous code in a cleaner and more readable way.
- **Error Handling**:
    - Using `.catch()` ensures any connection errors are logged to the console.

---
### **2.3 Verify Connection**

You can listen for connection events to ensure that Mongoose successfully connects:

```javascript
const db = mongoose.connection;

db.on('error', console.error.bind(console, 'Connection error:'));
db.once('open', () => {
  console.log('Database connected successfully!');
});
```

---

## **3. Example of Setting Up a Schema and Model**

### **3.1 Define a [Schema**](https://mongoosejs.com/docs/guide.html)
Schema defines the shape of the documents within that collection.

```javascript
const schema = new mongoose.Schema({
  name: String,
  age: Number,
  email: { type: String, required: true, unique: true },
});
```

### **3.2 Create a Model**
Model in mongoose is a class with which we construct documents.

```javascript
const User = mongoose.model('User', schema);
```

### **3.3 Use the Model**
An unique id(Primary Key) is created for each document
.save() returns a promise
```javascript
//Insert one document
const newUser = new User({ name: 'John Doe', age: 25, email: 'johndoe@example.com' });
newUser.save()
  .then(res => console.log('User saved successfully!',res))
  .catch(err => console.error('Error saving user:', err));

//Insert multiple document
User.insertMany([
	{name: 'John Smith', age: 29, email: 'john@example.com'},
	{name: 'John Danvers', age: 25, email: 'johndan@example.com'},
	{name: 'John Joestar', age: 25, email: 'jojo@example.com'}	
	]).then(res => console.log('User saved successfully!',res))
  .catch(err => console.error('Error saving user:', err));
```

---
### Note
Mongoose uses **Operation Buffering**
	Mongoose lets you start using your models immediately, without
	waiting for mongoose to establish a connection to MongoDB.

## **Note** 
**Mongoose Queries( find(), findOneAndUpdate() ,updateOne(),updateMany(), deleteOne(), countDocuments(), distinct(), aggregate() etc**

- **Query Object**: Mongoose queries return a Query Object, not a promise by default.
- **Then-able**: Queries are "then-able" and have a `.then()` method, allowing promise chaining.
- **Lazy Execution**: Queries are lazy-loaded and execute only when interacted with (e.g., `.exec()`, `.then()`, `.catch()`).
- **Promise Behavior**: Though they are not strict promises, Mongoose queries can behave like promises due to `.then()`.

**Best Practices**:

- Use `.exec()` or `async/await` for better readability and to fully leverage promise behavior.
---

