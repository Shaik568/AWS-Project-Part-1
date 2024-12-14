<h1 align="center">AWS Project 1</h1>


# Project Description: Implementation and Analysis of Storefronts Inventory Data
* This project involves setting up a comprehensive data analytics platform using AWS services to manage the City of Vancouver’s Storefronts Inventory data.

## Project Title: AWS Data Analytic Platform for the City of Vancouver - Part 1
* This project goal was to streamline data sourcing, storage, cleaning, transformation, and analysis, all while maintaining high standards of data security and governance. The platform was built with a focus on handling large datasets, securing sensitive information, and providing real-time insights through data visualization.
## Project Objective:
* The objective of this project is to design and implement a secure AWS-based Data Analytics Platform (DAP) for processing and analyzing the City of Vancouver’s Storefronts Inventory data. The platform ensures data protection, efficient processing, and the provision of actionable insights to assist city officials in better managing Stores in different streets.
## Methodology:
* The process of DAP designing and implementation is as follows.
### Data Analytical Question Formulation
Key analytical questions driving the project include:
- List out all the Service commercial Retail stores in different streets
- Calculate the percentage of them and add an additional feature to calculate the average of service commercial retail stores in different streets.
### 2. Data Discovery
- The data is sourced from external datasets. For example, the dataset for Storefronts Inventory is accessed via an open data portal. This involves identifying and accessing relevant datasets that will be used for analysis.
![Screenshot (186)](https://github.com/user-attachments/assets/a35060e0-5642-4eb3-b91e-fb47ae4805e3)


### 3. Storage Design
The storage design phase involves setting up a system to efficiently store and manage the data. 
- **Raw Bucket**: Stores raw, unprocessed data.
- **Staging Bucket**: Holds preliminary processed data after basic cleaning.
- **Curated Bucket**: Contains final cleaned and transformed data, ready for analysis. 
![Screenshot (188)](https://github.com/user-attachments/assets/18528ea8-fbfd-4c58-9840-545a1d471e7c)


### 1. Data Ingestion
Key analytical questions driving the project include:
- 1.	What is the rate of animals found Lost in the year 2024 and add an Average for count of Lost animals feature additionally to support your analysis.
- First we need to create a bucket in S3 and put the raw data inside it which we get from City of Vancouver.
![Screenshot (187)](https://github.com/user-attachments/assets/7f340d5d-9b29-4259-b7e3-5c1ae15424c9)



- Raw, transformed and curated Data have been created in a new bucket in Aws at respective folder locations. Now let us push the dataset into the raw folder generated on the bucket described earlier.
![Screenshot (188)](https://github.com/user-attachments/assets/1208a6e5-033f-4413-885b-d1bb758fab4f)

- Figure 3
![Screenshot (189)](https://github.com/user-attachments/assets/8525e62d-e146-4ef5-8709-01a65813137c)







### 2. Data Profiling
Shown below is the data profiling and cleaning which we perform to store the new transformed data in the new transformed bucket
![Screenshot (190)](https://github.com/user-attachments/assets/37effb8d-2bb3-4806-ac5c-82938d3f7725)





After ingestion we are going to focus on data profiling which will indicate to the summary of our data set any missing value or any relation that we can explore. To accomplish this first it will be necessary to develop a new transform bucket for all of this information. Then we have to navigate to AWS Glue Data brew, there we will have to create a new dataset wherein the data profiling will be run to get all the profiling data required for cleaning the data. 
![Screenshot (191)](https://github.com/user-attachments/assets/04782cf5-4745-427a-8ce5-879dc3a7fc5a)


- Result of profiling from the dataset

![Screenshot (192)](https://github.com/user-attachments/assets/22fec508-e16b-484a-af6a-55125795e8ad)




### 3. Data Cleaning
- When we complete doing the profiling there are certain irregularities we have to correct and can easily discern from the results of profiling.
 We make a project from the dataset and in this project all type of rules of data cleaning should be applied to make out data and to generate a new recipe.

![Screenshot (193)](https://github.com/user-attachments/assets/7b34ee7c-cf37-4a8e-a7ec-bc47500f3e5e)




After creating a recipe for your data you need to create a job and run it.
Inside the job you need to specify the type of output and where to store it.
We use 2 types of output one is for user in a csv format which is user friendly and second is in Parquet format which is system friendly.


![Screenshot (194)](https://github.com/user-attachments/assets/8b5f10f1-2e0b-4973-8721-7c0eb0d1b163)




Cleaned system data

![Screenshot (195)](https://github.com/user-attachments/assets/00b70d7a-8dbb-4d98-abff-d25e70e8cfad)


New cleaned data for user folders


![Screenshot (196)](https://github.com/user-attachments/assets/387ad22f-a3ba-485e-976b-9046aada5a5f)



### 4. Data Pipeline Design
- AWS Glue is used to create the data pipeline, automating the ETL process.
- Finally, after carrying out the data profiling and data cleaning steps; we have our final transformed data which have no null or invalid value in it. Now we are ready in the next step of our descriptive analysis part where our task first is to find out in percentage how many Stores are Service Commercial Retail and secondly to look them individually on the basis of type.
Count of Commercial Stores = (svr_comer_count/ right_Total_Category_count)*100
We find that it is necessary to obtain the percentage of count of animals lost. Now let it be our turn to design our Day 2 ETL pipeline to help answer this question.
- Draw.io diagram for the whole process until the ETL pipeline implementation


![Screenshot (197)](https://github.com/user-attachments/assets/f7e00986-c1e5-4df7-aa3d-88ef82b176e7)



Now we need to go to AWS Glue and start building our visual ETL pipeline
1.	Extract the parking tickets data from cleaned data folder in S3 bucket.
2.	Transformed the schema of the table by Dropping Extra Column from the table.
3.	Then we have divided the pipeline in 2 parts: one with the filtered data & another  one with total data.
4.	Then we put a filter transformation in which we filter out the count of Stores that were found Service Commercial.
5.	Then we transform it by aggregating the retail stores and then grouping it bystreet name.
6.	Then we rename the aggregated column as “Retail_Count” to make it more suitable for our analysis.
7.	On the other hand we aggregate the total number of Service Commercial Retail Stores and Total Retail Stores.
8.	Then we rename the aggregate column as “right_Total_Count” to make it more suitable for our analysis.
9.	Then we again rename the join key by adding the right_ as a prefix before joining.
10.	Then we merge the data sets as an outer join to include all the cells.
11.	Then we transform the data to calculate the % of count of animals found Matched count through (svr_comer_count/svr_comer_count)*100
12.	Now we load the data for separate types one for user in csv format and one for system in Parquet format.
13.	Then we save and run the pipeline.


- The data pipeline is designed to facilitate the smooth flow and transformation of data throughout the system.


![Screenshot (198)](https://github.com/user-attachments/assets/a38a891a-2a19-48fe-858e-0aa66103204a)



- The job for storing the ETL pipeline result


![Screenshot (199)](https://github.com/user-attachments/assets/e70e8b7e-974e-4a1b-9c09-d7d47c5a5623)



### 5. Exploratory Analysis
- In the exploratory analysis we are calculating the average of Count of Service Commercial Retail Stores that were found in different localities.
Let’s go through the steps for the exploratory analysis.
- Step 1: Data Ingestion
Same as the one we did above for descriptive analysis.
- Step 2: Data Profiling
Same as descriptive analysis
- Step 3: Data Cleaning
This step is like what we did for out descriptive analysis.
- Step 4: Data Pipeline Design
After doing the data profiling and data cleaning we have our final transformed data which is cleaned and does not have any null or invalid values in it. Now we can perform our descriptive analysis part in which we need find out how many Service Commercial Retail Stores have been recorded, also to see the average individually based on there types.
Average = (Matched_count/Total_State_Count)/ 2
Now we need to create the alterations for our ETL pipeline to answer this question.
- Draw.io diagram for the whole process until the ETL pipeline implementation


![Screenshot (200)](https://github.com/user-attachments/assets/ca03ec28-e3b9-40b7-83a9-21da70dd75bd)


- The average we got after running the pipeline is 0.5
Below is the ETL Visual Pipeline:
- Second ETL pipeline implementation


![Screenshot (201)](https://github.com/user-attachments/assets/36bf1fc5-62db-4b8a-8db5-e103be0c1c17)



- Second job for storing the ETL pipeline result


![Screenshot (202)](https://github.com/user-attachments/assets/32aae1a2-1e11-4614-a530-83d50258b39f)


- Result: The calculated average of Servicew Commercial Retail counts relative to the total inventory was 0.5
### Conclusion
- The project successfully implemented descriptive and exploratory analyses using AWS services, including S3, Glue DataBrew, and Glue ETL pipelines. The calculations provide insights into the rate of Service Commercial Retail Stores and facilitate further datadriven decisionmaking for Storefronts Inventory Management.

### DAP Estimated Cost
-The AWS Pricing Calculator gives an accurate estimate of cost of a number of AWS services out of the many available. Or if you want to observe a scenario for a single user the cost computed for a monthly operation is approximately $1.43
![Screenshot (78)](https://github.com/user-attachments/assets/0d4a4185-f850-444c-9eba-bad042fa78b7)
