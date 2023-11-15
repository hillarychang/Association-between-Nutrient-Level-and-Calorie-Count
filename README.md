by Hillary Chang (hic001@ucsd.edu)

## Introduction
In an era where mindful eating and wellness are in the spotlight, there's a growing emphasis on understanding the nutritional content of our meals. The calorie count of a recipe isn't just a number—it has evolved into a crucial piece of information, guiding individuals to make informed decisions about their dietary choices. For athletes, health enthusiasts, and even individuals living a normal lifestyle, having awareness of protein count and calorie content in recipes is essential for weight management, reaching fitness objectives, and fostering mindful decision-making. Our specific aim is to investigate the existence of a correlation between protein and calorie content in recipes.

Our dataset is curated from food.com and contains recipes and reviews. The data is separated into two datasets, the recipes dataset and ratings dataset. The recipes dataset contains columns like name, id, minutes, contributor_id, submitted tags, nutrition, n_steps, steps, description, ingredients, n_ingredients, representing the recipe name, recipe ID, the amount of recipes, ID of the person who contributed the recipe, and nutritional information, including the fats, sugar, sodium, protein, saturated fat, and carbohydrates. The ratings dataset includes te columns, user_id, recipe_id, date, rating, and review. This represents the ID of the user who left the review, the recipe ID the user left the review for, the date, and the rating and review the reviewer left for the recipe. The dataframe for recipes has 83782 rows, which represents 83782 unique recipes. The dataframe for ratings has 731927 rows, which represents 731927 reviews.

## Data Cleaning

### Merge Two Dataframes
In our exploration of the data, we first merged the Recipes and Ratings datasets using a left merge on the recipe's ID. This ensures that all recipes from the Recipes dataset are retained.

### Fill 0's with NaN Value
We also filled all ratings of 0 in the merged dataset with np.nan because the presence of 0's affect the mean of a column in the dataset, and we wanted to preserve an accurate mean. 

### Add Average Rating Column
Afterwards, we computed the average rating per recipe by grouping the dataset by recipe ID and calculating the mean of the ratings for each group.

### Convert Nutrition Column to List and Assign Individual Columns
the was a string so we had to convert the 

### Remove duplicate recipe entries 
(there are duplicate recipes with different reviews)

### Look at outliers 
extremely high calories

### The first few 5 rows of our cleaned and merged dataframe is shown below (with only important columns selected for display).
Show the head of your cleaned DataFrame (see Part 2: Report for instructions).

## Exploratory Data Analysis
## Univariate Analysis
In the univariate analysis, we analyzed the distribution of calorie count in the recipes. Because there were several recipes with extremely high calorie counts, we split the analysis into two graphs and created a distribution for recipes with calories greater than the recommended calorie intake of 2000 and a second one for recipes with calories less than or equal to the recommended calorie intake of 2000 to remove the outliers for each distribution.
<iframe src="assets/calorie_above.html" width=800 height=600 frameBorder=0></iframe>
This plot shows that the distribution of recipes with a calorie count from 0 to 2000 could be approximated as a right skewed gaussian distribution. The graph is centered around 200, meaning that most recipes below the recommended calorie intake of 2000 calories have around 200 calories.

<iframe src="assets/calorie_above.html" width=800 height=600 frameBorder=0></iframe>
This plot shows that the distribution of recipes with a calorie count from 2000 and up is also a right skewed gaussian distribution. Compared to the plot with a calorie count from 0 to 2000, this graph has a lot more outliers, with several recipes that have extremely high calorie count. The graph is centered around 2500, meaning that most recipes above the recommended calorie intake of 2000 calories have around 2500 calories.

## Bivariate Analysis
In the bivariate analysis, we analyzed the distribution of calorie count in the recipes with the protein count. Because there were several recipes with extremely high calorie counts, we split the analysis into two graphs and created a distribution for recipes with calories greater than the recommended calorie intake of 2000 and a second one for recipes with calories less than or equal to the recommended calorie intake of 2000 to remove the outliers for each distribution.
<iframe src="assets/bivariate" width=800 height=600 frameBorder=0></iframe>
This plot shows that the distribution of recipes with a calorie count from 0 to 2000 could be approximated as a right skewed gaussian distribution. The graph is centered around 200, meaning that most recipes below the recommended calorie intake of 2000 calories have around 200 calories.

<iframe src="assets/bivariate_above" width=800 height=600 frameBorder=0></iframe>
This plot shows that the distribution of recipes with a calorie count from 0 to 2000 could be approximated as a right skewed gaussian distribution. The graph is centered around 200, meaning that most recipes below the recommended calorie intake of 2000 calories have around 200 calories.

## Interesting Aggregates
Include a 1-2 sentence explanation about your plot, making sure to describe and interpret any trends present. (Your notebook will likely have more visualizations than your website, and that’s fine. Feel free to embed more than one bivariate visualization in your website if you’d like, but make sure that each embedded plot is accompanied by a description.)

Embed at least one grouped table or pivot table in your website and explain its significance.
pivot_table_recipe_type.sort_values(by='calories', ascending=False).to_markdown(index=False)

---
## Assessment of Missingness

Here's what a Markdown table looks like. Note that the code for this table was generated _automatically_ from a DataFrame, using

```py
print(counts[['Quarter', 'Count']].head().to_markdown(index=False))
```

---
## Hypothesis Testing
Hypothesis Test Question: 
Is there a significant relationship between nutrient levels (calories, total_fat, sugar, sodium, protein, saturated_fat, and carbs) in recipes and their calorie counts?

### Setting Up the Testing

```py
print(counts[['Quarter', 'Count']].head().to_markdown(index=False))
```

Null Hypothesis: 
The protein level has no association with calorie count in recipes.

Alternative Hypothesis: 
There is an association between protein level and calorie count in recipes.

Choice of Test Statistic: 
I am using the mean difference in calorie content between recipes with protein levels above and below their mean thresholds as the test statistic. Using the mean difference as the test statistic is appropriate because I am interested in comparing the calorie content for high protein levels (protein level above mean protein level) and low protein levels (protein level equal to or below mean protein level). We define "high protein level" as the protein level above mean protein level, and "low protein level" as the protein level equal to or below mean protein level.

Significance Level: 
I have chosen a significance level of 0.05 for this analysis. This is because a significance level of 0.05 is commonly used to represent the threshold for considering results statistically significant.


### Permutation Testing
<iframe src="assets/protein-calorie" width=800 height=600 frameBorder=0></iframe>


### Conclusion: 
The resulting p-value based on the observed difference and the distribution of differences obtained through permutation testing is 0.0.

With a p-value of 0.0 for the permutation test for protein, I have rejected the null hypothesis that the protein level has no association with calorie count in recipes. This p-value suggests that there is an association between the protein level and calorie content for the recipes.

---
