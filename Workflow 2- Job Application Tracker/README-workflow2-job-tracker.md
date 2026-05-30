# Job Application Tracker — Automated MySQL Database Pipeline

A job application tracking system built with Make.com that automatically saves every application to a real MySQL database hosted on Railway — no spreadsheets needed.

## Demo

▶️ [Watch Loom Demo](https://www.loom.com/share/c2bd456d48ff4d7ab127fb2447aecdf5)

## What It Does

When a job application is submitted through the Tally form:
1. Make.com picks up the new response instantly
2. All 7 fields are mapped and inserted into a MySQL database on Railway
3. Every application is permanently stored with a timestamp

No manual tracking. No spreadsheet chaos. Every application organized in a real database.

## Tech Stack

| Tool | Purpose |
|---|---|
| Make.com | Automation platform |
| Tally.so | Job application entry form |
| Railway | Cloud-hosted MySQL database |
| MySQL | Relational database storage |

## Workflow Architecture

```
Tally (Watch New Responses)
        ↓
MySQL — Insert a Row (Railway Database)
```

## Database Schema

```sql
CREATE TABLE IF NOT EXISTS job_applications (
  id INT AUTO_INCREMENT PRIMARY KEY,
  company_name VARCHAR(255),
  job_role VARCHAR(255),
  job_link TEXT,
  date_applied DATE,
  status VARCHAR(100),
  follow_up_date DATE,
  notes TEXT,
  created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);
```

## Form Fields

| Field | Database Column | Type |
|---|---|---|
| Company Name | company_name | VARCHAR |
| Job Role | job_role | VARCHAR |
| Job Link | job_link | TEXT |
| Date Applied | date_applied | DATE |
| Status | status | VARCHAR |
| Follow Up Date | follow_up_date | DATE |
| Notes | notes | TEXT |

## Environment Variables

Before running this workflow, replace all placeholder values with your own credentials. See `.env.example` in the root of this repo for the full list.

| Variable | Where to get it |
|---|---|
| TALLY_API_KEY | tally.so → Settings → API Key |
| RAILWAY_HOST | Railway → Variables → MYSQL_PUBLIC_URL |
| RAILWAY_PASSWORD | Railway → Variables → MYSQL_PUBLIC_URL |

## Setup Instructions

### Prerequisites
- Make.com account
- Tally.so account
- Railway account (railway.app)

### Steps
1. Deploy MySQL on Railway — click New Project → Deploy MySQL
2. Copy the `MYSQL_PUBLIC_URL` from Railway Variables tab
3. Create your Tally form with the 7 fields listed above
4. Import `Integration Tally.blueprint.json` into Make.com
5. Create a new MySQL connection in Make.com using your Railway credentials
6. Run the CREATE TABLE query once to set up the database
7. Map Tally fields to MySQL columns in the Insert module
8. Turn the scenario ON

### Extracting Railway Credentials from URL

Your `MYSQL_PUBLIC_URL` looks like:
```
mysql://root:PASSWORD@HOST:PORT/railway
```

Extract:
- **Username:** root
- **Password:** string between `:` and `@`
- **Host:** part after `@` before next `:`
- **Port:** number after host
- **Database:** railway

## How to Test

1. Click **Run Once** in Make.com
2. Immediately submit a test application through your Tally form
3. Go to Railway → Database → Query tab
4. Run `SELECT * FROM job_applications;` to verify the row was saved

## Files Included

- `Integration Tally.blueprint.json` — importable Make.com scenario
- `Screenshot-Job Application Tracker (Make.com).png` — Make.com scenario screenshot
- `Screenshot-Job Application Tracker(Railway).png` — Railway database screenshot

---

Built during SkillSync Automation Workshop · Make.com · Tally.so · Railway MySQL
