# What drives the price of a car ?
![CARS](images/kurt.jpeg)

**Himanshu Yadav**


## **OVERVIEW**

In this assignment we will explore a dataset from kaggle. The original dataset contained information on 3 million used cars. The provided dataset contains information on 426K cars to ensure speed of processing.  Your goal is to understand what factors make a car more or less expensive.  As a result of our analysis, we will provide clear recommendations to your client -- a used car dealership -- as to what consumers value in a used car.

### CRISP-DM Framework

![CRISP](images/crisp.png)
To frame the task, throughout our practical applications we will refer back to a standard process in industry for data projects called CRISP-DM. This process provides a framework for working through a data problem.

### Business Understanding to Data Problem Definition
**Business Problem:** Identifying key drivers for used car prices to guide inventory decisions for a used car dealership.

**Data Problem Definition:** The task is to develop a predictive model that can accurately determine the price of used cars based on their attributes. This involves analyzing historical data to identify which features (like make, model, year, mileage, condition) most significantly impact the selling price. The model needs to be robust, interpretable, and capable of handling large-scale data to provide actionable insights for strategic decision-making.

### Data Understanding

**Available features**
- id: A unique identifier for the car.
- region: The region in which the car is being sold.
- price: The selling price of the car (our target variable).
- year: The year the car was manufactured.
- manufacturer: The make of the car.
- model: The model of the car.
- condition: The condition of the car (like new, used, etc.).
- cylinders: The number of cylinders in the car’s engine.
- fuel: The type of fuel the car uses.
- odometer: The mileage of the car.
- title_status: The legal status of the car (clean, salvage, etc.).
- transmission: The type of transmission (automatic, manual).
- VIN: The Vehicle Identification Number.
- drive: The type of drive (FWD, RWD, AWD).
- size: The size category of the car.
- type: The body type of the car.
- paint_color: The color of the car.
- state: The state in which the car is being sold.

### **After studying the data it was concluded that it would be best to create a model per vehicle type as prices significantly vary based on type of vehicle and they cannot be judged on same scale.**

 ### Data Preparation
 Next step is to prepare the data for modelling. Following actions were taken during data preparation steps.  
- Drop unwanted columns
   - Dropped **Size and Cylendar** due to large numhber of missing values
   - Dropped **VIN** and **ID** as they should not have any impact on prices.
   - Dropped **Region** and **Model** to reduce number of features.
   - **Year** was converted to **car_age** and year was dropped
   - dropped **paint** as too many missing values color should not have too much impact on price. 
- handle junk data
  - Only considered vehicles made after 1999 . Vehicles older than 2000 can be considered antique. Such vehicles are priced very differently and should be considered through separate model .
  - Only considering vehicles with price range between 100 and 500000 to get rid of outliers.
  - To get rid of junk data only rows with **Odometer** value between **0 to 300000**
- handle missing values.
   - **Unknown** was added to rest of missing values
- Encoding Categorical Variables - 
  Many machine learning models require all input data to be numeric. Encoding categorical variables is essential to convert them into a format that can be provided to machine learning algorithms.

**Method: One-Hot Encoding**
One-Hot Encoding creates a binary column for each category and is suitable for nominal categorical data where no ordinal relationship exists.
- Data scaling - 
  Data Normalization or Scaling
Scaling numerical data, especially when the data spans several orders of magnitude, can improve the performance of many algorithms.

Scaling Methods:
Standard Scaling (Z-score scaling): This scales the features based on the standard deviation and mean. It’s effective when data follows a normal 
 
