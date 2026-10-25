# Azure DevOps MCP Server & GitHub Copilot Companion Repository

This repository accompanies the blog post: **"Stop Drowning in Browser Tabs: How to Run Your Azure DevOps Workflow Inside VS Code with GitHub Copilot and MCP"** (Exam AZ-401 Study Series).

## What's Inside

- `.vscode/mcp.json`: Connects Visual Studio Code to the Azure DevOps MCP Server with dynamic organization prompts and scoped tool domains (`core`, `work`, `work-items`, `repositories`, `pipelines`).
- `.github/copilot-instructions.md`: Automatic workspace guardrails so GitHub Copilot Agent Mode enforces parent-child work item links, shows a dry-run preview table before bulk updates, and uses two-step pipeline log inspection.
- `pipelines/ci-validation.yml`: Sample Azure Pipelines CI configuration used in the blog examples to test triggering builds and diagnosing failed task logs.
- `prompts/ado-mcp-playbook.md`: Copy-paste prompts matching the 5 workday examples from the article.

## Prerequisites

1. **Visual Studio Code** with the **GitHub Copilot Chat** extension installed.
2. **Node.js 18+** installed locally (`node --version`).
3. An **Azure DevOps Organization** and project where you have `Contributor` permissions.
4. Authenticated session via **Microsoft Entra ID** (browser sign-in) or **Azure CLI** (`az login`).

## Getting Started in 2 Minutes

1. Clone this repository and open the folder in Visual Studio Code.
2. Open `.vscode/mcp.json` and click the **Start** button above `"ado"`.
3. Type your Azure DevOps organization name (for example, `contoso-devops-org`) when prompted.
4. Open **GitHub Copilot Chat**, switch the mode dropdown to **Agent**, and try the prompts in `prompts/ado-mcp-playbook.md`.