# Chess Explainer Project

AI agent built with Google ADK (Agent Development Kit) for chess explanations and assistance.

## Project Overview

- **Framework**: Google ADK 1.20.0
- **Model**: Google Gemini 2.5 Flash via OpenRouter
- **Language**: Python 3.x
- **Purpose**: Chess-related assistance (currently example agent with time-telling functionality)

## Environment Setup

### Virtual Environment
- **Location**: `.venv/`
- **Activation Commands**:
  - Windows Command Prompt: `.venv\Scripts\activate.bat`
  - Windows PowerShell: `.venv\Scripts\Activate.ps1`
  - Git Bash/WSL: `source .venv/Scripts/activate`
- **Verification**: Look for `(.venv)` prefix in prompt

### API Keys Configuration
- **Location**: `my_agent/.env` (NEVER commit this file!)
- **Required Keys**:
  - `OPENROUTER_API_KEY`: OpenRouter API key for LiteLLM
  - `GOOGLE_API_KEY`: Google API key (if using Google AI directly)
  - `GOOGLE_GENAI_USE_VERTEXAI`: Set to 0
- **Template**: See `.env.example` for structure

## Running the Agent

All commands run from the **project root directory** with virtual environment activated:

```bash
# Interactive CLI mode
adk run my_agent

# Web interface on port 8080
adk web --port 8080
```

## Project Structure

```
chess-explainer/
├── .venv/              # Virtual environment (gitignored)
├── .idea/              # IDE settings (gitignored)
├── .claude/            # Claude Code configuration (gitignored)
├── my_agent/           # Agent implementation
│   ├── agent.py        # Main agent code with root_agent definition
│   ├── __init__.py     # Package initialization
│   ├── .env            # Environment variables (gitignored)
│   └── .adk/           # ADK session data (gitignored)
├── .gitignore          # Git exclusions
├── .env.example        # Template for environment variables
├── CLAUDE.md           # This file - project memory
└── README.md           # User documentation
```

## Development Guidelines

### Agent Configuration
- Agent definition: `my_agent/agent.py` exports `root_agent`
- API keys loaded via `os.getenv()` from `.env` file
- Tools defined as Python functions passed to agent

### Security
- **CRITICAL**: Never commit `.env` files or hardcode API keys
- API keys must be loaded from environment variables
- `.gitignore` protects sensitive files

### Git Workflow
- **Repository**: git@github.com:danielh1307/chess-explainer.git
- **Branch**: master
- **SSH Key**: Located at `~/.ssh/id_ed25519`
- Standard workflow: stage → commit → push

## Common Commands

### ADK Commands
```bash
adk --help              # View ADK help
adk list                # List available agents
adk run my_agent        # Run agent in CLI mode
adk web --port 8080     # Run agent web interface
```

### Python/Pip
```bash
pip list                # List installed packages
pip install <package>   # Install new package
```

### Git
```bash
git status              # Check repository status
git add <files>         # Stage files
git commit -m "msg"     # Commit changes
git push                # Push to remote
```

## Important Notes

1. **Always activate virtual environment** before running any Python or ADK commands
2. **API keys are in `my_agent/.env`** - this file is gitignored for security
3. **Agent runs from project root**, not from `my_agent/` directory
4. **Port 8080** is the default for web interface, but can be changed with `--port` flag
5. **SSH authentication** configured for GitHub pushes

## Future Development

- Transform from example time-telling agent to chess-specific functionality
- Add chess-related tools (move validation, position analysis, etc.)
- Update agent description and instructions for chess domain
