## OVERVIEW
Churn is a critical issue for any retailer, as retaining existing customers is often more cost-effective than acquiring new ones. 
To effectively reduce the churn rate, it is essential to understand the behavior and patterns of churned users, 
predict potential churners using machine learning models, and tailor promotional strategies to retain at-risk customers.

The project will support retailer to understand churn users behaviors, predict churn customer and segment churn users to offer targeted promotions through answering **3 key questions**:
1. What are the patterns/behavior of churned users? What are your suggestions to the company to reduce churned users?
2. Build the Machine Learning model for predicting churned users (fine tuning)
3. Company would like to offer targeted promotions for churn user. Segment these churned users into groups based on the behaviors. What are differences among clusters?

## DETAIL
- **Dataset** includes a diverse range of information such as customer interactions, preferences, behaviors, etc.
  + _CustomerID: a unique identifier for each customer._
  + _Churn: indicates whether a customer has stopped using the service (1-churn, 0-not churn)._
  + _Tenure: the length of time (month) a customer has been with the company._
  + _PreferredLoginDevice: A device customers prefer for logging into the service (Mobile Phone, Computer)._
  + _CityTier: city 1, 2, 3_
  + _WarehouseToHome: the distance (km) between the warehouse and the customer’s home._
  + _PreferredPaymentMode: the payment method favored by customers (Debit Card, UPI, Cash on Delivery, E wallet, Credit Card)._
  + _Gender: Male & Female._
  + _HourSpendOnApp: the number of hours customers spend on the app._
  + _NumberOfDeviceRegistered: the number of devices a customer has registered with their account._
  + _PreferedOrderCat: the preferred category of products ordered by the customer (Laptop & Accessory, Mobile Phone, Fashion, Grocery, Others)._
  + _SatisfactionScore: a measure of customer satisfaction (score 1-5)._
  + _MaritalStatus: the marital status of the customer (Single, Divorced, Married)._
  + _NumberOfAddress: the number of addresses associated with a customer._
  + _Complain: records of customer complaints (1-complaint, 0-no complaint)._
  + _OrderAmountHikeFromLastYear: changes in order amounts compared to the previous year._
  + _CouponUsed: the number of coupons a customer used._
  + _OrderCount: the total number of orders placed by the customer._
  + _DaySinceLastOrder: the number of days since the last order._
  + _CashbackAmount: the amount of cashback a customer has received._
![image](https://github.com/user-attachments/assets/c01fd2d4-5a1c-4400-be54-16039b3f6644)

- **Process**
  + Use Pandas, Numpy, Matplotlib, Seaborn, Scipy and ScikitLearn to clean, analyze, visualize, gather insights and build models.
  - **Question 1**
    + Apply Random Forest model to select the 6 most important features. Gain insights through data visualization.
    + [Supervised learning] Feature transforming (encoding, normalization, skewness reduction, fixing imbalance data) and Hyperparameter tuning to choose the best hyperparameter for model.
    + [Unsupervised learning] Feature transforming (encoding, normalization, skewness reduction, fixing imbalance data, dimension reduction, elbow method, etc) and gain insights through data visualization.
  
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
