# Tracking & Reporting

This README provides an overview of the tasks related to building a data flow for tracking and reporting using historical weather data. The objective is to demonstrate the technical ability to set up the data flow using various tools and technologies.

## Project Summary

This task involves building a representative dataflow to demonstrate technical proficiency in data processing. A fictional and nonsensical weather report has been selected as the dataset for this purpose. The goal is to showcase the ability to construct a dataflow.

## Task Steps
* Export historical weather data (last 7 days) for the cities of Hamburg, Berlin, and Munich using a Google Cloud Function from a weather API. Save this data in Google BigQuery.
* Utilize dbt (https://www.getdbt.com/) to create a reporting view containing the following data:
  * Cumulative average temperature for the cities of Berlin, Hamburg, and Munich.
  * Cumulative average precipitation amount for the cities of Berlin, Hamburg, and Munich.
  * Devise a fantasy score for the weather in each of the 3 cities (non-cumulative) and calculate it.
* Develop a dashboard in Google Looker Studio that presents the values over time for weather fantasy score, temperature, and precipitation amount.

Through these steps, the task aims to demonstrate the construction of a dataflow, integrating data collection, transformation, and visualization using tools like Google Cloud, dbt, and Looker Studio.

## Task Workflow

**Task 1: Setting Up BigQuery Database and Table**

Before exporting historical weather data from the weather API, you need to set up the required BigQuery database and table to store the data.

Steps:
1. *Create a BigQuery Project*:
* If you don't already have one, create a project in Google Cloud Console and enable the BigQuery API.
2. *Create a Dataset*:
* Inside your project, create a new dataset to organize your weather data.
3. *Design the Table Schema*:
* Define the schema of the table that will hold the historical weather data. This schema should match the structure of the data you'll retrieve from the weather API. For example:
```
city (STRING)
date (DATE)
temperature (FLOAT)
precipitation (FLOAT)
... (other relevant fields)
```
4. Create the Table:
* Using the defined schema, create a new table within your dataset to store the historical weather data.

![GCP Table Schema](https://github.com/d-kleine/gcp_dbt_challenge/blob/main/gcp_schema.png)

**Task 2: Export of Historical Weather Data**

With the BigQuery database and table set up, you can now proceed to export historical weather data from the weather API and store it in BigQuery using a Google Cloud Function.

Steps:
1. *Set up a Google Cloud Function*:
* Create a new Google Cloud Function project.
* Configure the necessary permissions and authentication for accessing the weather API.
2. *Fetch and Transform Data*:
* Write a function to fetch historical weather data for the specified cities from the weather API.
* Transform and format the data to match the schema of the BigQuery table you've created.
3. *Insert Data into BigQuery*:
* Utilize the BigQuery API to insert the transformed weather data into the appropriate table within your dataset.

![GCP Function](https://github.com/d-kleine/gcp_dbt_challenge/blob/main/gcp_function.png)
![GCP BigQuery](https://github.com/d-kleine/gcp_dbt_challenge/blob/main/gcp_table_preview.png)

**Task 3: Create Reporting-View with dbt**

In this task, you will use *dbt* (data build tool) to create a reporting view containing aggregated data.

Steps:
1. *Set Up dbt Cloud IDE*:
* Access dbt Cloud IDE and create a new project.
2. *Define Models and Transformations*:
* Create dbt models to aggregate and calculate the required metrics using the data in your BigQuery table.
3. *Execute dbt Run*:
* Run the dbt transformation process to build the reporting view.

![dbt yml](https://github.com/d-kleine/gcp_dbt_challenge/blob/main/dbt_yml.png)
![dbt sql](https://github.com/d-kleine/gcp_dbt_challenge/blob/main/dbt_sql.png)
![dbt GCP export](https://github.com/d-kleine/gcp_dbt_challenge/blob/main/gcp_dbt_aggtable.png)

**Task 4: Create Dashboard in Google Looker Studio**

In this task, you will create a dashboard using Google Looker Studio to visualize the weather data metrics over time.
Steps:

1. *Set Up Looker Studio*:
* Access Google Looker Studio and create a new dashboard project.
2. *Create Visualizations*:
* Design visualizations to display the metrics calculated by dbt over time.
3. *Configure Data Sources*:
* Connect Looker Studio to Google BigQuery and ensure access to the dbt-created reporting view.
4. Build Dashboard:
* Assemble the visualizations into a coherent dashboard layout and configure any necessary filters and date ranges for interactive exploration.

![Google Looker Vis](https://github.com/d-kleine/gcp_dbt_challenge/blob/main/looker_vis.png)
