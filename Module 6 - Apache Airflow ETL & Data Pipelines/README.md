# Apache Airflow ETL & Data Pipelines
> SoftCart has imported web server log files as `accesslog.txt`. Write an Airflow DAG pipeline that analyzes the log files, extracts the required lines and fields, transforms and loads the data to an existing file.

# Overview
Airflow DAGs uses Python scripts to automate ETL pipelines. I will be writing a script called `process_web_log.py` that extracts web server log data, filters out a specified IP address, and loads the new data into a log file `weblog.tar`.

# 1. Load Dependencies
This script will be using the `airflow` library along with the `bash_operator` for executing commands and `datetime` for specifying date/time fields.
```ruby
from airflow import DAG
from airflow.operators.bash_operator import BashOperator
import datetime as dt
```
# 2. Define the DAG Arguments
I will start by configuring the DAG with the following arguments:

- Owner
- Start Date
- Email

```ruby
default_args = {
  'owner': 'Rupam Dusane',
  'start_date': dt.datetime(2023,2,14),
  'email': ['rupam@somemail.com'],
}
```

# 3. Define the DAG
The DAG id will be labeled `process_web_log` and will be scheduled to run daily.
```ruby
dag=DAG(
  'process_web_log',
  description='SoftCart access log ETL pipeline',
  default_args=default_args,
  schedule_interval=dt.timedelta(days=1),
)
```
# 4. Task Definitions
The first task `extract_data` will use the `BashOperator` to cut all IP adddresses from `accesslog.txt` and output them into a new file `extracted_data.txt`.

```ruby
extract_data = BashOperator(
  task_id='extract_data',
  bash_command='cut -f1 -d" " $AIRFLOW_HOME/dags/capstone/accesslog.txt > $AIRFLOW_HOME/dags/capstone/extracted_data.txt',
  dag=dag,
)
```
After extraction, `transform_data` will remove all instances of the IP `198.46.149.143` and output the remaining list into `transformed_data.txt`.

```ruby
transform_data = BashOperator(
  task_id='transform_data',
  bash_command='grep -vw "198.46.149.143" $AIRFLOW_HOME/dags/capstone/extracted_data.txt > $AIRFLOW_HOME/dags/capstone/transformed_data.txt',
  dag=dag,
)
```
The `load_data` task will archive the contents of `transformed_data.txt` into a .tar file named `weblog.tar`.

```ruby
load_data = BashOperator(
  task_id='load_data',
  bash_command='tar -zcvf $AIRFLOW_HOME/dags/capstone/weblog.tar $AIRFLOW_HOME/dags/capstone/transformed_data.txt',
  dag=dag,
)
```

# 5. Define the Task Pipeline
```ruby

extract_data >> transform_data >> load_data

```

# Final DAG Script process_web_log.py
```
# Library Imports
from airflow import DAG
from airflow.operators.bash_operator import BashOperator
import datetime as dt

# DAG Arguments
default_args = {
  'owner': 'Rupam Dusane',
  'start_date': dt.datetime(2023,2,14),
  'email': ['rupam@somemail.com'],
}

# DAG Definition
dag=DAG(
  'process_web_log',
  description='SoftCart access log ETL pipeline',
  default_args=default_args,
  schedule_interval=dt.timedelta(days=1),
)

# Task Definitions
extract_data = BashOperator(
  task_id='extract_data',
  bash_command='cut -f1 -d" " $AIRFLOW_HOME/dags/capstone/accesslog.txt > $AIRFLOW_HOME/dags/capstone/extracted_data.txt',
  dag=dag,
)

transform_data = BashOperator(
  task_id='transform_data',
  bash_command='grep -vw "198.46.149.143" $AIRFLOW_HOME/dags/capstone/extracted_data.txt > $AIRFLOW_HOME/dags/capstone/transformed_data.txt',
  dag=dag,
)

load_data = BashOperator(
  task_id='load_data',
  bash_command='tar -zcvf $AIRFLOW_HOME/dags/capstone/weblog.tar $AIRFLOW_HOME/dags/capstone/transformed_data.txt',
  dag=dag,
)

# Task Pipeline
extract_data >> transform_data >> load_data
```

# 6. Submit the DAG
To submit the DAG, I will use the following command:

```ruby

cp process_web_log.py $AIRFLOW_HOME/dags

```
I can use `airflow dags list` along with `grep` to confirm the submission of our new DAG.
```

airflow dags list | grep 'process_web_log'

```
>```
>process_web_log.py | me | True

# 7. Unpause the DAG
To run the DAG, I have to unpause it using either the Airflow UI or the following command:

```

airflow dags unpause process_web_log

```
>```
>Dag: process_web_log, paused: False


# 8. Trigger and Test the DAG
Before I can successfully run the DAG, I will change the permissions of the working directory.
```

sudo chmod 777 /home/project/airflow/dags/capstone

```
Finally, I can use `airflow dags trigger` to run the DAG.
```

airflow dags trigger process_web_log

```
>```
>Created <DagRun process_web_log @ 2023-02-14T05:42:50+00:00: manual__2023-02-14T05:42:50+00:00, externally triggered: True>


# About This Lab
Environment/IDE
To complete this lab, we will be using the Cloud IDE based on Theia and Apache Airflow running in a Docker container.

# Tools/Software
- Apache AirFlow
