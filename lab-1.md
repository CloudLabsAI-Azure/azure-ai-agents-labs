# Lab 1: Setup AI Project and perform Chat Completion from VS Code

## Estimated Duration: 120 Minutes

## Overview

In this lab, you will configure the required environment for building AI agents. You will start by creating and configuring an AI Project in Microsoft Foundry, then deploy a Large Language Model (LLM) along with embedding models.

You will next establish connectivity between Visual Studio Code and the AI Project. To validate the setup, you will perform a basic chat completion request using the deployed model.

## Objectives

In this lab, you will perform:

- Task 1: Create a Microsoft Foundry Resource
- Task 2: Deploying an LLM and embedding models
- Task 3: Assign permissions to the Azure AI Search resource
- Task 4: Install dependencies, create a virtual environment, and create an environment variables file.

## Task 1: Create a Microsoft Foundry Resource

In this task, you will create a Microsoft Foundry resource, initialize an AI Project, enable the new Microsoft Foundry portal, and collect the Project endpoint and API key needed for later labs.

1. On the Azure Portal, search for **Microsoft Foundry (1)**, and select **Microsoft Foundry (2)** from the results.

    ![](./media/Lab1-0.png) 

1. From the left navigation pane, expand **Use with Foundry (1)**, click on **Foundry (2)** and then select **+ Create (3)** from the menu bar.

    ![](./media/new/1.png) 

1. On the **Create an Foundry resource** pane, enter the following details and click on **Review + create (5)**.

    - Subscription: **Leave default subscription**

    - Resource group: Select **azure-ai-agents-<inject key="Deployment ID" enableCopy="false"></inject> (1)** 
    - Name: Enter **my-foundry-<inject key="Deployment ID" enableCopy="false"></inject> (2)** 

    - Region: **<inject key="Region" enableCopy="false"></inject>** **(3)**

    - Default project name: Enter **my-project-<inject key="Deployment ID" enableCopy="false"></inject> (4)** 

         ![](./media/new/7.png) 

1. On **Review + create** tab, click on **Create**.

   ![](./media/new/3a.png)

1. Wait for the deployment to be completed, and then click on **Go to resource.**

   ![](./media/new/4.png)

1. On the **Overview** pane, click on **Go to Foundry portal** to navigate to the **Microsoft Foundry** portal.

   ![](./media/new/5a.png)

1. Once you are in the **Microsoft Foundry** portal, locate the **New Foundry** option and switch the toggle to **Enabled**.

   ![](./media/new/8.png)

1. Copy the **Project endpoint (1)** and **Project API key (2)** and save them in **Notepad** for later use.

   ![](./media/new/9.png)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

<validation step="10c2c620-8919-4af8-9a31-7f0722a264a4" />

## Task 2: Deploying an LLM and embedding models

In this task, you will deploy a large language model (LLM) and an embedding model within your Microsoft Foundry project. These models will be used for AI-driven applications and vector-based search capabilities in upcoming labs.

1. In the **Microsoft Foundry** portal, select **Build (1)** from the top left corner, click **Models (2)** from left pane and select **Deploy a base model (3)**.

    ![](./media/new/10.png)

1. In the **Model** page, search for **gpt-4.1 (1)** and select **gpt-4.1 (2)** from the results.

    ![](./media/new/a1.png)

1. In the **gpt-4.1** page, click on **Deploy (1)** and select **Custom Settings (2)** from the dropdown.

    ![](./media/new/a2.png)

1. On the **Deploy gpt-4.1** page, change the **Tokens per Minute Rate Limit** to **200K (1)** and click on **Deploy (2)**.

      ![](./media/new/a3.png)

   >**Note:** If the **Tokens per Minute rate limit** of **200K** is not available, use the next **highest available limit** (e.g., 150K or 100K).

1. After deployment, select **Models (1)** from left navigation pane and select the **gpt-4.1 (2)** model.

   ![](./media/new/a4.png)

1. Under **gpt-4.1**, select the **Details (1)** tab from top and copy the **Target URI (2)** and save it in **Notepad** for later use.

   ![](./media/new/a5.png)

1. From the left navigation pane, click **Models (1)** and select **Deploy a base model (2)**.

   ![](./media/new/n1.png)

1. In the **Model** page, search for **text-embedding-3-large (1)** and select **text-embedding-3-large (2)** from the results.

      ![](./media/new/17.png)

1. In the **text-embedding-3-large** page, click on **Deploy (1)** and select **Default Settings (2)** from the the dropdown.

    ![](./media/new/18.png)

1. From the left navigation pane, click **Models (1)** and ensure both the **Models (2)** are deployed successfully.

   ![](./media/new/a6.png)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

