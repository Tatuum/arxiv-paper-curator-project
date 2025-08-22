# The Mother of AI Project
## Phase 1 RAG Systems: arXiv Paper Curator

<div align="center">
  <h3>A Learner-Focused Journey into Production RAG Systems</h3>
  <p>Learn to build modern AI systems from the ground up through hands-on implementation</p>
  <p>Master the most in-demand AI engineering skills: <strong>RAG (Retrieval-Augmented Generation)</strong></p>
</div>

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.12+-blue.svg" alt="Python Version">
  <img src="https://img.shields.io/badge/FastAPI-0.115+-green.svg" alt="FastAPI">
  <img src="https://img.shields.io/badge/OpenSearch-2.19-orange.svg" alt="OpenSearch">
  <img src="https://img.shields.io/badge/Docker-Compose-blue.svg" alt="Docker">
  <img src="https://img.shields.io/badge/Status-Week%203%20Keyword%20Search-brightgreen.svg" alt="Status">
</p>

</br>

<p align="center">
  <a href="#-about-this-course">
    <img src="static/mother_of_ai_project_rag_architecture.gif" alt="RAG Architecture" width="700">
  </a>
</p>

## 📖 About This Course

This is a **learner-focused project** where you'll build a complete research assistant system that automatically fetches academic papers, understands their content, and answers your research questions using advanced RAG techniques.

**The arXiv Paper Curator** will teach you to build a **production-grade RAG system using industry best practices**. Unlike tutorials that jump straight to vector search, we follow the **professional path**: master keyword search foundations first, then enhance with vectors for hybrid retrieval.

> **🎯 The Professional Difference:** We build RAG systems the way successful companies do - solid search foundations enhanced with AI, not AI-first approaches that ignore search fundamentals.

By the end of this course, you'll have your own AI research assistant and the deep technical skills to build production RAG systems for any domain.

---

## 🚀 Quick Start

