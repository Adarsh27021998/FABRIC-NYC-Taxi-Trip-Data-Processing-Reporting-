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

![image](https://github.com/user-attachments/assets/33a17dee-d40e-41ab-b277-35e8a2708f40)

![image](https://github.com/user-attachments/assets/fea98b8c-b0b8-45e4-82bd-d5f44f9ebad0)

![image](https://github.com/user-attachments/assets/225f8a55-ca5a-47ea-b852-593276225df3)
in taxi zone look up file move to warehouse of stg lookup data 

![image](https://github.com/user-attachments/assets/b296adaf-2f50-4f55-8510-5487ef6587f9)
We set a dynamic parameter to store the variable v_date as @formatDateTime(addToTime(activity('Latest Processed Date').output.resultSets[0].rows[0].latest_processed_pickup, -1, 'Month'), 'yyyy-MM') so that v_date represents the previous month, and in the Copy Activity for staging nyc_yellowtaxi, we pass this parameter in the source file name and path as @concat('yellow_tripdata_', variables('v_date'), '.parquet') to dynamically select the correct file, while the destination table in the warehouse is stg.nyctaxi_yellow, and we store another variable @addToTime(concat(variables('v_date'), '-01'), 1, 'Month') to set the next month as v_end_date, followed by executing a Stored Procedure (SP) to remove outliers from the dataset.


![image](https://github.com/user-attachments/assets/e37257b7-ad3a-486b-8055-56e2019c2360)
![image](https://github.com/user-attachments/assets/655c05d1-f9b1-44cc-97c4-83290738dc8e)
In the invoke staging step, we call the stored procedure pl_stg_process_nyctaxi and pass the data to pl_pre_process_nyctaxi, enabling continuous monthly data fetching from the Lakehouse to the warehouse, which is connected to a semantic model for building Power BI reports.warehouse, which 

![image](https://github.com/user-attachments/assets/50f88ebe-8610-4861-a5fb-7533d8e5d2d2)







