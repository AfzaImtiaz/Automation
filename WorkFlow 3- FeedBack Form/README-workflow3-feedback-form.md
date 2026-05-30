# Feedback Form Auto-Router — Smart Email Response System

An automated feedback handling workflow built with Make.com that receives feedback via Tally, routes it based on sentiment (positive or negative), and sends a tailored Gmail response for each case.

## What It Does

When a feedback form is submitted through Tally:
1. Make.com receives the new response
2. A router checks the feedback sentiment/type
3. Positive feedback → sends a thank you email via Gmail
4. Negative feedback → sends an apology and follow-up email via Gmail

Every piece of feedback gets an instant, appropriate response — automatically.

## Tech Stack

| Tool | Purpose |
|---|---|
| Make.com | Automation platform |
| Tally.so | Feedback collection form |
| Make.com Router | Splits flow based on feedback type |
| Gmail | Sends tailored responses |

## Workflow Architecture

```
Tally (Watch New Responses)
        ↓
Router (Positive or Negative?)
   ↓ Positive          ↓ Negative
Gmail (Thank You)   Gmail (Apology + Follow-up)
```

## Routing Logic

The router splits the workflow into two paths based on the feedback response:
- **Positive path** — triggered when feedback is positive/satisfied
- **Negative path** — triggered when feedback is negative/unsatisfied

Each path sends a different, contextually appropriate Gmail response.

## Setup Instructions

### Prerequisites
- Make.com account
- Tally.so account
- Gmail account connected to Make.com

### Steps
1. Create your Tally feedback form with fields for name, email, and feedback
2. Import `Integration Tally, Gmail.blueprint.json` into Make.com
3. Connect your Tally account using your Tally API key
4. Connect your Gmail account in both Gmail modules
5. Customize the email templates in each Gmail module
6. Turn the scenario ON

## How to Test

1. Click **Run Once** in Make.com
2. Submit a positive feedback response through your Tally form
3. Verify the thank you email arrives
4. Click **Run Once** again
5. Submit a negative feedback response
6. Verify the apology email arrives

## Files Included

- `Integration Tally, Gmail.blueprint.json` — importable Make.com scenario
- `workflow.jpeg` — workflow screenshot
- `Positive Feedback.jpeg` — example positive response email
- `Negative Feedback.jpeg` — example negative response email

---

Built during SkillSync Automation Workshop · Make.com · Tally.so · Gmail
