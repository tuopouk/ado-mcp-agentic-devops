# Azure DevOps MCP Server — Workday Prompt Playbook

Copy and paste these prompts into **GitHub Copilot Chat (Agent Mode)** while following the examples in the blog post.

---

## Sanity Check: Verify Login & Sprint Dates
> "Which projects exist in my Azure DevOps organization, and what are the start and end dates of the current sprint for `Platform-Engineering-Team` in `Enterprise-Platform`?"

---

## Example 1: Morning Standup Prep
> "Show me all work items in our current sprint grouped by state. Flag any Active tasks that don't have an owner yet, and list any Bugs that are missing story points."

---

## Example 2: Create a User Story with Linked Child Tasks
> "In `Enterprise-Platform`, create a User Story in the current sprint titled 'Enforce OIDC workload identity federation for staging pipelines' with bulleted acceptance criteria. Then create 3 child Tasks underneath it:
> 1. Refactor service connection in Bicep
> 2. Update `pipelines/ci-validation.yml`
> 3. Validate token exchange in staging"

---

## Example 3: Safe Sprint Rollover (Preview First, Execute Second)
**Step A — Dry-Run Preview:**
> "Find all `Active` tasks in the current sprint that have 0 completed hours. Show me a Markdown table with their ID, Title, Current Sprint, and Proposed Next Sprint. Do NOT update anything yet."

**Step B — Confirmed Batch Update:**
> "That table looks right. Run the batch update to move those items to the next sprint, and leave a comment on each item: 'Rolled over during sprint planning'."

---

## Example 4: Open a Traceable Pull Request
> "Create a draft Pull Request from `feature/oidc-pipeline` into `main` in the `Enterprise-Platform` repo. Summarize our YAML changes in the description, link it to Work Item #1043, and assign our platform lead as a reviewer."

---

## Example 5: Two-Step Pipeline Log Troubleshooting
> "Check the latest failed run of `ci-validation.yml`. First check the build log index to find which task failed, then fetch only the log lines for that failed task and tell me what broke."