<validation step="73125dc6-9bc8-4d62-ae9c-f9ef5a421385" />

## Task 3:  Assign permissions to the Azure AI Search resource

In this task, you will configure the necessary permissions for the Azure AI Search resource to ensure it integrates securely and effectively with the AI Agent. This involves setting up the resource, enabling identity, and assigning required roles.

1. In the Azure portal, use the search bar at the top to search for **AI Search (1)**, and then select **AI Search** **(2)** from the Services section.

   ![](./media/aisearch1.png)

1. You will be redirected to the Microsoft Foundry interface. Within the **AI Search** section, click **+ Create** to begin creating a new search service.

    ![](./media/Lab1-21.png)

1. On the **Create a search service** pane, enter the following details and click on **Review + create (5)**.

    - Subscription: **Leave default subscription**

    - Resource group: Select **azure-ai-agents-<inject key="Deployment ID" enableCopy="false"></inject>** **(1)**

    - Service Name: **my-search-service-<inject key="Deployment ID" enableCopy="false"></inject> (2)**

    - Location: **<inject key="Region" enableCopy="false"></inject>** **(3)**

    - Pricing tier: **Standard (4)**

      ![](./media/new/w1.png)

1. On the **Review + create** tab, click **Create** to deploy the search service.

   ![](./media/createss.png)

1. Wait until the deployment is completed, and then click on **Go to resource**.

   ![](./media/gtrss.png)

   >**Note**: The deployment may take around **10 - 12 minutes**, depending on Azure’s provisioning time for the AI Search service.

1. In the Search Service, expand **Settings (1)** and select **Identity (2)** under the  section. Under **System assigned**, set the status to **On (3)** and click **Save (4)**.

   ![](./media/new/w2.png)

1. When prompted, confirm by selecting **Yes** to enable the system-assigned managed identity.

   ![](./media/L1T3S7.png)

1. Next, go to **Keys (1)** under **Settings**, and for API access control, select **Both (2)** options to enable complete access.

   ![](./media/l1.task1.22.png)

1. Confirm this selection by choosing **Yes** to enable API access control for the search service.

   ![](./media/ag25a.png)

1. On the Azure portal, search for **Storage Accounts (1)** and select **Storage accounts (2)** from the services.

   ![](./media/L1T3S15.png)

1. From the top, click on **+ Create** to create a Storage Account.

   ![](./media/new/w3.png)

1. Provide the following details and then click on **Review + create (7)**.

   - Leave the default **Subscription (1)**.

   - Resource group: Select **azure-ai-agents-<inject key="Deployment ID" enableCopy="false"></inject> (2)**

   - Storage account name: Enter **storage<inject key="Deployment ID" enableCopy="false"></inject> (3)**

   - Region: **<inject key="Region" enableCopy="false"></inject>** **(4)**

   - Performance: Select **Standard (5)**.

   - Redundancy: Select **Locally redundant storage (LRS) (6)**.

      ![](./media/new/w4.png)

1. Click on **Create** to create a storage account.

   ![](./media/new/w5.png)

1. Wait for the deployment to be completed, and then click on **Go to resource.**

   ![](./media/new/w6.png)

1. In the storage account blade, from the left navigation pane, select **Access control (IAM) (1)**, click **+ Add (2)**, and choose **Add role assignment (3)**.

   ![](./media/new/w7.png)

1. Under **Job function roles**, search for **Storage Blob Data Reader (1)**, select **Storage Blob Data Reader (2)**, and then select **Next (3)**.

   ![](./media/blbdr.png)

1. On the **Add role assignment** page, 

   - Under **Members** tab, select **Managed identity (1)**
   - Click on **+ Select members (2)**
   - Managed identity: **Search service(1)** **(3)**
   - Then select **my-search-service-<inject key="Deployment ID" enableCopy="false"></inject> (4)** search service.
   - Click on **Select (5)**

     ![](./media/blobra.png)

1. Finally, click **Review + assign** twice to complete the assignment.

   ![](./media/blobrpa.png)   

1. In the Azure portal, use the search bar at the top to search for **AI Search (1)**, and then select **AI Search** **(2)** from the Services section.

   ![](./media/aisearch1.png)

1. Select your **my-search-service-<inject key="Deployment ID" enableCopy="false"></inject>**

   ![](./media/new/w8.png)

1. From the left navigation pane, select **Access control (IAM) (1)**, click **+ Add (2)**, and choose **Add role assignment (3)**.

   ![](./media/new/w9.png)

1. Under **Job function roles**, search for **Search Index Data Reader (1)**, select **Search Index Data Reader (2)**, and then select **Next (3)**.

   ![](./media/new/w10.png)

