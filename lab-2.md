# Lab 2: Build a Simple AI Agent

### Estimated Duration: 30 Minutes

## Lab scenario

In this lab, you will learn how to build a simple AI Agent that processes data and generates a bar chart comparing different health benefit plans. This AI Agent leverages Azure AI services to analyze and visualize data efficiently.

## Lab Objective
In this lab, you will complete the following tasks:

- Task 1: Create a Simple AI Agent

## Task 1: Create a Simple AI Agent

In this task, you will build a simple AI Agent that processes data and generates a bar chart comparing different health benefit plans using Azure AI services for analysis and visualization.

1. Open the **Lab 2 - Create A Simple AI Agent.ipynb** file. This **Lab 2 - Create A Simple AI Agent.ipynb** notebook guides you through how to build a simple AI Agent that processes data and generates a bar chart comparing different health benefit plans.

   ![](./media/ag62.png)

1. In the notebook interface, click **Select kernel** in the top-right corner and choose **venv (Python 3.12.1)** from the available options.

   ![](./media/lab1-24.png)

1. Run the below cell to import necessary libraries and load environment variables for working with Azure AI Projects. This setup enables secure authentication and interaction with Azure AI services.

   ![](./media/ag63.png)

1. Run the below cell to connect to your Azure AI Foundry project and access the deployed **GPT-4o** model. This establishes a secure connection using the project connection string and Azure credentials.

   ![](./media/ag64.png)

1. Run this cell to create a **simple AI Agent** that processes data and generates a bar chart comparing different health benefit plans using Azure AI Foundry. This script initializes the AI agent, sends a prompt containing health plan data, and requests a bar chart. The agent processes the request, generates the chart, saves the image file, and then cleans up by deleting the agent.

   ![](./media/ag90.png)

1. Observe the resulting output chart. This visualizes the comparison of health benefit plans based on the input data..   

   ![](./media/lab2-26.png)

## Summary

In this lab, you have accomplished the following:
- Created a Simple AI Agent

### You have successfully completed the lab. Click **Next** to continue to the next lab.

   ![Start Your Azure Journey](./media/agg6.png)
