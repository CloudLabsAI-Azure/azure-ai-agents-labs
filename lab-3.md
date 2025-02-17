# Lab 3 -

## Lab Overview

## Lab Objectives

In this lab, you will perform:
1. Navigate to Azure Portal and select the storage account.

   ![](./media/lab1-34.png)
1. Click on containers(1) under data storage, then select +container(2).

   ![](./media/lab3-1.png)
1. On New Container page enter `healthplan`(1) as name and click on create(2).

   ![](./media/lab3-2.png)
1. Open healthplan container by clicking on it, click on upload to upload the files.
1. Click on browse for files.
1. Navigate to `C:\LabFiles\azure-ai-agents-labs\data` and select both the PDFs to upload, and click on next.
1. Click on upload.
1. Navigate to Azure Ai search service in azure portal.
1. Open the Azure Ai search service.
1. Click on import and vectorize data.

   ![](./media/lab3-3.png)
1. Select azure blob storage.
1. On Configure your Azure Blob Storage , enter the following details and click on next:
   |Setting|Value|
   |---|---|
   |Subscription|leave it default|
   |Storage account|select the Storage account with prefix **stodluser**|
   |Blob container|**healthplan**|

1. On Vectorize your text, enter the following details and click on next:
   |Setting|Value|
   |---|---|
   |Kind|Azure OpenAI|
   |Subscription|leave it default|
   |Azure OpenAI service|my-openai-service<inject key="DeploymentID" enableCopy="false" /></inject>|
   |Model deployment|**text-embedding-3-large**|
   |Authentication type|**System assigned identity**|
   |Acknowledgement rectangle|**checked**|

1. Click on Next twice.
1. Enter **health-plan** for  **Objects name prefix** and click on create.

>**Note**: The uploading of data to indexes in search service might take 5-10 minutes.

1. Enter the following details and click on next

Select Azure AI Search service   AzureAISearch

vector index   health-plan

check the box for Add vector search to this resource and click on nect

Click on Create vector index

1. 

1. On your **Lab VM**, launch **Visual Studio Code** and open the **AZURE-AI-AGENTS-LABS** folder located in *C:\Labfiles*.

1. Later Open the **lab3.ipynb** file, select the **Select kernel (1)** setting available in the top right corner and select **venv (Python 3.12.1)** from the list.

   ![](./media/lab1-24.png)

1. Run the each cell and observe the output.