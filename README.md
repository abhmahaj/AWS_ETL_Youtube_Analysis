# AWS_ETL_Youtube_Analysis
ETL Data Pipeline in Python on YouTube Data using Athena, Glue and Lambda.

Architecture
<img width="836" alt="image" src="https://github.com/abhmahaj/AWS_ETL_Youtube_Analysis/assets/53664559/ad52278c-fbb1-43bc-83fd-36d734cb7bf3">

Dataset Understanding:
The project centers around an ETL (Extract, Transform, Load) pipeline using Python on the AWS platform, focusing on the Kaggle YouTube video dataset. This dataset encompasses up to 200 trending videos daily for various locations, with each region having its file. The dataset includes essential information such as video title, channel title, publication time, tags, views, likes, dislikes, description, comment count, and a region-specific category ID.

AWS S3 Bucket Creation:
To kick off the ETL pipeline, the initial steps involve creating an AWS S3 account, establishing an IAM user/admin with necessary permissions and MFA device assignment. Following this, the AWS CLI is installed, and user credentials are entered. The Kaggle YouTube video dataset is downloaded and loaded into the AWS S3 bucket, adhering to best practices outlined in the official AWS documentation.

AWS Glue Catalog Creation:
The project proceeds to create an AWS Glue Catalog, serving as a central data repository. This involves importing data from the S3 bucket using a crawler, performing ETL tasks with AWS Glue ETL and SQL queries using Athena. The AWS Glue Catalog is configured to automatically discover and catalog data in the S3 bucket, enabling seamless data querying and analysis. The semi-structured JSON data is transformed for SQL queries using Athena's SerDe libraries.

AWS Lambda Data Pipeline:
The ETL process is extended using AWS Lambda, where a function extracts JSON data from the raw S3 bucket, converts it to Parquet format, and catalogues it into the Glue Catalog. The Lambda function utilizes essential libraries like AWS Data Wrangler and Pandas for efficient data manipulation. Data is stored in a new S3 bucket for organized data management.

Data Processing Using AWS Glue:
Leveraging AWS Glue's Spark ETL jobs feature, the project demonstrates the transformation of data from JSON to Parquet format. The Glue Spark job processes and transforms data in the cleansed S3 bucket, creating a new table in the Glue Catalog. An S3 trigger is added to the Lambda function for automated processing of new incoming JSON files, enhancing data organization.

Data Materialization Using AWS Glue Studio:
The analytics layer is introduced to provide a materialized view of the cleansed data, optimizing cost and performance. This involves creating a new S3 bucket, configuring IAM policies, and using Glue Studio to perform a join operation on Parquet format datasets. The results are stored in an S3 bucket for viewing through Athena SQL statements.

Data Visualization Using AWS QuickSight:
The final phase focuses on data visualization using AWS QuickSight. A new ETL workflow in Glue Studio is created to automate the transformation of raw JSON data to Parquet format and SQL Join outputs to materialized views in the Analytics database. QuickSight datasets are then generated, allowing the creation of customizable dashboards for in-depth data visualization.
