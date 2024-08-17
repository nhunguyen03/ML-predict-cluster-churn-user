## OVERVIEW
Churn is a critical issue for any retailer, as retaining existing customers is often more cost-effective than acquiring new ones. 
To effectively reduce the churn rate, it is essential to understand the behavior and patterns of churned users, 
predict potential churners using machine learning models, and tailor promotional strategies to retain at-risk customers.

The project will support retailer to understand churn users behaviors, predict churn customer and segment churn users to offer targeted promotions through answering **3 key questions**:
1. What are the patterns/behavior of churned users? What are your suggestions to the company to reduce churned users?
2. Build the Machine Learning model for predicting churned users (fine tuning)
3. Company would like to offer targeted promotions for churn user. Segment these churned users into groups based on the behaviors. What are differences among clusters?

## DETAIL
- ### **Dataset** includes a diverse range of information such as customer interactions, preferences, behaviors, etc.
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

- ### **Question 1**
  + Apply Random Forest model to select the 6 most important features (high-related to target column Churn).
  + Gain insights through data visualization.
    ![image](https://github.com/user-attachments/assets/e499f8fc-1127-41be-a3b5-7ec59ff2972e)
    ![image](https://github.com/user-attachments/assets/cc46db5c-a743-4806-ae4d-12dad8b31dd9)
    
- ### **Question 2: [Supervised learning] Predict churn customers with 91,25% accuracy**
  + Feature transforming (encoding, normalization, fixing imbalance data)
    + Encode: convert categorical variables to dummy variables and drop first columns to **advoid multicollinearity**.
    + Normalization: using **MinMaxScaler** to scale data to a fixed range [0, 1]. Prefer when algorithms that assume feature scales are important, such as neural networks or algorithms using distance metrics.
    + Fixing imbalance data: by **oversampling SMOTE** to increases the size of the minority class in train datasets.
      ![image](https://github.com/user-attachments/assets/5c827a59-6c7e-4a16-9054-290ee0abef69)
      ![image](https://github.com/user-attachments/assets/814153ff-ea0a-49cc-a3eb-2e3b27404b96)

  + Apply 3 classification models: KNN, LogisticRegression, RandomForest. Using balanced accuracy score to choose the best model => Random Forest
  + Tune 5 hyperparameters of Random Forest model by using GridSearchCV and RandomizedSearchCV:
    + n_estimators, max_depth, min_samples_split, min_samples_leaf, bootstrap
  => The result is that the balances accuracy score increases from 0.89 to 0.9125
 
- ### **Question 3: [Unsupervised learning] Cluster churn customers & Offer targeted promotions**
  + Feature transforming (encoding, normalization, dimension reduction, elbow method, etc)
    + Encode: convert categorical variables to dummy variables and drop first columns to **advoid multicollinearity**.
    + Normalization: using **MinMaxScaler** to scale data to a fixed range [0, 1]. Prefer when algorithms that assume feature scales are important, such as neural networks or algorithms using distance metrics.
    + Dimension reduction **PCA**: select 10 principal components contributing over 90% meaning, reduce complexity of dataset
    + **Elbow method**: Because we used KMeans model to cluster churn users, we need to choose the number of clusters through elbow method. From this chart below, we choose k=4 because "Điểm khuỷ tay là điểm mà ở đó tốc độ suy giảm của hàm biến dạng sẽ thay đổi nhiều nhất. Tức là kể từ sau vị trí này thì gia tăng thêm số lượng cụm cũng không giúp hàm biến dạng giảm đáng kể"
      ![image](https://github.com/user-attachments/assets/66c2e37c-cb75-4d51-8f9c-648b72c28319)
      https://phamdinhkhanh.github.io/deepai-book/ch_ml/KMeans.html
      
  + Gain insights through data visualization.
  ![image](https://github.com/user-attachments/assets/d2a7415c-4547-4fc0-80fe-2bc91b1099b3)

  + **Strategy**
    + Cluster 0: handle complaints well and quickly. Send email to apologize and express commitment to resolving complaints immeadiately. Because they have orders recently, they are responsive to retention efforts 
    + Cluster 1: provide continuosly promotions, coupons, cashback intensitive, etc to retain them. They have recent orders, so they are easily reponsive to retention efforts 
    + Cluster 2: send personalized email-marketing to inform limited-time offers, exclusive offers for only returning customers, etc. Suggest products based on their previous purchase history. The ultimate goal is to encourage them to return.
    + Cluster 3: send an email with a sincere apology for the negative experience they had. Emphasize that you value their feedback. Assure that the problems have been addressed and improved. Then, suggest products based on their previous purchase history.
    They do not concern about promotions, they value product quality, service, etc more and they have no orders recently so it is challenge to make them responsive to retention efforts.
    The thing we can do is quality commitment, improvement.
