# google-sheet-reader-automation
📡 n8n Webhook + Google Sheets (HTTP Request Automation)

📌 Overview

This project demonstrates how to use n8n to create a simple backend API using:

- Webhook (trigger)
- Google Sheets (data source)
- HTTP Request (to call the API)

No AI, no external APIs — only HTTP + Google Sheets.

---

⚙️ Architecture

🔹 Workflow 1 (Backend API)

Webhook → Google Sheets (Get Rows) → Respond to Webhook

🔹 Workflow 2 (Client)

HTTP Request → Calls Webhook URL

---

🚀 Setup Guide

🔹 Workflow 1: Webhook + Google Sheets

1. Webhook Node

- Method: GET (or POST)
- Path: get-sheet-data
- Response Mode: Using "Respond to Webhook" node

IMPORTANT:

- Activate the workflow
- Use Production URL (not test URL)

---

2. Google Sheets Node

- Operation: Get Rows
- Select your spreadsheet and sheet

---

3. Respond to Webhook Node

- Response Format: JSON

Example:
{
"status": "success",
"data": {{$json}}
}

---

Final Flow

Webhook → Google Sheets → Respond to Webhook

---

🔹 Workflow 2: HTTP Request

HTTP Request Node Config

- Method: GET
- URL:
  https://your-n8n-domain/webhook/get-sheet-data

IMPORTANT:

- Use Production URL only

---

📊 Example Google Sheets Data

Name| Score| Department
John| 90| CSE
Alice| 85| ECE
Ravi| 88| IT

---
Demo:
<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/c3bfdae6-2f54-49f1-a355-6c9082f5926d" />
<img width="960" height="540" alt="image" src="https://github.com/user-attachments/assets/28850adb-37d4-4dda-bd74-00c658640225" />



📤 Example JSON Output

{
"status": "success",
"data": [
{
"Name": "John",
"Score": 90,
"Department": "CSE"
},
{
"Name": "Alice",
"Score": 85,
"Department": "ECE"
},
{
"Name": "Ravi",
"Score": 88,
"Department": "IT"
}
]
}

---

⚠️ Common Issues

1. Webhook not registered
   Cause: Workflow not active or using test URL
   Fix: Activate workflow and use production URL

2. No response
   Cause: Missing Respond to Webhook node
   Fix: Add and connect the node properly

3. Empty data
   Cause: Google Sheets not configured correctly
   Fix: Check sheet name, permissions, and data

---

💡 Tips

- Use GET to fetch all rows
- Use POST to send filters or parameters
- Can be extended with filtering and frontend apps

---

🎯 Summary

- Workflow 1 = API (Webhook + Google Sheets)
- Workflow 2 = Client (HTTP Request)
- Always use Production Webhook URL
- Activate workflow before calling

---

🔥 Now you have a simple backend API using n8n and Google Sheets!
