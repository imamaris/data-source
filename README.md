# README

## Introduction
This README provides instructions for setting up and running a data ingestion pipeline using Python scripts and Airflow. The pipeline is designed to initiate the ingestion of raw data, process it, and store it in a specified database. Follow the steps below to set up the environment and execute the pipeline.

## Prerequisites
- Docker installed on your system.
- Python installed on your system.

## Setup Instructions

1. **Environment Configuration:**
   - Copy the `example.env` file and create your own environment configuration file.
   
2. **Initiate Raw Data Ingestion:**
   - Run the Python script `ingestion.py` to initiate the ingestion of raw data.

3. **Start Airflow:**
   - Run `docker compose up airflow-init` to initialize Airflow.
   - Once initialization is complete, start the Airflow services by running `docker compose up`.

4. **Database Credentials:**
   - After starting Airflow, your database is created with the following credentials:
     - Username: `airflow`
     - Password: `airflow`

5. **Access Airflow Web Interface:**
   - Navigate to Airflow homepage at [http://localhost:8080/](http://localhost:8080/).
   - You will be prompted to login. Please use the following credentials:
     - Username: `airflow`
     - Password: `airflow`

6. **Update DAG Configuration:**
   - In the Airflow web interface, locate the DAG named `analisis_report_dags`.
   - Update the database connection information in the DAG configuration:
     ```
     DB_USERNAME = '<DB_USERNAME>'
     DB_PASSWORD = '<DB_PASSWORD>'
     DB_HOST = '<DB_HOST>'
     DB_NAME = '<DB_NAME>'
     PORT = '<PORT>'
     ```

7. **Database Schema:**
   - Ensure that your database schema matches the following:
     ```
     transaction_amount_absolute numeric
     running_total numeric
     transaction_frequency integer
     transaction_volume integer
     average_transaction_amount numeric
     amount numeric
     high_value_transaction_indicator boolean
     balance_amount numeric
     month integer
     date date
     value_date date
     day_of_week character varying
     transaction_type character varying
     transaction_details character varying
     cheque_number character varying
     account_no character varying
     transaction_category character varying
     transaction_trend_monthly character varying
     ```

8. **Shutdown Airflow:**
   - To shutdown Airflow and clean up resources, run:
     ```
     docker compose down --volumes --remove-orphans
     ```

## Reference
For more detailed instructions on setting up Airflow with Docker, you can refer to the article [Hello World Airflow Docker](https://medium.com/@prithvijit.guha245/hello-world-airflow-docker-9102f4c5305b).

## Conclusion
You have now successfully set up the data ingestion pipeline using Python scripts and Airflow. You can customize the pipeline and extend its functionality as needed. If you encounter any issues or have questions, please refer to the documentation or contact the system administrator.

# Mini Application

## Installation
First, you'll need to install necessary packages. Run the following command:

```bash
pip install -r requirements.txt
```

## Setup Instructions

- Before running the application, make sure to configure your own database connection parameters. Modify the following variables in the main.py file:
     ```
     DB_USERNAME = '<DB_USERNAME>'
     DB_PASSWORD = '<DB_PASSWORD>'
     DB_HOST = '<DB_HOST>'
     DB_NAME = '<DB_NAME>'
     PORT = '<PORT>'
     ```

## Running the Application
- You can run this API application using Uvicorn. Execute the following command:
```bash
uvicorn main:app --reload
```
