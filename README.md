### FAOStat-Dataset-Time-Series
# Forecasting Food Production: Analyzing Trends, Challenges, and Opportunities in East Africa

![yfood_outlook_june23_pr_banner](https://github.com/Muramati/FAOStat-Dataset-Time-Series/assets/70520367/30563c28-b0dd-4a1f-ad03-4e45385f8d1b)


## Business Understanding 

### Overview

Kenya's food production plays a crucial role in ensuring food security for its population. The country's agricultural sector employs a significant portion of the population and contributes to the national economy. Kenya is known for its diverse agricultural activities, including crop cultivation, livestock rearing, and fisheries.

In recent years, Kenya has made strides to improve food production through various initiatives, including promoting modern farming techniques, investing in irrigation infrastructure, and supporting small-scale farmers. These efforts have led to increased agricultural productivity and improved crop yields.

However, despite these advancements, food production in Kenya still faces challenges that affect its sufficiency. Climate change, unpredictable weather patterns, and recurrent droughts pose significant risks to agricultural productivity. Additionally, limited access to affordable inputs, inadequate infrastructure, and post-harvest losses contribute to the food production challenges.

As a result, Kenya occasionally experiences food shortages and relies on imports to meet the country's food demands. Despite efforts to enhance domestic food production, there is a need for further investment in sustainable agriculture, resilient farming practices, and improved market access to ensure long-term food sufficiency in Kenya.

### Objectives

The objectives of the prediction model for food production in Kenya are as follows:

1. Forecasting Food Production: The primary objective of the model is to accurately predict food production levels in Kenya. By analyzing historical data, current conditions, and relevant variables, the model aims to provide forecasts that reflect the expected output of crops, livestock, and other food sources.

2. Assessing Food Sufficiency: The model seeks to determine whether the projected food production will be sufficient to meet the needs of the population. It aims to assess the adequacy of food supply in order to identify potential shortfalls or surpluses.

3. Informing Decision-Making: The model aims to provide valuable insights to policymakers, government agencies, and agricultural stakeholders. By offering reliable predictions, the model can inform decision-making processes related to resource allocation, import/export planning, and interventions to ensure food security.

4. Optimizing Resource Allocation: The model aims to optimize the allocation of resources by identifying areas of potential food shortages or surpluses. This can help in directing resources, such as irrigation, fertilizers, and agricultural investments, to areas that require them the most.

5. Promoting Sustainable Farming Practices: By considering various factors that impact food production, such as climate conditions and agricultural practices, the model can promote sustainable farming techniques. It can provide recommendations for resilient and environmentally-friendly practices that enhance productivity while minimizing negative impacts.

6. Enhancing Food Security: Ultimately, the objective of the prediction model is to contribute to improving food security in Kenya. By accurately forecasting food production and assessing sufficiency, the model aims to support proactive measures that ensure a consistent and adequate food supply for the growing population.

### Data Understanding

The data from this project comes from the FAOStas site.
[Food Balances](https://www.fao.org/faostat/en/#data/SCL)

The CSV has the following columns:

1. Area Code (M49): This column represents the standard area codes used by the United Nations for statistical purposes.

2. Area: This column contains the country name or area name.

3. Element Code: The element code represents the entities or categories based on which the data is collected. 

4. Element: This column provides a description or name for the entities or categories represented by the element code.

5. Item Code (CPC): The item code refers to the  code assigned to a specific product or item. 

6. Item: This column contains the product or item classification name.

7. Year: This column represents the year when the data was collected or recorded.

8. Unit:  specifies the measurement unit used for the corresponding item (e.g., kilograms, tonnes, liters).

9. Value: This column provides the numerical value associated with a specific item, measured in the units specified in the "Unit" column. It represents the quantity or magnitude of the item for a given year and area.

10. Flag: describes how the values in the dataset were acquired by the FAO (Food and Agriculture Organization of the United Nations).

12. Flag Description: This column provides additional information or descriptions related to the flags used in the dataset. The "E" represents estimated values, the "X"  indicates figures from international organizations, and the "I" flag denotes imputed values.
### Explanatory Data Analysis
##### Top 10 Items produced in Eastern Africa
![1](https://github.com/Muramati/FAOStat-Dataset-Time-Series/assets/99483846/7c324e49-febb-44e6-8f47-fcb008560297)
$ inference $
- After analyzing a visualization of the top 10 items produced by East African countries, we can observe distinct production patterns. Cassava and products emerges as the dominant product, closely followed by Bananas. Conversely, potatoes and associated products exhibit the lowest production levels among the selected items.
### Bivariate Analysis 
![import](https://github.com/Muramati/FAOStat-Dataset-Time-Series/assets/99483846/5cdfb8dd-0b22-4458-ae20-ad23503c4f9a)
$ inference $   
- The bar graph represents the comparison between the import quantity and export quantity in the dataset. The x-axis shows the two elements: "Import Quantity" and "Export Quantity." The y-axis represents the corresponding quantities.

- The bars in the graph depict the quantities, with the cyan color indicating the import quantity and the magenta color indicating the export quantity.

- This graph provides a visual representation of the difference between the import and export quantities, allowing for easy comparison between the two elements.
### Multivariate Analysis
![line pl](https://github.com/Muramati/FAOStat-Dataset-Time-Series/assets/99483846/9b7136a5-289a-42e5-991b-daf69090359a)
$ inference $
-  Tanzania's Growth: Tanzania shows a steady in domestic supply quantity from 2010 to 2020. The domestic supply quantity levels are observed in 2017 and 2018.

- Uganda's Growth: Uganda exhibits a fluctuating pattern in domestic supply quantity over the years. The highest domestic supply quantity levels are observed in 2012 and 2019.

- Kenya's Growth: Kenya demonstrates a generally increasing trend in domestic supply quantity with a significant rise in supply from 2014 to 2015. The highest supply levels are observed in 2015 and 2019.

- Rwanda's Growth: Rwanda experiences a notable increase in domestic supply quantity from 2010 to 2013, followed by a relatively small decline in supply. The highest supply levels are observed in 2015 and 2017.

Overall, the plots provide an overview of the growth patterns in domestic supply quantity for these countries over the specified time period. They highlight the variations and trends in supply levels, allowing for a comparison between the different countries.
##### Preprocessing kenyan dataset for  modeling  

![LINES](https://github.com/Muramati/FAOStat-Dataset-Time-Series/assets/99483846/a149e6be-0b2b-4340-9d4b-072a4284d44d)
$ inference $
- There is an upward trend over the years across all the elements except for exports which seems to be stagnant
##### correlation matrix kenya

![Corr](https://github.com/Muramati/FAOStat-Dataset-Time-Series/assets/99483846/df7050f0-2136-4df5-b135-78b641290021)
The elements are highly correlated because the affect each other
#### Modelling 
### Baseline model
Baseline models serve as a reference point or a benchmark against which the performance of more complex or sophisticated models can be compared. They provide a simple and straightforward approach to modeling a problem, often with minimal assumptions or complexity.
Overall, baseline models offer a simple starting point and serve as a valuable reference for understanding and assessing the performance of more complex models. They provide a baseline against which advancements in modeling techniques and feature engineering can be measured, guiding the iterative process of model development and improvement.
$ inference $
from statsmodels.tsa.ar_model import AutoReg

#iterate over each column in the DataFrame
for col in multivariate_kenya_data_diff.columns:

    # select the column as the endogenous variable
    endog = train_datakenya[col]

    # fit an AR model of order 1 to the time series
    model = AutoReg(endog,1)
    fitted_model = model.fit()

    # make predictions for the test set
    predictions = fitted_model.predict(start=len(train_datakenya), end=len(train_datakenya) + len(test_datakenya) - 1)

    # evaluate the model's performance on the test set
    mse = ((predictions - test_datakenya[col]) ** 2).mean()
    rmse = np.sqrt(mse)
    rmse_dict['AR'].append(rmse)
    print("RMSE for {}: {}".format(col, rmse))


### SARIMA MODEL 
The SARIMA (Seasonal AutoRegressive Integrated Moving Average) model is a popular time series forecasting method that extends the capabilities of the ARIMA model to handle seasonal patterns. It is particularly useful when dealing with data that exhibits both trend and seasonal components.

The SARIMA model incorporates three main components: autoregression (AR), differencing (I), and moving average (MA). Additionally, it includes a seasonal component represented by an additional set of AR, I, and MA terms.

components of the SARIMA model:
Autoregression (AR): The AR component models the relationship between the current observation and a number of lagged observations. 
Differencing (I): The differencing component accounts for removing trend and seasonality from the time series data. It involves taking the difference between consecutive observations to make the series stationary
Moving Average (MA): The MA component models the dependency between the current observation and a linear combination of past forecast errors. It captures the effect of previous forecast errors on the current value
Seasonal Autoregression (SAR): The seasonal autoregression component accounts for the relationship between the current observation and its lagged seasonal observations. It captures the influence of the seasonal pattern on the data. The "P" parameter determines the number of lagged seasonal observations considered.

Seasonal Differencing (SI): The seasonal differencing component accounts for removing the seasonal pattern from the data. It involves taking the difference between an observation and its corresponding observation from the previous season. The "D" parameter represents the order of seasonal differencing.


### Deployment 
Streamlit is an open-source Python library that enables the rapid development and deployment of interactive web applications for data science and machine learning projects. It simplifies the process of creating and sharing data-focused applications by providing an intuitive and straightforward interface.
key points about Streamlit and its capabilities: 
$ inference $
- Easy-to-use
- Rapid prototyping
- Data-focused capabilities
  

![forecast3](https://github.com/Muramati/FAOStat-Dataset-Time-Series/assets/99483846/aeafcaa0-d5ef-45ad-92c0-1f267fb8a13f)
