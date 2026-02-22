🚀 ADF SFTP to Blob to DB ETL Pipeline (Metadata-Driven)
📌 Project Overview

This project demonstrates a metadata-driven Azure Data Factory (ADF) pipeline that:

Ingests files from SFTP

Stores them in Azure Blob Storage

Identifies new files using a Stored Procedure

Decrypts password-protected files using Azure Databricks

Loads processed data into a database

Feeds downstream Power BI reports

This design ensures automation, scalability, and controlled file processing.

🏗️ Architecture Diagram

(You will paste the diagram image here — I’ll explain below how to create it.)

🔄 End-to-End Flow Explanation
Step 1 – Get Metadata from SFTP

Pipeline reads file metadata from SFTP.

Identifies available files for ingestion.

Step 2 – ForEach: Copy SFTP to Blob

Iterates through each file.

Copies files into Azure Blob Storage (Raw Layer).

Step 3 – Lookup Stored Procedure (New File Check)

Calls a stored procedure.

Identifies files with status = 'New'.

Step 4 – ForEach + Wait + Databricks Decryption

Iterates only over new files.

Wait condition ensures dependency control.

Azure Databricks decrypts password-protected files.

Decrypted file is stored in processed layer.

Step 5 – Update File Status

Lookup/Stored Procedure updates file status:

copyToBlob

copyToDB

Step 6 – Load to Database

Data is loaded into structured tables.

Step 7 – Reporting Layer

Power BI connects to database.

Reports automatically reflect latest processed data.

🛠️ Tech Stack

Azure Data Factory

Azure Blob Storage

Azure SQL Database

Azure Databricks

Power BI

Stored Procedures (Metadata Control)

🧠 Key Design Concepts

Metadata-driven architecture

Idempotent file processing

Status-based control mechanism

Secure handling of encrypted files

Automated reporting integration

📈 Learning Outcomes

Designed complex control flow using ForEach & Lookup

Implemented status-driven ingestion logic

Integrated Databricks with ADF

Built end-to-end ETL pipeline architecture
