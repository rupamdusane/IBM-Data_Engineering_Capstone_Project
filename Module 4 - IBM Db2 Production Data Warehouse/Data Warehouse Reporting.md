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


Next I will write a `ROLLUP` query using the columns `year`, `country`, and `totalsales`


This query produces the following output (first 10 rows). The full output can be viewed here: `rollup_data.csv`


Finally, I will write a `CUBE` query using the columns `year`, `country`, and `averagesales`


This query produces the following output (first 10 rows). The full output can be viewed here: `cube_data.csv`


# 3. Materialized Query Table (MQT)
I will create an MQT named `total_sales_per_country` based on the columns `country` and `totalsales`



# About This Lab
Environment/IDE
This portion of the project will be using the Cloud IDE based on Theia and an instance of DB2 running in IBM Cloud.

# Tools/Software
- Cloud instance of IBM DB2 database
