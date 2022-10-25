# HR_Analytics
_Capstone projecct_
# Introduction 

This is my capstone project for the #OUIBOOTCAMP by REPOTECH. The objective is to analyze a manufacturing group (Palmoria) HR database to discover issues bordering on gender inequality in its 3 regions across Nigeria. 
The documentation will include:
- Statement of Problem
- Objective 
- Data Cleaning 
- Data Preprocessing 
- Data Modelling 
- Data Analysis and Visualization 
- Recommendations

# Statement of Problem 
The Palmoria Group, a manufacturing company based in the Nigeria is embroiled in issues bordering on gender inequality in its 3 regions. Unfortunately, the media recently published in the news with the headline “Palmoria, the Manufacturing Patriarchy” This doesn’t look good for the owners of the business based on their ambition to scale the business to other regions and even overseas. Cases like this can only spiral downwards revealing other issues like gender pay gap amongst other possible issues.

My mission is to analyze the company’s HR Database to identify:

👉🏾 key areas within the business that could spring up issues 

👉🏾 Come up with recommendations for management’s attention 

👉🏾 Give a breakdown of the Salary details.

Upon handed this task the CEO told me.... 

_“Now, the future of gender equality in Palmoria lies in your hands”_


# Objective 
<details><summary>More</summary>
 
-	What is the gender distribution in the organization? Distil to regions and departments
-	Show insights on ratings based on gender
-	Analyze the company’s salary structure. Identify if there is a gender pay gap. If there is, identify the department and regions that should be the focus of management
-	A recent regulation was adopted which requires manufacturing companies to pay employees a minimum of $90,000 - Does Palmoria meet this requirement? 
-	Show pay-distribution of employees grouped by a band of $10,000. For example: How many employees fall into a band of $10,000 – $20,000, $20,000 – $30,000 etc. Also visualize this by regions
-	Calculate the amount to be paid as bonus to individual employees
-	Calculate the total amount to be paid to individual employees (salary inclusive of bonus) 
-	Total amount to be paid out per region and company-wide
</details>

# Data Cleaning 
<details><summary>More</summary>
This process was carried out on PowerBi desktop, the datasets were imported into power query. The following cleaning process was carried out
- Promotion of headers
- Removal Null values 
- Removal of leading spaces
- Removal of duplicate values
- Removal of values not useful for analysis based on an insider hint this include, employees without salary because they are no longer staff, and department that indicated null.
- I made sure each column has the right data type 
- I checked for the validity of my data using the column distribution, quality, and profiling from the view tab. 

![image](https://user-images.githubusercontent.com/108795960/192598573-96e3a5c2-8d2d-42d9-bed6-3c8d6286bd5d.png)
</details>
 
# Data Preprocessing 
<details><summary>More</summary>
The first thing I carried out at this stage was to give a unique ID to each employee to preserve the privacy of each employee, employee whose gender was not disclosed was given a generic gender name “Unspecified”. 
I also did a merge of the two datasets “emp-data and Bonus rules” so as assign each employee their corresponding rating and calculated the bonus value each employee received based on their rating and their department. 

 - Using data analysis expression (DAX), I created two new measures to calculate if the company meets the manufacturing regulation minimum requirements

- _For salary less than 90000_
```
Salary>90000 = CALCULATE(DISTINCTCOUNT('Insight'[Employee ID]),FILTER(VALUES(Insight[Employee ID]),CALCULATE(SUM('Salary structure'[Basic Salary]))>90000))
```
- _For Salary greater than 90000_
```
Salary<90000 = CALCULATE(DISTINCTCOUNT('Insight'[Employee ID]),FILTER(VALUES(Insight[Employee ID]),CALCULATE(SUM('Salary structure'[Basic Salary]))<90000))
```
![image](https://user-images.githubusercontent.com/108795960/192600833-6d731baf-024c-4739-b78b-ed4366a18db1.png)

Before loading the data model, I made sure that only tables that were needed for visualization and analysis were loaded into the data model. 
</details>

 # Data Model
<details><summary>More</summary>
The data model Contains two tables which are Insight and Salary structure 
- The insight table contains: Employee ID, Gender, and Region 
- Salary structure contains Employee ID, Department, Basic salary, Bonus value, Total salary (Basic salary plus Bonus value).
- A one-to-one relationship was created between the two tables 

 ![image](https://user-images.githubusercontent.com/108795960/192601742-a1cf1b33-904a-4812-b24d-fe4c168fc66e.png)       
</details>

# Data Analysis and Visualization 

<details><summary>More</summary>
 
 - **Employee distribution by gender and region** 
 
There are 943 active employees on the company database, which shows that there are 24 male employees than female employees while the total number of the unspecified gender is 39. The region distribution also shows that Kaduna has more employees across the region with Lagos being the lowest. Consequently, total pay by region 
follows this same trend from Kaduna-Lagos.

![image](https://user-images.githubusercontent.com/108795960/192602811-fca82213-6923-4e85-b89e-0c1057025c19.png)
![image](https://user-images.githubusercontent.com/108795960/192603012-149bd7aa-8349-4f8e-a650-a5bb420f5c99.png)

- **Gender Distribution by Department** 
 
The result of the analysis indicates that there are more males in 7 of the 12 departments within the organization while the departments where female employees were more dominant are strategic departments within the organization.

![image](https://user-images.githubusercontent.com/108795960/192603146-194dc7e1-cafa-4aba-8904-3fc6de0f2ef3.png)

- **Gender Insight by Rating** 
 
There was more female in the top-rated categories than the other gender, it was also revealed from the analysis that more employee falls in the average category which is dominated by the male gender as well as the two least rated category. of the total 39 employees of the unspecific gender, 50% are rated average. 

![image](https://user-images.githubusercontent.com/108795960/192603236-cace9f1d-0920-49ad-94bf-26b4773b85f0.png)

- **Salary structure Gap by Gender**
 
Obvious gender gaps were observed in Accounting, Human Resources, and marketing with Unspecified earning more while the gap in Business Administration and Product Management department are more tended towards the male and female genders for the entire company. 

![image](https://user-images.githubusercontent.com/108795960/192603321-da9fe839-08cc-4dbc-9610-d5f514d5bc6f.png)

- **Regulatory Minimum Requirement**
 
A regulation that directs all manufacturing companies to pay a minimum of $90000 to its employee, the analysis shows that 69% of the company’s workforce are paid below the stipulated minimum amount 

![image](https://user-images.githubusercontent.com/108795960/192603392-4b6ce1f9-85f0-48aa-9738-bbf89f9f9e19.png)
</details>

# Recommendations 

• The analysis was able to determine that there were more male employees in the company in Lagos and Kaduna which is a tip to the regions where the alarm for patriarchy claims might be springing from that requires the immediate attention of the company in these regions 

• Rating insight and department distribution shows that more female gender occupy the top-rated category and more female employee are in top departments within the manufacturing company, something the company should also investigate before it escalates 

• Though the Unspecified gender constitutes a minute of the company’s employees, analysis of salary-shows they earn more in more than 50% of departments which is more pronounced in Kaduna.

[View Dashboard Here]([https://github.com/theadewole/HR_Analytics/blob/main/HR_Analystic%20Dashboard%20Page%201.png](https://app.powerbi.com/view?r=eyJrIjoiODcyMjA1MGMtMGJmNC00NTE1LWI2YzktNzZmMmQ5ZjliNjAwIiwidCI6IjA4MmY1ZjZjLWRmYmEtNGFiZS04M2Q1LTEzZmU1MWIzZTc2OSJ9&pageName=ReportSection2746c5225dfefd5b8c08)) 


