# Azure DevOps MCP Agent Governance & Workflow Instructions

When operating in GitHub Copilot Agent Mode with the Azure DevOps MCP Server (`ado`), strictly follow these operational and governance rules:

## 1. Context Resolution & Defaults
- **Default Project:** `Enterprise-Platform`
- **Default Team:** `Platform-Engineering-Team`
- Before creating, querying, or moving sprint items, always verify the active sprint using the `work` domain tools (`@CurrentIteration`) rather than guessing iteration paths.

## 2. Work Item Hygiene & Traceability (`work-items`)
- **No Orphan Items:** Never create standalone `Task` or `Bug` work items without linking them to a parent `User Story`, `Product Backlog Item`, or `Feature`.
- **Structured Fields:** Every new `User Story` must include clear, testable bullet points in `Microsoft.VSTS.Common.AcceptanceCriteria`.
- **Pull Request Traceability:** Every Pull Request created via `repo_create_pull_request` must be linked to at least one active Azure Boards work item ID.

## 3. Human-in-the-Loop Safety Rules (Batch Operations)
- **Preview-Then-Execute Mandate:** Before invoking `wit_update_work_items_batch` or performing bulk state/iteration changes, you MUST first execute a read-only query and display a Markdown preview table with the columns:
  `| Work Item ID | Title | Field | Current Value | Proposed Value |`
- **Explicit Confirmation:** Wait for explicit user approval in chat after displaying the preview table before invoking any batch write tool.
- **Audit Trail:** When executing approved batch updates, add a concise audit comment via `wit_add_work_item_comment` explaining the reason for the bulk update.

## 4. Efficient Pipeline Troubleshooting (`pipelines`)
- **Two-Step Log Retrieval:** Never attempt to fetch all build logs at once.
  1. First, call `pipelines_get_build_log` to inspect the build log index and identify the specific failing task and its `logId`.
  2. Second, call `pipelines_get_build_log_by_id` to retrieve only the relevant log lines for that failed task.
- Summarize the root cause clearly and ask whether to apply a local fix or create a linked `Bug` work item with the diagnostic snippet.