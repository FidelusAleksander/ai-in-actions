## Step 2: Using Dynamic Context

Great work! You've successfully created your first AI-powered workflow. Now let's make it more interactive and useful by adding dynamic context.

### 📖 Theory: Dynamic Context and System Prompts

Dynamic context allows you to parameterize prompts with workflow data, user inputs, or repository information, making AI responses more relevant and useful. System prompts provide additional control over AI behavior and personality.

Key concepts:

- Workflow inputs can be passed to AI prompts to create interactive, user-driven workflows
- System prompts allow you to define the AI's role, personality, and response style
- GitHub context variables (`github.actor`, `github.repository`, etc.) provide repository-specific information
- Environment variables and step outputs can be incorporated into prompts for richer context
- Dynamic prompts enable AI to provide personalized and contextually relevant responses

**Learn more:**

- [GitHub Actions Context](https://docs.github.com/en/actions/learn-github-actions/contexts)
- [Workflow Inputs](https://docs.github.com/en/actions/using-workflows/workflow-syntax-for-github-actions#onworkflow_dispatchinputs)
- [AI Inference System Prompts](https://github.com/actions/ai-inference#system-prompts)

### ⌨️ Activity: Enhance with Dynamic Context

1. Update your existing `.github/workflows/ask-ai.yml` file to make it more interactive
1. Modify the workflow trigger to `workflow_dispatch` with an input parameter called `question` of type `string`
1. Add a creative `system-prompt` that gives the AI a unique personality (e.g., pirate, teacher, or expert)
1. Update the AI inference step to use the user-provided question: `${{ inputs.question }}`
1. Keep the `$GITHUB_STEP_SUMMARY` output format for consistent display
1. Commit and push your updated workflow file

### ⌨️ Activity: Test Dynamic Context

1. Navigate to the Actions tab and find your "Ask AI" workflow
1. Click "Run workflow" and notice the new input field for your question of your choosing
1. Check the workflow run summary to see the AI's response displayed

<details>
<summary>Having trouble? 🤷</summary><br/>

- Use `workflow_dispatch` with `inputs:` to define user input parameters
- The `system-prompt` parameter in `actions/ai-inference` controls the AI's personality
- Reference workflow inputs using `${{ inputs.parameter_name }}` syntax
- Make sure to commit and push your changes before testing the workflow

</details>
