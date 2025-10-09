# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

## Project Overview

This is a Python-based AI agents project focused on exploring agentic AI solutions for business problems. The project uses Jupyter notebooks for experimentation and development, with OpenAI API integration for AI workflows.

## Common Development Commands

### Environment Setup
```powershell
# Create and activate virtual environment (Windows)
python -m venv .venv
.\.venv\Scripts\Activate.ps1

# Install dependencies
pip install -r requirements.txt

# Alternative: Install using project definition
pip install -e .
```

### Jupyter Development
```powershell
# Start Jupyter Lab (preferred for development)
jupyter lab

# Start Jupyter Notebook
jupyter notebook

# Run specific notebook from command line
jupyter nbconvert --to notebook --execute Day01_AIWorkflow\basicAiWorkflow.ipynb
```

### Running Python Scripts
```powershell
# Run the main Python file
python main.py

# Run Python files in virtual environment context
.\.venv\Scripts\python.exe main.py
```

## Project Architecture

### High-Level Structure
- **Root Level**: Contains main entry point (`main.py`), configuration files (`pyproject.toml`, `requirements.txt`), and documentation
- **Day01_AIWorkflow/**: Contains Jupyter notebooks for AI workflow experimentation and development
- **.venv/**: Python virtual environment with all project dependencies

### Key Components

#### Main Application (`main.py`)
Simple entry point that prints a greeting. This appears to be a placeholder for future CLI functionality.

#### Jupyter Notebooks (Day01_AIWorkflow/)
- **`basicAiWorkflow.ipynb`**: Demonstrates basic OpenAI API integration patterns including:
  - Environment variable setup with `python-dotenv`
  - OpenAI client initialization
  - Simple chat completions
  - Interview question generation workflows
- **`agenticSolForBusiness.ipynb`**: Explores business applications of agentic AI:
  - Identifies business domains suitable for agentic AI
  - Pain point analysis and solution development
  - Uses iterative prompting techniques for solution refinement

#### Dependencies Architecture
The project uses a modern Python package management approach with:
- **Core AI**: `openai` for GPT API access
- **Environment Management**: `python-dotenv` for secure API key handling
- **Development Environment**: Full Jupyter ecosystem with extensions
- **Python Version**: Requires Python 3.13+

### Development Patterns

#### Environment Variables
All notebooks follow a consistent pattern:
1. Load environment variables with `load_dotenv(override=True)`
2. Retrieve `OPENAI_API_KEY` from environment
3. Validate API key presence before proceeding

#### OpenAI Integration
Standard workflow pattern:
1. Initialize OpenAI client: `openai = OpenAI()`
2. Structure messages as list of dictionaries with roles
3. Use `gpt-4o-mini` model for cost-effective development
4. Display responses using Markdown formatting in notebooks

#### Iterative AI Workflows
The notebooks demonstrate sophisticated prompting techniques:
- Chain multiple API calls for complex reasoning
- Use previous responses as context for follow-up prompts
- Implement business problem analysis workflows

## Configuration Requirements

### Essential Environment Variables
- `OPENAI_API_KEY`: Required for all OpenAI API interactions

### API Key Security
- Store API keys in `.env` file (not tracked in git)
- Use `python-dotenv` to load environment variables
- Notebooks validate API key presence before execution

## Working with Notebooks

### Best Practices
- Always run the environment setup cells first
- Verify API key is loaded before making OpenAI calls
- Use `display(Markdown())` for formatted AI responses
- Implement proper error handling for API calls

### Common Notebook Patterns
```python
# Standard setup pattern
import os
from dotenv import load_dotenv
from openai import OpenAI
from IPython.display import display, Markdown

load_dotenv(override=True)
openai_api_key = os.getenv("OPENAI_API_KEY")

# Always validate API key
if openai_api_key:
    print("OPENAI_API_KEY is set")
    openai = OpenAI()
else:
    print("OPENAI_API_KEY is not set")
```

## Development Workflow

### Starting Development
1. Ensure Python 3.13+ is installed
2. Create and activate virtual environment
3. Install dependencies from requirements.txt
4. Create `.env` file with `OPENAI_API_KEY`
5. Start Jupyter Lab for notebook development

### Testing AI Workflows
- Use notebooks for rapid prototyping and testing
- Start with `basicAiWorkflow.ipynb` for simple API testing
- Progress to `agenticSolForBusiness.ipynb` for complex workflows
- Always verify API responses before building on them

### Adding New Features
- Create new notebooks in appropriate subdirectories
- Follow established patterns for environment setup
- Use consistent message formatting for OpenAI API calls
- Document business use cases and pain points being addressed