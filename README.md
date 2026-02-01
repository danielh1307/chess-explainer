# Chess Explainer Agent

An AI agent built with Google ADK (Agent Development Kit) for explaining chess concepts and providing chess-related assistance.

## Prerequisites

- Python 3.8 or higher
- Virtual environment already created in `.venv`
- Google ADK installed (included in virtual environment)

## Initial Setup

### 1. Configure Environment Variables

Copy the example environment file and add your API keys:

```bash
cp .env.example my_agent/.env
```

Then edit `my_agent/.env` and add your actual API keys:
- `GOOGLE_API_KEY`: Your Google API key (if using Google AI)
- `OPENROUTER_API_KEY`: Your OpenRouter API key (required for the current model)

**IMPORTANT:** Never commit your `.env` file to version control. It's already in `.gitignore`.

## Getting Started

### 1. Activate the Virtual Environment

The activation command depends on your shell:

#### Windows Command Prompt (cmd)
```bash
.venv\Scripts\activate.bat
```

#### Windows PowerShell
```bash
.venv\Scripts\Activate.ps1
```

**Note:** If you encounter an execution policy error in PowerShell, run this command first:
```powershell
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
```

#### Git Bash / WSL / Linux / macOS
```bash
source .venv/Scripts/activate
```

### 2. Verify Activation

Once activated, you should see `(.venv)` at the beginning of your command prompt:
```
(.venv) C:\Users\hammd\IdeaProjects\chess-explainer>
```

### 3. Start the Agent

From the **root directory** of the project, you can start the agent in two ways:

#### Option 1: Interactive CLI Mode
```bash
adk run my_agent
```

This starts an interactive command-line chat session with the agent.

#### Option 2: Web Interface
```bash
adk web --port 8080
```

This starts a web server on port 8080. Access the agent by opening your browser to:
```
http://localhost:8080
```

## Project Structure

```
chess-explainer/
├── .venv/              # Python virtual environment
├── my_agent/           # Agent implementation
│   ├── agent.py        # Main agent code
│   ├── __init__.py     # Package initialization
│   ├── .env            # Environment variables
│   └── .adk/           # ADK configuration and data
├── claude_code.py      # Test file
└── README.md           # This file
```

## Agent Configuration

The agent is configured in `my_agent/agent.py` and uses:
- **Model:** Google Gemini 2.5 Flash via OpenRouter
- **Framework:** Google ADK (Agent Development Kit)
- **Tools:** Custom function tools for agent capabilities

## Environment Variables

Environment configuration is stored in `my_agent/.env`:
- `GOOGLE_GENAI_USE_VERTEXAI`: Set to 0 (not using Vertex AI)
- `GOOGLE_API_KEY`: Your Google API key
- `OPENROUTER_API_KEY`: Your OpenRouter API key for accessing models via OpenRouter

**Security Note:** The `.env` file is excluded from git via `.gitignore`. Use `.env.example` as a template.

## Deactivating the Virtual Environment

When you're done working with the agent, deactivate the virtual environment:
```bash
deactivate
```

## Troubleshooting

### Virtual Environment Not Found
If the virtual environment doesn't exist, create it:
```bash
python -m venv .venv
.venv\Scripts\activate.bat  # Windows
pip install -r requirements.txt  # If requirements file exists
```

### ADK Command Not Found
Make sure:
1. The virtual environment is activated
2. Google ADK is installed: `pip install google-adk`

### Port Already in Use
If port 8080 is already in use, specify a different port:
```bash
adk web --port 8081
```

## Additional ADK Commands

```bash
# View ADK help
adk --help

# View specific command help
adk run --help
adk web --help

# List available agents
adk list
```

## Development

To modify the agent behavior, edit `my_agent/agent.py`. The main agent is defined as `root_agent` and includes:
- Agent name and description
- LLM model configuration
- Instructions for agent behavior
- Tools and functions available to the agent

## License

[Add your license information here]

## Contact

[Add your contact information here]
