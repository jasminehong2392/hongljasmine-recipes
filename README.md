# COOKIN CALORIES
# Recipes

by Jasmine (jah041@ucsd.edu) & Shekar


---

## Introduction

For our analysis, we chose to explore what types of recipes tend to have the most recipes and predict the amount of calories in a given recipe. 
Our analysis is helpful for readers who are looking for a recipe that fits their dietary goals. Our analysis is a great tool for readers who are looking for people looking to gain weight in the form of lean muscle mass or energy. Calories are units of energy that every individual needs for their body to function. 

The two csv datasets we are working with are Raw Recipes and Raw Interactions. Raw recipes contains recipes and Raw_interactions contains the reviews and ratings submitted for the recipes in RAW_recipes. Both of the recipes are from Food.com.Food.com is a digital brand and media platform that features a large collection of recipes that are submitted, rated, and reviewed by foodies including home cooks, celebrity chefs, and shows. These data sets only contains recipes posted since 2008


Cleaned Dataframe Columns <br>

| Columns      | Datatype|
 |:-------------|--------:|
|id |  int64  | 
| minutes      |  int64  | 
|contributor_id|  int64  |
| submitted    |  object |
|  tags        |  object |
|  tags        |  object |
|  nutrition   |  object |

<br>


| Columns      | Datatype|
|:-------------|--------:|
|   id     |   int64|
|name      |  object | 
| minutes   |  int64  | 
|contributor_id|  int64  |
| submitted |datetime62[ns] |
|tags|  object  |
|nutrition|  object  |
|n_steps  |int64|
|steps       | object|
|description  | object|
|ingredients    | object|
|n_ingredients  | int64|
|ave_rating     | float64|
|calories      | float64|
|total fat (PDV)   | float64|
|sugar (PDV)    |float64|
|sodium (PDV)   | float64|
|protein (PDV)  |  float64|
|saturated fat (PDV) | float64|
|carbohydrates (PDV) |  float64|
dtype: object

**Recipes Dataset**


