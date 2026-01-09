# RAG
# LangChain RAG Pipeline (Colab-Friendly)

Simple Retrieval-Augmented Generation (RAG) system using LangChain, FAISS, HuggingFace embeddings, and Qwen LLM. Loads text docs, builds searchable vector DB, retrieves context for queries, generates grounded answers.

[

## 🚀 Quick Start (Google Colab)

1. **Open in Colab** (copy-paste code or use notebook)
2. **Run cells sequentially**:
   ```
   !pip install langchain faiss-cpu sentence-transformers huggingface-hub transformers langchain-community
   ```
3. **Add your `data/About_Ai.txt`** (upload/create via instructions)
4. **Query**: `rag_chain("What is AI?")`

**Expected Output**: Accurate answers from your document only.

## 📋 Features
- Local embeddings (no API keys needed)
- FAISS vector store (fast similarity search)
- Chunking + overlap for context
- Grounded generation (LLM uses retrieved docs only)
- Colab-optimized (pip installs, file handling)

## 🛠️ How It Works
```
Text File → Load → Split Chunks → Embed → FAISS Index
                    ↓
Query → Retrieve Top Chunks → Prompt LLM → Answer
```

**Key Components**:
| Module | Purpose |
|--------|---------|
| `TextLoader` | Read txt files |
| `RecursiveCharacterTextSplitter` | Chunk w/ overlap (300/50) |
| `HuggingFaceEmbeddings` | Semantic vectors ("all-MiniLM-L6-v2") |
| `FAISS` | Vector DB + retriever |
| `HuggingFacePipeline` | Qwen2.5-1.5B LLM (local) |
| `rag_chain()` | Retrieve → Prompt → Generate |

## 📁 File Structure
```
project/
├── data/
│   └── About_Ai.txt     # Your knowledge base
├── rag_pipeline.ipynb   # Main Colab notebook
└── README.md           # This file
```

## 🔧 Customization
- **New Docs**: Add txt to `data/`, rerun loader → FAISS.
- **Embeddings**: Swap `model_name="your-model"`.
- **LLM**: Change `Qwen/Qwen2.5-1.5B-Instruct` or use OpenAI/Groq.
- **Chunk Size**: Adjust `chunk_size=500, chunk_overlap=100`.
- **Persistence**: `db.save_local("faiss_index")`; `FAISS.load_local(...)`.

## 🧒 Kid Explanation
Giant book → sticky notes → magic tags → fast finder → smart robot reads notes → perfect answer!

## 📚 Concepts Learned
- **RAG**: Retrieve docs → Augment LLM prompts (no retraining).
- **Embeddings**: Text → numbers (similarity math).
- **Vector DB**: Fast "find alike" search.
- **Prompt Engineering**: "Use ONLY context" prevents lies.
