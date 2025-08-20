## Step 3: Combine with Other Actions

Excellent! You've mastered the basics of AI workflows. Now let's build something truly powerful by combining AI inference with other GitHub Actions to create intelligent automation.

### 📖 Theory: AI-Powered Automation

The GitHub marketplace offers numerous actions that can provide context for AI inference. By combining these actions with AI inference, you can create powerful AI enabled, context rich workflows.

Key concepts to understand:

- GitHub Actions can fetch repository data using actions like `actions/github-script`
- The GitHub REST API provides access to issues, pull requests, commits, and other repository data
- AI models can analyze and compare textual content to find patterns and similarities
- Combining data retrieval with AI analysis creates intelligent automation workflows
- Action outputs can be chained together to build complex, multi-step workflows

> [!TIP]
> Explore the [GitHub Script Action](https://github.com/actions/github-script), [GitHub REST API](https://docs.github.com/en/rest), and [Issues API](https://docs.github.com/en/rest/issues) to understand the data sources available for your AI workflows.

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

- Ensure your workflow has the correct trigger: `on: issues: types: [opened]`
- Check that all required permissions are set: `issues: write`, `contents: read`, `models: read`
- Verify the `github-script` action is fetching issue data correctly
- Make sure the AI inference step receives formatted data from the previous step
- Test the comment action by checking if comments appear on your issues

</details>
