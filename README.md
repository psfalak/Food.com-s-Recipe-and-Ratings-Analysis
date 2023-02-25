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



```py
print(recipes_cleaned.head().to_markdown(index=False))
```
pqwertyuiop
#4271

pqwertyuiop — 02/09/2023 7:13 PM
# project.py


import numpy as np
import pandas as pd
import os
Expand
message.txt
9 KB
You missed a call from 
aj_
 that lasted 5 minutes.
 — 02/10/2023 4:06 PM
pqwertyuiop
 started a call that lasted an hour.
 — 02/10/2023 4:12 PM
aj_ — 02/10/2023 4:28 PM
result[[2]]
aj_ — 02/10/2023 4:57 PM
model <- lda(y ~ ., data = iris[, -5])
aj_ — 02/10/2023 5:18 PM
library(MASS)

# Load the iris dataset
data(iris)

# Create a response variable
y <- ifelse(iris$Species == "setosa", 1, 0)

# Perform LDA
model <- lda(y ~ ., data = iris[, -5])

# Print the summary of the model
summary(model)
library(klaR)
library(psych)
library(MASS)
library(ggord)
library(devtools)
aj_ — 02/10/2023 5:26 PM
install.packages('topicmodels')
aj_
 started a call that lasted an hour.
 — 02/16/2023 2:25 PM
aj_ — 02/16/2023 2:40 PM
model <- lm(salary ~ hits)
coefficients <- coef(model)
se <- sqrt(diag(vcov(model)))
aj_ — 02/16/2023 2:59 PM
sum(resid(model)^2)
pqwertyuiop — 02/16/2023 3:09 PM
https://cran.r-project.org/web/packages/margins/readme/README.html
You missed a call from 
aj_
 that lasted 2 minutes.
 — 02/17/2023 12:11 AM
pqwertyuiop
 started a call that lasted an hour.
 — 02/17/2023 12:29 AM
aj_ — 02/17/2023 12:31 AM
To calculate the degrees of freedom for the numerator of an F-statistic in a one-way ANOVA, you first need to know the number of groups (k) being compared. The numerator degrees of freedom is equal to k - 1. This represents the number of independent pieces of information that go into calculating the numerator of the F-statistic.

To calculate the degrees of freedom for the denominator of an F-statistic in a one-way ANOVA, you need to know the total sample size (N) and the number of groups (k) being compared. The denominator degrees of freedom is equal to N - k. This represents the number of independent observations in the sample that go into calculating the denominator of the F-statistic.
aj_ — 02/17/2023 12:46 AM
n <- nrow(my_data)
p1 <- 1  # number of predictor variables in the null model
p2 <- 3  # number of predictor variables in the alternative model

RSS1 <- sum(model1$residuals^2)
RSS2 <- sum(model2$residuals^2)

