# 🤖 Smart AI Assistant — Multi-Agent Automation System

> A powerful **agentic AI system** built with **n8n** where a central Smart AI Assistant orchestrates 6 specialized sub-agents — handling emails, contacts, calendar, finances, research, and travel planning through natural conversation.

---

## 🧠 How It Works

```
User Message
     │
     ▼
┌─────────────────────┐
│  Smart AI Assistant  │  ← Master Orchestrator
│  (Central Brain)     │
└─────────┬───────────┘
          │  Routes tasks to specialized agents
    ┌─────┼──────────────────────────────┐
    ▼     ▼        ▼      ▼      ▼      ▼
 Email  Contact  Calendar Finance Research Travel
 Agent   Agent    Agent   Analyst Assistant Planner
```

The **Smart AI Assistant** receives the user's request, understands the intent, and autonomously delegates to the right sub-agent.

---

## 🚀 Tech Stack

| Layer | Technology |
|---|---|
| **AI Orchestration** | [n8n](https://n8n.io/) (Multi-Agent Workflow) |
| **LLM** | Google Gemini (PaLM API) |
| **Email** | Gmail API (OAuth2) |
| **Calendar** | Google Calendar API |
| **Contacts** | Google Contacts API |
| **Finance Data** | Google Sheets |
| **Research** | Web Search Tools |

---

## 🗂️ Project Structure

```
smart-ai-assistant/
├── Smart AI Assistant.json     # Master orchestrator — import this FIRST
├── Email Agent.json            # Handles read/write/reply emails
├── Contact Agent.json          # Manages contacts (add/update/lookup)
├── Calendar Agent (1).json     # Creates/updates/deletes calendar events
├── Financial Analyst.json      # Reads balance sheet & sends analysis via email
├── Research Assistant.json     # Researches topics & emails the summary
└── Travel Planner.json         # Generates day-by-day travel itineraries
```

---

## 🤖 Agent Capabilities

### 🧠 Smart AI Assistant (Master)
- Central brain that understands user intent
- Autonomously routes tasks to the correct sub-agent
- Connects all 6 sub-agents as tools

### 📧 Email Agent
- Read, compose, send, and reply to emails
- Handles error recovery with retry logic

### 👤 Contact Agent
- Look up existing contacts
- Add new contacts or update existing ones
- Fields: name, email, phone, company

### 📅 Calendar Agent
- Create solo or multi-attendee events
- Fetch upcoming schedule
- Update or delete events by ID
- Time-aware (uses current date/time automatically)

### 💰 Financial Analyst
- Reads your Google Sheets balance sheet
- Generates financial analysis
- Sends the report directly to your Gmail

### 🔬 Research Assistant
- Takes a topic via n8n form
- Researches using web tools
- Emails a clean summary report

### ✈️ Travel Planner
- Takes destination + travel dates via n8n form
- Generates a full day-by-day HTML itinerary
- Includes morning/afternoon/evening activities, food, and tips
- Emails the plan directly

---

## ⚙️ Setup & Import Instructions

### Step 1 — Import Sub-Agents First

Import these workflows into n8n **in this order**:
1. `Email Agent.json`
2. `Contact Agent.json`
3. `Calendar Agent (1).json`
4. `Financial Analyst.json`
5. `Research Assistant.json`
6. `Travel Planner.json`

> Go to **n8n → Workflows → Import from File** for each one.

### Step 2 — Import the Master

7. Import `Smart AI Assistant.json` last

### Step 3 — Add Credentials

Connect your accounts in n8n for each agent:
- ✅ **Google Gemini API** — for all AI agents
- ✅ **Gmail OAuth2** — for Email Agent, Financial Analyst, Research Assistant, Travel Planner
- ✅ **Google Calendar OAuth2** — for Calendar Agent
- ✅ **Google Contacts OAuth2** — for Contact Agent
- ✅ **Google Sheets OAuth2** — for Financial Analyst

### Step 4 — Activate All Workflows

Activate each sub-agent workflow, then activate the Smart AI Assistant last.

---

## 🔐 Credentials Required

| Agent | Service | Auth Type |
|---|---|---|
| All AI nodes | Google Gemini | API Key |
| Email Agent | Gmail | OAuth2 |
| Calendar Agent | Google Calendar | OAuth2 |
| Contact Agent | Google Contacts | OAuth2 |
| Financial Analyst | Google Sheets + Gmail | OAuth2 |
| Research Assistant | Gmail | OAuth2 |
| Travel Planner | Gmail | OAuth2 |

> ⚠️ Never share your API keys or OAuth tokens publicly.

---

## 🛠️ Built By

**NWL Studioz** — AI Creator & Brand Solutions Studio
*Agentic AI · Automation · Web Experiences*

---

## 📄 License

MIT License — free to fork, customize, and build on top of.
