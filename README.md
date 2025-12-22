# 🌟  LocalDocsAI assistant

**A private, local AI assistant for your documents—without sending data to the cloud**

<a href="https://github.com/mscbuild"><img src="https://img.shields.io/badge/AI-Code%20Assist-EB9FDA"></a>
![](https://komarev.com/ghpvc/?username=mscbuild) 
 ![](https://img.shields.io/github/license/mscbuild/local-docs-ai-agent) 
 ![](https://img.shields.io/badge/PRs-Welcome-green)
 ![](https://img.shields.io/github/languages/code-size/mscbuild/local-docs-ai-agent)
![](https://img.shields.io/badge/code%20style-python-green)
![](https://img.shields.io/github/stars/mscbuild)
![](https://img.shields.io/badge/Topic-Github-lighred)
![](https://img.shields.io/website?url=https%3A%2F%2Fgithub.com%2Fmscbuild)

<img width="1200" height="494" alt="ai agent" src="https://github.com/user-attachments/assets/36affcb3-175a-4f1e-b98d-a5533181ed08" />


# 💡 The gist of the idea

Users upload their PDF, DOCX, TXT, or notes (e.g., from Obsidian, Notion, or personal files) and receive a local AI assistant that:

- Answers questions about document content.
- Finds citations, summarizes sections, and compares files.
- Works completely offline on their computer (Mac, Windows, or Linux).
- No data is transmitted online—maximum privacy.

 # ✨ Opportunities

 - 📄 Document upload: **PDF, TXT, Markdown**
- 💬 AI-powered chat based on your documents (RAG)
- 🕵️‍♂️ Complete privacy – everything runs on your computer
- 🧠 Uses local LLM via **Ollama** (phi3, Mistral, Llama 3, etc.)
- 📜 Chat history is saved
- 🌐 Simple web interface (or desktop app)
  
  # 🔧 Technologies

- **Language:** Python (base) + Electron or Tauri (for GUI)
- **LLM:** Ollama (phi3, Mistral, Llama 3)
- **Embeddings + RAG:** ChromaDB or FAISS
- **Frontend:** React + Vite (if using Tauri) or pure HTML/CSS for simplicity
- **Documents:** PyPDF2, built-in parsers

  # 🔧 Requirements
  
- [Ollama](https://ollama.com/) (install and run)
- Python 3.9+
- pip
  

  # 💰 Monetization

- **Free version (open-source):**
- Supports basic formats (TXT, PDF)
- Works with small files
- CLI interface

  **Paid "Pro" version (SaaS or desktop license)**

- Support for DOCX, PPTX, Excel, and Notion exports
- Improved UI with chat history and tags
- Syncing across devices (optional, with encryption)
- Priority support and updates
- Selling through **Gumroad** or your own website (~$15–$29/time or $5/month)

  **Additionally:**
  
- GitHub Sponsors to support development
- Partnerships with privacy software vendors (Proton, Tuta, etc.)

  # 🎯 Target audience

- Lawyers, doctors, and researchers who work with confidential documents.
- Product managers and analysts who analyze internal reports.
- Regular users who are tired of ChatGPT "remembering" their data.

  # 🌍 Why is this relevant?

- Growing interest in **local LLMs** (Ollama, LM Studio, Jan.ai).
- Privacy concerns when using ChatGPT.
- Many want an AI assistant but don't want to be **dependent on the cloud.**

  # 🗺️ 1. Project Architecture (LocalDocs AI)

 ~~~bash
 ┌───────────────────────────────────────────────────────┐
│                  LocalDocs AI (Desktop App)           │
└───────────────────────────────────────────────────────┘
                              │
          ┌───────────────────┼───────────────────┐
          │                   │                   │
┌─────────▼─────┐   ┌─────────▼─────┐   ┌─────────▼─────┐
│   Frontend    │   │   Backend     │   │   AI Engine   │
│  (Tauri/React)│   │ (FastAPI/Flask)│  │ (Ollama/Llama.cpp)│
└───────────────┘   └───────┬───────┘   └───────▲───────┘
                            │                   │
                    ┌───────▼───────┐   ┌───────┴───────┐
                    │  Document     │   │  Vector       │
                    │  Storage      │   │  Database     │
                    │  (./docs/)    │   │  (ChromaDB)   │
                    └───────────────┘   └───────────────┘
 ~~~
  
  **🔁 Data flow:**

- The user adds a PDF → saves it to ./docs/.
- The system **parses** the text and breaks it into chunks.
- The chunks are **embedded** and saved in **ChromaDB.**
- When asked:
→ the query is embedded → relevant chunks are searched →
→ a prompt is generated → sent to the local LLM →
→ a response is returned

# 📁 Project structure
~~~bash
LocalDocs AI
│
├── core/
│   ├── document_loader.py   ← support PDF, TXT, MD
│   ├── rag_engine.py        ← RAG + chat history
│   └── chat_history.py      ← history management
│
├── api/
│   └── main.py              ← FastAPI server
│
├── static/                  ← simple HTML interface
│   └── index.html
│
├── docs/                    ← user files
└── chroma_db/               ← vector database
~~~


**Install:**

~~~bash
pip install -r requirements.txt
~~~

**And make sure Ollama is running and the model is loaded:**

~~~bash
ollama pull phi3  # mistral, llama3
~~~

# ▶️ How to launch an MVP

- Create a docs/ folder and place any PDF there (name it sample.pdf).
- Launch Ollama: ollama serve (it usually starts automatically).
- Run:

~~~bash
python main.py add docs/sample.pdf
python main.py ask "What is this document about?"
~~~

# Installation

~~~bash
git clone https://github.com/mscbuild/local-docs-ai-agent.git
cd local-docs-ai-agent
pip install -r requirements.txt
~~~

# Launching the web version

~~~bash
cd api
uvicorn main:app --reload --port 8000
~~~

**Open in your browser: http://localhost:8000**

**Usage**

- Upload a PDF/TXT/MD file
- Ask questions: "What is this document about?", "Find the contract date," etc.
- Get answers from AI trained on your data

# 🔒 Privacy

- All documents are stored locally `(./docs/)`
- The vector database is on your disk `(./chroma_db/)`
- Requests to LLM are processed through Ollama on your machine
- **Not a single byte is lost to the internet**

# 🤝 Support the project

This project is open source. If you find it useful:

- ⭐ Star it on GitHub
- 💬 Report bugs in Issues
- 💰 Support the developer through GitHub Sponsors (coming soon)

# 📜 License

License – free to use for personal and commercial purposes.

# 🕵️ Build AI Agents, Visually

<li>⭐ Quick Start <a href="https://flowiseai.com">Build AI Agents, Visually</a>"</li>
