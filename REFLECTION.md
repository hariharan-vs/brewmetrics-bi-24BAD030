# Reflection

GitHub Copilot was useful throughout the development of the BrewMetrics Business Intelligence project, particularly during the creation of DAX measures. Instead of writing every measure from scratch, Copilot provided initial DAX suggestions that could then be reviewed and tested in Power BI.

The project included four main measures: Month-over-Month Sales Growth, Running Total Sales, City Sales Rank, and Average Transaction Value. Copilot helped explain the purpose of functions such as CALCULATE, DATEADD, FILTER, ALL, ALLSELECTED, RANKX, and DIVIDE. Reviewing the generated DAX was important because the suggestions still needed to be checked against the actual data model and reporting requirements.

One important model consideration identified during the process was the structure of the Dim_Date table. Since the date dimension was created from distinct sales dates rather than a continuous calendar, this could affect some time-intelligence calculations. The issue was documented rather than changing the working measures unnecessarily.

Git and GitHub also improved the development process. Each major stage was committed separately, making it possible to track the star schema, individual DAX measures, and final dashboard independently. This provided a clear development history and made changes easier to review.

Overall, the combination of Power BI, GitHub, and Copilot made the BI development process more structured and easier to document.