## Step 1: Introduction to AI Actions

In this exercise, you'll learn to integrate AI capabilities directly into your GitHub Actions workflows using GitHub Models. Let's start with understanding the key concepts and then straight to creating your first AI-powered workflow!

### 📖 Theory: GitHub Models in Actions

#### 🤖 What is GitHub Models?

**[GitHub Models](https://docs.github.com/github-models)** is a service that provides a curated catalog of AI models from leading providers. Among its many use cases, GitHub Models includes an inference API available at `https://models.github.ai/inference` that allows developers to integrate AI capabilities directly into their GitHub workflows and applications.

#### ⚙️ How GitHub Actions work with GitHub Models

The [integration](https://docs.github.com/en/github-models/use-github-models/integrating-ai-models-into-your-development-workflow#using-ai-models-with-github-actions) between GitHub Actions and GitHub Models is designed to be seamless:

- 🔑 **Built-in Authentication**: The GitHub Actions built-in [`GITHUB_TOKEN`](https://docs.github.com/en/actions/tutorials/authenticate-with-github_token#modifying-the-permissions-for-the-github_token) can be used to authorize calls to the GitHub Models service, eliminating the need for additional API keys or complex authentication setup with third party providers.

- 🔐 **Simple Permissions**: The [`models: read`](https://docs.github.com/en/actions/tutorials/authenticate-with-github_token#modifying-the-permissions-for-the-github_token) permission grants the `GITHUB_TOKEN` access to the GitHub Models inference API for making AI requests.

- 🎯 **Easy Integration**: The official [actions/ai-inference](https://github.com/actions/ai-inference) action provides a very simple path to using GitHub Models in GitHub Actions.

> [!TIP]
>
> Want to dive deeper? Check out these resources:
>
> - 📖 [GitHub Models Documentation](https://docs.github.com/en/github-models)
> - ⚡ [Rate Limits](https://docs.github.com/en/github-models/use-github-models/prototyping-with-ai-models#rate-limits) and [Moving Beyond Free Limits](https://github.blog/changelog/2025-06-24-github-models-now-supports-moving-beyond-free-limits/) for GitHub Models

### ⌨️ Activity: Create Your First AI Workflow

Now that you understand the concepts, let's put them into practice! Open a new tab of this repository to follow these steps.

Let's create a simple workflow that we can trigger manually from the GitHub UI.

1. Navigate to the `Code` tab of your repository. Then into `.github/workflows/` directory.

1. Click `Add File` and create a new workflow file named

   ```text
   ask-ai.yml
   ```

1. Start by adding the workflow name, manual event trigger and required permissions:

   ```yaml
   name: Ask AI
   on:
     workflow_dispatch:

   permissions:
     models: read
   ```

   > ❗ **Caution:** Copy the contents as provided, as this exact workflow name (`Ask AI`) is required to progress to next steps of this exercise.

1. Now we'll add a job that uses the AI inference action.

   In this simple scenario, we'll ask the AI a simple hardcoded question and display the response in the workflow summary:

   ```yaml
   jobs:
     ask-ai:
       runs-on: ubuntu-latest

       steps:
         - name: AI Inference
           id: ai-response
           uses: actions/ai-inference@v2
           with:
             token: {% raw %}${{ secrets.GITHUB_TOKEN }}{% endraw %}
             prompt: |
               Give me a programming joke.

         - name: Display AI Response
           run: |
             echo "## 🤖 AI Response" >> $GITHUB_STEP_SUMMARY
             echo "" >> $GITHUB_STEP_SUMMARY
             echo "{% raw %}${{ steps.ai-response.outputs.response }}{% endraw %}" >> $GITHUB_STEP_SUMMARY
   ```

   > ❗ **Caution:** Be mindful of YAML formatting! GitHub's file editor will show red underlines for certain YAML errors.

1. Commit the workflow file directly to the `main` branch.

### ⌨️ Activity: Test Your AI Workflow

Now let's test the workflow you just created to see AI in action!

1. Navigate to the **Actions** tab in your repository.

1. In the left sidebar, look for the **Ask AI** workflow in the workflow list and click on it.

1. Click the **Run workflow** button, keep the default branch selected, and click the green **Run workflow** button to trigger it.

1. Wait for the workflow to complete and check the workflow run summary to see the AI's response displayed in a nicely formatted way.

1. As your workflow completes successfully, Mona will automatically prepare the next step in your learning journey!

<details>
<summary>Having trouble? 🤷</summary><br/>

- **Workflow fails to run**: Ensure you're on a repository where you have write permissions and that GitHub Actions are enabled
- **No AI response**: Make sure the `id: ai-response` is set on the AI Inference step and referenced correctly in the Display step
- **Permission errors**: Double-check that the `models: read` permission is properly configured in your workflow file
- **Action not found**: Verify you're using the exact action name: `actions/ai-inference@v2`

</details>
