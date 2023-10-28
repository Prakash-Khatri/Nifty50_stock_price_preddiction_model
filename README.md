![MasterHead](https://cdn.dribbble.com/users/1330777/screenshots/15577460/media/63bebb993ca3416be861f0953182a9d6.gif)

# Introduction:
The Nifty 50, often simply referred to as the Nifty, is the flagship stock market index of the National Stock Exchange of India (NSE). It comprises the top 50 actively traded stocks from various sectors, representing a diversified and comprehensive reflection of the Indian equity market. Investors and analysts closely monitor the Nifty 50 to gauge the overall market sentiment, economic health, and investment opportunities in India.

---

## Aim of the project 🎯:
The aim of this project is to develop a robust linear regression model for predicting stock prices based on historical data. The primary focus will be on creating an accurate and efficient linear regression model that can analyze historical stock prices and relevant features to make reliable predictions about future stock values. Once the model is trained and validated, the objective is to save the linear regression model to a file, enabling seamless and rapid predictions for future stock prices. By achieving this goal, the project aims to provide investors and financial analysts with a valuable tool for making data-driven decisions in the stock market.

---

## Project Description 📃:
The "Linear Regression Model for Stock Price Predictions" project focuses on creating a predictive model using linear regression techniques to forecast stock prices. This project revolves around analyzing historical stock data, developing a linear regression model based on this data, and saving the trained model for future predictions. The goal is to provide accurate predictions for stock prices, aiding investors and traders in making informed decisions about buying or selling stocks.

#### Key Steps in the Project:
1. Data Collection:
  - Gather historical stock price data, including features like opening price, closing price, trading volume, and any other relevant metrics.

2. Data Preprocessing:
  - Clean and preprocess the collected data, handling missing values and outliers. Prepare the data in a format suitable for training a linear regression model, ensuring numerical features are normalized if needed.

3. Feature Selection:
  - Identify relevant features that influence stock prices. Common features include historical prices, trading volume, moving averages, and technical indicators. Select features that have significant correlations with stock prices.

4. Linear Regression Model:
  - Implement a linear regression model using libraries like scikit-learn in Python. Train the model on the preprocessed historical data, mapping features to stock prices using linear relationships.

5. Model Training and Evaluation:
  - Split the data into training and testing sets. Train the linear regression model using the training data and evaluate its performance on the test data. Utilize metrics like Mean Absolute Error (MAE) and Root Mean Square Error (RMSE) to assess the model's accuracy.

6. Saving the Model:
   - Once the linear regression model demonstrates satisfactory performance, save the trained model to a file using serialization techniques. Common formats include pickle files in Python or joblib files, preserving the model's state and parameters.

7. Real-time Predictions:
  - Implement a mechanism to load the saved model and use it for real-time predictions. Users can input relevant features (such as current trading volume and historical prices), and the model will output the predicted stock price.

---

# _Steps involved in process:_

## Data Scrapping ⛏️
1. Company Names:
  - Initially, the names of companies constituting the Nifty 50 index were manually downloaded from the official Nifty 50 website. This curated list served as the foundation for subsequent automated data extraction procedures.
  - After importing the dataset into a file, the project further processed the information by creating a list of shares from the file. To optimize search operations on the Yahoo Finance platform, ".NS" was appended to each share name in the list. This modified list was then used as input to send keys into the search bar, streamlining the automation process for retrieving specific share data.

![image](https://github.com/Prakash-Khatri/Nifty50_stock_price_preddiction_model/assets/133597202/eb766e5f-b8cd-40db-9193-9c3c1c2224c0)

2. Automated Data Retrieval from Yahoo Finance:
  - Selenium and WebDriver automation tools were employed to navigate the Yahoo Finance website. The automation script identified the search box, entered the names of individual companies obtained from the manually downloaded list, and executed a search operation. Upon accessing the designated share data pages, the process continued as follows.

3.  Accessing Historical Data:
  - Once on the specific share's data page, the automation script identified and interacted with the 'Historical Data' tab. This tab provided access to the historical performance metrics of the chosen share.
![image](https://github.com/Prakash-Khatri/Nifty50_stock_price_preddiction_model/assets/133597202/2559210c-cabe-4323-9a88-702dc0fc2e94)

4.  Selecting Time Span:
  - The automation tool interacted with the drop-down menu to select the desired time span, enabling customization of the data extraction process. A specific time frame, such as 5 years, was chosen to gather comprehensive historical data for analysis.
![image](https://github.com/Prakash-Khatri/Nifty50_stock_price_preddiction_model/assets/133597202/c280a8c9-d334-4b0c-a376-2884313df1d0)

5. Download of CSV Files:
  - Post selecting the appropriate time span, the automation tool located and activated the download button. This action initiated the download of a CSV (Comma-Separated Values) file containing the historical data of the particular share over the specified 5-year period.

#### _Following is the code for Data Scrapping:_
![image](https://github.com/Prakash-Khatri/Nifty50_stock_price_preddiction_model/assets/133597202/42df4986-7a5b-4efc-b8a9-adf966284cf3)

## Exploratory Data Analysis
- A list of strings was created to import files into a list. Then, the names of these files were used to add a column simultaneously, associating each file with a particular company name. Finally, the dataset was rearranged, likely to enhance the organization and readability of the collected information.
![image](https://github.com/Prakash-Khatri/Nifty50_stock_price_preddiction_model/assets/133597202/118ee2ad-579b-492a-8485-cf8b86606142)

## Outlier ANalysis
- In the context of Nifty 50 stock data analysis, the Interquartile Range (IQR) method was employed to identify outliers within the dataset. The process began by calculating the IQR, which is the range between the first quartile (Q1) and the third quartile (Q3) of the data.
![image](https://github.com/Prakash-Khatri/Nifty50_stock_price_preddiction_model/assets/133597202/484de351-ffd4-42f6-bfc6-3970f2839cf1)

## Feature Selection
- Selecting features on the basis of multicolinearity. Since the most of the data was correlated, I went with NPC technique.
![image](https://github.com/Prakash-Khatri/Nifty50_stock_price_preddiction_model/assets/133597202/daccb54f-e211-45e9-804e-99dd5a27ece9)

- PCA (Principal Component Analysis) techniques were applied to facilitate feature selection for a model. PCA is a dimensionality reduction method that identifies patterns and relationships within the dataset by transforming correlated variables into a set of linearly uncorrelated components, called principal components. By utilizing PCA, redundant or less informative features were identified and removed, streamlining the dataset. This process enhanced the model's efficiency and accuracy by focusing on the most relevant and significant features
![image](https://github.com/Prakash-Khatri/Nifty50_stock_price_preddiction_model/assets/133597202/45f43766-75a5-412c-97d1-a00d9d58fc41)
![image](https://github.com/Prakash-Khatri/Nifty50_stock_price_preddiction_model/assets/133597202/2affa1db-d9f0-4051-9516-ec01f7facf20)

## Model Building 📊:
1. One-hot encoding is utilized to convert categorical variable into a numerical format suitable for machine learning models.
![image](https://github.com/Prakash-Khatri/Nifty50_stock_price_preddiction_model/assets/133597202/8e0d2d0a-6af9-4d7f-8e4d-94a194a362b3)

2. Scaling in stocks data involves transforming numerical features to a standard scale, often between 0 and 1. This ensures uniformity, prevents skewed influence of variables, and enhances the accuracy of machine learning models by putting all features on an equal footing for analysis and prediction. 
![image](https://github.com/Prakash-Khatri/Nifty50_stock_price_preddiction_model/assets/133597202/b38d38ea-adec-49ea-93fa-b117baed5d3b)

3. In stock data analysis, the train-test split is a fundamental step where the dataset is divided into two subsets: the training set used to train the machine learning model and the test set used to evaluate the model's performance. This split ensures that the model is trained on historical data and tested on unseen data, providing a reliable measure of its effectiveness in predicting stock market behavior.
![image](https://github.com/Prakash-Khatri/Nifty50_stock_price_preddiction_model/assets/133597202/6d7b206d-e494-4af6-920f-137602838f6d)

4. Finally fitting the data to Linear Regression Model. Linear regression for stocks data involves utilizing a linear equation to model the relationship between one or more independent variables and a dependent variable. The objective is to find the best-fitting line that minimizes the difference between predicted and actual stock prices.
![image](https://github.com/Prakash-Khatri/Nifty50_stock_price_preddiction_model/assets/133597202/5367e11c-f4b6-40a6-8d8c-ea41fb51dca1)

5. Evaluation Metrices:
Here are the evaluation metrices to check the accuracy of the model
![image](https://github.com/Prakash-Khatri/Nifty50_stock_price_preddiction_model/assets/133597202/68f4be18-9999-48dc-89b1-65f2b680e3eb)

## Storing the Machine Learning Model
- The pickle library in Python is commonly used for serializing and deserializing data. When applied to saving stock data, it allows you to store complex data structures, such as dictionaries or lists containing stock information, into a binary file. This serialized data can be easily saved and loaded later, enabling efficient storage and retrieval of stock-related information within Python programs.This means you can save your trained ML model along with stock data in a file for future use. This approach ensures that your model and data are stored in a compact binary format, enabling easy retrieval and deployment when needed.
![image](https://github.com/Prakash-Khatri/Nifty50_stock_price_preddiction_model/assets/133597202/a3ea3144-843d-4531-bc4c-d640d06c37b0)

---

# Conclusion
represents a significant advancement in the realm of financial forecasting and decision-making. By leveraging sophisticated algorithms and historical stock data, these models can analyze complex patterns, identify trends, and make predictions about future market movements.

Such ML models not only provide valuable insights for investors and traders but also aid in risk management and strategic planning. They offer a data-driven approach to stock market analysis, enabling stakeholders to make informed decisions, optimize portfolios, and maximize returns on investments.

However, it's crucial to acknowledge that while ML models can offer powerful predictions, they are not foolproof. Market conditions are influenced by numerous unpredictable factors, and past performance is not always indicative of future results. Continuous monitoring, validation, and adaptation of these models are necessary to ensure their accuracy and relevance in dynamic and ever-changing financial markets. Integrating human expertise with machine learning capabilities can enhance the effectiveness of these models, providing a holistic approach to navigating the complexities of the stock market landscape.

---

# Learnings
1. Data Quality is Paramount:
The accuracy and reliability of the model heavily depend on the quality of the input data. Ensuring clean, accurate, and up-to-date data is crucial for meaningful predictions.

2. Feature Selection is Key:
Identifying the right features (indicators) from the stock data significantly impacts the model's performance. Effective feature selection involves domain knowledge and experimentation to choose the most relevant variables.

3. Data Preprocessing is Essential:
Data preprocessing steps like normalization, scaling, handling missing values, and outlier detection are essential to prepare the data for the model. Proper preprocessing enhances the model's ability to extract meaningful patterns.

4. Model Selection and Tuning:
Choosing an appropriate machine learning algorithm and fine-tuning its hyperparameters are critical steps. Iterative testing and validation help in identifying the most suitable algorithm and parameter settings for the specific dataset.

---

# Future Scope
1. Enhanced Predictive Accuracy:
Continued research and development can focus on improving the accuracy of predictions. Advanced algorithms, ensemble methods, and deep learning techniques can be explored to make more precise forecasts regarding stock movements.

2. Sentiment Analysis:
Integrating natural language processing (NLP) techniques for sentiment analysis from news articles, social media, and financial reports can provide additional context to stock predictions. Understanding market sentiment can significantly enhance the accuracy of predictions.

3. Real-time Analysis:
Developing real-time ML models that can process and analyze stock data instantaneously. This could be invaluable for high-frequency trading and real-time decision-making for investors and traders.

4. Anomaly Detection:
Machine learning algorithms can be used to detect anomalies in stock behavior. This can help in identifying market manipulations, abnormal trading patterns, or unexpected events that might affect stock prices.

5. Portfolio Optimization:
ML models can assist in optimizing investment portfolios. By considering multiple factors and constraints, these models can suggest the most balanced and profitable portfolio for investors.
