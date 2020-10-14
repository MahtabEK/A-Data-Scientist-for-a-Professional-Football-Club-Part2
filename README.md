# A-Data-Scientist-for-a-Professional-Football-Club-Part2
This project is part 2 of the project  "A Data Scientist for a Professional Football Club". In this project, managers want to test some hypotheses relating a player's overall rating and some of their characteristics in order to make better decisions on what players to trade/sign. They would like to create some statistical models for inference instead of prediction. And for that reason, in this project, I took off my "data" hat and put on my "science" hat :D


**The Dataset**
To test some of the management's hypotheses, the football club has spent some money to go out and collect new data in footballer_sample.csv. The variables are more or less the same from the previous dataset.

The data contain 52 columns, including some information about the player, their skills, and their overall measure as an effective footballer.

Most features relate to the player's abilities in football related skills, such as passing, shooting, dribbling, etc. Some features are rated on a 1-5 scale (5 being the best), others are rated on 0-100 (100 being the best), and others still are categorical (e.g. work rate is coded as low, medium, or high).

The target variable (𝑦) is overall. This is an overall measure of the footballer's skill and is rated from 0 to 100. The most amazingly skilled footballer would be rated 100. The model(s) we build will use the other features to predict overall.


**Part 1:**

In this section, I just read in the data and take a look at the dataframe. There are 52 columns. The outcome of interest is called overall which gives an overall measure of player performance. Not all of the other columns are particularly useful for modelling though (for instance, ID is just a unique identifier for the player. This is essentially an arbitrary number and has no bearing on the player's rating).

Same as part 1 of this project, we will remove these columns because they have no information for our work.

ID
club
club_logo
birth_date
flag
nationality
photo
potential


**Part 2:**

In statistics, it is useful to standardize our data to have mean 0 and standard deviation 1. This has the effect of putting all the variables on the same scale. It also has the added benefit of easing the interpretation of the coefficients to the following:

    Every 1 standard deviation change in the predictor  𝑥  results in a change of  𝛽  in the outcome.

Here,  𝛽  is the coefficient from the linear model we fit to the data. Standardize all the numeric variables. A good way to check that we've done this correctly is to compute the means (which should be close to 0) and the standard deviations (which should be close to 1).


**Part 3:**

One of the things scouts like to disagree upon is how a player changes as they age. Some insist that players hit their prime in their late 20s and as they reach middle age, they become worse because they can't keep up with younger players.

Other scouts are certain that the experience a player gains over their tenure makes them more valuable; they can anticipate what will happen on the field much better than a new player.

So here I want to investigate a quadratic term for age in a statistical model. I wrote a statistical model for these competing hypotheses and I have defined what is a null hypothesis and what is the alternative hypothesis.


**Part 4:**

I fit my model from Part 3. 
Here is a question for you: What can you conclude from the model about the quadratic effect of age? Can you explain your answer in terms of the null hypothesis?

You can find the answer to this question in the Jupyter Notebook I provided: "A Data Scientist for a Professional Football Club Part2.ipynb"


**Part 5:**

Management would also like to know how marking (the player's ability to prevent the other team from getting the ball) and interceptions (taking the ball when the opposing team is passing the ball between players) impact a player's overall ranking, controlling for age.

Those sound awfully similar, don't they? In this section, I fit two models: one model only controls for age (including the quadratic term) and marking, the other controls for age (including the quadratic term), marking, AND interceptions.

Here, there are some good questions to think about:

- What are the differences between the coefficient for marking in the first and second model? The size of the coefficient really is't the issue. Check out the sign of the coeffieicnt.

- Why do you think this difference could be troubling? How does the interpretation of a one standard deviation change in marking change between models?

- What might explain this difference? (I looked at model_data.corr() to answer this question).

You can find the answer to these questions in the Jupyter Notebook I provided: "A Data Scientist for a Professional Football Club Part2.ipynb"


**Part 6:**

Here, I fit the linear model overall~ preferred_foot. Incredibly, the model says that RIGHT FOOTED PLAYERS TEND TO BE WORSE AS COMPARED TO LEFT FOOTED PLAYERS! Scounts don't believe it, this goes against everything they've believed about being left footed.

So I perform a randomization test on this data. I performed 1000 randomizations of preferred_foot, fit the same model, and record the effects. Then I ploted a histogram of the effects from the randomized data and used plt.axvline to plot a vertical red line to indicate where the observed effect from our data lies.

I printed out the p value as well (p value is the proportion of the resampled effects are larger than our observed effect in absolute value).


**Part 7:**

Based on the findings from the randomization test, left footed players are on average 2.5 points better than their right footed counterparts! 
However, that might not be the whole story. So I decide to take a look at the dataset from my predictive model, called footballer_data.csv. I load the data, clean it up as I did in part 1, and perform another regression of overall onto preferred_foot, this time controlling for age (including the quadratic term) and interceptions. You can see the results. So here are some questions for you:

- What is the p-value for the effect of being right footed?

- What does that mean in terms of the null hypothesis?

You can find the answer to these questions in the Jupyter Notebook I provided: "A Data Scientist for a Professional Football Club Part2.ipynb"


**Part 8:**

Based on these results, what do you think about the idea of replacing the whole team with left-footed players?

You can find the answer to this question in the Jupyter Notebook I provided: "A Data Scientist for a Professional Football Club Part2.ipynb"
