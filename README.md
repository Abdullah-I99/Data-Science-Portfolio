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
we began by importing the CSV dataset into a pandas DataFrame using pd.read_csv() function (which can be seen in figure 1). I also ran initial exploration of the data to understand structure and content which can be seen in figure 1, figure 2 and figure 3. 

| ![Figure 1](images/Figure%201.png) | ![Figure 2](images/Figure%202.png) |
|:---------------------------------:|:---------------------------------:|
| **Figure 1**   | **Figure 2**  |

![Figure3](images/Figure%203.png)
**Figure 3**

### Transform
The data was then cleansed by reducing the number of columns needed (reducing from 53 to 12. This was to remove irrelevant columns like customer info etc. This was done by defining the columns we wanted to keep and then using a DataFrame along with copy() to create a new DataFrame. 

After this correct data types were applied to date columns (to allow accurate calculation of certain columns) like shipping and order date column. These were converted to datetime format, using the pd.to_datetime() function. This can be seen in figure 4


![Figure4](images/Figure%204.png)
**Figure 4**

2 new columns were created in the dataframe to show number of days from order to ship and days delayed. The previous step was very important (changing to datetime data type) to create the order to ship days column. The code is very self explanotary of how these both column were created and calculate, please see figure 5 as an example. The 2 date columns were then dropped using function df.drop() as these were no longer needed. See figure 6. 

<p align="center">
  <img src="images/Figure%205.png" width="400"><br>
  <strong>Figure 5</strong>
</p>

<p align="center">
  <img src="images/Figure%206.png" width="400"><br>
  <strong>Figure 6</strong>
</p>

### Load
Finally the cleansed data was saved as a cleansed final dataset (to be used later for analysis) locally. This was using the function df.to_csv() function. See figure 7 for the code. 

<p align="center">
  <img src="images/Figure%207.png" width="400"><br>
  <strong>Figure 7</strong>
</p>

## Data Visualisation
After cleaning the data some Exploratory data Analysis was carried using python’s Matplotlib and seaborn libraries. Initially importing the relevant libraries needed for analysis (see figure 8) and then loaded the cleansed data using pd.read_csv() function (see figure 1 for example). 

<p align="center">
  <img src="images/Figure%208.png" width="400"><br>
  <strong>Figure 8</strong>
</p>

We then did a basic target distribution using a bar chart to visualise the distribution of late vs on-time deliveries. The analysis showded a clear difference between on-time and late deliveries with late delieviries being much higher. This was created using the seaborn function sns.countplot which can be seen in figure 9. Figure 10 shows the output. 

<p align="center">
  <img src="images/Figure%209.png" width="400"><br>
  <strong>Figure 9</strong>
</p>

<p align="center">
  <img src="images/Figure%2010.png" width="400"><br>
  <strong>Figure 10</strong>
</p>

For further exploration of late delivery risk a boxplot was then created to showcase comparison of late delivery again shipping delays. This showed a clear distribution that orders classified as Late showed higher shipping delay values in comparison to on-time deliveries (as can be seen in figure 12). A logistics regression model was created to show proof of this, which we will showcase a little later. This was created using seaborn function sns.boxplot (as can be seen in figure 11

<p align="center">
  <img src="images/Figure%2011.png" width="400"><br>
  <strong>Figure 11</strong>
</p>

<p align="center">
  <img src="images/Figure%2012.png" width="400"><br>
  <strong>Figure 12</strong>
</p>

Finally for the final part of the EDA another bar chart was created to showcase comparison of shipping modes vs shipping delay days. This showed a clear indication of some modes exhibiting lower delay profile, namely same day delivery showing lower shipping delays (as seen in figure 14). The bar chart was created using panda/matplotlib function .plot(kind=”bar”) after creating an average column for shipping delay days (see figure 13)

<p align="center">
  <img src="images/Figure%2013.png" width="400"><br>
  <strong>Figure 13</strong>
</p>

<p align="center">
  <img src="images/Figure%2014.png" width="400"><br>
  <strong>Figure 14</strong>
</p>

## Data Analytics
Once exploring the data further a logistics regression model was created to predict late delivery risk using the static dataset. Once the data was loaded certain object based column either needed to be dropped or turned in numeric features (as logistics regression cannot work directly with strings). Columns shipping mode was converted into binary format using one hot encoding, this creates a new column for each category where 1 = exists and 0 = does not exist (GeeksforGeeks, 2025), this can be seen in figure 15. 

<p align="center">
  <img src="images/Figure%2015.png" width="400"><br>
  <strong>Figure 15</strong>
</p>

Next the data was split into feature and target variables. The target variable is what we want to predict so late delivery risk in this instance, whereas the features are variable we want to use to make that prediction (in this instance certain object based column were dropped along with late delivery risk column like delivery status as it directly reveals the answer as seen in figure 16).

<p align="center">
  <img src="images/Figure%2016.png" width="400"><br>
  <strong>Figure 16</strong>
</p>

The data was then split into train/test set using and 80:20 ratio. This was done using the function in SKlearn called train_test_split() (see figure 17), a method used to split the data (GeeksforGeeks, 2025). 

The numerical features were then standardised using standardscaler (an SKlearn Function). According to GeeksforGeeks, this transformation adjusts the data so that each feature has a mean of 0 and a standard deviation of 1. In simple terms, this puts all numerical values so they were all on a similar range to stop one feature (for example sales, which has much larger values) from dominating the model. The way this is performed can be seen in figure 18

<p align="center">
  <img src="images/Figure%2017.png" width="400"><br>
  <strong>Figure 17</strong>
</p>

<p align="center">
  <img src="images/Figure%2018.png" width="400"><br>
  <strong>Figure 18</strong>
</p>

The model was then trained using the logisticRegression() SKlearn function (see figure 19) and then evaluated for accuracy and made predictions. The model showed an accuracy of 0.974 (s0 97.4% accuracy), whilst correctly identifying all late deliveries and only misclassifying a few on-time deliveries as late (showing a recall off 0.94, meaning only 6% were misclassified) – this makes the model very useful for predicting delivery risk in logistics. The results can be seen in figure 20. Figure 21 shows the matrix of the results, this was created using sns.heatmap a seaborn function. 

<p align="center">
  <img src="images/Figure%2019.png" width="400"><br>
  <strong>Figure 19</strong>
</p>

<p align="center">
  <img src="images/Figure%2020.png" alt="Figure 20" height="200">
  <strong>Figure 20</strong>
  <img src="images/Figure%2021.png" alt="Figure 21" height="200">
  <strong>Figure 21</strong>
</p>

Finally feature importance was assessed to see what features lead to further delays in late deliveries. It was found that features like shipping delays had a high positive coefficient which means this increase late delivery risk, whereas there was negative coefficients for shipping mode same day which meant it directly relates to reducing delays. Overall these insights directly align with the EDA findings. See figure 22 and 23 for clear view of this. 

<p align="center">
  <img src="images/Figure%2022.png" alt="Figure 20" height="200">
  <strong>Figure 22</strong>
  <img src="images/Figure%2023.png" alt="Figure 21" height="200">
  <strong>Figure 23</strong>
</p>
