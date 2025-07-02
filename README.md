# PALMORA GROUP HR ANALYSIS
This is where i started my Portfolio Building while taking my Data Analysis class with the Incubator.

## Project Topic: Palmora Group HR Analysis

### Project Overview
This project showcases a comprehensive HR analytics solution developed in Power BI for Palmoria Group, a manufacturing company based in Nigeria, embroiled with issues over internal gender inequality in its 3 regions. By analysing  the company’s HR data we seek to gather enough insights to make reasonable decisions which then enable us to tell compelling stories around our data from the insight gotten and to uncover gender-related insights to support management's decisions.

### Data Sources
The primary source of Data used here is Palmora Data Sale.csv and this is gotten from the company CHRO,.

### Tools Used
- Ms Excel for Data Collection [Download Here](https://www.microsoft.com)
- Power BI [Download Here](https://www.microsoft.com/en-us/download/details.aspx?id=58494)
  - For Data Cleaning
  - For Creating a report
  - For Visualization

### Data Cleaning and Preparation
In the initial phase of the Data cleaning and prepartion.I perform the following actions;
1. Data loading and Inspection
2. Handling missing variables
3. Data cleaning and formating

### Exploratory Data Analysis
EDA involves the exploring of the Data to answer some questions about the Data such as;
- Gender distribution across regions and departments
- Performance ratings based on gender
- Gender pay gap analysis
- Salary band compliance with regulatory thresholds
- Bonus allocation based on employee ratings

### Data Analysis

This where i include some lines of code and the DAX expression i used during my analysis
``` POWER BI/DAX EXPRESSION
Average Rating = AVERAGE('Palmoria Group emp-data'[Rating])
```
```
Average Salary = AVERAGE('Palmoria Group emp-data'[Salary])
```
```
BelowMinimumPay = CALCULATE(COUNTROWS('Palmoria Group emp-data'),'Palmoria Group emp-data'[Salary] < 90000)
```
```
Gender PayGap = VAR MaleSalary = CALCULATE(AVERAGE('Palmoria Group emp-data'[Salary]),'Palmoria Group emp-data'[Gender]
= "Male")VAR FemaleSalary
 = CALCULATE(AVERAGE('Palmoria Group emp-data'[Salary]),'Palmoria Group emp-data'[Gender] = "Female")
RETURN DIVIDE(MaleSalary-FemaleSalary,MaleSalary)
```
```
 PercentBelowMinimum = DIVIDE(CALCULATE(COUNTROWS('Palmoria Group emp-data'),'Palmoria Group emp-data'[Salary]
 < 90000), COUNTROWS('Palmoria Group emp-data'), 0)
```
```
SalaryBand = VAR BandStart =INT('Palmoria Group emp-data'[Salary]/10000) * 10000 VAR BandEnd
= BandStart + 10000 RETURN "$" & FORMAT(BandStart,"#,0") & "-$" & FORMAT(BandEnd,"#,0")
```
```
Bonus Amount = 'BONUS RATE'[Salary] *'BONUS RATE'[Bonus Rate]
```

### Results
- There are more Male gender than Female gender in the 3 Regions(Kaduna,Abuja,Lagos).
Also, there is a relatively balanced Male & Female distribution but 40% of individuals choose not to disclose there gender.
- The Male gender has the Highest Rating(49.7%) than the Female gender(46.22%) and Undisclosed individuals(4.08%).
- From the analysis,there is a gender PayGap in there Locations/Regions and Departments
  |Region|PayGap|Department|                    
  |------|------|----------|                    
  |Lagos|2.79%|Research and Developmemt,Services,Sales,Product Management|                      
  |Abuja|1.64%|Human Resources,Accounting,Services|
  |Kaduna|0.91|Business Development,Marketing,Legal|
- The analysis shows that Total Count of employee earning below minimum pay is 567,which gives 68.07% of people earning below $90,000. Thereforw,Palmora does not meet this requirement.
- The SalaryBand by the Employee are as follow;
   |Salary Band|EmployeeCount|
   |-----------|-------------|
   |$10,000|Zero|
   |$20,000|21|
   |$30,000|91|
   |$40,000|89|
   |$50,000|84|
   |$60,000|87|
   |$70,000|102|
   |$80,000|91|
   |$90,000|82|
   |$100000|89|
   |$110,000|90|

![4  PAY DISTRIBUTION BY REGION](https://github.com/user-attachments/assets/2ae1d687-d0cd-49fe-acc9-1ccd5b10d46e)

- The total bonus paid out per regions is $161.96M

### Visualizations

![1  GENDER DISTRIBUTION](https://github.com/user-attachments/assets/dba0d66f-e464-4611-8529-6e6389aa9f49)

![2  RATING BASED ON GENDER](https://github.com/user-attachments/assets/18961e73-2633-4f28-9072-8c5efbb6e636)

![3b  PAYGAP BY REGION   DEPARTMENT](https://github.com/user-attachments/assets/5baccbf5-42d0-4286-aecc-84aeb73091ea)
![3c  GENDER PAYGAP](https://github.com/user-attachments/assets/94c4fe83-d47a-4f05-abc3-4600f20998f8)

![5 RATING BONUS](https://github.com/user-attachments/assets/4cf6b452-5410-403e-a791-54a33c391968)
![5b chart](https://github.com/user-attachments/assets/53faeae4-6273-4a1f-8491-ce491ea9d586)

### Recommendations
Based on the analysis,i recommend the following actions;
 - Top performance should recieve more noticeable rewards"Excellent" than  "very good","good" or "average". There is need for unified performance appraisal training.
 - There need to balanced up the paygap amount genders and the department affected.
 - There need for Bonus Automation which is the use of Business Intelligent( That is, implementing power BI Dashboard to automate bonus calculation and reporting,thereby reducing manual errors and saving HR time.
 - Strategically reallocation of bonus within the Regions to match performance with compensation to avoid being bais.

### Limitations
I had to remove Null values from the department and salary column and also replaced the empty column in the gender column with matching values like "Undisclosed" because they would have affected the accuracy of my calculation from the analysis. Also, duplicates values were removed to ensure accuracy.
