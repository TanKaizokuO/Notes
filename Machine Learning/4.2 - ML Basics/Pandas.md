
df.rename
df['name'].str.split(' ').str(0)
pd.to_datetime(df('DOB'))
 
### 1. **Importing Pandas**
   ```python
   import pandas as pd
   ```
   - The `pandas` library is imported and aliased as `pd` for convenience.
   - Pandas is a powerful library for data manipulation and analysis in Python.

---

### 2. **Creating an Empty DataFrame**
   ```python
   df = pd.DataFrame()
   ```
   - Creates an empty DataFrame `df`.
   - A DataFrame is a 2D labeled data structure in pandas, similar to a table in a database or an Excel spreadsheet.

---

### 3. **Viewing the First Few Rows**
   ```python
   df.head()
   ```
   - Displays the first 5 rows of the DataFrame.
   - Useful for quickly inspecting the data.
   - Since the DataFrame is empty, this will return an empty DataFrame.

---

### 4. **Viewing the Last Few Rows**
   ```python
   df.tail()
   ```
   - Displays the last 5 rows of the DataFrame.
   - Like `head()`, this is useful for inspecting the data.
   - For an empty DataFrame, this will also return an empty DataFrame.

---

### 5. **Listing Column Names**
   ```python
   df.columns()
   ```
   - **Incorrect Syntax**: The correct method is `df.columns` (without parentheses).
   - `df.columns` returns an Index object containing the column names of the DataFrame.
   - For an empty DataFrame, this will return an empty Index.

   **Correct Syntax:**
   ```python
   df.columns
   ```

---

### 6. **Listing Index Values**
   ```python
   df.index.tolist()
   ```
   - Converts the DataFrame's index to a Python list.
   - The index represents the row labels.
   - For an empty DataFrame, this will return an empty list.

---

### 7. **Generating Descriptive Statistics**
   ```python
   df.describe()
   ```
   - Provides summary statistics for numerical columns in the DataFrame.
   - Statistics include count, mean, standard deviation, min, max, and quartiles.
   - For an empty DataFrame, this will return an empty DataFrame with no statistics.

---

### 8. **Finding Unique Values**
   ```python
   df.unique
   ```
   - **Incorrect Syntax**: The correct method is `df[column_name].unique()` for a specific column.
   - `unique()` returns an array of unique values in a column.
   - For an empty DataFrame, this will raise an error because no column is specified.

   **Correct Syntax:**
   ```python
   df['column_name'].unique()
   ```

---

### 9. **Getting DataFrame Shape**
   ```python
   df.shape
   ```
   - Returns a tuple representing the dimensions of the DataFrame: `(number_of_rows, number_of_columns)`.
   - For an empty DataFrame, this will return `(0, 0)`.

---

### 10. **Getting DataFrame Size**
   ```python
   df.size
   ```
   - Returns the total number of elements in the DataFrame (rows × columns).
   - For an empty DataFrame, this will return `0`.

---
### **11. `df.sample(n)` – Random Sampling**

```python
df.sample(n=5)
```

- Returns a **random sample** of `n` rows from the DataFrame.
- Useful for quick data inspection.

---

### **12. `df.loc[]` – Label-Based Indexing**

```python
df.loc[2, 'name']
df.loc[2, ['name', 'age']]
df.loc[df['age'] > 30]
```

- Used for **label-based** selection.
- Can retrieve **specific rows/columns** using labels.
- Supports **conditional filtering**.

---

### **13. `df.iloc[]` – Position-Based Indexing**

```python
df.iloc[2, 1]  # 3rd row, 2nd column
df.iloc[1:4, 0:2]  # Slicing: rows 1 to 3, columns 0 to 1
```

- Works like a NumPy array.
- Uses **integer index positions** instead of labels.

---

### **14. `df[column]` – Accessing Columns**

```python
df['age']
df[['name', 'age']]
```

- Returns a **single column** as a Series.
- Use double brackets (`[['col1', 'col2']]`) to get multiple columns as a DataFrame.

---

### **15. `df.sort_values()` – Sorting Data**

```python
df.sort_values(by='age', ascending=False)
df.sort_values(by=['age', 'salary'], ascending=[True, False])
```

- Sorts rows based on column values.
- Supports **multiple sorting criteria**.

---

### **16. `for index, row in df.iterrows()` – Iterating Over Rows**

```python
for index, row in df.iterrows():
    print(f"Row {index}: Name - {row['name']}, Age - {row['age']}")
```

- Iterates **row-by-row** in a DataFrame.
- Slower for large datasets – **prefer vectorized operations**.

---

### **17. Filtering Based on Column Values**

```python
df[df['ht_cm'] > 25]
```

- Selects rows where `ht_cm` is greater than 25.

---

### **18. Filtering Strings Using `.str.contains()`**

```python
df[df['name'].str.contains("lol|mol", regex=True)]
```

- Finds rows where `name` contains **"lol" or "mol"**.
- Uses **regular expressions (regex)**.

---
### **19. Using `np.where()` for Conditional Column Assignment**

```python
df['new_price'] = np.where(df['coffee'] == 'espresso', 3.99, 5.99)
```

- This **creates a new column `new_price`**:
    - If `coffee` is `"espresso"`, the price is set to **3.99**.
    - Otherwise, the price is set to **5.99**.
- `np.where(condition, value_if_true, value_if_false)` works like an **inline if-else** for Pandas.

✅ **Efficient alternative to `.apply()` for conditional column creation**.

---

### **20. Dropping Columns or Rows Using `df.drop()`**

#### **Dropping a Column**

```python
df.drop(columns=['new_price'], inplace=True)
```

- Removes the `new_price` column.
- `inplace=True` modifies the DataFrame directly.

#### **Dropping Rows by Index**

```python
df.drop(index=[2, 4], inplace=True)
```

- Removes rows with index **2 and 4**.

#### **Dropping Rows by Condition**

```python
df.drop(df[df['coffee'] == 'espresso'].index, inplace=True)
```

- Removes **all rows where `coffee` is 'espresso'**.
---



### Summary of Output for an Empty DataFrame
| Command              | Output for Empty DataFrame  | Notes                                             |
| -------------------- | --------------------------- | ------------------------------------------------- |
| `df.head()`          | Empty DataFrame             | Displays first 5 rows (none in this case).        |
| `df.tail()`          | Empty DataFrame             | Displays last 5 rows (none in this case).         |
| `df.columns`         | Empty Index                 | Returns column names (none in this case).         |
| `df.index.tolist()`  | Empty list `[]`             | Converts index to a list (no rows in this case).  |
| `df.describe()`      | Empty DataFrame             | Provides summary statistics (none in this case).  |
| `df['col'].unique()` | Error (no column specified) | Requires a specific column to find unique values. |
| `df.shape`           | `(0, 0)`                    | Indicates 0 rows and 0 columns.                   |
| `df.size`            | `0`                         | Total number of elements is 0.                    |

---

### Key Takeaways
- **Empty DataFrame**: Most operations on an empty DataFrame will return empty results or raise errors.
- **Common Methods**:
  - Use `head()` and `tail()` to inspect data.
  - Use `columns` to view column names.
  - Use `describe()` for summary statistics.
  - Use `shape` and `size` to understand the dimensions and size of the DataFrame.
- **Errors**: Be cautious with methods like `unique()`, which require a specific column to operate on.

