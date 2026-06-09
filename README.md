# AI GitHub Repository Analyzer

An AI-powered n8n workflow that analyzes GitHub repositories using local LLMs through LM Studio. The workflow retrieves repository metadata and README content, then generates a project summary, identifies key technologies, and extracts the main features of the project.

## Features

* Retrieves repository metadata from the GitHub API
* Downloads and analyzes README files
* Extracts programming languages, frameworks, databases, and libraries
* Identifies key project features
* Generates AI-powered project summaries
* Supports webhook-based execution
* Runs entirely with a local LLM via LM Studio

## Tech Stack

* n8n
* LM Studio
* Qwen 3 8B
* GitHub REST API

## How It Works

1. A repository is submitted through a webhook request.
2. Repository metadata is fetched from GitHub.
3. The repository README is downloaded and processed.
4. A local LLM analyzes the content.
5. The workflow generates:

   * Project summary
   * Technologies used
   * Key features
6. Results are returned as structured JSON.

## Webhook Request

Send a POST request to:

```text
/webhook/analyze-repo
```

Request body:

```json
{
  "repo": "owner/repository"
}
```

Example:

```json
{
  "repo": "microsoft/semantic-kernel"
}
```

## Example Response

```json
{
  "repository": "owner/repository",
  "analysis": {
    "technologies": [
      "Technology 1",
      "Technology 2"
    ],
    "features": [
      "Feature 1",
      "Feature 2"
    ],
    "summary": "AI-generated project summary."
  },
  "status": "success"
}
```

## Getting Started

### Prerequisites

* n8n installed locally
* LM Studio installed
* Qwen 3 8B model loaded in LM Studio
* OpenAI-compatible API enabled in LM Studio

### Installation

1. Clone this repository.
2. Import `workflow.json` into n8n.
3. Configure the Chat Model nodes to use your LM Studio endpoint.
4. Start LM Studio and load the model.
5. Activate the workflow.
6. Send a POST request to the webhook endpoint.

## Screenshot

Place a workflow screenshot inside the `screenshots` folder and reference it below:

```md
![Workflow](screenshots/workflow_ss.png)
```

## License

MIT
