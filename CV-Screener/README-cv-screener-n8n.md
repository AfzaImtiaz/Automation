# CV Screener — Automated Hiring Pipeline

An intelligent CV screening workflow built with n8n that automatically scores job applicants using AI and logs results to a Notion Talent Board.

## Demo

▶️ [Watch Loom Demo](https://www.loom.com/share/bfc7d961f207458e83777132e9dd93bb)

## What It Does

When a candidate submits a job application through Google Forms, this workflow:
1. Detects the new form submission via Google Sheets
2. Fetches the uploaded CV from Google Drive
3. Sends the CV to Groq AI for scoring and analysis
4. Creates a candidate card in Notion with score, strengths, gaps, and recommendation
5. Sends a Gmail alert to the hiring manager if the candidate scores 7 or above

## Tech Stack

| Tool | Purpose |
|---|---|
| n8n | Workflow automation engine (self-hosted) |
| Google Forms | Job application entry form |
| Google Sheets | Form response storage and trigger |
| Google Drive | CV file storage |
| Groq AI (LLaMA 3.3) | CV analysis and scoring |
| Notion | Candidate Talent Board |
| Gmail | High-score candidate alerts |

## Workflow Architecture

```
Google Sheets Trigger
        ↓
HTTP Request (Fetch CV from Google Drive)
        ↓
Code Node (Convert CV to base64)
        ↓
HTTP Request (Send to Groq AI)
        ↓
Code Node (Parse AI response)
        ↓
HTTP Request (Create Notion card)
        ↓
IF Node (Score >= 7?)
   ↓ TRUE              ↓ FALSE
Gmail Alert        (ends — card already saved)
```

## AI Scoring Output

Each CV is scored by Groq AI and returns:
- **Score** — 1 to 10
- **Strengths** — 2-3 sentence summary
- **Gaps** — areas of concern
- **Recommendation** — Strong Yes / Yes / No

## Notion Database Properties

| Property | Type |
|---|---|
| Name | Title |
| Email | Email |
| Role | Select |
| AI Score | Number |
| Strengths | Text |
| Gaps | Text |
| Recommendation | Select |
| Applied At | Date |
| Status | Select |

## Environment Variables

Before running this workflow, replace all placeholder values with your own API keys. See `.env.example` in the root of this repo for the full list.

| Variable | Where to get it |
|---|---|
| GROQ_API_KEY | console.groq.com |
| NOTION_TOKEN | notion.so/my-integrations |
| NOTION_DATABASE_ID | Your Notion database URL |
| GOOGLE_OAUTH_CLIENT_ID | console.cloud.google.com |
| GOOGLE_OAUTH_CLIENT_SECRET | console.cloud.google.com |

## Setup Instructions

### Prerequisites
- n8n (self-hosted on Node.js 20 LTS)
- Google Cloud project with OAuth 2.0 credentials
- Google Sheets API and Google Drive API enabled
- Groq API key (console.groq.com)
- Notion integration token (notion.so/my-integrations)

### Steps
1. Import `n8n-CV screener.json` into your n8n instance
2. Set up Google OAuth credentials in n8n Settings → Credentials
3. Add your Groq API key to the HTTP Request node (Node 4) Authorization header
4. Create a Notion database with the 9 properties listed above
5. Add your Notion integration token and database ID to the Notion HTTP Request node
6. Connect your Google Form to a Google Sheet
7. Activate the workflow

## How to Test

1. Submit a test application through your Google Form with a real CV uploaded to Google Drive
2. Wait 60 seconds for the trigger to fire
3. Check your Notion Talent Board for the new candidate card
4. If the score is 7+, check Gmail for the alert

## Files Included

- `n8n-CV screener.json` — importable n8n workflow
- `SS_n8n_CV-screener_workflow.png` — workflow screenshot
- `Notion-cv-screener-n8n.zip` — Notion database template

---

Built during SkillSync Automation Workshop · n8n · Groq AI · Notion
