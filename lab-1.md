# Lab 1: Setup AI Project and perform Chat Completion from VS Code

## Estimated Duration: 120 Minutes

## Overview

In this lab, you will configure the required environment for building AI agents. You will start by creating and configuring an AI Project in Microsoft Foundry, then deploy a Large Language Model (LLM) along with embedding models.

You will next establish connectivity between Visual Studio Code and the AI Project. To validate the setup, you will perform a basic chat completion request using the deployed model.

## Objectives

In this lab, you will perform:

- Task 1: Setting up the AI Project in the Microsoft Foundry
- Task 2: Deploying an LLM and embedding models
- Task 3: Assign permissions to the Azure AI Search resource
- Task 4: Install dependencies, create a virtual environment, and create an environment variables file.

## Task 1: Setting up the AI Project in the Microsoft Foundry

In this task, you will create and configure an AI Project within Microsoft Foundry. This involves setting up the necessary resources, defining project parameters, and ensuring that the environment is ready for deploying AI models. By the end of this task, you will have a fully initialized AI Project, serving as the foundation for further development and experimentation.

1. On the Azure Portal page, in the Search resources, services, and docs (G+/) box at the top of the portal, enter **Microsoft Foundry (1)**, and then select **Microsoft Foundry (2)** under **Services**.

    ![](./media/Lab1-0.png) 

1. In the left navigation pane for the Microsoft Foundry, select **AI Hubs (1)** under **Use with Foundry**. On the **AI Hubs** page, click on **+ Create (2)** and select **Hub (3)** from the drop-down.

    ![](./media/Lab1-1.png) 

1. On the **Create an AI hub resource** pane, enter the following details:

    - Subscription: **Leave default subscription** 
    - Resource group: Select **azure-ai-agents-<inject key="Deployment ID" enableCopy="false"></inject> (1)** 
    - Region: **<inject key="Region" enableCopy="false"></inject>** **(2)**
    - Name: Enter **aihub-<inject key="Deployment ID" enableCopy="false"></inject> (3)** 

         ![](./media/L1T1S3i.png) 

1. Scroll down, fill in the necessary details: 

    - Connect AI Services incl. OpenAI: Click on **Create new (1)**
    - Create new Azure AI Services: Enter **my-ai-service-<inject key="Deployment ID" enableCopy="false"></inject> (2)**  
    - Click on **Save (3)**
    - Click on **Next : Storage (4)** to proceed
    
        ![](./media/Lab1-2.png)  

1. Keep all settings as default, and Click on **Review + create** tab followed by **Create**.

   ![](./media/rpc.png)

   ![](./media/airsrc.png) 

1. Wait for the deployment to be completed, and then click on **Go to resource.**

   ![](./media/Lab1-4.png)

1. On the **Overview** pane, click on **Launch Azure AI Foundry** to navigate to the **Microsoft Foundry** portal.

   ![](./media/laaf.png)

1. Scroll down and click on **+ New project** from the **Hub Overview** section.

   ![](./media/newpr.png)

1. Provide the Project name as **my-project-<inject key="Deployment ID" enableCopy="false"></inject>** **(1),** then click on **Create (2)**.

   ![](./media/Lab1-6.png)

1. Once the project is created, scroll down and copy the **Project connection string**, then **paste it into Notepad or a secure location**, as it will be required for upcoming tasks.

     ![](./media/concnstr.png)

> **Congratulations** on completing the task! Now, it's time to validate it. Here are the steps:
> - If you receive a success message, you can proceed to the next task.
> - If not, carefully read the error message and retry the step, following the instructions in the lab guide. 
> - If you need any assistance, please contact us at cloudlabs-support@spektrasystems.com. We are available 24/7 to help you out.

<validation step="10c2c620-8919-4af8-9a31-7f0722a264a4" />

## Task 2: Deploying an LLM and embedding models

In this task, you will deploy a large language model (LLM) and an embedding model within your Microsoft Foundry project. These models will be used for AI-driven applications and vector-based search capabilities in upcoming labs.

1. In the Microsoft Foundry project, go to the **My assets** section, then select **Models + endpoints (1)**. Click **+ Deploy model (2)** and choose **Deploy base model (3)** from the drop-down to continue.

    ![](./media/Lab1-8.png)

2. In the **Select a model** page, search for **gpt-4o (1)**, select **gpt-4o (2)**, and then click **Confirm (3)**.

    ![](./media/L1T2S2-1912.png)

