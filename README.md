# 🤖 AI Knowledge Retrieval Assistant

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://python.org)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.30+-red.svg)](https://streamlit.io)
[![Gemini AI](https://img.shields.io/badge/Gemini-AI-orange.svg)](https://ai.google.dev)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

## 🌐 Live Demo

**[Try the App Live →](https://mrrohitjd-gdg-knowledge-agent-day-3streamlit-app-zfrkpp.streamlit.app/)**

---

An intelligent **RAG (Retrieval-Augmented Generation)** powered chatbot built with Google's Gemini AI. Ask questions about GDG events, workshops, and any documents you upload - get accurate, sourced answers!

![AI Knowledge Retrieval Assistant](https://res.cloudinary.com/startup-grind/image/upload/c_fill,dpr_2.0,f_auto,g_center,h_1200,q_100,w_1200/v1/gcs/platform-data-goog/contentbuilder/GDG_Bevy_SocialSharingThumbnail_KFxxrrs.png)

## ✨ Features

- 🔍 **RAG Pipeline** - Retrieves relevant context from your documents before generating answers
- 📚 **Source Attribution** - Every answer cites the exact sources used
- 🚫 **No Hallucinations** - AI only uses information from your knowledge base
- 📄 **Document Upload** - Add `.txt` and `.md` files to expand knowledge
- 🌐 **Web Scraping** - Fetch live data from GDG chapter pages
- 💬 **Chat Interface** - Beautiful, interactive Streamlit UI
- 🔐 **Secure** - API keys stored in environment variables

## 🏗️ Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                    AI Knowledge Retrieval Assistant                       │
├─────────────────────────────────────────────────────────────┤
│                                                              │
│  User Question                                               │
│       │                                                      │
│       ▼                                                      │
│  ┌─────────────┐    ┌──────────────┐    ┌───────────────┐  │
│  │  Embedding  │───▶│ Vector Search│───▶│ Top-K Chunks  │  │
│  │   Model     │    │  (ChromaDB)  │    │  Retrieved    │  │
│  └─────────────┘    └──────────────┘    └───────┬───────┘  │
│                                                  │          │
│                                                  ▼          │
│  ┌─────────────────────────────────────────────────────┐   │
│  │              Gemini AI (gemini-2.5-flash)            │   │
│  │    Context + Question → Sourced Answer               │   │
│  └─────────────────────────────────────────────────────┘   │
│                                                              │
└─────────────────────────────────────────────────────────────┘
```

## 📁 Project Structure

```
gdg-aiml/
├── Day-1/                      # NLP Fundamentals
│   ├── text_cleaner.py         # Text preprocessing utilities
│   ├── semantic_similarity.py  # Embedding-based similarity
│   └── faq_finder.py           # FAQ matching system
│
├── Day-2/                      # Knowledge Base
│   ├── chunking_utility.py     # Smart text chunking
│   ├── knowledge_base.py       # Vector database (ChromaDB)
│   └── gdg_guidelines.txt      # Sample GDG documentation
│
├── Day-3/                      # RAG Agent
│   ├── gemini_wrapper.py       # Gemini AI API wrapper
│   ├── rag_agent.py            # Complete RAG pipeline
│   └── streamlit_app.py        # Web interface
│
├── .env                        # API keys (not in repo)
├── .gitignore                  # Git ignore rules
├── requirements.txt            # Python dependencies
└── README.md                   # This file
```

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/MrRohitJD/GDG-Knowledge-Agent.git
cd GDG-Knowledge-Agent
```

### 2. Create Virtual Environment

```bash
python -m venv venv

# Windows
venv\Scripts\activate

# macOS/Linux
source venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -r requirements.txt
```

### 4. Set Up API Key

Get your free Gemini API key from [Google AI Studio](https://aistudio.google.com/app/apikey)

Create a `.env` file in the project root:

```env
GEMINI_API_KEY=your_api_key_here
```

### 5. Run the Application

```bash
cd Day-3
streamlit run streamlit_app.py
```

Open http://localhost:8501 in your browser 🎉

## 💻 Usage

### Web Interface (Streamlit)

1. The app auto-initializes with GDG Guidelines
2. Ask questions in the chat input
3. Upload additional documents via sidebar
4. Fetch live data from GDG chapter URLs
5. View sources for every answer

### Command Line (RAG Agent)

```bash
cd Day-3
python rag_agent.py
```

### Python API

```python
from rag_agent import RAGAgent
from knowledge_base import KnowledgeBase

# Initialize
kb = KnowledgeBase("my_knowledge_base")
kb.add_document("Your document content here...", metadata={'source': 'doc.txt'})

agent = RAGAgent(
    gemini_api_key="your_key",
    knowledge_base=kb,
    temperature=0.3
)

# Ask questions
result = agent.answer("What is this document about?")
print(result['answer'])
print(result['sources'])
```

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| LLM | Google Gemini 2.5 Flash |
| Embeddings | sentence-transformers (all-MiniLM-L6-v2) |
| Vector DB | ChromaDB |
| Web UI | Streamlit |
| Web Scraping | BeautifulSoup4 |

## 📝 Workshop Curriculum

This project was built during a 3-day GDG AI/ML Workshop:

| Day | Topic | Key Learnings |
|-----|-------|---------------|
| **Day 1** | NLP Fundamentals | Text cleaning, tokenization, embeddings, semantic similarity |
| **Day 2** | Knowledge Base | Document chunking, vector databases, ChromaDB |
| **Day 3** | RAG System | Gemini API, prompt engineering, Streamlit deployment |

## 🔧 Configuration

### Environment Variables

| Variable | Description | Required |
|----------|-------------|----------|
| `GEMINI_API_KEY` | Google Gemini API key | Yes |
| `HF_TOKEN` | Hugging Face token (optional, for faster downloads) | No |

### Model Settings

```python
# In rag_agent.py
temperature = 0.3  # Lower = more factual (recommended for RAG)
top_k = 3          # Number of chunks to retrieve
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [Google Developer Groups (GDG)](https://gdg.community.dev/) for the workshop
- [Google Gemini AI](https://ai.google.dev/) for the powerful LLM
- [Streamlit](https://streamlit.io/) for the amazing UI framework
- [ChromaDB](https://www.trychroma.com/) for the vector database

---

<p align="center">
  Built with ❤️ at GDG AI/ML Workshop
</p>
