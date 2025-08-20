## Step 3: Combine with Other Actions

Excellent! You've learned how to make AI workflows interactive with dynamic context. Now let's create a truly powerful workflow by combining AI inference with other GitHub Actions.

### 📖 Theory: AI-Powered Repository Automation

The GitHub marketplace offers numerous actions that can provide context for AI inference. By combining these actions with AI inference, you can create powerful AI-enabled, context-rich workflows that automate intelligent repository management tasks.

Key concepts:

- GitHub Actions can gather repository data (issues, pull requests, files) and pass it to AI for analysis
- The `actions/github-script` action provides access to the GitHub REST API for data collection
- AI can analyze patterns, suggest improvements, and provide insights based on repository context
- Combining multiple actions creates workflows that are both data-driven and intelligent

**Learn more:**

- [GitHub Script Action](https://github.com/actions/github-script)
- [GitHub REST API](https://docs.github.com/en/rest)
- [Issues API](https://docs.github.com/en/rest/issues)

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

- Use `on: issues: types: [opened]` to trigger on new issues
- Include all required permissions: `models: read`, `issues: write`, `contents: read`
- Use `actions/github-script` to access the GitHub API and gather issue data
- Pass the collected data to `actions/ai-inference` for analysis
- Use `GrantBirki/comment` to post the AI analysis as an issue comment

</details>
