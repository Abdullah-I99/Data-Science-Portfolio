# Predicting Late Deliveries using Data Analytics

## Executive Summary:
This project explores supply chain logistics data from DataCo Smart Supply chain dataset to identify key reasons for late deliveries and higher logistics costs. Late deliveries raise an growing problem for logistics companies as they negatively impact customer satisfaction, increase cost and  put more strain on services.

Using historical order data an end to end data science project was undertaken better understand the reasoning for late deliveries and ways we can tackle to improve this. This was done through general EDA and creating a predictive model via logistics regression (which helps understand key factors for late deliveries). EDA was used to asses cost across shipping modes and regions and logistics regression was used to predict likelihood of late deliveries. 

Initially the data was cleansed to calculate key metrics which the data was missing like order to ship days and shipping delay days, these helped give clarity of some key insights like avg delay days across shipping mode (with 2nd class being most delayed). Using the cleaned data exploratory data analytics (EDA) was performed to understand how the data is distributed. This showed a clear correlation of shipping delays having a great impact on late delivery.

A logistics regression model was then created to predict whether late deliveries are based on certain engineered factor. The model resonated the EDA findings in which shipping delay contributed highly to late deliveries, whereas certain shipping modes (like same day) and order to ship days contributed negatively – meaning better chance of order being shipped on time. 

Overall this project showed there are easy fixes by reducing shipping delays and promotion of certain shipping modes can greatly reduce delay of orders.

## Data Infrastructure and Tools
The dataset used for this project was a publicly available dataset called DataCos Smart Supply chain dataset from Kaggle (shashwatwork, 2025). This was downloaded as a csv file due to the ease of storage locally and loading into python. 

Python was used for data processing and analytics as it provides flexibility for ETL and Modelling. Pandas library was used for data engineering like ingestion, cleaning and transformations, whilst Numpy was used for model preparation. Jupyter notebook (within VScode) was also used as it makes it easier to test idea  in small steps (through iterative development) and show clear workings for each section.

Scikit-learn was used to run a logistics regression model to predict late delivery risk, one of the main libraries used for regression models due to its robust implementation of machine learning algorithms. 

All data visualisations were performed using matplotlib, to show clear charts and communicate insight to non-technical stakeholders.  These were chose for their flexibility and easy integration with the python data stack.

There are limitations to using the above models and datasets as it only operates currently on a static model. this provides a strong foundation that could be extended to automated ETL pipelines using live data. 

## Data Engineering
This area focused heavily on transforming raw supply chain data into data ready to be used for exploration, by removing irrelevant columns, looking at data structures and removing null values. We use the ETL process which is highlighted below. 
### Extract
I began by importing the CSV dataset into a pandas DataFrame using pd.read_csv() function (which can be seen in figure 1). I also ran initial exploration of the data to understand structure and content which can be seen in figure 1, figure 2 and figure 3. 
