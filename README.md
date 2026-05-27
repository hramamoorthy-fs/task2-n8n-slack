# Apollo Lead Enrichment Automation

## Description

An automated lead enrichment workflow built using n8n, Apollo API, Google Sheets, Mailmeteor, Slack, and a custom HTML dashboard.

This workflow automatically reads company website data from Google Sheets, extracts domains, searches Apollo for relevant contacts, checks for duplicate leads, enriches contact information, retrieves email addresses, stores new leads in Google Sheets, and sends notifications to Slack.

The project also includes a simple web dashboard with a button interface that triggers the workflow through an n8n webhook.

---

## Features

✅ Read company website data from Google Sheets

✅ Extract and normalize domains

✅ Search contacts using Apollo API

✅ Detect duplicate leads automatically

✅ Enrich lead data

✅ Find missing emails using Mailmeteor

✅ Save enriched leads to Google Sheets

✅ Send Slack notifications

✅ Trigger workflow from a custom dashboard

---

## Technologies Used

- n8n
- Apollo API
- Google Sheets API
- Mailmeteor API
- Slack Webhooks
- HTML
- CSS
- JavaScript

---

# Project Structure

```bash
project-folder/
│
├── apollotask2.json       # n8n workflow export
├── button.html            # Dashboard UI
├── README.md
```

---

## Workflow Architecture

Webhook Trigger

↓

Read Company Data From Google Sheets

↓

Parse Website Domain

↓

Apollo Search API

↓

Extract Contact Information

↓

Read Existing Leads

↓

Check Duplicate Leads

↓

If Duplicate
→ Send Slack Notification

Else

↓

Apollo Lead Enrichment

↓

Check Email Availability

↓

Email Found?
│
├── Yes → Save Lead
│
└── No → Search Email via Mailmeteor

↓

Append Lead To Google Sheets

↓

Slack Notification

---

# How To Use

## Step 1: Clone Repository

```bash
git clone https://github.com/yourusername/apollo-lead-enrichment.git

cd apollo-lead-enrichment
```

---

## Step 2: Import Workflow into n8n

1. Open n8n
2. Click:

   Workflows → Import from File

3. Select:

```bash
apollotask2.json
```

4. Save the workflow

---

## Step 3: Configure Credentials

Update the following credentials inside n8n:

### Google Sheets

Add:

- Google OAuth Credentials

---

### Apollo API

Replace:

```javascript
X-Api-Key: YOUR_APOLLO_API_KEY
```

with your actual Apollo API key.

---

### Mailmeteor API

Replace:

```javascript
Bearer YOUR_MAILMETEOR_API_KEY
```

with your Mailmeteor API key.

---

### Slack Webhook

Replace:

```javascript
https://hooks.slack.com/your-webhook-url
```

with your Slack webhook URL.

---

## Step 4: Update Google Sheet IDs

Replace spreadsheet IDs:

Input Sheet:

```bash
YOUR_INPUT_SHEET_ID
```

Output Sheet:

```bash
YOUR_OUTPUT_SHEET_ID
```

---

## Step 5: Activate Workflow

Turn ON workflow:

```bash
Active → ON
```

---

## Step 6: Configure Dashboard

Open:

```bash
button.html
```

Update:

```javascript
const N8N_WEBHOOK_URL="YOUR_N8N_WEBHOOK_URL"
```

Example:

```javascript
const N8N_WEBHOOK_URL="https://yourdomain.app.n8n.cloud/webhook/start-enrichment"
```

Save the file.

---

## Step 7: Run the Workflow

Open:

```bash
button.html
```

Click:

```bash
Start Enrichment
```

The workflow will:

- Read companies
- Search contacts
- Enrich data
- Save leads
- Send Slack updates

---

## Output Fields

Generated output includes:

| Field | Description |
|---------|-------------|
| company_name | Company Name |
| website | Website URL |
| first_name | Contact First Name |
| last_name | Contact Last Name |
| designation | Job Title |
| email | Contact Email |
| linkedin_url | LinkedIn Profile |
| employee_count | Employee Count |
| industry | Industry Type |

---

## Example Notification

New Leads Added Successfully

Name: John Doe

Company: ABC Company

Designation: Marketing Manager

Email: john@abc.com

LinkedIn:
https://linkedin.com/in/johndoe

---

## Future Improvements

- Add Stop Workflow functionality
- Add database integration
- Add analytics dashboard
- Add lead scoring
- Add email validation
- Add retry mechanism

---

## Author

Hari Krishna
