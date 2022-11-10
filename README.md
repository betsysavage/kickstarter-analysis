# Kickstarting with Excel

## Overview of Project

### Purpose ###
This report reviews the fundraising outcomes for theater campaigns based on their launch dates and fundraising goals. The client, Louise, is in the process of raising money for her play, Fever, and is interested in examining common factors that have made fundraising campaigns successful or unsuccessful historically. This specific analysis describes trends in funding goals and campaign start time for various campaigns grouped by their outcomes. This analysis will help the client to strategize her campaign goal and timing and predict progress towards her campaign's funding goal based on the launch date.
-
## Analysis and Challenges ##

### Analysis of Outcomes Based on Launch Date ###
In the first part of this analysis, I prepared the kickstarter workbook data to create a pivot table and pivot chart describing campaign outcomes based on the date the campaigns began, or "launched." To do this, the following action items were completed:
- A "Years" column was inserted directly next to the "Date Created Conversion column". The =YEAR() function was used to refer to the Date Created Conversion cells, thereby extracting the year from the month, day, and year data in a separate column. After the function was applied to the cell in the top row, the formula was dragged until the entire column was populated.
- After this new column was added, the full worksheet range was selected to create a pivot table. A pivot table was inserted by selecting the "Pivot Table" icon from the "Insert" menu. When confirming the data range for the table input, the pivot table wizard offered an option to insert the chart in a new sheet. 
- To populate the pivot table, the following fields were selected:
        - Columns: Outcomes
        - Values: Count of outcomes
        - Rows: Date Created Conversion
        - Filters: Parent category, Years
- After the pivot table was created, I applied the filter for "parent category" to list only the "theater" options in the results. This was completed by clicking the "filter" icon on the parent category field and deselecting all checkboxes except "theater".
- To visually prioritize campaigns that were successful, I sorted the chart by clicking the "filter" icon on the table headers and selecting the option to sort by descending alphabetical order, which would list the "s" for successful outcomes in the first column reading left to right. 
At the conclusion of this analysis, the pivot table contained data that was filtered to display only campaigns in the theater category - Louise's field of interest. The data was organized by month and sorted by outcomes to visually prioritize the successful campaigns.  
The next step of this analysis was to create a visual representation of the results. The graph was created by: 
- Selecting the pivot table, navigating to the "PivotTable Analyze" menu, and selecting "PivotChart." 
- The chart that was automatically generated was a column chart type; In order to use this data to create a line chart, I selected "Design", then "Change Chart Type." The "Line with Markers" option was available for selection in the dropdown menu.
- To insert the chart title, I remained on the "Design" menu, selected "Add Chart Element," and selected "Chart Title."
At the conclusion of this analysis, the line graph displays the pivot chart data visually in a line chart to allow us to easily track trends by month throughout the year. The different lines represent campaigns of different outcomes. 
<img width="1298" alt="image" src="https://user-images.githubusercontent.com/114873837/201186243-f28c6f0b-dd76-45a0-87b6-f7558bb7bb76.png">

### Analysis of Outcomes Based on Goals
In the second part of this analysis, I used the kickstarter workbook data to prepare a table of calculations summarizing the number of campaigns fittng a specific subset of criteria (campaigns belonging to the "plays" subcategory with goals falling into a specific dollar range for each outcome type). To create this table, the following action items were completed:
- The column and row assignments were populated with the headers and row labels of interest, with outcome types in the column labels and goal fundraising amounts in the row labels.
- The number of campaigns in each category were calculated using a COUNTIFS formula establishing the criteria for a selected range of data. The COUNTIFS formula behaves as a filter to reduce the data in the selected range to only the items that fit the criteria provided. For example, in cell B2, to count the number of successful campaigns belonging to the play subcategory that had goals of less than $1000, we would insert the following function:
                =COUNTIFS(Kickstarter!D:D,"<1000",Kickstarter!F:F,"=successful",Kickstarter!R:R,"=plays")
- This formula was inserted into every cell in the first three columns, and then the criteria were edited accordingly to target the appropriate goal range and outcome type. For example, in our table, Cell C8 would describe the number of campaigns with goals between $25,000 and $29,000 that failed in their fundraising attempts. The function in this cell would read as follows:
                =COUNTIFS(Kickstarter!D:D,">=25000",Kickstarter!D:D,"<=29999",Kickstarter!F:F,"=successful",Kickstarter!R:R,"=plays")
- After populating the first three columns with data, I could use these values to summarize the number of total projects in the play subcategory for each goal range. To do so, I applied a =SUM function to add the number of campaigns for each outcome type. There are many ways to structure a formula to add values of different cells, including directly referencing the cells (=B2 + C2 + D2), but a summary function that covers the range of interest is the most efficient syntax to add values from several cells quickly (=SUM(B2:D2)). This function was then applied to all rows to populate the "Total Projects" column.
 - While displaying the overall number of projects by outcome is good, these numbers would be more suitable for analysis if we had a clearer understanding of the context. For example, would 45 campaigns that have failed be considered high in relation to the overall number of campaigns? The values that I have calculated would have more meaning if they were displayed as a percentage of a whole. To calculate a percentage, I used a simple division formula using the / operator to divide each cell by the total number of projects for the goal range of interest. An example of this formula for the top row would be =B2/E2.
 - Once the calculation was applied, the resulting numbers displayed as a decimal number. For the cells to appear as percentages, I changed the data's format type to a percentage by navigating from the home tab to the data format dropdown menu. I adjusted the format from "General" to "Percentage". This was repeated until all percentages were calculated and formatted for the various outcome types.
