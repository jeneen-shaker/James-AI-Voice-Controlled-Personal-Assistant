# James-AI-Voice-Controlled-Personal-Assistant

Overview
James is a high-performance, voice-activated personal assistant built to handle complex scheduling and real-time information retrieval. By combining ElevenLabs for conversational voice AI with n8n for backend orchestration, James can manage your Google Calendar nd search the web.

# Core Functionalities
Voice-First Interaction: Integrated with ElevenLabs to provide a seamless, low-latency voice experience.

Intelligent Routing: Uses a central AI Agent Router in n8n to delegate tasks to specialized "Mini Agents" (Calendar & Search).

Live Web Intelligence: Real-time information retrieval via Tavily Search API.

Calendar Management: Capable of creating, updating, deleting, and retrieving Google Calendar events autonomously.

# Technical Architecture
The system follows a modular "Tool-Calling" pattern:

Voice Trigger: User speaks to the ElevenLabs Agent.

Webhook Delivery: ElevenLabs sends structured JSON data (intent + parameters) to an n8n Webhook.

Agent Logic: The n8n AI Agent analyzes the request and decides which sub-tool to call (e.g., Google Calendar nodes).

Response: The result is sent back to the user via the "Respond to Webhook" node to be spoken by James.

# Engineering Highlights: Solving Data Mismatches
During development, I optimized the system to handle strict API requirements:

Data Type Synchronization: Resolved issues where APIs expected specific formats (like Arrays) while receiving Strings by implementing strict LLM Prompting and custom JS mapping.

Contextual Memory: Integrated Simple Memory nodes to allow James to remember previous parts of the conversation for follow-up questions.

# Tech Stack
Orchestration: n8n (Self-hosted/Cloud).

Voice AI: ElevenLabs (Conversational AI).

LLM: OpenAI GPT-4o.

Tools: Google Calendar API and Tavily Search.
