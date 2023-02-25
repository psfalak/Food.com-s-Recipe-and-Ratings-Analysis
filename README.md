<!-- # Food.coms Recipe and Ratings Analysis

This repository shows analysis conducted by Pukhraj Falak and Patrick Salsbury

<!-- This is to test that the file is working correctly  --> -->
# Recipe and Ratings Analysis

by Patrick Salsbury (psalsbury@ucsd.edu) & Pukhraj Falak (pfalak@ucsd.edu)

***Note***: This page shows analysis done on Food.com's dataset containing recipes and ratings.


---

## Introduction

**TEMP** In this project, we examined how the calories, total fat, and protein impacted the rating of different recipes.

#### Question
Throughout our 

---

## Cleaning and EDA

```py
print(recipes_cleaned.head().to_markdown(index=False))
```

#### Univariate Analysis 
<iframe src="assets/Histogram-Boxplot_of_calories.html" width=800 height=600 frameBorder=0></iframe>
<iframe src="assets/Violinplot_of_calories.html" width=800 height=600 frameBorder=0></iframe>


#### Bivariate Analysis 
<iframe src="assets/Proportion_of_Ratings_per_Year2.html" width=800 height=600 frameBorder=0></iframe>
<iframe src="assets/Proportion_of_Ratings_per_Year3.html" width=800 height=600 frameBorder=0></iframe>


---

## Assessment of Missingness

**Temp text** We found that ratings was NMAR

<iframe src="assets/month_reviews.html" width=800 height=600 frameBorder=0></iframe>


This is a test to see the spacing 


<iframe src="assets/year_reviews.html" width=800 height=600 frameBorder=0></iframe>
This is another test to test spacing 
<!-- Here's what a Markdown table looks like. Note that the code for this table was generated _automatically_ from a DataFrame, using

<!-- ```py
print(counts[['Quarter', 'Count']].head().to_markdown(index=False))
```

| Quarter     |   Count |
|:------------|--------:|
| Fall 2020   |       3 |
| Winter 2021 |       2 |
| Spring 2021 |       6 |
| Summer 2021 |       4 |
| Fall 2021   |      55 | -->

--- -->

## Hypothesis Testing

<iframe src="assets/hypothesis_test.html" width=800 height=600 frameBorder=0></iframe>

---