df1 <- n - p1 - 1  # degrees of freedom for the null model
df2 <- n - p2 - 1  # degrees of freedom for the alternative model
p_value <- pf(F_statistic, p2 - p1, df2, lower.tail = FALSE)
pf(fstat, df1, df2, lower.tail = FALSE)
aj_ — 02/17/2023 12:59 AM
if (p_value < 0.05) {
  cat("The multivariate linear regression model provides a significantly better fit than the simple linear regression model (p-value =", p_value, ").")
aj_ — 02/17/2023 1:21 AM
For example, the coefficient for x has a p-value of 1.08e-08, which is less than 0.05, indicating a significant effect of x on y.
aj_
 started a call that lasted an hour.
 — 02/21/2023 3:06 PM
pqwertyuiop — 02/21/2023 3:19 PM
def extract_book_links(text):
    soup = bs4.BeautifulSoup(text)
    li = soup.find_all('li', attrs = {'class':'col-xs-6 col-sm-4 col-md-3 col-lg-3'})
    return [li_i.find('a').get('href') for li_i in li if \
                     float(li_i.find('p', attrs = {'class': 'price_color'}).text.strip('Â').strip('£')) < 50 and \
                    (li_i.find('p', attrs = {'class': 'star-rating Four'}) != None or li_i.find('p', attrs = {'class': 'star-rating Five'}) != None)]


def get_product_info(text, categories):
    soup = bs4.BeautifulSoup(text)
    category = soup.find_all('a')[3].text
    if category in categories:
        table = soup.find('table', attrs = {'class': 'table table-striped'})
        keys = list(map(lambda t: t.text, table.find_all('th')))
        values = list(map(lambda t:t.text, table.find_all('td')))
        row_dict = dict(zip(keys,values))
        row_dict['Rating'] = soup.find('p', attrs = {'class': 'star-rating'}).get('class')[1]
        row_dict['Description'] = soup.find('div', attrs = {'id': 'content_inner'}).find_all('p')[3].text
        row_dict['Title'] = soup.find('h1').text
        row_dict['Category'] = category
        return row_dict
    return None


def scrape_books(k, categories):
    df_rows = []
    page_url = lambda i: 'http://books.toscrape.com/catalogue/page-' + str(i) + '.html'
    for i in range(1, k+1):
        request = requests.get(page_url(i))
        html_string = request.text
        qualified_book_urls = extract_book_links(html_string)
        for book_url in qualified_book_urls:
            book_info_request = requests.get('http://books.toscrape.com/catalogue/' + book_url)
            book_html_string = book_info_request.text
            row_result = get_product_info(book_html_string, categories)
            if row_result != None:
                df_rows.append(pd.Series(row_result))

    return pd.DataFrame(df_rows)
aj_ — 02/21/2023 9:06 PM
what i have so far. cant see any of the graphs for some reason
Attachment file type: unknown
template.ipynb
63.14 KB
aj_
 started a call that lasted 41 minutes.
 — 02/21/2023 11:49 PM
aj_ — 02/21/2023 11:57 PM
https://dsc80.com/project3/recipes-and-ratings/
DSC 80
Recipes and Ratings 🍽️
Description of the recipes and ratings dataset in Project 3.
https://dsc80.com/project3/#requirement-cleaning-and-eda-exploratory-data-analysis
DSC 80
Project 3
Description of Project 3.
aj_
 started a call that lasted 22 minutes.
 — 02/22/2023 7:43 PM
You missed a call from 
aj_
 that lasted a minute.
 — 02/22/2023 8:26 PM
aj_
 started a call that lasted 27 minutes.
 — 02/22/2023 8:48 PM
pqwertyuiop — 02/22/2023 9:15 PM
Attachment file type: unknown
template_1.ipynb
3.92 MB
pqwertyuiop
 started a call that lasted 13 minutes.
 — 02/22/2023 9:35 PM
aj_
 started a call that lasted an hour.
 — 02/22/2023 11:58 PM
aj_
 started a call that lasted an hour.
 — Yesterday at 11:29 AM
pqwertyuiop — Yesterday at 12:41 PM
Attachment file type: unknown
pat_aj_temp_2.ipynb
22.10 KB
aj_
 started a call that lasted 28 minutes.
 — Yesterday at 2:27 PM
aj_
 started a call that lasted 37 minutes.
 — Yesterday at 8:42 PM
aj_ — Yesterday at 8:44 PM
https://psfalak.github.io/Food.com-s-Recipe-and-Ratings-Analysis/
Food.com-s-Recipe-and-Ratings-Analysis
Food.coms-Recipe-and-Ratings-Analysis
This repository shows analysis conducted by Pukhraj Falak and Patrick Salsbury
aj_
 started a call that lasted 2 hours.
 — Today at 12:47 AM
pqwertyuiop — Today at 12:56 AM
Image
aj_ — Today at 10:40 AM
test_stat = shuffled_table.diff(axis=1).iloc[:,-1].abs().sum() / 2
        tvds.append(test_stat)
-------------------------
    fig = px.histogram(pd.DataFrame(tvds))
    fig.add_vline(obv_stat, line_color = 'red')
    fig.show()
--------------------------
    return np.mean(np.array(tvds) >= obv_stat) 
aj_ — Today at 11:04 AM
Null Hypothesis: The distribution of 'reviewed_submitted_month' is the same when 'review' is missing and when 'review' is not missing. 

Alternative Hypothesis: The distribution of 'reviewed_submitted_month' is the not the same when 'review' is missing and when 'review' is not missing.
this should be the markdown right before the first function call
-------------------------------------------------------------
Null Hypothesis: The distribution of 'reviewed_submitted_year' is the same when 'review' is missing and when 'review' is not missing. 

Alternative Hypothesis: The distribution of 'reviewed_submitted_year' is the not the same when 'review' is missing and when 'review' is not missing. 

this should be the markdown before the second function call 
aj_
 started a call that lasted an hour.
 — Today at 12:12 PM
pqwertyuiop — Today at 1:24 PM
Attachment file type: unknown
pat_aj_temp_3.ipynb
39.15 KB
aj_
 started a call that lasted 39 minutes.
 — Today at 3:40 PM
pqwertyuiop — Today at 3:56 PM
Attachment file type: unknown
pat_aj_temp_4.ipynb
43.34 KB
aj_ — Today at 5:18 PM
(np.array(test_stats) <= observed_stat).mean()
aj_
 started a call that lasted 9 minutes.
 — Today at 6:51 PM
aj_ — Today at 6:54 PM
https://psfalak.github.io/Recipe-and-Ratings-Analysis/
Recipe-and-Ratings-Analysis
Recipe-and-Ratings-Analysis
This repository shows analysis conducted by Pukhraj Falak and Patrick Salsbury
pqwertyuiop — Today at 7:42 PM
Data cleaning:
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
aj_
 started a call.
 — Today at 10:08 PM
aj_ — Today at 10:09 PM
https://psfalak.github.io/Recipe-and-Ratings-Analysis/
Recipe-and-Ratings-Analysis
Recipe-and-Ratings-Analysis
This repository shows analysis conducted by Pukhraj Falak and Patrick Salsbury
aj_ — Today at 10:37 PM
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th>recipe_id</th>
      <th>author_id</th>
      <th>recipe_name</th>
Expand
message.txt
12 KB
﻿
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
      <th>steps</th>
      <th>n_steps</th>
      <th>ingredients</th>
      <th>n_ingredients</th>
      <th>tags</th>
      <th>n_tags</th>
      <th>calories</th>
      <th>total_fat</th>
      <th>protein</th>
      <th>sugar_data</th>
      <th>sodium</th>
      <th>sat_fat</th>
      <th>carbs</th>
      <th>description</th>
      <th>reviewer_id</th>
      <th>rating</th>
      <th>reviewed_submitted_date</th>
      <th>reviewed_submitted_year</th>
      <th>reviewed_submitted_month</th>
      <th>reviewed_submitted_dow</th>
      <th>review</th>
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
      <td>['heat the oven to 350f and arrange the rack in the middle', 'line an 8-by-8-inch glass baking dish with aluminum foil', 'combine chocolate and butter in a medium saucepan and cook over medium-low heat , stirring frequently , until evenly melted', 'remove from heat and let cool to room temperature', 'combine eggs , sugar , cocoa powder , vanilla extract , espresso , and salt in a large bowl and briefly stir until just evenly incorporated', 'add cooled chocolate and mix until uniform in color', 'add flour and stir until just incorporated', 'transfer batter to the prepared baking dish', 'bake until a tester inserted in the center of the brownies comes out clean , about 25 to 30 minutes', 'remove from the oven and cool completely before cutting']</td>
      <td>10</td>
      <td>['bittersweet chocolate', 'unsalted butter', 'eggs', 'granulated sugar', 'unsweetened cocoa powder', 'vanilla extract', 'brewed espresso', 'kosher salt', 'all-purpose flour']</td>
      <td>9</td>
      <td>['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'for-large-groups', 'desserts', 'lunch', 'snacks', 'cookies-and-brownies', 'chocolate', 'bar-cookies', 'brownies', 'number-of-servings']</td>
      <td>14</td>
      <td>138.4</td>
      <td>10.0</td>
      <td>3.0</td>
      <td>50.0</td>
      <td>3.0</td>
      <td>19.0</td>
      <td>6.0</td>
      <td>these are the most; chocolatey, moist, rich, dense, fudgy, delicious brownies that you'll ever make.....sereiously! there's no doubt that these will be your fav brownies ever for you can add things to them or make them plain.....either way they're pure heaven!</td>
      <td>386585</td>
      <td>4.0</td>
      <td>2008-11-19</td>
      <td>2008</td>
      <td>November</td>
      <td>Tuesday</td>
      <td>These were pretty good, but took forever to bake.  I would send it ended up being almost an hour!  Even then, the brownies stuck to the foil, and were on the overly moist side and not easy to cut.  They did taste quite rich, though!  Made for My 3 Chefs.</td>
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
      <td>['pre-heat oven the 350 degrees f', 'in a mixing bowl , sift together the flours and baking powder', 'set aside', 'in another mixing bowl , blend together the sugars , margarine , and salt until light and fluffy', 'add the eggs , water , and vanilla to the margarine / sugar mixture and mix together until well combined', 'add in the flour mixture to the wet ingredients and blend until combined', 'scrape down the sides of the bowl and add the chocolate chips', 'mix until combined', 'scrape down the sides to the bowl again', 'using an ice cream scoop , scoop evenly rounded balls of dough and place of cookie sheet about 1 - 2 inches apart to allow for spreading during baking', 'bake for 10 - 15 minutes or until golden brown on the outside and soft &amp; chewy in the center', 'serve hot and enjoy !']</td>
      <td>12</td>
      <td>['white sugar', 'brown sugar', 'salt', 'margarine', 'eggs', 'vanilla', 'water', 'all-purpose flour', 'whole wheat flour', 'baking soda', 'chocolate chips']</td>
      <td>11</td>
      <td>['60-minutes-or-less', 'time-to-make', 'cuisine', 'preparation', 'north-american', 'for-large-groups', 'canadian', 'british-columbian', 'number-of-servings']</td>
      <td>9</td>
      <td>595.1</td>
      <td>46.0</td>
      <td>13.0</td>
      <td>211.0</td>
      <td>22.0</td>
      <td>51.0</td>
      <td>26.0</td>
      <td>this is the recipe that we use at my school cafeteria for chocolate chip cookies. they must be the best chocolate chip cookies i have ever had! if you don't have margarine or don't like it, then just use butter (softened) instead.</td>
      <td>42468</td>
      <td>5.0</td>
      <td>2012-01-26</td>
      <td>2012</td>
      <td>January</td>
      <td>Wednesday</td>
      <td>Originally I was gonna cut the recipe in half (just the 2 of us here), but then we had a park-wide yard sale, &amp; I made the whole batch &amp; used them as enticements for potential buyers ~ what the hey, a free cookie as delicious as these are, definitely works its magic! Will be making these again, for sure! Thanks for posting the recipe!</td>
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
      <td>['preheat oven to 350 degrees', 'spray a 2 quart baking dish with cooking spray , set aside', 'in a large bowl mix together broccoli , soup , one cup of cheese , garlic powder , pepper , salt , milk , 1 cup of french onions , and soy sauce', 'pour into baking dish , sprinkle remaining cheese over top', 'bake for 25 minutes or until cheese is lightly browned', 'sprinkle with rest of french fried onions and bake until onions are browned and cheese is bubbly , about 10 more minutes']</td>
      <td>6</td>
      <td>['frozen broccoli cuts', 'cream of chicken soup', 'sharp cheddar cheese', 'garlic powder', 'ground black pepper', 'salt', 'milk', 'soy sauce', 'french-fried onions']</td>
      <td>9</td>
      <td>['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'vegetables', 'easy', 'beginner-cook', 'broccoli']</td>
      <td>10</td>
      <td>194.8</td>
      <td>20.0</td>
      <td>22.0</td>
      <td>6.0</td>
      <td>32.0</td>
      <td>36.0</td>
      <td>3.0</td>
      <td>since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this one  #412 broccoli casserole.i don't think there are any like this one in the database. i based this one on the famous "green bean casserole" from campbell's soup. but i think mine is better since i don't like cream of mushroom soup.submitted to "zaar" on may 28th,2008</td>
      <td>29782</td>
      <td>5.0</td>
      <td>2008-12-31</td>
      <td>2008</td>
      <td>December</td>
      <td>Tuesday</td>
      <td>This was one of the best broccoli casseroles that I have ever made.  I made my own chicken soup for this recipe. I was a bit worried about the tsp of soy sauce but it gave the casserole the best flavor. YUM!  \nThe photos you took (shapeweaver) inspired me to make this recipe and it actually does look just like them when it comes out of the oven.  \nThanks so much for sharing your recipe shapeweaver. It was wonderful!  Going into my family's favorite Zaar cookbook :)</td>
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
      <td>['preheat oven to 350 degrees', 'spray a 2 quart baking dish with cooking spray , set aside', 'in a large bowl mix together broccoli , soup , one cup of cheese , garlic powder , pepper , salt , milk , 1 cup of french onions , and soy sauce', 'pour into baking dish , sprinkle remaining cheese over top', 'bake for 25 minutes or until cheese is lightly browned', 'sprinkle with rest of french fried onions and bake until onions are browned and cheese is bubbly , about 10 more minutes']</td>
      <td>6</td>
      <td>['frozen broccoli cuts', 'cream of chicken soup', 'sharp cheddar cheese', 'garlic powder', 'ground black pepper', 'salt', 'milk', 'soy sauce', 'french-fried onions']</td>
      <td>9</td>
      <td>['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'vegetables', 'easy', 'beginner-cook', 'broccoli']</td>
      <td>10</td>
      <td>194.8</td>
      <td>20.0</td>
      <td>22.0</td>
      <td>6.0</td>
      <td>32.0</td>
      <td>36.0</td>
      <td>3.0</td>
      <td>since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this one  #412 broccoli casserole.i don't think there are any like this one in the database. i based this one on the famous "green bean casserole" from campbell's soup. but i think mine is better since i don't like cream of mushroom soup.submitted to "zaar" on may 28th,2008</td>
      <td>119628</td>
      <td>5.0</td>
      <td>2009-04-13</td>
      <td>2009</td>
      <td>April</td>
      <td>Sunday</td>
      <td>I made this for my son's first birthday party this weekend. Our guests INHALED it! Everyone kept saying how delicious it was. I was I could have gotten to try it.</td>
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
      <td>['preheat oven to 350 degrees', 'spray a 2 quart baking dish with cooking spray , set aside', 'in a large bowl mix together broccoli , soup , one cup of cheese , garlic powder , pepper , salt , milk , 1 cup of french onions , and soy sauce', 'pour into baking dish , sprinkle remaining cheese over top', 'bake for 25 minutes or until cheese is lightly browned', 'sprinkle with rest of french fried onions and bake until onions are browned and cheese is bubbly , about 10 more minutes']</td>
      <td>6</td>
      <td>['frozen broccoli cuts', 'cream of chicken soup', 'sharp cheddar cheese', 'garlic powder', 'ground black pepper', 'salt', 'milk', 'soy sauce', 'french-fried onions']</td>
      <td>9</td>
      <td>['60-minutes-or-less', 'time-to-make', 'course', 'main-ingredient', 'preparation', 'side-dishes', 'vegetables', 'easy', 'beginner-cook', 'broccoli']</td>
      <td>10</td>
      <td>194.8</td>
      <td>20.0</td>
      <td>22.0</td>
      <td>6.0</td>
      <td>32.0</td>
      <td>36.0</td>
      <td>3.0</td>
      <td>since there are already 411 recipes for broccoli casserole posted to "zaar" ,i decided to call this one  #412 broccoli casserole.i don't think there are any like this one in the database. i based this one on the famous "green bean casserole" from campbell's soup. but i think mine is better since i don't like cream of mushroom soup.submitted to "zaar" on may 28th,2008</td>
      <td>768828</td>
      <td>5.0</td>
      <td>2013-08-02</td>
      <td>2013</td>
      <td>August</td>
      <td>Thursday</td>
      <td>Loved this.  Be sure to completely thaw the broccoli.  I didn&amp;#039;t and it didn&amp;#039;t get done in time specified.  Just cooked it a little longer though and it was perfect.  Thanks Chef.</td>
    </tr>
  </tbody>
</table>
message.txt
12 KB

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
