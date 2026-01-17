🤖 AI Review Automation System
End-to-End ML Orchestration with n8n, Slack & OpenAI

Continuation of:
🔗 Multimodal Product Review Analyzer
(ML training, modeling & inference pipeline)

This project extends a trained machine learning sentiment analysis system into a fully automated, production-style AI workflow.

The system connects:

a Python ML inference API

n8n as the orchestration engine

OpenAI for natural language explanations

Slack as the user interface

It demonstrates how machine learning models are integrated into real business systems, not just trained offline.

🚀 What This Project Demonstrates

✅ ML model deployment via REST API
✅ Workflow orchestration (event-driven automation)
✅ Conversational AI interface
✅ Asynchronous processing
✅ Real-time Slack integration
✅ Clean system architecture
✅ Production-style separation of concerns

This project focuses on ML systems engineering, not only model accuracy.

🧠 Workflow Architecture
![AI Review Automation Architecture](image/ai_review_automation_architecture.png)


🏗 System Components
1️⃣ Python ML Inference API

Loads trained sentiment model

Accepts queries about review results

Computes aggregations (counts, examples, summaries)

Returns structured JSON responses

Runs locally.


2️⃣ n8n — Automation & Orchestration Layer

n8n acts as the central brain of the system.

Responsibilities:

Receives incoming webhooks

Routes user questions

Calls ML inference API

Sends ML output to OpenAI

Formats clean JSON responses

Sends results back to Slack

Two workflows exist:

🔹 Workflow A — Batch Analysis

Triggered by new review data

Sends reviews to ML API

Stores predictions

Sends alerts & summaries to Slack

🔹 Workflow B — Chat / Q&A Interface

Receives natural language questions

Queries ML results

Uses GPT for explanation

Returns structured responses

3️⃣ OpenAI — Explanation Layer

OpenAI is not used for prediction.

It is used only to:

Interpret ML output

Convert statistics into human-readable explanations

Provide conversational analytics

This separation ensures:

ML remains deterministic

LLM remains explanatory

4️⃣ Slack — User Interface

Slack acts as the frontend.

Users can ask questions such as:

“How many negative reviews are there?”

“What are the most common complaints?”

“Give examples of bad reviews”

Slack receives:

Immediate acknowledgment

Final AI-generated response after processing

🌐 Public Webhook Access (ngrok)
Why ngrok is required:

Slack slash commands and interactive messages require a public HTTPS endpoint.

During development, n8n runs locally so

Slack cannot access localhost directly.

To solve this, ngrok is used to expose the local n8n instance to the internet securely.

How it works
Slack → ngrok → n8n webhook → workflow execution


ngrok generates a temporary public URL

which forwards traffic to local url.


This URL is configured in the Slack App as the request URL for slash commands.


🔄 End-to-End Flow (Chat Workflow)
1. User asks question in Slack
2. Slack sends request to n8n webhook (via ngrok)
3. n8n immediately responds: “Analyzing…”
4. n8n calls ML API (/query)
5. ML API returns structured results
6. n8n sends data to OpenAI
7. OpenAI generates explanation
8. n8n sends final message back to Slack


This design supports asynchronous execution, avoiding Slack timeouts.

🧪 Example API Response
{
  "answer": "There are 12 negative reviews out of 50 total.",
  "count": 12,
  "examples": [
    "Battery stopped working after two days",
    "Very poor build quality"
  ],
  "timestamp": "2026-01-16T09:41:29Z"
}

📁 Repository Structure
ai-review-automation/
├── README.md
├── n8n-workflows/
│   ├── batch-analysis.json
│   └── chat-interface.json
├── diagrams/
│   └── architecture.png
├── screenshots/
│   └── slack-demo.png

🎯 Key Engineering Concepts Demonstrated

Event-driven architecture

ML model serving

Workflow orchestration

API-based system integration

LLM-as-explainer pattern

Async webhook design

Real-world ML deployment practices

🔮 Future Improvements

Dockerized deployment

Cloud-hosted n8n

Scheduled automated reports

Role-based Slack commands

Multi-product review support

Monitoring & logging dashboards

👤 Author

Myrto Gasparinatou
🎓 PhD Candidate in Machine Learning | AI Engineer

GitHub: @mirtogaspar

LinkedIn: linkedin.com/in/mirto-m-gasparinatou

Email: mgasparinatou@gmail.com
