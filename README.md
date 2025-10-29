# AWS Core Services Hands-On: S3, IAM, Glue, CloudWatch, and Athena

This project demonstrates how to use several core AWS services to ingest data, catalog it, and query it using a serverless architecture.  
The dataset used in this hands-on is an e-commerce sales dataset from Kaggle.

---

## Project Architecture Workflow
Local CSV → S3 Bucket → Glue Crawler → Data Catalog → Athena Queries


---

## Steps Completed

### 1. **Created an S3 Bucket**
- Uploaded the raw CSV dataset to the S3 bucket.
- Configured public access settings to *block public access*.
- Stored processed query results in a separate `processed/` folder within the same bucket.

### 2. **Created an IAM Role**
- Created a new IAM Role for AWS Glue.
- Attached **AmazonS3FullAccess** and **AWSGlueServiceRole** policies.
- Assigned this role to the Glue crawler.

### 3. **Configured AWS Glue Crawler**
- Created a Glue Crawler pointed to the S3 raw data folder.
- Used the IAM Role from Step 2.
- Ran the crawler to populate the AWS Glue Data Catalog.
- Verified table schema was correctly inferred.

### 4. **Monitored Job Using CloudWatch**
- Used CloudWatch log groups to verify the crawler run and check for errors.

### 5. **Queried Data in Amazon Athena**
- Selected the database created by the Crawler.
- Ran the required queries (see below).
- Saved results as CSV and uploaded to this repository under `/results`.

---

## Athena Queries Used

> All queries were executed with `LIMIT 10`.

1. **Cumulative Sales Over Time (Running Total for a Year)**  
2. **Geographical Hotspots for Unprofitable Products**  
3. **Discount Impact on Profitability by Sub-Category**  
4. **Top 3 Most Profitable Products per Category (Window Function)**  
5. **Monthly Sales & Profit Growth Analysis (MoM Window Function)**  


## Key Takeaways

| AWS Service | Key Purpose |
|------------|------------|
| **S3** | Stores raw and processed data files. |
| **IAM** | Controls access permissions for services. |
| **Glue Crawler** | Automatically detects schema and builds metadata catalog. |
| **CloudWatch** | Monitors job execution and logs. |
| **Athena** | Performs SQL queries directly on data stored in S3. |

---

## Screenshots

CloudWatch
<img width="959" height="539" alt="image" src="https://github.com/user-attachments/assets/00fcf7cc-d24d-4628-8827-76435ed72b24" />

IAM role
<img width="959" height="539" alt="image" src="https://github.com/user-attachments/assets/e874302b-afa7-43cf-99ec-552cc0899f22" />

S3 Buckets
<img width="959" height="539" alt="image" src="https://github.com/user-attachments/assets/7fa0ec0c-c10f-420d-b62a-088dbca50682" />
