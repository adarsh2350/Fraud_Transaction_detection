# Fraud_Transaction_detection


Note - The code Presented is not showing the best results, it is just showing the approach of how to tackle this problem. Results can be better by more analysing it and with better threshold values and hyperparameters.





  


Demonstrate using code and explain how did would you identify the potential fraudulent activities in financial transactions.

Codes - https://colab.research.google.com/drive/1qafmRB_prrfqQSSrh6c08GA3jU37fOPe?usp=sharing


The given dataset encompasses features such as AccountID, Merchant, Location, TransactionType, Timestamp, Amount, etc. with the objective of identifying potential fraudulent transactions.

Primarily, this problem aligns with Unsupervised Learning.

A plausible approach involves utilising Exploratory Data Analysis (EDA) to label the data, differentiating between fraudulent and normal transactions. Subsequently, this could be transformed into a straightforward Supervised Classification problem for model development.

Let's envisage real-life scenarios indicative of potential fraudulent transactions:

Unusually High Transaction Amounts: Transactions with exceptionally high amounts might indicate potential fraud. Identifying outliers within the 'Amount' feature using Z-scores (threshold set at 3) can help flag these transactions as potentially fraudulent.

Right-Skewed Transaction Distributions: Instances where the mean transaction amount significantly surpasses the median could signal potential fraud. Monitoring AccountID-Merchant pairs with right-skewed transaction distributions (mean > median) and setting an upper cap factor based on this skewness could pinpoint transactions deviating from the norm within this pair.

Sudden Transaction Surges in Specific Locations: Abrupt increases in transaction volume within specific locations could signify fraudulent activities. Similar to the second point, monitoring and capping transaction amounts within these locations could assist in detecting potential fraudulent transactions.

Additionally, sudden increases in total transaction amounts within short time intervals or a surge in small transactions might also indicate potential fraud. These anomalies could be tracked and flagged as potentially fraudulent.

Furthermore, there exist several other indicators of potential fraud, such as spikes in transaction numbers over short intervals or pattern analyses between various entities or individuals.

It's important to note that the thresholds and methodologies presented here are illustrative; determining accurate values would require a detailed market analysis for optimal detection of fraudulent transactions.








Why did you choose the given approach over other methods? What other method did you evaluate ?


Initially, the problem was approached as an unsupervised learning task due to its complex nature and the abundance of categorical features. However, the dataset's high dimensionality stemming from these categorical attributes posed a challenge. Moreover, the disproportionately low occurrence of fraudulent transactions compared to the overall volume hindered effective separation and identification of these instances. Even attempts at dimensionality reduction techniques such as PCA did not yield significant improvements in detecting fraudulent transactions. This limitation, common in unsupervised learning, led to a shift in strategy towards Exploratory Data Analysis (EDA) to convert the problem into a supervised learning scenario.

Through EDA, deeper insights into the dataset were gained, allowing for a better understanding of the data's patterns and characteristics. This shift to supervised learning became imperative to leverage labeled data or discover indicative patterns effectively. By uncovering and utilizing these patterns, it became possible to transition the problem into a supervised learning framework, empowering the model with necessary labels and insights crucial for accurate identification and classification of fraudulent transactions. This strategic shift offered a more directed and labeled approach, addressing the challenges posed by unsupervised learning's limitations in handling categorical features and imbalanced class distributions.





What feature did you consider to find potential fraudulent activities? How did you perform feature engineering to improve the model ?


In the process of feature engineering, careful consideration was given to the dataset's attributes to pinpoint features instrumental in identifying potential fraudulent transactions. Among the various attributes available—Timestamp, TransactionID, AccountID, Amount, Merchant, TransactionType, and Location—specific focus was directed towards AccountID, Amount, Merchant, TransactionType, and Location for their inherent relevance in detecting fraud. Analyzing the dataset revealed that the transactions spanned from January 1st, commencing at 8 am, to May 31st, concluding at 23:59. Consequently, key features for detecting fraud were identified as AccountID, Amount, Merchant, TransactionType, and Location.

To further refine the feature set and facilitate robust analysis, the Timestamp was dissected to extract significant temporal details, including date and month. While extracting these temporal elements, the year was deemed uniform across all transactions and thus excluded from consideration. Additionally, to streamline and optimise the feature set, the precise time component was omitted to mitigate dimensionality concerns. Despite its potential value, retaining time data could notably escalate the number of features. Therefore, for the current analysis, emphasis was placed solely on date and month attributes. Furthermore, to standardise the dataset and ensure uniformity in the model's evaluation, one-hot encoding was employed for categorical features, converting them into numerical representations. Additionally, Min-Max scaling was applied to the numerical features to normalise their values within a standardised range. Notably, TransactionID was disregarded in this analysis, being a categorical feature bearing distinct values for each transaction and contributing insignificantly to the fraud detection analysis.








Demonstrate using code and explain how would you predict the spend for all Transaction Types for the month of June.


This is a problem of Time Series Analysis where we predict the future depending on the past patterns. The best way to handle this problem will be by using LSTM RNN model, which is best suited for handling sequential data. 

Not demonstrated in the given code. Due to time constraints. And earlier I never worked on a Time Series analysis based project that’s why it’s more time consuming for now.








How would you test the effectiveness of the model to unseen data ? 

Similar to the methodology applied in this problem, the approach involves passing unseen data through an Exploratory Data Analysis (EDA) process to initially gauge its potential classification as fraudulent or non-fraudulent. This preliminary assessment serves as a basis for comparison with the outcomes generated by our model.

This process closely resembles an ensemble technique wherein multiple individual models or units are created. Each unit—either the EDA process or the subsequent model—contributes its classification output for comparison and evaluation. By leveraging this ensemble-like strategy, the initial EDA assessment and the subsequent model prediction can be juxtaposed, allowing for a comprehensive evaluation and refinement of the overall fraud detection system. This comparison helps validate the model's predictions and potentially improves its accuracy by incorporating insights gleaned from the EDA stage.




Improvements -

During the Exploratory Data Analysis (EDA) phase, we meticulously explored various real-life scenarios to effectively label the data, distinguishing potential fraud instances from non-fraudulent ones. These scenarios provided diverse angles for data classification based on different contextual situations, enriching our understanding and refining the labeling process.

Addressing the issue of an imbalanced dataset, an essential step involved oversampling to rectify the skewed distribution. Though time constraints led to a basic balancing approach—equalizing the number of '0s' and '1s'—a more optimal strategy entails a multi-step technique. This comprises initial oversampling to augment the minority class to a higher proportion, followed by under sampling to moderate the vast discrepancy between the classes.

Moreover, in the model fitting process, incorporating K-Fold cross-validation emerged as pivotal. This technique, facilitating multiple training and validation iterations, ensures a robust model by averting overfitting concerns and fortifying its generalization capabilities.

Although the initial approach directly involved fitting and predicting test and train data on the model, an improved process mandates hyperparameter tuning. Fine-tuning these parameters optimizes the model's performance, ensuring it operates at its best efficiency level. The incorporation of hyperparameter tuning enhances the model's ability to capture intricate patterns within the data, bolstering its predictive accuracy.
