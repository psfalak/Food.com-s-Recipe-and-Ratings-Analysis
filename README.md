<!-- # Food.coms Recipe and Ratings Analysis

This repository shows analysis conducted by Pukhraj Falak and Patrick Salsbury

<!-- This is to test that the file is working correctly  --> -->
# Recipe and Ratings Analysis

by Patrick Salsbury (psalsbury@ucsd.edu) & Pukhraj Falak (pfalak@ucsd.edu)

***Note***: This page shows analysis done on Food.com's dataset containing recipes and ratings.


---

## Introduction

For this project we were motivated to analyze the different relationships between variables within the two datasets that were gathered from Food.com. The first dataset involved information regarding recipes themselves while the second dataset kept track of all of the recipe reviews given by user. Utilizing a simple left-join, we can immediately enable analysis to begin within the 234,429 rows x 17 columns dataset. However, given all the number of experiment permutations we could perform, we decided to focus our project around investigating one single question.

### **Question: What type of recipes tend to have higher average ratings?**
We thought this would be a good question to answer because imagining the perspective of a prospective chef, we would want to know what attributes or features increase the likeliness of a recipe rating higher. In addition, the question is broad enough that allows our analysis to be lenient and more exploratory rather than a linear set of investigative steps. That being said, we decided to look at the possible relationships between rating and a myriad of variables including: the total cooking minutes, number of steps, number of ingredients, calories, protein, total fat, the year the recipe was submitted, the month the recipe was submitted, the tags the recipe included, and the ingredients the recipe included.

---

## Cleaning and EDA

### Data Cleaning 
The first step in our data cleaning process was to address the nan values present. Although description and review had a significant number of nan values, we chose to focus on the other columns with nans because we hypothesized that there are underlying missing mechanisms present with description and review. Therefore, we ended up dropping rows and filling in entries with placeholder values in order to ensure our analysis can continue. Afterwards we converted all of the columns into their correct datatypes respectively so we can correctly analyze the data later on. For columns like date and submitted, we decided to extract the year, month, and  day-of week into their own columns so we can investigate possible relationships later on. Similarily, we extracted the macronutrients individually from the nutrition column into their own columns respectively as well. Finally, just to  make our project easier, we created our own naming convention for the columns and also changed the order of the columns just so it is easier to refer to intuitively.


