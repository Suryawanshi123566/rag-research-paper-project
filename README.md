# 📄 RAG-Based Research Paper Analysis

> A Retrieval-Augmented Generation (RAG) system for intelligent question-answering over research papers using Google Gemini and LangChain.

---

## 🧠 About The Project

This project implements a **RAG (Retrieval-Augmented Generation)** pipeline that allows users to upload any research paper (PDF) and ask natural language questions about it. The system retrieves the most relevant sections from the document and uses **Google Gemini 2.5 Flash** to generate accurate, context-aware answers.

The notebook was tested on a research paper focused on **sarcasm-aware sentiment analysis for Hindi–Marathi social media text using Indic-specific transformer models**.

---

## ✨ Features

- 📥 Upload any research paper in PDF format
- 🔍 Intelligent document chunking and semantic search
- 🧩 Vector-based retrieval using **ChromaDB**
- 🤖 Answer generation powered by **Gemini 2.5 Flash**
- 🌐 Embeddings via `gemini-embedding-001`
- ⚡ Runs on Google Colab with GPU acceleration (T4)

---

## 🏗️ System Architecture

```
PDF Document
     │
     ▼
PyPDFLoader  ──►  RecursiveCharacterTextSplitter  ──►  Text Chunks
                                                              │
                                                             ▼
                                              GoogleGenerativeAIEmbeddings
                                                              │
                                                             ▼
                                                      ChromaDB VectorStore
                                                              │
                    User Query ──────────────────►  Retriever (Top-k=3)
                                                              │
                                                             ▼
                                               ChatGoogleGenerativeAI (Gemini 2.5 Flash)
                                                              │
                                                             ▼
                                                      Final Answer
```

---

## 🛠️ Tech Stack

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Google Gemini 2.5 Flash | Answer generation (LLM) |
| `gemini-embedding-001` | Semantic embeddings |
| LangChain | RAG pipeline orchestration |
| ChromaDB | Vector store for document retrieval |
| PyPDF / pypdf | PDF loading and parsing |
| Sentence Transformers | Embedding support |
| Google Colab | Runtime environment (GPU: T4) |

---

## 📁 Project Structure

```
rag-research-paper-project/
│
├── Reserch_paper_rag_project.ipynb   # Main Jupyter Notebook with full RAG pipeline
├── requirements.txt                   # Python dependencies
└── README.md                          # Project documentation
```

---

## 🚀 Getting Started

### Prerequisites

- A [Google Colab](https://colab.research.google.com/) account
- A **Google Gemini API Key** → Get it at [Google AI Studio](https://aistudio.google.com/app/apikey)

### Setup & Run

1. **Clone this repository**
   ```bash
   git clone https://github.com/your-username/rag-research-paper-project.git
   ```

2. **Open the notebook in Google Colab**
   - Go to [colab.research.google.com](https://colab.research.google.com/)
   - Upload `Reserch_paper_rag_project.ipynb`

3. **Install dependencies** *(first cell in notebook)*
   ```bash
   pip install -q -U google-generativeai langchain-google-genai langchain chromadb pypdf sentence-transformers
   ```

4. **Add your Gemini API Key**
   - In the notebook, replace `"GEMINI API KEY"` with your actual key:
   ```python
   API_KEY = "your-actual-gemini-api-key-here"
   ```

5. **Upload your research paper**
   - Run the file upload cell and select your PDF

6. **Run all cells** and ask questions about your paper!

---

## 💡 Example Output

**Question asked:**
```
What is the main objective of this research?
```

**Generated Answer:**
```
The main objective of this research is to bridge the research gap in exploring 
sarcasm-aware sentiment analysis for Hindi–Marathi social media text using 
Indic-specific transformer models. It aims to achieve this by evaluating a 
unified transformer-based approach that focuses on contextual understanding, 
multilingual representation, and balanced class detection.
```

---

## 📦 Requirements

```
numpy
pandas
scikit-learn
transformers
torch
langchain
sentence-transformers
faiss-cpu
google-generativeai
langchain-google-genai
chromadb
pypdf
```

Install all at once:
```bash
pip install -r requirements.txt
```

---

## ⚠️ Notes

- This notebook is designed to run on **Google Colab** (uses `google.colab.files` for upload).
- GPU runtime (T4) is recommended for faster embedding generation.
- Ensure your Gemini API key has access to `gemini-2.5-flash` and `gemini-embedding-001`.

---

## 👩‍💻 Author

**Sakshi Surywanshi**  
M.Tech Student – AI / Data Science

---

## 📃 License

This project is open-source and available under the [MIT License](LICENSE).
