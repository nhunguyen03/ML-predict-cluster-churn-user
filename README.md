## OVERVIEW
Churn is a critical issue for any retailer, as retaining existing customers is often more cost-effective than acquiring new ones. 
To effectively reduce the churn rate, it is essential to understand the behavior and patterns of churned users, 
predict potential churners using machine learning models, and tailor promotional strategies to retain at-risk customers.

The project will answer **3 key questions**:
1. What are the patterns/behavior of churned users? What are your suggestions to the company to reduce churned users?
2. Build the Machine Learning model for predicting churned users (fine tuning)
3. Company would like to offer targeted promotions for churn user. Segment these churned users into groups based on the behaviors. What are differences among clusters?

## DETAIL
- **Data Collection** based on customer transactions, including the date of the last purchase, the total number of purchases, and the total amount spent.

- **Calculate RFM Metrics:**
**Recency**: Calculate the number of days since the last purchase for each customer.
**Frequency**: Count the total number of purchases each customer has made.
**Monetary**: Sum the total amount spent by each customer.
  
- **Score RFM**:
Divide the customers into quartiles for each RFM metric. This means splitting the customers into 5 groups based on their scores.
Assign scores from 1 to 5 for each metric, where 1 is the lowest quartile and 5 is the highest quartile. The scoring can be interpreted as follows:
**Recency**: The most recent buyers get a score of 5, while the least recent get a score of 1.
**Frequency**: The most frequent buyers get a score of 5, while the least frequent get a score of 1.
**Monetary**: The highest spenders get a score of 5, while the lowest spenders get a score of 1.

![Customer Segmentation - RFM method](assets/segment_RFM.png)

## STRATEGY
![Customer Segmentation - RFM method](assets/result_segmen_RFM.png)

![Strategy for Each Segmentation](assets/strategy_segment.png)