(Note: description, review, steps, tags, and ingredients column are not shown here for presentation sake)
```py
print(recipes_cleaned.head().to_markdown(index=False))
```
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>recipe_id</th>
      <th>author_id</th>
      <th>recipe_name</th>
      <th>recipe_submitted_date</th>
      <th>recipe_submitted_year</th>
      <th>recipe_submitted_month</th>
      <th>recipe_submitted_dow</th>
      <th>cooking_minutes</th>
      <th>n_steps</th>
      <th>n_ingredients</th>
      <th>n_tags</th>
      <th>calories</th>
      <th>total_fat</th>
      <th>protein</th>
      <th>sugar_data</th>
      <th>sodium</th>
      <th>sat_fat</th>
      <th>carbs</th>
      <th>reviewer_id</th>
      <th>rating</th>
      <th>reviewed_submitted_date</th>
      <th>reviewed_submitted_year</th>
      <th>reviewed_submitted_month</th>
      <th>reviewed_submitted_dow</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>333281</td>
      <td>985201</td>
      <td>1 brownies in the world    best ever</td>
      <td>2008-10-27</td>
      <td>2008</td>
      <td>October</td>
      <td>Sunday</td>
      <td>40</td>
      <td>10</td>
      <td>9</td>
      <td>14</td>
      <td>138.4</td>
      <td>10.0</td>
      <td>3.0</td>
      <td>50.0</td>
      <td>3.0</td>
      <td>19.0</td>
      <td>6.0</td>
      <td>386585</td>
      <td>4.0</td>
      <td>2008-11-19</td>
      <td>2008</td>
      <td>November</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <td>453467</td>
      <td>1848091</td>
      <td>1 in canada chocolate chip cookies</td>
      <td>2011-04-11</td>
      <td>2011</td>
      <td>April</td>
      <td>Sunday</td>
      <td>45</td>
      <td>12</td>
      <td>11</td>
      <td>9</td>
      <td>595.1</td>
      <td>46.0</td>
      <td>13.0</td>
      <td>211.0</td>
      <td>22.0</td>
      <td>51.0</td>
      <td>26.0</td>
      <td>42468</td>
      <td>5.0</td>
      <td>2012-01-26</td>
      <td>2012</td>
      <td>January</td>
      <td>Wednesday</td>
    </tr>
    <tr>
      <td>306168</td>
      <td>50969</td>
      <td>412 broccoli casserole</td>
      <td>2008-05-30</td>
      <td>2008</td>
      <td>May</td>
      <td>Thursday</td>
      <td>40</td>
      <td>6</td>
      <td>9</td>
      <td>10</td>
      <td>194.8</td>
      <td>20.0</td>
      <td>22.0</td>
      <td>6.0</td>
      <td>32.0</td>
      <td>36.0</td>
      <td>3.0</td>
      <td>29782</td>
      <td>5.0</td>
      <td>2008-12-31</td>
      <td>2008</td>
      <td>December</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <td>306168</td>
      <td>50969</td>
      <td>412 broccoli casserole</td>
      <td>2008-05-30</td>
      <td>2008</td>
      <td>May</td>
      <td>Thursday</td>
      <td>40</td>
      <td>6</td>
      <td>9</td>
      <td>10</td>
      <td>194.8</td>
      <td>20.0</td>
      <td>22.0</td>
      <td>6.0</td>
      <td>32.0</td>
      <td>36.0</td>
      <td>3.0</td>
      <td>119628</td>
      <td>5.0</td>
      <td>2009-04-13</td>
      <td>2009</td>
      <td>April</td>
      <td>Sunday</td>
    </tr>
    <tr>
      <td>306168</td>
      <td>50969</td>
      <td>412 broccoli casserole</td>
      <td>2008-05-30</td>
      <td>2008</td>
      <td>May</td>
      <td>Thursday</td>
      <td>40</td>
      <td>6</td>
      <td>9</td>
      <td>10</td>
      <td>194.8</td>
      <td>20.0</td>
      <td>22.0</td>
      <td>6.0</td>
      <td>32.0</td>
      <td>36.0</td>
      <td>3.0</td>
      <td>768828</td>
      <td>5.0</td>
      <td>2013-08-02</td>
      <td>2013</td>
      <td>August</td>
      <td>Thursday</td>
    </tr>
    <tr>
      <td>306168</td>
      <td>50969</td>
      <td>412 broccoli casserole</td>
      <td>2008-05-30</td>
      <td>2008</td>
      <td>May</td>
      <td>Thursday</td>
      <td>40</td>
      <td>6</td>
      <td>9</td>
      <td>10</td>
      <td>194.8</td>
      <td>20.0</td>
      <td>22.0</td>
      <td>6.0</td>
      <td>32.0</td>
      <td>36.0</td>
      <td>3.0</td>
      <td>52083</td>
      <td>5.0</td>
      <td>2017-10-17</td>
      <td>2017</td>
      <td>October</td>
      <td>Monday</td>
    </tr>
    <tr>
      <td>286009</td>
      <td>461724</td>
      <td>millionaire pound cake</td>
      <td>2008-02-12</td>
      <td>2008</td>
      <td>February</td>
      <td>Monday</td>
      <td>120</td>
      <td>7</td>
      <td>7</td>
      <td>20</td>
      <td>878.3</td>
      <td>63.0</td>
      <td>20.0</td>
      <td>326.0</td>
      <td>13.0</td>
      <td>123.0</td>
      <td>39.0</td>
      <td>813055</td>
      <td>5.0</td>
      <td>2008-04-09</td>
      <td>2008</td>
      <td>April</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <td>475785</td>
      <td>2202916</td>
      <td>2000 meatloaf</td>
      <td>2012-03-06</td>
      <td>2012</td>
      <td>March</td>
      <td>Monday</td>
      <td>90</td>
      <td>17</td>
      <td>13</td>
      <td>10</td>
      <td>267.0</td>
      <td>30.0</td>
      <td>29.0</td>
      <td>12.0</td>
      <td>12.0</td>
      <td>48.0</td>
      <td>2.0</td>
      <td>2204364</td>
      <td>5.0</td>
      <td>2012-03-07</td>
      <td>2012</td>
      <td>March</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <td>475785</td>
      <td>2202916</td>
      <td>2000 meatloaf</td>
      <td>2012-03-06</td>
      <td>2012</td>
      <td>March</td>
      <td>Monday</td>
      <td>90</td>
      <td>17</td>
      <td>13</td>
      <td>10</td>
      <td>267.0</td>
      <td>30.0</td>
      <td>29.0</td>
      <td>12.0</td>
      <td>12.0</td>
      <td>48.0</td>
      <td>2.0</td>
      <td>221672</td>
      <td>5.0</td>
      <td>2012-03-21</td>
      <td>2012</td>
      <td>March</td>
      <td>Tuesday</td>
    </tr>
    <tr>
      <td>500166</td>
      <td>2549237</td>
      <td>5 tacos</td>
      <td>2013-05-13</td>
      <td>2013</td>
      <td>May</td>
      <td>Sunday</td>
      <td>20</td>
      <td>5</td>
      <td>9</td>
      <td>26</td>
      <td>249.4</td>
      <td>26.0</td>
      <td>39.0</td>
      <td>4.0</td>
      <td>6.0</td>
      <td>39.0</td>
      <td>0.0</td>
      <td>369715</td>
      <td>4.0</td>
      <td>2013-06-13</td>
      <td>2013</td>
      <td>June</td>
      <td>Wednesday</td>
    </tr>
  </tbody>
