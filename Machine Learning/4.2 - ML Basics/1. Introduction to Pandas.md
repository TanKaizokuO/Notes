
### **1.1 What is Pandas?**

- A Python library for **data manipulation & analysis**.
- Built on **NumPy** and integrates well with **Matplotlib** for visualization.

---

### **1.2 Basic Data Structures**

#### **Series** (1D labeled array)

- **Creating a Series:**
    
    ```python
    import pandas as pd
    s = pd.Series([10, 20, 30, 40])
    ```
    
- **Accessing elements:**
    
    ```python
    s.loc[0]  # Access by label
    s.iloc[2]  # Access by position
    ```
    
- **Basic operations:**
    
    ```python
    s + 10  # Element-wise addition
    s * 2   # Element-wise multiplication
    ```
    

#### **DataFrame** (2D labeled data structure)

- **Creating a DataFrame:**
    
    ```python
    data = {'Name': ['Alice', 'Bob'], 'Age': [25, 30]}
    df = pd.DataFrame(data)
    ```
    
- **Understanding rows & columns:**
    - **Rows are indexed**, columns have names.
    - **Accessing rows & columns:**
        
        ```python
        df.loc[0]  # Access first row by label
        df.iloc[1]  # Access second row by position
        df['Name']  # Access column
        ```
        

---

### **1.3 Reading and Writing Data**

- **Read from CSV:**
    
    ```python
    df = pd.read_csv('data.csv')
    ```
    
- **Write to CSV:**
    
    ```python
    df.to_csv('output.csv', index=False)
    ```
    
- **Read other formats:**
    
    ```python
    pd.read_excel('data.xlsx')   # Excel
    pd.read_json('data.json')    # JSON
    pd.read_sql('SELECT * FROM table', conn)  # SQL
    ```
    

---
### **1.4 Basic Operations (Elaborated)**

Pandas provides various operations to explore, inspect, and understand datasets. These operations help in **data exploration** and **preliminary analysis** before applying transformations and modeling.

---

### **Viewing Data in a DataFrame**

When working with large datasets, it's useful to **preview** the data instead of displaying everything.

- **View the first few rows:**
    
    ```python
    df.head()  # By default, returns the first 5 rows
    df.head(10)  # Returns the first 10 rows
    ```
    
- **View the last few rows:**
    
    ```python
    df.tail()  # Returns the last 5 rows
    df.tail(3)  # Returns the last 3 rows
    ```
    
- **View a random sample:**
    
    ```python
    df.sample()  # Returns a random row
    df.sample(5)  # Returns 5 random rows
    ```
    

**Why use these?**

- Helps get an idea of the structure of data.
- Useful when working with **large datasets** where printing everything isn’t feasible.

---

### **Checking DataFrame Information**

#### **1. Understanding the structure of data**

- **Check metadata and data types:**
    
    ```python
    df.info()
    ```
    
    **Output Example:**
    
    ```
    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 100 entries, 0 to 99
    Data columns (total 5 columns):
    #   Column    Non-Null Count  Dtype  
    ---  ------    --------------  -----  
    0   Name      100 non-null     object 
    1   Age       98 non-null      float64
    2   Salary    95 non-null      float64
    3   City      100 non-null     object 
    4   Joining   100 non-null     datetime64[ns]
    dtypes: float64(2), object(2), datetime64ry usage: 4.0 KB
    ```
    
    **Key Points:**
    
    - **Total number of rows and columns.**
    - **Column names and data types (int, float, object, datetime, etc.).**
    - **Number of non-null values per column** (helps detect missing values).
    - **Memory usage** (important for large datasets).

---

#### **2. Summary Statistics for Numerical Data**

- **Generate summary statistics for numeric columns:**
    
    ```python
    df.describe()
    ```
    
    **Output Example:**
    
    ```
              Age       Salary
    count   98.000000   95.000000
    mean    35.489796   58000.250000
    std     10.423563   10250.125485
    min     22.000000   35000.000000
    25%     28.000000   47000.000000
    50%     35.000000   58000.000000
    75%     42.000000   68000.000000
    max     58.000000   95000.000000
    ```
    
    **What this tells us:**
    
    - **Count**: Total non-null values.
    - **Mean**: Average of the column.
    - **Standard Deviation (std)**: Measures the spread of values.
    - **Min & Max**: Smallest and largest values.
    - **Percentiles (25%, 50%, 75%)**: Helps understand the distribution.
