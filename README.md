# 🤖 AI Review Automation System

End-to-end automation platform that extends a machine learning sentiment analysis system into a **production-style AI workflow**, combining ML inference, orchestration, LLM reasoning, and Slack-based interaction.

This repository is the continuation of the ML project:

➡️ **multimodal-review-analyzer**  
(Training, evaluation, and model development)

This repo focuses on **deployment, automation, and AI systems design**.

---

## 🚀 What This Project Demonstrates

This project shows how to move from a trained ML model to a **real-world AI system**.

It demonstrates:

✅ ML model deployment via API  
✅ Workflow orchestration with n8n  
✅ Conversational AI interface  
✅ Asynchronous automation  
✅ Slack integration  
✅ Public webhook exposure using ngrok  
✅ Clean system architecture  

This is **not just ML** — it is **ML + MLOps + Automation + AI Systems Engineering**.

---

## 🧠 Architecture

![Architecture Diagram](image/ai_review_automation_architecture.png)

---

## 🔄 System Overview

### Two Complementary Workflows

This project consists of **two independent but connected workflows**.

---

### 🅰 Workflow A — Batch ML Analysis Pipeline

Used for automated analysis of product reviews.

**Responsibilities:**
- Receive reviews (Google Sheets / Webhook)
- Run sentiment inference via Python ML API
- Aggregate predictions
- Store results
- Send Slack summaries

This workflow demonstrates:

- Data pipelines
- ML inference at scale
- Automation logic
- Monitoring & reporting

---

### 🅱 Workflow B — Conversational AI Interface

Used for **interactive querying of ML results**.

**Responsibilities:**
- Receive user questions from Slack
- Query ML analysis results
- Ask GPT to explain findings
- Return structured JSON
- Display final response in Slack

This workflow demonstrates:

- AI agents
- LLM reasoning on top of ML outputs
- API-based conversation systems
- Production-style chatbot design

---

## 🧩 Architecture Explanation

### 1️⃣ Slack (User Interface)

Users interact through Slack asking questions such as "How many negative reviews are there?"

### 2️⃣ ngrok — Public Tunnel

Slack requires a **public HTTPS endpoint**.

Since n8n runs locally, ngrok is used to expose it. This allows Slack to reach the local n8n instance securely.

### 3️⃣ n8n — Orchestration Layer

n8n is the **brain of the system**.

It handles:
- Webhooks
- Routing logic
- API calls
- Error handling
- Automation logic

n8n coordinates all components without embedding business logic.

---

### 4️⃣ Python ML API (Flask)

A lightweight Flask API wraps the trained ML model.

Responsibilities:
- Load trained model
- Perform sentiment inference
- Aggregate results
- Return structured JSON

This keeps ML logic fully separated from orchestration.

---

### 5️⃣ OpenAI GPT — Explanation Layer

The ML model returns **numbers**.

GPT converts them into **human-readable insight**:

- Explains results
- Summarizes trends
- Adds natural language reasoning

GPT never replaces ML, it **interprets ML output**.

---

### 6️⃣ Slack Response

The final explanation is posted back to Slack automatically:

- Clean
- Human-readable
- Business-friendly

This closes the full loop.

---

## 🔁 End-to-End Flow
Slack user question
↓
ngrok public endpoint
↓
n8n webhook (/chat)
↓
Python ML API (/query)
↓
Aggregated predictions
↓
OpenAI GPT explanation
↓
n8n response
↓
Slack message to user

🛠️ Tech Stack
| Layer         | Technology                          |
| ------------- | ----------------------------------- |
| ML            | scikit-learn, TF-IDF, Random Forest |
| API           | Python, Flask                       |
| Orchestration | n8n (self-hosted)                   |
| LLM           | OpenAI GPT                          |
| Messaging     | Slack                               |
| Tunneling     | ngrok                               |
| Deployment    | Local (cloud-ready)                 |

📂 Repository Structure
ai-review-automation/
│
├── image/
│   └── ai_review_automation_architecture.png
│
├── workflows/
│   ├── batch-analysis.json
│   └── chat-interface.json
│
├── ml_api.py
├── requirements.txt
├── README.md
└── .env.example




