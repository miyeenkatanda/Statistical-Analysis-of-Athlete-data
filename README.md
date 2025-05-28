# Statistical Analysis Functions: T-test and Histograms

This file contains Python functions for performing t-tests (independent and dependent) and for plotting histograms of datasets. These functions are useful for basic statistical analysis and data visualization.

## Functions Included:

### 1. `perform_ttest(series1, series2, test_type="independent")`

* **Purpose:** Calculates the t-statistic and p-value for either an independent (Welch's) t-test or a dependent (paired) t-test.
* **Parameters:**
    * `series1` (array-like): The first dataset.
    * `series2` (array-like): The second dataset.
    * `test_type` (str): Specifies the type of t-test.
        * `"independent"`: Performs Welch's t-test, assuming unequal variances.
        * `"dependent"`: Performs a paired t-test. Requires `series1` and `series2` to have the same length.
* **Returns:** A dictionary with `t_statistic` and `p_value`.
* **Raises:** `ValueError` for invalid `test_type` or mismatched lengths in dependent test.

### 2. `plot_histograms(series1, series2, bins=10, overlay=True)`

* **Purpose:** Generates histograms for two datasets, allowing for overlayed or side-by-side plots.
* **Parameters:**
    * `series1` (array-like): The first dataset.
    * `series2` (array-like): The second dataset.
    * `bins` (int, default=10): The number of bins for the histograms.
    * `overlay` (bool, default=True):
        * `True`: Plots both histograms on the same axes with transparency.
        * `False`: Plots histograms in separate subplots side-by-side.

## Usage Example:

To use these functions, you need to import them and provide your data.

```python
# Import necessary libraries
from scipy.stats import ttest_ind, ttest_rel
import numpy as np
import matplotlib.pyplot as plt

# Define the functions (as provided above in this README)
# ... (copy the perform_ttest and plot_histograms functions here) ...

# Example: Performing an independent t-test on random data
np.random.seed(42) # For reproducibility
data_group1 = np.random.rand(25)
data_group2 = np.random.rand(25)

# Perform and print the t-test result
ttest_result = perform_ttest(data_group1, data_group2, test_type="independent")
print(f"Independent t-test result: {ttest_result}")

# Example: Plotting overlayed histograms
plot_histograms(data_group1, data_group2, bins=10, overlay=True)

# Example: Performing a dependent t-test (assuming related data)
# data_before = np.random.normal(loc=10, scale=2, size=25)
# data_after = data_before + np.random.normal(loc=0.5, scale=0.5, size=25) # Simulate a slight increase
# dependent_ttest_result = perform_ttest(data_before, data_after, test_type="dependent")
# print(f"Dependent t-test result: {dependent_ttest_result}")

# Example: Plotting side-by-side histograms
# plot_histograms(data_group1, data_group2, bins=10, overlay=False)
