# Parental Leave Index Project by Matthew Pernes

<img width="1330" height="743" alt="Screenshot 2026-02-22 172056" src="https://github.com/user-attachments/assets/eec59fc9-2127-4e04-bd0e-1c31eeb7e54a" />
<img width="1324" height="738" alt="Screenshot 2026-02-22 172210" src="https://github.com/user-attachments/assets/ac52dce5-0b2c-458b-a614-285d78e1c7b2" />
<img width="1321" height="742" alt="Screenshot 2026-02-22 172405" src="https://github.com/user-attachments/assets/03e45f6f-707d-4df5-8223-5c3bf26b527c" />

Technical Tools Used: Power Query, DAX, Power BI Desktop

## Table of Contents

1. The Problem
2. Our Goal
3. Data Preparation
4. Data Analysis
5. Data Visualization
6. Proposed Action

## The Problem

Job seekers and career shifters often lack the transparency needed to compare parental leave benefits across different companies and industries before accepting an offer. This information gap creates significant financial and professional risk for families who must make major career decisions without knowing if their employer truly supports parental leave or gender equity. This project addresses the lack of accessible, comparative data by transforming policy information into a clear, actionable tool for the public.

This project aims to answer 5 questions:

1. Which industries act as the 'Gold Standard' for parental leave, and which are lagging significantly behind?
2. How does the ratio of Paid vs. Unpaid leave vary across the top-scoring companies?
3. What is the 'Paternity Gap' within our dataset, and does a high Maternity score always guarantee a high Paternity score?
4. Are there specific companies that are 'disrupting' their industry by offering benefits far above their sector average?
5. Does a high 'Family Support Score' correlate more strongly with the length of leave or the fact that the leave is fully paid?

*Note: To see the answers for the questions above, jump immediately to the ‘Data Analysis’ section.*

## Our Goal

The primary goal of this project is to build a Power BI dashboard that empowers job seekers to make data-backed career decisions based on family-leave transparency. By analyzing maternity and paternity data from over 1,601 companies, the dashboard identifies which industries are leading in paid support and gender equality. Ultimately, this project aims to bridge the information gap between employers and the public, helping families choose workplaces that offer both financial security and career balance.

## Data Preparation

Dataset Used In This Project: [https://mavenanalytics.io/data-playground/parental-leave-policies](https://mavenanalytics.io/data-playground/parental-leave-policies)

Description of the dataset:
Crowdsourced parental leave data from 1,601 companies across different industries, including paid/unpaid maternity and paternity leave weeks.

Dataset Dictionary

| Column | Description |
| :--- | :--- |
| Company | Company Name |
| Industry | Company industry & sub-industry (Industry: Sub-Industry) |
| Paid Maternity Leave | Paid weeks off from work for mothers after the birth of their child |
| Unpaid Maternity Leave | Unpaid weeks off from work for mothers after the birth of their child |
| Paid Paternity Leave | Paid Weeks off from work for fathers after the birth of their child |
| Unpaid Paternity Leave  | Unpaid weeks off from work for fathers after the birth of their child |

I prepared this dataset through the following steps:
1. Loaded the dataset in Power Query editor as a csv file.
2. Removed duplicates.
3. Removed fields with empty values unnecessary for the data analysis.
4. Converted nulls (N/A) from several fields (paid/unpaid leave) into “0” for better use in the final calculations of the analysis.
5. Added conditional columns to create tiers (Critical Gap, Emerging Standard, Competitive, Market Leading) for maternity and paternity leaves respectively.
6. Created DAX measures to calculate average paid/unpaid maternity/paternity leaves.
7. Totaled paid and unpaid maternity/paternity leaves to add columns for ‘total protected time off’ for respective categories.
8. Added a ‘Gender Score’ column to identify inequalities by subtracting average paid time off for paternity leaves from average paid time off for maternity leaves.
9. Added a ‘Family Support Score’ which shows the average of maternity and paternity leave in weeks.
10. Constructed a Quick Measure to total the amount of paid weeks and unpaid weeks of all companies for a side by side comparison analysis.
11. Reclassified companies who were previously labelled ‘N/A’ into their respective sectors using manual research and Power Query conditional logic.

## Data Analysis

This section aims to answer the following questions. Answers will be attached below their respective inquiry.

*Which industries act as the 'Gold Standard' for parental leave, and which are lagging significantly behind?*

The ‘Family Support Score’ equation was used to identify the top three (‘Gold Standard’) and bottom three (lagging) industries for parental leave. The Family Support Score is written in the formula as follows:

Family Support Score = (parental_leave[Avg Paid Maternity Leave] + [Avg Paid Paternity Leave])/2

Top 3 industries: <img width="387" height="45" alt="image" src="https://github.com/user-attachments/assets/e659d55c-48f9-44af-8c6b-02bba81c3859" />

Bottom 3 industries:<img width="382" height="45" alt="image" src="https://github.com/user-attachments/assets/98969411-fce6-4931-9475-e836a3170823" />


