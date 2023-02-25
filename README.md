<!-- # Food.coms Recipe and Ratings Analysis

This repository shows analysis conducted by Pukhraj Falak and Patrick Salsbury

<!-- This is to test that the file is working correctly  --> -->
# Recipe and Ratings Analysis

by Patrick Salsbury (psalsbury@ucsd.edu) & Pukhraj Falak (pfalak@ucsd.edu)

***Note***: This page shows analysis done on Food.com's dataset containing recipes and ratings.


---

## Introduction

**TEMP** In this project, we examined how the calories, total fat, and protein impacted the rating of different recipes.

### **Question**
Our analysis is centered around analyzing the distribution of missing food reviews throughout the years. We will look at the missingness in different *groups* of years and see if there is any relation between the two. Our two groups will be more recent years (2016 - 2018) and older years (2008 - 2016). 

Our question will be **Is there a relationship between the number of reviews missing and the year that the reivew was submitted in?**

We will be interested in the 'rating' column, which consists of a reviewers rating for a particular recipe, as well as the 'review_submitted_year' column, which consists of the year that the review was submitted ins.  


---

## Cleaning and EDA

```py
print(recipes_cleaned.head().to_markdown(index=False))
```

### Univariate Analysis 
<body>
    <iframe src="assets/Histogram-Boxplot_of_calories.html" width=800 height=600 frameBorder=0></iframe>
        <p>For our univariate analysis, we decided to look at the distribution of calories for all the recipes. We were curious to see if there most of the recipes consisted of low/high calorie meals. We can see from this plot, most of the recipes were in fact relatively low in calories, as more than half of our data was less than 300 calories. Noticing this trend, we thought it would be interesting to see if there was a trend with the rating for recipes and the amount of calories it contained.</p>
    <iframe src="assets/Violinplot_of_calories.html" width=800 height=600 frameBorder=0></iframe>
        <p>We created a violin plot to analyze the distribution of the different ratings. As we can see from the plot, there doesn't seem to be any clear trend between rating and the amount of calories.</p>
</body>

### Bivariate Analysis
<body>
    <p>For our bivariate analysis, we wanted to get some more insight before we conduct a hypothesis test on our question. We decided to look at the propotion of ratings per year. We wanted to see if there was a significantly larger amount of ratings in a particular year, as well more of a particular rating in a certain year. Let's take a look at our findings.</p>
    <iframe src="assets/Proportion_of_Ratings_per_Year2.html" width=800 height=600 frameBorder=0></iframe>
    <p>It is clear that the number of 5 star ratings is significantly higher than any other rating for every single year! Not only that, but we can see the amount of 1 star rating become more apparent as the years go on. For example, 2018 had a lot more one star ratings than 2008 did. </p>
    <iframe src="assets/Proportion_of_Ratings_per_Year3.html" width=800 height=600 frameBorder=0></iframe>
</body>


### Interesting Aggregates

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