# IBM Db2 Production Data Warehouse
> Using the adjusted schema design in prior module, create an instance of IBM DB2 and load the sample datasets into their respective tables. Write aggregation queries and create a Materialized Query Table for future reports.

# 1. Prepare an Instance of IBM DB2
First I will create the following tables and load their respective datasets.

- `DimDate`
- `DimCategory`
- `DimCountry`
- `DimItem`
- `FactSales`
# 2. Aggregation Queries
The first aggregation query will be a `GROUPING SETS` query using the columns `country`, `category`, and `totalsales`

![groupingsets](https://github.com/rupamdusane/IBM-Data_Engineering_Capstone_Project/assets/92736419/e6ef01cf-bf0c-47b9-a0e0-22b27a92ceeb)


Next I will write a `ROLLUP` query using the columns `year`, `country`, and `totalsales`

![rollup](https://github.com/rupamdusane/IBM-Data_Engineering_Capstone_Project/assets/92736419/ad42fc2f-b1bb-4833-9f1c-e97b8eb2bca9)


Finally, I will write a `CUBE` query using the columns `year`, `country`, and `averagesales`

![cube](https://github.com/rupamdusane/IBM-Data_Engineering_Capstone_Project/assets/92736419/3cbae528-6ac9-47f3-9b92-e148fcf70378)


# 3. Materialized Query Table (MQT)
I will create an MQT named `total_sales_per_country` based on the columns `country` and `totalsales`

![mqt](https://github.com/rupamdusane/IBM-Data_Engineering_Capstone_Project/assets/92736419/9e5db73c-dc8c-4cb5-942e-c1af4334e701)


# About This Lab
Environment/IDE
This portion of the project will be using the Cloud IDE based on Theia and an instance of DB2 running in IBM Cloud.

# Tools/Software
- Cloud instance of IBM DB2 database
