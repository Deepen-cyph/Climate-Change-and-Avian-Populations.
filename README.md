# Climate-Change-and-Avian-Populations.

## Introduction
Climate change is having profound effects on ecosystems worldwide, and birds are among the most affected groups of organisms. As temperatures rise, weather patterns shift, and habitats alter, avian populations are experiencing significant changes in their behavior, distribution, and survival rates. This project explores the various impacts of climate change on bird species, including changes in migration patterns, breeding cycles, and habitat availability. Understanding these impacts is crucial for developing effective conservation strategies to protect avian biodiversity in a rapidly changing world.

## Data Overview
We have pre-processed climate data and converted it into a SpatialPixelDataFrame. This data frame contains:

The decade of observation
* Spatial coordinates (x, y)
* Six selected climatic variables:
* Minimum temperature
* Maximum temperature
* Rainfall
* Wind speed
* Snow lying
* Air frost

## Visualization

An excellent first step in any analysis is visualizing the data. Visualizing the data ensures that the data import worked correctly and helps us develop intuition about the patterns in our dataset. Since we are dealing with spatial data, creating maps is a natural approach.

We will start by creating two maps: one representing the climatic conditions in 1970 and another for 2010. Given the various climatic variables available, we will initially focus on the minimum temperature.

![image](https://github.com/user-attachments/assets/fc6ab65e-3d90-4ede-805d-4694a988f244)

![image](https://github.com/user-attachments/assets/2e0985a3-517b-4b57-afde-f0c49404c2fd)

## Accessing Species Occurrence Data

Obtaining species occurrence records, once a formidable challenge in biogeography, is now streamlined thanks to modern tools and resources. Historically, natural historians like Charles Darwin and Alexander von Humboldt spent years collecting specimens across the globe. Today, accessing such data is remarkably efficient, thanks to the following organizations:

* The Global Biodiversity Information Facility (GBIF): This international network provides open access to data about life on Earth, allowing us to retrieve species occurrence records for our project.

* rOpenSci: This non-profit initiative offers open-source tools for academic datasets. The rgbif package from rOpenSci will be instrumental in accessing and managing species data.



![image](https://github.com/user-attachments/assets/b05cb7f3-8fba-4632-91ce-a8be1390dbfc)

## Cleaning and Filtering Species Data

GBIF and rOpenSci have streamlined the process of obtaining species occurrence records, saving us from extensive fieldwork. However, to ensure the data's accuracy and relevance, we must carefully clean and filter it. Large-scale datasets can have inconsistencies, so we'll use specific criteria to refine our records.

Data Cleaning Criteria
* Issues: Exclude records with any reported issues or doubts about the observation's accuracy.
* License: Use only records that are licensed under Creative Commons to ensure proper usage rights.
* Date: Filter records to include only those from 1965 to 2015, aligning with our climate dataset's timeframe.



![image](https://github.com/user-attachments/assets/0420b8d6-ca68-416f-a2ea-431345caf9b4)

## Aligning Bird Observations with Climate Data

After cleaning the data, we face the challenge of matching each bird observation with the climatic conditions at its location and time. Given that our climate data spans multiple decades, this requires a method to accurately associate each observation with the corresponding climate raster cell.

To achieve this, we'll use a powerful technique: nesting the data in a list column. This approach allows us to:

* Retain the original grouping columns in the data frame.
* Add a list column containing aggregated data for each group.
List columns can hold various types of variables, such as vectors, data frames, and complex objects. For example, the climate data we imported was nested by decade and includes a list column named rasters, which contains a RasterStack object for each decade.

Using this technique, we can accurately align each bird observation with the appropriate climatic conditions.



![image](https://github.com/user-attachments/assets/877c9af3-d0e7-4a59-91c4-c4219eee716f)


## Building Models with caret
We are now ready to train our model using the glmnet package, which fits a generalized linear model (GLM) with elastic net regularization. This method allows us to perform logistic regression with regularization to improve model performance.

## Hyperparameter Tuning
Our algorithm involves several hyperparameters—variables that influence the learning process of the machine learning model. These parameters affect model performance and often interact with one another, making it challenging to determine the optimal settings beforehand.

To identify the best hyperparameters, we will:

* Define a Tuning Grid: Create a grid of possible values for each hyperparameter. This grid specifies different scenarios to be tested.
* Use Cross-Validation: Employ cross-validation to evaluate the performance of various hyperparameter combinations. This process helps us find the most effective settings for building a predictive model.
The caret package simplifies this process by automating the grid search and cross-validation, making it easier to select the optimal hyperparameters for our model.



![image](https://github.com/user-attachments/assets/e18807b2-94e2-4e53-bb3f-a1e5910d366d)



## Visualizing Predictions – The Power of Maps

While we have our predictions, presenting them as a table of numbers makes it challenging to grasp the insights and convey them effectively to stakeholders like politicians, the general public, or local decision-makers.

To make the data more comprehensible and impactful, we need to visualize our predictions. Visual representations, especially maps, can uncover patterns and trends that are not immediately apparent in raw data. Maps are particularly powerful as they can effectively communicate the spatial and temporal aspects of climate change.

Let’s create a map that showcases our predictions of climate change in the UK from 1965 to 2015. This visualization will help us better understand the patterns and effectively share our findings.


![image](https://github.com/user-attachments/assets/070a0fe9-e93d-4486-98b3-256ed6db5798)










