# RAG_custom_semantic_chunking
Retrieval-Augmented Generation (RAG) with Custom Semantic Chunking

This notebook implements a robust RAG pipeline using a document-heavy scientific report. The system includes:
Advanced PDF parsing and cleaning
Semantic and Custom semantic anchor-based chunking strategy
Embedding and indexing using ChromaDB
Retrieval with OpenAI GPT-4 for grounded Q&A

## 📚 Chunking Strategy Descriptions

### 🧱 Sequential + Buffer Chunking
This strategy breaks the document into chunks by moving linearly through the text, combining each sentence with a fixed number of neighboring sentences (the buffer) on either side. It preserves local coherence and is simple to implement, making it effective when important context is typically found nearby. However, it may miss deeper semantic relationships between sentences that aren't adjacent, especially in documents with dispersed or cross-referenced content.

### 🧠 Anchor-Based Semantic Chunking
In this approach, selected anchor sentences serve as the center of each chunk. For each anchor, the system computes semantic similarity with all surrounding sentence groups (pre-computed via the buffer logic) and gathers the most relevant ones, regardless of their original order in the document. This allows the chunk to contain high-context, meaningfully related content even from non-contiguous sections. It results in richer and more focused retrieval, particularly useful in complex documents with interrelated topics.
