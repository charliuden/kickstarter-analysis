# An Analysis of Kickstarter Campaigns 
Performing analysis on Kickstarter data to discover trends

## Background
This analysis was put together for Louise, a playwright looking to use Kickstarter to fund her play, "Fever". Louise anticipates the project costing $10,000 but wants to use data on other crowdfunding campaigns to make sure she has set realistic goals. 

## Question
What factors make a crowdfunding campaign successful?

## Data
We will be looking at trends in crowdfunding data from Kickstarter. The dataset is made up of 20 columns and 3883 rows - a row for each Kickstarter project. Although this is a lot of data, we are only using some of the columns. Columns used in this analysis include:
* name - the name of the project
* blurb - a description of the project
* goal - how much money the campaign hoped to raise
* pledged - how much money they raised
* outcomes - whether the campaign met its goal: successful, failed, canceled, live
* country - location of the campaign
* deadline - end date of the campaign
* launched_at - start data of campaign
* backers_count - number of people that made a contributed to the campaign
* Category and Subcategory - the type of project being funded
* Percentage Funded - the proportion of total cost that is being supported by the crowdfunding campaign
* Average Donation - the average amount of money donated by backers
    
    * The final four columns were created from other columns in the dataset

# Analysis
We began by comparing campaign outcomes for all categories and found that while the theater category had the most successful campaigns, it also had the largest number of failures. 

![ParentCategoryOutcomes.png](https://github.com/charliuden/kickstarter-analysis/blob/main/ParentCategotyOutcomes.png)

To make sure that Louise falls into the successful outcome group, we next compared outcomes based on the launch date of campaigns. The most successful campaigns were those launched between May and August. Failed campaigns remain a steady count across all months. 

![OutcomesByMonth.png](https://github.com/charliuden/kickstarter-analysis/blob/main/OutcomesByMonth.png)

Looking specifically at the theater category, plays see more frequent successes than musicals or dramas. 

![TheaterSubcategoryOutcomes.png](https://github.com/charliuden/kickstarter-analysis/blob/main/TheaterSubcategoryOutcomes.png)

The location of Louise's campaign also matters - she would like her play to be in Great Britain. To look at how much money Louise can hope to raise during her campaign, we compared the distribution of campaign goals with campaign pledges in British plays. The mean campaign goal was $2,654.06 (all outcomes included). The median is $1,725.00, indicating that most goals fall below the mean. Further, if we take only successful play campaigns into account, their mean goal is $2,140.74. Again, most successful plays set a goal below this mean. Failed play campaigns saw higher a mean goal of $4,505.79. Perhaps these plays set goals too high -however, we see the same pattern - a median of $2,000 indicates that most failed goals fall below the mean, and in fact overlap with successful campaign goals. 

![Boxplot_GB_Goals_Pledges.png](https://github.com/charliuden/kickstarter-analysis/blob/main/Boxplot_GB_Goals_Pledges.png)

# Conclusions
Based on this analysis, I would recommend that Louise starts her campaign in May. At this point in my analysis, I also would recommend she set a goal of no more than $2,140.74 (the mean goal for all play campaign outcomes). However, I think a good next step would be to look at the relationship between a campaign start date and goal amount -were those campaigns that failed, despite setting reasonable goals, unsuccessful because of the start date? 
