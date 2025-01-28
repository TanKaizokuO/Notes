
**Status:**  #Complete 
**Tags:**  [[Backend]] [[server]]

# Node.js Basics

```json
"scripts": {
    "format": "prettier --write .",
    "start": "node index.js",
    "dev": "nodemon index.js"
}
````

## `process` Object

- Provides information about and control over the current Node.js process.
- `process.argv`: Returns an array containing command-line arguments passed during execution.
    
    ```javascript
    console.log(process.argv);
    
    // Run with:
    // node script.js Tan Man Fan
    
    Output:
    [
      "Node location",
      "script location",
      "Tan",
      "Man",
      "Fan"
    ]
    ```
    

## Modules

### Exporting and Importing

- Example module (`math.js`):
    
    ```javascript
    const add = (a, b) => a + b;
    const mul = (a, b) => a * b;
    const pi = 3.14;
    const g = 9.8;
    
    module.exports = { add, mul, pi, g };
    ```
    
- Example consumer (`script.js`):
    
    ```javascript
    const math = require("./math");
    console.log(math.add(2, 2)); // Output: 4
    ```
    

## NPM (Node Package Manager)

- **Purpose:** Standard package manager for Node.js.
- **Important Files:**
    - `node_modules`: Contains all installed dependencies.
    - `package-lock.json`: Records exact versions of all dependencies and sub-dependencies.
    - `package.json`: Metadata for the project (e.g., name, version, scripts).
        
        ```json
        {
          "type": "module",
          "scripts": {
            "start": "node index.js",
            "dev": "nodemon index.js"
          }
        }
        ```
        
- **Common Commands:**
    - Install package globally: `npm i -g <package_name>` (avoid unless necessary).
    - Local installation: `npm install <package_name>`.

---

# Express Framework

## Setup:

```javascript
import express from "express";

const app = express();
const port = 3000;

app.listen(port, () => {
    console.log(`App listening on port ${port}`);
});
```

## Routing:

1. **Basic Route**:
    
    ```javascript
    app.get("/apple", (req, res) => {
        res.send({ name: "apple", color: "red" });
    });
    ```
    
2. **Path Parameters**:
    
    ```javascript
    app.get("/user/:username", (req, res) => {
        const username = req.params.username;
        res.send(`This account belongs to @${username}`);
    });
    ```
    
3. **Query Strings**:
    
    ```javascript
    app.get("/search", (req, res) => {
        const query = req.query;
        res.send(`Search: ${JSON.stringify(query)}`);
    });
    // Example URL: /search?q=Tan&job=student
    // Output: Search: {"q":"Tan","job":"student"}
    ```
    

---

# EJS (Embedded JavaScript)

- EJS is a templating engine for Node.js, allowing you to generate HTML with dynamic content.

## Example Usage:

1. Create a `views` folder.
2. Code:
    
    ```javascript
    const express = require('express');
    app.set('view engine', 'ejs');
    
    app.get('/', (req, res) => {
        res.render('home.ejs', { title: 'Home' });
    });
    ```
    
3. `home.ejs`:
    
    ```html
    <h1>Tanishq Bhattacharjee <%= title %></h1>
    <h2>Web Developer</h2>
    ```
    

## Interpolation in EJS:

```html
<h3>Competitive programming wins: <%= 6 * 3 %></h3>
<!-- Output: Competitive programming wins: 18 -->
```

## Using `data.json`:

```javascript
import igData from './data.json' assert { type: 'json' };

app.get('/ig/:username', (req, res) => {
    let { username } = req.params;
    let instaData = igData[username];
    console.log(instaData);
    res.render('ig.ejs', { instaData });
});
```

## Includes:

- Includes are relative to the template with the `include` call.
- Example:
    
    ```html
    <%- include('user/show'); %>
    ```
    

---

# Forms and Requests

## GET Request:

```html
<form action="http://localhost:3005/register" method="get">
    <label for="email">Email: </label>
    <input type="text" name="email" id="email" />
    <label for="password">Password: </label>
    <input type="password" name="password" id="password" />
    <button>Submit</button>
</form>
```

## POST Request:

```html
<form action="http://localhost:3005/register" method="post">
    <label for="email">Email: </label>
    <input type="text" name="email" id="email" />
    <label for="password">Password: </label>
    <input type="password" name="password" id="password" />
    <button>Submit</button>
</form>
```

## Backend:

### GET Request:

```javascript
app.get('/register', (req, res) => {
    let { email, password } = req.query;
    res.send(`Welcome ${email}! Your password is ${password}`);
});
```

### POST Request:

```javascript
app.use(express.urlencoded({ extended: true })); // Middleware
app.use(express.json()); // Parse JSON data

app.post('/register', (req, res) => {
    console.log(req.body); 
    // Output: { email: 'admin@example.com', password: 'securepassword123' }
});
```

## References
