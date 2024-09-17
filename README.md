# AWS-ETL-Pipeline
---
Data Engineering Project Pipeline that incorporates AWS IAM, Amazon S3, AWS Glue, Amazon Athena, and Amazon QuickSight. This pipeline covers the entire flow from data ingestion to visualization, highlighting the role of AWS IAM in securing the process.
---
## Pipeline Architecture
![Sportify ETL data pipeline Architecture](https://github.com/user-attachments/assets/687dff18-cff7-4371-ad51-b2c3f013eb82)
---
## Data Source
Kaggle Spotify Dataset 2023 - (https://www.kaggle.com/datasets/tonygordonjr/spotify-dataset-2023)
---
## **Steps**

### 1. **AWS IAM (Identity and Access Management)**
- **Purpose**: Manage access and permissions for AWS services.
- **Actions**:
  - Create IAM roles and policies to control access to:
    - **S3 Buckets** (staging and data warehouse).
    - **Glue Jobs** and **Crawlers**.
    - **Athena** and **QuickSight**.
  - Ensure least privilege access for security compliance.

### 2. **Staging Layer - Amazon S3**
- **Purpose**: Store raw data before processing.
- **Actions**:
  - Ingest data from source (sportify dataset)
  - Apply IAM policies to restrict access to the staging layer.

### 3. **ETL Process - AWS Glue**
- **Purpose**: Extract, Transform, Load (ETL) data from the staging area to data warehouse.
- **Actions**:
  - **Create Glue Jobs**:
    - Write ETL scripts using Pyspark to transform data.
    - Create a visual ETL, run and monitor ETL (Pspark scripts)
    
      ![Sportify ETL Visual](https://github.com/user-attachments/assets/71216815-c840-4c82-a344-41deb7442531)

      
  - **Use Glue Crawlers**:
    - Automatically discover and categorize data in S3.
    - Create a **database** in the Glue Data Catalog.
    - Populate a **table** for the database based on the crawled data.
  - Ensure that Glue has the necessary IAM permissions to access S3.

### 4. **Data Warehouse - Amazon S3**
- **Purpose**: Store processed data for querying and analysis.
- **Actions**:
  - Move transformed data to a new S3 bucket intended for the data warehouse (e.g., `/data/warehouse/`).
  - Store data in optimized formats (e.g., Parquet) for better performance.
  - Control access to the data warehouse using IAM policies.

### 5. **Querying Data - Amazon Athena**
- **Purpose**: Query the data stored in S3 using SQL.
- **Actions**:
  - Use the Glue Data Catalog to reference the database and tables created.
  - Write SQL queries to analyze data efficiently.
  - Ensure IAM permissions allow Athena to access the data in S3.

### 6. **Data Visualization - Amazon QuickSight**
- **Purpose**: Create visualizations and dashboards.
- **Actions**:
  - Connect QuickSight to Amazon Athena as a data source.
  - Design interactive dashboards to visualize query results.
  - Share insights with stakeholders through reports and dashboards.
  - Set IAM permissions for users accessing QuickSight and the underlying data.

## Summary of Key Components
| **Component**        | **Purpose**                                     | **Tools**        |
|----------------------|-------------------------------------------------|------------------|
| **Secure Access**    | Manage access and permissions                   | AWS IAM          |
| **Staging Layer**    | Store raw data                                  | Amazon S3        |
| **ETL Process**      | Transform and load data                         | AWS Glue         |
| **Data Warehouse**   | Store processed data                            | Amazon S3        |
| **Querying**         | Query data using SQL                           | Amazon Athena     |
| **Visualization**     | Create dashboards and reports                   | Amazon QuickSight |

This pipeline effectively integrates **AWS IAM** to ensure secure access while managing data through various stages from ingestion to visualization. 
