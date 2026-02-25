# Parental Leave Index Project by Matthew Pernes

<img width="1330" height="743" alt="Screenshot 2026-02-22 172056" src="https://github.com/user-attachments/assets/eec59fc9-2127-4e04-bd0e-1c31eeb7e54a" />
<img width="1324" height="738" alt="Screenshot 2026-02-22 172210" src="https://github.com/user-attachments/assets/ac52dce5-0b2c-458b-a614-285d78e1c7b2" />
<img width="1321" height="742" alt="Screenshot 2026-02-22 172405" src="https://github.com/user-attachments/assets/03e45f6f-707d-4df5-8223-5c3bf26b527c" />

Technical Tools Used: Power Query, DAX, Power BI Desktop

Dashboard can be found on [parental_leave_dashboard_pernes.pbix](parental_leave_dashboard_pernes.pbix)

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

*1. Which industries act as the 'Gold Standard' for parental leave, and which are lagging significantly behind?*

The ‘Family Support Score’ equation was used to identify the top three (‘Gold Standard’) and bottom three (lagging) industries for parental leave. The Family Support Score is written in the formula as follows:

Family Support Score = (parental_leave[Avg Paid Maternity Leave] + [Avg Paid Paternity Leave])/2

Top 3 industries: 

<img width="387" height="45" alt="image" src="https://github.com/user-attachments/assets/e659d55c-48f9-44af-8c6b-02bba81c3859" />

Bottom 3 industries:

<img width="382" height="45" alt="image" src="https://github.com/user-attachments/assets/98969411-fce6-4931-9475-e836a3170823" />

The **Telemedicine (Healthcare), Bus (Transportation), and Philanthropy** industries lead the market, offering an average of 27 weeks of paid maternity leave. Notably, this sector also shows 2 months (8 weeks) of paternity leave. 

Conversely, industries such as **Utilities, Foodservice (Hospitality), Agrochemical (Natural Resources)** lag significantly behind, with an average of 1 week paid maternity leave, relying heavily on unpaid leave to meet minimum legal requirements.

---

*2. How does the ratio of Paid vs. Unpaid leave vary across the top-scoring companies?*

<img width="392" height="102" alt="image" src="https://github.com/user-attachments/assets/0589769d-7939-48fc-9f9a-a71588343f8d" />

Companies such as **Grant Thornton, LAC-Group, Flatiron Health, American Income Life, and ASML** rank as the top-scoring companies for leave periods, offering 90+ weeks for parental leave. LAC-Group and American Income Life both offer 50+ weeks of paid parental leave. On the other hand, companies such as Grant Thornton, Flatiron Health, and ASML offer extended unpaid leave beyond their parental absence also offering an average of 27 weeks for paternal leave.

---

*3. What is the 'Paternity Gap' within our dataset, and does a high Maternity score always guarantee a high Paternity score?*

‘Leave Tiers’ were utilized in this analysis to categorize leave durations:

| Tier | Weeks | Description |
| :--- | :--- | :--- |
| Critical Gap | 0-4 weeks | Minimal/lacking support |
| Emerging Standard | 5-12 weeks | Baseline coverage |
| Competitive | 13-26 weeks | Strong Support |
| Market Leading | 27+ weeks | High-tier social support |

A donut chart was used to analyze the leave tiers created for maternity and paternity leaves respectively:

<img width="444" height="359" alt="image" src="https://github.com/user-attachments/assets/b52055b5-fc4d-446d-a739-5eee9fd13772" />

While the Maternity Donut Chart shows a healthy percentage of companies offering 58% in the "Emerging Standard” (5-12 weeks) tier, the Paternity Donut Chart is heavily weighted (90%) toward the Critical Gap, 0-4 weeks category.

<img width="431" height="352" alt="image" src="https://github.com/user-attachments/assets/b819df6f-4875-4b8f-bbde-d5af092602e0" />

A high maternity score does not guarantee a high paternity score. Many companies that rank in the top decile (top 20%) for maternity leave still largely offer 0-4 weeks (97%) for paternity leave, indicating a traditional view of caregiving roles.

<img width="429" height="364" alt="image" src="https://github.com/user-attachments/assets/4215acfb-c103-4f7c-a23c-2c2e758864cd" />

