# GBQ Performance and Consumption SpotApp

SpotApps are ThoughtSpot’s out-of-the-box solution templates built for specific use cases and data sources. They leverage ThoughtSpot Modeling Language (TML) Blocks, which are pre-built pieces of code that are easy to download and implement directly from the product.

The GBQ Performance and Consumption SpotApp mimics the GBQ data model. When deployed, it creates several Worksheets, Answers, and Liveboards based on your GBQ data in your cloud data warehouse.

Use the GBQ Performance and Consumption SpotApp to manage GBQ costs and consumption, tracking how and where consumption of slots and bytes are processed.

## Prerequisites

Before you can deploy the GBQ Performance and Consumption SpotApp, you must complete the following prerequisites:

- **Review Required Data**: Examine the required tables and columns for the SpotApp.
- **Ensure Column Compatibility**: Ensure that your columns match the required column type listed in the schema for your SpotApp.
- **Sync Data**: Synchronize all tables and columns from GBQ to your cloud data warehouse. Although you can choose to sync only the required tables and columns, ThoughtSpot recommends syncing all tables and columns from GBQ to your CDW, including GBQ’s out-of-the-box columns or any custom columns you are using.
- **Collaborate on Data Movement**: If using an ETL/ELT tool or working with another team within your organization, sync all columns from the tables listed in the SpotApp.
- **Obtain Credentials**: Obtain credentials and SYSADMIN privileges to connect to GBQ. Your cloud data warehouse must contain the data ThoughtSpot will use to create Answers, Liveboards, and Worksheets. Refer to the connection reference for GBQ for detailed information about required credentials.
- **Unique Connection Name**: Each new SpotApp connection name must be unique.
- **Administrator Access**: Ensure administrator access to GBQ on console.cloud.google.com for the project and to IAM for creating roles and service accounts.
- **Access to GBQ Tables and Worksheets**: Ensure access to the following GBQ tables and Worksheets in your cloud data warehouse:
  - `JOBS_BY_PROJECT` (table)
  - `GBQ: JOB TIMELINE BY PROJECT` (Worksheet)

### Run SQL Commands

Execute the following SQL commands in your cloud data warehouse to import the `JOBS_BY_PROJECT` metadata table into your project dataset. Modify the code as necessary for your specific cloud data warehouse.

```sql
create view `<project_name>.<dataset_name>.JOBS_BY_PROJECT` as
select * from `region-us`.INFORMATION_SCHEMA.JOBS_BY_PROJECT
```

 # Implementation Steps 
 Once you have downloaded the Zip file and have verified its contents, the implementation steps are as follows:

1. Log into your ThoughtSpot instance and create an Embrace connection to all of the relevant views.
2. Import the TML for the worksheets and verify that it has all been imported without any errors.
3. Import the TML for the pinboard and verify that it has all been imported without any errors.
4. You are ready to start searching your GBQ data!

For detailed instructions on how to import TML files, refer to the [ThoughtSpot documentation](https://docs.thoughtspot.com/software/latest/tml-import-export-multiple).

