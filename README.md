# 📄 RAG Solution for PDF Question Answering with LangChain, OpenAI, and Chroma

This project implements a **Retrieval-Augmented Generation (RAG)** system using LangChain, OpenAI’s GPT-3.5-Turbo, and Chroma to answer user questions based on the content of a PDF file. It includes secure handling of environment variables via a `.env` file.

---

## 📚 Overview

- Loads a PDF file and splits it into manageable chunks.
- Stores vector embeddings of the chunks using ChromaDB.
- Retrieves relevant document pieces based on a user question.
- Sends those chunks to an LLM (GPT-3.5-Turbo) for a final answer.
- Uses `.env` file to safely manage the `OPENAI_API_KEY`.

---

## 🔐 Environment Setup

To avoid exposing your OpenAI API key in code, this project uses a `.env` file. Create a file named `.env` in the same directory as `Solucao RAG.ipynb`:

```bash
OPENAI_API_KEY=your-api-key-here
```

The notebook loads the key automatically with the following commands:

```python
%pip install python-dotenv
import dotenv
%load_ext dotenv
%dotenv
```

---

## 🛠️ Installation

Make sure you have the following Python packages installed:

```bash
pip install langchain langchain-openai langchain-community chromadb python-dotenv
```

---

## 🧠 How It Works

1. **Load and Split PDF**  
   The PDF is loaded and split into chunks using `RecursiveCharacterTextSplitter`.

2. **Store Embeddings**  
   Chunks are embedded using OpenAI and stored in a local Chroma vector store.

3. **Retrieve and Answer**  
   Given a user question, relevant chunks are retrieved, and a chain calls the LLM to produce a final answer.

---

## 🧩 Key Components

| Function | Description |
|---------|-------------|
| `ask(question)` | Retrieves relevant document chunks and generates an answer using GPT-3.5 |
| `load_qa_chain(...)` | Loads a prompt/response chain to work with LangChain |
| `Chroma(...)` | Used for persisting and retrieving vector data |

---

## 🧪 Example

```text
User: What is mentioned in the document about data privacy?
Answer: <LLM-generated response>
```

---

## 📂 File Structure

```
.
├── Solucao RAG.ipynb     # Main notebook
├── DOC-....pdf           # PDF used for QA
├── text_index/           # Folder with Chroma vector index
└── .env                  # Environment variable file (not shared)
```

---

## 📝 Notes

- The current setup uses a hardcoded PDF. Update the path if needed.
- Responses are best suited for structured legal or technical documents.
- Designed to be run inside a Jupyter Notebook environment.

