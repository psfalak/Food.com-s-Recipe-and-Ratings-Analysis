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

### Data Cleaning 
The first step in our data cleaning process was to address the nan values present.
Although description and review had a significant number of nan values, we chose to focus on
the other columns with nans because we hypothesized that there are underlying
missing mechanisms present with description and review. Therefore, we ended up 
dropping rows and filling in entries with placeholder values in order to ensure
our analysis can continue. Afterwards we converted all of the columns into their
correct datatypes respectively so we can correctly analyze the data later on. For
columns like date and submitted, we decided to extract the year, month, and 
day-of-week into their own columns so we can investigate possible relationships
later on. Similarily, we extracted the macronutrients individually from the
nutrition column into their own columns respectively as well. Finally, just to 
make our project easier, we created our own naming convention for the columns and 
also changed the order of the columns just so it is easier to refer to intuitively.



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
        <p>When we look at the stacked bar chart for this plot, we can more clearly see that the amount of one star ratings has significantly increased as the years went on. Not only that, but we can see a significant drop in the number five star ratings from 2015-2016. This fact could help us understand our result when we run our hypothesis test to answer our underlining question! </p>
</body>


### Interesting Aggregates


```py
print(recipes_temp_eda.head().to_markdown(index=False))
```


|   recipe_submitted_year |   rating |   count |   proportion |
|------------------------:|---------:|--------:|-------------:|
|                    2008 |        1 |    1110 |    0.0121043 |
|                    2009 |        1 |     707 |    0.0119525 |
|                    2010 |        1 |     340 |    0.0121668 |
|                    2011 |        1 |     211 |    0.0131105 |
|                    2012 |        1 |     204 |    0.0173322 |

---

## Assessment of Missingness

#### NMAR Analysis
<body>
When looking at our data, we observed that there was 3 columns that contained missing values: 'rating', 'description', and 'review'. Let's do some analysis on each of these columns to see if we believe are NMAR.
</body>
1. 'Rating' - We believe that rating column is in fact NMAR. In our original dataset, there was 6 different types of rating, ranging from 0 - 5. However, this was not due to the fact that reviews hated the dish so much that they gave the dish a 0. It was actually because they had left the section blank. When we converted these 0s to NaNs, we saw that there was a significant portion of the data missing for this column. We assumed this to be attributed to the fact that people did not like the recipe that they created, which would lead to a bad rating. Rather than them being rude to the person who posted the recipe, they would've decided just to leave it blank. Since the missingness is dependent on the value itself, we can conclude that the missingness in the 'rating' column is NMAR.
2. 'Description' - This column had the second most missing values in dataset. However, there isn't really an explanation of why the column would be NMAR. We were curious to see if there was relation to the length of the description and the missingness, however, no relationship was found. Coupling this with the fact that we could not justify how the missingness was dependent on the description itself, we decided to conclude that the missingness for this column was MAR.
3. 'Reviews' - The review column was definitely the trickiest in terms of determining if the data was NMAR. Initially we thought that if a person would leave a review blank, it was because they did not have nice things to say.

#### Missingneess Dependency


<body>
    <p>For our missingness, we chose to analyze the missingness in the 'reviews' column more closely. We wanted to see if the missingness of this column depended on any columns in our cleaned dataframe. We started by looking at the months. We thought this would be interesting to look at since there could be some trend around the holiday season where people are too lazy/more willing to give reviews. Let's unpack what we saw.</p>
    <iframe src="assets/month_reviews1.html" width=800 height=600 frameBorder=0></iframe>
        <p>From the graph, we can see that there are some values that are greater than our observed test statistic. However, when we run our permutation test, our p-value flucuates from .08 to around .2, indicating that we fail to reject our null hypothesis and say that there isn't a clear dependency of the 'review_submitted_month' column.</p>
    <p>Since we couldn't determine dependencies in that column, we decided to look at the 'review_submitted_year' column. This is what we found. </p>
    <iframe src="assets/year_reviews.html" width=800 height=600 frameBorder=0></iframe>
        <p>We can see that observed statistic is very from the most of the data in the distribution. After we ran our permutation tests, we saw that the p value was 0.0, indicating that there was in fact a dependancy on this columnn!</p>
        <p>When we examined our data more closely, we saw that out of the 57 missing values in the review column, only 4 came before 2015. The rest came between 2016-2018.</p>
</body>

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

To wrap up our analysis, we decided to go back and fully answer our original question: Is there a relationship between the number of reviews missing and the year that the reivew was submitted in?
In order to test whether or not this is true, we will set up a hypothesis test to compare the difference in means of ratings of 2016, 2017 and 2018 compared to the rest of the population. That being said, we can define our alternative hypothesis as:
**Null Hypothesis**:  the average of ratings from the years 2016, 2017, and 2018 = average of ratings from all other years
**Alternative Hypothesis**:  the average of ratings from the years 2016, 2017, and 2018 < average of ratings from all other years
the significance level will be at the 99% confidence level threshold so an alpha value of 0.01.

For our test statistic we will use the difference in means because we are trying to compare the means of a sample to the rest of the population. Since we want to test if the ratings in 2016, 2017, and 2018 are significantly lower, we will not use the absolute in means because the direction of the test is important.

After running our test, the distribution of the test statistics looked like this:

<iframe src="assets/hypothesis_test.html" width=800 height=600 frameBorder=0></iframe>

According to the results of our hypothesis test, we obtained a p-value of 0 which means that the probability that we obtained a test statistic under the null hypothesis as extreme in the direction of our alternative hypothesis is 0. That being said, we reject our null hypothesis that 2016, 2017, and 2018 recipes received average ratings as low as the rest of the population of recipes from other years.


** Back to our question : What types of recipes tend to have higher average ratings? **

As we originally observed from our EDA process and what we concluded from our hypothesis test, it appears that recipes from 2016, 2017 and 2018 scored lower ratings on average. That being said, this helps us answer our question because now we can observe that recipes that were submitted prior to 2016 tended to have higher average rating scores. Although we unfortunately can't isolate the reason why this is happening due to the number of confounding variables, it can help motivate another future step in this project to evaluate this phenomenon. If we also consider the number of reviews over the years, we observe a constant decrease in the number of reviews submitted since 2008. This additional piece of information could also help us analyze food.com's consumer base and possibly reveal other trends.
---