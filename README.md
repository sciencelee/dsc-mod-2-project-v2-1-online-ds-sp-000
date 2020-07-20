
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

Using single variable regressions, we determined that no indiviudal variable is sufficient to describe the price, but several independent variables stood out with r-squared over 0.4.  The single variable regression results for the top r-squared values is below.
![Single Variable Regression](https://github.com/sciencelee/dsc-mod-2-project-v2-1-online-ds-sp-000/blob/master/images/single_var_regression.png)


## Submitting your Project

 You’re almost done! In order to submit your project for review, include the following links to your work in the corresponding fields on the right-hand side of Learn.

 1. **GitHub Repo:** Now that you’ve completed your project in Jupyter Notebooks, push your work to GitHub and paste that link to the right. (If you need help doing so, review the resources [here](https://docs.google.com/spreadsheets/d/1CNGDhjcQZDRx2sWByd2v-mgUOjy13Cd_hQYVXPuzEDE/edit#gid=0).)
_Reminder: Make sure to also add and commit a pdf of your non-technical presentation to the repository with a file name of presentation.pdf._
2. **Blog Post:** Include a link to your blog post.
3. **Record Walkthrough:** Include a link to your video walkthrough.

 Hit "I'm done" to wrap it up. You will receive an email in order to schedule your review with your instructor.
 
 
## Grading Rubric
Online students can find a PDF of the grading rubric for the project [here](https://github.com/learn-co-curriculum/dsc-mod-2-project-v2-1/blob/master/mod2_project_rubric.pdf). On-campus students may have different review processes, please speak with your instructor.


## Summary

The end of module projects and project reviews are a critical part of the program. They give you a chance to both bring together all the skills you've learned into realistic projects and to practice key "business judgement" and communication skills that you otherwise might not get as much practice with.
