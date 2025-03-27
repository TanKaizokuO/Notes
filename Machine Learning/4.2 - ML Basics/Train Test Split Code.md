```python
import numpy as np
from sklearn.model_selection import train_test_split

# Step 1: Generate artificial data
np.random.seed(42)
X = np.random.rand(100, 2)  # Random features for demonstration
y = 3 + 5 * X[:, 0] + np.random.randn(100)  # Target variable with some noise

# Step 2: Perform train-test split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)

# Explanation of the variables after splitting:
print("Training set shape:", X_train.shape)
print("Testing set shape:", X_test.shape)
```

**Code Explanation:**

- **Generating Data**: We create 100 samples with 2 features each and a target variable that is linearly related to one feature plus some random noise.
  
- **Train-Test Split**: The `train_test_split` function divides the data into training and testing sets. Here, 80% of the data is used for training (`X_train`, `y_train`), and 20% is reserved for testing (`X_test`, `y_test`).

- **Random State**: Ensures that the split is reproducible across different runs.

This approach ensures that we can evaluate our model's performance on unseen data, which is crucial for assessing how well the model will generalize to new inputs.