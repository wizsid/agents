# Agents

### 0. Quick Start (No Project Required)
If you want to use the ADK CLI globally without setting up a full project structure:
```bash
# Install the ADK CLI globally
uv tool install google-adk

# Or run the CLI without installing it
uvx google-adk --help

# Run a standalone script with the dependency injected
uv run --with google-adk python agent.py
```

### 1. System-Level Toolchain Setup
```bash
# Install uv via Homebrew
brew install uv
# Verify the installation
uv --version
```

### 2. Project Initialization & Environment Isolation
```bash
# Initialize a modern Python project
uv init agent-workspace
cd agent-workspace

# Pin your Python version (uv will fetch it automatically if it is missing from your Mac)
uv python pin 3.12

# Create the virtual environment and sync the base project
uv sync

### 3. Dependency Management
```bash
# Install the core Google ADK
uv add google-adk

# Add environment management and standard HTTP libraries
uv add python-dotenv httpx

# Add development dependencies for linting and testing
uv add --dev ruff pytest
```

### 4. Agent Directory Architecture
```bash
agent-workspace/
├── .env                  # Local secrets and API routing
├── .python-version       # Pinned version (e.g., 3.12)
├── pyproject.toml        # Declarative dependencies
├── uv.lock               # Deterministic dependency tree
└── src/
    └── agent_workspace/
        ├── __init__.py
        ├── agent.py      # The ADK Agent instantiation
        ├── runner.py     # The core execution loop
        └── tools/
            ├── __init__.py
            └── extractors.py # Custom API bindings and data extraction logic
```

### 5. Configuring for Local Apple Silicon Execution
```bash
# Disable Vertex AI for local routing
GOOGLE_GENAI_USE_VERTEXAI=FALSE

# Your local model endpoint (e.g., an OpenAI-compatible server running on port 1234)
LOCAL_MODEL_ENDPOINT=http://localhost:1234/v1
```