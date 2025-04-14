<!--
Title: Task Master AI Overview
Author: Eyal Toledano (@eyaltoledano), Ralph Khreish (@Crunchyman-ralph)
Description: Summary and setup guide for the Task Master AI task management system.
Target Models: N/A (Documentation)
Category: Documentation
Version: 1.0
Date Added: 2025-04-14
-->

# Task Master AI Overview

## Source
[eyaltoledano/claude-task-master on GitHub](https://github.com/eyaltoledano/claude-task-master)

## Description
Task Master AI is an AI-powered task management system designed for AI-driven development workflows, particularly within editors like Cursor AI. It helps manage project tasks by leveraging AI (specifically Claude) for generation, expansion, and prioritization.

## Authors
- Eyal Toledano ([@eyaltoledano](https://github.com/eyaltoledano))
- Ralph Khreish ([@Crunchyman-ralph](https://github.com/Crunchyman-ralph))

## Requirements
- Anthropic API key (for Claude)
- OpenAI SDK (Optional, for Perplexity API integration)

## Quick Start (MCP - Recommended for Editors like Cursor)

1.  **Install Globally:**
    ```bash
    npm i -g task-master-ai
    ```
2.  **Configure MCP in Editor:** Add the following to your editor's MCP settings (e.g., Cursor's `settings.json`):
    ```json
    {
        "mcpServers": {
            "taskmaster-ai": {
                "command": "npx",
                "args": ["-y", "task-master-mcp"],
                "env": {
                    "ANTHROPIC_API_KEY": "YOUR_ANTHROPIC_API_KEY_HERE",
                    "PERPLEXITY_API_KEY": "YOUR_PERPLEXITY_API_KEY_HERE", // Optional
                    "MODEL": "claude-3-opus-20240229", // Or other supported Claude model
                    "PERPLEXITY_MODEL": "sonar-large-32k-online", // Optional
                    "MAX_TOKENS": 4000,
                    "TEMPERATURE": 0.2
                    // Other optional env vars like DEFAULT_SUBTASKS, DEFAULT_PRIORITY
                }
            }
        }
    }
    ```
    *Replace API keys and adjust model names as needed.*
3.  **Enable MCP:** Activate the MCP server in your editor.
4.  **Initialize via Prompt:** Ask your AI assistant:
    `Can you please initialize taskmaster-ai into my project?`
5.  **Use Commands via Prompt:**
    - `Can you parse my PRD at scripts/prd.txt?`
    - `What's the next task I should work on?`
    - `Can you help me implement task 3?`
    - `Can you help me expand task 4?`

## Quick Start (Command Line)

1.  **Install:**
    ```bash
    # Globally
    npm install -g task-master-ai
    # Or Locally
    npm install task-master-ai
    ```
2.  **Initialize Project:**
    ```bash
    # If global
    task-master init
    # If local
    npx task-master-init 
    ```
3.  **Common Commands:**
    ```bash
    task-master parse-prd <path-to-prd.txt>
    task-master list
    task-master next
    task-master generate
    ```

## Licensing
MIT License with Commons Clause:
- **Allowed:** Use, modify, distribute, build products using it.
- **Not Allowed:** Sell Task Master itself, offer it as a hosted service, create competing products based directly on it.

*Refer to the full [LICENSE](https://github.com/eyaltoledano/claude-task-master/blob/main/LICENSE) file for details.* 