</table>
### Univariate Analysis 
<body>
    <iframe src="assets/Histogram-Boxplot_of_calories.html" width=800 height=600 frameBorder=0></iframe>
        <p>For our univariate analysis, one of the variables we decided to look at was the distribution of calories across all recipes. We were curious to see how  the number of calories were distributed with regards to all the population of recipes. As a result, we can see from this plot that most of the recipes were in fact relatively low in calories, as more than half of our data was less than 300 calories. Noticing this trend, we thought it would be interesting to see if there was a trend with the rating for recipes and the amount of calories it contained.</p>
    <iframe src="assets/Violinplot_of_calories.html" width=800 height=600 frameBorder=0></iframe>
        <p>We created a violin plot to analyze the distribution of the different ratings. As we can see from the plot, there doesn't seem to be any clear trend between rating and the amount of calories.</p>
</body>

### Bivariate Analysis
<body>
    <p>For our bivariate analysis, we wanted to get some more insight on our variables before we conducted a hypothesis test to answer our question. One bivariate analysis we decided to look at the proportion of different ratings per year. We wanted to see if there was a significantly larger amount of a type of in a particular year compard to others. Let's take a look at our findings.</p>
    <iframe src="assets/Proportion_of_Ratings_per_Year2.html" width=800 height=600 frameBorder=0></iframe>
        <p>It is clear that the number of 5 star ratings is significantly higher than any other rating for every single year! Not only that, but we can see the amount of 1 star rating become more apparent as the years go on. For example, 2018 had a lot more one star ratings than 2008 did. </p>
    <iframe src="assets/Proportion_of_Ratings_per_Year3.html" width=800 height=600 frameBorder=0></iframe>
        <p>When we look at the stacked bar chart for this plot, we can more clearly see that the amount of one star ratings has significantly increased as the years went on. Not only that, but we can see a significant drop in the number five star ratings from 2015-2016. This fact could help us understand our result when we run our hypothesis test to answer our underlining question! </p>
</body>


### Interesting Aggregates
In order to have generated the plots above for our EDA step, we had to perform an interesting aggregate that outputted a dataframe as shown below. What makes this dataframe special is that we are able to showcase the count of ratings and their proportions distributed among the year the recipe was submitted and the rating respectively. This enables us to easily create a fancy plot to show how the distribution of ratings changes over the years.

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
When looking at our data, we observed that there was 3 columns that contained missing values: 'rating', 'description', and 'review'. However, the one column that we hypothesized would be categorized as an NMAR missing mechanism is rating.

