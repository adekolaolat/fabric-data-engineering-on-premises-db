
# Data ingestion into Fabric Lakehouse

To bring in data from on-prem, I will need a Lakehouse to store it and a Data Factory pipeline to fetch and land the on-premises data. It iss important to first understand the structure of the database and figure out which tables are actually needed for the business requirements.

For the AdventureWorks database, I’m planning to load all the tables (except the system ones) into the Lakehouse for now. Later, I will build targeted use cases and transformations at the silver and gold layer.

## Create Lakehouse in Fabric

To create a Lakehouse in Fabric, start by creating a Workspace, then add a new item. Pick Lakehouse and give it a name, this is where the data will live.

The Lakehouse comes with two main folders: Tables and Files.

The Tables is built on the Delta table structure, so it’s perfect for storing data in Parquet and Delta formats.

The Files section can hold any type of file you want. The pipeline gives the flexibility of customizing where the data lands and what format is best for a use case.

## Create Data pipeline item.

In the same workspace, create a data pipeline and give it a name.

This will launch the Data Factory UI, where pipeline activities will be used to ingest data.

For this pipeline, the goal is to bring in data from all the tables in the on-prem database into the Lakehouse. So it’s a good idea to first look at the structure and schemas of the database.

For the AdventureWorks database, I plan to grab the schema names and table names first. That way, I can set up the pipeline to load data dynamically into the Lakehouse destination I want.

To do this, I’ll need three activities, which I’ll add to the pipeline

1. A Look up activity to query the on-prem database with the created SQL connection gateway created in the [Set-up section](https://github.com/adekolaolat/fabric-data-engineering-on-premises-db/blob/main/guides/on-prem-db-setup.md). This look up activity will return the Schema and Table names I want in the database using this query.
   
   ```
   -- Get Schema and Table names from database.
    SELECT s.name AS SchemaName, t.name AS TableName
    FROM sys.tables t
    JOIN sys.schemas s ON t.schema_id = s.schema_id
    WHERE s.name NOT LIKE 'dbo%'
    ORDER BY s.name, t.name;

   ```
2. A For Each activity - This will be used to loop the pair f schema and table names returned by the Look up activity.
   
3. Within the For Each Activity, a Copy Data activity is added which uses a query to copy data for each table in the on-prem and land in a bronze folder under Files in the Lakehouse. Path for the destination would look like this `Files/bronze/schemaName/tableName.csv` 

#### Configuration for pipeline activities.

##### Lookup activity
![alt text](</images/LookupActivity_Config.jpg>)


##### For Each activity
![alt text](</images/ForEach_Configuration.jpg>)

##### Copy Data activity - Source
![alt text](</images/CopyDataActivity_Source_ Configuration.jpg>)

##### Copy Data activity - Destination
![alt text](</images/CopyDataActivity_Destination_Configuration.jpg>)



After set up, validate and run the pipeline.

**Pipeline run status**



![alt text](</images/DataFactory_Pipeline.jpg>)

Pipeline will copy and store data from the on-prem table as csv files tables dynamically into the target bronze folder in the Lakehouse.

## Outcome 

**On-prem data landed into Lakehouse**
![alt text](</images/On-premise data landed in Lakehouse_bronze.jpg>)

*The pipeline activity configurations can also be tweaked to land data in the Tables folder instead of Files. That way, you don’t have to worry about keeping the data structure consistent when your pipeline runs updates from on-prem. Plus, using Tables gives you the ‘Upsert’ feature, so new data just gets updated automatically each time the pipeline runs.*

[⏮️ Go to Set up](https://github.com/adekolaolat/fabric-data-engineering-on-premises-db/blob/main/guides/on-prem-db-setup.md)
