# Azure Database Migration Project
**Overview**
In this project, I'll be designing and building a cloud-based database system on Microsoft Azure to demonstrate my cloud engineering skills. I'll start by setting up a production environment database and then migrate it to Azure SQL Database. This phase will include key processes like data backup, restoration, and setting up automated scheduling to solidify our data management practices.

A critical part of the project is a simulated disaster recovery scenario to test our data resilience, involving data loss and recovery strategies. I will also delve into the complexities of geo-replication and failover configurations to ensure data availability under any conditions.

Additionally, for enhanced security, I will integrate Microsoft Entra ID to define access roles, which will add a robust layer of control and protection to our system.

**A description of the project**
1. I set up a virtual machine on Azure and configured the inbound rule to allow RDP traffic on port 3389, enabling secure remote connections. I then connected to this VM from my local machine using Remote Desktop Connection and the provided RDP file. Once logged into the VM, I installed SQL Server and SQL Server Management Studio (SSMS) directly on it. I restored the AdventureWorks database from a backup file, using SMSS, ensuring that the system was ready for database management and operations tasks. This setup serves as the foundation.
2. To transition the AdventureWorks database from our on-premises server to Azure, I started by setting up a new Azure SQL Database. During this setup, I opted for SQL Login authentication, a decision that streamlined later processes by simplifying database access from various locations.

Initial Setup and Configuration

Azure SQL Database Creation: I created the Azure SQL Database instance through the Azure portal, specifying necessary configurations including performance tiers and storage settings.
Firewall Configuration: I then configured the firewall settings on the Azure SQL Database to include the IP address of my virtual machine (VM). This step was crucial as it enabled secure communications between the Azure SQL server and my VM.
Establishing Connections and Tools Installation

After setting up the database and firewall, I installed Azure Data Studio on my VM. This powerful tool was instrumental for the subsequent steps of the migration.
Using Azure Data Studio, I established connections to both the on-premises SQL Server and the newly created Azure SQL Database.
Schema and Data Migration

Schema Migration: To ensure that the database schema from the on-premises SQL Server was accurately replicated in Azure, I utilized SQL Server Schema Compare. This tool helped compare and synchronize the database schema between the two environments.
Data Migration: Following the schema migration, I used the Migration extension within Azure Data Studio to transfer the actual data. Before executing the full data transfer, I ran a validation process through the tool to check migration settings and ensure that there were no conflicts or issues that might disrupt the migration.
Successful Data Migration

The validation confirmed that all settings were correctly configured and the migration paths were clear. I proceeded with the migration, which executed smoothly without any interruptions. The AdventureWorks data was successfully migrated and fully operational within the Azure SQL Database environment.

3. In my journey to ensure robust data protection, I meticulously initiated a full backup of my production database hosted on a Windows VM, safeguarding against potential disruptions. To enhance security, I configured an Azure Blob Storage account as my secure online repository, where I uploaded the backup, thus establishing a redundant storage solution. I then set up a mirrored development environment on a new Windows VM to serve as a controlled testing ground, onto which I restored the database backup. This "sandbox" allowes to safely test and develop without impacting the production systems. Lastly, within this environment, I used SSMS to create a Maintenance Plan, automating weekly backups of the development database to maintain consistency and ease restoration processes when necessary.
   
4. 

**File structure of the project**

**Installation instructions**

**Usage instructions**

**License information**