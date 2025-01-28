
**Status:** #Incomplete  
**Tags:**  [[Backend]] [[Database]] [[Mongoose]] [[MongoDB]] [[CRUD]]

### Schema Validations

#### 1. **Built-in Validations**

Mongoose provides built-in validations for schema fields:

- **Required**: Ensures the field must have a value.
    
    ```javascript
    const schema = new Schema({
      name: { type: String, required: true }
    });
    ```
    
- **Min/Max Length**: Limits the length of strings.
    
    ```javascript
    const schema = new Schema({
      name: { type: String, minlength: 3, maxlength: 20 }
    });
    ```
    
- **Min/Max Values**: For numbers.
    
    ```javascript
    const schema = new Schema({
      age: { type: Number, min: 18, max: 65 }
    });
    ```
    
- **Enums**: Restricts values to a predefined set.
    
    ```javascript
    const schema = new Schema({
      role: { type: String, enum: ['admin', 'user', 'guest'] }
    });
    ```
    
- **Match**: Validates strings against a regex pattern.
    
    ```javascript
    const schema = new Schema({
      email: { type: String, match: /.+@.+\..+/ }
    });
    ```
    

---

### Schema Type Options

#### Common Options for Fields

- `type`: Defines the data type (String, Number, Boolean, etc.).
    
- `required`: Indicates if the field must be present.
    
- `default`: Sets a default value.
    
    ```javascript
    const schema = new Schema({
      status: { type: String, default: 'pending' }
    });
    ```
    
- `unique`: Ensures the field value is unique across documents.
    
- `index`: Creates an index for the field.
    
- `validate`: Allows custom validations.
    
    ```javascript
    const schema = new Schema({
      age: {
        type: Number,
        validate: {
          validator: (v) => v > 0,
          message: "Age must be positive."
        }
      }
    });
    ```
### **Mongoose Schema Options**

#### **String**

- `lowercase`: `boolean` – Converts the value to lowercase.
- `uppercase`: `boolean` – Converts the value to uppercase.
- `trim`: `boolean` – Trims whitespace from the value.
- `match`: `RegExp` – Validates if the value matches the specified regular expression.
- `enum`: `Array` – Validates if the value is one of the specified array elements.
- `minLength`: `Number` – Validates if the value's length is not less than the specified number.
- `maxLength`: `Number` – Validates if the value's length is not greater than the specified number.
- `populate`: `Object` – Sets default populate options.

---

#### **Number**

- `min`: `Number` – Validates if the value is greater than or equal to the specified minimum.
- `max`: `Number` – Validates if the value is less than or equal to the specified maximum.
- `enum`: `Array` – Validates if the value matches one of the specified array elements.
- `populate`: `Object` – Sets default populate options.

---

#### **Date**

- `min`: `Date` – Validates if the value is greater than or equal to the specified minimum date.
- `max`: `Date` – Validates if the value is less than or equal to the specified maximum date.
- `expires`: `Number` or `String` – Creates a TTL index; value is expressed in seconds.

---

#### **ObjectId**

- `populate`: `Object` – Sets default populate options.

The `populate` option in Mongoose schemas sets default behavior for populating referenced documents. For example, in a `Post` schema, setting `populate: { select: 'name' }` on an `author` field ensures only the `name` field from the referenced `User` document is retrieved during population.

**Example:**

```javascript
author: {
  type: mongoose.Schema.Types.ObjectId,
  ref: 'User',
  populate: { select: 'name' },
}
```

populate: { select: 'name' }` ensures that when the field is populated, only the `name` field from the referenced document is retrieved. All other fields from the referenced document are excluded by default unless explicitly included.

---
### Validation in Updates

#### Validation with `findOneAndUpdate` or `update`

- By default, Mongoose does not validate fields during updates.
- Enable validation using the `runValidators` option:
    
    ```javascript
    Model.findOneAndUpdate(
      { _id: id },
      { age: 30 },
      { runValidators: true },
      (err, doc) => {
        if (err) console.error(err);
        else console.log("Updated Document:", doc);
      }
    );
    ```
    