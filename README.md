# Association-between-Protein-and-Calorie-Count
by Hillary Chang (hic001@ucsd.edu)

## Introduction

In this project, we studied the which n of spice challenges in building team morale.
Provide an introduction to your dataset, and clearly state the one question your analysis is centered around. Why should readers of your website care about the dataset and your question specifically? Report the number of rows in the dataset, the names of the columns that are relevant to your question, and descriptions of those relevant columns.

---

## Cleaning and EDA

Describe, in detail, the data cleaning steps you took and how they affected your analyses. The steps should be explained in reference to the data generating process. Show the head of your cleaned DataFrame (see Part 2: Report for instructions).

<iframe src="assets/10-80-enrollment.html" width=800 height=600 frameBorder=0></iframe>
Embed at least one plotly plot you created in your notebook that displays the distribution of a single column (see Part 2: Report for instructions). Include a 1-2 sentence explanation about your plot, making sure to describe and interpret any trends present. (Your notebook will likely have more visualizations than your website, and that’s fine. Feel free to embed more than one univariate visualization in your website if you’d like, but make sure that each embedded plot is accompanied by a description.)

Embed at least one plotly plot that displays the relationship between two columns. Include a 1-2 sentence explanation about your plot, making sure to describe and interpret any trends present. (Your notebook will likely have more visualizations than your website, and that’s fine. Feel free to embed more than one bivariate visualization in your website if you’d like, but make sure that each embedded plot is accompanied by a description.)


Embed at least one grouped table or pivot table in your website and explain its significance.

---

## Assessment of Missingness

Here's what a Markdown table looks like. Note that the code for this table was generated _automatically_ from a DataFrame, using

```py
print(counts[['Quarter', 'Count']].head().to_markdown(index=False))
```

---

## Hypothesis Testing

Hypothesis Test Question: Is there a significant relationship between nutrient levels (calories, total_fat, sugar, sodium, protein, saturated_fat, and carbs) in recipes and their calorie counts?

Null Hypothesis: The nutrient levels (calories, total_fat, sugar, sodium, protein, saturated_fat, and carbs) have no association with calorie count in recipes.

Alternative Hypothesis: There is an association between nutrient levels (calories, total_fat, sugar, sodium, protein, saturated_fat, and carbs) and calorie count in recipes.

Choice of Test Statistic: I am using the mean difference in calorie content between recipes with nutrient levels above and below their mean thresholds as the test statistic. Using the mean difference as the test statistic is appropriate because I am interested in comparing the calorie content for high nutrient levels (nutrient level above mean nutrient level) and low nutrient levels (nutrient level equal to or below mean nutrient level).

Significance Level: I have chosen a significance level of 0.05 for this analysis. This is because a significance level of 0.05 is commonly used to represent the threshold for considering results statistically significant.

Resulting p-value: The resulting p-value based on the observed difference and the distribution of differences obtained through permutation testing is 0.0.

Conclusion: With a p-value of 0.0 for each permutation test for each nutrient level (calories, total_fat, sugar, sodium, protein, saturated_fat, and carbs), I have rejected the null hypothesis that the nutrient levels (calories, total_fat, sugar, sodium, protein, saturated_fat, and carbs) have no association with calorie count in recipes. This p-value suggests that there is an association between nutrient levels (total_fat, sugar, sodium, protein, saturated_fat, carbs) and calorie content for the recipes, and recipes with higher nutrient levels tend to have higher calorie count.


Embed a visualization related to your hypothesis test in your website.

Tip: When making writing your conclusions to the statistical tests in this project, never use language that implies an absolute conclusion; since we are performing statistical tests and not randomized controlled trials, we cannot prove that either hypothesis is 100% true or false.

---
