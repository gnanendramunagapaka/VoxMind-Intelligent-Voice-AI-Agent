# 🎙️ VoxMind — Intelligent Voice AI Agent

<div align="center">

[![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen.svg)]()

*A real-time voice AI assistant that listens, understands, reasons, uses tools when needed, and responds naturally with speech.*

</div>

---

## 📋 Table of Contents

- [Overview](#-overview)
- [Features](#-features)
- [How It Works](#-how-it-works)
- [Architecture](#-architecture)
- [Technology Stack](#-technology-stack)
- [Installation](#-installation)
- [Quick Start](#-quick-start)
- [Usage](#-usage)
- [Tool Capabilities](#-tool-capabilities)
- [Contributing](#-contributing)
- [License](#-license)

---

## 📌 Overview

**VoxMind** is an end-to-end Python-based Voice AI Agent that combines multiple AI components into a single conversational pipeline:

1. **Listens** to human speech through microphone input
2. **Converts** speech to text using advanced speech recognition
3. **Understands** user intent using a Large Language Model
4. **Reasons** about whether tools are needed
5. **Acts** by calling relevant tools when necessary
6. **Responds** with synthesized natural-sounding speech

Perfect for building voice-based AI assistants, voice interfaces, and conversational AI applications.

---

## ✨ Features

- 🎤 **Real-time Voice Input** — Stream audio from microphone
- 📝 **Advanced Speech-to-Text** — Faster Whisper for accurate transcription
- 🧠 **LLM-Powered Reasoning** — Qwen2.5-1.5B for intelligent responses
- 🔧 **Intelligent Tool Calling** — Uses tools only when needed
- ⏰ **Built-in Tools** — Current time, calculator, and extensible framework
- 🔊 **Natural Text-to-Speech** — Piper TTS with multiple voices
- ⚡ **GPU Acceleration** — CUDA support for faster inference
- 💻 **CPU Compatible** — Works on systems without GPU
- 🎓 **Google Colab Ready** — Run in cloud without setup
- 🔄 **End-to-End Pipeline** — Complete voice-to-voice interaction

---

## 🧠 How It Works

### Complete Pipeline

```
🎤 Microphone Input
      ↓
📝 Speech-to-Text (Faster Whisper)
      ↓
🧠 LLM Processing (Qwen2.5)
      ↓
🔧 Tool Calling (if needed)
      ↓
💬 Response Generation
      ↓
🔊 Text-to-Speech (Piper)
      ↓
🎧 Voice Output
```

### Step-by-Step Breakdown

#### 1️⃣ **Microphone Input**

User speaks into the microphone:
```
"What time is it?"
```

The audio is captured and passed to the Speech-to-Text component.

#### 2️⃣ **Speech-to-Text Processing**

VoxMind uses **Faster Whisper** (CTranslate2-based) for efficient speech recognition:

```
🎤 Audio Stream
      ↓
Faster Whisper Model
      ↓
"What time is it?"
```

**Why Faster Whisper?** Provides 2-4x faster inference than standard Whisper while maintaining accuracy.

#### 3️⃣ **LLM Reasoning**

The transcribed text is processed by the LLM to understand intent:

**Example 1: Direct Answer**
```
User: "What is 25 × 8?"
LLM: "200" (calculated internally)
```

**Example 2: Tool Required**
```
User: "What time is it right now?"
LLM: "I need to use the get_current_time tool"
```

The LLM intelligently decides whether a tool call is necessary.

#### 4️⃣ **Tool Calling**

VoxMind demonstrates extensible tool calling with Python functions.

**Available Tools:**

| Tool | Purpose | Example |
|------|---------|---------|
| `get_current_time()` | Returns current system time | "What time is it?" → 03:25 PM |
| `calculate(expression)` | Performs mathematical operations | "Calculate 125 × 48" → 6000 |

**Key Principle:** Tools are used only when necessary, not for every request.

#### 5️⃣ **Text-to-Speech**

The final response is converted to natural-sounding speech using **Piper TTS**:

```
💬 Text Response
      ↓
Piper TTS
      ↓
response.wav
      ↓
🔊 Audio Playback
```

---

## 🏗️ Architecture

### Agent Decision Flow

```
              User Request (Voice)
                      │
                      ▼
            📝 Speech-to-Text
                      │
                      ▼
            🧠 LLM Understanding
                      │
         Can Answer Directly?
            /                \
          Yes                No
           │                 │
           ▼                 ▼
        Direct Response   🔧 Tool Call
           │                 │
           └─────────┬────────┘
                     ▼
            💬 Generate Response
                     │
                     ▼
            🔊 Text-to-Speech
                     │
                     ▼
            🎧 Voice Output
```

---

## 🛠️ Technology Stack

| Component | Technology | Version |
|-----------|-----------|---------|
| **Language** | Python | 3.8+ |
| **Speech-to-Text** | Faster Whisper | Latest |
| **LLM** | Qwen2.5-1.5B-Instruct | - |
| **Tool Calling** | Python Functions | - |
| **Text-to-Speech** | Piper TTS | Latest |
| **Audio Processing** | SciPy | - |
| **GPU Support** | CUDA | 11.8+ (Optional) |
| **Cloud Ready** | Google Colab | ✓ |

---

## 📦 Installation

### Prerequisites

- Python 3.8 or higher
- pip or conda
- (Optional) CUDA-capable GPU for faster inference

### Step 1: Clone the Repository

```bash
git clone https://github.com/gnanendramunagapaka/VoxMind-Intelligent-Voice-AI-Agent.git
cd VoxMind-Intelligent-Voice-AI-Agent
```

### Step 2: Create Virtual Environment

```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

### Step 3: Install Dependencies

```bash
pip install -r requirements.txt
```

### Step 4: Download Models (Optional)

For faster startup, pre-download models:

```bash
python -c "from faster_whisper import WhisperModel; WhisperModel('base')"
```

---

## 🚀 Quick Start

### Basic Usage

```python
from voxmind import VoiceAgent

# Initialize the agent
agent = VoiceAgent(model_name="qwen2.5-1.5b")

# Start voice interaction
agent.run()
```

### Interactive Session

```bash
python main.py
```

The agent will:
1. Activate your microphone
2. Listen for your voice command
3. Process your request
4. Respond with synthesized speech

**Try these commands:**
- "What time is it?"
- "Calculate 125 times 48"
- "What is the capital of France?"
- "Tell me a joke"

---

## 💻 Usage

### Command Line Interface

```bash
# Run with default settings
python main.py

# Run with specific voice
python main.py --voice en_US-male

# Run with GPU acceleration
python main.py --gpu

# Run with custom model
python main.py --model qwen2.5-7b
```

### Python API

```python
from voxmind import VoiceAgent, ToolRegistry

# Create agent
agent = VoiceAgent()

# Register custom tools
registry = ToolRegistry()
registry.register("get_weather", get_weather_function)
agent.set_tools(registry)

# Run single interaction
response = agent.process_voice_input()
print(response)
```

---

## 🔧 Tool Capabilities

### Built-in Tools

#### ⏰ Current Time Tool
```python
def get_current_time():
    """Returns the current system time"""
    return datetime.now().strftime("%I:%M %p")
```

**Usage:** "What time is it?"

#### 🧮 Calculator Tool
```python
def calculate(expression: str) -> str:
    """Evaluates mathematical expressions"""
    return eval(expression)
```

**Usage:** "Calculate 2^10 + 50"

### Extending with Custom Tools

```python
def get_weather(location: str) -> str:
    """Get weather for a location"""
    # Your implementation
    return weather_data

# Register the tool
agent.register_tool("get_weather", get_weather)
```

---

## 📊 Performance

### Benchmarks (on CPU)

| Operation | Time |
|-----------|------|
| Speech-to-Text (5s audio) | ~2-3 seconds |
| LLM Processing | ~1-2 seconds |
| Tool Execution | <100ms |
| Text-to-Speech (10s output) | ~2-3 seconds |
| **Total E2E** | ~5-8 seconds |

### GPU Acceleration

With CUDA-capable GPU:
- **2-3x faster** inference
- Real-time audio streaming
- Lower latency for interactive use

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### Areas for Contribution

- 🔧 New tool implementations
- 🗣️ Additional language support
- 🎤 Microphone input improvements
- 📚 Documentation enhancements
- 🐛 Bug fixes and optimizations

---

## 📝 Example Interactions

### Example 1: Simple Question
```
User: "What time is it?"
Agent: (using get_current_time tool)
Response: "The current time is 3:25 PM"
```

### Example 2: Calculation
```
User: "Calculate 125 times 48"
Agent: (using calculator tool)
Response: "125 times 48 equals 6000"
```

### Example 3: General Knowledge
```
User: "What is the capital of France?"
Agent: (LLM knows this)
Response: "The capital of France is Paris"
```

---

## 📚 Documentation

For detailed documentation, see:
- [Architecture Guide](docs/ARCHITECTURE.md)
- [API Reference](docs/API.md)
- [Tool Development](docs/TOOLS.md)
- [Troubleshooting](docs/TROUBLESHOOTING.md)

---

## 🐛 Troubleshooting

### Microphone Not Detected
```bash
python -c "import pyaudio; print(pyaudio.PyAudio().get_device_count())"
```

### CUDA Issues
```bash
pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu118
```

### Model Download Issues
```bash
# Clear cache and retry
rm -rf ~/.cache/huggingface
python main.py --download-models
```

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **Faster Whisper** — OpenAI Whisper via CTranslate2
- **Qwen2.5** — Alibaba Cloud's LLM
- **Piper TTS** — Mozilla's Text-to-Speech
- **PyAudio** — Cross-platform audio I/O

---

## 📞 Support & Contact

- 📧 **Email:** [gnanendramunagapaka@gmail.com]
- 🐛 **Issues:** [GitHub Issues](https://github.com/gnanendramunagapaka/VoxMind-Intelligent-Voice-AI-Agent/issues)
- 💬 **Discussions:** [GitHub Discussions](https://github.com/gnanendramunagapaka/VoxMind-Intelligent-Voice-AI-Agent/discussions)

---

<div align="center">

⭐ **If you find VoxMind helpful, please consider giving it a star!** ⭐

Made with ❤️ by [gnanendramunagapaka](https://github.com/gnanendramunagapaka)

</div>
