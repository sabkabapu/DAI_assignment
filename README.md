# Exploratory Data Analysis (EDA) on Product Sales Dataset

This report details the Exploratory Data Analysis (EDA) performed on a dataset containing sales information for various products across different outlets. The dataset includes **8,523 rows** and **12 columns**, capturing details about items and outlets. The primary objective of this EDA is to understand the structure of the data, identify patterns, and uncover key insights that could inform business strategies or further analyses.

---

## 1. Introduction

### Dataset Description
The dataset comprises the following columns:
- **Item_Identifier**: Unique identifier for each item
- **Item_Weight**: Weight of the item (float, with missing values)
- **Item_Fat_Content**: Fat content category (e.g., 'Low Fat', 'Regular')
- **Item_Visibility**: Percentage of display area allocated to the item
- **Item_Type**: Category of the item (e.g., 'Dairy', 'Snack Foods')
- **Item_MRP**: Maximum Retail Price of the item
- **Outlet_Identifier**: Unique identifier for each outlet
- **Outlet_Establishment_Year**: Year the outlet was established
- **Outlet_Size**: Size of the outlet (e.g., 'Small', 'Medium', 'High', with missing values)
- **Outlet_Location_Type**: Location tier (e.g., 'Tier 1', 'Tier 2', 'Tier 3')
- **Outlet_Type**: Type of outlet (e.g., 'Supermarket Type1', 'Grocery Store')
- **Item_Outlet_Sales**: Sales amount for the item at a specific outlet (target variable)

---

## 2. Data Cleaning and Preprocessing

Several steps were undertaken to clean and preprocess the data for analysis:

### Handling Missing Values
- **Item_Weight**: Approximately **17%** (1,463 out of 8,523) of the values were missing. For this analysis, these were not explicitly handled but could be imputed using the mean or median weight per `Item_Type`.
- **Outlet_Size**: Around **28%** (2,410 out of 8,523) of the values were missing. These could be imputed based on `Outlet_Type` or marked as 'Unknown' for categorical analysis.

### Standardizing Categorical Variables
- **Item_Fat_Content**: Contained inconsistent labels ('Low Fat', 'Regular', 'LF', 'reg', 'low fat'). Standardized as:
  - 'LF' and 'low fat' → 'Low Fat' (5,517 entries)
  - 'reg' → 'Regular' (3,006 entries)

### Feature Engineering
New features were created to enhance the analysis:
- **Outlet_Age**: Calculated as the difference between 2025 (assumed current year) and `Outlet_Establishment_Year`.
- **Item_Code**: Extracted the first three characters of `Item_Identifier` (e.g., 'FDA' from 'FDA15').
- **no_of_items**: Estimated quantity sold by dividing `Item_Outlet_Sales` by `Item_MRP`.
- **Visibility_Category**: Categorized `Item_Visibility` into:
  - Low: ≤ 0.033
  - Medium: 0.033–0.094
  - High: > 0.094
- **MRP_Category**: Categorized `Item_MRP` into:
  - Low: ≤ 94.0
  - Medium: 94.0–185.0
  - High: > 185.0
---

## 3. Exploratory Analysis

The EDA examined the data's structure, distributions, and relationships using statistical summaries and visualizations.

### Initial Data Inspection
- **Shape**: 8,523 rows, 12 columns (modified with feature engineering).
- **Data Types**: 
  - Float: `Item_Weight`, `Item_Visibility`, `Item_MRP`, `Item_Outlet_Sales`
  - Integer: `Outlet_Establishment_Year`
  - Object: Seven categorical columns
- **Missing Values**: 1,463 in `Item_Weight`, 2,410 in `Outlet_Size`.

### Visualizations
1. **Visibility_Category vs Item_Type**:
   - Count plot showing distribution of item types across visibility categories.
2. **Item_Fat_Content vs Item_Type**:
   - Count plot examining fat content distribution across item types.

---

## 4. Key Insights

1. **Item Visibility and Sales**:
   - 'Snack Foods' and 'Fruits and Vegetables' often have 'High' visibility, potentially boosting sales.
2. **Fat Content Distribution**:
   - 'Dairy' and 'Meat' show mixed fat content; 'Soft Drinks' are mostly 'Regular'.
3. **Price and Sales Relationship**:
   - High `MRP_Category` items (MRP > 185.0) generate higher sales revenue, but quantity sold varies.
4. **Outlet Characteristics Impact**:
   - Supermarkets outperform grocery stores in sales; older outlets (e.g., 38 years) maintain strong performance.
5. **Quantity Sold Insights**:
   - Varies widely (e.g., NCD19: ~18.47 units; FDX07: ~4.02 units), reflecting demand differences.

---

## 5. Conclusion

This EDA provided a comprehensive overview of the dataset, identifying patterns in visibility, pricing, and outlet performance.

### Summary of Findings
- High-visibility and higher-priced items drive sales revenue.
- Supermarkets outperform grocery stores.
- Fat content preferences vary by item type.

### Recommendations for Next Steps
- **Handle Missing Values**: Impute `Item_Weight` and `Outlet_Size`.
- **Deep Dive into Sales**: Use statistical tests to confirm differences.
- **Predictive Modeling**: Build models with engineered features.
- **Business Applications**: Optimize product placement and pricing.

This report serves as a foundation for further analysis and business decisions.
