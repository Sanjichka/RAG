# RAG
Retrieval Augmented Generation

My goal: Gemini-Powered RAG Pipeline for Technical Documentation
This repository contains a Retrieval-Augmented Generation (RAG) system designed to extract and query information from technical documents. It leverages Google's Gemini 2.5 for high-speed reasoning and Chroma DB for efficient vector storage.

🏗️ Architecture
The system transforms raw .docx documentation into a searchable knowledge base through the following steps:
-> Hierarchical Document Parsing: Uses python-docx to detect document Headings. This ensures text chunks are split logically by topic rather than arbitrary character counts, preserving semantic context.

-> Incremental Indexing: Every text chunk is hashed using SHA-256. The system compares these hashes against the existing database and only adds or updates content that has changed, saving processing time and API costs.

-> Vector Embedding: Converts text into 768-dimensional vectors using the text-embedding-004 model.

-> Retrieval & Grounding: When a query is made, the system retrieves the most relevant document sections and prompts Gemini to answer strictly based on that context to prevent hallucinations.

🛠️ Tech Stack
-> LLM: Gemini 2.5 Flash Lite (optimized for speed and low-latency RAG)
-> Embeddings: Google Text Embedding 004
-> Vector DB: Chroma
-> Orchestration: LangChain
-> Environment: Python / Google Colab

📋 Example Usage
The system is designed to handle complex technical queries. For example, when queried about Google BigQuery, the system retrieves specific architectural details from the indexed healthcare analytics documentation:
-> Query: Which standard SQL is supported in BigQuery?
-> Response: BigQuery supports standard SQL:2011. Sources: ['BigQuery for Large-Scale Healthcare Analytics.docx:3', ...]
