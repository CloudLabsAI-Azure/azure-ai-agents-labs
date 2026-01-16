# Lab 3: Build a RAG Agent

## Estimated Duration: 60 Minutes

## Overview

In this lab, you will build an AI Agent powered by **Retrieval-Augmented Generation (RAG)** to extract insights from health plan documents. Using **Azure AI Search** as a vector database, you will store and retrieve document embeddings to enable context-aware and accurate responses. This hands-on experience will help you understand how to implement RAG-based solutions and integrate Azure AI Search for improved document-driven interactions.

## Objectives

In this lab, you will complete the following tasks:

- Task 1: Create the Azure AI Search Index
- Task 2: Create the Search Agent

## Task 1: Create the Azure AI Search Index

In this task, you will create an **Azure AI Search index** to store vectorized representations of health insurance plan documents, enabling efficient retrieval for AI-driven search and analysis.

1. Navigate to **Azure Portal**, search for **Storage Accounts (1)** and select the **Storage accounts (2)** from Services section.

   ![](./media/L1T3S15.png)

1. Select the Storage account **storage<inject key="Deployment ID" enableCopy="false"></inject>**.

   ![](./media/new/g1.png)

1. In the left-hand menu, expand **Data storage (1)** section, click on **Containers (2)**, then select **+ Add container (3)**.

   ![](./media/new/g2.png)

1. In the new container dialog, enter **healthplan** **(1)** as the name and click **Create (2)**.

   ![](./media/hlthpln.png)

1. Open the newly created **healthplan** container.

   ![](./media/new/g3.png)

1. Click **Upload (1)** and then **Browse for files (2)**.

   ![](./media/new/g4.png)

1. Navigate to `C:\LabFiles\azure-ai-agents-labs\data` **(1)** and select both the PDFs to upload **(2)**, and click on **Open (3)**.

   ![](./media/pdfup.png)

1. Click **Upload** to upload the documents.

   ![](./media/finup.png)

1. Navigate to Azure Portal and search **AI Search** and select **my-search-service-<inject key="Deployment ID" enableCopy="false"></inject>** in azure portal.

   ![](./media/Lab3-1.png)

1. On the **Overview (1)** page of the Search Service, click **Import data(new) (2)**.

    ![](./media/idn.png)

1. Select **Azure Blob Storage** as the data source.

   ![](./media/abst.png)

1. Choose the **RAG** model type.

   ![](./media/rag.png)

1. On **Connect to your data** tab, enter the following details and click on **Next (5):**

   |Setting|Value|
   |---|---|
   |Subscription|**Leave it default** **(1)**|
   |Storage account|Select the Storage account with prefix **storage<inject key="Deployment ID" enableCopy="false"></inject> (2)**|
   |Blob container|**healthplan** **(3)**|
   |Authenticate using managed identity|**Enable** **(4)**|
   |Managed identity type|**System-assigned** **(5)**|

   ![](./media/new/g5.png)

1. On **Vectorize your text** tab, enter the following details and click on **Next (7):**

   |Setting|Value|
   |---|---|
   |Kind|**Azure AI Foundry (Preview) (1)**|
   |Subscription|**Leave it default** **(2)**|
   |Azure AI Foundry/Hub project|**my-project-<inject key="DeploymentID" enableCopy="false" /></inject>** **(3)**|
   |Model deployment|**text-embedding-3-large** **(4)**|
   |Authentication type|**System assigned identity** **(5)**|
   |Acknowledgement rectangle|**Checked** **(6)**|

      ![](./media/new/g6.png)

1. Click on **Next** twice.

1. On the **Review and create** tab, enter **health-plan (1)** as the **Object name prefix**, and click **Create (2)**.

   ![](./media/rchp.png)

   >**Note:** The uploading of data to indexes in the search service might take 5-10 minutes.

1. On the **Create succeeded** Pop Up, click on **Close**.

   ![](./media/new/g7.png)

