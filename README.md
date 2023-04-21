# SC1015_MiniProject
Code repository for B126 Team 5

# Our Motivation

Nanyang Technological University is an academic institution located in the western region of Singapore, secluded from the rest of Singapore. Due to long commuting hours, it was decided to buy a second-hand car for a more cost-effective approach. Thus, this has led to our question, “Which variables affect the selling price of a Honda Vezel 1.5A X the most, to obtain the most value for our money?”

We used a dataset from Kaggle "https://www.kaggle.com/datasets/jiantay33/singapore-used-car"

# Setting the Stage

## Cleaning our Dataset:

First, we have to clean our dataset. We have done that by first removing duplicate values and also removing N.A. values. This is because we do not want duplicate and N.A. values to give us the wrong result. 

Next, since all the categories in this dataset are labelled as "object", we want to change it to a suitable label such that we can plot them on graphs. In this case, we have converted Price, Mileage, COE, Manufactured, No. of Owners, Depreciation, and Power into float64. We then create Age from 2021 (the year this dataset was released) minus Manufactured, which gives us the Age of the car. 

Then, we remove unusable car brands like "3", "5" and "S-Class" etc. as we do not need them in our dataset.

## Exploratory Data Analysis:

First, we plot all the car types against price in a box plot. We determine which car types are the most suitable for us. We have shortlisted SUVs, Mid-Sized Sedans and Hatchback cars. This is because we do not have the budget to purchase high-end cars like Sports cars. Also, we only have a Class 3 License and therefore cannot purchase buses and vans.

Next, we isolate the specific car brand we want. We have chosen Honda as it has the most number of entries in our histogram plot. Now we have shortlisted our car to - a Honda, which is either an SUV, Mid-Sized Sedan or Hatchback.  

Plotting a histogram of the models of cars that Honda offers, we took into consideration that Honda Vezel 1.5AX has the most number of entries amongst all the Honda cars in our cleaned dataset. Honda Vezel 1.5AX is also popular in Singapore due to its reliability, fuel efficiency and sustainability. Therefore we have chosen Honda Vezel 1.5A X to be researched to determine which variable affects its selling price the most.

This allows us to remove other variables associated with car model, such as the variable Power, since it will be the same across all the Honda Vezel 1.5A X.

# Our Analysis

## Heatmap and Correlation value:

First, we plot a joint heatmap to get the correlation value for all the independent variables we have used, namely: Age, Mileage, COE, Depreciation, No. of Owners, OMV and Dereg Value, against our dependent variable Price of the car. After observation, we have chosen to remove No. of Owners as it shows the lowest correlation among all the variables. 

We are thus left with Age, Mileage, COE, Depreciation, OMV and Dereg Value as our independent variables (total = 6 independent + 1 dependent).

## Multi-Variate Linear Regression:

We used multiple linear regression to train a prediction model.

Response Variable : **Price**     
Predictor Feature : **Age, Mileage, COE, Depreciation, OMV and Dereg Value**   

Regression Model : Total = $a_1$ $\times$ Age + $a_2$ $\times$ Mileage + $a_3$ $\times$ COE + $a_4$ $\times$ Depreciation + $a_5$ $\times$ OMV + $a_6$ $\times$ Dereg Value + $b$

## Hypothesis Testing:

We conducted an F-test for our data to determine the significance of our 5 variables in predicting price. The test was conducted at a significance level, α, of 0.05 to determine if each variable is statistically significant in the regression.

We use F-values together with their corresponding P-Values to determine the significance of the overall results. P-Value is defined as the smallest possible value of α required to reject 𝐻0.

The P-Value is the probability of observing a value of F that equals or exceeds the F-Value. This is the probability of obtaining a sample from the population that is more extreme than the ones observed in the data, assuming 𝐻0 is true. P – Value = P (F ≥ F – Value)

The high p-Value for Mileage indicates the large extent of errors that the inclusion of mileage introduces to the regression model.
Hence, Mileage is rejected from the regression and we conclude that this variable is statistically insignificant in predicting Price.

We then refined our multi-variate linear regression model, excluding Mileage from the list of predictors.

Response Variable : **Price**     
Predictor Feature : **Age, COE, Depreciation, OMV and Dereg Value**   

Regression Model : Total = $a_1$ $\times$ Age + $a_2$ $\times$ COE + $a_3$ $\times$ Depreciation + $a_4$ $\times$ OMV + $a_5$ $\times$ Dereg Value + $b$

After rejecting Mileage and removing it from the predictors, the R^2 value of the test dataset model improved, from 0.83328 to 0.93556 respectively. As such, we can conclude that the model improved after rejecting Mileage as a predictor.

# Conclusion

We created an algorithm using our linear regression equation coefficients to estimate the potential value of each Honda Vezel in our dataset. 
We subtracted the listed price from the predicted price to get the net difference in price. If the result is positive, the value of the car is worth more than its listed price and hence it is a good deal. We can input a budget of $60,000, and our model will return the car that has the most bang for our buck.
Within the dataset, car 19 has the largest positive value differential to its price. We will actually be getting a significant bargain, almost 4200 based on the variables we analysed in the linear regression model. \
Therefore, we have concluded that car 19 is the best value car for us to buy using our linear regression model. 

Our model is limited in the way that is that it cannot predict the price other types of cars well as they have different specifications. To fit this model to other cars, we can train the model using the data of that model.


