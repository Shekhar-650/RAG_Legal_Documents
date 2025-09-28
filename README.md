# RAG-on-Legal-Documents

A Retrieval-Augmented Generation (RAG) system for legal document intelligence — ingest legal documents, index them into vector storage, and build an interactive question-answering assistant that returns grounded, citeable responses.

> Lightweight, modular, and built for experimentation with vector databases, embeddings, and open/closed LLMs.

---

## Table of Contents

- [Overview](#overview)  
- [Features](#features)  
- [Architecture](#architecture)  
- [Getting Started](#getting-started)  
- [Installation](#installation)  
- [Usage](#usage)  
- [Ingesting Documents](#ingesting-documents)  
- [Indexing & Embeddings](#indexing--embeddings)  
- [Running the App](#running-the-app)  
- [Evaluation](#evaluation)  
- [Roadmap](#roadmap)  
- [Contributing](#contributing)  
- [License](#license)  
- [Acknowledgements](#acknowledgements)

---

## Overview

This project demonstrates how to build a RAG pipeline tailored for legal text: contracts, court opinions, statutes, regulations, and memos. It focuses on:

- Accurate retrieval of small, relevant snippets from long legal documents.
- Context-aware prompting to reduce hallucinations.
- Citations and provenance so answers can be verified.
- Easy swapping of vector DBs and embedding/LLM providers.

Use cases: legal research assistant, contract question answering, automated summarization, precedent retrieval.

---

## Features

- Document ingestion (PDF, DOCX, TXT).
- Chunking with overlap and metadata (document title, section, page).
- Embeddings generation using pluggable providers.
- Vector index support (Milvus, Pinecone, FAISS, Weaviate, SQLite + HNSW).
- FastAPI-backed QA API + optional Streamlit/Gradio UI.
- Source-aware generation (returns supporting snippets + citations).
- Evaluation harness for retrieval (Recall@K) and generation (ROUGE / BERTScore).

---

## Architecture

1. **Ingest** — parse docs, extract text and metadata.  
2. **Chunk** — split into chunks with overlap and keep mapping to source/page.  
3. **Embed & Index** — create embeddings and store in vector DB.  
4. **Retrieve** — at query time, retrieve top-k chunks.  
5. **Generate** — feed retrieved context + prompt to LLM to produce answer with citations.  
6. **Serve** — FastAPI endpoints for query, ingest and admin tasks.



