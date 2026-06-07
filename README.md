# 📅Smart-slot-bot
An automated, AI-powered scheduling and calendar management assistant built using **n8n**. This workflow connects a Telegram bot interface to an advanced LangChain AI Agent powered by Google Gemini, using Google Calendar as the scheduling backend to create, search, and manage events through natural language.

## 🚀 Features
- **Conversational Scheduling:** Users can book, look up, or manage appointments simply by chatting with a Telegram bot.
- **Smart Event Creation:** Automatically extracts dates, times, and event titles from casual chat text to generate formal calendar invitations.
- **Live Calendar Search:** The AI Agent dynamically queries an integrated Google Calendar to list existing events and prevent scheduling conflicts.
- **Dynamic Context Awareness:** Built-in memory allows the agent to hold multi-turn conversations, keeping track of details across multiple messages.
- **Time-Zone Intelligence:** Includes dedicated date and time utilities so the agent precisely understands relative time expressions (e.g., "tomorrow at 3 PM" or "next Friday").

## 🛠️ Architecture & Nodes Used
As shown on the n8n canvas:
1. **Telegram Trigger:** Listens for incoming chat messages and text commands sent to your bot.
2. **AI Agent (LangChain):** The central orchestration node that processes customer intent and determines actions.
3. **Model (Google Gemini):** Provides advanced natural language reasoning and execution formatting.
4. **Brain (Window Buffer Memory):** Maintains conversational context for up to 10 historical interactions.
5. **Custom Tools (Google Calendar & Utilities):**
   - `Create` (Google Calendar Tool): Appends new scheduled events to your calendar.
   - `Search` (Google Calendar Tool): Retrieves and lists events matching specified filters or time ranges.
   - `Date & Time`: Provides structured timezone and mathematical date parsing to the LLM.
6. **Send a text message (Telegram):** Dispatches the finalized confirmation message back to the user's chat window.

## 📋 Prerequisites
To deploy this workflow, you will need active credentials for:
- An **n8n instance** (Self-hosted or Cloud)
- A **Telegram Bot API Token** (Generated via `@BotFather`)
- **Google Cloud Console** credentials with the Google Calendar API enabled (via OAuth2)
- A **Google AI Studio Key** (for Gemini)

## 📦 Installation & Setup
1. Clone this repository or download your `My workflow.json` file.
2. Inside your n8n dashboard, select **New Workflow** -> **Import from File** and upload the JSON configuration.
3. Configure your account credentials inside the respective nodes:
   - Telegram Receiver/Sender APIs
   - Google Gemini API account
   - Google Calendar OAuth2 API
4. Turn the workflow toggle to **Active** to start handling live events.
