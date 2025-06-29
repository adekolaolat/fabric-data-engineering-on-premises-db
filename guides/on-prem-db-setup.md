# Set up on-premises database and Fabric.

This guide and the linked resources provide steps to set up an on-premises database (DB) and configure it so Fabric can access it remotely.


## 1. Set up on-prem DB to your machine.

- Install SQL Server Express
- Instal SSMS 
- Download AdventureWorks database backup and restore to SQL Server.

Follow this [guide](https://www.youtube.com/watch?v=XIAGi3Pg3mQ) to set up SQL Server and SSMS.

Follow this [guide](https://learn.microsoft.com/en-us/sql/samples/adventureworks-install-configure?view=sql-server-ver17&tabs=ssms#download-backup-files) to download and restore AdventureWorks db to SQL Server.

## 2. Configure DB for remote access.

- Enable Remote Connection to SQL Server using SQL Server Configuration manager and Configure Windows Firewall. Check [here](https://www.youtube.com/watch?v=lJ_WRSN_wD0)
- Set up should allow SQL/Windows authentication.

## 3. Get Fabric free trial.

- For Fabric free trial set up, follow [this](https://www.youtube.com/watch?v=RHV7jZqc_tE)

## 4. Set up Fabric connection to DB

Fabric will talk to on-prem DB through a gateway.

- Use on-premises Data Gateway to allow Fabric connect securely to db using SQL authentication. Check out this [guide](https://learn.microsoft.com/en-us/fabric/data-factory/how-to-access-on-premises-data)
  
- On-premises gateway needs to be installed on the machine and set up using the Fabric tenant details.
