# An Analysis of Kickstarter Campaigns 
Performing analysis on Kickstarter data to discover trends 

# *Module 1 Guided Exercise*

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

## Analysis
We began by comparing campaign outcomes for all categories and found that while the theater category had the most successful campaigns, it also had the largest number of failures. 

![ParentCategoryOutcomes.png](https://github.com/charliuden/kickstarter-analysis/blob/main/ParentCategotyOutcomes.png)

To make sure that Louise falls into the successful outcome group, we next compared outcomes based on the launch date of campaigns. The most successful campaigns were those launched between May and August. Failed campaigns remain a steady count across all months. 

![OutcomesByMonth.png](https://github.com/charliuden/kickstarter-analysis/blob/main/OutcomesByMonth.png)

Looking specifically at the theater category, plays see more frequent successes than musicals or dramas. 

![TheaterSubcategoryOutcomes.png](https://github.com/charliuden/kickstarter-analysis/blob/main/TheaterSubcategoryOutcomes.png)

The location of Louise's campaign also matters - she would like her play to be in Great Britain. To look at how much money Louise can hope to raise during her campaign, we compared the distribution of campaign goals with campaign pledges in British plays. The mean campaign goal was $2,654.06 (all outcomes included). The median is $1,725.00, indicating that most goals fall below the mean. Further, if we take only successful play campaigns into account, their mean goal is $2,140.74. Again, most successful plays set a goal below this mean. Failed play campaigns saw higher a mean goal of $4,505.79. Perhaps these plays set goals too high -however, we see the same pattern - a median of $2,000 indicates that most failed goals fall below the mean, and in fact overlap with successful campaign goals. 

![Boxplot_GB_Goals_Pledges.png](https://github.com/charliuden/kickstarter-analysis/blob/main/Boxplot_GB_Goals_Pledges.png)

## Conclusions
Based on this analysis, I would recommend that Louise starts her campaign in May. At this point in my analysis, I also would recommend she set a goal of no more than $2,140.74 (the mean goal for all play campaign outcomes). However, I think a good next step would be to look at the relationship between a campaign start date and goal amount -were those campaigns that failed, despite setting reasonable goals, unsuccessful because of the start date? 

## *Module 1 Challenge*

# Kickstarting with Excel

## Overview of Project

### Purpose

This analysis was put together for Louise, a playwright looking to use Kickstarter to fund her play, "Fever". Louise anticipates the project costing $10,000 but wants to use data on other crowdfunding campaigns to make sure she has set realistic goals. So far, her campaign is going well - she has reached her goal! But, Louise would like to know how campaigns performed in relation to their launch data and funding goal. 

## Analysis and Challenges

### Data
To help Louise with her crowdfunding project, this analysis looks at trends in crowdfunding data from Kickstarter. The dataset is made up of 20 columns and 3883 rows - a row for each Kickstarter project. Although this is a lot of data, excel has a plethora of tools and functions that allow users to create new columns and summary statistics. All analyses were carried out using Microsoft Excel 2016. Columns used in this analysis include:

* *goal* - how much money the campaign hoped to raise
* *outcomes* - whether the campaign met its *goal*: successful, failed, canceled, live
* *launched_at* - start data of campaign, entered as a Unix timestamp
* *backers_count* - number of people that made a contributed to the campaign
* *Category and Subcategory* - the type of project being funded
* *Date Created Conversion* - created from *launched_at* (column J) using the following equation: =(((J2/60)/60)/24)+DATE(1970,1,1)
* *Year* - created from *Date Created Conversion* using the YEAR() function
* *Parent  Category*  and *Subcategory* - both were created from *Category and Subcategory* using the text to column tool

### Analysis of Outcomes Based on Launch Date

To get a count of each campaign outcome for a given campaign start month, data was sorted using a pivot table. Outcomes went into the 'Columns' and 'Values" boxes, Date Created Conversion went into the 'Rows' box, and Parent Category and Year both were placed into the 'Filter' box. The pivot table showed a column for each campaign outcome for each month of the year. The table can be filtered by Parent Category and Year. The line plot below shows theater campaign outcomes by month for all years (2012-2017). 

### Analysis of Outcomes Based on Goals

The COUNTIFS() function was used to find the percent of successful, failed, and canceled campaigns for intervals of campaign goals (amount of money a campaign hoped to raise). The "Goals", "Outcomes" and "Subcategory" columns were all used to find a count of plays whose campaigns failed, succeeded, or were canceled. 

![ParentCategoryOutcomes.png](https://github.com/charliuden/kickstarter-analysis/blob/main/resources/ScreenShot_PivotTable.png)

Values for goals were broken up into $5000 increments. The code below yields the number of plays with a goal between $1000 and $4999 that succeeded, where Kickstarter is the name of the sheet containing Kickstarter data. Column F contains campaign outcomes, column D contains a campaign's goal and column R contains the campaign's subcategory. 

=COUNTIFS(Kickstarter!$F:$F,"successful",Kickstarter!$D:$D,"<1000", Kickstarter!$R:$R, "plays")

Percentages for each outcome were then calculated for each goal interval. Finally, a line plot was used to look at the relationship between campaign goal and campaign outcome. 

### Challenges and Difficulties Encountered

The COUNTIFS() function is able to take in multiple columns from a spreadsheet and filter based on criteria defined by the user. I got slightly caught up in the order of inputs that the function requires but found [this](https://support.microsoft.com/en-us/office/countifs-function-dda3dc6e-f74e-4aee-88bc-aa8c2a866842) link helpful in making sure I was using the function properly. 

## Results

### Outcomes Based on Launch Date

Failed campaigns follow a similar temporal trend as successful ones. That is, there is little proportional difference in failed versus successful campaigns over time. However, during the months of May and June, the data deviate from this trend; there is a spike in successful campaigns, while failed campaigns remain level. 

![ParentCategoryOutcomes.png](https://github.com/charliuden/kickstarter-analysis/blob/main/resources/Theater_Outcomes_vs_Launch.png)

### Outcomes Based on Goals?

More campaigns succeed than fail when their goal is less than $19999. More campaigns fail than succeed when their goal is greater than $45000. The outcomes of campaigns with goals between this interval are more difficult to predict. 

![ParentCategoryOutcomes.png](https://github.com/charliuden/kickstarter-analysis/blob/main/resources/Outcomes_vs_Goals.png)

 ### Limitations of this Dataset

It would be good to know a little more about the content of campaigns for theater projects that succeed, failed, or are canceled. Perhaps some keywords that describe the genre of the play, drama, or musical (ie. comedy, romance, etc). Are some genres generating more money than others? Although this information is not available, there are more charts that could be created to help Louise decide if she should continue her campaign, despite already meeting her goal. 

### Further Work

Louise has met her goal -should she continue to try and raise money for her play? By how much do successful campaigns surpass their goal? To answer this question, I would subtract the *pledge* column from the *goal* column and filter for positive values. This gives us the amount of money by which successful campaigns surpass their goal. Then I would make a line plot similar to the "Outcomes Based on Goals" chart. Intervals of goal amount on the x-axis and the mean amount of money surpassed on the y-axis (using AVERAGE()). 

It would also be useful to look at campaign success in relation to campaign length -has Louise met her goal in a short amount of time, relative to other campaigns with similar goals? You can get campaign length from the *Date Created Conversion* and *Date Ended Conversion* columns. Then you could filter for "successful" (*outcomes*) "plays"(*Subcategory*) and make a scatterplot with campaign length on the x-axis and amount pledged on the y-axis.  


