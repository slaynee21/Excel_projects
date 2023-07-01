# data_cleaning_excel

This data cleaning project focuses on a dataset of data science job posts scraped from Glassdoor's website. The dataset contains information about job titles, salary estimation, job descriptions, ratings, companies, locations, headquarters, company size, type of ownership, industry sector, revenue, salary details, job states, same state as headquarters, company age, required skills, job type, and seniority.

# Cleaning Steps:

Delete Index: Remove any index column that is unnecessary for analysis.

Delete Rows with Invalid Location: Identify and remove any rows with invalid or missing location information.

Extract Minimum Salary: Use the formula "=VALUE(LEFT(B2,FIND("-",B2)-1))" to extract the minimum salary from the "Salary Estimation" column.

Extract Maximum Salary: Use the formula "=VALUE(RIGHT(B2,LEN(B2)-FIND("-",B2)))" to extract the maximum salary from the "Salary Estimation" column.

Calculate Average Salary: Use the formula "=AVERAGE(P2,Q2)" to calculate the average salary based on the extracted minimum and maximum salary values.

Extract State: Use the formula "=RIGHT(G2,2)" to extract state from the "Location" column.

Check if Job Location is Same as Headquarters: Use the formula "=IF(EXACT(S2,RIGHT(H2,2)),1,0)" to determine if the job location is the same as the headquarters. This creates a Boolean column indicating the result.

Calculate Company Age: Use the formula "=YEAR(TODAY())-J2" to calculate the age of the company based on the "Headquarter" column.

Check if Required Skill (Python) is Present: Use the formula "=IF(ISNUMBER(SEARCH($V$1, $D2)), 1,0)" to check if the required skill "Python" is present in the "Job Description" column. This creates a Boolean column indicating the result.

Categorize Job Types: Use the formula "=IF(ISNUMBER(SEARCH("Scientist",A2)),"Data Science",IF(ISNUMBER(SEARCH("Machine",A2)),"MLE",IF(ISNUMBER(SEARCH("Analyst",A2)),"Data Analyst","NA")))" to categorize the job types based on the "Job Title" column. This creates a new column with categories such as "Data Science," "MLE" (Machine Learning Engineer), "Data Analyst," or "NA" (Not Applicable).

Identify Senior Positions: Use the formula "=IF(ISNUMBER(SEARCH("Senior",A2)),1,IF(ISNUMBER(SEARCH("Sr",A2)),1,0))" to identify if a job title includes "Senior" or "Sr," indicating a senior position. This creates a Boolean column indicating the result.

