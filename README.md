# Telecom_ETL_Pipeline_SSIS


## 📌 Overview
This project demonstrates a full SSIS (SQL Server Integration Services) data flow pipeline designed for processing telecom CSV files. The pipeline handles raw data ingestion, transformation, error handling, data enrichment through lookup, and auditing — all tailored to telecom domain data such as subscriber records.

## 📁 Data Source
- *File Type*: .csv
- *Source Content*: Telecom data (e.g., call data records, subscriber details)

## 🔄 ETL Flow Summary

1. *Flat File Source*
   - Loads telecom data from CSV files.
   - Configured with *error output redirection* to handle parsing/format errors, sending bad rows to err_source_output table.

2. *Derived Columns*
   - Multiple transformations and calculated columns applied to enhance/clean the data before loading.

3. *Lookup Transformation*
   - Performs a lookup to fetch subscriber_id from imsi_reference table.

4. *Row Count*
   - Counts are captured at various stages to determine:
     - Records extracted
     - Records added
     - Records rejected
   - These counts are stored in SSIS variables for logging/audit purposes.

5. *OLE DB Destination*
   - Loads processed data into the target SQL table.
   - Configured with *error output* to redirect invalid rows (e.g., schema mismatch) to err_destination_output table.

## 🧪 Error Handling

- *Source Errors*:
  - Rows that fail at the source due to malformed structure or invalid data are redirected to err_source_output.
  
- *Destination Errors*:
  - Records that fail to insert due to schema mismatch or constraint violation are redirected to err_destination_output.

## 📊 Auditing
- Captures metrics such as:
  - Total records read
  - Records successfully loaded
  - Records rejected
- These are stored in an *audit table* to support data quality and monitoring.

## 🚀 Technologies Used
- Microsoft SQL Server Integration Services (SSIS)
- SQL Server (for staging, audit, and reference tables)
- Flat File Source (CSV)
- Lookup, Derived Column, Row Count, OLE DB components

## 📎 Project Purpose
This ETL pipeline was built to provide a robust, auditable, and maintainable solution for ingesting and transforming telecom data from CSV files into a relational database. The design supports clear tracking of rejected data and makes error handling transparent and traceable.

---

## 📬 Contact
Developed by [Mahmoud El-Tabakh](https://www.linkedin.com/in/mahmoud-eltabakh2001)  
Feel free to reach out or connect with me on [LinkedIn](https://www.linkedin.com/in/mahmoud-eltabakh2001).
