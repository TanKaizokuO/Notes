**Status:**  #Incomplete 
**Tags:** [[Backend]] [[Database]] [[CRUD]]

---

# SQL Notes

## **What is a Database?**

- **Definition**: A database is a collection of data in a format that can be easily accessed and managed.
- **Why Databases?**
    - Store large amounts of data.
    - Features like **security** and **scalability**.
    - Simplifies **insert**, **update**, and **delete** operations.

---

## **SQL (Structured Query Language)**

- A programming language used to interact with **relational databases**.

### **Table Queries**

- **Create Database**:
    
    ```sql
    CREATE DATABASE db_name;
    CREATE DATABASE IF NOT EXISTS db_name;
    ```
    
- **Drop Database**:
    
    ```sql
    DROP DATABASE db_name;
    DROP DATABASE IF EXISTS db_name;
    ```
    
- **Show Databases and Tables**:
    
    ```sql
    SHOW DATABASES;
    SHOW TABLES;
    ```
    
- **Create Table**:
    
    ```sql
    CREATE TABLE table_name (
      column_name1 datatype constraint,
      column_name2 datatype constraint
    );
    ```
    

---

## **Constraints**

- **Definition**: Rules applied to the data in a table.
- **Types**:
    - **NOT NULL**: Ensures columns cannot have null values.
    - **UNIQUE**: Ensures all values in a column are distinct.
    - **DEFAULT**: Sets a default value for the column.
        - Example: `Salary INT DEFAULT 25000`
    - **CHECK**: Restricts values allowed in a column.
        - Example:
            
            ```sql
            CONSTRAINT age_check CHECK (age >= 18 AND city = 'Delhi');
            ```
            

---

## **Keys**

- **Definition**: Special columns in a table that help organize and link data.

### **Primary Key**

- **Purpose**: Uniquely identifies each row in a table.
- **Rules**:
    - Only one primary key per table.
    - Cannot have null values.
- **Example**:
    
    ```sql
    CREATE TABLE temp (
      id INT NOT NULL,
      PRIMARY KEY (id)
    );
    ```
    

### **Foreign Key**

- **Purpose**: Establishes a relationship between tables by referencing a primary key in another table.
- **Rules**:
    - Can have duplicate and null values.
    - A table can have multiple foreign keys.
- **Example**:
    
    ```sql
    CREATE TABLE temp (
      cust_id INT,
      FOREIGN KEY (cust_id) REFERENCES customer(id)
    );
    ```
    

---

## **Basic SQL Commands**

### **Insert Data**

```sql
INSERT INTO table_name (colname1, colname2) 
VALUES (value1, value2), (value3, value4);
```

### **Select Data**

- **Basic Selection**:
    
    ```sql
    SELECT col1, col2 FROM table_name;
    ```
    
- **Distinct Selection**:
    
    ```sql
    SELECT DISTINCT column FROM table_name;
    ```
    
- **Select All Columns**:
    
    ```sql
    SELECT * FROM table_name;
    ```
    

---

## **Example Table**

```sql
CREATE TABLE USER (
  id INT UNIQUE,
  name VARCHAR(35) NOT NULL,
  email VARCHAR(35) UNIQUE,
  followers INT DEFAULT 0,
  following INT DEFAULT 0
);
```

---
