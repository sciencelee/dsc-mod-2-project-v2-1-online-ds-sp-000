
# King County Housing Data Analysis

![seattle_pikes_place](https://github.com/sciencelee/dsc-mod-2-project-v2-1-online-ds-sp-000/blob/master/images/seattle-4748986_640.jpg)


## Background

Being able to understand the home characteristics that ultimately affect the sale price of a home in the Seattle area, can help us to:
* identify good values when purchasing homes
* maximize our profits by manipulating characteristics of the home
* avoid overspending on home purchases or unnecessary renovations


## Objectives
Use Linear Regression to model how a variety of home characteristics affect the sale price in King County, Washington.


## The Dataset

For this project, we used the King County House Sales dataset. The dataset can be found in the file `"kc_house_data.csv"`, in this repo. The description of the column names can be found in the `"column_names.md"` file in this repository. 


## Our Process

Data preprocessing:
* Checking for Null and placeholder values - replace as necessary
* Checking for outliers and limiting ranges/limits of variables
* Identifying continuous and categorical values

Single variable analysis
* Perform single variable regression model for every target variable
* Create relevant plots and visualizations for variables of interest 
* Test for single variable fits and r-squared values

Select our variables:
* Check collinearity of variables, and remove variables as necessary
* Transform and normalize data as needed
* One hot encode (create dummy variables) for categorical data
* Perform a forward-backward feature selection
* Make a final selection of features

Create our model:
* Create linear using Scikit Learn
* Calculate r-squared and look at model summary

Verify model:
Train test split
Overfitting measures such as k-fold validation
Model evalueation including r-squared and mean squared error (MSE)


## The Data
A good picture/overview of home prices in Seattle can be seen by looking at a series of maps made with Folium in this project.
The interactive maps are linked to the images and are available in [folium_maps folder](https://github.com/sciencelee/dsc-mod-2-project-v2-1-online-ds-sp-000/tree/master/folium_maps)

The most revealing maps for our model are below:

Map of all 21000+ homes with a hue of sale price.
![All Homes Price Colomap](https://github.com/sciencelee/dsc-mod-2-project-v2-1-online-ds-sp-000/blob/master/images/colormap_price.png)

Map of all 20 King County school districts with hue of mean home sale price
![School districts with mean price map](https://github.com/sciencelee/dsc-mod-2-project-v2-1-online-ds-sp-000/blob/master/images/school_dist_choropleth.png)

Map of all home sales with views.
![Home Views Colormap](https://github.com/sciencelee/dsc-mod-2-project-v2-1-online-ds-sp-000/blob/master/images/view_colormap.png)

Apart from all of the other data, the time you sell is relevant to the sell price
![Sales by month](https://github.com/sciencelee/dsc-mod-2-project-v2-1-online-ds-sp-000/blob/master/images/Mean_sale_month.png)

The data was imported and preprocessed in pandas.  All maps were shown with Folium.  Colormaps were built with branca.  Choropleth maps use geojson data files from King County website.

We filtered our data to remove the following homes
*  homes with sale price less than $120,000 or more than $2,000,000.
*  homes with fewer than 2 bedrooms or more than 5.
*  homes with assessed condition of poor or very poor

We calculated and added the following columns:
* distance to downtown
* distance to nearest waterfront
* school district
* rating of school district by niche.com
* number of homes with view in neighborhood/proximity to home
* has basement

Using single variable regressions, we determined that no indiviudal variable is sufficient to describe the price, but several independent variables stood out with r-squared over 0.4.  The single variable regression results for the top r-squared values is below.  We will do a multivariate linear regression model.

![Single Variable Regression](https://github.com/sciencelee/dsc-mod-2-project-v2-1-online-ds-sp-000/blob/master/images/single_var_regression.png)

## Variable Selection
We created a correlation matrix with all of our potential variables and filtered out relationships greater than 70% correlated for our final model.  The most highly correlated variables in our final model are grade and sqft_living, which are seemingly unrelated in describing the home, but large homes clearly are graded better by the assessor.

![Correlation Matrix](https://github.com/sciencelee/dsc-mod-2-project-v2-1-online-ds-sp-000/blob/master/images/single_var_regression.png)

We chose not to transform or normalize our data to make it easier to interpret the results of the regression. When doing this, we were able to improve the results of the model and this may be a next step to refine our model.

Categorical data chosen for inclusion was the view (0 to 4).  We also experimented with using school district, but 20 districts complicated the model and led us to use the school district score instead (taken from https://www.niche.com/k12/search/best-school-districts/c/king-county-wa/). Note that the scores were from 2020 and our housing data is 2015.

Using a forward-backward feature selection, we arrived at the following final variables for our model.
![Feature Selection](https://github.com/sciencelee/dsc-mod-2-project-v2-1-online-ds-sp-000/blob/master/images/selected_variables.png)

## Our Model
We used the following variabls for our model:
* grade (from county assessor)
* sqft_living
* school_score (latlong to find school_district and converted to score)
* dist_downtown (point to point distance to Pike's Place)
* view (categorical 1 through 4)

We used sklearn.linear_model to create our regression and sklearn.model_selection for our cross validation and kfold analysis.
The r_squared from cross validation was 0.70.

When using the kfold method and a train test split of 80/20, we found very little difference in the MSE.

`
Train Mean Squarred Error: 23795705325.594067
Test Mean Squarred Error: 24272450149.82784
RMSE: 154300.0 155800.0
`

## Model Inferences
Coefficients from our model were:
`
[('sqft_living', 140.94600028379642),
 ('grade', 78037.90833279114),
 ('downtown_dist', -8845.882074783778),
 ('school_score', 38116.39475887594),
 ('view_4.0', 344191.5901786746),
 ('view_3.0', 170133.09222368588),
 ('view_2.0', 93477.37469634558),
 ('view_1.0', 99472.8084683562)]
`

We expect that for each additional sqft of house, we will get about $141 dollars.
An assesed grade from improvements just one grade higher is expected to add $78,000
For every increase in school score (B+ to A-), expect an increase of $38,000.
Any view is worth $90,0000 to $100,000.  Elite views can be worth $344,000 toward the home value.

## Recommendations
If you are looking to buy an investiment home in King County:
* Look for homes with upgrade potential in areas with exceptional schools, great views, and accessibility to downtown.
* Markets in desirable areas can likely absorb price increases and maximize profit
* Avoid expensive improvements in areas that do not have the identified characteristics
* Be flexible when you buy.  Avoid peak.

If you are looking to sell an investment home in King County:
* Do improvements aimed at increase of the assessed grade
* Add sqft, beds, baths, finish basement if possible
* Reserve high end investments for areas where market can handle high end homes
* Sell in the spring/summer.  List in March/April

see Mod2Presentation.pdf file for more data presentation.


## Further Study
A predictive model might be helpful by using other tools.  
Different variable selection or filtering of data might improve the model.
Looking at individual areas of King County might prove more stable for the model (perhaps try Mercer Island homes only to test)


