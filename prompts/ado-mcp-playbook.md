# Azure DevOps MCP Server — Prompt Playbook

Use these natural-language prompts in **GitHub Copilot Chat (Agent Mode)** with the `ado` MCP server enabled.

---

## 1. Validate Connection & Explore Sprint Context
> "Using the `ado` MCP server, list the projects in my organization, verify the `Platform-Engineering-Team` inside `Enterprise-Platform`, and show the start and end dates for the current sprint (`@CurrentIteration`)."

> "List all work items in the current sprint for `Platform-Engineering-Team` grouped by State. Highlight any Active tasks that are unassigned or Bugs missing story points."

---

## 2. Create Hierarchical Work Items with Traceability
> "In `Enterprise-Platform`, create a new User Story in the current sprint titled 'Enforce OIDC workload identity federation for staging pipelines' with bulleted acceptance criteria. Then create 3 linked child Tasks under it:
> 1. Refactor service connection in Bicep
> 2. Update `pipelines/ci-validation.yml`
> 3. Validate token exchange in staging"

---

## 3. Batch Sprint Rollover (Preview-Then-Execute Pattern)
**Step 1 — Dry-Run Preview:**
> "Find all `Active` and `New` tasks in the current sprint for `Platform-Engineering-Team` that have 0 completed work hours. Present a Markdown preview table showing their ID, Title, Current Iteration, and Proposed Iteration (next sprint). Do NOT update any work items yet."

**Step 2 — Confirmed Execution:**
> "The preview table looks right. Proceed with `wit_update_work_items_batch` to move those items to the next sprint, and add a comment on each item: 'Rolled over during sprint boundary triage via ADO MCP'."

---

## 4. Create Traceable Pull Requests & Manage Review Threads
> "Create a draft Pull Request from branch `feature/oidc-pipeline` into `main` in the `Enterprise-Platform` repo. Summarize the recent commits in the PR description, link the PR to Work Item #1042, and add the platform lead as a required reviewer."

> "List all active comment threads on Pull Request #88 in `Enterprise-Platform` and summarize which files still need changes."

---

## 5. Trigger Pipelines & Run Two-Step Log Diagnostics
> "Trigger the `ci-validation.yml` pipeline on branch `feature/oidc-pipeline` with `runExtendedChecks` set to `true`, and report the initial build status."

> "Inspect the latest failed run of `ci-validation.yml`. First, list the build log index to identify which specific task failed. Second, retrieve only the log content for that failing task ID, explain the root cause, and draft a linked Bug work item under our active User Story."