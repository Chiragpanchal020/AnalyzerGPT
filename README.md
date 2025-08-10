# 🤖 Analyzer GPT - AI Data Analysis Assistant

[![Python](https://img.shields.io/badge/Python-3.11+-blue.svg)](https://www.python.org/downloads/)
[![Streamlit](https://img.shields.io/badge/Streamlit-1.28+-red.svg)](https://streamlit.io/)
[![AutoGen](https://img.shields.io/badge/AutoGen-0.4+-green.svg)](https://github.com/microsoft/autogen)
[![LLM](https://img.shields.io/badge/LLM-Multi--Provider-orange.svg)](https://huggingface.co/models)
[![Docker](https://img.shields.io/badge/Docker-Enabled-blue.svg)](https://www.docker.com/)

> **Multi-agent AI system that transforms CSV data into insights through natural language conversations.**

## 🎯 Overview

An intelligent data analysis platform using Microsoft's AutoGen framework with advanced language models. Upload CSV files, ask questions in plain English, and get automated analysis with visualizations - all executed securely in Docker containers.

## ✨ Key Features

- 🧠 **Natural Language Queries**: Ask complex data questions in plain English
- 🔒 **Secure Execution**: All code runs in isolated Docker containers
- 📊 **Auto Visualizations**: Generates charts and graphs automatically
- ⚡ **Real-time Streaming**: Live responses as analysis progresses
- 🎨 **Intuitive Interface**: Simple drag-and-drop CSV upload

## 🛠️ Tech Stack

| Component | Technology |
|-----------|------------|
| **AI Framework** | Microsoft AutoGen |
| **Language Model** | Advanced LLMs (OpenAI/Open Source) |
| **Frontend** | Streamlit |
| **Data Processing** | Pandas + Matplotlib |
| **Execution** | Docker Containers |

## �️ Architecture

```
Streamlit UI ↔ AutoGen Orchestrator ↔ Docker Executor
                      ↓
              [Data Analyzer Agent]
                      ↓
              [Code Executor Agent]
```

**Multi-Agent System:**
- **Data Analyzer**: Interprets queries, generates Python code
- **Code Executor**: Runs code safely in Docker containers

## 🎨 System Design

The system architecture and design process is documented in `analyzer gpt.excalidraw` - open with [Excalidraw](https://excalidraw.com/) to view the visual system design and architecture diagrams.

## 🚀 Quick Start

```bash
# Clone and setup
git clone https://github.com/YOUR_USERNAME/analyzer-gpt.git
cd analyzer-gpt
pip install -r requirements.txt

# Configure API key
cp .env.example .env
# Add your LLM API key to .env

# Run application
streamlit run streamlit_app.py
```

## 📊 Usage Examples

- **"Show me a summary of the sales data"** → Statistical analysis
- **"Create a correlation heatmap"** → Matplotlib visualization
- **"What trends do you see over time?"** → Time series analysis

## 🏗️ Project Structure

```
analyzer-gpt/
├── 📁 agents/                    # AI Agent Definitions
│   ├── code_executor_agent.py   # Docker-based code execution agent
│   ├── data_analyzer_agent.py   # Data analysis and query interpretation
│   └── prompts/                 # Agent prompt templates
│       └── data_analyzer_prompt.py  # System prompts for analysis agent
│
├── 📁 config/                   # Configuration Management
│   ├── constants.py             # Application constants (models, timeouts)
│   ├── docker_utils.py          # Docker executor utilities & lifecycle
│   └── model_client.py          # LLM client configuration & initialization
│
├── 📁 team/                     # Multi-Agent Orchestration
│   └── analyzer_gpt_team.py     # Team coordination & round-robin logic
│
├── 📄 streamlit_app.py          # Streamlit Web Interface
├── 📄 main.py                   # CLI Application Entry Point
├── 📄 requirements.txt          # Python Dependencies
├── 📄 Dockerfile               # Container Configuration
├── 📄 .env.example             # Environment Variables Template
├── 📄 .gitignore               # Git Ignore Rules
└── 📄 README.md                # Project Documentation
```

### 📋 **Component Details**

| Component | Purpose | Key Features |
|-----------|---------|--------------|
| **`agents/`** | Core AI logic | Specialized agents for analysis & execution |
| **`config/`** | System setup | Environment management, Docker config |
| **`team/`** | Orchestration | Multi-agent coordination & communication |
| **`streamlit_app.py`** | Web UI | File upload, chat interface, visualization |
| **`main.py`** | CLI tool | Command-line version for automation |

## 🔧 Configuration

| Variable | Description | Required |
|----------|-------------|----------|
| `OPENAI_API_KEY` | LLM API key (OpenAI/other providers) | ✅ Required |
| `DOCKER_TIMEOUT` | Execution timeout | ❌ Optional (120s) |

## 🧪 Technical Implementation

### Multi-Agent System
```python
# Round-robin collaboration between specialized agents
team = RoundRobinGroupChat(
    participants=[data_analyzer_agent, code_executor_agent],
    termination_condition=TextMentionTermination("STOP")
)
```

### Secure Execution
```python
# Isolated Docker containers for code execution
docker_executor = DockerCommandLineCodeExecutor(
    image='amancevice/pandas',
    timeout=DOCKER_TIMEOUT
)
```

### Real-time Streaming
```python
# Live response streaming
async for message in team.run_stream(task=user_query):
    display_response(message)
```

## 🚀 Deployment

### Hugging Face Spaces
```bash
# Automatic Docker deployment
git push origin main  # Auto-deploys to HF Spaces
```

### Local Development
```bash
streamlit run streamlit_app.py
```

## 🎯 Key Achievements

- ✅ **Multi-Agent AI**: AutoGen framework with advanced LLM integration
- ✅ **Secure Architecture**: Docker containerization for safe code execution
- ✅ **Real-time UX**: Async streaming responses
- ✅ **Production Ready**: Comprehensive error handling and logging

## 📄 License

MIT License - see [LICENSE](LICENSE) for details.

---

<div align="center">

**⭐ Star this repo if you found it helpful! ⭐**

*Built with cutting-edge AI technology*

</div>
