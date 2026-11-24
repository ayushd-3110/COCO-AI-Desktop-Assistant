# Coco AI Desktop Assistant

A Python desktop voice assistant with the original PyQt5 interface, conversational AI, web search, speech input/output, image generation and desktop automation.

## Architecture

| Component | Responsibility |
| --- | --- |
| Main.py | Application lifecycle and request orchestration |
| Frontend/GUI.py | Original PyQt5 interface and status display |
| Backend/Model.py | Cohere intent classification |
| Backend/Chatbot.py | Groq conversation and chat history |
| Backend/RealtimeSearchEngine.py | Search excerpts and AI summaries |
| Backend/SpeechToText.py | Chrome speech recognition via Selenium |
| Backend/TextToSpeech.py | Edge TTS and audio playback |
| Backend/Automation.py | Applications, search and content writing |
| Backend/ImageGeneration.py | Configurable image inference provider |

## Installation (Windows)

Install Python 3.10+ and Google Chrome. Open PowerShell inside the folder containing `Main.py` and `Requirements.txt`.

```powershell
python -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r Requirements.txt
Copy-Item .env.example .env
notepad .env
```

Add your own Groq, Cohere and Hugging Face credentials as needed, select model IDs supported by your accounts and set a compatible image inference endpoint. Keep `.env` private. Allow Chrome microphone access for voice requests. Internet access is required for online features.

```powershell
.\.venv\Scripts\python.exe Main.py
```

## Usage

Use the original microphone control, speak a question, and view or listen to the response. Examples: “Explain cloud computing”, “Open Notepad”, “Search YouTube for Python tutorials”, and “Generate image of a mountain landscape”. Availability depends on the classifier and providers. Reminders are classified but not implemented.

## Bug fixes

- Preserved original UI assets; fixed empty startup chat and queries.
- Delayed API clients and Chrome startup; removed unsolicited browser search.
- Removed recursive retries and prevented deletion of chat history on failed requests.
- Added speech recognition timeout and removed fake microphone input.
- Used current Python interpreter for image subprocesses, handled commas in prompts and sanitized filenames.
- Configured provider model IDs and image endpoint; added network timeouts for chat and images.
- Excluded credentials, virtual environments, caches and private runtime data.

## Verification and limitations

Run `python -m compileall -q Main.py Backend Frontend calender.py` for syntax verification. External providers, graphical rendering, microphone/audio access and application automation require live testing on a configured Windows machine. This release does not claim full end-to-end validation. Close applications only after saving work. Voice queries and chat requests may be sent to third-party services.
