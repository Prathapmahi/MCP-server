# 🧠 MCP Server Project - Multi-Agent AI Tools

This project demonstrates how to build and serve multiple AI tools using the **FastMCP** framework. It includes a combination of COM-based email automation, external API integration (OpenWeather), local file-based notes, and utility functions—all accessible via an MCP-compatible agent interface.

-----------------------------------------------------------------------------------------------------

## 🔧 Requirements

- Python 3.10+
- Windows (required for Outlook COM)
- `.env` file with:
  ```env
  OPENWEATHER_API_KEY=your_openweather_key_here
  ```

-----------------------------------------------------------------------------------------------------

## 📁 Directory Structure

.
├── outlook_assistant.py        # Outlook email read/reply/compose/search tools
├── weather_mcp.py              # Current, forecast, historical, and air quality weather tools
├── sticky_notes.py             # Notes tools backed by a text file
├── addition_server.py          # Simple addition and greeting tool
├── notes.txt                   # File to store sticky notes
└── README.md                   # This file

-----------------------------------------------------------------------------------------------------

## 📬 Outlook Email Assistant

A COM-based email assistant that integrates with Microsoft Outlook to:

- List all folders in Outlook
- Fetch and display recent or matching emails
- Read full email contents
- Send replies or compose new emails

### 🔧 Tools Exposed:

- `list_folders()`
- `list_recent_emails(days, folder_name)`
- `search_emails(search_term, days, folder_name)`
- `get_email_by_number(email_number)`
- `reply_to_email_by_number(email_number, reply_text)`
- `compose_email(recipient_email, subject, body, cc_email)`

> ⚠️ Must be run on **Windows** with Microsoft Outlook installed.

-----------------------------------------------------------------------------------------------------

## 🌍 Weather Tools (OpenWeather API)

Provides weather details using OpenWeatherMap API including:

- Current weather
- 5-day forecast
- Air quality
- Weather alerts
- Historical weather (past 5 days)

### 🌦 Tools Exposed:

- `get_current_weather(location)`
- `get_weather_forecast(location, days)`
- `get_air_quality(location)`
- `get_historical_weather(location, date)`
- `get_weather_alerts(location)`
- `search_location(query)`

> 🌐 Requires setting `OPENWEATHER_API_KEY` in `.env`

-----------------------------------------------------------------------------------------------------

## 📝 AI Sticky Notes

Simple note-taking assistant that stores notes locally in a `notes.txt` file.

### 🛠 Tools and Resources:

- `add_note(message)`
- `read_notes()`
- `get_latest_note()` – as resource `notes://latest`
- `note_summary_prompt()` – generates a summarization prompt from all notes

-----------------------------------------------------------------------------------------------------

## ➕ Addition Utility

Example of a simple arithmetic and dynamic greeting tool using MCP:

- `add(a, b)`
- `get_greeting(name)` → resource `greeting://{name}`

-----------------------------------------------------------------------------------------------------

## 🏁 Running Any MCP Server

Each file defines its own FastMCP server. Run them individually:

python outlook_assistant.py
python weather_mcp.py
python sticky_notes.py
python addition_server.py

> Each server will start on its own FastMCP interface for integration with agents.

---

## 🧪 Example Agents

You can now connect these MCP tools with agents (CrewAI, LangChain, etc.) to enable conversational workflows like:

- "What’s the weather in London today?"
- "Summarize my latest sticky notes"
- "Reply to the last unread email from Ajay"
- "What is 42 + 11?"