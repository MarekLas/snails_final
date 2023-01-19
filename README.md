<img src="https://github.com/MarekLas/snails_final/blob/master/Abalone_snails_SDA_Final_Project.png" align="center" width ="69%" /> <img src="https://github.com/MarekLas/snails_final/blob/master/abalone.jpg" align="left" width ="28%" />

## Dataset Relevant Information Paragraph

Predicting the age of abalone from physical measurements.  The age of
abalone is determined by cutting the shell through the cone, staining it,
and counting the number of rings through a microscope -- a boring and
time-consuming task.  Other measurements, which are easier to obtain, are
used to predict the age.  Further information, such as weather patterns
and location (hence food availability) may be required to solve the problem.

From the original data examples with missing values were removed (the
majority having the predicted value missing), and the ranges of the
continuous values have been scaled for use with an ANN (by dividing by 200).

Data comes from an original (non-machine-learning) study:

```latex
Warwick J Nash, Tracy L Sellers, Simon R Talbot, Andrew J Cawthorn and
Wes B Ford (1994) "The Population Biology of Abalone (_Haliotis_
species) in Tasmania. I. Blacklip Abalone (_H. rubra_) from the North
Coast and Islands of Bass Strait", Sea Fisheries Division, Technical
Report No. 48 (ISSN 1034-3288)
```

## Features

|Name		    |Data Type	|Meas.	|Description
|---------------|-----------|-------|-----------
|Sex		    |nominal	|		|M, F, and I (infant)
|Length		    |continuous	|mm	    |Longest shell measurement
|Diameter	    |continuous	|mm	    |perpendicular to length
|Height		    |continuous	|mm	    |with meat in shell
|Whole weight	|continuous	|grams	|whole abalone
|Shucked weight	|continuous	|grams	|weight of meat
|Viscera weight	|continuous	|grams	|gut weight (after bleeding)
|Shell weight	|continuous	|grams	|after being dried
|Rings		    |integer	|		|+1.5 gives the age in years

## First script with regression models and neural network without normalization
I decided to check how the final results look with different regression models and some basic neural networks.

Link to the script:
https://github.com/MarekLas/snails_final/blob/master/abalone_2023.ipynb

## Modules used (mostly) in the script

<img src="https://github.com/MarekLas/snails_final/blob/master/01_modules.png" align="center" width ="55%"/> 

## Data sample
We can see that the are som not welcome object data. So I should use one hot encoding soon.

<img src="https://github.com/MarekLas/snails_final/blob/master/02_dane.png" align="center" />

## Data information
Here we can check that the are some null values. I decided to delete them.

<img src="https://github.com/MarekLas/snails_final/blob/master/03_info.png" align="center" />

## Data describe
At first sight nothing terrible seems to be happening here.

<img src="https://github.com/MarekLas/snails_final/blob/master/04_describe.png" align="center" />

## One hot encoding 
Now it's time to do something with categorical data. 
This time I use pandas.get_dummies().
https://pandas.pydata.org/docs/reference/api/pandas.get_dummies.html

But first let's look at the sex column. It's seems to be very interesting, because there are 3 types of sex F, M and I.

<img src="https://github.com/MarekLas/snails_final/blob/master/05_countplot_sex.PNG" align="center" />

After doing get_dumies method the data table looks a little different.

<img src="https://github.com/MarekLas/snails_final/blob/master/05a_table_after_get_dummies.PNG" align="center" />

## Label data
Now let's look at the label data - rings column. Box-plot chart suggests that there are some outliers.

<img src="https://github.com/MarekLas/snails_final/blob/master/06_label_data.png" align="center" width ="50%"/>

## Size group
Thera are two group of data size group and weight group. At the beginning I was wondering to do some pseudo voulume value from length, height and diameter. But the results weren't satisfactory.

<img src="https://github.com/MarekLas/snails_final/blob/master/07_length_diameter_height.png" align="center" width ="55%"/> 

## Correlation matrix

<img src="https://github.com/MarekLas/snails_final/blob/master/correlation_matrix.JPG" align="center" />

## Outliers elimination example

<img src="https://github.com/MarekLas/snails_final/blob/master/height_age.png" align="center" width ="55%"/> 

<img src="https://github.com/MarekLas/snails_final/blob/master/hight_ouliers_v2.JPG" align="center" width ="47%"/> 

<img src="https://github.com/MarekLas/snails_final/blob/master/height_age_outliers.png" align="center" width ="70%"/> 

<img src="https://github.com/MarekLas/snails_final/blob/master/hight_ouliers_changed_v2.JPG" align="center" width ="47%"/>

## Regression example

<img src="https://github.com/MarekLas/snails_final/blob/master/linear_regression_v2.png" align="center" width ="70%" />

## First results

<img src="https://github.com/MarekLas/snails_final/blob/master/results.JPG" align="center" width ="100%"/>



![GitHub last commit](https://img.shields.io/github/last-commit/MarekLas/snails_final)
