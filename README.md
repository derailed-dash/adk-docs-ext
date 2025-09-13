# ADK Docs Extension for Gemini CLI

This extension provides documentation support for using the [Agent Development Kit (ADK)](https://google.github.io/adk-docs/).

## Repo Metadata

Author: Darren Lester

## How It Works

This extension uses a MCP server to provide the Gemini model with up-to-date information about the ADK. The documentation content is sourced from the `llms.txt` file in the [official ADK-Docs](https://github.com/google/adk-docs) repo. 
This file is effectively a sitemap of the documentation available in that repo.

The extension's `GEMINI.md` file provides instructions to the Gemini model, guiding it to use the tools provided by this extension when answering questions about the ADK.

## Why Is This Useful?

This extension empowers Gemini CLI to provide accurate and current information about the ADK, without relying on potentially outdated internal knowledge. This is particularly useful for:

*   Answering questions about the ADK's features and APIs.
*   Assisting with development tasks related to the ADK.
*   Ensuring that the information provided by the Gemini CLI is consistent with the latest ADK documentation.

## Gemini CLI installation

You can clone the repository directly into your Gemini CLI extensions directory. Choose between a global installation (available to your user everywhere) or a local installation (for the current workspace/project).

### Global Installation
```bash
mkdir -p ~/.gemini/extensions
git clone https://github.com/derailed-dash/adk-docs-ext.git ~/.gemini/extensions/adk-docs-ext
```

### Workspace Installation
```bash
mkdir -p ./.gemini/extensions
git clone https://github.com/derailed-dash/gemini-docs-ext.git ./.gemini/extensions/adk-docs-ext
```

Gemini CLI will automatically load the extension on startup.

## Acknowledgements

This extension was inspired by the [gemini-docs-ext](https://github.com/markmcd/gemini-docs-ext) by Mark McDonald.