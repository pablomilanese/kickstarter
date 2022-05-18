# Analysis of Kickstarter Campaigns

## Overview of Project

### Background
Louise, an up-and coming playwright, did a Kickstarter campaign for a play called Fever. Her campaign came close to its fundraising goal in a short amount of time. Louise wants to know how other campaigns fared in relation to hers in relation to their launch dates and their funding goals. We were provided with a datasheet that included fundraising information for various campaigns with similar endeavours. The datasheet included information such as launch date, country of origin, outcome, goal amount and amount pledged.

### Purpose

The purpose of this project is to help Louise understand how her Kickstarter campaign fared in relation to other campaigns. To do so I visualized Kickstarter campaign outcomes based on their launch dates and their funding goals. By making this information easier to understand, Louise can adjust her funding goals and launch dates to achieve better results in the future.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

The purpose of this analysis is to assess if the launch date of Kickstarter campaigns had an effect on their outcome.
Before creating a pivot table to analyze this information I converted the launch dates from the unix format provided into a MM/DD/YY format. To do so I used the following formula:

```=(((J2/60)/60)/24)+DATE(1970,1,1)``` 

I also split the "Category and Subcategory" column into two separate columns. Because each cell differentiated the "Parent Category" from it's "Subcategory" with a "/" I went to Data > Text to Columns > Delimited > Other > "/".

After I had formatted my data accordingly I created a Pivot Table with the following fields:

<img width="294" alt="Screen Shot 2022-05-18 at 1 44 16 AM" src="https://user-images.githubusercontent.com/105120795/168974744-653004a6-18cc-41c5-b5b8-fe158c3286c3.png">

> I filtered the Date Created field under row to only show months.
> 
> The Parent Category filter was set to "theater" given that this is the information Louise is interested in
>
>The Column Label was sorted in Descending order.

Once the pivot table was correctly organized I created a line chart to visualize the information.

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/105120795/168975465-6956108a-b16d-4171-84f1-fd5df295fdae.png)


### Analysis of Outcomes Based on Goals

To perform my analysis of Outcomes Based on Goals I created a table that counted the number of successful, failed and canceled Kickstarters based on different ranges of monetary goals. This table also shows the total amount of projects and the percentage of successful, failed and canceled campaigns.

<img width="890" alt="Screen Shot 2022-05-18 at 1 54 23 AM" src="https://user-images.githubusercontent.com/105120795/168976365-e59e5132-6b1b-4826-ab52-2fb90ce01251.png">


To find the values for Columns B to D I used the Countif formula with the "outcome" and "Subcategory" column as my variables. These variables were needed to ensure that the formula would only consider Kickstarter campaigns by outcome results to match my table and ensure that only "plays" were considered.

To illustrate how this formula works we will be looking at cell C4 (outcomes failed with a goal between 5000 to 9999) as an example:

<img width="894" alt="Screen Shot 2022-05-17 at 9 30 34 PM" src="https://user-images.githubusercontent.com/105120795/168976615-6bb2e3ed-4353-4a70-8f6c-f15be93620a7.png">

I made the following graphic to illustrate how we found this value using the countif formula:

<img width="1001" alt="Screen Shot 2022-05-17 at 9 30 09 PM" src="https://user-images.githubusercontent.com/105120795/168976685-06dcd54f-8d3a-4308-802f-bb590f8a2f00.png">


To find the amount of Total Projects by goals I used a =SUM() formula adding the values for each row, from column B to D.

For example the Total Projects for Goals less than 1000 the formula looks as follows:

<img width="575" alt="Screen Shot 2022-05-17 at 9 36 06 PM" src="https://user-images.githubusercontent.com/105120795/168976866-f48ce7d6-d40c-4485-b208-bbb68c323901.png">


To calculate the percentage of Successful projects, for example, I divided the number of successful campagins by the amount of total projects.

<img width="697" alt="Screen Shot 2022-05-17 at 9 39 51 PM" src="https://user-images.githubusercontent.com/105120795/168976988-5a263e14-e70b-4283-8c05-8dc9b949f833.png">


After finishing my table I created a line chart to compare the different set of goals for each outcome by percentage.

The chart looks as follows:

![Outcomes_vs_Goals](https://user-images.githubusercontent.com/105120795/168977041-9e75240f-d0ba-4fb2-9c86-bf237c821130.png)

>It is important to note that there were no canceled plays, which are illustrated in a straight gray line that goes horizontally on the chart.

### Challenges and Difficulties Encountered for the Analysis of Outcomes Based on Launch Date

The first challenge I found 



## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

> The first conclusion I can draw about the Outcomes based on Launch Date is that there is a higher number of successful Kickstarter campagins between March and May. With this in mind it is recommended that future campaigns are planned around these months and disregarded outside of this bracket. By doing so better goals can be achieved in the future.

> The second conclusion I can draw about the Outcomes based on Launch Date is that failed Kickstarter campagins seem to follow a similar path as successful campaigns but at lower numbers. Because this analysis does not include other factors it is hard to discern if failure happened because of the launch date alone. 

- What can you conclude about the Outcomes based on Goals?

> I can conclude that the number of "successful campaigns" and number of "failed campaigns" based on goals are inversely correlated. It is also important to note that there were no canceled Kickstarters for plays. Because this analysis only gives us two values for each goal

> What are some limitations of this dataset?

> Because this data set only shows campaign information concerning goals, we cannot discern if a campaign with a goal of <$1,000, for example, was not successful because of other variables such as launch date, popularity of plays in X country or other factors. On the other hand we may conclude that a campaign with a target of >$50,000 failed because the amount of money was too high.

- What are some other possible tables and/or graphs that we could create?

> Given that Louise's play is based in the US, I believe it is worth to consider the country as a variable that may help us get a more precise analysis of how her play may compare to other ones.
