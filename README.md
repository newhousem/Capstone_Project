# Mandates and COVID19 
## Capstone Project
-------
## Purpose
Covid-19 has impacted the world for over a year.
States have set different mandates around masks, restaurants, and gatherings in an attempt to mitigate the effects of the virus.
Have these mandates been effective?
What mandates were the most critical?
This project aims to create a model to understand the impact of the mandates on Covid cases.
This will help us understand if mandates are affective and how governments should use them in the future. 

## Data Used
The data used in this project was aggregated from multiple sources
- Data on COVID-19 cases by state and county along with the population of each county was found on USAfacts.org
https://usafacts.org/visualizations/coronavirus-covid-19-spread-map/
- Data on restaurant mandates, mask mandates, and gathering ban mandates were found on Data.gov
https://catalog.data.gov/dataset/u-s-state-and-territorial-orders-closing-and-reopening-restaurants-issued-from-march-11-20-f454b
https://catalog.data.gov/dataset/u-s-state-and-territorial-gathering-bans-march-11-december-31-2020-by-county-by-day-79295
https://catalog.data.gov/dataset/u-s-state-and-territorial-public-mask-mandates-from-april-10-2020-through-january-10-2021--e0ce3

## Data Manipulation
- The data was organized by state and county. 
- The mandates for mask usage, gatherings, gatherings with social distancing, and restaurants were correlated with each county by the date they were made effective in that county.
- Cases in each county were recorded with the corresponding date.
- An extra column was engineered to create Cases/Population for each county.
- Model was built to predict Cases/Population given the effective mandates in each county.

## Modeling Process
I built a gradient boosting regression model for Colorado and Florida
- Florida had an extra category for restaurant orders - ‘Authorized to fully open’
Due to this category the Florida model performed best 
  - Model error rates,
     - Mean Absolute Error: 0.011297040577091784
    - Mean Squared Error: 0.0003035919001125868
    - Root Mean Squared Error: 0.017423888776980492
    - Cases/Population average: 0.02791

- Colorado model, Colorado counties were more likely to put in a mandate and keep it for a long time
    - Model error rates,
        - Mean Absolute Error: 0.008024926274175495
        - Mean Squared Error: 0.0003489350913987028
        - Root Mean Squared Error: 0.01867980437260259
        - Cases/Population average: 0.01687

## Feature Importance
Florida Feature Importance
![alt text](Images/Florida%20Feature%20Importance.png)

Colorado Feature Importance
![alt text](Images/Colorado%20Feature%20Importance.png)

Features with the most variations proved to be the most important for the model, like restaurant orders in Florida. 

## Colorado Mandates Explored
![alt text](Images/Colorado%20Gatherings%20Orders.png)
![alt text](Images/Colorado%20Mask%20Mandate.png)
![alt text](Images/Colorado%20Restaurant%20Orders.png)
![alt text](Images/Colorado%20with%20SD%20orders.png)

## Florida Mandates Explored
![alt text](Images/Florida%20Gatherings%20Orders.png)
![alt text](Images/Florida%20Mask%20Mandate.png)
![alt text](Images/Florida%20Restaurant%20Orders.png)
![alt text](Images/Florida%20with%20SD%20orders.png)

Florida did not implement as many mandates as Colorado. Florida's case rate also looks to steadily rise more than Colorado's case rate. Both states were affected by the dramatic increase in cases in the US in winter 2020-2021. 

## Restaurant Mandates by the Numbers
Florida restaurant orders and the average rate of cases:

- Authorized to fully reopen: 0.046655
- Curbside/delivery only: 0.000488
- Open with limitations: 0.015066
- NA: 0.066253

Colorado restaurant orders and the average rate of cases:

- Curbside/delivery only: 0.001484
- No restriction found: 0.000029
- Open with limitations: 0.015408
- NA: 0.058282

It is interesting to observe the similar case rate when both states were 'Open with limitations' and the increased case rate when Florida was 'Authorised to fully reopen'. The 'NA' category refers to a similar time (winter 2020-2021) where both state's cases increased, yet Colorado's increased at a lower rate. 

## Conclusions
- The implementation of mandates may have affected case rate
    - Florida average case rate = 0.02791
    - Colorado average case rate = 0.01687
- Florida did not implement mask mandates or mandates for gathering with social distancing
- The model used Florida’s implementations of restaurant orders to better predict case outcome due to its variation
- Colorado had more consistent limitations across restaurant orders so it wasn’t as important for the Colorado model
- The average case rate when Florida restaurants were authorized to open: 0.046655
  - At the end of 2020 and beginning of 2021 case rate climbed to 0.066253
    - Comparatively, Colorado’s case rate average climbed to 0.058282 over that time
- It is clear that Florida’s cases continuously climbed, where Colorado’s cases stayed more consistent and only increased dramatically during the winter of 2020-2021 when cases increased dramatically across the country
- In the US, where travel between states is frequent, isolating states and the impact of their individual mandates is difficult. 
- However, with the data in two states that implemented mandates very differently, Florida and Colorado, it is clear that mandates may have helped mitigate the impact of the virus.
- From the model, we can see that the restaurant orders in Florida had an impact on the case predictions made by the model.  
- Since Florida’s case rates were higher on average, this indicates that not implementing restaurant restrictions may have a negative impact on case rate. 
- Mandates are important, and governments should continue to implement them based on current risks with the current COVID19 pandemic and should use them for pandemics in the future.

## Next Steps
- Analysis across all 50 states and considering federal mandates may help understand the impact of mandates more. As well as analysis of other countries and their mandates. 
- Due to the 14 day incubation period for COVID19 symptoms to develop, it may be helpful to offset cases by two weeks compared to mandate implementation.

