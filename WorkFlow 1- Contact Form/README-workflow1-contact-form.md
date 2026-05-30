# Contact Form Auto-Responder — AI-Powered Email Reply

An automated contact form pipeline built with Make.com that receives form submissions via webhook, generates a personalized AI reply using Groq, and sends it via Gmail.

## What It Does

When a contact form is submitted:
1. Make.com receives the submission via a custom webhook
2. The message is sent to Groq AI (LLaMA 3.3) which generates a warm, personalized reply
3. The AI-generated response is sent back to the sender via Gmail automatically

No manual email writing. Every inquiry gets an instant, personalized response.

## Tech Stack

| Tool | Purpose |
|---|---|
| Make.com | Automation platform |
| Webhooks | Receives form submissions |
| Groq AI (LLaMA 3.3) | Generates personalized email replies |
| Gmail | Sends the AI-generated response |

## Workflow Architecture

```
Webhook (receives form submission)
        ↓
HTTP Request (Groq AI — generate reply)
        ↓
Gmail (send personalized response)
```

## AI Prompt Logic

The AI acts as a professional customer service assistant. It:
- Addresses the sender by first name
- References their specific message content
- Writes a warm, concise, professional reply
- Maintains consistent brand tone

## Setup Instructions

### Prerequisites
- Make.com account (free tier works)
- Groq API key (console.groq.com)
- Gmail account connected to Make.com

### Steps
1. Import `Integration Webhooks.blueprint.json` into Make.com
2. Update the Groq API key in the HTTP Request module Authorization header
3. Connect your Gmail account in the Gmail module
4. Copy the webhook URL from Make.com
5. Add the webhook URL to your contact form's submission endpoint
6. Turn the scenario ON

## How to Test

1. Send a POST request to the webhook URL with a name, email, and message
2. Make.com triggers instantly
3. Check the sender's inbox — AI-generated reply should arrive within seconds

## Files Included

- `Integration Webhooks.blueprint.json` — importable Make.com scenario
- `workflow ss.jpeg` — workflow screenshot
- `gmail.jpeg` — example Gmail output

---

Built during SkillSync Automation Workshop · Make.com · Groq AI · Gmail
