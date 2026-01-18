# Predicting Late Deliveries using Data Analytics

## Executive Summary:
This project explores supply chain logistics data from DataCo Smart Supply chain dataset to identify key reasons for late deliveries and higher logistics costs. Using historical order data an end to end data science project was undertaken. The results of this will provide insights that can help optimise delivery planning and improve overall supply chain performance. EDA was used to asses cost across shipping modes and regions and logistics regression was used to predict likelihood of late deliveries. 

## Data Infrastructure and Tools
The dataset used for this project was a publicly available dataset called DataCos Smart Supply chain dataset from Kaggle (shashwatwork, 2025). This was downloaded as a csv file due to the ease of storage locally and loading into python. 

Python was used for data processing and analytics as it provides flexibility for ETL and Modelling. Pandas library was used for data engineering like ingestion, cleaning and transformations, whilst Numpy was used for model preparation. Jupyter notebook (within VScode) was also used as it makes it easier to test idea  in small steps (through iterative development) and show clear workings for each section.

Scikit-learn was used to run a logistics regression model to predict late delivery risk, one of the main libraries used for regression models due to its robust implementation of machine learning algorithms. 

All data visualisations were performed using matplotlib, to show clear charts and communicate insight to non-technical stakeholders.  These were chose for their flexibility and easy integration with the python data stack.

There are limitations to using the above models and datasets as it only operates currently on a static model. this provides a strong foundation that could be extended to automated ETL pipelines using live data. 
