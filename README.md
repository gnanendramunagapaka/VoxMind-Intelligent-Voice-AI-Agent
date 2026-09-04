# VoxMind-Intelligent-Voice-AI-Agent
A real-time voice AI assistant that listens, understands, reasons, uses tools when needed, and responds naturally with speech.
# 🎙️ VoxMind — Voice AI Agent

> An end-to-end Voice AI Agent that listens to human speech, converts it into text, understands the request using an LLM, intelligently uses tools when required, and responds with synthesized speech.

---

## 📌 Overview

**VoxMind** is a Python-based Voice AI Agent that combines multiple AI components into a single conversational pipeline.

The project demonstrates how speech recognition, Large Language Models, tool calling, and text-to-speech can work together to create a voice-based AI assistant.

The complete pipeline is:

```text
🎤 Microphone
     ↓
📝 Speech-to-Text
     ↓
🧠 LLM Reasoning
     ↓
🔧 Tool Calling (when required)
     ↓
💬 Final Response
     ↓
🔊 Text-to-Speech
     ↓
🎧 Voice Output
✨ Features
🎤 Voice input through microphone
📝 Speech-to-Text using Faster Whisper
🧠 LLM-based reasoning
🔧 Tool calling
⏰ Current time tool
🧮 Calculator tool
🔊 Text-to-Speech using Piper
💻 CPU support
⚡ GPU support when a compatible CUDA environment is available
🔄 End-to-end voice interaction
📓 Google Colab compatible
🧠 How It Works
1. 🎤 Microphone Input

The user speaks into a microphone.

For example:

"What time is it?"

The recorded audio is saved as an audio file and passed to the Speech-to-Text component.

2. 📝 Speech-to-Text

VoxMind uses Faster Whisper to convert the recorded speech into text.

🎤 Audio
   ↓
Faster Whisper
   ↓
"What time is it?"

Faster Whisper is based on the Whisper speech recognition model and provides efficient inference using CTranslate2.

3. 🧠 LLM Reasoning

The transcribed text is sent to the Large Language Model.

The LLM determines what the user wants and decides whether the request can be answered directly or requires a tool.

For example:

User:
What is 25 × 8?

LLM:
200

The LLM can handle simple calculations itself.

However:

User:
What time is it right now?

LLM:
Use the get_current_time tool.

This allows the agent to use tools only when they are actually useful.

🔧 Tool Calling

VoxMind demonstrates tool calling using Python functions.

⏰ Current Time

The get_current_time() tool returns the current system time.

def get_current_time():
    return datetime.now().strftime("%I:%M %p")

Example:

User:
What time is it?

LLM:
Tool required → get_current_time()

Tool:
03:25 PM

Agent:
The current time is 03:25 PM.
🧮 Calculator

The calculator tool can perform mathematical expressions.

def calculate(expression):
    ...

Example:

User:
Calculate 125 × 48

Tool:
6000

However, simple calculations such as:

25 × 8

can be answered directly by the LLM without necessarily calling the calculator.

🔄 Agent Decision Process

The important concept in VoxMind is intelligent tool selection.

The agent follows this basic decision process:

              User Request
                   │
                   ▼
              🧠 LLM
                   │
          Can LLM answer directly?
             /            \
           Yes             No
            │               │
            ▼               ▼
       Direct Answer     🔧 Tool
                            │
                            ▼
                       Tool Result
                            │
                            ▼
                       Final Answer

The purpose of tool calling is not to use a tool for every request.

Tools are useful when the agent needs:

Real-time information
External data
Deterministic computation
Access to another service
An external action
🔊 Text-to-Speech

After generating the final response, VoxMind uses Piper TTS to convert the response text into speech.

💬 Text Response
       ↓
     Piper
       ↓
   response.wav
       ↓
🔊 Audio Playback

This completes the voice-to-voice interaction.

🛠️ Technology Stack
Component	Technology
Programming Language	Python
Speech-to-Text	Faster Whisper
LLM	Qwen2.5-1.5B-Instruct
Tool Calling	Python Functions
Text-to-Speech	Piper TTS
Audio Processing	SciPy
GPU Acceleration	CUDA
Development Environment	Google Colab
