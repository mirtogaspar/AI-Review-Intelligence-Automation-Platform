🤖 AI Review Intelligence Automation Platform

n8n · Python ML API · OpenAI · Slack

This project extends the Multi-Modal Product Review Analyzer into a production-style AI automation system.

It demonstrates how machine learning models can be operationalized using workflow orchestration, APIs, and conversational interfaces — transforming static ML models into interactive decision-support systems.

🚀 Project Overview

This repository focuses on ML deployment, orchestration, and AI system design.

While the previous project trained and evaluated the sentiment model, this project shows:

how predictions are consumed by downstream systems

how users interact with ML results via chat

how automation replaces manual analysis

how AI explanations are layered on top of ML outputs

This is a real-world ML engineering continuation, not a toy demo.

🧠 What This System Does

The platform enables:

✅ Automatic analysis of review batches
✅ Centralized storage of ML predictions
✅ Natural-language querying of ML results
✅ Slack-based conversational AI interface
✅ Human-readable explanations of model output

🏗️ High-Level Architecture
Google Sheets / Webhooks
          |
          v
        n8n
          |
          v
Python ML API (Flask)
(sentiment inference)
          |
          v
Results Store (in-memory / extensible)
          |
          v
OpenAI (LLM explanations)
          |
          v
Slack AI Assistant

🔧 Tech Stack
Layer	Technology
Orchestration	n8n (self-hosted)
ML Inference	Python + Flask
Model	Random Forest (multimodal)
NLP	TF-IDF (text)
LLM	OpenAI GPT
Interface	Slack Slash Commands
Tunneling	ngrok
Data Source	Google Sheets / Webhooks
🧩 Workflows Implemented
🔹 Workflow A — Batch Review Analysis

Purpose: ML Ops & Automation

Steps:

Receive reviews (Google Sheets or webhook)

Send reviews to ML API (/batch_predict)

Store sentiment predictions

Generate statistics

Send Slack alerts and summaries

Demonstrates:

ML pipeline automation

API orchestration

batch inference

operational monitoring

🔹 Workflow B — Conversational Q&A Interface

Purpose: AI systems & human interaction

User flow:

/ask-reviews how many negative reviews are there?


System flow:

Slack
   ↓
n8n Webhook (/chat)
   ↓
ML API (/query)
   ↓
OpenAI (explanation)
   ↓
Slack response


Example response:

🤖 AI Review Assistant
There are 2 negative reviews out of 10 total.

Supported questions:

How many negative reviews are there?

How many positive reviews?

What is the average confidence?

Show examples of negative reviews

🧪 Verified End-to-End Test

The system was validated using direct API calls:

curl -X POST http://localhost:5678/webhook-test/chat \
  -H "Content-Type: application/json" \
  -d '{"question":"How many negative reviews are there?"}'


Response:

{
  "answer": "Based on the provided ML data...",
  "data": {
    "answer": "There are 0 negative reviews out of 2 total.",
    "count": 0,
    "examples": []
  },
  "timestamp": "2026-01-16T09:41:29.029Z"
}


✅ Webhook routing works
✅ ML API responds correctly
✅ LLM explanation layer works
✅ JSON contract is stable
✅ End-to-end system validated

🧠 Key Engineering Concepts Demonstrated

This project showcases real-world ML engineering skills:

✅ ML → Product Transition

Turning trained models into usable systems.

✅ Model Serving

Deploying ML inference through REST APIs.

✅ Orchestration Layer

Using n8n as an integration backbone.

✅ Asynchronous Systems

Instant Slack responses + delayed processing.

✅ Conversational Analytics

Querying ML results with natural language.

✅ Separation of Concerns

ML model = prediction

LLM = explanation

n8n = orchestration

Slack = interface

🧩 Repository Structure
ai-review-automation/
├── workflows/
│   ├── batch_analysis_workflow.json
│   └── chat_interface_workflow.json
│
├── ml_api/
│   └── ml_api.py
│
├── diagrams/
│   └── architecture.png
│
├── README.md
└── .gitignore

🔗 Related Repository

This project builds directly on:

👉 Multi-Modal Product Review Analyzer
https://github.com/mirtogaspar/multimodal-review-analyzer

That repository focuses on:

ML training

data leakage prevention

realistic evaluation

feature engineering

This repository focuses on:

deployment

orchestration

automation

AI interaction
👤 Author

Myrto Gasparinatou
🎓 PhD Candidate in Machine Learning | AI Engineer

GitHub: https://github.com/mirtogaspar

LinkedIn: https://linkedin.com/in/mirto-m-gasparinatou

Email: mgasparinatou@gmail.com
