# -AWS-DB-Migration-Lab
 Database Migration from EC2 to AWS RDS – MariaDB 
In this lab, I migrated the café application’s database from an EC2-hosted MariaDB to a fully managed AWS RDS MariaDB instance.
 The goal was to improve scalability, reliability, and simplify database management by leveraging AWS managed services.
Steps with screenshots:

1 Architecture Overview
 High-level diagram showing the migration process from the EC2 MariaDB database to AWS RDS MariaDB, along with application and networking components.

2 RDS Instance Creation
 Created a new AWS RDS MariaDB instance named CafeDatabase.

3 Creating Database Backup from EC2
 On the EC2 instance, used the following command to export the existing MariaDB database into a .sql dump file:

mysqldump -u root -p CafeDB > CafeDbDump.sql

4 Importing Data into RDS
 Connected to the newly created RDS MariaDB instance and imported the Café database dump:


5 Verifying the Database on RDS
 Executed the following command to verify that the Café database was successfully added to the RDS instance:

show databases;

6 Updating AWS Secrets Manager – Database Password
 Updated the stored password in AWS Secrets Manager to match the new RDS database password so the application can authenticate correctly.

7 Updating AWS Secrets Manager – Database URL
 Modified the DB connection URL to point to the RDS endpoint instead of the EC2 private IP.

8 Updating AWS Secrets Manager – Database Username
 Changed the username in Secrets Manager to match the RDS admin user for proper authentication.

 Outcome:
 The migration was completed successfully, with zero data loss and no downtime. The application now benefits from the high availability, automated backups, and monitoring provided by AWS RDS.
