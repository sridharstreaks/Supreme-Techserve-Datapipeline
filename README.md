# Data Pipeline - Supreme Techserve

This repository provides an overview of the data pipeline used at Supreme Techserve. The pipeline integrates data from an ERP tool, processes it through several stages, and produces comprehensive reports and dashboards.

## Table of Contents
1. [Overview](#overview)
2. [Architecture](#architecture)
3. [Pipeline Stages](#pipeline-stages)
    - [Bronze Layer](#bronze-layer)
    - [Silver Layer](#silver-layer)
    - [Gold Layer](#gold-layer)
    - [Reporting Layer](#reporting-layer)
    - [Automation Layer](#automation-layer)
4. [Technologies Used](#technologies-used)
5. [Automation and Scheduling](#automation-and-scheduling)
6. [Contributing](#contributing)
7. [License](#license)

## Overview

The data pipeline for Supreme Techserve is designed to facilitate the seamless integration, transformation, and visualization of data extracted from the Microsoft Dynamics NAV ERP system. This pipeline leverages data engineering principles to ensure data integrity, consistency, and availability for reporting and analytics purposes. The architecture follows medallion architecture and is divided into four layers: Bronze, Silver, Gold, and Reporting, each serving a specific role in the data processing workflow.

1. **Bronze Layer**: 
   - **Data Extraction**: Raw data is exported from the Microsoft Dynamics NAV ERP system. This export process generates CSV/XLSX files containing raw transactional and master data.
   - **Storage**: The raw CSV/XLSX files are initially stored on a NAS (Network Attached Storage) server to ensure high availability and fault tolerance.
   - **Staging**: These files are then moved to a local staging area for preliminary processing.

2. **Silver Layer**:
   - **Data Transformation**: Using Power Query, the raw data undergoes a series of transformation steps. These include data cleansing, normalization, and enrichment to convert the raw data into a structured and refined format. *M Query is occasionally used for the transformation.*
   - **ETL (Extract, Transform, Load) Processes**: The transformation processes in this layer are **Manual** at this point; future automation and scheduling are required.

3. **Gold Layer**:
   - **Data Modeling**: The cleansed and transformed data is loaded into Power Pivot. Here, complex data models are constructed, enabling advanced analytical capabilities. After the transformation, each table in the data model is stored in a single big Excel File that holds the PowerPivot model and the tables.
   - **Data Aggregation and Structuring**: Power Pivot facilitates the creation of calculated columns, measures, and hierarchies, providing a robust foundation for data analysis.

4. **Reporting & Automation Layer**:
   - **Reporting Automation**: VBA scripts are employed to automate the generation and distribution of reports. These scripts extract the required data, format it, and distribute it via email to relevant Team Members and Departments. It is also used to Schedule the Data Extraction from ERP Tool.
   - **Visualization**: Similarly, PowerBI is used to create interactive and dynamic dashboards using the Data Model. These dashboards provide comprehensive insights to managers and facilitate data-driven decision-making across the organization.

### Key Components and Technologies
- **Microsoft Dynamics NAV**: The primary ERP system from which data is extracted.
- **NAS Server**: Provides scalable and reliable storage for raw data files.
- **Power Query**: A data connection technology that enables data discovery, connectivity, and transformation.
- **Power Pivot**: An Excel add-in allowing sophisticated data modeling and analysis.
- **VBA (Visual Basic for Applications)**: Used to script and automate reporting tasks.
- **PowerBI**: A business analytics service that delivers insights through data visualizations.

## Architecture

![Data Pipeline](Supreme-Techserve-Datapipeline/Supreme_Techserve_Datapipeline.png)

## Pipeline Stages

### Bronze Layer
- **Source**: ERP Tool (MS Dynamics NAV)
- **Storage**: NAS Server
- **Export**: Raw Excel files in CSV/XLSX format
- **Destination**: Local staging destination

### Silver Layer
- **Transformation Tool**: Power Query and Excel
- **Operations**: Data cleaning and transformation
- **Output**: Transformed data connections

### Gold Layer
- **Modeling Tool**: Power Pivot and DAX
- **Operations**: Data modeling and table creation
- **Output**: Modeled data tables

### Reporting Layer
- **Reporting Tool**: VBA and PowerBI
- **Operations**: Scheduled Generating and emailing reports, creating dashboards
- **Output**: Emails to team members, PowerBI dashboards

### Automation Layer
- **Automation Tool**: VBA
- **Operations**: Scheduled Extraction of Data From ERP and Exporting CSV&Excel files to Local Destination
- **Output**: Extraction from Source, Storing in Local Destination

## Technologies Used

- **ERP Tool**: Microsoft Dynamics NAV
- **Storage**: NAS Server
- **Data Transformation**: Power Query, Excel
- **Data Modeling**: Power Pivot, DAX, Excel Tables
- **Reporting**: VBA, PowerBI
- **Automation**: VBA

## Contributing

We welcome contributions from the community. **Feedback and Improvements are always welcome to make this Pipeline Less Sophisticated and Optimised.**
Please follow these steps to contribute:
1. Fork the repository
2. Create a new branch (`git checkout -b feature/your-feature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feature/your-feature`)
5. Create a new Pull Request

## License

This project is licensed under the MIT License.
