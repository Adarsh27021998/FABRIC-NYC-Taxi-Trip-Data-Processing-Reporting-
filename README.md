# FABRIC-NYC-Taxi-Trip-Data-Processing-Reporting-
Developed an end-to-end data pipeline using Microsoft Fabric Data Lakehouse, Azure Data Factory, and Power BI to process NYC TLC trip data.

NYC Taxi Trip Data Processing & Reporting

1.	Landing
o	Source: NYC TLC trip record data in Parquet format.
o	Storage: Data is landed in a Fabric Data Lakehouse.
2.	Staging
o	Transformation: Azure Data Factory Copy Activity loads data into staging tables (e.g., stg.nyctaxi_yellow and stg.taxi_zone_lookup).
3.	Presentation
o	Processing: Dataflows and Stored Procedures refine and aggregate the data into the presentation layer (dbo.nyctaxi_yellow).
4.	Reporting
o	Visualization: The cleaned and processed data is used to create a Semantic Model, which feeds into Power BI Dashboards for analytics and reporting.

![image](https://github.com/user-attachments/assets/83294a05-1bff-4734-8831-a6db3d611265)