1. On the **Deploy gpt-4o** page, select **Customize**.

   ![](./media/4ocus.png)
   
   - Change the **Model version to 2024-08-06 (Default) (1)**
   - Change the Tokens per Minute Rate Limit to **200K (2)** (You can use keyboard arrow keys to adjust the limit).
   - Click on **Connect and deploy (3)**

      ![](./media/cnd.png)   

   >**Note:** If the **Tokens per Minute rate limit** of **200K** is not available, use the next **highest available limit** (e.g., 150K or 100K).

4. After deployment, click **Model + Endpoints (1)** under **My assets** to view the deployed **gpt-4o (2)** model.

   ![](./media/4odep.png)

1. Click on **gpt-4o** model and copy the **Target URI (1)** and **Key (2)**, and save them securely for later use.

   ![](./media/4okey.png)

1. In the Microsoft Foundry project, go to the **My assets** section, then select **Models + endpoints (1)**. Click **+ Deploy model (2)** and choose **Deploy base model (3)**.

   ![](./media/depemb.png)

2. On the **Select a model** page:
   - Search for **text-embedding-3-large (1)**
   - Select **text-embedding-3-large (2)**
   - Click **Confirm (3)**

      ![](./media/L1T2S7-1912.png)

3. On the **Deploy text-embedding-3-large** page:
   - Deployment type: **Standard (1)** 
   - Tokens per Minute Rate Limit:**`120K` (2)**
   - Click **Deploy (3)**

       ![](./media/embdep.png)

4. After deployment completes, under **My assets** select **Models + endpoints (1)** and confirm the **text-embedding-3-large (2)** model is listed alongside your GPT-4o deployment.

   ![](./media/embscs.png)

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

1. On the **Create a search service** pane, enter the following details and click on **Review + create (4)**.

    - Subscription: **Leave default subscription** 
    - Resource group: Select **azure-ai-agents-<inject key="Deployment ID" enableCopy="false"></inject>** **(1)** 
    - Service Name: **my-search-service-<inject key="Deployment ID" enableCopy="false"></inject> (2)**

    - Location: **<inject key="Region" enableCopy="false"></inject>** **(3)**

      ![](./media/css.png)

1. On the **Review + create** tab, click **Create** to deploy the search service.

   ![](./media/createss.png)

1. Wait until the deployment is completed, and then click on **Go to resource**.

   ![](./media/gtrss.png)

   >**Note**: The deployment may take around **10 - 12 minutes**, depending on Azure’s provisioning time for the AI Search service.

1. In the resource settings, navigate to **Identity (1)** under the **Settings** section. Under **System assigned**, set the status to **On (2)** and click **Save (3)**.

   ![](./media/L1T3S6-1912.png)

1. When prompted, confirm by selecting **Yes** to enable the system-assigned managed identity.

   ![](./media/L1T3S7.png)

1. Next, go to **Keys (1)** under **Settings**, and for API access control, select **Both (2)** options to enable complete access.

   ![](./media/l1.task1.22.png)

1. Confirm this selection by choosing **Yes** to enable API access control for the search service.

   ![](./media/ag25a.png)

1. Now, navigate back to your previously created service in **Microsoft Foundry** **|** **Foundry** blade named **my-ai-service-<inject key="DeploymentID" enableCopy="false" /></inject>**.

   ![](./media/navfon.png)

1. In the Foundry service blade, select **Access control (IAM) (1)**, click **+ Add (2)** drop-down, and then choose **Add role assignment (3)**.

   ![](./media/araf.png)

1. Under **Job function roles**, search for **Cognitive Services OpenAI User (1)**, select **Cognitive Services OpenAI User (2)**, and then select **Next (3)**.

   ![](./media/aranxt.png)

1. On the **Add role assignment** page, 

   - Under **Members** tab, select **Managed identity (1)**
   - Click on **+ Select members (2)**
   - Managed identity: **Search service(1)** **(3)**
   - Then, select **my-search-service-<inject key="Deployment ID" enableCopy="false"></inject> (4)** search service.
   - Click on **Select (5)**

     ![](./media/slctmem.png)

1. Click **Review + assign** twice to finalize the role assignment.

   ![](./media/finra.png)

1. On the Azure portal, search for **Storage Accounts (1)** and select **Storage accounts (2)** from the services.

   ![](./media/L1T3S15.png)

1. Now, navigate to the **Storage account** named **aihubxxxxxxxx** for the project.

   ![](./media/strgnav.png)

