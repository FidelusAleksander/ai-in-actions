## Step 3: Combine with Other Actions

Excellent! Now you have an interactive AI workflow. Let's take it to the next level by combining AI inference with other GitHub Actions to create a practical, intelligent automation system that analyzes new issues.

### 📖 Theory: Building Intelligent Workflows

The GitHub marketplace offers numerous actions that can provide context for AI inference. By combining these actions with AI inference, you can create powerful AI-enabled, context-rich workflows.

When building intelligent workflows, consider:

- Using `actions/github-script` to interact with GitHub's REST API and gather repository data
- Formatting data appropriately before passing it to AI models for analysis
- Combining multiple data sources (issues, pull requests, repository content) for richer context
- Using the AI's analysis to trigger other actions like commenting, labeling, or creating tasks

Learn more about [GitHub Script Action](https://github.com/actions/github-script), [GitHub REST API](https://docs.github.com/en/rest), and [Issues API](https://docs.github.com/en/rest/issues).

### ⌨️ Activity: Create Issue Analysis Workflow

1. Create a new workflow `.github/workflows/issue-analyzer.yml` that triggers on `issues: opened`

1. Add permissions for `issues: write`, `contents: read`, and `models: read`

1. Add a step using `actions/github-script` to:
   - Get the current issue title and body
   - Search for a few recent open issues in the repository
   - Format the issue data for AI analysis

1. Use `actions/ai-inference` to analyze the new issue against existing issues for potential similarities

1. Use `GrantBirki/comment` to post a comment with the AI analysis results

1. Commit and push your issue analyzer workflow file

### ⌨️ Activity: Test Your Issue Analysis Workflow

1. Create a test issue with a title like "Bug: Login page not loading" and describe a common web application problem

1. Observe the workflow execution in the Actions tab to ensure it triggers automatically when the issue is created

1. Check that the AI analysis comment appears on your test issue

<details>
<summary>Having trouble? 🤷</summary><br/>

- Make sure the workflow file is saved as `.github/workflows/issue-analyzer.yml`
- Verify all required permissions are set: `issues: write`, `contents: read`, and `models: read`
- Check that the `actions/github-script` step properly formats the data for the AI
- Ensure the `GrantBirki/comment` action has the correct repository and issue number parameters
- If the workflow doesn't trigger, verify the event trigger is set to `issues: opened`

</details>
