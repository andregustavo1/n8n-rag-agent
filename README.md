# RAG Agent with Supabase + OpenAI + n8n

This repository contains a no-code workflow built in n8n that allows you to feed data into a Supabase vector database and ask questions via an OpenAI-powered agent using RAG (Retrieval-Augmented Generation).

## 🧠 Problem Solved

It enables users to build powerful AI assistants that respond based on private or external documents. Ideal for internal knowledge bases, document Q&A, and chatbots backed by your own data.

## 💡 Workflow Summary

The system is divided into two main flows:

### 🔴 Feed Database

- **Trigger**: Manually triggered (or could be adapted to run on file upload).
- **Text Input**: Accepts text that will be embedded (e.g., book, article, document, etc).
- **Splitter**: Uses a recursive character text splitter to divide content into chunks.
- **Embedding**: Sends the chunks to OpenAI to generate vector embeddings.
- **Storage**: Saves the embeddings in a Supabase Vector Store for later retrieval.

> 🛠️ Easily adaptable to handle files like PDFs, spreadsheets, web content, or any other structured input.

### 🔵 Ask with AI (RAG Agent)

- **Trigger**: Starts when a chat message is received.
- **AI Agent**: Uses an n8n "AI Agent" node configured with:
  - OpenAI Chat Model (for generation)
  - Postgres-based memory (for context persistence)
  - Tool calling to query the vector database
- **Retrieval**: Queries Supabase to fetch relevant document vectors.
- **Response**: The agent generates a contextual answer using the retrieved information.


## 📸 Workflow Preview
![image](https://github.com/user-attachments/assets/f999b84c-f853-4221-bf79-791f9bae3d08)

