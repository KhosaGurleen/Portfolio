# Gurleen Kaur Khosa - Portfolio
Project 1: Business Licence (Part 1)
HomeAll ProjectsCertificationsBadges
   Descriptive Analysis
   Project Description: Establishing AWS DAP for The City of Vancouver(Descriptive Analysis of Business licences issued per year)

   Project Title: DAP Design and Implementation for City of Vancouver(Business Licences in Downtown Vancouver)

   Objective: The City of Vancouver is in an advantageous place where the proper use of data can further improve decision-making, public services, and usage of resources. The establishment of the Data Analytic Platform (DAP) is essential for the city because it provides a foundation for the integration, processing, and visualization of a massive amount of data received from different sources. Through this platform, city officials can make the right decisions for the city's betterment by considering the analyzed data on the people’s quality of living, improved service delivery, and enhanced city planning.

   Dataset:Business licences data retrieved from city of Vancouver (open data portal) for year 2024 and 2023. The dataset includes the following key features:

   RSN, Licence Number, Licence Revision Number, Business Name, Business Trade Name, Status, Issued Date Expired Date, Business Type, Business SubType, Unit, Unit Type, House, Street, City, Province, Country, Postal Code, Local Area, Number of Employees, Fee Paid, Extract Date

![(DAP Part 1) dataset](https://github.com/user-attachments/assets/8bf1ff8f-7f5e-4756-a2ea-f8ede37dd9e0)


   Methodology:

   To be able to implement and migrate a data analytic platform of The City of Vancouver to the AWS, we have designed and implemented based on the 13 steps below:
Step 1: Data Analytic Question Formulation:

This step shows a breakdown of the data analysis process to improve business licence issuance and compliance in Downtown Vancouver. It starts with a high-level goal and breaks it down into different steps.

Descriptive Metric: The first step is to understand the current situation. This involves analyzing data on the number of business licenses issued per year. How many business licenses are issued per year?
Diagnostic Metric: The next step is to identify the reasons for business license delays. This can be done by analyzing data about the reasons for the delay. Why are there delays in issuing licenses?
Predictive Metric: The goal here is to predict the likelihood of a business license renewal. This can be done by analyzing data about past renewal patterns and other factors that might influence renewals. How likely is a business license to be renewed?
Prescriptive Metric: Finally, the goal is to recommend proactive actions to improve renewal reminders. This involves analyzing data about successful reminders and developing new ways to ensure businesses are reminded about their licence renewal. How can we remind businesses about license renewals?

Sorry for the Inconvenience
Step 2: Data Discovery

Data discovery is about finding, understanding, and organizing data to set the stage for deeper analysis and informed decision-making. It involves data collection which means gathering data from various sources, such as databases, files, or external sources and then analyzing the collected data to understand its structure, quality, and content.

Sorry for the Inconvenience
Step 3: Data Storage Design

In this step, we need to store our operational data in an analytical environment using S3 service in AWS. To do this, firstly, we need to create a bucket for our data storage in S3. Bucket is a place where we store objects and object could be anything be it excel file, pdf, image, json file etc.

Bucket Created: business-businesslicences-gurleen
Organize by year: Inside the bucket, created folders for each year ("2023/Landing," "2024/Landing")
Created folders for specific data: Within each year folder, made more folders for different types of data, like “business licences application records”, “business licences delay logs”, “business licences renewal history”, “business licences compliance data”, “business licences renewal reminder logs”, “process efficiency metrics” inside the “landing folder”

Finally, uploaded the dataset files into those relevant folders. This helps keep data organized and easy to find later.

Sorry for the Inconvenience	Sorry for the Inconvenience
Sorry for the Inconvenience	Sorry for the Inconvenience

Step 4: Data Preparation

Data Preparation is basically preparing or arranging your data from various sources to achieve your business goal which in my case was Business licences data retrieved from city of Vancouver (open data portal) for year 2024 and 2023.
Sorry for the Inconvenience	Sorry for the Inconvenience
Sorry for the Inconvenience


Step 5: Data Ingestion

Data Ingestion involves uploading your data inside your AWS bucket in specific folders. As in my case, uploading my excel and pdf files into their relevant folders. For instance, business licences application records.xlsx for Business Licences Application Records folder of my business bucket and so on.

Sorry for the Inconvenience	Sorry for the Inconvenience

Step 6: Data Storage

Data storage is an essential step in data analytics platforms. It involves storing the collected data into folders of S3 buckets for efficient access and analysis. After gathering data from open data portal, it is then stored to the landing environment of S3.

Sorry for the Inconvenience
Step 7: Data Pipeline Design

The Data Pipeline design step is about planning how data will travel through the system, from where it starts to where it ends up. This includes deciding how data will be collected, processed, changed, and stored. The aim is to make sure data moves smoothly and is ready for analysis. I created visual representation of my ETL pipeline in draw.io using tables showing various stages of my design such as removing, filtering, extracting and grouping stage and then finally, reaching to my final outcome table showing “Licence Issuance Rate” calculations for year 2024 and 2023.

Sorry for the Inconvenience	Sorry for the Inconvenience
Sorry for the Inconvenience	Sorry for the Inconvenience
Sorry for the Inconvenience


Step 8: Data Cleaning

In this step cleaned up the dataset of business licences application records in an AWS S3 bucket. The steps involve creating raw folder inside landing zone and and then using a data cleaning tool called AWS Glue DataBrew, I created a project. The project then cleaned the data by removing invalid, null or missing values using function feature inside it depending upon the percentage of missing values in the column, which will ensure the accuracy of any future analysis performed on the data. If had more than 80% missing values, I dropped that column because it was of no use.

Sorry for the Inconvenience	


Step 9: Data Structuring

In this step, I arranged my data in structured manner meaning renamed columns names with relevant names with respect to the information they hold in them. Furthermore, I configured “Schema” in AWS Glue DataBrew to ensure whether my dataset had relevant datatypes for specific columns and if not changes them accordingly. Furthermore, I created and ran my job and stored the result of my cleaning and structuring inside the raw folder of my S3 bucket.

Sorry for the Inconvenience	Sorry for the Inconvenience
Sorry for the Inconvenience	Sorry for the Inconvenience



Step 10: Data Pipeline Implementation

This step involves creation of visual ETL using AWS Glue service. This step provides us with the summarized information for our analysis. In this step, I fetched data from my raw folder (cleaned and structured data) and then performed certain operations to that dataset to extract specific information. I used aggregation, filter and change schema to retrieve specific information from my dataset. Then I used to join function to group my dataset and performed average calculation on my dataset to get “Licence Issuance Rate” for year 2024 and 2023 using columns “Number of business licence issued per year” and “Total number of business licence applications initiated”. Licence Issuance Rate = (Number of business licence issued per year/ Total number of business licence applications initiated) *100 Finally, I run my job, and my results were stored in the curated folder of my S3 bucket.

Sorry for the Inconvenience	Sorry for the Inconvenience
Sorry for the Inconvenience	Sorry for the Inconvenience
Sorry for the Inconvenience	Sorry for the Inconvenience
Sorry for the Inconvenience


Step 11: Data Analysis

The AWS service used for executing this step is Amazon Athena. This step involved analyzing the summarized curated folder data from S3 bucket by creating tables for specific CSV files. The table contained columns such as Year and LIR (Licence Issuance Rate) for the years 2023 and 2024. After table creation, I ran SQL queries to retrieve specific information from the table using SQL “ORDER BY”, “SELECT” and various other queries.

Sorry for the Inconvenience	Sorry for the Inconvenience
Sorry for the Inconvenience	Sorry for the Inconvenience


Step 12: Data Visualization

In this step, I created visualizations for my Athena downloaded data file for Licence Issuance Rate containing 2024 and 2023 data. I made my visualizations for this step in excel using recommended charts and then downloaded that file in pdf format and renamed it as Graph_Report.

Sorry for the Inconvenience	Sorry for the Inconvenience


Step 13: Data Publishing

AWS EC2 service was used to execute this step. This step involved publishing your data files to general and web servers to be accessible by the public. To do this step, I created two EC2 instances, one for general server and another one for web server. For connecting my instances, I used “Remote desktop connection” inbuild software in windows and uploaded my files to remote computer in analysis folder in C-Drive for general server and in wwwroot folder for web server and then using public IP address, I accessed my uploaded files on the web browser.

Sorry for the Inconvenience	Sorry for the Inconvenience
Sorry for the Inconvenience	Sorry for the Inconvenience
Sorry for the Inconvenience


DAP Estimated Cost

To estimate the cost of the dataset preparation phase for the above-listed projects using the AWS pricing calculator, we broke down the services used and their respective costs. The services in use include Amazon S3, AWS Glue, Amazon Athena, and Amazon EC2.
Amazon Simple Storage Service (S3)
Storage Used: 527.9 GB per month
Cost Estimate: 12.14 USD per month
AWS Glue
DPUs Used: Number of DPUs for Apache Spark job (10) and Number of DPUs for Python Shell job (5)
Cost Estimate: 0.14 USD per month
Amazon Athena
Queries and Data Scanned: Total number of queries (7 per month), Amount of data scanned per query (varies)
Cost Estimate: 9.99 USD per month
Amazon EC2
Instance Types: t2.micro
Cost Estimate: 12.21 USD per month
Total Estimated Cost for Dataset Preparation Phase:
Monthly Cost: 17.54 USD
Total 12 Months Cost: 210.48 USD


Sorry for the Inconvenience   This descriptive analysis project aims analyzing data on the number of business licenses issued per year.
