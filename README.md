# Enron_Email_Analysis

## Overview
This project analyzes the Enron email dataset using Apache Spark on the Databricks platform. The goal is to extract meaningful insights such as email traffic patterns, top senders and recipients, and email exchanges over time, specifically focusing on the year 2000.

## Group Members
- Group 45

## Project Objectives
- Load and preprocess Enron email data.
- Extract key email metadata such as sender (`From`), recipients (`To`), and timestamps.
- Analyze email volume per sender and recipient.
- Explore daily email exchange trends in the year 2000.

---

## Project Workflow and Group Contributions

### 1. Data Preparation and Exploration
- **Activity:** Group members collectively checked available files in Databricks’ FileStore, focusing on `emails.csv` for analysis.
- **Steps Taken:**
  - Verified the presence of required files using `dbutils.fs.ls`.
  - Copied and unzipped the dataset from `/FileStore/tables`.
  - Confirmed the integrity of the unzipped CSV via shell commands.
- **Outcome:** Clean dataset ready for ingestion.

### 2. Data Loading and Initial Inspection
- **Activity:** Team loaded the CSV data into a Spark DataFrame and inspected the columns and initial rows.
- **Steps Taken:**
  - Used `spark.read.csv()` with appropriate options (`header`, `multiLine`, `quote`, `escape`).
  - Verified columns and sample data (`file` and `message` columns).
- **Outcome:** Confirmation of data structure and readiness for extraction.

### 3. Email Metadata Extraction
- **Activity:** Extracted sender (`From`) and recipient (`To`) fields using regex from the raw message text.
- **Steps Taken:**
  - Applied `regexp_extract` Spark functions to parse out sender and recipient emails.
  - Checked and handled null or blank entries.
  - Filtered out emails with missing recipients to clean the dataset.
- **Outcome:** Cleaned DataFrame with clear sender and recipient columns.

### 4. Email Counts and Top Users Analysis
- **Activity:** Calculated aggregate statistics and identified top email senders and recipients.
- **Steps Taken:**
  - Computed the total number of emails and unique senders.
  - Calculated the mean emails sent per sender.
  - Used grouping and aggregation to find top 10 senders and recipients.
- **Outcome:** Key insights into email communication patterns and major contributors.

### 5. Recipient Field Explosion
- **Activity:** Processed multiple recipients by splitting and exploding the `To` field into individual email addresses.
- **Steps Taken:**
  - Split recipient strings by commas.
  - Trimmed spaces and filtered out invalid or empty strings.
- **Outcome:** Detailed recipient-level email counts.

### 6. Date Extraction and Parsing
- **Activity:** Extracted and converted raw date strings from the message to Spark timestamp format.
- **Steps Taken:**
  - Extracted raw `Date` lines from the message body using regex.
  - Cleaned timezone and parenthetical info.
  - Converted to timestamp format with legacy parsing policy to handle old formats.
  - Filtered emails to only include those from the year 2000.
- **Outcome:** Timestamped dataset suitable for time series analysis.

### 7. Daily Email Activity Analysis
- **Activity:** Analyzed email traffic per day by counting emails sent and received.
- **Steps Taken:**
  - Grouped emails by date to count sent and received emails.
  - Joined sent and received counts for a comprehensive daily view.
  - Visualized email exchanges over the year 2000.
- **Outcome:** Time series insight into email volume fluctuations throughout 2000.

---

## Tools and Technologies Used
- **Databricks platform** for distributed data processing.
- **Apache Spark (PySpark)** for scalable data processing and analysis.
- **Python** as the main programming language.
- **Regex** for text parsing.
- **Spark SQL functions** for aggregation, filtering, and date/time processing.

---

## Summary of Group Collaboration
- The group divided responsibilities efficiently:
  - Data ingestion and preparation were handled by members focused on file management and environment setup.
  - Extraction and cleaning of email metadata were performed collaboratively to ensure accuracy.
  - Analysis and aggregation tasks, including sender/recipient ranking and time-based grouping, were done in tandem with regular group discussions.
  - Visualization and interpretation of results were conducted jointly to derive insights and prepare final deliverables.

---

## How to Run the Code
1. Upload the `emails_csv.zip` file to Databricks `/FileStore/tables/`.
2. Follow the notebook cells sequentially to unzip, load, preprocess, and analyze the data.
3. Use Spark UI and Databricks display functions to visualize outputs.

---

## Future Work
- Sentiment analysis on email bodies.
- Network graph visualization of sender-recipient relationships.
- Anomaly detection in communication patterns.

---