1. On the **Add role assignment** page, 

   - Under **Members** tab, select **Managed identity (1)**
   - Click on **+ Select members (2)**
   - Managed identity: **Foundry project (1)** **(3)**
   - Then select **my-project-<inject key="Deployment ID" enableCopy="false"></inject> (4)**.
   - Click on **Select (5)**

     ![](./media/new/e1b.png)

1. Finally, click **Review + assign** twice to complete the assignment.

   ![](./media/new/e2.png)

1. Again select **Access control (IAM) (1)**, click **+ Add (2)**, and choose **Add role assignment (3)**.

   ![](./media/new/w9.png)

1. Under **Job function roles**, search for **Search Service Contributor (1)**, select **Search Service Contributor (2)**, and then select **Next (3)**.

   ![](./media/new/e3.png)

1. On the **Add role assignment** page, 

   - Under **Members** tab, select **Managed identity (1)**
   - Click on **+ Select members (2)**
   - Managed identity: **Foundry project (1)** **(3)**
   - Then select **my-project-<inject key="Deployment ID" enableCopy="false"></inject> (4)**.
   - Click on **Select (5)**

     ![](./media/new/e4.png)

1. Finally, click **Review + assign** twice to complete the assignment.

   ![](./media/new/e5.png)

1. On the Azure Portal page, search **Microsoft Foundry (1)**, and then select **Microsoft Foundry (2)** from the results.

    ![](./media/Lab1-0.png) 

1. Select **Foundry (1)** from the left pane and select **my-foundry-<inject key="Deployment ID" enableCopy="false"></inject> (2)**.

   ![](./media/new/e6.png)

1. In the Foundry service blade, select **Access control (IAM) (1)**, click **+ Add (2)** drop-down, and then choose **Add role assignment (3)**.

   ![](./media/new/e7.png)

1. Under **Job function roles**, search for **Azure AI Project Manager (1)**, select **Azure AI Project Manager (2)**, and then select **Next (3)**.

   ![](./media/new/f1.png)

1. On the **Add role assignment** page, 

   - Under **Members** tab, select **Users, group or service principal (1)**
   - Click on **+ Select members (2)**
   - Search for **<inject key="AzureAdUserEmail"></inject> (3)** in the search bar.
   - Then, select **ODL_User <inject key="Deployment ID" enableCopy="false"></inject> (4)**.
   - Click on **Select (5)**

     ![](./media/new/f2.png)
   
1. Click **Review + assign** twice to finalize the role assignment.

   ![](./media/new/f3.png)

1. Follow steps from **31** to **34**, and assign the **Cognitive Services OpenAI Contributor** role to the **ODL_User <inject key="Deployment ID" enableCopy="false"></inject>**.

   ![](./media/new/f4.png)

1. In the Foundry service blade, select **Access control (IAM) (1)**, click **+ Add (2)** drop-down, and then choose **Add role assignment (3)**.

   ![](./media/new/e7.png)

1. Under **Job function roles**, search for **Cognitive Services OpenAI User (1)**, select **Cognitive Services OpenAI User (2)**, and then select **Next (3)**.

   ![](./media/aranxt.png)

1. On the **Add role assignment** page, 

   - Under **Members** tab, select **Managed identity (1)**
   - Click on **+ Select members (2)**
   - Managed identity: **Search service(1)** **(3)**
   - Then, select **my-search-service-<inject key="Deployment ID" enableCopy="false"></inject> (4)** search service.
   - Click on **Select (5)**

     ![](./media/new/e8.png)

1. Click **Review + assign** twice to finalize the role assignment.

   ![](./media/finra.png)

## Task 4: Install dependencies, create a virtual environment, and create an environment variables file

In this task, you will install the required dependencies, configure a virtual environment, and set up environment variables. This setup ensures a consistent development environment and securely manages configuration settings for your AI project.

1. On the **Desktop** of your **Lab VM**, launch **Visual Studio Code**.

   ![](./media/L1T4S1-1912.png)

2. Go to **File (1)** and click **Open Folder... (2)**.

   ![](./media/ag37.png) 

1. Navigate to `C:\LabFiles` **(1)**, select the **azure-ai-agents-labs (2)** folder and then click **Select Folder (3)**.

   ![](./media/ag38.png) 

1. When prompted, click **Yes, I trust the authors**.

   ![](./media/ag39.png)

1. Click on the **ellipsis (...) (1)** in the top menu, then select **Terminal (2)** and click **New Terminal (3)**.

   ![](./media/L1T4S5.png)

