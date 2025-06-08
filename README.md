## This branch is been created for custom event for Matthew Calder
# Hands-on Labs for AI Agents using Azure AI Agent Service SDK

This repo contains the hands-on Labs for building your AI Agents using Azure AI Agent Service SDK.

# Pre-Requisites
**Microsoft will provide the Lab environment with all the pre-requisites**
* Azure Subscription
* Azure AI Foundry - AI Hub and AI Project (You will setup in Lab 1) <br>
* VS Code <br>
* Python <br>
* Azure CLI <br>
* Azure CLI Azure ML extension <br>

# Labs

**Lab 1 - Setup AI Project and peform Chat Completion from VS Code**
<br> Lab 1 helps you to learn how to setup the necessary environment for  building the AI Agents. This includes:
* Setting up the AI Project in the Azure AI Foundry
* Deploying an LLM and embedding models
* Establish connectivity from VS Code into the AI Project
* Perform a simple Chat completion call

**Lab 2 Build a simple AI Agent**
<br>Lab 2 introduced you to AI Agents in Azure. You will learn how to build simple AI Agent that generates a bar chart comparing the health benefit plans.

**Lab 3 - Build a RAG Agent**
<br>In Lab 3, you will be building an AI Agent that will perform Retrieval Augmented Generaton (RAG) on health plan documents. Azure AI Search will be used as the vector database for storing the embeddings for the health plan documents.

**Lab 4 - Develop a multi-agent system**
<br>In Lab 4, you will be creating a multi-agent system consisting of 4 agents working together to generate reports about health plan documents. You will build these 4 AI Agents: <br>
1. Search Agent - This agent will search an Azure AI Search index for information about specific health plan policies.
2. Report Agent - This agent will generate a detailed report about the health plan policy based on the information returned from the Search Agent.
3. Validation Agent - This agent will validate that the generated report meets specified requirements. In our case, making sure that the report contains information about coverage exclusions.
4. Orchestrator Agent - This agent will act as an orchestrator that manages the communication between the Search Agent, Report Agent, and Validation Agent.
