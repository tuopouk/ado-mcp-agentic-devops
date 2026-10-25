# Azure DevOps MCP Server & GitHub Copilot Companion Repository

This repository contains the configuration files, governance instructions, sample CI pipeline, and prompt playbook referenced in the blog post: **"Agentic DevOps on Azure: Automating Azure DevOps Workflows with MCP Server and GitHub Copilot"** (Exam AZ-401 Study Series).

## Repository Structure

- `.vscode/mcp.json`: Configures the Azure DevOps MCP Server in Visual Studio Code with dynamic input prompts and scoped tool domains (`core`, `work`, `work-items`, `repositories`, `pipelines`).
- `.github/copilot-instructions.md`: Repository-level guardrails that instruct GitHub Copilot Agent Mode to enforce work item traceability, preview batch updates before execution, and use two-step build log inspection.
- `pipelines/ci-validation.yml`: Sample Azure Pipelines CI workflow used to test MCP pipeline execution (`pipelines_run_pipeline`) and targeted task log troubleshooting (`pipelines_get_build_log_by_id`).
- `prompts/ado-mcp-playbook.md`: Copy-paste natural language prompts for day-to-day Azure Boards, Repos, and Pipelines operations.

## Prerequisites

1. **Visual Studio Code** with the **GitHub Copilot Chat** extension installed.
2. **Node.js 18+** installed locally (`node --version`).
3. Access to an **Azure DevOps Organization** and project (`Contributor` permissions recommended for testing write operations).
4. Authenticated session via **Microsoft Entra ID** (interactive browser login) or **Azure CLI** (`az login`).

## Quickstart

1. Clone this repository and open it in Visual Studio Code.
2. Open `.vscode/mcp.json` and click the **Start** code lens above the `"ado"` server definition.
3. Enter your Azure DevOps organization name (e.g., `contoso-devops-org`) when prompted.
4. Open **GitHub Copilot Chat**, switch to **Agent** mode, and run the validation prompts in `prompts/ado-mcp-playbook.md`.