<p>'name' : Recipe Name <br>
'id' : Recipe ID <br>
'minutes' : minutes to prepare recipe <br>
'contributor_id' : user id who submitted recipe <br>
'submitted' : date recipe was submitted <br>
'tabs' - related tags for the recipe, generated by Food.com <br>
'nutrition' - Nutrition information in the form [calories (#), total fat (PDV), sugar (PDV), sodium (PDV), protein (PDV), saturated fat (PDV), carbohydrates (PDV)]; PDV stands for “percentage of daily value” <br>
'n_steps' - # of steps in recipe <br>
'steps' - text for recipe steps, in order<br>
description - user provided description <p>

**Raw interations Dataset**

<p>'user_id' : User ID <br>
'recipe_id':Recipe ID <br>
'date' : Date of interaction <br>
'rating' : Rating given <br>
'review' : Review text <br>

<br>**Merged Datframe**<br>
Both of the dataframes have common columns id and recipe id. In order to keep all the recipes, we merge left the two dateferames to show the corresponding rating and review for each unique recipe. 


<br>**Duplicate column**s<br>

Since the id and recipe id match up, we dropped the recipe column beccause it is uneccesssary to have duplicate values <br>

The columns relevant to our question are protein, sugar, n_steps, minutes, sodium, saturated fat, minutes, total fat, sugar, and carbohydrates, recipe id. 

<br>**Extracting Nutrition Column**<br>
We discovered that the values in the list are actually strings. 
As a result, we converted the values into a list of floats and created individual columns for each value in the list. The added columns are 
calories, total fat (PDV), sugar (PDV), sodium (PDV), protein (PDV), saturated fat (PDV), carbohydrates (PDV) with float data type




---

## Cleaning and EDA

<iframe src="assets/10-80-enrollment.html" width=800 height=600 frameBorder=0></iframe>


**Univariate Analysis*
We looked at the distribution of number of steps('n_steps') and 
the distribution of number of ingredients('n_ingredients')

The distributuon is skewed right  with the max count being 8, meaning that more most recipes have n_ingredients .
<iframe
  src="assets/un1_analysis.html"
  width="600"
  height="400"
  frameborder="0"
></iframe>


The distribution is skewed right with the max count being 7, meaning that most recipes have 7 steps.
<iframe
  src="assets/un2_analysis.html"
  width="600"
  height="400"
  frameborder="0"
></iframe>

The distribution is skewed right with the max count being 7, meaning that most recipes have 7 steps. 

**Bivariate Analysis**
We looked at the relationship between number of steps
and the amount of protein and the number of ingredients and the the number
of steps and the number of ingredients <br>

For the  number of steps and the amount of protein there seems no be no correlation and a weak relationship. There is an apparent outlier of4356 g of protein and 4 steps. The points are mainly clustered below 1000
g of protein. 


For the number of ingredients and the the number
of steps, there also seems to be no correlation and a weak relationship. 
There is an appparent outlier at the point of 37 ingredients and 6 steps.


**interesting aggregate**<br>
The average,min, and max sugar content of a recipe based on the amount of steps in the recipe.

print(pivot_table[['mean', 'min','max]].head().to_markdown(index=False))


---

## Assessment of Missingness

Missingness of 'Description'<br>
The column 'description' is NMAR because the user might have submitted
the recipe on a mobile device like an Iphone. Since it's a smaller screen, it's harder to write out a description. As a result, it takes more time to
write one. Therefore, the individual chooses not to include a description<br>

'Description' can become a MAR missingness if we add a new column with boolean statements of whether or not they are on a mobile device. There may be no description if the value is true. <br>

Here's what a Markdown table looks like. Note that the code for this table was generated _automatically_ from a DataFrame, using

Here's what a Markdown table looks like. Note that the code for this table was generated _automatically_ from a DataFrame, using

```py
print(counts[['Quarter', 'Count']].head().to_markdown(index=False))
```

| Quarter     |   Count |
|:------------|--------:|
| Fall 2020   |       3 |
| Winter 2021 |       2 |
| Spring 2021 |       6 |
| Summer 2021 |       4 |
| Fall 2021   |      55 |

There is more than one column that has nan values. However, columns with 
only one row of nan values don't have a significant impact on our 
analysis. 
We assume that ratings of 0 are replaced with nan because 
the individual didn't rate the recipe at at all. As a result, there
is not rating. 0.0 indicates that they strongly disliked the recipe which may not Including 0 would
impact the average rating. 

**'Rating' Missingness** <br>
**Missingness of rating based on the number of steps**
Null Hypothesis<mark> : distribution of n_steps when rating is missing is the same as the distribution of the calories 
when rating is not missing <br>
Alternative Hypothesis - distribution n_steps is different when rating is missing and when rating is not <br>

observed statistic- absolute diff between average n_steps of two distributions <br>

---

## Hypothesis Testing
**Question: Do fancier recipes have a greater average amount of calories?**<br>

fancy:
  more than 15 ingredients<br>
regular: 
  less than or equal to 15 ingredients<br>

<mark>null hypothesis<mark>: There is no difference in the number of calories between recipes fancy  and regular ingredients <br>

<mark>alternative hypothesis<mark> : Fancier recipes have a greater average of calories
than regular recipes <br>

Since we are dealing with numerical values: 
<mark>observed test statistic <mark>: The observed difference between the average number of calors of fancier and regular recipes. <br>

We decided to create a new column called 'ingred_gt_10' that includes
boolean statements of whether the recipe needs more than in 10 ingredients.
We also included another column called 'shuffled_ingred_gt_10' to shuffle 
our values and conduct a permutation test. 

We conducted a permutation test 10000 times and found that the p_value to be 0.178 with a significance level of  0.05 <br>
  src="assets/hypothesis.html"
  width="600"
  height="400"
  frameborder="0"


**conclusion**
Because 0.178> 0.05, we fail to reject the hypothesis that there is a difference between the number of. This means that there is no significant difference in the average number of calories between fancier and regular recipes. This may be because we don't take into account the preparation 
of the recipe and the type of ingredients. This can effect the amount of
calories. <br>











---
