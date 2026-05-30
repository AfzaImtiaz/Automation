# SkillSync Automation Workshop — n8n & Make.com Projects

A collection of 4 automation workflows built during the SkillSync Automation Workshop covering n8n and Make.com. Each project solves a real-world problem using no-code/low-code automation tools, AI APIs, and cloud services.

**Built by:** [Afza Imtiaz](https://www.linkedin.com/in/afza-imtiaz)
**GitHub:** [github.com/AfzaImtiaz/Automation](https://github.com/AfzaImtiaz/Automation)

---

## Projects Overview

| # | Project | Platform | Tools | Demo |
|---|---|---|---|---|
| 1 | CV Screener | n8n | Google Forms, Groq AI, Notion, Gmail | [▶️ Loom](https://www.loom.com/share/bfc7d961f207458e83777132e9dd93bb) |
| 2 | Contact Form Auto-Responder | Make.com | Webhooks, Groq AI, Gmail | — |
| 3 | Job Application Tracker | Make.com | Tally, Railway MySQL | [▶️ Loom](https://www.loom.com/share/c2bd456d48ff4d7ab127fb2447aecdf5) |
| 4 | Feedback Form Router | Make.com | Tally, Gmail | — |

---

## Project 1 — CV Screener (n8n)

📁 `CV-Screener/` | [▶️ Watch Demo](https://www.loom.com/share/bfc7d961f207458e83777132e9dd93bb)

An intelligent hiring pipeline that automatically screens CVs using AI the moment a candidate submits a job application.

**How it works:**
- Candidate submits Google Form with CV upload
- n8n detects new row in linked Google Sheet
- CV is fetched from Google Drive and sent to Groq AI
- AI scores the CV 1-10 with strengths, gaps and recommendation
- Result is saved as a card in Notion Talent Board
- Gmail alert sent to hiring manager if score is 7 or above

**Tech Stack:** n8n · Google Forms · Google Sheets · Google Drive · Groq AI (LLaMA 3.3) · Notion · Gmail · ngrok

---

## Project 2 — Contact Form Auto-Responder (Make.com)

📁 `WorkFlow 1- Contact Form/`

Automatically replies to contact form submissions with a personalized AI-generated email — instantly, without any manual effort.

**How it works:**
- Contact form submits data via webhook to Make.com
- Groq AI generates a warm, personalized reply referencing the sender's message
- Gmail sends the AI-generated response automatically

**Tech Stack:** Make.com · Webhooks · Groq AI (LLaMA 3.3) · Gmail

---

## Project 3 — Job Application Tracker (Make.com)

📁 `Workflow 2- Job Application Tracker/` | [▶️ Watch Demo](https://www.loom.com/share/c2bd456d48ff4d7ab127fb2447aecdf5)

Eliminates spreadsheet chaos by automatically saving every job application to a real MySQL database the moment a form is submitted.

**How it works:**
- Candidate fills Tally form with job details
- Make.com triggers instantly on new response
- All 7 fields are inserted into Railway MySQL database with timestamp

**Tech Stack:** Make.com · Tally.so · Railway · MySQL

---

## Project 4 — Feedback Form Router (Make.com)

📁 `WorkFlow 3- FeedBack Form/`

Routes feedback responses to different email templates based on sentiment — positive feedback gets a thank you, negative feedback gets an apology and follow-up.

**How it works:**
- User submits feedback via Tally form
- Make.com router checks feedback type
- Positive → thank you email via Gmail
- Negative → apology and follow-up email via Gmail

**Tech Stack:** Make.com · Tally.so · Gmail

---

## Repository Structure

```
Automation/
├── CV-Screener/
│   ├── README.md
│   ├── n8n-CV screener.json
│   └── SS_n8n_CV-screener_workflow.png
│
├── WorkFlow 1- Contact Form/
│   ├── README.md
│   ├── Integration Webhooks.blueprint.json
│   └── workflow ss.jpeg
│
├── Workflow 2- Job Application Tracker/
│   ├── README.md
│   ├── Integration Tally.blueprint.json
│   └── screenshots/
│
├── WorkFlow 3- FeedBack Form/
│   ├── README.md
│   ├── Integration Tally, Gmail.blueprint.json
│   └── screenshots/
│
├── .env.example
├── .gitignore
└── README.md
```

---

## Environment Variables

All API keys and credentials have been removed from the workflow files. Before importing any workflow, create a `.env` file using `.env.example` as a template and fill in your own credentials.

```
GROQ_API_KEY=your_groq_api_key_here
NOTION_TOKEN=your_notion_token_here
NOTION_DATABASE_ID=your_notion_database_id_here
RAILWAY_HOST=your_railway_host_here
RAILWAY_PASSWORD=your_railway_password_here
TALLY_API_KEY=your_tally_api_key_here
GOOGLE_OAUTH_CLIENT_ID=your_google_client_id_here
GOOGLE_OAUTH_CLIENT_SECRET=your_google_client_secret_here
```

**Where to get each key:**

| Key | Source |
|---|---|
| GROQ_API_KEY | [console.groq.com](https://console.groq.com) |
| NOTION_TOKEN | [notion.so/my-integrations](https://notion.so/my-integrations) |
| NOTION_DATABASE_ID | Your Notion database URL |
| RAILWAY credentials | [railway.app](https://railway.app) → Variables tab |
| TALLY_API_KEY | tally.so → Settings → API Key |
| GOOGLE_OAUTH | [console.cloud.google.com](https://console.cloud.google.com) |

---

## How to Import Workflows

**n8n (CV Screener):**
1. Open n8n at `http://localhost:5678`
2. Click **...** → **Import from file**
3. Select `n8n-CV screener.json`
4. Update all credentials in each node

**Make.com (all other workflows):**
1. Go to make.com → Create new scenario
2. Click **...** → **Import Blueprint**
3. Select the `.blueprint.json` file
4. Reconnect all modules with your own credentials

---

## Prerequisites

- Node.js 20 LTS (for n8n)
- n8n installed globally: `npm install n8n -g --legacy-peer-deps`
- Make.com account (free tier works)
- Accounts on: Google, Groq, Notion, Tally, Railway

---

Built during SkillSync n8n Launchpad Workshop · May 2026
