<h1 align="center">AWS Project 1</h1>


# Project Description: Implementation and Analysis of Animal Control Data
* This project involves setting up a comprehensive data analytics platform using AWS services to manage the City of Vancouver’s animal control data.

## Project Title: AWS Data Analytic Platform for the City of Vancouver - Part 1
* This project goal was to streamline data sourcing, storage, cleaning, transformation, and analysis, all while maintaining high standards of data security and governance. The platform was built with a focus on handling large datasets, securing sensitive information, and providing real-time insights through data visualization.
## Project Objective:
* The objective of this project is to design and implement a secure AWS-based Data Analytics Platform (DAP) for processing and analyzing the City of Vancouver’s Animal Control Lost and Found inventory data. The platform ensures data protection, efficient processing, and the provision of actionable insights to assist city officials in better managing animal-related cases.
## Methodology:
* The process of DAP designing and implementation is as follows.
### 1. Data Analytical Question Formulation
Key analytical questions driving the project include:
- What are the trends in lost and found animals over the years?
- Which breeds or colours are most commonly reported as lost or found?
### 2. Data Discovery
- The data is sourced from external datasets. For example, the dataset for animal control inventory lost and found is accessed via an open data portal. This involves identifying and accessing relevant datasets that will be used for analysis.
![Screenshot 2024-08-23 151933](https://github.com/user-attachments/assets/af3367e1-e511-4357-b16f-02047df47c06)

### 3. Storage Design
The storage design phase involves setting up a system to efficiently store and manage the data. 
- **Raw Bucket**: Stores raw, unprocessed data.
- **Staging Bucket**: Holds preliminary processed data after basic cleaning.
- **Curated Bucket**: Contains final cleaned and transformed data, ready for analysis. 
![Screenshot 2024-08-23 152757](https://github.com/user-attachments/assets/3b65d36f-f35b-4991-bb20-a43e420f5ecf)

### 4. Data Preparation
- AWS DataBrew was employed to cleaning and transforming the data to ensure  that there is no null values, correcting data formats, and eliminating unnecessary data points.
![databrew project creation](https://github.com/user-attachments/assets/ff1a64b0-0503-4f3a-bd96-23053af83f96)


### 5. Data Injection
- Once cleaned, the cleaned data is transferred into the designated storage location, such as a raw data bucket for further processing.
![raw job output for  2024](https://github.com/user-attachments/assets/58abb425-d4d6-4572-b531-2f47d6e6bd88)
![raw job output for  2023](https://github.com/user-attachments/assets/ca504498-9b47-43dd-9d9f-0c7be3397cdd)


### 6. Data Pipeline Design
- AWS Glue is used to create the data pipeline, automating the ETL process.
- The data pipeline is designed to facilitate the smooth flow and transformation of data throughout the system.
![ETL](https://github.com/user-attachments/assets/38404349-da8e-4234-8140-73577f838f5e)

### 7. Data Cleaning
- Data cleaning involves removing any inconsistencies or errors in the data to improve its quality. and was free of null or incomplete entries. 
![Screenshot 2024-08-23 153336](https://github.com/user-attachments/assets/973bff0b-8e64-4b4c-b58b-be2bcd285d22)

### 8. Data Structuring
- Data is organized in a way that aligns with the analytical questions being addressed, making it easier to analyze.
![Screenshot 2024-08-23 150716](https://github.com/user-attachments/assets/f73d8421-7f52-44a0-aa5c-3c3c9fe1fe79)

### 9. Data Pipeline Implementation
- AWS Glue Jobs were set up to ensure the data was properly transformed and loaded into the final S3 Curated bucket for analysis.
- The data pipeline is implemented to ensure data is processed and loaded correctly, using tools like AWS Glue.
![image](https://github.com/user-attachments/assets/33f5b481-cd4a-4506-94e4-7e2a2a84317a)
![image](https://github.com/user-attachments/assets/0162ae05-d76f-4ed0-946c-b267f3bac78f)

### 10. Data Analysis
- AWS Athena was utilized to execute SQL queries on the structured data. An example query used in the project is:
![Querry](https://github.com/user-attachments/assets/c4aa7940-2e9c-4df2-acf0-547e448b943d)

- This query helped retrieve information on found animal differnece in 2023 and 2024

### 11. Data Visualization
- Based on the output data recorded from the table created a data visualization where it show the difference in the year the number of found animal in year 2024 and 2023.
![image](https://github.com/user-attachments/assets/5d49a1be-057f-499d-91eb-031dc3c793c1)
### 12. Data Publishing
- The final step involves publishing the analysis results, making them accessible to stakeholders through a server setup like AWS EC2. This rewritten version maintains the original content's meaning while using different wording and structure.
![image](https://github.com/user-attachments/assets/2b9c68de-290c-4a65-b5ac-80fe67a138c7)