1. Make sure you are in the **azure-ai-agents-labs** project directory. Run the following PowerShell commands to create and activate your virtual environment:

   ```powershell
   python -m venv venv
   ```

   ```powershell
   venv/Scripts/activate
   ```

   ![](./media/ag41.png)

1. Run the below PowerShell command. This installs all the required packages:

   ```powershell
   pip install -r requirements.txt
   ```
   ![](./media/ag42.png)

   >**Note:** This can take 3-5 minutes to complete. Wait for the command execution to complete then proceed ahead.

1. Run the following PowerShell command to install or upgrade pip to the latest version.

   ```powershell
   python.exe -m pip install --upgrade pip
   ```

   ![](./media/ag43.png)

1. Run the below command to log into your Azure account.

   ```
   az login
   ```

1. In the window that opens, select **Work or school account (1)** and click on **Continue (2)**.

   ![](./media/L1T4S11-1912.png)

   > **Note**: If the window is not visible, try minimizing VS Code and the Edge browser, as it might be hidden behind them.

1. Sign in using below credentials:-

   - Username: **<inject key="AzureAdUserEmail"></inject>**

   - Temporary Access Pass: **<inject key="AzureAdUserPassword"></inject>**

1. On the **Sign in to all apps, websites, and services on this device ?** pop-up, select on **No, this app only**.

   ![](./media/new/r1.png)

1. Once the Authorization is completed, navigate back to Visual Studio Code.

1. When prompted to **Select a subscription and tenant (Type a number or press Enter to keep the default)**, simply press **Enter**.

   ![](./media/upimage0002.png)

1. Open the **sample.env** file.

   ![](./media/new/r2.png)

1. In the `sample.env` file, provide the following environment variables using the values retrieved from your Microsoft Foundry project:

   - `AIPROJECT_ENDPOINT`: Provide the **Project endpoint** value you have copied in Step 8 of Task 1.
   - `API_KEY`: Provide the **Key** value of the **gpt-4.1** model you have copied in Step 8 of Task 1.
   - `CHAT_MODEL_ENDPOINT`: Provide the **Target URI** of the **gpt-4.1** model you have copied in Step 6 of Task 2.
   - `CHAT_MODEL`: **gpt-4.1**

     ![](./media/new/r3.png)

1. Save the changes made to the `sample.env` file by clicking **CTRL + S**.

1. Create a `.env` file by running the following PowerShell command:

   ```powershell
   cp sample.env .env
   ```

   ![](./media/ag50.png)   

1. Next, open the **Lab 1 - Project Setup.ipynb** file. The **Lab 1 - Project Setup.ipynb** notebook guides you through setting up an AI Project in Microsoft Foundry, deploying an LLM and embedding models, and configuring VS Code connectivity. It also includes a simple Chat Completion API call to verify the setup. Running this notebook ensures that your environment is correctly configured for developing AI-powered applications. 

   ![](./media/new/r4.png)

1. Click **Select Kernel (1)** in the top-right corner and choose **Install/Enable suggested extensions Python + Jupyter (2)** if prompted.

   ![](./media/lab1-22.png)

1. Wait for the **Python** extension to be installed.

   ![](./media/new/h10.png)

1. Once the Python extension is installed, select **Python Environments** to ensure that Jupyter Notebook runs in the correct Python interpreter with the necessary dependencies installed. 

   ![](./media/lab1-23.png)

1. Select **venv (Python 3.X.X)** from the list as this version is likely required for compatibility with Microsoft Foundry SDK and other dependencies.

   ![](./media/new/r5.png)

1. Run the first cell to import the necessary Python libraries for working with Azure AI services.   

   ![](./media/new/r6.png)

1. Run the next cell to create an AIProjectClient instance using your project endpoint from environment variables and Azure authentication credentials. This initializes a secure connection to your Microsoft Foundry project so that you can interact with its AI resources programmatically.

   ![](./media/new/r7.png)

1. Run the next cell to interact with the GPT-4.1 model using your Microsoft Foundry project. This code initializes a chat client, sends a request for a joke about a teddy bear, and prints the response. Finally, see the output provided from the chat model.

   ![](./media/new/27.png)

   > **Note:** If you encounter errors such as **"unknown connection"**, recheck your `.env` file. Ensure all values are correct, save the file, and restart the **Jupyter kernel** before re-running the notebook cells.

   ![](./media/L1T4S24N.png)

## Summary

In this lab, you have accomplished the following:
- Created a Microsoft Foundry Resource.
- Deployed an LLM and embedding models.
- Established connectivity from VS Code to the AI Project.
- Performed a simple Chat Completion call.

### You have successfully completed the lab. Click **Next >>** to continue to the next lab.

   ![Start Your Azure Journey](./media/2-next.jpg)
