# 🏥 MediBot — AI Medical Chatbot

An intelligent, fully offline AI medical chatbot powered by **RAG (Retrieval-Augmented Generation)**, **Llama 3**, and **ChromaDB** — built with Python and Flask. No API keys, no internet required, completely private.

![Python](https://img.shields.io/badge/Python-3.12+-blue?style=flat-square&logo=python)
![Flask](https://img.shields.io/badge/Flask-3.0+-black?style=flat-square&logo=flask)
![LangChain](https://img.shields.io/badge/LangChain-0.2+-green?style=flat-square)
![Ollama](https://img.shields.io/badge/Ollama-Llama3-orange?style=flat-square)
![ChromaDB](https://img.shields.io/badge/ChromaDB-Vector_DB-purple?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-yellow?style=flat-square)

---

## 📌 Project Overview

MediBot is an AI-powered medical assistant that answers health-related questions using Retrieval-Augmented Generation (RAG). It combines a built-in medical knowledge base with the ability to upload and query custom medical PDFs — all processed locally using the Llama 3 language model via Ollama.

Unlike cloud-based medical chatbots, MediBot runs entirely on your machine — your health data never leaves your computer.

---

## 🚀 Features

| Feature | Description |
|---|---|
| 💬 Medical Chat | Ask any health question — symptoms, diseases, medications, treatments |
| 🩺 Symptom Checker | Structured assessment with urgency level, red flags, and recommended action |
| 📄 PDF Upload | Upload medical textbooks, WHO guidelines, CDC documents to expand knowledge |
| 🔗 Source Citation | Every answer shows exactly which document and page it came from |
| 🧠 Chat Memory | Remembers full conversation history for natural multi-turn dialogue |
| 🔒 Medical Filter | Keyword-based intent detection — rejects non-medical questions |
| 🗑️ Knowledge Reset | Clear uploaded PDFs and restore to built-in knowledge only |

---

## 🧠 How RAG Works

```
User Question
      ↓
Convert to vector (HuggingFace Embeddings)
      ↓
ChromaDB similarity search → Top 4 relevant chunks
      ↓
Assemble prompt: System instructions + Context + Chat history + Question
      ↓
Llama 3 (via Ollama) generates answer
      ↓
Return answer + source citations to user
```

---

## 🤖 Tech Stack

| Tool | Role |
|---|---|
| Flask | Web framework — routes, sessions, API endpoints |
| Ollama + Llama 3 | Local LLM — generates medical answers offline |
| LangChain | RAG orchestration — connects LLM, retriever, memory, and prompts |
| ChromaDB | Vector database — stores and searches document embeddings |
| HuggingFace Embeddings | Converts text to vectors (all-MiniLM-L6-v2 model) |
| PyPDF | Extracts text from uploaded PDF documents |
| ConversationBufferMemory | Stores chat history per session for context-aware responses |

---

## 📂 Project Structure

```
medical_chatbot/
│
├── app.py                  # Main Flask application with RAG pipeline
├── requirements.txt        # Python dependencies
├── README.md               # Project documentation
├── SETUP.md                # Detailed setup instructions
│
├── templates/
│   └── index.html          # Chat UI (dark themed)
│
├── uploads/                # Uploaded PDFs stored here (auto-created)
└── chroma_db/              # ChromaDB vector store (auto-created)
```

---

## 🧪 Built-in Medical Knowledge Base

MediBot comes pre-loaded with knowledge on:

- Diabetes (Type 1 & Type 2)
- Hypertension
- Heart Attack (Myocardial Infarction)
- Pneumonia
- Asthma
- Stroke
- COVID-19
- Depression
- Common Medications reference
- Emergency symptom guidelines

> You can expand this by uploading any medical PDF through the sidebar.

---

## ⚙️ Installation & Setup

### Prerequisites

- Python 3.12+
- Ollama installed — download from [https://ollama.ai](https://ollama.ai)

### Step 1 — Pull Llama 3 model

```bash
ollama pull llama3
```

> Note: This downloads ~4.7 GB. Keep Ollama running in the background.
> For faster responses on CPU, use: `ollama pull llama3.2:1b`

### Step 2 — Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/medical-chatbot.git
cd medical-chatbot
```

### Step 3 — Create virtual environment

```bash
python -m venv medibot_env
medibot_env\Scripts\activate   # Windows
source medibot_env/bin/activate # Mac/Linux
```

### Step 4 — Install dependencies

```bash
pip install -r requirements.txt
```

### Step 5 — Run the app

```bash
python app.py
```

### Step 6 — Open in browser

```
http://localhost:5000
```

---

## 💬 How to Use

**Medical Chat Mode**
- Type any health-related question in the chat box
- MediBot retrieves relevant context from the knowledge base
- Answer includes source citations showing which document was used

**Symptom Checker Mode**
- Click "Symptom Checker" in the sidebar
- Describe your symptoms in detail
- Get a structured assessment with urgency level and recommended action

**Upload Medical PDFs**
- Click the upload zone in the sidebar
- Upload any medical PDF (textbooks, guidelines, reports)
- MediBot immediately starts answering from the uploaded document

---

## 🔍 Example Questions

```
"What are the symptoms of diabetes?"
"How is hypertension treated?"
"What medications are used for asthma?"
"I have fever, headache and body aches for 2 days"
"What is the difference between Type 1 and Type 2 diabetes?"
"When should I go to the emergency room?"
```

---

## ⚠️ Disclaimer

MediBot provides **general medical information only**. It does not replace professional medical advice, diagnosis, or treatment. Always consult a qualified healthcare provider for personal medical decisions.

For medical emergencies, call your local emergency services immediately.

---

## 🔑 Key Concepts

**RAG (Retrieval-Augmented Generation)** — Combines document retrieval with LLM generation. Instead of relying only on training data, the model answers based on actual retrieved document content, reducing hallucination and enabling real-time knowledge updates.

**ChromaDB** — A vector database that stores text as mathematical vectors and finds semantically similar content using cosine similarity search.

**Ollama** — A tool that runs large language models locally on your machine without requiring cloud APIs or GPU infrastructure.

---

## 🛠️ Troubleshooting

| Problem | Solution |
|---|---|
| LLM Error in chat | Make sure Ollama is running in background |
| Slow responses | Switch to `llama3.2:1b` for faster CPU inference |
| Embedding model fails | Connect to internet once for first-time download |
| Port 5000 in use | Change to `app.run(port=5001)` in app.py |
| WinError 32 on clear | Use the collection-based clear method (see app.py) |

---

## 📄 License

This project is licensed under the MIT License.

---

## 🙋 Author

**Kavya**
- GitHub: [@YOUR_USERNAME](https://github.com/YOUR_USERNAME)

---

## ⭐ If you found this project useful, please give it a star!
