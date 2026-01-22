# Customer Segmentation and Personality Analysis

## Executive Summary
This project identifies distinct consumer segments within a retail dataset of 2,240 customers to drive targeted marketing and resource optimization. Using K-Means clustering and Principal Component Analysis (PCA), the analysis revealed four primary customer profiles. A key finding of this study is the distinction between volume and value: while Cluster 3 contributes the highest total revenue to the business (40.62%), Cluster 0 represents the most efficient segment with the highest per-capita spending, contributing 17.45% of revenue from only 6.59% of the population. These insights allow for a transition from broad marketing to a segment-specific strategy.

---

## Data Sourcing
The analysis utilizes the Customer Personality Analysis dataset sourced from Kaggle. This dataset consists of 2240 records and 29 features, encompassing a comprehensive mix of demographic information, purchasing behaviors, and campaign responsiveness. 

Dataset Link: https://www.kaggle.com/datasets/imakash3011/customer-personality-analysis

---

## Data Preprocessing and Cleaning
To ensure the robustness of the clustering model, the raw data was cleaned and standardized through the following steps:

* **Outlier Management**: Rather than removing data points, outliers were addressed by capping values at three standard deviations from the mean across all columns. This approach preserves the sample size while preventing extreme values—such as a 600,000 income entry—from skewing the centroids.
* **Missing Values**: 24 rows had missing income values which was deemed unusable, and was dropped as it only represented 1% of the total dataset.
* **Feature Engineering**: Age was derived from birth year data to represent the demographic landscape accurately. Categorical variables, including Education and Marital Status, were simplified and encoded for model compatibility.

---

## Dimensionality Reduction and Clustering
The modeling phase focused on optimizing cluster cohesion over raw variance explanation:

* **PCA Optimization**: An initial attempt to retain 80% of the variance through a scree chart resulted in high noise and poor cluster definition. The model was refined to use 6 principal components, explaining approximately 50% of the variance. This adjustment improved the Silhouette Score from 0.15 to 0.24, indicating more distinct and well-defined customer segments.
* **K-Means Execution**: The data was partitioned into four clusters (K=4). The selection of four clusters was determined by maximizing the Silhouette Score to ensure practical business interpretability.



---

## Segment Profiles and Revenue Impact

### Cluster 3: The Gourmet Traditionalist (Highest Total Revenue)
* **Population Share**: 22.16%
* **Revenue Contribution**: 45.50%
* **Characteristics**: This is the most valuable group in terms of total dollars. These are high-income individuals who prioritize fresh food categories, specifically Fish and Fruits. They show a strong preference for traditional purchasing channels, including physical stores and catalogs.

### Cluster 2: Seasoned Bargain Hunter
* **Population Share**: 26.22%
* **Revenue Contribution**: 30.11%
* **Characteristics**: Moderate income spenders with the longest average tenure. This group has a high concentration of teenagers at home with moderate total spending and wine consumption. They are the second-highest contributors to total revenue, and are avid deal purchasers.

### Cluster 0: Premium VIPs (Highest Per-Capita Spend)
* **Population Share**: 6.59%
* **Revenue Contribution**: 17.45%
* **Characteristics**: While the smallest group by headcount, they are the most profitable on an individual basis. With an average income over $80,000 and no children at home, they have the highest discretionary income and the highest campaign acceptance rate (74%).

### Cluster 1: Budget-Sensitive Majority
* **Population Share**: 45.04%
* **Revenue Contribution**: 6.94%
* **Characteristics**: The largest segment of the customer base. These are lower-income households with children who visit the website frequently but have low conversion rates – the window shoppers. Their spending is primarily driven by deep discounts and promotional deals.

---

## Strategic Recommendations

* **Maximize High-Value Retention**: Direct the majority of the marketing budget toward Cluster 3 and Cluster 0. For Cluster 3, focus on store-based events and fresh food quality. For Cluster 0, prioritize high-end digital engagement and luxury-tier loyalty perks.
* **Channel Optimization**: Maintain robust catalog and in-store operations for Cluster 3, as they are the primary drivers of total revenue and prefer these "traditional" channels.
* **Inventory Management**: Use Cluster 1 and Cluster 2 to move high volumes of promotional stock. Since Cluster 1 represents nearly half the population but less than 9% of revenue, they should be targeted with low-cost, automated digital marketing rather than expensive physical mailers.
* **Product Cross-Selling**: Leverage Cluster 2’s long-term loyalty and high deal-responsiveness by offering bundled promotional discounts on high-margin "Gold" products when paired with their frequent Wine purchases.

---

## Technical Stack
```text
Tools: Python, Excel
Data Libraries: Pandas, NumPy
Machine Learning: Scikit-learn (PCA, K-Means, StandardScaler)
Visualization: Matplotlib, Seaborn