### **📋 Prerequisites**
- **Docker Desktop** (with Docker Compose)  
- **Python 3.12+**
- **UV Package Manager** ([Install Guide](https://docs.astral.sh/uv/getting-started/installation/))
- **8GB+ RAM** and **20GB+ free disk space**

### **⚡ Get Started**

```bash
# 1. Clone and setup
git clone <repository-url>
cd arxiv-paper-curator

# 2. Configure environment (IMPORTANT!)
cp .env.example .env
# The .env file contains all necessary configuration for OpenSearch, 
# arXiv API, and service connections. Defaults work out of the box.

# 3. Install dependencies
uv sync

# 4. Start all services
docker compose up --build -d

# 5. Verify everything works
curl http://localhost:8000/health
```

### **📚 Weekly Learning Path**

| Week | Topic | Blog Post | Code Release |
|------|-------|-----------|--------------|
| **Week 0** | The Mother of AI project - 6 phases | [The Mother of AI project](https://jamwithai.substack.com/p/the-mother-of-ai-project) | - |
| **Week 1** | Infrastructure Foundation | [The Infrastructure That Powers RAG Systems](https://jamwithai.substack.com/p/the-infrastructure-that-powers-rag) | [week1.0](https://github.com/jamwithai/arxiv-paper-curator/releases/tag/week1.0) |
| **Week 2** | Data Ingestion Pipeline | [Building Data Ingestion Pipelines for RAG](https://jamwithai.substack.com/p/bringing-your-rag-system-to-life) | [week2.0](https://github.com/jamwithai/arxiv-paper-curator/releases/tag/week2.0) |
| **Week 3** | OpenSearch ingestion & BM25 retrieval | [The Search Foundation Every RAG System Needs](https://jamwithai.substack.com/p/the-search-foundation-every-rag-system) | [week3.0](https://github.com/jamwithai/arxiv-paper-curator/releases/tag/week3.0)  |
| **Week 4** | Chunking & Hybrid Retrieval | _Coming Soon_ | _Coming Soon_ |
| **Week 5** | Full RAG Pipeline | _Coming Soon_ | _Coming Soon_ |
| **Week 6** | Setting up evals | _Coming Soon_ | _Coming Soon_ |

**📥 Clone a specific week's release:**
```bash
# Clone a specific week's code
git clone --branch <WEEK_TAG> https://github.com/jamwithai/arxiv-paper-curator
cd arxiv-paper-curator
uv sync
docker compose down -v
docker compose up --build -d

# Replace <WEEK_TAG> with: week1.0, week2.0, etc.
```

### **📊 Access Your Services**

| Service | URL | Purpose |
|---------|-----|---------|
| **API Documentation** | http://localhost:8000/docs | Interactive API testing |
| **Airflow Dashboard** | http://localhost:8080 | Workflow management |
| **OpenSearch Dashboards** | http://localhost:5601 | Hybrid search engine UI |

#### **NOTE**: Check airflow/simple_auth_manager_passwords.json.generated for Airflow username and password
---

## 📚 Week 1: Infrastructure Foundation ✅

**Start here!** Master the infrastructure that powers modern RAG systems.

### **🎯 Learning Objectives**
- Complete infrastructure setup with Docker Compose
- FastAPI development with automatic documentation and health checks
- PostgreSQL database configuration and management
- OpenSearch hybrid search engine setup
- Ollama local LLM service configuration
- Service orchestration and health monitoring
- Professional development environment with code quality tools

### **🏗️ Architecture Overview**

<p align="center">
  <img src="static/week1_infra_setup.png" alt="Week 1 Infrastructure Setup" width="800">
</p>

**Infrastructure Components:**
- **FastAPI**: REST endpoints with async support (Port 8000)  
- **PostgreSQL 16**: Paper metadata storage (Port 5432)
- **OpenSearch 2.19**: Search engine with dashboards (Ports 9200, 5601)
- **Apache Airflow 3.0**: Workflow orchestration (Port 8080)
- **Ollama**: Local LLM server (Port 11434)

### **📓 Setup Guide**

```bash
# Launch the Week 1 notebook
uv run jupyter notebook notebooks/week1/week1_setup.ipynb
```

### **✅ Success Criteria**
Complete when you can:
- [ ] Start all services with `docker compose up -d`
- [ ] Access API docs at http://localhost:8000/docs  
- [ ] Login to Airflow at http://localhost:8080
- [ ] Browse OpenSearch at http://localhost:5601
- [ ] All tests pass: `uv run pytest`

### **📖 Deep Dive**
**Blog Post:** [The Infrastructure That Powers RAG Systems](https://jamwithai.substack.com/p/the-infrastructure-that-powers-rag) - Detailed walkthrough and production insights

---

## 📚 Week 2: Data Ingestion Pipeline ✅

**Building on Week 1 infrastructure:** Learn to fetch, process, and store academic papers automatically.

### **🎯 Learning Objectives**
- arXiv API integration with rate limiting and retry logic
- Scientific PDF parsing using Docling
- Automated data ingestion pipelines with Apache Airflow
- Metadata extraction and storage workflows
- Complete paper processing from API to database

### **🏗️ Architecture Overview**

<p align="center">
  <img src="static/week2_data_ingestion_flow.png" alt="Week 2 Data Ingestion Architecture" width="800">
</p>

**Data Pipeline Components:**
- **MetadataFetcher**: 🎯 Main orchestrator coordinating the entire pipeline
- **ArxivClient**: Rate-limited paper fetching with retry logic
- **PDFParserService**: Docling-powered scientific document processing  
- **Airflow DAGs**: Automated daily paper ingestion workflows
- **PostgreSQL Storage**: Structured paper metadata and content

### **📓 Implementation Guide**

```bash
# Launch the Week 2 notebook  
uv run jupyter notebook notebooks/week2/week2_arxiv_integration.ipynb
```

### **💻 Code Examples**

**arXiv API Integration:**
```python
# Example: Fetch papers with rate limiting
from src.services.arxiv.factory import make_arxiv_client

async def fetch_recent_papers():
    client = make_arxiv_client()
    papers = await client.search_papers(
        query="cat:cs.AI",
        max_results=10,
        from_date="20240801",
        to_date="20240807"
    )
    return papers
```

**PDF Processing Pipeline:**
```python
# Example: Parse PDF with Docling
from src.services.pdf_parser.factory import make_pdf_parser_service

async def process_paper_pdf(pdf_url: str):
    parser = make_pdf_parser_service()
    parsed_content = await parser.parse_pdf_from_url(pdf_url)
    return parsed_content  # Structured content with text, tables, figures
```

**Complete Ingestion Workflow:**
```python
# Example: Full paper ingestion pipeline
from src.services.metadata_fetcher import make_metadata_fetcher

async def ingest_papers():
    fetcher = make_metadata_fetcher()
    results = await fetcher.fetch_and_store_papers(
        query="cat:cs.AI",
        max_results=5,
        from_date="20240807"
    )
    return results  # Papers stored in database with full content
```

### **✅ Success Criteria**
Complete when you can:
- [ ] Fetch papers from arXiv API: Test in Week 2 notebook
- [ ] Parse PDF content with Docling: View extracted structured content
- [ ] Run Airflow DAG: `arxiv_paper_ingestion` executes successfully
- [ ] Verify database storage: Papers appear in PostgreSQL with full content
- [ ] API endpoints work: `/papers` returns stored papers with metadata

### **📖 Deep Dive**
**Blog Post:** [Building Data Ingestion Pipelines for RAG](https://jamwithai.substack.com/p/bringing-your-rag-system-to-life) - arXiv API integration and PDF processing

---

## 📚 Week 3: Keyword Search First - The Critical Foundation ⚡

> **🚨 The 90% Problem:** Most RAG systems jump straight to vector search and miss the foundation that powers the best retrieval systems. We're doing it right!

**Building on Weeks 1-2 foundation:** Implement the keyword search foundation that professional RAG systems rely on.

### **🎯 Why Keyword Search First?**

**The Reality Check:** Vector search alone is not enough. The most effective RAG systems use **hybrid retrieval** - combining keyword search (BM25) with vector search. Here's why we start with keywords:

1. **🔍 Exact Match Power:** Keywords excel at finding specific terms, technical jargon, and precise phrases
2. **📊 Interpretable Results:** You can understand exactly why a document was retrieved  
3. **⚡ Speed & Efficiency:** BM25 is computationally fast and doesn't require expensive embedding models
4. **🎯 Domain Knowledge:** Technical papers often require exact terminology matches that vector search might miss
5. **📈 Production Reality:** Companies like Elasticsearch, Algolia, and enterprise search all use keyword search as their foundation

### **🏗️ Week 3 Architecture Overview**

<p align="center">
  <img src="static/week3_opensearch_flow.png" alt="Week 3 OpenSearch Flow Architecture" width="800">
  <br>
  <em>Complete Week 3 architecture showing the OpenSearch integration flow</em>
</p>

**Search Infrastructure:** Master full-text search with OpenSearch before adding vector complexity.

#### **🎯 Learning Objectives**
- **Foundation First:** Why keyword search is essential for RAG systems
- **OpenSearch Mastery:** Index management, mappings, and search optimization
- **BM25 Algorithm:** Understanding the math behind effective keyword search
- **Query DSL:** Building complex search queries with filters and boosting
- **Search Analytics:** Measuring search relevance and performance
- **Production Patterns:** How real companies structure their search systems

#### **Key Components**
- `src/services/opensearch/`: Professional search service implementation
- `src/routers/search.py`: Search API endpoints with BM25 scoring
- `notebooks/week3/`: Complete OpenSearch integration guide  
- **Search Quality Metrics:** Precision, recall, and relevance scoring

#### **💡 The Pedagogical Approach**
```
Week 3: Master keyword search (BM25) ← YOU ARE HERE
Week 4: Add intelligent chunking strategies  
Week 5: Introduce vector embeddings for hybrid retrieval
Week 6: Optimize the complete hybrid system
```

**This progression mirrors how successful companies build search systems - solid foundation first, then enhance with advanced techniques.**

### **📓 Week 3 Implementation Guide**

```bash
# Launch the Week 3 notebook
uv run jupyter notebook notebooks/week3/week3_opensearch.ipynb
```

### **💻 Code Examples**

**BM25 Search Implementation:**
```python
# Example: Search papers with BM25 scoring
from src.services.opensearch.factory import make_opensearch_client

async def search_papers():
    client = make_opensearch_client()
    results = await client.search_papers(
        query="transformer attention mechanism",
        max_results=10,
        categories=["cs.AI", "cs.LG"]
    )
    return results  # Papers ranked by BM25 relevance
```

**Search API Usage:**
```python
# Example: Use the search endpoint
import httpx

async def query_papers():
    async with httpx.AsyncClient() as client:
        response = await client.post("http://localhost:8000/api/v1/search", json={
            "query": "neural networks optimization",
            "max_results": 5,
            "latest_papers": True
        })
        return response.json()
```

### **✅ Success Criteria**
Complete when you can:
- [ ] Index papers in OpenSearch: Papers searchable via OpenSearch Dashboards
- [ ] Search via API: `/search` endpoint returns relevant papers with BM25 scoring
- [ ] Filter by categories: Search within specific arXiv categories (cs.AI, cs.LG, etc.)
- [ ] Sort by relevance or date: Toggle between BM25 scoring and latest papers
- [ ] View search analytics: Understanding why papers matched your query

### **Future Weeks Overview** (Weeks 4-6)
- **Week 4:** Chunking strategies and hybrid retrieval (combining keyword + vector search)
- **Week 5:** Full RAG pipeline with LLM integration and prompt optimization
- **Week 6:** Observability with Langfuse and evaluation systems

---

## ⚙️ Configuration Management

### **Environment Configuration**

The project uses a **unified `.env` file** with nested configuration structure to manage settings across all services.

#### **Configuration Structure**
```bash
# Application Settings
DEBUG=true
ENVIRONMENT=development

# arXiv API (Week 2)
ARXIV__MAX_RESULTS=15
ARXIV__SEARCH_CATEGORY=cs.AI
ARXIV__RATE_LIMIT_DELAY=3.0

# PDF Parser (Week 2)  
PDF_PARSER__MAX_PAGES=30
PDF_PARSER__DO_OCR=false

# OpenSearch (Week 3)
OPENSEARCH__HOST=http://opensearch:9200
OPENSEARCH__INDEX_NAME=arxiv-papers

# Services
OLLAMA_HOST=http://ollama:11434
OLLAMA_MODEL=llama3.2:1b
```

#### **Key Configuration Variables**

| Variable | Default | Description |
|----------|---------|-------------|
| `DEBUG` | `true` | Debug mode for development |
| `ARXIV__MAX_RESULTS` | `15` | Papers to fetch per API call |
| `ARXIV__SEARCH_CATEGORY` | `cs.AI` | arXiv category to search |
| `PDF_PARSER__MAX_PAGES` | `30` | Max pages to process per PDF |
| `OPENSEARCH__INDEX_NAME` | `arxiv-papers` | OpenSearch index name |
| `OPENSEARCH__HOST` | `http://opensearch:9200` | OpenSearch cluster endpoint |
| `OLLAMA_MODEL` | `llama3.2:1b` | Local LLM model |

#### **Service-Aware Configuration**

The configuration system automatically detects the service context:
- **API Service**: Uses `localhost` for database and service connections
- **Airflow Service**: Uses Docker container hostnames (`postgres`, `opensearch`)

```python
# Configuration is automatically loaded based on context
from src.config import get_settings

settings = get_settings()  # Auto-detects API vs Airflow
print(f"ArXiv max results: {settings.arxiv.max_results}")
```

---

## 🔧 Reference & Development Guide

### **🛠️ Technology Stack**

| Service | Purpose | Status |
|---------|---------|--------|
| **FastAPI** | REST API with automatic docs | ✅ Ready |
| **PostgreSQL 16** | Paper metadata and content storage | ✅ Ready |
| **OpenSearch 2.19** | Hybrid search engine | ✅ Ready |
| **Apache Airflow 3.0** | Workflow automation | ✅ Ready |
| **Ollama** | Local LLM serving | ✅ Ready |

**Development Tools:** UV, Ruff, MyPy, Pytest, Docker Compose

### **🏗️ Project Structure**

```
arxiv-paper-curator/
├── src/                                    # Main application code
│   ├── main.py                             # FastAPI application
│   ├── routers/                            # API endpoints
│   │   ├── ping.py                         # Health check endpoints
│   │   ├── papers.py                       # Paper retrieval endpoints
│   │   └── search.py                       # 🆕 NEW: BM25 search endpoints
│   ├── models/                             # Database models (SQLAlchemy)
│   ├── repositories/                       # Data access layer
│   ├── schemas/                            # Pydantic validation schemas
│   │   ├── api/                            # API request/response schemas
│   │   │   ├── health.py                   # Health check schemas
│   │   │   └── search.py                   # 🆕 NEW: Search request/response schemas
│   │   ├── arxiv/                          # arXiv data schemas
│   │   └── pdf_parser/                     # PDF parsing schemas
│   ├── services/                           # Business logic
│   │   ├── arxiv/                          # arXiv API client
│   │   ├── pdf_parser/                     # Docling PDF processing
│   │   ├── opensearch/                     # 🆕 NEW: OpenSearch integration
│   │   │   ├── client.py                   # OpenSearch client implementation
│   │   │   ├── factory.py                  # Client factory pattern
│   │   │   ├── index_config.py             # Index configuration
│   │   │   └── query_builder.py            # BM25 query construction
│   │   ├── metadata_fetcher.py             # Complete ingestion pipeline
│   │   └── ollama/                         # Ollama LLM service
│   ├── db/                                 # Database configuration
│   ├── config.py                           # Environment configuration
│   └── dependencies.py                     # Dependency injection
│
├── notebooks/                              # Learning materials
│   ├── week1/                              # Week 1: Infrastructure setup
│   │   └── week1_setup.ipynb               # Complete setup guide
│   ├── week2/                              # Week 2: Data ingestion
│   │   └── week2_arxiv_integration.ipynb   # Data pipeline guide
│   └── week3/                              # 🆕 NEW: Keyword search
│       └── week3_opensearch.ipynb          # OpenSearch & BM25 guide
│
├── airflow/                                # Workflow orchestration
│   ├── dags/                               # Workflow definitions
│   │   ├── arxiv_ingestion/                # arXiv ingestion modules
│   │   └── arxiv_paper_ingestion.py        # Main ingestion DAG
│   └── requirements-airflow.txt            # Airflow dependencies
│
├── tests/                                  # Comprehensive test suite
├── static/                                 # Assets (images, GIFs)
└── compose.yml                             # Service orchestration
```

### **🔧 Essential Commands**

#### **Using the Makefile** (Recommended)
```bash
# View all available commands
make help

# Quick workflow
make start         # Start all services
make health        # Check all services health
make test          # Run tests
make stop          # Stop services
```

#### **All Available Commands**
| Command | Description |
|---------|-------------|
| `make start` | Start all services |
| `make stop` | Stop all services |
| `make restart` | Restart all services |
| `make status` | Show service status |
| `make logs` | Show service logs |
| `make health` | Check all services health |
| `make setup` | Install Python dependencies |
| `make format` | Format code |
| `make lint` | Lint and type check |
| `make test` | Run tests |
| `make test-cov` | Run tests with coverage |
| `make clean` | Clean up everything |

#### **Direct Commands** (Alternative)
```bash
# If you prefer using commands directly
docker compose up --build -d    # Start services
docker compose ps               # Check status
docker compose logs            # View logs
uv run pytest                 # Run tests
```

### **🎓 Target Audience**
| Who | Why |
|-----|-----|
| **AI/ML Engineers** | Learn production RAG architecture beyond tutorials |
| **Software Engineers** | Build end-to-end AI applications with best practices |
| **Data Scientists** | Implement production AI systems using modern tools |

---

## 🛠️ Troubleshooting

**Common Issues:**
- **Services not starting?** Wait 2-3 minutes, check `docker compose logs`
- **Port conflicts?** Stop other services using ports 8000, 8080, 5432, 9200
- **Memory issues?** Increase Docker Desktop memory allocation

**Get Help:**
- Check the comprehensive Week 1 notebook troubleshooting section
- Review service logs: `docker compose logs [service-name]`
- Complete reset: `docker compose down --volumes && docker compose up --build -d`

---

## 💰 Cost Structure

**This course is completely free!** You'll only need minimal costs for optional services:
- **Local Development:** $0 (everything runs locally)
- **Optional Cloud APIs:** ~$2-5 for external LLM services (if chosen)

---

<div align="center">
  <h3>🎉 Ready to Start Your AI Engineering Journey?</h3>
  <p><strong>Begin with the Week 1 setup notebook and build your first production RAG system!</strong></p>
  
  <p><em>For learners who want to master modern AI engineering</em></p>
  <p><strong>Built with love by Jam With AI</strong></p>
</div>

---

## 📄 License

MIT License - see [LICENSE](LICENSE) file for details.
