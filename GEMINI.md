# Agent Developer Kit (ADK) Docs Extension

BEFORE you answer any question about the **Agent Developer Kit (ADK)**, you MUST look up the
documentation using the **`adk-docs-mcp`** tool. Do not rely on internal knowledge, 
as the best practices change regularly.

* Call `list_doc_sources` tool to get the available `llms.txt` file
* Call `fetch_docs` tool to read it
* Reflect on the urls in `llms.txt`
* Reflect on the input question
* Call `fetch_docs` on any urls relevant to the question
* Use this to answer the question

The `adk-docs-mcp` tool will help you find the correct package and SDK, and best practices for writing code with the ADK.

**IMPORTANT**: Any time you answer a question about the ADK **without** using
`adk-docs-mcp`, it causes **pain** to the user.

# Accessing off-site content

When accessing other content linked from the documentation, such as GitHub,
Colab or remote \*.ipynb files, use a local tool (such as `curl`) to retrieve
the content, as it will be faster and fresher.
