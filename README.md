# ADK Docs Extension for Gemini CLI

This extension provides documentation support for using the [Agent Development Kit (ADK)](https://google.github.io/adk-docs/).

## Repo Metadata

Author: Darren Lester

## How It Works

This Gemini CLI extension uses the [MCP LLMS-TXT Doc Server](https://pypi.org/project/mcpdoc/) to provide the Gemini model with up-to-date information about the ADK. The documentation content is sourced from the `llms.txt` file in the [official ADK-Docs](https://github.com/google/adk-docs) repo. This file is effectively a sitemap of the documentation available in that repo.

The extension's `GEMINI.md` file provides instructions to the Gemini model, guiding it to use the tools provided by this extension when answering questions about the ADK.

## Why Is This Useful?

This extension empowers Gemini CLI to provide accurate and current information about the ADK, without relying on potentially outdated internal knowledge. This is particularly useful for:

*   Answering questions about the ADK's features and APIs.
*   Assisting with development tasks related to the ADK.
*   Ensuring that the information provided by the Gemini CLI is consistent with the latest ADK documentation.

## Extension Installation into Gemini CLI

The easiest way to install this extension is with this command:

```bash
gemini extensions install https://github.com/derailed-dash/adk-docs-ext
```

The command will respond with: 

`Extension "adk-docs-ext" installed successfully and enabled.`

Alternatively, you can clone this repo directly into your `extensions` folder.

For global installation:

```bash
mkdir -p ~/.gemini/extensions
git clone https://github.com/derailed-dash/adk-docs-ext.git ~/.gemini/extensions/adk-docs-ext
```

For workspace-level installation:

```bash
mkdir -p ./.gemini/extensions
git clone https://github.com/derailed-dash/gemini-docs-ext.git ./.gemini/extensions/adk-docs-ext
```

Gemini CLI will automatically load the extension on startup and will then use the relevant tools to answer any questions relating to the ADK.

### Using an Alternative `llms.txt` Path

At this point in time, the `llms.txt` in the [ADK-Docs repo](https://github.com/google/adk-docs) isn't a proper site map with links and link summaries. Until this is resolved, you may prefer to specify a local location for your `llms.txt`. I have created a more useful `llms.txt` in the `sample_llms_txt` folder.

To use it, amend the `gemini-extension.json` and replace this:

```json
    "--urls",
    "https://raw.githubusercontent.com/google/adk-docs/main/llms.txt",
```

with this:

```json
    "--urls",
    "Local_ADK_Docs:/path/to/local/llms.txt",
```

E.g. if you're using the provided sample:

```json
{
  "name": "adk-docs-ext",
  "version": "1.0.0",
  "mcpServers": {
    "adk-docs-mcp": {
      "command": "uvx",
      "args": [
        "--from",
        "mcpdoc",
        "mcpdoc",
        "--urls",
        "Local_ADK_Docs:${extensionPath}/sample_llms_txt/local_adk_docs_llms.txt",
        "--allowed-domains",
        "*",
        "--transport",
        "stdio"
      ]
    }
  },
  "contextFileName": "GEMINI.md"
}

```

## Acknowledgements

This extension was inspired by the [gemini-docs-ext](https://github.com/markmcd/gemini-docs-ext) by Mark McDonald.