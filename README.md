# ESP32LLM (Terminal Prototype)

A terminal-based prototype for a voice assistant pipeline that will later be moved to an ESP32 device.

This version uses your **laptop microphone** for input (STT), a **Groq-hosted LLM** for responses, and **Piper TTS (via Pipecat)** to generate a spoken reply that plays back locally.

---

## What this project does

**Voice → Text → LLM → Voice**

1. Records audio from your **laptop microphone** (WAV, 16kHz mono).
2. Runs **Whisper** Speech-to-Text (STT) to get a transcript.
3. Sends transcript to **Groq** (LLM) to generate a reply.
4. Runs **Piper TTS** (through **Pipecat**) to synthesize speech audio.
5. Saves `reply.wav` and plays it on macOS using `afplay`.

---

## Tech stack

- **Python**
- **Groq** (LLM via API)
- **OpenAI Whisper** (local STT)
- **Pipecat + Piper** (local TTS)
- **sounddevice + soundfile** (microphone recording)
- **ffmpeg** (required by Whisper for decoding)

---

## Project structure 


You can place the script anywhere; the important part is your virtual environment and dependencies.

---

## Requirements

### System (macOS)
- Python 3.11+ recommended  
  (Python 3.13 can work, but some async libs may be pickier.)
- `ffmpeg`
- A working microphone (macOS privacy permissions may apply)

Install ffmpeg and dependencies:

```bash
brew install ffmpeg
pip install openai-whisper sounddevice soundfile groq pipecat-ai websockets
