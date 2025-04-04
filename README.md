![GitHub last commit](https://img.shields.io/github/last-commit/MarekLas/snails_final)
<!--
<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/Abalone_snails_SDA_Final_Project.png" align="center" width ="69%" /> <img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/abalone.jpg" align="left" width ="28%" />
-->
<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/abalone_v2.jpg" align="center" width ="100%" />

# Description

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

# Part I - Regression models

## First script with regression models and neural network without normalization
I decided to check how the final results will look with different regression models and some basic neural networks.

## <b>Link to the first script:</b>

### <b>https://github.com/MarekLas/snails_final/blob/master/scripts/abalone_2023_v2.ipynb</b>

## Modules used (mostly) in the script

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/01_modules_v2.png" align="center" width ="56%"/> 

## Data sample
We can see that the are some not welcome object data. So I should use one hot encoding soon.

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/02_dane.png" align="center" />

## Data information
Here we can check that there are some null values. I decided to delete them.

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/03_info.png" align="center" width ="41%"/>

## Data describe
At first sight nothing terrible seems to be happening here.

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/04_describe.png" align="center" />

## One hot encoding 
Now it's time to do something with categorical data. 
This time I use pandas.get_dummies().

https://pandas.pydata.org/docs/reference/api/pandas.get_dummies.html

But first let's look at the sex column. It's seems to be very interesting, because there are 3 types of sex: F, M and I.

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/05_countplot_sex.PNG" align="center" />

After doing get_dumies method the data table looks a little different.

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/05a_table_after_get_dummies.png" align="center" />

## Label data
Now let's look at the label data - rings column. Box-plot chart suggests that there are some outliers.

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/06_label_data.png" align="center" width ="55%"/>

## Size group
There are two group of data - size group and weight group. At the beginning I was wondering to do some pseudo voulume value from length, height and diameter.There are some diferences in thevalues scales. But the results weren't satisfactory.

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/07_length_diameter_height.png" align="center" width ="61%"/> 

Below we can see that height data have a different scale than the others.

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/25_volume.png" align="center" width ="50%"/> 

## The weight group

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/08_weights.png" align="center" width ="60%"/> 

## Dependences
We can discover here some dependences. Especially visible in the size group.

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/09_pairplot.png" align="center" width ="70%"/> 

## Correlation matrix
The heatmap is showing also that there are some nice dependences with the weight group.

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/10_heatmap.png" align="center" width ="80%"/>

## Outliers
The next step is to reduce the impact of outliers. Because the data isn't large I decided to do this using scaterr plot charts. The height data are great example how the charts changed after reducing some of the outliers.

* Raw height data

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/21_height_01.png" align="center" width ="30%"/> 

* Height data after outliers elimination

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/22_height_02.png" align="center" width ="30%"/> 

## Spliting data
First step is to split data into features and labels. Then I splited data into train and test data. I used also StandardScaler() to scale splited data.

https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.StandardScaler.html

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/26_spliting_and_scaling.png" align="center" width ="70%" />

## Different regression models
I decided to check what will be the results using different regression algorithms.To pick optimal hiperparmeters I used the GridSearchCV() method from scikit-learn library.

https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.GridSearchCV.html

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/27_models.png" align="center" width ="90%" />

GridSearchCV code example for the Lasso Regression:

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/28_hiperparameters.png" align="center" width ="60%" />

## Coefficient of determination and mean absolute errors results table and charts

* Table

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/29_r2_score_mae_table.PNG" align="center" width ="40%" />

* Barplot charts

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/30_barplot_r2_score.png" align="center" width ="50%" />

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/31_barplot_mae.png" align="center" width ="50%" />

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/32_barplot_r2_mae.png" align="center" width ="50%" />

# Part II - Neural network
Basic neural network using TesorFlow library. I decided to check results using different neural network hiperparameters. In this step the data isn't normalized.

## First model
As an example how the models were built I put here the first one. The model with two layers, 100 epochs and SGD() optimizer.

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/33_first_tensor_flow_model.png" align="center" width ="80%" />

## Plot history (also known as a loss curve or a training curve)
The chart that shows how the model learned during the epochs.

* SGD() optimizer with 100 epochs and 2 layers

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/37_loss_curve_SGD_l2_e100.png" align="center" width ="40%" />

* SGD() optimizer with 100 epochs and 3 layers

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/38_loss_curve_SGD_l3_e100.png" align="center" width ="40%" />

* Adam() optimizer with 100 epochs and 3 layers

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/39_loss_curve_Adam_l3_e100.png" align="center" width ="40%" />

## Coefficient of determination and mean absolute errors results table and charts after testing different neural networks

* Table

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/34_tf_r2_score_mae_table.PNG" align="center" width ="40%" />

* Barplot charts

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/35_barplot_r2_score.png" align="center" width ="40%" />

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/36_barplot_mae.png" align="center" width ="40%" />

# Part III - Neural network with normalize data
I was courious if normalizing the data will improve the results. So I decided to do some new script with the same data but instead of scaling them I used column transformer to normalize the data. It was also good possibility to try a different method for one hot encoding. To normalize the data I used MinMaxScaler()

https://scikit-learn.org/stable/modules/generated/sklearn.compose.make_column_transformer.html

https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.MinMaxScaler.html

## <b>Link to the second script:</b>

### <b>https://github.com/MarekLas/snails_final/blob/master/scripts/abalone_tensor_flow.ipynb</b>

## Creating column with transformer

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/40_column_transformer.png" align="center" width ="70%" />

## Transform training and test data using column transformer

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/41_normal_ohe.png" align="center" width ="70%" />

## Neural network model
I decided to use Adam optimizer, 3 layers and 1000 epochs.

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/42_model_Adam_l3_e1000.png" align="center" width ="70%" />

## Results

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/43_tensor_flow_mse_r2_score.png" align="center" width ="70%" />

## Plot history

<img src="https://github.com/MarekLas/snails_final/blob/master/readme_files/44_tf_loss_curve.png" align="center" width ="40%" />

# Summary
After analizing the results the first conclusion is that there is no significatn improvement when I used neural network with almost default settings. Probably if I spent more time selecting appropriate different hiperparameters the result would be better.  So I think that with this issue using neural network is something like shooting the bazooka at the mosquitoes.


![GitHub last commit](https://img.shields.io/github/last-commit/MarekLas/snails_final)
