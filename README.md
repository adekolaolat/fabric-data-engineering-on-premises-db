# On-Premises Data Pipeline with Microsoft Fabric

## Overview

This project will simulate a typical  retail chain scenario where sales and product data is loaded from an on-premise SQL database, transforms and visualise the data using Microsoft Fabric.

  <details><summary><b> A Business Scenario</b></summary>
Let's say . . .

A company was facing quality issues in its supply chain, several vendors were consistently delivering defective items, leading to increased rejection rates, production delays, and rising costs. Procurement teams struggled to pinpoint which suppliers were responsible for the most rejected goods and how much these defects were costing the business.

Now, management has asked:
“Which of our suppliers are responsible for the most product rejections, and how much are these defects costing us? Which vendors are delivering consistent quality, and how can we reduce returns and losses?”

A solution . . .

proposes up a data pipeline that pulls procurement and vendor info from the on-premises database and processes using **Fabric**. It calculates key metrics like how many items were rejected, how much they cost, and which vendors have the highest rejection rates. The results show up in a BI dashboard so the team can quickly spot which suppliers are not meeting up with expectations. With this, the team will use the data to negotiate better deals and cut down on procurement costs.

  </details>

## Prerequisite

- Adventure Works database set up on machine. Check [here](https://github.com/adekolaolat/fabric-data-engineering-on-premises-db/blob/main/guides/on-prem-db-setup.md) for set up.
- Azure account
- Fabrics setup. For the free trial follow [this](https://www.youtube.com/watch?v=RHV7jZqc_tE)
- Microsoft tenant/ work email.
- [Medalllion lakehouse architecture](https://learn.microsoft.com/en-us/azure/databricks/lakehouse/medallion)

- Pyspark, SQL


## Data Pipeline Overview

To simulate the process, the AdventureWorks database will be used. This involves setting up the database locally, ingesting the data remotely into Fabric through a Data Pipeline, transforming it using PySpark following the medallion architecture, and creating a semantic model for visualization.

![alt text](/images/On-prem_Fabric.png)

## Implementation Steps

- [Set up  on-prem DB and Fabric](https://github.com/adekolaolat/fabric-data-engineering-on-premises-db/blob/main/guides/on-prem-db-setup.md)
  <details><summary>Set up</summary>

  - SQL Server, SSMS
  - Restore AdventureWorks database
  - Enable Remote Connections to SQL Server
  - Set up on-premises DB on machine

  </details>

- [Data ingestion - Use Data pipeline to land data from  on-premises into lakehouse.](https://github.com/adekolaolat/fabric-data-engineering-on-premises-db/blob/main/guides/data-ingestion.md)

- [Transformation - Transform data to silver and  gold tables using PySpark](https://github.com/adekolaolat/fabric-data-engineering-on-premises-db/blob/main/guides/transformation.md)

- [Set up Semantic model for tables and build report/dashboard in Fabric.](https://github.com/adekolaolat/fabric-data-engineering-on-premises-db/blob/main/guides/semantic-model.md)

## Outcome

- **PowerBI Report on procurement review of suppliers**.

![alt text](images/AW_dashboard_Fabric_procurement.jpg)
