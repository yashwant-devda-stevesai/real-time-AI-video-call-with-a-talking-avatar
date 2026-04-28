# Voice Avatar Assistant

A voice-enabled educational assistant built with LiveKit Agents and Tavus Avatars. This project combines a Next.js frontend with a Python Tavus agent backend to deliver an interactive study experience using voice, flash cards, quizzes, and an avatar-driven conversational interface.

## Project structure

- `voice-assistant-frontend/` - Next.js application with LiveKit voice assistant components and UI for flash cards, quizzes, and transcriptions.
- `tavus/` - Python Tavus avatar agent, FastAPI endpoint, and LiveKit worker entrypoint.
- `tavus/requirements.txt` - Python dependencies for running the Tavus agent.

## Features

- Conversational voice assistant powered by LiveKit Agents
- Tavus avatar integration for realistic AI character interaction
- Visual flash cards and multiple-choice quizzes
- Client-side LiveKit room connection and media handling
- Transcription and session controls for microphone / audio management

## Prerequisites

- Node.js 18+ (or compatible version)
- pnpm or npm
- Python 3.11+ (recommended)
- A LiveKit deployment or LiveKit Cloud account
- A Tavus API key
- Optional ElevenLabs API key for TTS support

## Setup

### 1. Configure the frontend

```bash
cd voice-assistant-frontend
pnpm install
```

Create `voice-assistant-frontend/.env.local` with:

```env
LIVEKIT_URL=https://your-livekit-server
LIVEKIT_API_KEY=your_livekit_api_key
LIVEKIT_API_SECRET=your_livekit_api_secret
```

### 2. Configure the Tavus backend

```bash
cd ../tavus
python -m pip install -r requirements.txt
```

Create `voice-avatar-assistant/tavus/.env` with:

```env
TAVUS_API_KEY=your_tavus_api_key
ELEVENLABS_API_KEY=your_elevenlabs_api_key  # optional
```

### 3. Run the backend agent

From `voice-avatar-assistant/tavus`:

```bash
python main.py
```

This starts the FastAPI connection endpoint and the LiveKit worker for the Tavus avatar agent.

### 4. Run the frontend

From `voice-avatar-assistant/voice-assistant-frontend`:

```bash
pnpm dev
```

Then open `http://localhost:3000` in your browser.

## Usage

1. Start the application in the browser.
2. Click the connect button to join a LiveKit voice room.
3. Grant microphone permissions when prompted.
4. Speak with the avatar assistant and use the flash card / quiz UI.

## Environment variables

- `LIVEKIT_URL` - LiveKit server URL used by the frontend connection API.
- `LIVEKIT_API_KEY` - LiveKit API key for token generation.
- `LIVEKIT_API_SECRET` - LiveKit API secret for token generation.
- `TAVUS_API_KEY` - Tavus API key for avatar session creation.
- `ELEVENLABS_API_KEY` - Optional ElevenLabs key for TTS if enabled.

## Notes

- The frontend generates room connection details via `app/api/connection-details/route.ts`.
- The Tavus worker entrypoint is `tavus/main.py` and it launches the agent with `tavus/tavus_agent.py`.
- The current experience is designed as a Socratic learning assistant with flash cards and quizzes.

## Contributing

Contributions are welcome. Open an issue or submit a pull request with improvements to the UI, agent behavior, or setup documentation.
