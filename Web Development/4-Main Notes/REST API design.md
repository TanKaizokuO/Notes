**Status:**  #Incomplete  
**Tags:**  [[Backend]] [[Mongoose]] [[CRUD]] [[SQL]]
**Reference:** [Best practices for REST API design](https://stackoverflow.blog/2020/03/02/best-practices-for-rest-api-design/)

---
## Introduction

REST APIs are widely used web interfaces enabling clients like browser apps to communicate with services. Proper API design ensures ease of use, security, performance, and future-proofing.

---

## Core Principles

### 1. **Accept and Respond with JSON**

- JSON is the standard for data transfer: lightweight and universally supported.
- Set `Content-Type` to `application/json` for responses.
- Example (Node.js/Express):
    
    ```javascript
    const express = require('express');
    const app = express();
    
    app.use(express.json());
    app.post('/', (req, res) => res.json(req.body));
    
    app.listen(3000, () => console.log('Server started'));
    ```
    

### 2. **Use Nouns in Endpoint Paths**

- Use nouns to represent entities, e.g., `/articles`.
- HTTP methods convey actions:
    - `GET`: Retrieve resources
    - `POST`: Add new data
    - `PUT`: Update data
    - `DELETE`: Remove data
- Example:
    
    ```javascript
    app.get('/articles', (req, res) => res.json([]));
    app.post('/articles', (req, res) => res.json(req.body));
    ```
    

### 3. **Logical Nesting for Hierarchical Data**

- Reflect relationships in endpoint structure:
    - `/articles/:articleId/comments` for comments of an article.
- Avoid deep nesting; instead, return URIs for related resources.

---

## Error Handling

### 4. **Handle Errors Gracefully**

- Return meaningful HTTP status codes:
    - `400`: Bad Request
    - `401`: Unauthorized
    - `403`: Forbidden
    - `404`: Not Found
    - `500`: Internal Server Error
- Example:
    
    ```javascript
    app.post('/users', (req, res) => {
      const { email } = req.body;
      if (emailExists(email)) {
        return res.status(400).json({ error: 'User already exists' });
      }
      res.json(req.body);
    });
    ```
    

---

## Performance Optimization

### 5. **Filtering, Sorting, and Pagination**

- Allow clients to request subsets of data using query parameters:
    
    ```javascript
    app.get('/employees', (req, res) => {
      const { age } = req.query;
      const filtered = employees.filter(emp => emp.age == age);
      res.json(filtered);
    });
    ```
    

### 6. **Caching**

- Use caching to reduce load and improve performance.
- Example (using `apicache`):
    
    ```javascript
    const apicache = require('apicache');
    app.use(apicache.middleware('5 minutes'));
    ```
    

---

## Security

### 7. **Maintain Good Security Practices**

- Use SSL/TLS to secure communications.
- Enforce role-based access control.
- Apply the principle of least privilege to limit data exposure.

---

## API Versioning

### 8. **Version Your APIs**

- Use `/v1/`, `/v2/`, etc., in endpoint paths to indicate versions:
    
    ```javascript
    app.get('/v1/employees', (req, res) => res.json([]));
    app.get('/v2/employees', (req, res) => res.json([]));
    ```
    
- Gradually phase out old versions to avoid breaking clients.

---

## Summary

Following these best practices ensures REST APIs are:

1. Easy to use and understand.
2. Secure and performant.
3. Scalable and maintainable for future changes.