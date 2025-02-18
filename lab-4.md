# Lab 4 - Develop a multi-agent system
In Lab 4, you will be creating a multi-agent system consisting of 4 agents working together to generate reports about health plan documents. You will build these 4 AI Agents:
- **Search Agent** - This agent will search an Azure AI Search index for information about specific health plan policies.
- **Report Agent** - This agent will generate a detailed report about the health plan policy based on the information returned from the Search Agent.
- **Validation Agent** - This agent will validate that the generated report meets specified requirements. In our case, making sure that the report contains information about coverage exclusions.
- **Orchestrator Agent** - This agent will act as an orchestrator that manages the communication between the Search Agent, Report Agent, and Validation Agent.

    ![](./media/download.png)

Orchestration is a key part of multi-agentic systems since the agents that we create need to be able to communicate with each other in order to accomplish the objective.

We'll use the Azure AI Agent Service to create the Search, Report, and Validation agents. However, to create the Orchestrator Agent, we'll use Semantic Kernel. The Semantic Kernel library provides out-of-the-box functionality for orchestrating multi-agent systems.

## Task 1: Create the Search, Report, and Validation Agents

1. Navigate back to **Visual Studio Code** on your **Lab VM**
1. Later Open the **Lab 4 - Develop A Mult-Agent System.ipynb** file, select the **Select kernel (1)** setting available in the top right corner and select **venv (Python 3.12.1)** from the list.

   ![](./media/lab1-24.png)
1. Run the each cell and observe the output.

   ![](./media/lab2-26.png)
1. **Create a multi-agent system** : When you run the below cell, you will see a chat box pop up at the top of VS Code asking you to input the name of a health plan. If you recall, we uploaded two health plans to the search index. Type one of the following health plans in the box and press enter to begin running the multi-agent system:

    - Northwind Health Standard
    - Northwind Health Plus

        ![](./media/download1.png)
    > **Note**: After the successful run of the cell you will recieve the following outcome.

    ```
    Orchestrator Agent is starting...
    Calling SearchAgent...
    SearchAgent completed successfully.
    Calling ReportAgent...
    ReportAgent completed successfully.
    Calling ValidationAgent...
    ValidationAgent completed successfully.
    The report for Northwind Plus has been generated. Please check the Northwind Plus Report.md file for the report.
    Orchestrator Agent is starting...
    ```