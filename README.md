
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


## The Results
An good picture/overview of home prices in Seattle can be seen by looking at a series of maps made with Folium in this project.
The interactive maps are linked to the images and are available in ![folium_maps folder](https://github.com/sciencelee/dsc-mod-2-project-v2-1-online-ds-sp-000/tree/master/folium_maps)
![price_colormap](https://github.com/sciencelee/dsc-mod-2-project-v2-1-online-ds-sp-000/blob/master/images/colormap_price.png)


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
