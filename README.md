# Flight-price-prediction

Created a tool that estimates Flight Prices to help users look for best prices when booking flight tickets.
Engineered features from the Departure Time, Date of Journey, to quantify the data and make it more understandable.
Optimized multiple Regression models using GridsearchCV to reach the best model.
Built a client facing API using flask

# Problem Statement

Flight ticket prices can be something hard to guess, today we might see a price, check out the price of the same flight tomorrow, it will be a different story. We might have often heard travelers saying that flight ticket prices are so unpredictable. As data scientists, we are gonna prove that given the right data anything can be predicted. Here you will be provided with prices of flight tickets for various airlines between the months of March and June of 2019 and between various cities. Size of training set: 10683 records

Size of test set: 2671 records

FEATURES: Airline: The name of the airline.

Date_of_Journey: The date of the journey

Source: The source from which the service begins.

Destination: The destination where the service ends.

Route: The route taken by the flight to reach the destination.

Dep_Time: The time when the journey starts from the source.

Arrival_Time: Time of arrival at the destination.

Duration: Total duration of the flight.

Total_Stops: Total stops between the source and destination.

Additional_Info: Additional information about the flight

Price: The price of the ticket


# Cleaning the Data

I needed to clean it up so that it was usable for our model. I made the following changes and created the following variables:

Made Columns for Day and Month out of Date of Journey
Calculated the total flight duration
Removed the null values
Removed the outliers

# Model Building

First, I transformed the categorical variables into dummy variables. I also split the data into train and tests sets with a test size of 20%.

I tried forteen different models and evaluated them using Root Mean Squared Error. I chose RMSE because it is relatively easy to interpret and outliers aren’t particularly bad in for this type of model.

Different models I tried:

LinearRegression :  2875.378820303944
ElasticNet : 3520.7455916655294
Lasso :  2877.470296686765
Ridge :  2878.8315343543945
KNeighborsRegressor :  3037.051412069077
DecisionTreeRegressor :  2517.5464343595067
RandomForestRegressor :  2133.0061133326553
SVR :  4643.370521026606
AdaBoostRegressor :  3560.9647073251294
GradientBoostingRegressor :  2106.297313980016
ExtraTreeRegressor :  2509.9116852422344
HuberRegressor :  3158.177092463484
XGBRegressor :  1818.4249893522529
BayesianRidge :  2875.1706769559164

XGBRegressor, RandomForestRegressor and GradientBoostingRegressor gave the lowest RMSE so I chose these model and performed hyper parameter tuning

# Model Accuracy

Mean Absolute Error: 1159.2971469235836
Mean Squared Error: 4157632.95820125
Root Mean Squared Error: 2039.027454008712

![image](https://user-images.githubusercontent.com/84179246/132945652-2c5bc33b-dbc7-470a-aa0d-fc286516df10.png)

# Productionization

In this step, I built a flask API endpoint that was hosted on a local webserver. The API endpoint takes in a request with a list of values from a flight and returns an estimated price.