Only three companies belong in the ‘Market Leading’ category for both paternity and maternity leave. 

---

*4. Are there specific companies that are 'disrupting' their industry by offering benefits far above their sector average?*

By filtering the data by industry, I identified 'Disruptor' companies like WeWork that offer benefits far exceeding their sector’s average. For example, while the Business industry typically provides only 5 weeks of leave, WeWork offers 14 weeks for maternity leave and 15 weeks for paternity leave. This places them in a much higher benefit tier than their direct competitors. The analysis reveals that these outliers use aggressive parental leave policies as a strategic tool to attract top talent in industries where support is traditionally scarce. 

While other Business companies do offer 48+ weeks for parental leave, this is exclusive only for maternal leave. 

---

*5. Does a high 'Family Support Score' correlate more strongly with the length of leave or the fact that the leave is fully paid?*

<img width="434" height="170" alt="image" src="https://github.com/user-attachments/assets/cb450601-89de-4e0d-8385-d42e94d5a53b" />

<img width="425" height="343" alt="image" src="https://github.com/user-attachments/assets/599b3502-5f60-498f-ba8e-e978d15aa99e" />

In the top 5 industries of Family Support Score, data strongly expresses that most companies offer to pay 80% or more for the leave duration. This high percentage suggests that leading sectors prioritize financial stability for new parents, ensuring that taking leave does not result in a significant loss of household income. Furthermore, this trend creates a competitive 'floor' where any company offering less than 80% pay would likely struggle to attract talent away from these top-tier industries. Ultimately, the data proves that in the most supportive sectors, 'leave' is synonymous with 'paid leave,' rather than just job protection.

## Data Visualization

<img width="1330" height="743" alt="Screenshot 2026-02-22 172056" src="https://github.com/user-attachments/assets/eec59fc9-2127-4e04-bd0e-1c31eeb7e54a" />

My dashboard leads with four primary KPIs: Average Paid Maternity Leave, Average Paid Paternity Leave, Total Company Count, and a custom Family Support Score. These KPIs provide a health check of parental leave across the dataset. The Clustered Bar Chart (Chart 1) and Table (Chart 6) allow for a direct comparison of these metrics by industry, highlighting the "Gold Standard" sectors versus those lagging behind. By visualizing these benchmarks, I identified that top-tier industries don't just offer more time off, but focus on a higher "Gender Score" to ensure support is equitable for all parents.

To uncover the "hidden truth" behind corporate policies, I utilized a 100% Stacked Bar Chart (Chart 2) that visualizes the ratio of paid versus unpaid weeks, exposing which firms offer true financial security. This is supported by Donut Charts (Charts 3 & 4) that categorize companies into tiers, making it easy to see the "Paternity Gap" across the 1,600+ organizations. Finally, the inclusion of a detailed Company Table (Chart 6) and interactive filters allows users to drill down into specific employers, transforming raw data into an actionable tool for job seekers prioritizing family-centric work cultures.

## Proposed Action

Based on the trends identified in this analysis, I propose the following strategic actions for job seekers, corporate leaders, and industry observers:

**For Job Seekers: Look Beyond the "Total Weeks" Headline**

Candidates should utilize the "Paid-to-Unpaid Ratio" identified in this dashboard to evaluate the true value of a benefit package. A 16-week fully paid policy (The "Fully Funded" Model) offers more long-term financial security than a 28-week policy that is 92% unpaid. Priority should be given to "Disruptor" companies in traditional industries who are using progressive leave to differentiate their culture.

**For Corporate Leaders: Close the "Paternity Gap" to Retain Talent**

With 90% of companies still stuck in the "Critical Gap" (0-4 weeks) for paternity leave, there is a massive opportunity for firms to differentiate themselves. Companies looking to improve their "Family Support Score" should prioritize matching paternity tiers to maternity tiers. This not only supports gender equity but prevents the "Motherhood Penalty" by normalizing caregiving across the entire workforce.

**For Industry Benchmarking: Establish an 80% "Pay Floor"**

The data reveals that the most supportive industries (Telemedicine, Philanthropy) have set a competitive floor of 80% salary replacement. To remain competitive in the global talent market, companies in lagging sectors—such as Utilities and Foodservice—must move away from statutory minimums and toward a model that prioritizes financial stability alongside job protection.
