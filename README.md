# DSA 2040: Association Rule Mining with Real-World Data

**Author:** Chiadika Elue

## Project Overview

This project implements association rule mining on a real-world grocery transactions dataset to discover meaningful patterns and relationships between products purchased together.

## Dataset

- **Name:** Groceries Dataset
- **Source:** Custom retail transactions data
- **Records:** 38,006 transactions (after cleaning)
- **Unique Customers:** 3,898
- **Unique Items:** 167
- **Time Period:** 2014-2015

### Dataset Description
The dataset contains grocery store transactions with three columns:
- `Member_number`: Customer identifier
- `Date`: Transaction date
- `itemDescription`: Product purchased

## Implementation

### Libraries Used
```python
pandas, numpy, matplotlib, seaborn
mlxtend.frequent_patterns (apriori, fpgrowth, association_rules)
warnings

Key Steps
Data Preparation

Loaded and explored dataset structure

Removed duplicates (759 records)

Grouped transactions by customer and date

Encoded transactions using TransactionEncoder

Frequent Itemset Mining

Implemented Apriori algorithm with support thresholds: 0.01 and 0.03

Implemented FP-Growth algorithm with support threshold: 0.01

Compared algorithm performance and itemset discovery

Association Rule Generation

Generated rules using lift metric (min_threshold=1.0)

Analyzed rules using confidence, lift, and support

Identified top association rules

Visualization

Created bar chart of top 10 frequent itemsets

Performance comparison between algorithms


### Sample Outputs
Top 5 Frequent Itemsets
Itemset	Support
Whole milk	15.79%
Other vegetables	12.21%
Rolls/buns	11.00%
Soda	9.71%
Yogurt	8.59%
Top 3 Association Rules
Curd → Sausage (Lift: 1.45, Confidence: 8.73%)

Brown bread → Canned beer (Lift: 1.36, Confidence: 6.39%)

Frozen vegetables → Sausage (Lift: 1.23, Confidence: 7.40%)

Algorithm Performance Comparison
Algorithm	Support	Itemsets Found	Runtime
Apriori	0.01	69	0.28s
Apriori	0.03	27	0.07s
FP-Growth	0.01	69	0.50s

###  Business Insights
Product Placement: Curd and sausage show strong association - consider placing them nearby

Promotion Strategy: Bundle deals for brown bread and canned beer

Inventory Management: Ensure adequate stock of high-support items like whole milk

### How to Run
Clone the repository:

bash
git clone https://github.com/username/dsa2040-association-rules
Install dependencies:

bash
pip install -r requirements.txt
Run the Jupyter notebook:

bash
jupyter notebook notebooks/association_analysis.ipynb

Google Colab Notebook
https://colab.research.google.com/drive/1yNFOv-Lu_I4ZSO-fjyD4JaUunGkw7kH0?usp=sharing
