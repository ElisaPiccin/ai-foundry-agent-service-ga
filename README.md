# ai-foundry-agent-service-ga

## Setup Instructions

1. Create a new conda environment with Python 3.12:
   ```powershell
   conda create -y -n aifoundry-agent-service-ga python=3.12
   conda activate aifoundry-agent-service-ga
   ```
2. Install dependencies:
   ```powershell
   pip install -r requirements.txt
   ```

## Key Packages
- azure-ai-projects
- azure-ai-agents 1.1.0b1 (now a separate package, installed with azure-ai-projects 1.0.0b11 GA)

## Background and Key Changes

### Azure AI Projects Library and Breaking Changes

This project uses the [azure.ai.projects](https://learn.microsoft.com/en-us/python/api/overview/azure/ai-projects-readme?view=azure-python-preview) library, which is part of the Azure AI Foundry SDK. As of version 1.0.0b11, there are important breaking changes:
- **Agents are now implemented in a separate package** (`azure-ai-agents`), but you can still access agent operations via the `.agents` property on the `AIProjectClient`.
- The client endpoint must be set to your Azure AI Foundry project endpoint (instead of previously used project connection string).
- For more details and migration guidance, see the [official changelog](https://github.com/Azure/azure-sdk-for-python/blob/azure-ai-projects_1.0.0b11/sdk/ai/azure-ai-projects/CHANGELOG.md).

### New Project Types in Azure AI Foundry

Azure AI Foundry now supports two main project types:
- **Foundry Project**: The default, simple setup for most use cases, supporting agents, model inference, evaluations, and more.
- **Hub-based Project**: Projects can be created inside a shared hub, allowing for shared configurations, security, and resource management across teams. You can now [create multiple projects on the same resource](https://learn.microsoft.com/en-us/azure/ai-foundry/how-to/create-projects?tabs=ai-foundry&pivots=fdp-project#create-multiple-projects-on-the-same-resource), enabling collaboration and project-level isolation.
- For a detailed comparison, see [Types of projects](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry#project-types).

### Key Concepts in This Example
- **Library**: `azure.ai.projects`
- **Class**: `AIProjectClient`
- **Object**: `project_client`
- **Properties**: `agents`, `threads`, `messages`, `runs`
- **Methods**: `create_agent`, `create_thread`, `create_message`, `create_and_process`, `list_messages`, `delete_agent`

These abstractions allow you to programmatically manage agents, conversations (threads), messages, and execution runs within your Azure AI Foundry project.

#### References
- [Azure AI Projects Python SDK documentation](https://learn.microsoft.com/en-us/python/api/overview/azure/ai-projects-readme?view=azure-python-preview)
- [How to create projects in Azure AI Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/how-to/create-projects?tabs=ai-foundry&pivots=fdp-project#create-multiple-projects-on-the-same-resource)
- [Types of projects in Azure AI Foundry](https://learn.microsoft.com/en-us/azure/ai-foundry/what-is-azure-ai-foundry#project-types)
- [Changelog for azure-ai-projects](https://github.com/Azure/azure-sdk-for-python/blob/azure-ai-projects_1.0.0b11/sdk/ai/azure-ai-projects/CHANGELOG.md)