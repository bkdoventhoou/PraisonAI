# PraisonAI

> A fork of [MervinPraison/PraisonAI](https://github.com/MervinPraison/PraisonAI) — Multi-Agent AI Framework

[![GitHub Stars](https://img.shields.io/github/stars/MervinPraison/PraisonAI?style=social)](https://github.com/MervinPraison/PraisonAI)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Python 3.10+](https://img.shields.io/badge/python-3.10+-blue.svg)](https://www.python.org/downloads/)

PraisonAI is a production-ready multi-agent AI framework that enables you to build, orchestrate, and deploy AI agents with minimal code. It supports multiple LLM providers and integrates seamlessly with tools like AutoGen and CrewAI.

> **Personal fork note:** I'm using this primarily with Ollama for local model experimentation. See my notes in [`NOTES.md`](NOTES.md) for setup tips.

## Features

- 🤖 **Multi-Agent Orchestration** — Coordinate multiple AI agents to solve complex tasks
- 🔧 **Tool Integration** — Equip agents with web search, code execution, file I/O, and more
- 🌐 **Multi-LLM Support** — OpenAI, Anthropic, Google Gemini, Ollama, and others
- 📋 **YAML-Based Config** — Define agent workflows declaratively
- 🖥️ **UI Included** — Built-in chat and workflow UI
- 🔄 **AutoGen & CrewAI** — Optional integration with popular agent frameworks

## Quick Start

### Installation

```bash
pip install praisonai
```

For all optional dependencies:

```bash
pip install "praisonai[all]"
```

### Set Up Environment

```bash
cp .env.example .env
# Edit .env and add your API keys
```

### Run Your First Agent

```bash
# Interactive chat
praisonai chat

# Run with a YAML config
praisonai --config agents.yaml

# Auto-generate agents from a task description
praisonai --auto "Research the latest AI trends and write a report"
```

## Example Agent Config

```yaml
# agents.yaml
framework: praisonai
topic: Research AI trends
roles:
  researcher:
    role: Research Analyst
    goal: Find and summarize the latest AI developments
    backstory: You are an expert AI researcher with deep knowledge of the field.
    tasks:
      research_task:
        description: Research the top 5 AI trends of 2024
        expected_output: A detailed report with sources
    tools:
      - internet_search
      - read_file
```

## Environment Variables

See [`.env.example`](.env.example) for all supported configuration options.

Key variables:

| Variable | Description |
|---|---|
| `OPENAI_API_KEY` | OpenAI API key |
| `ANTHROPIC_API_KEY` | Anthropic (Claude) API key |
| `GOOGLE_API_KEY` | Google Gemini API key |
| `OPENAI_MODEL_NAME` | Default model (e.g. `gpt-4o`) |
| `OLLAMA_HOST` | Ollama server URL (default: `http://localhost:11434`) |

> **My Ollama setup:** I run Ollama on a separate machine on my LAN, so I set `OLLAMA_HOST=http://192.168.1.50:11434` in my `.env`. Works great with `llama3` and `mistral` for most agent tasks.

## Documentation

Full documentation is available at [docs.praison.ai](https://docs.praison.ai).

## Contributing

Contributions are welcome! Please open an issue or pull request.

1. Fork the repository
2. Create your feature branch (`git checkout -b feat/my-feature`)
3. Commit your changes (`git commit -m 'Add some feature'`)
4. Push to the branch (`git push origin feat/my-feature`)
5. Open a Pull Request
