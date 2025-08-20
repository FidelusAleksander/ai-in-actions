## Step 1: Introduction to AI Actions

Welcome to AI in Actions! In this exercise, you'll learn to integrate AI capabilities directly into your GitHub Actions workflows using GitHub Models. Let's start by creating your first AI-powered workflow.

### 📖 Theory: GitHub Models in Actions

GitHub Actions can integrate with AI models through the GitHub Models service, which provides access to various AI models via the inference API at `https://models.github.ai/inference`. The built-in `GITHUB_TOKEN` is used to authorize calls to this service, eliminating the need for additional API keys or authentication setup.

Key concepts to understand:

- The `models: read` permission grants the `GITHUB_TOKEN` access to GitHub Models inference API for making AI requests
- You can interact with GitHub Models in multiple ways:
  - **Direct API calls** using `curl` with the `GITHUB_TOKEN` for custom implementations
  - **GitHub CLI extension** (`gh models`) for command-line AI interactions  
  - **Ready-to-use GitHub Actions** like `actions/ai-inference` for workflow integration
  - **Custom Actions** that you build for scenario-specific AI workflows
- For this exercise, we'll use the `actions/ai-inference` action as it provides the simplest integration path
- AI in workflows is most useful for tasks requiring content analysis, text processing, and intelligent decision-making
- For deterministic operations like file manipulation or environment setup, regular actions remain more appropriate
- The `actions/ai-inference` action supports both inline prompts and system prompts for controlling AI behavior

Learn more about [GitHub Models Documentation](https://docs.github.com/en/github-models), [Integrating AI models into your development workflow](https://docs.github.com/en/github-models/use-github-models/integrating-ai-models-into-your-development-workflow), [AI Inference Action](https://github.com/actions/ai-inference), [GitHub CLI Models Extension](https://github.com/github/gh-models), and [GitHub Actions Permissions](https://docs.github.com/en/actions/tutorials/authenticate-with-github_token#modifying-the-permissions-for-the-github_token).

### ⌨️ Activity: Create Your First AI Workflow

1. Create a new workflow file `.github/workflows/ask-ai.yml`

1. Set up the workflow with `workflow_dispatch` trigger for manual testing

1. Configure the job with `models: read` permission

1. Add a step using `actions/ai-inference@v2` with a simple prompt asking "What is the meaning of life?"

1. Display the AI response using `$GITHUB_STEP_SUMMARY` to create a nicely formatted output

1. Commit and push your workflow file

### ⌨️ Activity: Test Your AI Workflow

1. Navigate to the Actions tab in your repository

1. Find the "Ask AI" workflow and click "Run workflow"

1. Trigger the workflow manually and wait for it to complete

1. Check the workflow run summary to see the AI's response displayed

<details>
<summary>Having trouble? 🤷</summary><br/>

- Make sure your workflow file is saved in the correct location: `.github/workflows/ask-ai.yml`
- Verify that the `models: read` permission is added to the job level
- Check that you're using the correct action name: `actions/ai-inference@v2`
- If the workflow doesn't appear in the Actions tab, try refreshing the page after committing

</details>