1. On the Azure Portal page, search **Microsoft Foundry (1)**, and then select **Microsoft Foundry (2)** from the results.

    ![](./media/Lab1-0.png) 

1. Select **Foundry (1)** from the left pane and select **my-foundry-<inject key="Deployment ID" enableCopy="false"></inject> (2)**.

   ![](./media/new/e6.png)

1. On the **Overview** pane, click on **Go to Foundry portal** to navigate to the **Microsoft Foundry** portal.

   ![](./media/new/5a.png)

1. On the **Microsoft Foundry** portal, click on **Profile (1)** icon from the top right corner and select **Project details (2)**.

   ![](./media/new/g8.png)

1. To add a new connection, click on **Add connection** from the top right corner.

   ![](./media/new/g9.png)

1. In **Choose a connection** pop up window, select **Azure AI Search (1)** and click on **Continue (2)**.

   ![](./media/new/g10.png)

1. Select **my-search-service-<inject key="Deployment ID" enableCopy="false"></inject> (1)** from the dropdown and click on **Connect (2)**.

   ![](./media/new/g11.png)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

<validation step="246b1fec-7b90-4bdf-ae2b-18d3e2beabf2" />

## Task 2: Create the Search Agent

In this task, you will build an AI Agent using **Retrieval-Augmented Generation (RAG)** to extract and generate responses from health plan documents stored in **Azure AI Search**. By leveraging the **Azure AI Agent Service**, the agent will retrieve document embeddings for accurate and context-aware answers.

1. Navigate back to **Visual Studio Code** on your **Lab VM**.
   
1. Open the **Lab 3 - Create A RAG Agent.ipynb** file, This **Lab 3 - Create A RAG Agent.ipynb** notebook guides you through building an AI agent using the **Azure AI Agent Service**. This agent will retrieve information from health insurance policy documents stored in **Azure AI Search**, a vector database, enabling efficient and accurate information retrieval.

   ![](./media/new/g12.png)

1. In the notebook interface, click **Select kernel (1)** in the top-right corner and choose **venv (Python 3.X.X) (2)** from the available options.

   ![](./media/new/h1.png)
   
1. Run the first cell to set up the foundation for a RAG (Retrieval-Augmented Generation) Agent using Microsoft Foundry. This script imports necessary libraries, loads environment variables, and initializes components like AIProjectClient for project management and AzureAISearchTool for retrieval capabilities.

   ![](./media/new/h2.png)

1. Run the next cell to connect to your Microsoft Foundry project and access the deployed GPT-4.1 model.

   ![](./media/new/h3.png)

1. Run the next two cells to retrieve the connection ID for your Azure AI Search instance and connect to the "health-plan" index. This ensures your RAG Agent can fetch relevant data from Azure AI Search for retrieval-augmented generation.

   ![](./media/new/h4.png)

   ![](./media/new/h5.png)

1. Run the next cell to define a search agent that utilizes Azure AI Search and the GPT-4.1 model to retrieve relevant health plan documents.

   ![](./media/new/h6.png)

1. Run the next cell to chat with the search agent and retrieve details about the Northwind Standard health plan using Azure AI Search and GPT-4.1. This script initiates a conversation, queries the agent for health plan information, and displays the agent’s response.

   ![](./media/new/h7.png)
   
1. Observe the output returned by the AI agent.

   ![](./media/new/h8.png)

   > **Note:** Here's an example of what your output is likely to see; however, the precise recommendation could vary.
   
## Summary

In this lab, you built a Retrieval-Augmented Generation (RAG) AI Agent using Microsoft Foundry. You created an Azure AI Search index to store vectorized health plan documents and integrated it with an AI agent to retrieve relevant content and generate accurate, context aware responses.

### You have successfully completed the lab. Click **Next >>** to continue to the next lab.

   ![Start Your Azure Journey](./media/4nxt.png)
