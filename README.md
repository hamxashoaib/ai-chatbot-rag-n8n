# AI-Powered Chatbot using RAG
![n8n](https://img.shields.io/badge/n8n-workflow-orange)
![OpenAI](https://img.shields.io/badge/OpenAI-GPT--4o--mini-blue)
![LangChain](https://img.shields.io/badge/LangChain-RAG-green)

An AI chatbot built in n8n that answers questions using Retrieval-Augmented Generation (RAG). Instead of relying only on the language model's built-in knowledge, the chatbot retrieves relevant information from a connected knowledge base before generating a response — reducing made-up answers and keeping replies grounded in real data.

## How It Works

The workflow is split into two parts:

**1. Live Chat Flow**
Runs every time a user sends a message.
`Chat Trigger → RAG Agent → Knowledge Base Retriever (Tool) → Response`
The agent searches the knowledge base for relevant context, then answers using that information along with conversation memory for follow-up questions.

**2. Knowledge Base Setup (One-Time)**
Loads source content into the vector store so the chatbot has something to retrieve from.
`Manual Trigger → Source Data → Knowledge Base Ingest → Text Splitter → Embeddings`
This only needs to run once, or again whenever the knowledge base content is updated.

## Tech Stack

- **n8n** → workflow automation and orchestration
- **LangChain (via n8n)** → RAG Agent, vector store, memory, and document loader nodes
- **OpenAI** → chat model and embeddings
- **In-memory vector store** → for retrieval

## Demo Content

For demonstration purposes, the knowledge base is loaded with FAQ content about a fictional company, "TechNova Inc.," covering its products, pricing, and support details. This makes it easy to verify the RAG pipeline is retrieving real data rather than generating a generic answer.  uestions about TechNova can only be answered correctly if the retrieval step is actually working.

## Example Questions

| Question | Expected Answer Source |
|---|---|
| "What pricing plans does TechNova offer?" | Retrieved from knowledge base |
| "What is TechNova's main product called?" | Retrieved from knowledge base |
| "Does TechNova have an office in Dubai?" | Model should say it doesn't have that information, rather than guessing |

## Setup

1. Import `rag-chatbot.json` into n8n
2. Add your OpenAI credential to the **Chat Model** and **Embeddings** nodes
3. Run the **Knowledge Base Setup** flow once (click "Execute workflow" on that section) to load the demo content
4. Open the chat panel on the **Live Chat Flow** section and start asking questions

## Notes

- The in-memory vector store resets when the n8n instance restarts. If this happens, re-run the Knowledge Base Setup flow.
- To use this with real content instead of the demo FAQ, replace the text in the source data node with your own documents.

## Screenshots

![Workflow Screenshot](Workflow%20Image/Screenshot.png)

## Key Learnings

- Structuring a RAG pipeline in n8n as two separate flows (live chat vs. one-time data ingestion) instead of one reusable node with manual mode-switching
- Debugging real integration issues (credential setup, vector store connection requirements) rather than just following a tutorial end-to-end
- Testing retrieval accuracy using content the model couldn't already know, to confirm the RAG step was actually working and not just guessing

## Future Improvements

- Swap the in-memory vector store for a persistent one (e.g., Pinecone or Supabase) so data survives restarts
- Connect to a real knowledge base instead of demo FAQ content
- Add a fallback response for questions outside the knowledge base scope

## About Me

I'm **Hamza Shoaib**, a BS Artificial Intelligence student at The Islamia University of Bahawalpur, focused on AI agents, automation, and applied GenAI. I built this project as part of my ongoing freelance and portfolio work in AI-powered automation using n8n.

- LinkedIn: [linkedin.com/in/ch-hamza-shoaib](https://linkedin.com/in/ch-hamza-shoaib)
- GitHub: [github.com/hamxashoaib](https://github.com/hamxashoaib)