As a result of this analysis, the table contains the count of campaigns in the play subcategory for each type of outcome. The data is organized by fundraising goal ranges and allows us to examine the percentage of campaigns within each fundraising range that were successful, unsuccessful, or canceled.
The next step of this analysis was to create a visual representation of the results. This graph was created by:
- Highlighting the columns of interest for the analysis, which included the Goal column (Column A), Percentage Successful, Percentage Failed, and Percentage Canceled columns (Columns F through H), navigating to the "Insert" menu, and selecting the icon for line charts. 
- The title and axes of the chart were automatically populated. I edited the chart title by simply double clicking and renaming.
At the conclusion of this analysis, this chart displays this information visually in lines to allow us to track the percentage of overall projects that were successful or unsuccessful as the fundraising goal range increases.  
<img width="1316" alt="image" src="https://user-images.githubusercontent.com/114873837/201186369-d9f4b7fe-a114-4080-aab1-bc92bd859d04.png">

### Challenges and Difficulties Encountered
I experienced a couple challenges when completing this analysis:
- Separating the rows by month in the Outcomes by Launch Date pivot table: When the Date Created Conversion field was dragged into the "rows" section of the pivot table, the rows automatically grouped by year, when the unit of interest for our analysis was month. 
<img width="145" alt="image" src="https://user-images.githubusercontent.com/114873837/201208804-3fce6722-102c-4b4e-81cc-2bc32ca73971.png">
To resolve this issue, I consulted module 1.3.3, which included an exercise in which campaigns were similarly grouped by month. When the Years and Quarters options were clicked and dragged back to the selection panel, months were the only remaining group to use as a label.

- Applying multiple criteria to filter by goal ranges in the Outcomes Based on Goals table: When I was initially compiling the criteria within the COUNTIFS function, I experienced some confusion around setting a range for goal amounts. While I could filter the campaigns based off of a "greater than" or "less than" statement, I was unsure how to include both (for example, goals greater than or equal to 1000 AND less than or equal to 4999). Since I had already used the range of the column to set up the "greater than" lower bound, I assumed I could not reuse the range for an additional set of criteria. However, after reviewing the course material, I recalled the course activity that used nested IF functions to define ranges for grades (https://richmond.bootcampcontent.com/Richmond-Boot-Camp/UR-VIRT-DATA-PT-11-2022-U-B/-/blob/main/01-Excel/1/Activities/02-Stu_GradeBook/Solved/GradeBook_Solved.xlsx). By repeating this activity, I was able to determine that applying multiple sets of criteria to the same range was appropriate, and therefore the syntax of =COUNTIFS(Kickstarter!D:D,"<=9999",Kickstarter!D:D,">=5000" should generate results for all campaigns falling within the range.

## Results

#### What are two conclusions you can draw about the Outcomes based on Launch Date? ####
1. Theater campaigns like Louise's are far more likely to be successful when launched in May and June. Starting a campaign in December is not advisable, since this month has the lowest records of successful campaigns.
2. Overall, theater campaigns are more likely to be successful than not successful. In all months throughout the year, the number of successful campaigns exceeds the number of failed or canceled fundraising attempts.

#### What can you conclude about the Outcomes based on Goals? ####
1. When the fundraising goals of plays were less than $20,000, they were more likely to be successful. Setting a goal within this range is advised.
2. When the goals ranged between $20,000 and $35,000, a higher percentage of these campaigns failed. This further supports the previous advice to set a goal below $20,000.
3. The lines on this graph are mirror images of one another because all play campaigns either succeeded or failed.

#### What are some limitations of this dataset? ####
While we are examining patterns of correlation within this data set, we must be careful in assuming causality. It is possible that there are other factors that go into a campaign's success. For example, success of plays may vary significantly by overall genre of play, country of origin, region of the country, or intended venue. In addition, we lack information about marketing techniques that each of these campaigns used, if they targeted new or old donors, if they supplemented their kickstarter page with social media campaigns or cold calls, etc. Any of these variables not captured by the data set could have been incremental in the success of these campaigns, and further research would be needed to draw conclusions.   
In addition, the subcategory of campaigns being examined, plays, lacked data for campaigns that were canceled, so we are unable to draw conclusions about common trends for plays that have canceled their fundraisers. 

#### What are some other possible tables and/or graphs that we could create? ####
To provide context of overall success rates of plays, it could be helpful to create a stacked column chart displaying the total number of successful, failed, and canceled campaigns for theaters and plays. 
Because it would be helpful to have more information about the type of donor targeted for campaigns, it may also be beneficial to create a table similar to the "Outcomes Based on Goals" layout that describes the outcomes based on the number of donors and average donation. Do successful campaigns tend to target wealthier donors, or crowdfund from a mass amount of small donations? The answers to these questions would help inform marketing strategies. 
