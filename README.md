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

Now we need to obtain species occurrence records. This used to be the main challenge in biogeography. Natural historians, such as Charles Darwin and Alexander von Humboldt, traveled around the globe for years on rustic sail ships collecting animal and plant specimens to understand the natural world. Today, we stand on the shoulders of giants. Getting data is fast and easy thanks to two organizations:

* The Global Biodiversity Information Facility (GBIF): An international network and research infrastructure aimed at providing anyone, anywhere, open access to data about life on Earth. We will use their data in this project.

* rOpenSci: A non-profit initiative that develops open-source tools for academic datasets. Their package rgbif will help us access the species data.

