# Site-Daily-Report-Automation-
An autonomous AI Agent built in n8n designed for engineering and construction project management. It intercepts daily site reports sent by engineers via Telegram, extracts structured project metrics using LLMs, logs them into Google Sheets, and automates instant confirmations or missing-field follow-ups.
## 🎯 Problem Solved
Collecting daily progress updates from engineers working on-site is chaotic. Reports come in unstructured formats via chat, making manual entry into operational spreadsheets or databases slow and error-prone. 

This workflow provides an intelligent communication interface:
1. **Natural Language Extraction:** Parses unstructured text updates (e.g., accomplishments, site problems, hours worked) directly from site chat channels.
2. **Autonomous Logging:** Maps and inserts the extracted data points into core spreadsheets via custom tools.
3. **Smart Follow-ups:** Features dynamic conditional loops. If an engineer misses an essential metric (like hours or project name), the agent halts insertion and prompts the engineer to provide the missing data.

---

## ⚡ Workflow Architecture
[ Engineer Reports via Telegram ]
↓
[ n8n AI Agent Executor ]
↓
🚦 Are Essential Fields Present?
├── Yes → [ Save Report to Google Sheets Tool ] → [ Send Success Ping via Telegram ]
└── No  → [ Prompt Engineer for Missing Data Tool ]


---

## 🔧 Tech Stack
| Tool | Role |
| :--- | :--- |
| **n8n Advanced AI** | Agent orchestration, tool calling framework, and runtime environment |
| **OpenAI (GPT Models)** | The processing model driving semantic entity extraction |
| **Google Sheets API** | Secure data store for all daily construction metrics |
| **Telegram Bot API** | Direct two-way communication channel for field engineers |

---

## 📋 Key Logic & Rules
* **🔎 Entity Extraction Schemas:** The agent isolates specific attributes: `engineer_name`, `project_name`, `achievement`, `problem`, `hours`, and `follow_up` directly from natural conversation logs.
* **🛑 Input Validation Guardrails:** Includes programmatic loops that evaluate inputs before appending database rows, keeping construction logs clean and complete.
* **⏰ Automations (Optional):** Supports scheduled routines to parse or aggregate daily records at set cut-off times.

---

## 🚀 Setup Instructions

### Prerequisites
* n8n instance (Self-hosted or Cloud) with **Advanced AI** nodes active.
* Google Workspace account with Google Sheets API access.
* OpenAI API Key or a compatible LLM provider.
* Telegram Bot Token generated via BotFather.

### Steps to Deploy
1.  **Import:** Download and import `Engineering_Site_Report_Agent.json` into your n8n workspace.
2.  **API Connection Setup:** Populate your custom credentials for the Telegram Trigger/Nodes, OpenAI Model, and Google Sheets connectors.
3.  **Target Spreadsheet Mapping:** Create a Google Sheet containing column headers matching the agent parameters (`Date`, `Engineer`, `Project`, `Achievement`, `Problems`, `Hours`, `Follow-up`) and bind the sheet ID in the tool parameters.
4.  **Activate:** Switch the workflow to Active. Share the bot handle with your site team, and let the automation manage data ingestion.

---

## 📁 Repository Structure
```bash
engineering-site-report-agent/
├── Engineering_Site_Report_Agent.json  # The clean n8n reporting automation file (Import this)
├── assistant-canvas-preview.png        # Visual screenshot of the parsing logic flow
└── README.md                           # Project documentation
👤 Author
Asem Ahmed — AI Automation Engineer
