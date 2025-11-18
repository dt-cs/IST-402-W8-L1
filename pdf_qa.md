# PDF Q&A RAG Assignment Report

### Group 10 – Deebak, Andreea, Tsehynesh

---

## Overview

This task involved understanding how a **PDF Q&A Retrieval-Augmented Generation (RAG) application** using Streamlit and local models works. The application allows users to upload one or more PDF files, automatically chunk and embed their contents using a MiniLM embedding model, build a FAISS vector store, and answer questions using a local FLAN-T5 model.

The objective was to understand RAG workflows, vector database integration, and how local language models can provide context-based answers.

---

## Code 

The application demonstrates an end-to-end RAG pipeline with the following components:

### 1. Environment Setup

The environment installs necessary Python packages:

- `streamlit` — building the web UI  
- `langchain-community` — embeddings and vector store support  
- `faiss-cpu` — vector similarity search  
- `sentence-transformers` — MiniLM embeddings  
- `transformers` and `accelerate` — local LLM inference  
- `pypdf` — PDF parsing  

The Colab notebook handles process cleanup and ensures the Streamlit app runs on port 8501 with a public URL via Cloudflare Tunnel or NGROK can also be used.

### 2. Model Loading

The application loads two key models:

- **Embeddings:** `sentence-transformers/all-MiniLM-L6-v2` generates vector representations of PDF text chunks.  
- **Local LLM:** `google/flan-t5-base` generates answers using the retrieved context. The model automatically selects GPU if available.

Caching is used for both models to avoid reloading on every interaction.

### 3. Application Execution

The Streamlit UI provides:

- Upload interface for PDF files  
- Buttons to build/rebuild the FAISS index or clear it  
- Question input field  
- Top-k retrieval and answer length sliders  
- Retrieval of relevant chunks and FLAN-T5 answer generation  

| Component | Role | Model / Library |
|----------|------|----------------|
| User Interface | File upload, question input, buttons | Streamlit |
| PDF Parsing | Extracts text from uploaded PDFs | PyPDF |
| Text Chunking | Splits PDFs into smaller chunks | LangChain RecursiveCharacterTextSplitter |
| Embedding | Converts chunks to vector representations | MiniLM (`sentence-transformers`) |
| Vector Store | Stores and retrieves text chunks | FAISS |
| Answer Generation | Generates answer using retrieved chunks | FLAN-T5 (`transformers`) |

---

## Experiment

The application was tested with various PDF documents, including technical papers and user manuals, to evaluate the accuracy and usefulness of the answers provided.

### 1. Example: Single PDF

| Uploaded PDF | Question | Retrieved Chunks | Generated Answer |
|:---|:---|:---|:---|
| ![](INSERT_PDF_IMAGE_URL_HERE) | “What is the main purpose of this document?” | 4 most relevant chunks extracted from PDF | “The document provides an overview of …” |

**Analysis:**  
The system successfully retrieves the most relevant chunks from the PDF and provides coherent answers. Minor errors occur if the answer requires cross-chunk reasoning or very specific details not explicitly present in a single chunk.

---

## Learnings

The PDF Q&A RAG app demonstrates:

- How RAG pipelines can provide context-aware answers using local LLMs.  
- Efficient use of vector databases (FAISS) for fast similarity search.  
- Chunking and embedding strategies significantly affect retrieval quality.  
- Local LLMs like FLAN-T5 can produce coherent answers when sufficient context is retrieved.
- 
The final meeting summarizer app will use a RAG workflow where a custom script scrapes the video transcription from a user-provided URL and stores it as vectors. This vector base will then be used to retrieve relevant meeting-specific information to answer detailed follow-up questions from the user.
Challenges observed:
