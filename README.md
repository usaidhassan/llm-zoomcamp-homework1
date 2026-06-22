# Agentic RAG Homework 1 – LLM Zoomcamp

This project is my implementation of Homework 1: Agentic RAG from the LLM Zoomcamp course by DataTalksClub.
It demonstrates how to build a full RAG pipeline from scratch, then progressively enhance it into:

* Chunked retrieval
* Token-efficient RAG
* Tool-using agent (agentic loop)

## 📌 Project Overview

The system uses course lesson markdown files from the GitHub repository (fixed commit `8c1834d`) as the knowledge base.
Main components:

* GitHub-based document loader (`gitsource`)
* Keyword search index (`minsearch`)
* Basic RAG pipeline
* Chunked RAG optimization
* Agent with tool usage (`toyaikit`)
* OpenAI model (`gpt-5.4-mini` via gateway)

## 🧪 Key Results

### Q1 – Dataset size

* Lesson pages: `72`

### Q2 – Retrieval (MinSearch)

Query:
> How does the agentic loop keep calling the model until it stops?

* Top result file:

```
01-agentic-rag/lessons/14-agentic-loop.md
```

### Q3 – RAG token usage

* Input tokens: `7104`

This measures full prompt size including retrieved context.

### Q4 – Chunking

Using sliding window chunking:

* `size = 2000`
* `step = 1000`
* Total chunks: `295`

### Q5 – Chunked RAG efficiency

* Original tokens: `7104`
* Chunked tokens: `2315`
* Reduction: ~3× fewer tokens

Chunking significantly reduces prompt size while preserving relevant context.

### Q6 – Agentic loop tool calls

Built an agent using `toyaikit` with a `search` tool over chunked index.

* Number of tool calls: `3`

## 🧠 What I Learned

* How RAG pipelines are structured (search → context → LLM)
* Why chunking improves retrieval efficiency
* How token usage directly depends on retrieved context size
* How agentic systems repeatedly call tools until a stopping condition
* How frameworks like `toyaikit` abstract the agent loop

## ⚙️ Tech Stack

* Python 3.12
* OpenAI API (`gpt-5.4-mini`)
* gitsource (GitHub document loader)
* minsearch (text retrieval)
* toyaikit (agent framework)
* dotenv (environment management)

## 🚀 How It Works (Pipeline)

1. Load markdown lessons from GitHub repo snapshot
2. Index documents using keyword search
3. Build baseline RAG system
4. Add token tracking
5. Apply chunking for better retrieval
6. Build agent with tool-based search
7. Let model decide when to search

## 📂 Structure

```
.
├── documents (GitHub lesson pages)
├── minsearch index
├── chunked index
├── rag() baseline system
├── chunk_rag() optimized system
└── agent (toyaikit tool-based loop)
```

## 📊 Summary

This assignment shows the evolution from:
**Simple RAG → Optimized RAG → Agentic RAG**
and highlights the trade-offs between:

* accuracy
* token cost
* system flexibility
