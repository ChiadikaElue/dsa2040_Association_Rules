# DSA 2040 Assignment Report: Association Rule Mining

## 1. Introduction

Association rule mining is a fundamental technique in data mining that discovers interesting relationships between variables in large datasets. This project applies association rule mining to a grocery store transactions dataset to identify patterns in customer purchasing behavior that can inform retail strategy and business decisions.

## 2. Data Preparation Process

### 2.1 Dataset Loading and Exploration
The dataset was loaded from a CSV file containing 38,765 initial transactions. Initial exploration revealed the dataset structure with three main attributes: customer ID, transaction date, and product description.

### 2.2 Data Cleaning
- **Duplicate Removal**: 759 duplicate transactions were identified and removed
- **Missing Values**: No missing values were found in the dataset
- **Final Dataset**: 38,006 clean transactions remained

### 2.3 Transaction Encoding
Transactions were grouped by customer and date, then encoded into a binary matrix format suitable for association rule mining using the TransactionEncoder from mlxtend:

```python
transactions = df.groupby(['Member_number', 'Date'])['itemDescription'].apply(list).tolist()
te = TransactionEncoder()
te_array = te.fit(transactions).transform(transactions)
basket = pd.DataFrame(te_array, columns=te.columns_)
```

## 3. Methodology
### 3.1 Frequent Itemset Mining
Two algorithms were implemented with different support thresholds:

**- Apriori Algorithm:**

Minimum support: 0.01 and 0.03

Identified 69 and 27 itemsets respectively

**- FP-Growth Algorithm:**

Minimum support: 0.01

Identified 69 itemsets

### 3.2 Association Rule Generation
Rules were generated using the following metrics:

**Support:** Frequency of itemset occurrence

**Confidence:** Conditional probability of consequent given antecedent

**Lift:** Strength of association compared to random chance

## 4. Key Findings
### 4.1 Frequent Itemset Analysis
The analysis revealed that dairy products dominate the top frequent items:

Whole milk (15.79% support) - Most popular item

Other vegetables (12.21%) - Healthy eating trend

Rolls/buns (11.00%) - Bakery staples

Soda (9.71%) - Beverage category

Yogurt (8.59%) - Dairy category

### 4.2 Strong Association Rules
Three particularly interesting rules were identified:

**Rule 1: Curd → Sausage**

Lift: 1.45

Confidence: 8.73%

Interpretation: Customers who buy curd are 45% more likely to buy sausage than random chance. This suggests complementary breakfast or cooking patterns.

**Rule 2: Brown bread → Canned beer**

Lift: 1.36

Confidence: 6.39%

Interpretation: Brown bread purchasers show higher likelihood of buying canned beer, possibly indicating snack or party shopping behavior.

**Rule 3: Frozen vegetables → Sausage**

Lift: 1.23

Confidence: 7.40%

Interpretation: Convenience-focused shoppers buying frozen vegetables also tend to purchase sausage, suggesting quick meal preparation patterns.

### 4.3 Algorithm Performance
FP-Growth demonstrated competitive performance with Apriori, finding the same number of itemsets (69) with slightly longer runtime (0.50s vs 0.28s), but offering computational advantages for larger datasets.

## 5. Business and Domain Insights
### 5.1 Retail Strategy Implications
**- Product Placement:** The strong association between curd and sausage suggests they should be placed in proximity to encourage cross-purchases.

**- Promotional Campaigns:** Bundle deals could be created for high-lift pairs like brown bread and canned beer.

**- Inventory Management:** High-support items like whole milk should maintain adequate stock levels, while associated items should be stocked considering their relationship.

### 5.2 Customer Behavior Insights
**- Health Consciousness:** Vegetables and yogurt appearing in top items indicates health-aware shopping behavior

**- Convenience Orientation:** Frozen vegetables and prepared items suggest time-constrained shopping patterns

**- Meal Planning:** Product associations reveal common meal combinations and cooking habits

## 6. Limitations and Future Work
### 6.1 Current Limitations
- Temporal patterns (seasonality, time of day) were not considered

- Customer segmentation was not implemented

- Product categories could provide broader pattern insights

### 6.2 Future Enhancements
- Implement temporal analysis to identify seasonal patterns

- Add customer segmentation based on purchasing behavior

- Incorporate product categories for hierarchical analysis

- Develop real-time recommendation systems

## 7. Conclusion
This association rule mining project successfully identified meaningful patterns in grocery transaction data. The discovered rules provide actionable insights for retail optimization, demonstrating the practical value of data mining techniques in business intelligence. The implementation of both Apriori and FP-Growth algorithms provided comprehensive analysis of frequent patterns and their business implications.

The project highlights how data mining can transform raw transaction data into strategic business knowledge, enabling data-driven decision making in retail operations
