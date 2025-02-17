# Lab 4 - Develop a multi-agent system
In Lab 4, you will be creating a multi-agent system consisting of 4 agents working together to generate reports about health plan documents. You will build these 4 AI Agents:
- **Search Agent** - This agent will search an Azure AI Search index for information about specific health plan policies.
- **Report Agent** - This agent will generate a detailed report about the health plan policy based on the information returned from the Search Agent.
- **Validation Agent** - This agent will validate that the generated report meets specified requirements. In our case, making sure that the report contains information about coverage exclusions.
- **Orchestrator Agent** - This agent will act as an orchestrator that manages the communication between the Search Agent, Report Agent, and Validation Agent.