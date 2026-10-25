# Azure DevOps MCP Agent Governance & Workflow Instructions

When operating in GitHub Copilot Agent Mode with the Azure DevOps MCP Server (`ado`), follow these team rules automatically:

## 1. Context Resolution & Defaults
- **Default Project:** `Enterprise-Platform`
- **Default Team:** `Platform-Engineering-Team`
- Always resolve the active sprint using the `work` domain tools (`@CurrentIteration`) before creating, querying, or moving sprint items.

## 2. Work Item Hygiene & Traceability (`work-items`)
- **No Orphan Items:** Never create standalone `Task` or `Bug` work items without linking them to a parent `User Story`, `Product Backlog Item`, or `Feature`.
- **Testable Acceptance Criteria:** Every new `User Story` must include clear bullet points in `Microsoft.VSTS.Common.AcceptanceCriteria`.
- **Pull Request Traceability:** Every Pull Request created via `repo_create_pull_request` must link to at least one active Azure Boards work item ID.

## 3. Human-in-the-Loop Safety Rules (Batch Operations)
- **Preview-Then-Execute Mandate:** Before calling `wit_update_work_items_batch`, always run a read-only query first and render a Markdown preview table with the columns:
  `| Work Item ID | Title | Field | Current Value | Proposed Value |`
- **Wait for Approval:** Never execute a batch update until the user explicitly confirms the preview table in chat.
- **Audit Comment:** Whenever a batch update runs, append an audit comment via `wit_add_work_item_comment` explaining the change.

## 4. Two-Step Pipeline Log Inspection (`pipelines`)
- Never fetch all build logs at once.
  1. First call `pipelines_get_build_log` (the log "table of contents") to find which specific task failed and get its `logId`.
  2. Second call `pipelines_get_build_log_by_id` to fetch only the log lines for that failing `logId`.