We believed that rating column is in fact NMAR because in our original dataset, there was 6 different types of rating, ranging from 0 - 5. However, we thought that this was due to the fact that reviewers hated the dish so much that they gave the dish a 0. However, that should be impossible because ratings, according to food.com, should only range from 1 - 5 so when we converted these 0s to NaNs, we saw that there was a significant portion of the data missing for this column. Therefore, we assumed this to be attributed to the fact that when people did not like the recipe that they reviewed, they would just leave it review empty; then since we converted all the 0 ratings to nan values because they aren't possible, it resulted in a missingness mechanism dependent on the column itself.


#### Missingness Dependency
For our missingness, we chose to analyze the missingness in the 'reviews' column more closely. We wanted to see if the missingness of this column depended on any other columns in our cleaned dataframe. One of our tests involved running a permutation test on recipe_id. We thought this would be interesting to look at since maybe there was a trend that a particular recipe constantly kept getting reviewers who didn't feel the need to leave a review description.

<iframe src="assets/recipe_id_perm1.html" width=800 height=600 frameBorder=0></iframe>
    
After obtaining the results of our test, we see that there were enough test statistics in the direction as extreme of our observed statistic with a p-value of 0.96. At a significance level of 0.05, we inevitably fail to reject our hypothesis that the missing reviews depended on the recipe_id.

Another variable we decided to test was the year the review was submitted.

<iframe src="assets/year_reviews.html" width=800 height=600 frameBorder=0></iframe>

As a result, we obtianed a p-value of 0 which means that the reviews missing does depend on another column - in this case the year the reviews were submitted. There could be an infinite amount of confounding variables that contribute to this, but hypothesized that maybe after a certain year, food.com allowed users to not be forced to leave a description for their review.

However, this inclined us to investigate a possible relationship between the year the recipe was submitted and the review that it recieved. 


## Hypothesis Testing

To wrap up our analysis, we decided to go back and fully answer our original question: Is there a relationship between the number of reviews missing and the year that the reivew was submitted in?
In order to test whether or not this is true, we will set up a hypothesis test to compare the difference in means of ratings of 2016, 2017 and 2018 compared to the rest of the population. That being said, we can define our alternative hypothesis as:

**Null Hypothesis**:  the average of ratings from the years 2016, 2017, and 2018 = average of ratings from all other years

**Alternative Hypothesis**:  the average of ratings from the years 2016, 2017, and 2018 < average of ratings from all other years.

The significance level will be at the 99% confidence level threshold so an alpha value of 0.01.

For our test statistic we will use the difference in means because we are trying to compare the means of a sample to the rest of the population. Since we want to test if the ratings in 2016, 2017, and 2018 are significantly lower, we will not use the absolute in means because the direction of the test is important.

After running our test, the distribution of the test statistics looked like this:

<iframe src="assets/hypothesis_test.html" width=800 height=600 frameBorder=0></iframe>

According to the results of our hypothesis test, we obtained a p-value of 0 which means that the probability that we obtained a test statistic under the null hypothesis as extreme in the direction of our alternative hypothesis is 0. That being said, we reject our null hypothesis that 2016, 2017, and 2018 recipes received average ratings as low as the rest of the population of recipes from other years.


Back to our question : What types of recipes tend to have higher average ratings?

As we originally observed from our EDA process and what we concluded from our hypothesis test, it appears that recipes from 2016, 2017 and 2018 scored lower ratings on average. That being said, this helps us answer our question because now we can observe that recipes that were submitted prior to 2016 tended to have higher average rating scores. Although we unfortunately can't isolate the reason why this is happening due to the number of confounding variables, it can help motivate another future step in this project to evaluate this phenomenon. If we also consider the number of reviews over the years, we observe a constant decrease in the number of reviews submitted since 2008. This additional piece of information could also help us analyze food.com's consumer base and possibly reveal other trends.

---