1. Inside the storage account blade, go to **Access control (IAM) (1)**, click **+ Add (2)**, and choose **Add role assignment (3)**.

   ![](./media/L1T3S17.png)

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

1. Run the following PowerShell command to install the required package.

   ```
   pip install azure-ai-ml azure-identity
   ```

   >**Note:** This can take 3-5 minutes to complete. Wait for the command execution to complete then proceed ahead.

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

   ![](./media/no.png)

1. Once the Authorization is completed, navigate back to Visual Studio Code.

1. When prompted to **Select a subscription and tenant (Type a number or press Enter to keep the default)**, simply press **Enter**.

   ![](./media/upimage0002.png)

1. Open the **sample.env** file.

   ![](./media/ag46.png)

1. In the `sample.env` file, provide the following environment variables using the values retrieved from your Microsoft Foundry project:

   - `AIPROJECT_CONNECTION_STRING`: Provide the **Project connection string** value you have copied in Task 1 of Step 10.
   - `CHAT_MODEL_ENDPOINT`: Provide the **Target URI** of the **gpt-4o** model you have copied in Task 2 of Step 5.
   - `CHAT_MODEL_API_KEY`: Provide the **Key** value of the **gpt-4o** model you have copied in Task 2 of Step 5.
   - `CHAT_MODEL`: **gpt-4o**

     ![](./media/upag49.png)

      > **Note:** To get the Project Connection string, follow these steps to get the value:
      > 1. On the **Azure Portal** page, in the *Search resources, services, and docs (G+/)* box at the top of the portal, search for **aihub-<inject key="Deployment ID" enableCopy="false"></inject>**.
      > 2. In the **Overview** pane, click **Launch Microsoft Foundry** to open the Microsoft Foundry portal.
      > 3. In the **Project Overview** section, select **Go to project**, then copy the **Project connection string**.
   
1. Save the changes made to the `sample.env` file by clicking **CTRL + S**.

1. Create a `.env` file by running the following PowerShell command:

   ```powershell
   cp sample.env .env
   ```

   ![](./media/ag50.png)   

1. Next, open the **Lab 1 - Project Setup.ipynb** file. The **Lab 1 - Project Setup.ipynb** notebook guides you through setting up an AI Project in Microsoft Foundry, deploying an LLM and embedding models, and configuring VS Code connectivity. It also includes a simple Chat Completion API call to verify the setup. Running this notebook ensures that your environment is correctly configured for developing AI-powered applications. 

   ![](./media/ag61.png)

1. Click **Select Kernel (1)** in the top-right corner and choose **Install/Enable suggested extensions Python + Jupyter (2)** if prompted.

   ![](./media/lab1-22.png)

1. Once the Python extension is installed, select **Python Environments** to ensure that Jupyter Notebook runs in the correct Python interpreter with the necessary dependencies installed. 

   ![](./media/lab1-23.png)

1. Select **venv (Python 3.X.X)** from the list as this version is likely required for compatibility with Microsoft Foundry SDK and other dependencies.

   ![](./media/python-kernal00-01.jpg)

1. Run the first cell to import the necessary Python libraries for working with Azure AI services.   

   ![](./media/ag72.png)

1. Run the next cell to retrieve the project connection string and model name from environment variables. These values are needed to interact with the Large Language Model (LLM) securely, without hardcoding sensitive information.

   ![](./media/ag73.png)

1. Run the next cell to connect to your Microsoft Foundry project using the connection string. This establishes a secure connection with AIProjectClient, enabling interactions with your project resources.

   ![](./media/ag74.png)

1. Run the next cell to interact with the GPT-4o model using your Microsoft Foundry project. This code initializes a chat client, sends a request for a joke about a teddy bear, and prints the response. Finally, see the output provided from the chat model.

   ![](./media/ag75.png)

   > **Note:** If you encounter errors such as **"unknown connection"**, recheck your `.env` file. Ensure all values are correct, save the file, and restart the **Jupyter kernel** before re-running the notebook cells.

   ![](./media/L1T4S24N.png)

## Summary

In this lab, you have accomplished the following:
- Set up the AI Project in Microsoft Foundry.
- Deployed an LLM and embedding models.
- Established connectivity from VS Code to the AI Project.
- Performed a simple Chat Completion call.

### You have successfully completed the lab. Click **Next** to continue to the next lab.

   ![Start Your Azure Journey](./media/2-next.jpg)
