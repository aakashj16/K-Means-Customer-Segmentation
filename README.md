# K-Means-Customer-Segmentation

This repository contains an implementation of the K-Means clustering algorithm for customer segmentation. It demonstrates how to group customers into distinct segments based on their behavior, demographics, or other relevant features, enabling targeted marketing strategies and personalized service offerings.

## Overview

Understanding customer behavior is crucial for businesses to optimize marketing strategies, improve customer retention, and drive sales growth. This project leverages K-Means clustering to segment customers based on their purchasing patterns, helping businesses identify distinct groups with similar shopping habits.

The dataset consists of transactional data from an e-commerce platform. By engineering meaningful features and applying clustering techniques, this project aims to:
- Identify customer segments based on shopping behavior.
- Analyze spending trends to recognize high-value customers.
- Detect churn risks by examining recency and transaction frequency.
- Optimize marketing campaigns by tailoring strategies to different segments.

Using data preprocessing, feature engineering, outlier detection, and model optimization, we ensure robust clustering results. The final model assigns customers to segments, enabling businesses to gain data-driven insights into their customer base.

## Dataset
The dataset (`Customer Segmentation.csv`) includes columns such as:
- **invoice_number:** Unique identifier for each transaction
- **stock_code:** Product code
- **description:** Product description
- **quantity:** Number of products purchased
- **invoice_date:** Transaction date
- **unit_price:** Price per unit
- **customer_id:** Unique customer identifier
- **country:** Customer’s country

## Libraries Used
- **Data Manipulation & Processing:** numpy, pandas
- **Visualization:** matplotlib, seaborn
- **Outlier Detection:** IsolationForest
- **Feature Scaling & Reduction:** StandardScaler, Variance Inflation Factor (VIF)
- **Model Optimization:** optuna
- **Clustering & Evaluation:** KMeans, silhouette_score, davies_bouldin_score

## Key Steps
1. ### Data Preprocessing
- Removed duplicate records
- Handled missing values (customer_id, description)
- Identified and removed erroneous stock_code values
- Filtered transactions with negative or zero unit_price
- Created new features like transaction_status, total_spend, average_transaction_value
2. ### Feature Engineering
- **Recency:** Days since last purchase
- **Frequency:** Total transactions and total products purchased
- **Monetary:** Total and average spend per customer
- **Behavioral Trends:** Favorite shopping day, hour, and purchase patterns
- **Geographical Analysis:** Identified top ordering countries
- **Cancellation Trends:** Cancellation frequency and rate
3. ### Outlier Detection & Treatment
- Used Isolation Forest to detect and remove outliers
- Verified outliers using the Interquartile Range (IQR) method
4. ### Feature Scaling & Reduction
- Applied Variance Inflation Factor (VIF) to remove multicollinear features
- Scaled features using StandardScaler
5. ### K-Means Clustering
- Used Optuna to optimize K-Means hyperparameters
- Evaluated models using Silhouette Score and Davies-Bouldin Index
- Assigned clusters to customers based on their purchasing patterns

## Results
- Identified distinct customer segments with unique purchasing behaviors
- Created interpretable customer profiles using cluster statistics

## Customer Segment Analysis  

| Metric                               | Cluster 0 (Low-Value Buyers) | Cluster 1 (High-Value Buyers) |
|--------------------------------------|------------------------------|-------------------------------|
| **Days Since Last Purchase**         | 112.90                       | 35.59                         |
| **Total Products Purchased**         | 328.46                       | 1553.88                       |
| **Average Transaction Value ($)**    | 261.76                       | 335.88                        |
| **Unique Products Purchased**        | 33.79                        | 112.02                        |
| **Average Days Between Purchases**   | 3.41                         | 2.50                          |
| **Percentage of UK Customers**       | 91.7%                        | 93.4%                         |
| **Cancellation Frequency**           | 0.18                         | 1.63                          |
| **Cancellation Rate**                | 5.76%                        | 20.55%                        |
| **Spending Variability (Std Dev $)** | 51.83                        | 303.39                        |

## Insights From Consumer Segment Analysis
**Cluster 0: Infrequent, Low-Value Buyers**
- **Low Engagement:** Last purchase was on average 112 days ago, indicating inactive or churned customers.
- **Lower Purchase Volume:** Bought 328 products on average across transactions.
- **Lower Spending Power:** Average transaction value: $261.76, indicating budget-conscious shoppers.
- **Limited Variety:** Purchased from ~34 unique products, suggesting focused buying habits.
- **Low Cancellations:** 0.18 cancelled orders on average, with a 5.76% cancellation rate.
- **Consistent Spending:** Standard deviation in monthly spending: $51.83, showing predictable spending patterns.

**Cluster 1: High-Value, Frequent Buyers**
- **Highly Engaged:** Last purchase was just 35 days ago, indicating active and loyal customers.
- **Heavy Buyers:** Bought 1,554 products on average, significantly more than Cluster 0.
- **High Spending Power:** Average transaction value: $335.88, making them premium customers.
- **Diverse Purchases:** Purchased ~112 unique products, showing broad shopping interests.
- **Higher Cancellations:** 1.63 cancelled orders on average, with a 20.55% cancellation rate, meaning they might order in bulk and return items.
- **Fluctuating Spending:** Standard deviation in monthly spending: $303.39, suggesting variable spending habits (e.g., seasonal spikes or bulk purchases).

## Key Business Takeaways
- **Target Cluster 1 for Loyalty Programs:** They are high-value customers but have a higher cancellation rate. Offering incentives like discounts on future purchases could improve retention.
- **Re-Engage Cluster 0 with Win-Back Campaigns:** Since they are less engaged, targeted promotions (e.g., limited-time offers or personalized recommendations) could bring them back.
- **Investigate High Cancellation Rate in Cluster 1:** Understand why these customers cancel frequently. If it’s due to stock issues or product dissatisfaction, adjustments in inventory or product descriptions may be needed.
- **Leverage Product Recommendations:** Since Cluster 1 buys a wider variety of products, personalized recommendations and cross-selling strategies could further increase revenue.
- **Align Promotional Campaigns with Customer Segments:** Since Cluster 0 is dominant, marketing efforts should primarily cater to their needs while ensuring premium services and personalized engagement for Cluster 1.