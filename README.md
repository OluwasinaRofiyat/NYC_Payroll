
# **NYC Payroll Data Integration Project**

## **Overview**
This project focuses on integrating payroll data for the City of New York for the years 2020 and 2021. The goal is to develop a scalable and automated ETL pipeline using AWS services to analyze financial resource allocation, specifically focusing on overtime expenditures, and to make the data accessible to the public for transparency.

## **Objectives**
- **Data Integration**: Combine and standardize payroll data from 2020 and 2021.
- **Automated ETL Pipeline**: Build an automated pipeline using AWS Glue to load and transform data.
- **Data Aggregation**: Create normalized OLAP tables optimized for fast queries and data aggregation.
- **Transparency**: Provide public access to salary and overtime data for all municipal employees.

## **Project Structure**
The project is organized into several key components:

### **1. Data Preprocessing**
- **Files**: 
  - `payroll_2020.csv`
  - `payroll_2021.csv`
- **Process**: 
  - Data was concatenated using a Python script before being uploaded to AWS S3.
  - Preprocessing involved data cleaning, standardizing formats, and handling missing values.

### **2. AWS Crawler**
- **Purpose**: 
  - Automated schema discovery and metadata creation for the combined dataset stored in S3.
- **Output**: 
  - `nyc_payroll_new` table in the AWS Glue Data Catalog.

### **3. AWS Glue ETL Jobs**
- **Dimension Tables**:
  - `DimAgency`
  - `DimTitle`
  - `DimEmployee`
- **Fact Tables**:
  - `FactPayroll`
  - `FactOvertime`
- **Scripts**:
  - SQL scripts to create the dimension and fact tables, along with procedures to populate them, were executed within AWS Glue.
  
### **4. Version Control**
- **Repository**: The project is version-controlled using Git.
  - **Branching Strategy**: Separate branches for development, testing, and production.
  - **Documentation**: Detailed readme files, inline comments, and process diagrams.

### **5. Logging and Monitoring**
- **CloudWatch Logs**: Enabled for all AWS Glue jobs to monitor execution and capture logs.
- **Custom Logging**: Implemented within the Glue scripts for specific events and error handling.
- **Metrics**: AWS Glue job performance metrics are monitored through CloudWatch, with alarms set for any anomalies.

## **Challenges**
- **Data Consistency**: Addressed inconsistencies and missing values during the preprocessing stage.
- **Access Permissions**: Resolved S3 access issues by correctly configuring IAM roles and S3 bucket policies.
- **Performance**: Optimized query performance by creating normalized OLAP tables and implementing partitioning.

## **Optimization Recommendations**
- **Data Partitioning**: Further partition the data by fiscal year and agency to enhance query performance.
- **Data Archiving**: Archive older data to reduce storage costs and improve query speed.
- **Resource Management**: Adjust DPUs for Glue jobs during peak times to reduce execution time.
- **Monitoring Enhancements**: Implement more detailed CloudWatch alarms for better monitoring.

## **Future Work**
- **Scalability**: Explore using AWS Redshift for handling larger datasets and more complex queries.
- **Data Enrichment**: Integrate additional datasets, such as budget allocations, to provide deeper insights.
- **Public API**: Develop an API to facilitate public access to the payroll data.

## **How to Reproduce**
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/your-repo/nyc-payroll-integration.git
   ```
2. **Set Up AWS Environment**:
   - Upload the concatenated `nyc_payroll_new.csv` to an S3 bucket.
   - Run the AWS Crawler to create the table schema.
   - Execute the SQL scripts via AWS Glue jobs to create and populate the dimension and fact tables.
3. **Monitor and Debug**:
   - Use AWS CloudWatch for logs and metrics.
   - Review the Glue job run history for any errors or performance issues.

## **Contributing**
Contributions are welcome! Please fork the repository and create a pull request with your changes. Ensure all code is properly documented and tested.

