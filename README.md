<div align="center">

# 🧠 Personal Productivity Assistant
### AI-Powered Document Intelligence for Personal Knowledge Management

**Query your own documents. Get accurate answers. Cut through information overload.**

Natural language access to your notes, PDFs, and meeting transcripts — powered by Agentic AI and RAG.

![Status](https://img.shields.io/badge/Status-In%20Development-brightgreen)
![Domain](https://img.shields.io/badge/Domain-Personal%20Productivity-blue)
![Approach](https://img.shields.io/badge/Approach-Retrieval--Augmented%20Generation-purple)
![Stack](https://img.shields.io/badge/Stack-Python%20%7C%20Flask%20%7C%20Vector%20DB-orange)
![License](https://img.shields.io/badge/License-MIT-lightgrey)

---

> **"Stop searching. Start asking."**
> Your documents have the answers — the assistant just finds them.

</div>

---

## 🚨 The Problem

Knowledge workers produce and consume enormous volumes of unstructured data every day:

- Meeting transcripts buried in folders
- Notes scattered across apps
- PDFs never read after download
- Decisions forgotten because no one can find the original context

A real-world productivity bottleneck:

- Hours lost every week searching for information that already exists
- Generic AI chatbots fabricate answers when documents aren't in context
- Cloud search tools index text but understand nothing
- Personal data shared with third-party services raises privacy concerns

Traditional search finds **keywords**.
Productivity requires **understanding**.

---

## 💡 What is Personal Productivity Assistant?

A **private, document-grounded AI assistant** that lets you query your own files using plain English.

It answers one question that matters:

> **What does my own knowledge base say about this?**

The system ingests your documents, converts them into semantic vector representations, and retrieves the most relevant context before generating an answer — keeping responses accurate, private, and grounded in your actual data.

---

## 🧭 Design Principles

This system is built on three core assumptions:

1. Accuracy requires **context**, not just a capable model.
2. Private data must stay **private** — not sent to external services unnecessarily.
3. Responses must be **grounded** in your documents, not generated from general knowledge.

Therefore, every answer is tied to a retrievable source. If the document doesn't say it, the assistant won't fabricate it.

---

## 🌍 How Information Overload Happens in Real Life

```
1️⃣  You take notes during a meeting
2️⃣  The transcript gets saved and forgotten
3️⃣  A question comes up two weeks later
4️⃣  You search manually, find nothing useful
5️⃣  You ask a generic chatbot — it guesses
6️⃣  The actual answer was in your notes the whole time
```

The solution isn't a better search bar. It's a system that **reads and understands** your documents.

---

## 🧨 The Hallucination Problem

Generic LLMs have a fundamental flaw for personal knowledge use:

- They answer from training data, not your documents
- They confidently fabricate details when they don't know
- They have no access to private, recent, or domain-specific content

This assistant addresses this by anchoring every response in retrieved document chunks — the model sees your actual content before generating any answer.

---

## 🔍 Supported Document Types

| Document Type | Examples |
|---|---|
| 📝 **Personal Notes** | Daily notes, ideas, to-dos |
| 📄 **PDFs** | Research papers, reports, manuals |
| 🎙️ **Meeting Transcripts** | Team calls, interviews, discussions |
| 📋 **Unstructured Text** | Logs, journals, raw text files |

---

## ⚙️ System Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    DOCUMENT INGESTION LAYER                  │
│        Notes │ PDFs │ Meeting Transcripts │ Text Files       │
└─────────────────────────┬───────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                  PROCESSING & INDEXING LAYER                 │
│                                                             │
│   Step 1: Document Parsing & Text Extraction                │
│   Step 2: Text Chunking (context-preserving segments)       │
│   Step 3: Embedding Generation (vector representations)     │
│   Step 4: Vector Store Indexing                             │
└─────────────────────────┬───────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                    RETRIEVAL LAYER                           │
│      User Query → Query Embedding → Similarity Search       │
│             → Top-K Relevant Chunks Retrieved               │
└─────────────────────────┬───────────────────────────────────┘
                          │
                          ▼
┌─────────────────────────────────────────────────────────────┐
│                   GENERATION LAYER                           │
│     Retrieved Chunks + User Query → LLM → Grounded Answer   │
└─────────────────────────┬───────────────────────────────────┘
                          │
            ┌─────────────┼─────────────┐
            ▼             ▼             ▼
         Answer       Source Refs   Confidence
```

---

## 🌐 Why RAG Over Standard Chatbots?

| | Generic Chatbot | Personal Productivity Assistant |
|---|---|---|
| Data source | Training data | Your documents |
| Hallucination risk | High | Low — answers grounded in source |
| Privacy | Data leaves your system | Operates on local/private data |
| Recency | Capped at training cutoff | Reflects your latest documents |
| Relevance | General knowledge | Domain and context specific |

Retrieval-Augmented Generation bridges the gap between powerful language models and the specific knowledge you actually need.

---

## 🧠 RAG Pipeline

| Step | Module | Purpose |
|------|--------|---------|
| 1 | Document Loader | Parse and extract raw text |
| 2 | Chunker | Split text into meaningful segments |
| 3 | Embedding Model | Convert chunks to vector representations |
| 4 | Vector Store | Index and persist embeddings |
| 5 | Query Engine | Embed query, retrieve top-K chunks |
| 6 | LLM Generation | Generate grounded response with context |
| 7 | Flask API | Serve results to the user |

---

## 📊 Example Interaction

```
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  PERSONAL PRODUCTIVITY ASSISTANT
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
  Query   : "What were the action items from
             the product review last week?"

  Answer  : Based on your meeting transcript,
             the action items were:
             1. Finalize API design by Friday
             2. Schedule user testing session
             3. Update docs for v2 release

  Sources : meeting_march_12.txt
            product_notes.pdf

  Status  : ✅ Grounded — answer sourced from
             your documents
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
```

---

## 🏗️ Technology Stack

| Layer | Technology |
|---|---|
| Backend Framework | Python, Flask |
| LLM | *(e.g., OpenAI GPT / Ollama / Gemini)* |
| Embeddings | *(e.g., sentence-transformers / OpenAI Embeddings)* |
| Vector Database | *(e.g., ChromaDB / FAISS / Pinecone)* |
| Document Parsing | *(e.g., PyMuPDF / pdfplumber)* |
| Deployment | Scalable REST API |

---

## ⚙️ Setup & Installation

### Prerequisites

- Python 3.9+
- pip

### 1. Clone the repository

```bash
git clone https://github.com/ItsRavi-AIML/Personal-Productivity-Assistants.git
cd Personal-Productivity-Assistants
```

### 2. Create a virtual environment

```bash
python -m venv venv
source venv/bin/activate        # Windows: venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure environment variables

```bash
cp .env.example .env
# Add your API keys and config
```

### 5. Ingest your documents

```bash
python ingest.py --input your_documents/
```

### 6. Run the server

```bash
python app.py
```

API available at `http://localhost:5000`

---

## 📡 API Endpoints

### `POST /query`

Ask a natural language question against your document knowledge base.

**Request:**
```json
{
  "question": "What were the key decisions from last week's meeting?"
}
```

**Response:**
```json
{
  "answer": "Based on your documents, the key decisions were...",
  "sources": ["meeting_transcript.txt", "notes_march.pdf"]
}
```

### `POST /ingest`

Upload a new document to the knowledge base.

**Response:**
```json
{
  "status": "success",
  "chunks_indexed": 38
}
```

---

## 📏 Evaluation Strategy

System performance measured using:

- Answer relevance to query intent
- Groundedness — answers traceable to source documents
- Retrieval precision across document types
- Hallucination rate on out-of-context queries
- Response latency under load

Goal: maximum accuracy on personal document queries with near-zero fabricated content.

---

## ⚠️ Current Limitations

- Accuracy depends on quality and completeness of ingested documents
- Very large documents require chunking strategy tuning
- Cross-document reasoning is limited to retrieved chunks
- Real-time document sync not yet supported

---

## 📈 Expected Impact

- 🔍 Instant answers from your own knowledge base
- 🧠 No more manual searching through old files
- 🔒 Private-by-design — your data stays yours
- 📄 Source-cited responses — no blind trust required
- ⚡ Scalable to large personal document libraries

---

## 🔭 Future Scope

- [ ] Web UI for document upload and chat interface
- [ ] Real-time document sync from cloud storage
- [ ] Multi-modal support (audio, images)
- [ ] Streaming responses
- [ ] Docker containerization
- [ ] User authentication and isolated knowledge bases

---

## 👥 Team

| Name |
|---|
| Maddi Balaji |
| N Lirish Teja |
| Guvvadi Ganesh |
| N Raja Ravi Varma |

---

## 🏆 What We Are Working Towards

Information overload is not a search problem — it's an understanding problem. Existing tools index your files. They don't read them, reason about them, or connect ideas across them.

We are working towards a system where **no important insight stays buried** simply because it was in a file nobody thought to open again.

This Personal Productivity Assistant treats knowledge retrieval as an **AI reasoning problem**, not a keyword matching problem — and delivers answers grounded in what you actually wrote, not what a model thinks you might have meant.

---

<div align="center">

**Personal Productivity Assistant — Your documents have the answers. We just help you find them.**

</div>
