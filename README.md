# Configuring Codium AI for GitHub Actions PR Assistant

Welcome to the setup guide for integrating Codium AI as a Pull Request (PR) assistant in your GitHub Actions workflow. Codium AI can help automate code reviews and enhance collaboration within your development team. Follow the steps below to configure Codium AI seamlessly.

## Prerequisites

Before you begin, ensure that you have:

- A GitHub repository with your source code.
- An Open AI account with access to GPT-4. If you don't have one, sign up [here](https://chat.openai.com/).
- A GitHub\GitLab\BitBucket personal access token (classic) with the repo scope.

## GitHub Actions Workflow

Open or create your GitHub Actions workflow file (e.g., `.github/workflows/main.yml`). Add the following steps to integrate Codium AI into your workflow:

```yaml
name: "OpenAI PR Agent"

on:
  pull_request:
  issue_comment:
jobs:
  pr_agent_job:
    runs-on: ubuntu-latest
    permissions:
      issues: write
      pull-requests: write
      contents: write
    steps:
      - name: PR Agent action step
        id: pragent
        uses: Codium-ai/pr-agent@v0.8
        env:
          OPENAI_KEY: ${{ secrets.OPENAI_KEY }}
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
```


This workflow is triggered when a pull request is opened, synchronized, or reopened. It installs the Codium AI CLI, reviews the PR, and provides feedback.

## OpenAI API Token

To securely use Codium AI in your workflow, add your OpenAI API Key as a secret in your GitHub repository.

1. Go to your repository on GitHub.
2. Navigate to `Settings` > `Secrets` > `New repository secret`.
3. Name the secret `OPENAI_KEY` and paste your OpenAI API Key.

```
Name = OPENAI_KEY
Secret = <your key>
```
You can also create new API keys by [visiting here](https://platform.openai.com/api-keys) and Clicking "Create new secrte key"  

The GITHUB_TOKEN secret is automatically created by GitHub.

## Usage

Now, whenever a pull request is created or updated, Codium AI will automatically analyze the changes and provide feedback as comments in the PR.  

It will also make an analysis on every comment in the PR with the specific trigger command

## Customization

Feel free to customize the workflow and Codium AI parameters based on your project's requirements. For more details on available Codium AI CLI options, refer to the [official documentation](https://docs.codium.team/).

## Conclusion

Congratulations! You have successfully configured Codium AI as a PR assistant in your GitHub Actions workflow. Enhance your code review process and collaboration with the power of Codium AI.

Happy coding! 🚀🤖
