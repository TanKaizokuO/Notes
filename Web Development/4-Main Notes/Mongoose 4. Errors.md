**Status:** #Incomplete  
**Tags:**  [[Backend]] [[Database]] [[Mongoose]] [[MongoDB]] 
### Error Handling

#### 1. **Validation Errors**

- Occurs when data does not satisfy schema validation rules.
- Example:
    
    ```javascript
    const doc = new Model({ age: -5 });
    doc.save((err) => {
      if (err) {
        console.error("Validation Error:", err.message);
      }
    });
    ```
    

#### 2. **Duplicate Key Errors**

- Occurs when inserting a duplicate value in a unique field.
- Error code: `11000`.
- Example:
    
    ```javascript
    const doc = new Model({ email: "duplicate@example.com" });
    doc.save((err) => {
      if (err && err.code === 11000) {
        console.error("Duplicate Key Error:", err.message);
      }
    });
    ```
    

#### 3. **Connection Errors**

- Handle database connection issues gracefully:
    
    ```javascript
    mongoose.connection.on("error", (err) => {
      console.error("Database Connection Error:", err);
    });
    ```
    

---

