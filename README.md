# healthcare-data-analysis
This project demonstrates the use of Amazon Redshift Serverless and Amazon S3 to analyze healthcare data efficiently. The dataset includes patient records, and the goal is to load, filter, and retrieve patient information, specifically identifying diabetic cases using SQL queries.

## Step 1: Create a table for storing healthcare data
CREATE TABLE healthcare_data (
    patient_id INT,
    patient_name VARCHAR(255),
    age INT,
    diagnosis VARCHAR(255),
    admission_date DATE
);

## Step 2: Load data from Amazon S3 using COPY command ##
COPY healthcare_data
FROM 's3://your-bucket-name/healthcare_data.csv'
IAM_ROLE 'arn:aws:iam::your-role-id:role/RedshiftAccess'
CSV
IGNOREHEADER 1;

![Screenshot (19)](https://github.com/user-attachments/assets/ef959bc2-41ee-4862-870f-0bfffc495c92)



## Step 3: Query to filter diabetic patient records ##
SELECT * FROM healthcare_data
WHERE diagnosis = 'Diabetes';

## Step 4: Count the number of diabetic cases
SELECT COUNT(*) AS diabetic_cases FROM healthcare_data
WHERE diagnosis = 'Diabetes';

![Screenshot (20)](https://github.com/user-attachments/assets/1fc55507-9082-4329-bca8-4ed4db168631)



