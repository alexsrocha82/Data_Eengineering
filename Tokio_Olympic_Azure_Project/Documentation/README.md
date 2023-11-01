# Tokyo Olimçyc Game Project

On this project, we will try to develop an end-to-end project with some basic transformations. 
This will pass through each stage of an ingestion lifecycle.

**Brief summary:**

- Read files from a Data Source in CSV format.
- Create a Pipeline using Azure Data Factory to read the data from the source.
- Copy the data into a Storage Container (Raw Data).
- Transform the data with Azure Databricks.
- Copy the transformed data into the Storage Container (Transformed Data).
- Use Azure Synapse Analytics to create and copy the data to a database.
- Visualize and create dashboard indicators using Power BI.

![Alt text](image.png)

To start with the project, we have to create a new Storage Account.
Choose a resource name and Storage Account Name.
![Alt text](image-1.png)

After all set, create your Storage, and get into your Storage.
![Alt text](image-2.png)

When it's all done, create your Container.
![Alt text](image-3.png)

Create the folder that you will use in the ingestion.
![Alt text](image-4.png)

Now you will have to copy the data to the container, using Azure Data Factory.
To do that, we have to create a Data Factory.
Select the resource name that you have created, and give it a name to the new Data Factory.
![Alt text](image-5.png)

Once it's done, enter into your Data Factory that you have just created.
![Alt text](image-6.png)

Now we start to build the Pipelines, to copy the data to the Storage Account.
![Alt text](image-7.png)