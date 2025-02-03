## **Phase 1: Introduction to Pandas**

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

### **1.4 Basic Operations**

- **View data:**
    
    ```python
    df.head()   # First 5 rows
    df.tail()   # Last 5 rows
    df.sample() # Random row
    ```
    
- **Check DataFrame info:**
    
    ```python
    df.info()   # Data types & non-null counts
    df.describe()  # Summary statistics
    ```
    
- **Check dimensions & size:**
    
    ```python
    df.shape  # (rows, columns)
    df.size   # Total elements
    ```
    
- **Check for missing values:**
    
    ```python
    df.isnull().sum()  # Count missing values
    df.notnull()  # True for non-missing values
    ```
    

---

## **Phase 2: Data Manipulation**

### **2.1 Data Cleaning**

- **Handle missing values:**
    
    ```python
    df.dropna(inplace=True)  # Remove missing values
    df.fillna(0, inplace=True)  # Replace missing values with 0
    ```
    
- **Remove duplicates:**
    
    ```python
    df.drop_duplicates(inplace=True)
    ```
    
- **Rename columns:**
    
    ```python
    df.rename(columns={'old_name': 'new_name'}, inplace=True)
    ```
    
- **Change data types:**
    
    ```python
    df['column'] = df['column'].astype('int')
    ```
    

---

### **2.2 Filtering and Sorting**

- **Filter rows using Boolean indexing:**
    
    ```python
    df[df['Age'] > 25]  # Select rows where Age > 25
    ```
    
- **Sort data:**
    
    ```python
    df.sort_values(by='Age', ascending=False, inplace=True)
    ```
    
- **Query data:**
    
    ```python
    df.query('Age > 25')
    ```
    

---

### **2.3 Adding and Removing Data**

- **Add columns:**
    
    ```python
    df['Salary'] = [50000, 60000]
    ```
    
- **Drop columns:**
    
    ```python
    df.drop(columns=['Salary'], inplace=True)
    ```
    
- **Add rows:**
    
    ```python
    new_row = {'Name': 'Charlie', 'Age': 35}
    df = df.append(new_row, ignore_index=True)
    ```
    
- **Drop rows:**
    
    ```python
    df.drop(index=[0], inplace=True)
    ```
    

---

### **2.4 Grouping and Aggregation**

- **Group data:**
    
    ```python
    df.groupby('Department').mean()
    ```
    
- **Aggregate multiple statistics:**
    
    ```python
    df.groupby('Department').agg({'Salary': ['mean', 'max']})
    ```
    
- **Pivot tables:**
    
    ```python
    df.pivot_table(values='Salary', index='Department', columns='Gender', aggfunc='mean')
    ```
    

---

## **Phase 3: Advanced Data Manipulation**

### **3.1 Merging and Joining**

- **Concatenate DataFrames:**
    
    ```python
    pd.concat([df1, df2], axis=0)  # Vertical stacking
    pd.concat([df1, df2], axis=1)  # Horizontal stacking
    ```
    
- **Merge DataFrames:**
    
    ```python
    pd.merge(df1, df2, on='ID', how='inner')  # Inner join
    ```
    
- **Join DataFrames:**
    
    ```python
    df1.join(df2, lsuffix='_left', rsuffix='_right')
    ```
    

---

### **3.2 Reshaping Data**

- **Melt data:**
    
    ```python
    df.melt(id_vars=['ID'], var_name='Category', value_name='Value')
    ```
    
- **Pivot data:**
    
    ```python
    df.pivot(index='ID', columns='Category', values='Value')
    ```
    
- **Stack and unstack:**
    
    ```python
    df.stack()
    df.unstack()
    ```
    

---

### **3.3 Handling Time Series Data**

- **Convert to datetime:**
    
    ```python
    df['Date'] = pd.to_datetime(df['Date'])
    ```
    
- **Set datetime index:**
    
    ```python
    df.set_index('Date', inplace=True)
    ```
    
- **Resample time series data:**
    
    ```python
    df.resample('M').mean()  # Monthly average
    ```
    

---

## **Phase 4: Data Analysis and Visualization**

### **4.1 Descriptive Statistics**

- **Summary statistics:**
    
    ```python
    df.describe()
    ```
    
- **Correlation:**
    
    ```python
    df.corr()
    ```
    
- **Covariance:**
    
    ```python
    df.cov()
    ```
    

---

### **4.2 Visualization with Pandas**

- **Basic plots:**
    
    ```python
    df.plot()
    ```
    
- **Histograms:**
    
    ```python
    df['Age'].hist()
    ```
    
- **Box plots:**
    
    ```python
    df.boxplot(column='Salary', by='Department')
    ```
    
- **Scatter plots:**
    
    ```python
    df.plot.scatter(x='Age', y='Salary')
    ```
    

---

### **4.3 Advanced Analysis**

- **Rolling windows:**
    
    ```python
    df['Salary'].rolling(window=3).mean()
    ```
    
- **Expanding windows:**
    
    ```python
    df['Salary'].expanding().mean()
    ```
    
- **Custom functions with `.apply()`:**
    
    ```python
    df['new_col'] = df['Age'].apply(lambda x: 'Senior' if x > 30 else 'Junior')
    ```
    

---

### **Key Takeaways**

✔ **Pandas is essential for data manipulation**  
✔ **Use `.groupby()`, `.merge()`, and `.pivot_table()` for advanced operations**  
✔ **Vectorized operations are faster than loops**  
✔ **Use `.apply()` for custom transformations**

Would you like me to add more **real-world examples**? 🚀