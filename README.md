# n8n Workflow Portfolio

A collection of production-grade n8n automation workflows I've built for real clients and internal projects. All sensitive data (client names, emails, webhook URLs, credentials) has been anonymized.

These workflows demonstrate expertise in **AI/LLM integration**, **RAG systems**, **document processing**, **API automation**, and **production monitoring**.

---

## Workflows

### RAG (Retrieval-Augmented Generation)
A complete RAG system split into three operational workflows:

| Workflow | Nodes | Description |
|----------|-------|-------------|
| [rag-ingestion-system](rag/rag-ingestion-system.json) | 102 | Watches Google Drive for new documents, extracts text (PDF/other), splits into chunks, generates OpenAI embeddings, and stores in Supabase vector store with metadata tracking |
| [rag-chat-agent](rag/rag-chat-agent.json) | 34 | Webhook-triggered AI chatbot with Cohere reranking, Supabase vector retrieval, OpenAI LLM, and Postgres-backed chat memory |
| [rag-cleanup](rag/rag-cleanup.json) | 48 | Scheduled maintenance — compares Drive files against vector store and removes orphaned embeddings |

**Tech:** OpenAI Embeddings, Cohere Reranker, Supabase Vector Store, Google Drive, Postgres

---

### AI Agents

| Workflow | Nodes | Description |
|----------|-------|-------------|
| [telegram-ai-agent](ai-agents/telegram-ai-agent.json) | 56 | Telegram-based AI assistant with buffer memory, SQL tool for querying Postgres, and Supabase logging |
| [voice-finance-assistant](ai-agents/voice-finance-assistant.json) | 74 | Telegram bot that accepts text and voice messages, transcribes via OpenAI Whisper, categorizes expenses with AI, logs to Google Sheets. Includes n8n evaluation nodes for quality testing |
| [ai-sales-agent](ai-agents/ai-sales-agent.json) | 47 | AI-powered sales chatbot for a business — uses OpenAI agent with tools for pricing lookup, lead management, quote generation, and email sending |
| [pre-call-report-generator](ai-agents/pre-call-report-generator.json) | 40 | Generates sales briefings by scraping LinkedIn profiles + company websites, then synthesizing with OpenAI |

**Tech:** OpenAI (GPT + Whisper), Telegram, Google Sheets, Proxycurl, Gmail

---

### AI Ideas Pipeline
A 5-workflow orchestrated pipeline for evaluating and researching AI product ideas:

| Step | Workflow | Nodes | Description |
|------|----------|-------|-------------|
| 1 | [form-assistant](ai-agents/ai-ideas-01-form-assistant.json) | 36 | Webhook chatbot (Google Gemini + memory) that guides users through idea submission |
| 2 | [save-to-database](ai-agents/ai-ideas-02-save-to-database.json) | 65 | Sub-workflow that validates and persists ideas to Google Sheets + sends confirmation |
| 3 | [scoring-assistant](ai-agents/ai-ideas-03-scoring-assistant.json) | 128 | Scheduled AI scoring of ideas on business value metrics using Gemini |
| 4 | [hypothesis-generator](ai-agents/ai-ideas-04-hypothesis-generator.json) | 61 | Generates testable hypotheses for top-scoring ideas |
| 5 | [research-brief](ai-agents/ai-ideas-05-research-brief.json) | 61 | Creates research briefs and distributes via email |

**Tech:** Google Gemini, Google Sheets, Sub-workflows, Gmail, Scheduled triggers

---

### Invoice Automation

| Workflow | Nodes | Description |
|----------|-------|-------------|
| [ai-invoice-processor](invoice-automation/ai-invoice-processor.json) | 176 | End-to-end invoice processing: watches Google Drive for uploads, routes by file type (PDF/image), runs OCR, extracts structured data with OpenAI, deduplicates against database, appends to spreadsheet, moves processed files |

**Tech:** OCR API, OpenAI (LangChain Information Extractor), Google Drive, Google Sheets, Supabase

---

### Government API Integration (KSeF)
Integration with Poland's National e-Invoice System (KSeF):

| Workflow | Nodes | Description |
|----------|-------|-------------|
| [ksef-authentication](government-api/ksef-authentication.json) | — | Token-based authentication with encryption for KSeF API |
| [ksef-invoice-inbox](government-api/ksef-invoice-inbox.json) | — | Fetches and processes incoming e-invoices |
| [ksef-send-invoice](government-api/ksef-send-invoice.json) | — | Generates XML invoices and submits to KSeF |

**Tech:** KSeF REST API, XML generation, Encryption, HTTP Request, Sub-workflows

---

### Data Enrichment

| Workflow | Nodes | Description |
|----------|-------|-------------|
| [tmdb-image-enrichment](data-enrichment/tmdb-image-enrichment.json) | 86 | Batch enrichment pipeline: reads titles from Google Sheets, searches TMDB API for matching movies, fetches poster/backdrop images, updates spreadsheet with image URLs |

**Tech:** TMDB API, Google Sheets, Supabase, Batch processing

---

### Social Media Content Pipeline

| Workflow | Nodes | Description |
|----------|-------|-------------|
| [linkedin-topic-discovery](social-media/linkedin-topic-discovery.json) | 61 | Reads RSS feeds + Hacker News, scores content relevance with OpenAI, writes curated topics to Google Sheets, sends email digest |
| [linkedin-post-publisher](social-media/linkedin-post-publisher.json) | 36 | Publishes approved posts from Google Sheets to LinkedIn API, updates status, sends confirmation emails |

**Tech:** RSS, Hacker News API, LinkedIn API, OpenAI, Google Sheets, Gmail

---

### Monitoring & Error Handling

| Workflow | Nodes | Description |
|----------|-------|-------------|
| [global-error-handler](monitoring/global-error-handler.json) | 44 | Catches workflow failures, logs to Supabase, sends detailed error alerts via Gmail |
| [automation-health-monitor](monitoring/automation-health-monitor.json) | 20 | Scheduled health checks — queries Supabase for automation metrics, sends summary reports |

**Tech:** Supabase, Gmail, Scheduled triggers, n8n Error Trigger

---

### DevOps

| Workflow | Nodes | Description |
|----------|-------|-------------|
| [n8n-github-backup](devops/n8n-github-backup.json) | 21 | Scheduled backup of all n8n workflows to GitHub — fetches via n8n API, commits each as JSON, generates index |

**Tech:** n8n API, GitHub API

---

## Skills Demonstrated

- **AI/LLM**: OpenAI (GPT, Whisper, Embeddings), Google Gemini, LangChain agents, information extraction
- **RAG**: Vector stores, embeddings, reranking (Cohere), chat memory, document ingestion
- **Integrations**: Google Drive, Sheets, Gmail, Telegram, LinkedIn, TMDB, KSeF, GitHub, RSS
- **Architecture**: Multi-workflow orchestration, sub-workflows, error handling, monitoring
- **Data**: OCR, PDF extraction, batch processing, deduplication, vector store maintenance
- **Production**: Dev/prod environments, error workflows, health monitoring, automated backups

---

## Usage

These are n8n workflow JSON files. To explore them:

1. Import any `.json` file into your n8n instance via **Settings → Import Workflow**
2. The workflows reference external credentials that you'll need to configure for your own environment
3. All webhook URLs and API endpoints have been anonymized

---

## Author

**Mikołaj Wojnarowski** — AI Automation Consultant

- [LinkedIn](https://linkedin.com/in/mikolajwojnarowski)
- [Website](https://wdrazaj.ai)
