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

Create Copy Data Activities.
![Alt text](image-8.png)

In this scenario, we will copy the data from GitHub:
https://github.com/alexsrocha82/Data_Engineering/tree/main/Tokyo_Olympic_Azure_Project/Storage/raw-data
![Alt text](image-9.png)

Make sure to copy the raw link.
![Alt text](image-10.png)
![Alt text](image-11.png)

Create the new dataset. In this case, we're going to choose HTTP because we are accessing the data from GitHub. 
And then choose the data format type.
![Alt text](image-12.png)

And then choose the data format type.
![Alt text](image-13.png)

Create the link service. Paste the 'raw' link into the linked service.
![Alt text](image-14.png)

Create Data Lake storage where you can store your data.
![Alt text](image-15.png)

Choose the data format, in our case, CSV.
![Alt text](image-16.png)

Create Linked service for the Sink.
![Alt text](image-17.png)

Set the path to store the data.
![Alt text](image-18.png)
![Alt text](image-19.png)

Once it's done, copy the data with the 'Debug' button.
![Alt text](image-20.png)

When the process is done, check the container to see if the data was copied as desired.
![Alt text](image-21.png)

Now we repeat the copy process for all the data files and create the 'Source' Linked service to get the data.
![Alt text](image-23.png)

And adjust the 'Sink' Path.
![Alt text](image-24.png)

Then copy the data. When it's all done, the ADF and the container should look like this.
![Alt text](image-25.png)
![Alt text](image-26.png)

The next step is to create an Azure Databricks service.
![Alt text](image-27.png)
![Alt text](image-28.png)

Once the Azure Databricks workspace is created, you'll have to create a Cluster. 
For this project, we can use a 'single node' because we don't need much transformation power.
![Alt text](image-29.png)

The next step is to create a Notebook to start the transformations.
![Alt text](image-30.png)

Select your cluster and create a security key to mount the notebook to the lake. 
To do that, go back to Azure home and search for App registrations.
![Alt text](image-31.png)

Then create a new registration.
![Alt text](image-32.png)

Give it any name and press 'Register.'
![Alt text](image-33.png)

From there, you need to keep two codes (Application (client) ID and Directory (tenant) ID) and save them somewhere, as you'll need them later. 
Note that the keywords I'm using will not work for you; you will need to use the keywords available in your application.
![Alt text](image-34.png)

Next, create the secret. Give it a name and copy the values.
![Alt text](image-35.png)

Give it a name and copy the values.
![Alt text](image-36.png)
![Alt text](image-37.png)

Then create the basic authentication from Databricks to the data lake. 
The best practice is to create a key vault, but in this case, we'll just create a manual connection.
![Alt text](image-38.png)

Now, mount the container connection. 
Go back to home -> storage account.
![Alt text](image-39.png)

Copy the name of the storage to the source string connection.
![Alt text](image-40.png)

And now copy the container name.
![Alt text](image-41.png)

Then run.
![Alt text](image-42.png)