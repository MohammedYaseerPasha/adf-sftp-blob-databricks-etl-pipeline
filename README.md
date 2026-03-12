# 🚀 ADF SFTP → Blob → DB ETL Pipeline
### Metadata-Driven Automation with Azure Data Factory

---

## 📌 Project Overview

This project demonstrates an **automated metadata-driven Azure Data Factory (ADF) pipeline** that performs the following:

- Ingests files from **SFTP**
- Stores files in **Azure Blob Storage**
- Identifies **new files using a Stored Procedure**
- **Decrypts password-protected files** using Azure Databricks
- Loads processed data into an **Azure SQL Database**
- Feeds downstream **Power BI reports**

This architecture ensures **automation, scalability, and controlled file processing**.

---

## 🏗️ Architecture Diagram

![ADF Pipeline Architecture](https://github.com/user-attachments/assets/32fc1ba5-0e6e-46c8-8b7a-0281d5110265)

---

# 🔄 End-to-End Pipeline Flow

## Step 1 – Get Metadata from SFTP
The pipeline retrieves **file metadata from the SFTP server** to identify available files for ingestion.

---

## Step 2 – ForEach: Copy SFTP to Blob
- Iterates through each detected file  
- Copies files into **Azure Blob Storage (Raw Layer)**

---

## Step 3 – Lookup Stored Procedure (New File Check)
A **stored procedure** is executed to check file status.

Only files with the following status are processed:


---

## Step 4 – ForEach + Wait + Databricks Decryption
- Iterates over **new files only**
- Uses a **Wait activity** to control pipeline dependencies
- **Azure Databricks decrypts password-protected files**
- Decrypted files are stored in the **Processed Layer**

---

## Step 5 – Update File Status
Stored procedures update the **processing status of files**.

| Status | Description |
|------|------|
| `New` | File detected in SFTP |
| `CopyToBlob` | File copied to Blob Storage |
| `CopyToDB` | File successfully loaded to Database |

This enables **idempotent and controlled file processing**.

---

## Step 6 – Load to Database
The decrypted and processed data is loaded into **structured tables in Azure SQL Database**.

---

## Step 7 – Reporting Layer
- **Power BI** connects directly to the database  
- Reports automatically update with **latest processed data**

---

# 🛠️ Tech Stack

- **Azure Data Factory**
- **Azure Blob Storage**
- **Azure SQL Database**
- **Azure Databricks**
- **Power BI**
- **SQL Stored Procedures**

---

# 🧠 Key Design Concepts

- Metadata-driven architecture
- Idempotent file processing
- Status-based pipeline control
- Secure handling of encrypted files
- Automated data ingestion pipeline

---

# 📈 Learning Outcomes

Through this project, I learned to:

- Design **complex ADF pipelines using ForEach, Lookup, and Stored Procedures**
- Implement **status-driven ingestion logic**
- Integrate **Azure Databricks with Azure Data Factory**
- Build an **end-to-end automated ETL pipeline**
- Enable **automated reporting with Power BI**

---

# 👨‍💻 Author

**Mohammed Yaseer Pasha**

Data Engineer | ETL Developer | Azure Data Engineering

---
