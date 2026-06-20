# RAG From Scratch 🧠

A locally running Retrieval-Augmented Generation (RAG) application built from scratch — no LangChain, no magic, just pure Python.

---

## 📌 Project Goal

Understand and implement RAG internals step by step:
1. Extract text from a PDF
2. Chunk it manually
3. Convert chunks to vectors (embeddings)
4. Search using cosine similarity
5. Send relevant chunks to an LLM
6. Get a grounded answer

---

## 🖥️ System Requirements

| Tool | Version | Purpose |
|------|---------|---------|
| Python | 3.10+ | Runtime |
| VS Code | Latest | IDE |
| Ollama | Latest | Local LLM server |

---

## 🤖 Ollama Models

| Model | Command | Purpose |
|-------|---------|---------|
| Gemma 3 | `ollama pull gemma3` | LLM for answering questions |
| nomic-embed-text | `ollama pull nomic-embed-text` | Converting text to vectors (embeddings) |

---

## 📦 Python Packages

| Package | Purpose |
|---------|---------|
| `pymupdf` | Extract text from PDF files |
| `ollama` | Python client to talk to local Ollama server |

### Install
```bash
pip install pymupdf ollama
```

---

## 🗂️ Project Structure

```
rag-from-scratch/
├── venv/               # Virtual environment (do not commit)
├── README.md           # This file
└── (more files coming as we build)
```

---

## ⚙️ Setup Steps

### 1. Clone / create project folder
```bash
mkdir rag-from-scratch
cd rag-from-scratch
```

### 2. Create and activate virtual environment
```bash
python -m venv venv

# Windows
venv\Scripts\activate

# Mac/Linux
source venv/bin/activate
```

### 3. Install dependencies
```bash
pip install pymupdf ollama
```

### 4. Verify Ollama is running
```bash
ollama list
curl http://localhost:11434/api/tags
```

---

## 🧠 Concepts Covered So Far

- **Virtual Environment** — isolated Python environment per project (like `node_modules` in Node.js)
- **Embeddings** — converting text into vectors (lists of floats) so we can measure similarity
- **Cosine Similarity** — measuring how close two vectors are in meaning
- **RAG Pipeline** — Indexing → Retrieval → Generation

---

## 🚧 Progress

- [x] Step 1 — Verify setup (Python, Ollama, VS Code)
- [x] Step 2 — Project folder + virtual environment + packages installed
- [x] Step 3 — Extract text from PDF (PyMuPDF / fitz)
- [x] Step 4 — Minimal whitespace cleaning + manual chunking (chunk_size=500, overlap=100)
- [x] Step 5 — Generate embeddings using nomic-embed-text (768 dimensions)
- [x] Step 6 — Build vector store (simple Python list of {text, embedding})
- [x] Step 7 — Cosine similarity search (manual implementation, no libraries)
- [x] Step 8 — Generate grounded answers using Gemma 3 via Ollama

✅ **First working end-to-end RAG pipeline complete!**

---

## 📝 Notes

- Ollama runs locally at `http://localhost:11434`
- No API keys needed — everything runs on your machine
- Claims/sensitive data never leaves your machine
- LangChain is intentionally avoided — we build everything from scratch to understand internals
- No vector DB (ChromaDB/Pinecone) needed at this scale — a Python list works fine for small datasets
- Model used for generation: `gemma3` (pulled via `ollama pull gemma3`)
- If `gemma3` isn't found, pull a tagged version e.g. `ollama pull gemma3:4b` and update model name in code

---

## 🔮 What's Next (Future Improvements)

- [ ] Persist vector store to disk (currently lost on notebook restart)
- [ ] Try ChromaDB for comparison once internals are understood
- [ ] Improve chunking (sentence-aware / paragraph-aware instead of fixed character size)
- [ ] Add source citation (which page/chunk the answer came from)
- [ ] Try with a multi-page real-world PDF (insurance EOB, policy doc)
- [ ] Build simple Streamlit UI on top of this pipeline
- [ ] Eventually migrate to LangGraph for claims adjudication POC
