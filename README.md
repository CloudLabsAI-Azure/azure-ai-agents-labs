# Hands-On Labs for AI Agents Using Azure AI Agent Service SDK and Semantic Kernel

This repo contains hands-on labs for building AI Agents using the Azure AI Agent Service SDK and Semantic Kernel. The Azure AI Agent Service is used to create AI agents and Semantic Kernel is used to orchestrate the agents in a multi-agent system. 

## Prerequisites
**Microsoft will provide the lab environment with all the prerequisites**
* Azure subscription
* Azure AI Foundry resource (You will set this up in Lab 1)
* Visual Studio Code
* Python 3.10>
* Azure CLI
* Azure CLI Azure ML extension

## Labs

### Lab 1 - Setup and test the lab environment
Lab 1 walks you through how to setup the necessary lab environment for building AI Agents. This includes:
* Setting up the AI Project in the Azure AI Foundry
* Deploying an LLM and embedding models
* Establish connectivity from VS Code to the AI Project
* Perform a simple Chat Completion call to the LLM to test that your lab environment is set up properly. 

### Lab 2 - Build a simple AI agent
Lab 2 introduces you to AI agents in Azure. You will learn how to build a simple AI agent that generates a bar chart comparing costs between health insurance plans.

### Lab 3 - Build a RAG Agent
In Lab 3, you will be building an AI Agent that will perform Retrieval Augmented Generaton (RAG) on health plan documents. Azure AI Search will be used as the vector database for storing the embeddings for the health plan documents.

### Lab 4 - Develop a multi-agent system
In Lab 4, you will be creating a multi-agent system consisting of 4 agents working together to generate reports about health plan documents. You will build these 4 AI Agents:
1. Search Agent - This agent will search an Azure AI Search index for information about specific health plan policies.
2. Report Agent - This agent will generate a detailed report about the health plan policy based on the information returned from the Search Agent.
3. Validation Agent - This agent will validate that the generated report meets specified requirements. In our case, making sure that the report contains information about coverage exclusions.
4. Orchestrator Agent - This agent will act as an orchestrator that manages the communication between the Search Agent, Report Agent, and Validation Agent.
