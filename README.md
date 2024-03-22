# COOKIN CALORIES

by Jasmine & Shekar 

---

## Introduction

For our analysis, we chose to explore what types of recipes tend to have the most calories and we chose to predict the ratings of food using modeling. Our analysis is helpful for readers who are looking for a recipe that fits their dietary goals. This is a greal tool for people who are looking
for a tasty recipe that is also within their calorie goal. Calorie is a unit of energy that every person needs in order to function. People are always trying to find
recipes that diet friendly and good tasting. 

The two csv datasets we are working with are Raw Recipes and Raw Interactions. Raw_Recipes contains recipes and Raw_interactions contains the reviews and ratings submitted for the recipes in RAW_recipes. Both of the recipes are from Food.com.Food.com is a digital brand and media platform that features a large collection of recipes that are submitted, rated, and reviewed by foodies including home cooks, celebrity chefs, and shows. These data sets only contain data posted since 2008 

There are 82782 rows and 12 columns in the Recipe dataset. Each row is a unique recipe.
**Recipes Dataset**

<p>'name' : Recipe Name <br>
'id' : Recipe ID <br>
'minutes' : minutes to prepare recipe <br>
'contributor_id' : user id who submitted recipe <br>
'submitted' : date recipe was submitted <br>
'tabs' - related tags for the recipe, generated by Food.com <br>
'nutrition' - Nutrition information in the form [calories (#), total fat (PDV), sugar (PDV), sodium (PDV), protein (PDV), saturated fat (PDV), carbohydrates (PDV)]; PDV stands for “percentage of daily value” <br>
'n_steps' - # of steps in recipe <br>
'steps' - text for recipe steps, in order <br>
'description' - user provided description <br>


</p>

There are  731927 rows and 5 columns in raw interactions. Each row is a review left by a user.
**Raw Interactions Dataset** 

'user_id' : User ID 

'recipe_id':Recipe ID 

'date' : Date of interaction 

'rating' : Rating given 

'review' : Review text 

**Average Rating**
We created an extra column with the average rating of recipes. This is useful in order to build our model and predict the ratings of foods. 

**Merged Datframe**
Both of the dataframes have common columns id and recipe id. In order to keep all the recipes, we merged left the two dateferames to show the corresponding rating and review for each unique recipe. 


**Duplicate columns**

Since the id and recipe id match up, we dropped the recipe column beccause it is uneccesssary to have duplicate values


**Extracting Nutrition Column** 
We discovered that the values in the list are actually strings. 
As a result, we converted the values into a list of floats and created individual columns for each value in the list. The added columns are 
calories, total fat (PDV), sugar (PDV), sodium (PDV), protein (PDV), saturated fat (PDV), carbohydrates (PDV) with float data type<br>


The columns relevant to our question are coluprotein,calories, sugar, n_steps,ingredients, n_ingredients, minutes, sugar, recipe id,rating,average rating,and
review. Those are the columns we focused on for cleaning. 


**Cleaned DataFrame and Data Type With Relevant Columns**

|     id |   minutes |   n_steps |   n_ingredients |   calories |   total_fat |   sugar |   sodium |   protein |   saturated fat |   carbohydrates |   rating | review                                                                                                                                                                                                                                                                                                                                           |   average_rating |
|-------:|----------:|----------:|----------------:|-----------:|------------:|--------:|---------:|----------:|----------------:|----------------:|---------:|:-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|-----------------:|
| 333281 |        40 |        10 |               9 |      138.4 |          10 |      50 |        3 |         3 |              19 |               6 |        4 | These were pretty good, but took forever to bake.  I would send it ended up being almost an hour!  Even then, the brownies stuck to the foil, and were on the overly moist side and not easy to cut.  They did taste quite rich, though!  Made for My 3 Chefs.                                                                                   |                4 |
| 453467 |        45 |        12 |              11 |      595.1 |          46 |     211 |       22 |        13 |              51 |              26 |        5 | Originally I was gonna cut the recipe in half (just the 2 of us here), but then we had a park-wide yard sale, & I made the whole batch & used them as enticements for potential buyers ~ what the hey, a free cookie as delicious as these are, definitely works its magic! Will be making these again, for sure! Thanks for posting the recipe! |                5 |
| 306168 |        40 |         6 |               9 |      194.8 |          20 |       6 |       32 |        22 |              36 |               3 |        5 | This was one of the best broccoli casseroles that I have ever made.  I made my own chicken soup for this recipe. I was a bit worried about the tsp of soy sauce but it gave the casserole the best flavor. YUM!                                                                                                                                  |                5 |
|        |           |           |                 |            |             |         |          |           |                 |                 |          | The photos you took (shapeweaver) inspired me to make this recipe and it actually does look just like them when it comes out of the oven.                                                                                                                                                                                                        |                  |
|        |           |           |                 |            |             |         |          |           |                 |                 |          | Thanks so much for sharing your recipe shapeweaver. It was wonderful!  Going into my family's favorite Zaar cookbook :)                                                                                                                                                                                                                          |                  |
| 306168 |        40 |         6 |               9 |      194.8 |          20 |       6 |       32 |        22 |              36 |               3 |        5 | I made this for my son's first birthday party this weekend. Our guests INHALED it! Everyone kept saying how delicious it was. I was I could have gotten to try it.                                                                                                                                                                               |                5 |
| 306168 |        40 |         6 |               9 |      194.8 |          20 |       6 |       32 |        22 |              36 |               3 |        5 | Loved this.  Be sure to completely thaw the broccoli.  I didn&#039;t and it didn&#039;t get done in time specified.  Just cooked it a little longer though and it was perfect.  Thanks Chef.                                                                                                                                                     |                5 |


| Column Name    | Data Type   |
|:---------------|:------------|
| id             | int64       |
| minutes        | int64       |
| n_steps        | int64       |
| n_ingredients  | int64       |
| calories       | float64     |
| total_fat      | float64     |
| sugar          | float64     |
| sodium         | float64     |
| protein        | float64     |
| saturated fat  | float64     |
| carbohydrates  | float64     |
| rating         | float64     |
| review         | string      |
| average_rating | float64     |




**The whole Dataframe data type**

| Column Name    | Data Type   |
|:---------------|:------------|
| name           | object      |
| id             | int64       |
| minutes        | int64       |
| contributor_id | int64       |
| submitted      | object      |
| tags           | object      |
| nutrition      | object      |
| n_steps        | int64       |
| steps          | object      |
| description    | object      |
| ingredients    | object      |
| n_ingredients  | int64       |
| user_id        | Int64       |
| date           | object      |
| rating         | float64     |
| review         | object      |
| average_rating | float64     |
| calories       | float64     |
| total_fat      | float64     |
| sugar          | float64     |
| sodium         | float64     |
| protein        | float64     |
| saturated fat  | float64     |
| carbohydrates  | float64     |




---

## Cleaning and EDA


**Univariate Analysis**
We looked at the distribution of number of steps('n_steps') and 
the distribution of number of ingredients('n_ingredients') 

This is a distribution of the number of steps in recipes.The distributionn has a bell shaped curved and is skewed right  with the max count of n_steps being 7. This means that most recipes have 
7 steps .

<br>

<iframe
  src="assets/update.html"
  width="600"
  height="400"
  frameborder="0"
></iframe>

This is a count of n_ingredients
<iframe
  src="assets/un2_analysis.html"
  width="600"
  height="400"
  frameborder="0"
></iframe>
<br>
The distribution has a bell shaped curve and is is skewed right. The max count is at 8. This means that most recipes has 8 steps. 


**Bivariate Analysis**
We looked at the relationship between number of steps
and the amount of protein and the number of ingredients and the the number
of steps and the number of ingredients <br>

For the  number of steps and the amount of protein there seems no be no correlation and a weak relationship. There is an apparent outlier of 4356  of protein and 4 steps. The points are mainly clustered below 1000 for protein. 

<iframe
  src="assets/un3_analysis.html"
  width="600"
  height="400"
  frameborder="0"
></iframe>


This is the box plot of n_steps and n_ingredients
<iframe
  src="assets/box.html"
  width="600"
  height="400"
  frameborder="0"
></iframe>

There are many apparent outliers. A general pattern is that as n_ingredients increases, the range of steps increases. The boxplot with the greatest range
is at 30 ingredients. 


**interesting aggregate**<br>
The average,min, and max sugar content of a recipe based on the amount of steps in the recipe.<br>


|   n_steps |   ('mean', 'sugar') |   ('max', 'sugar') |   ('min', 'sugar') |
  |----------:|--------------------:|-------------------:|-------------------:|
|         1 |             64.0372 |               2360 |                  0 |
|         2 |             67.5614 |               4005 |                  0 |
|         3 |             60.2696 |               3537 |                  0 |
|         4 |             60.8759 |              16901 |                  0 |
|         5 |             54.3202 |              14495 |                  0 |



---

## Assessment of Missingness

**Missingness of 'Description'** <br>
The column 'description' is NMAR because the user might have submitted
the recipe on a mobile device like an Iphone. Since it's a smaller screen, it's harder to write out a description. As a result, it takes more time to
write one. Therefore, the individual may choose not to include a description<br>

'Description' can become a MAR missingness if we add a new column with boolean statements of whether or not they are on a mobile device. There may be no description if the value is true. <br>

There is more than one column that has nan values. However, columns with 
only one row of nan values don't have a significant impact on our 
analysis. We assume that ratings of 0 are replaced with nan because it 
may impact the average rating. Nan is not included when calculating mean.This
is more appropriate in cases where the values are not known or the true rating is not actually bad<br>

**'Rating' Missingness** <br>
**Missingness of rating based on the number of steps** <br>

*Null Hypothesis* : The distribution of 'n_steps' when 'rating' is missing is the same as the distribution of 'n_steps' when 'rating' is not missing.
 <br>
*Alternative Hypothesis* - The distribution of 'n_steps' is different when 'rating' is missing compared to when 'rating' is not missing. <br>
*observed statistic* - absolute difference between the average 'n_steps' when 'rating' is missing and the average 'n_steps' when 'rating' is not missing. <br>

<iframe
  src="assets/missingness4.html"
  width="600"
  height="400"
  frameborder="0"
></iframe>

The mean is about the same because they are both cerntered around the same place but have different shape. 

<iframe
  src="assets/missingness3.html"
  width="600"
  height="400"
  frameborder="0"
></iframe>


After conducting a permutation test to shuffle the missingness of rating 1000 times and geting 1000 simulating results about the absolute difference, we got a p-value of
0.0. Our significance level is 0.05. Because 0.0 < 0.05, we reject the null hypothesis that the distribution of  n_steps when rating is missing is the same as the distribution of the minutes when rating is not missing. Based on our p-value and results, rating is MAR because it's missingness is dependent on the number of steps it takes to prepare the food.


**Missingness of Rating Based on Minutes** <br>
*null hypothesis*: the distribution of the minutes when rating is missing is the same as the distribution of the minutes when rating is not missing 

*alternative hypothesis*: the distribution of the minutes when rating is missing is different from the distribution of the minutes when rating is not missing <br>
*observed statistic*: the absolute difference between minutes mean of these two distributions. <br>

<iframe
  src="assets/missingness2.html"
  width="600"
  height="400"
  frameborder="0"
></iframe>

The observed absolute difference is 51.45. Most of the points are to the left of the observed absolute difference point,

<iframe
  src="assets/missingness1.html"
  width="600"
  height="400"
  frameborder="0"
></iframe>

<p> After conducting a permutation test to shuffle the missingness of rating 1000 times and 1000 simulating results about the absolute difference, we got a p-value of
0.117. Our significance level is 0.05. Because 0.117> 0.05, we fail to reject the null hypothesis that the distribution of the minutes when rating is missing is the same as the distribution of the minutes when rating is not missing. Based on our p-value and results, rating is MCAR because it's missingness is not dependent on the amount of minutes it takes to prepare the food. <br> 


---




## Hypothesis Testing <br>
**Question: Do fancier recipes have a greater average amount of calories?** <br>

fancy:
  more than 15 ingredients<br>
regular: 
  less than or equal to 15 ingredients<br>

*null hypothesis*: There is no difference in the number of calories between fancy recipes  and regular recipes <br>

*alternative hypothesis* : Fancier recipes have a greater average of calories
than regular recipes <br>

Since we are dealing with numerical values: 
*observed test statistic* : The observed difference between the average number of calors of fancier and regular recipes. <br>

<p>We decided to create a new column called 'ingred_gt_10' that includes
boolean statements of whether the recipe needs more than in 10 ingredients.
We also included another column called 'shuffled_ingred_gt_10' to shuffle 
our values and conduct a permutation test. <br>

|   calories |   n_ingredients | ingred_gt_10   | shuffled_ingred_gt_10   |
|-----------:|----------------:|:---------------|:------------------------|
|      138.4 |               9 | False          | False                   |
|      595.1 |              11 | False          | False                   |
|      194.8 |               9 | False          | False                   |
|      194.8 |               9 | False          | False                   |
|      194.8 |               9 | False          | False                   |




We conducted a permutation test 10000 times and found that the p_value to be 0.178 with a significance level of  0.05 <br>


<iframe
  src="assets/hypthesis.html"
  width="600"
  height="400"
  frameborder="0"
></iframe>

<br>


**conclusion** <br>
<pr>Because 0.178> 0.05, we fail to reject the hypothesis that there is a difference between the number of calories in fancy and regular recipes. This means that there is no significant difference in the average number of calories between fancier and regular recipes. There are many factors that can contribute to calories of a recipe. This may include the preparation process
of the recipe and the type of ingredients it is made of. This can effect the amount of calories in a recipe. <br>

---







