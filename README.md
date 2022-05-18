# Analysis of Kickstarter Campaigns

## Overview of Project

### Background
Louise, an up-and-coming playwright, did a Kickstarter campaign for a play called Fever. Her campaign came close to its fundraising goal in a short amount of time. Louise wants to know how other campaigns fared in relation to hers in relation to their launch dates and their funding goals. We were provided with a datasheet that included fundraising information for various campaigns with similar endeavours. The datasheet included information such as launch date, country of origin, outcome, goal amount and amount pledged.

### Purpose

The purpose of this project is to help Louise understand how her Kickstarter campaign fared in relation to other campaigns. To do so I visualized Kickstarter campaign outcomes based on their launch dates and their funding goals. By making this information easier to understand, Louise can adjust her funding goals and launch dates to achieve better results in the future.

## Analysis and Challenges

### Analysis of Outcomes Based on Launch Date

The purpose of this analysis is to assess if the launch date of Kickstarter campaigns had an effect on their outcome.
Before creating a pivot table to analyze this information I converted the launch dates from the unix format provided into a MM/DD/YY format. To do so I used the following formula:

```=(((J2/60)/60)/24)+DATE(1970,1,1)``` 
> Column J in the datasheet provided included the unix dates.
> 
> This is why cell J2 is used in the formula above.

I also split the "Category and Subcategory" column into two separate columns. Doing this helps us get specific information that is tailored to Louise's requests.

To do this I went to Data > Text to Columns > Delimited > Other > "/". This process creates a column for each identifier. For example, a cell that included "theater / plays" was split into two separate columns; one showing "theater" and another showing "plays".

After formatting the datasheet I created a Pivot Table with the following fields:

<img width="294" alt="Screen Shot 2022-05-18 at 1 44 16 AM" src="https://user-images.githubusercontent.com/105120795/168974744-653004a6-18cc-41c5-b5b8-fe158c3286c3.png">

> I filtered the Date Created field under row to only show months.
> 
> The Parent Category filter was set to "theater" given that this is the information Louise is interested in.
>
>The Column Label was sorted in Descending order.

Once the pivot table was correctly organized I created a line chart to visualize the information.

![Theater_Outcomes_vs_Launch](https://user-images.githubusercontent.com/105120795/168975465-6956108a-b16d-4171-84f1-fd5df295fdae.png)


### Analysis of Outcomes Based on Goals

To perform my analysis of Outcomes Based on Goals I created a table that counted the number of successful, failed and canceled Kickstarters based on different ranges of monetary goals. This table also shows the total amount of projects and the percentage of successful, failed and canceled campaigns.

<img width="890" alt="Screen Shot 2022-05-18 at 1 54 23 AM" src="https://user-images.githubusercontent.com/105120795/168976365-e59e5132-6b1b-4826-ab52-2fb90ce01251.png">


To find the values for Columns B to D (count of successful, failed and canceled Kickstarters) I used the Countif formula with the "outcome" and "Subcategory" column as my variables. These variables were needed to ensure that the formula would only consider Kickstarter campaigns by outcome results to match my table and ensure that only "plays" were considered.

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

The first challenge I encountered was debugging formulas for the Outcomes Based on Goals table. I was getting an error after I had copied and pasted the formulas I used for the "Successful" column to use for the "failed" column. It was only when I manually did the formula again that I realized that I had not 'frozen' the column with a "$" sign on the Successful column and this was fetching information from the wrong column. Going forward I realize the importance of reworking formulas/code to ensure I am not overlooking an error. 

Another challenge I encountered was trying to confirm that my Outcomes based on Goals values were calculated correctly. To do so I manually filtered the datasheet with my two variables (Subcategory and Outcome), filtered the Goal column by each goal bracket and added the values to ensure they matched the results on my table. Although this was time-consuming I wondered if there might have been an easier way to confirm my findings. Going forward I want to work on my abilities to check my work and learn what are the most efficient ways to do so.

A possible challenge that we did not encounter was heavily formatting the information. Although we had to make some adjustments, the information provided was clear and well identified overall. We could be presented a datasheet that is not well structured, has lack of reliability if it is provided by a client, it's missing data and/or has deficiencies that we do not know about. Because of this our work could be correct but if the dataset is not reliable we would be presenting false information.



## Results

- What are two conclusions you can draw about the Outcomes based on Launch Date?

> The first conclusion I can draw about the Outcomes based on Launch Date is that there is a higher number of successful Kickstarter campagins between March and May. With this in mind it is recommended that future campaigns are planned around these months and disregarded outside of this bracket. By doing so better goals can be achieved in the future.
> 
> The second conclusion I can draw about the Outcomes based on Launch Date is that failed Kickstarter campagins seem to follow a similar path as successful campaigns but at lower numbers. Because this analysis does not include other factors it is hard to discern if failure happened because of the launch date alone. Although this last statement is also true for the first conclusion, there is a bigger contrast of campaigns being successful between March and May.

- What can you conclude about the Outcomes based on Goals?

> I can conclude that the number of "successful campaigns" and number of "failed campaigns" based on goals are inversely correlated. This is because the total number of projects by goal brackets only includes two values. That being said, we can confirm that it is true that the lower the bracket for funding goals, the higher the chance of a campaign being successful.

- What are some limitations of this dataset?

> One limitation of the dataset is that this file only shows Kickstarter results. It does not detail other external factors. For example, if these campaigns were shared outside of the Kickstarter website and the reach they had. Another external factor could be the popularity of plays according to patrons. A play or playwright that may we well known would probably have a higher chance of getting funding instead of a new play such as the one Louise campaigned for.
> 
> Another limitation is how a user may present their campaign on Kickstarter. Kickstarter allows users to upload videos, photographs, links and paragraphs of information to present to patrons. Because this information was not measured in the dataset we do not know the chance of a campaign failing because of poor presentation on Kickstarter.

- What are some other possible tables and/or graphs that we could create?

> Given that Louise's play is based in the US, it would be helpful to focus on Kickstarter campaigns for plays in the United States. Because there are multiple countries considered I believe that this may be skewing our results.
>
> First, I would create an Outcomes based on Country table. I would identify each country on the first column, number of successful campaigns on the second, failed campaigns on the third and canceled campaings on the fourth column. I would use a =COUNTIF( formula to find the sum of outcomes with country (US), Subcategory (plays) and outcomes (successful, failed and canceled) as variables. Then I would order them in descending order and identify how the US compares to the most popular countries. The purpose of this table is to have a visual understanding of how many Kickstarter campaigns there are per country and what was their outcome. I would also create a pie chart since I believe that it would be visually easier to understand for Louise.
> 
> I would also create an Outcomes based on Launch Date pivot table and add "country" as a filter to compare Fever to other American plays. Although the highest peak we found for our original table was between March and May I wonder if the highest peak for US plays would be a different set of months.


