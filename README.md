# COOKIN CALORIES
# Recipes

by Jasmine Hong (jah041@ucsd.edu) & Shekar


---

## Introduction

For our analysis, we chose to explore what types of recipes tend to have the most recipes and predict the amount of calories in a given recipe. 
Our analysis is helpful for readers who are looking for a recipe that fits their dietary goals. Our analysis is a great tool for readers who are looking for people looking to gain weight in the form of lean muscle mass or energy. Calories are units of energy that every individual needs for their body to function. 

The two csv datasets we are working with are Raw Recipes and Raw Interactions. Raw recipes contains recipes and Raw_interactions contains the reviews and ratings submitted for the recipes in RAW_recipes. Both of the recipes are from Food.com.Food.com is a digital brand and media platform that features a large collection of recipes that are submitted, rated, and reviewed by foodies including home cooks, celebrity chefs, and shows. These data sets only contains recipes posted since 2008


Cleaned Dataframe Columns

| Columns      | Datatype|
|:-------------|--------:|
|   id         |  int64  | 
| minutes      |  int64  | 
|contributor_id|  int64  |
| submitted    |  object |
|  tags        |  object |
|  tags        |  object |
|  nutrition   |  object |

Recipes Dataset
'name' - Recipe Name 
'id' - recipe id 
'minutes' - minutes to prepare recipe
'contributor_id' - user id who submitted recipe
'submitted' - date recipe was submitted
'tabs' - related tags for the recipe, generated by Food.com
'nutrition' - Nutrition information in the form [calories (#), total fat (PDV), sugar (PDV), sodium (PDV), protein (PDV), saturated fat (PDV), carbohydrates (PDV)]; PDV stands for “percentage of daily value”
'n_steps' - # of steps in recipe
'steps' - text for recipe steps, in order
description - user provided description 

Raw interations Dataset
'user_id' - User ID
'recipe_id'	- Recipe ID
'date' - Date of interaction
'rating' - Rating given
'review' - Review text


Merged Datframe 
Both of the dataframes have common columns id and recipe id. In order to keep all the recipes, we merge left the two dateferames to show the corresponding rating and review for each unique recipe. 



Duplicate columns 
Since the id and recipe id match up, we dropped the recipe column beccause it is uneccesssary to have duplicate values 

The columns relevant to our question are protein, sugar, n_steps, minutes, sodium, saturated fat, minutes, total fat, sugar, and carbohydrates, recipe id. 

Extracting Nutrition Column
We discovered that the values in the list are actually strings. 
As a result, we converted the values into a list of floats and created individual columns for each value in the list. The added columns are 
calories, total fat (PDV), sugar (PDV), sodium (PDV), protein (PDV), saturated fat (PDV), carbohydrates (PDV) with float data type




---

## Cleaning and EDA

<iframe src="assets/10-80-enrollment.html" width=800 height=600 frameBorder=0></iframe>

---

## Assessment of Missingness

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

---

## Hypothesis Testing




---
