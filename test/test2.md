
# Building a Survey Reporting Dashboard

Google Analytics includes a number of tools that allow individuals and teams to capture and analyze different types of data. These tools are especially valuable when it comes to survey-based user research.

This guide will walk through the integration of Google Forms, Google Sheets, and Google Data Studio in order to visualize a set of user survey data.

The example described includes connecting a Google Form to Google Sheets, cleaning a set of data within a Worksheet, and finally, building a data report in Google Data Studio.

For more detailed guidance, please see [Additional Resources](https://www.hackforla.org/guide-pages/survey-reporting-dashboard-guide#additional-resources).

## Link Google Form To Google Sheets
 - Link your survey results to a designated Google Sheets workbook

## Select Response Destination - *Click the vertical elipsis located at the top right of the survey form*

![img1](https://www.hackforla.org/assets/images/guides/survey-reporting/dashboard-0.png)

<p align="center">
  <img  src="https://www.hackforla.org/assets/images/guides/gray-arrow.svg">
</p>


## SELECT RESPONSE DESTINATION
![img2](https://www.hackforla.org/assets/images/guides/survey-reporting/dashboard-1.png)

<p align="center">
  <img  src="https://www.hackforla.org/assets/images/guides/gray-arrow.svg">
</p>

## SELECT EXISTING SPREADSHEET
![img3](https://www.hackforla.org/assets/images/guides/survey-reporting/dashboard-2.png)

<p align="center">
  <img  src="https://www.hackforla.org/assets/images/guides/gray-arrow.svg">
</p>

## SELECT TARGET SHEET
![img4](https://www.hackforla.org/assets/images/guides/survey-reporting/dashboard-3.png)


# Clean Data in Google Sheets

<p align="center">
Clean the data exported by your Google Form to enable proper manipulation in Google Data Studio
</p>


## Format Spreadsheet

Once you have set the response destination for your Google Form to your desired Google Sheets File, your data will be visible in a new worksheet.

1. Choose a short, yet descriptive title for your worksheet. If your spreadsheet contains multiple worksheets, move the new tab to the desired location by dragging and dropping using the tab selector.

2. Format the first row of data. Select the first row, then go to Format -> Text Wrapping -> Wrap.

3. Select the first row and set the font to bold. Add a background color to further set the column titles off from the rows of data below.


![img5](https://www.hackforla.org/assets/images/guides/survey-reporting/dashboard-4.png)

## CREATE NEW COLUMNS

Depending on the way your data is structured within a particular column, you will need to insert columns in order to clean your data for processing.

In most cases, where data is formatted as a list within a cell, this can be accomplished through the insertion of 2 new columns to the right of your target column data.

1. Select the target column (‘G’). As a shortcut, select the column that immediately precedes as well (‘F’).

2. In the Go to the Insert menu -> choose ‘2 Columns right.’


![img5](https://www.hackforla.org/assets/images/guides/survey-reporting/dashboard-5.png)

# TITLE NEW COLUMNS
Once you have created your new columns to clean your data, title the new columns the same title as your target column with an appendage, such as “- 1” and “- 2”. This will distinguish your new columns from your target column

![img6](https://www.hackforla.org/assets/images/guides/survey-reporting/dashboard-6.png)

## TRANSPOSE ROW DATA
To create a chart, whether direclty in Google Sheets, or by using a data visualization tool like Google Data Studio, we must have a 1:1 relationship between the data in a particular cell and its dimension (column name). By default, survey questions of the “check all that apply” variety produce data arrays that violate this principle.

We use the TRANSPOSE() function with the SPLIT() and JOIN() functions to achieve this outcome. In our example, we enter the formula =TRANSPOSE((SPLIT(JOIN(“,”, G2:G995), “,”))) in cell H2.

How did we choose G995 as the endpoint of our range? The parameter requires a defined end point; therefore, we arbitrarily choose a cell value beyond which we are certain no future values will be recorded.

![img7](https://www.hackforla.org/assets/images/guides/survey-reporting/dashboard-8.png)

## TRIM DATA

Once we have transposed our data, we must remove any leading or trailing spaces found in every string. We can accomplish this by using the TRIM() function coupled with the ARRAYFORMULA() function.

In our example, we enter =ARRAYFORMULA(TRIM(H2:H)) in cell I2. Why do we use “H” as the endpoint of our range? In this case, the TRIM() permits us to use an undefined endpoint.

![img8](https://www.hackforla.org/assets/images/guides/survey-reporting/dashboard-9.png)

![img9](https://www.hackforla.org/assets/images/guides/survey-reporting/dashboard-9b.png)

# Build Report in Google Data Studio
<p align="center">
Build a report in Google Data Studio using your data in Google Sheets
</p>

