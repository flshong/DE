# Cloud Data Warehouses

Sharpen your data warehousing skills and deepen your understanding of data infrastructure. Create cloud-based data warehouses on Amazon Web Services (AWS).

## Build a Cloud Data Warehouse



## Steps:

1) Configuration setup - Fill the dwh.cfg with the necessary information to start a redshift cluster
2) Run create_redshift_cluster - Run this jupyter notebook and create the cluster
3) Run create_tables.py - Use this python file to drop and create tables
4) Run etl.py - Run this python file to create the etl pipeline to insert data into the created tables.
5) Run test_analytics.py - This python file to run some basic analytical queries.

#### Don't forget to run the last steps in the jupyter notebook to delete the cluster.


## How to run

1. To run this project you will need to fill the following information, and save it as *dwh.cfg* in the project root folder.

```
[CLUSTER]
HOST=''
DB_NAME=''
DB_USER=''
DB_PASSWORD=''
DB_PORT=5439

[IAM_ROLE]
ARN=

[S3]
LOG_DATA='s3://udacity-dend/log_data'
LOG_JSONPATH='s3://udacity-dend/log_json_path.json'
SONG_DATA='s3://udacity-dend/song_data'

[AWS]
KEY=
SECRET=

[DWH]
DWH_CLUSTER_TYPE       = multi-node
DWH_NUM_NODES          = 4
DWH_NODE_TYPE          = dc2.large
DWH_CLUSTER_IDENTIFIER = 
DWH_DB                 = 
DWH_DB_USER            = 
DWH_DB_PASSWORD        = 
DWH_PORT               = 5439
DWH_IAM_ROLE_NAME      = 
```

2. Create a python environment with the dependencies listed on *requirements.txt*
awscli==1.16.140
boto3==1.9.164
botocore==1.12.164
pandas==0.23.4
psycopg2==2.7.7
psycopg2-binary==2.8.2
3. Run the *create_cluster* script to set up the needed infrastructure for this project.

    `$ python create_cluster.py`

4. Run the *create_tables* script to set up the database staging and analytical tables

    `$ python create_tables.py`

5. Finally, run the *etl* script to extract data from the files in S3, stage it in redshift, and finally store it in the dimensional tables.

    `$ python create_tables.py`


## Project structure

This project includes five script files:

- analytics.py runs a few queries on the created star schema to validate that the project has been completed successfully.
- create_cluster.py is where the AWS components for this project are created programmatically
- create_table.py is where fact and dimension tables for the star schema in Redshift are created.
- etl.py is where data gets loaded from S3 into staging tables on Redshift and then processed into the analytics tables on Redshift.
- sql_queries.py where SQL statements are defined, which are then used by etl.py, create_table.py and analytics.py.
- README.md is current file.
- requirements.txt with python dependencies needed to run the project