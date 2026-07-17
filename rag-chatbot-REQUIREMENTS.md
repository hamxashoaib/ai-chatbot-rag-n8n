# Requirements

## Platform
- n8n (self-hosted or n8n Cloud), version 1.60+ recommended for LangChain node compatibility

## Credentials Needed
- OpenAI API key (for Chat Model and Embeddings nodes)
  - Get one at: https://platform.openai.com/api-keys
  - Alternatively, n8n Cloud users can use the built-in free OpenAI credits for testing

## n8n Community Nodes / Packages
No additional installation needed if using n8n Cloud, the LangChain nodes used in this workflow (`@n8n/n8n-nodes-langchain`) are included by default in recent n8n versions.

If self-hosting an older n8n instance, install with:
```
npm install n8n-nodes-langchain
```

## Files in This Repo
- `rag-chatbot.json`: The exported n8n workflow, ready to import
- `README.md`: Project overview and setup instructions
