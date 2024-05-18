# IBM Data Engineering Capstone Project

In this project, I will take on the role of a Junior Data Engineer at a fictional online e-commerce company named SoftCart. I will tackle real-world use cases, applying industry-standard data engineering solutions.

![data-platform-architecture](https://github.com/rupamdusane/IBM-Data_Engineering_Capstone_Project/assets/92736419/1d0d2892-0da7-41fb-b763-0fab80d058ca)

# Objectives
- Demonstrate proficiency in skills required for an entry-level data engineering role.
- Design and implement various concepts and components in the data engineering lifecycle, such as data repositories.
- Showcase working knowledge with relational databases, NoSQL data stores, big data engines, data warehouses, and data pipelines.
- Apply skills in Linux shell scripting, SQL, and Python programming languages to data engineering problems.

# Project Outline
- SoftCart's online presence is primarily through its website, which customers access using a variety of devices, including laptops, mobiles, and tablets.
- All product catalog data is stored in the MongoDB NoSQL server.
- Transactional data, such as inventory and sales, is stored in the MySQL database server.
- SoftCart's web server relies on these two databases.
- Data is periodically extracted from these databases and loaded into a staging data warehouse running on PostgreSQL.
- The production data warehouse is hosted on a cloud instance of the IBM Db2 server.
- BI teams connect to the IBM Db2 for operational dashboard creation using IBM Cognos Analytics.
- SoftCart uses a Hadoop cluster as its big data platform for collecting analytics data.
- Spark is used to analyze the data on the Hadoop cluster.
- ETL pipelines, running on Apache Airflow, move data between OLTP, NoSQL, and the data warehouse.

# Assignment Briefs
**1. MySQL Online Transactional Processing Database**
SoftCart will use MySQL for online transactional processing, such as storing inventory and sales data. Based on the sample data provided, design the database schema and create a database to store sales data. Create an index on the timestamp column and write an administrative bash script to export sales data into a SQL file.

**2. MongoDB NoSQL Catalog Database**
All of SoftCart's catalog data will be stored on a MongoDB NoSQL server. Create the database catalog and import the electronics products from catalog.json into a collection named electronics. Run test queries against the data and export the collection into a file named electronics.csv using only the _id, type, and model fields.

**3. PostgreSQL Staging Data Warehouse**
Sales data from MySQL and catalog data from MongoDB will be periodically extracted and stored in a staging data warehouse running on PostgreSQL. The data will then be transformed and loaded into a production data warehouse running on IBM Db2 to generate reports such as:

- Total sales per year per country
- Total sales per month per category
- Total sales per quarter per country
- Total sales per category per country

Design a data warehouse star schema using the pgAdmin ERD design tool, ensuring the tables can generate yearly, monthly, daily, and weekly reports. Export the schema SQL and create a staging database. Your Senior Data Engineer will review your schema design. Make any necessary adjustments before moving to the next phase.

**4. IBM Db2 Production Data Warehouse**
Using the adjusted schema design, create an instance of IBM Db2 and load the sample datasets into their respective tables. Write aggregation queries and create a Materialized Query Table for future reports.

**5. Python Scripts & Automation**
SoftCart needs to keep data synchronized between different databases/data warehouses as part of our daily routine. One task routinely performed is syncing the staging data warehouse and production data warehouse. Write a script to automate the process of regularly updating the DB2 instance with new records from MySQL.

**6. Apache Airflow ETL & Data Pipelines**
SoftCart has imported web server log files as accesslog.txt. Write an Airflow DAG pipeline that analyzes the log files, extracts the required lines and fields, transforms the data, and loads it into an existing file.

**7. Apache Spark Big Data Analytics**
Our team has prepared a dataset containing search terms used on our e-commerce platform. Download the data and run analytic queries on it using PySpark and JupyterLab. Use a pretrained sales forecasting model to predict sales for 2023.

# Tools/Software
- OLTP Database - MySQL
- NoSql Database - MongoDB
- Production Data Warehouse – DB2 on Cloud
- Staging Data Warehouse – PostgreSQL
- Big Data Platform - Hadoop
- Big Data Analytics Platform – Spark
- Business Intelligence Dashboard - IBM Cognos Analytics
- Data Pipelines - Apache Airflow

# About This Project
This project is part of the IBM Data Engineering Professional Certificate program, offered by IBM Skills Network and hosted on edX.

Read more: https://www.edx.org/certificates/professional-certificate/ibm-data-engineering?index=product&queryID=be6784a44dd32394ff4deef520818f79&position=8&linked_from=autocomplete&c=autocomplete