- **For categorical columns, use `describe(include='object')`:**
    
    ```python
    df.describe(include='object')
    ```
    
    **This gives the count, unique values, top occurring value, and its frequency.**
    

---

### **Checking Data Dimensions & Size**

Understanding the size of a dataset is useful when handling large files.

- **Check number of rows and columns:**
    
    ```python
    df.shape  # Returns (rows, columns)
    ```
    
    **Example Output:**
    
    ```python
    (100, 5)  # 100 rows, 5 columns
    ```
    
- **Check total elements in DataFrame:**
    
    ```python
    df.size  # Returns total number of elements (rows * columns)
    ```
    
    **Example Output:**
    
    ```python
    500  # 100 rows * 5 columns
    ```
    

---

### **Checking for Missing Values**

Missing values can cause errors in calculations and must be handled properly.

- **Check for missing values column-wise:**
    
    ```python
    df.isnull().sum()
    ```
    
    **Example Output:**
    
    ```
    Name       0
    Age        2
    Salary     5
    City       0
    Joining    0
    dtype: int64
    ```
    
    **Interpretation:**
    
    - 2 missing values in **Age**.
    - 5 missing values in **Salary**.
    - **Name, City, and Joining have no missing values.**
- **Find rows with missing values:**
    
    ```python
    df[df.isnull().any(axis=1)]
    ```
    
    **Output:**  
    Displays only rows where at least one column has missing values.
    
- **Check for missing values at a detailed level:**
    
    ```python
    df.isnull()
    ```
    
    This returns **True/False** for each element.
    
- **Check for non-missing values:**
    
    ```python
    df.notnull()
    ```
    
    This returns **True** where values are present.
    

---

### **Handling Missing Values**

- **Drop missing values (Remove rows with NaN values):**
    
    ```python
    df.dropna(inplace=True)
    ```
    
    - Removes all rows where any column has a missing value.
    - `inplace=True` modifies the DataFrame directly.
- **Fill missing values with a specific value:**
    
    ```python
    df.fillna(0, inplace=True)  # Replaces NaN with 0
    df['Age'].fillna(df['Age'].mean(), inplace=True)  # Replaces NaN with column's mean
    ```
    
    - Useful when **zero is a valid default value** or **taking the mean is appropriate**.
- **Forward fill (propagate last valid value forward):**
    
    ```python
    df.fillna(method='ffill', inplace=True)
    ```
    
    - Copies the last known value **down** to the next row.
- **Backward fill (propagate next valid value backward):**
    
    ```python
    df.fillna(method='bfill', inplace=True)
    ```
    
    - Copies the next available value **up** to the previous row.

---

### **Summary: Key Operations**

|Operation|Description|
|---|---|
|`df.head(n)`|Show first `n` rows|
|`df.tail(n)`|Show last `n` rows|
|`df.sample(n)`|Show random `n` rows|
|`df.info()`|Get metadata about DataFrame|
|`df.describe()`|Get statistical summary of numerical columns|
|`df.shape`|Get dimensions `(rows, columns)`|
|`df.size`|Get total elements `(rows * columns)`|
|`df.isnull().sum()`|Count missing values per column|
|`df.dropna()`|Remove rows with missing values|
|`df.fillna(value)`|Replace missing values with `value`|
|`df.fillna(method='ffill')`|Fill missing values using forward fill|
|`df.fillna(method='bfill')`|Fill missing values using backward fill|

---

### **Conclusion**

- Understanding **basic operations** in Pandas is essential for **exploring data** before performing transformations or analysis.
- Checking for **missing values** helps prevent errors in data processing.
- Using **statistical summaries** (`describe()`, `info()`, `shape`) is useful for **initial data analysis**.
- Knowing how to **fill or remove missing data** ensures that datasets are ready for further use.

Would you like additional examples or explanations? 🚀