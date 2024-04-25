# Azure Database Migration Project
**Overview**

In this project, I'll be designing and building a cloud-based database system on Microsoft Azure to demonstrate my cloud engineering skills. I'll start by setting up a production environment database and then migrate it to Azure SQL Database. This phase will include key processes like data backup, restoration, and setting up automated scheduling to solidify our data management practices.

A critical part of the project is a simulated disaster recovery scenario to test our data resilience, involving data loss and recovery strategies. I will also delve into the complexities of geo-replication and failover configurations to ensure data availability under any conditions.

Additionally, for enhanced security, I will integrate Microsoft Entra ID to define access roles, which will add a robust layer of control and protection to our system.

**A description of the project**

1. I set up a virtual machine on Azure and configured the inbound rule to allow RDP traffic on port 3389, enabling secure remote connections. I then connected to this VM from my local machine using Remote Desktop Connection and the provided RDP file. Once logged into the VM, I installed SQL Server and SQL Server Management Studio (SSMS) directly on it. I restored the AdventureWorks database from a backup file, using SMSS, ensuring that the system was ready for database management and operations tasks. This setup serves as the foundation.
2. To transition the AdventureWorks database from our on-premises server to Azure, I started by setting up a new Azure SQL Database. During this setup, I opted for SQL
   Login authentication, a decision that streamlined later processes by simplifying database access from various locations.
   Initial Setup and Configuration
   Azure SQL Database Creation: I created the Azure SQL Database instance through the Azure portal, specifying necessary configurations including performance tiers and storage settings
   Firewall Configuration: I then configured the firewall settings on the Azure SQL Database to include the IP address of my virtual machine (VM). This step was crucial as it enabled secure communications between the Azure SQL server and my VM.
   
   Establishing Connections and Tools Installation
   After setting up the database and firewall, I installed Azure Data Studio on my VM. This powerful tool was instrumental for the subsequent steps of the migration
   Using Azure Data Studio, I established connections to both the on-premises SQL Server and the newly created Azure SQL Database.
   
   Schema and Data Migration
   Schema Migration: To ensure that the database schema from the on-premises SQL Server was accurately replicated in Azure, I utilized SQL Server Schema Compare. This tool helped compare and synchronize the database schema between the two environments.
   Data Migration: Following the schema migration, I used the Migration extension within Azure Data Studio to transfer the actual data. Before executing the full data transfer, I ran a validation process through the tool to check migration settings and ensure that there were no conflicts or issues that might disrupt the migration.
   
   Successful Data Migration
   The validation confirmed that all settings were correctly configured and the migration paths were clear. I proceeded with the migration, which executed smoothly without any interruptions. The AdventureWorks data was successfully migrated and fully operational within the Azure SQL Database environment.

3. In my journey to ensure robust data protection, I meticulously initiated a full backup of my production database hosted on a Windows VM, safeguarding against potential disruptions. To enhance security, I configured an Azure Blob Storage account as my secure online repository, where I uploaded the backup, thus establishing a redundant storage solution. I then set up a mirrored development environment on a new Windows VM to serve as a controlled testing ground, onto which I restored the database backup. This "sandbox" allowes to safely test and develop without impacting the production systems. Lastly, within this environment, I used SSMS to create a Maintenance Plan, automating weekly backups of the development database to maintain consistency and ease restoration processes when necessary.
   
4. In my disaster recovery simulation, I began by deliberately removing selected critical data from my production database to replicate a scenario where data integrity was compromised. I carefully documented this simulated data loss to serve as a detailed blueprint for my recovery testing. After the simulation, I confirmed its success by examining the Azure SQL Database using the connection established in Azure Data Studio.
   Next, I utilized Azure SQL Database Backup to restore my production database to a point just before the simulated data loss occurred. I validated the restoration's success by closely examining the restored data through the same connection in Azure Data Studio. This step was crucial, as the restored database needed to function seamlessly as my production database, given that the previous one lacked critical data. Finally, I completed the recovery process by deleting the database that had suffered data loss in the Azure portal.

5. To enhance the resilience of my production Azure SQL Database, I started by setting up geo-replication. This process involved creating a synchronized replica of my primary database on a separate SQL server located in a different geographical region.
   Next, I carried out a planned failover to the secondary region. This move shifted operations to the secondary database copy and allowed me to simulate real-world challenges. I carefully checked the availability and data consistency of the failover database to ensure it met operational standards.
   Finally, I executed a failback to the primary region, showing the reliable and repeatable nature of my failover strategy.

6. To enhance the security and management of my Azure SQL production database, I began by integrating Microsoft Entra ID as a trusted identity provider, enabling authentication using Microsoft Entra credentials. This step was important for setting a robust foundation for access control.
   I then designated a Microsoft Entra admin with privileged permissions within my Azure SQL Database environment. This admin role was critical as it held authority over user management and access control. I ensured that I could connect to the production database using these Microsoft Entra admin credentials within Azure Data Studio.
   Following this, I created a new user account in Microsoft Entra ID to act as the DB Reader. With the admin credentials, I connected to the production database in Azure Data Studio and assigned the db_datareader role to this newly created DB Reader User. This role definition was specifically chosen to provide the user with read-only privileges, ensuring they could access data without the ability to modify it.
   To finalize the setup, I reconnected to my production database using the credentials of the new DB Reader user to test the assigned permissions. This step helped me to confirm that the correct role had been assigned, and the user had the appropriate read-only access. Through these actions, I successfully configured and defined roles, and created both admin and reader accounts, streamlining user access and enhancing security.

**File structure of the project**

- README.md file contains all my experience with the project.
- AzureProjectDiagram.pdf file contains a UML visual diagram for the architecture I built.

**Installation instructions**

Although there is no need to download, you can clone this repository by copying and pasting the following in your command line. git clone https://github.com/Tayyaba2287/azure-database-migration663.git

**Usage instructions**

You can have a read through my README.md file and AzureProjectDiagram.pdf file to see how I went about the project. 

**License information**

his repository is open-source and available for download. 
