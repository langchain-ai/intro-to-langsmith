# 🔗 Introduction to LangSmith

## Introduction

Welcome to LangChain Academy's **Introduction to LangSmith** course!

This repository is the companion to the course located [HERE](https://academy.langchain.com/courses/intro-to-langsmith).

In this course, we will walk through the fundamentals of LangSmith - exploring observability, prompt engineering, evaluations, feedback mechanisms, and production monitoring.

---

## 🚀 Setup

Here’s our recommended setup to get started with the course.

### Prerequisites

- The [Chrome](https://www.google.com/chrome/) browser is recommended
- [git](https://git-scm.com/install/) is recommended
- A package/project manager: [uv](https://docs.astral.sh/uv/) (recommended) or [pip](https://pypi.org/project/pip/)
- The course requires Python >=3.12, <3.14  See [HERE](#python-virtual-environments) for more information on virtual environments and Python versions.

### Installation

Download the course repository
```bash
# Clone the repo
git clone --depth 1 https://github.com/langchain-ai/intro-to-langsmith.git
$ cd intro-to-langsmith
```

Make a copy of the example .env
```bash
# Create .env file
cp example.env .env
```

Obtain the necessary API Keys if you don't already have them and add them to the .env file.

- LangSmith API key [More Info](#getting-started-with-langsmith)
- OpenAI API key [More Info](#model-providers)

Create a virtual environment and install dependencies. [More Info](#python-virtual-environments)

<details open>
<summary>Using uv (recommended)</summary>

```bash
uv sync
```

</details>

<details>
<summary>Using pip</summary>

```bash
python -m venv .venv
# WinPS:  Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process
source .venv/bin/activate  # WinPS: .venv\Scripts\activate.ps1
pip install -r requirements.txt
```

</details>

### Setup Verification

After completing the Setup section, we recommend you run the following command to verify your environment.

<details open>
<summary>Using uv</summary>

```bash
uv run python env_utils.py
```

</details>

<details>
<summary>Using pip</summary>

```bash
source .venv/bin/activate  # WinPS: .venv\Scripts\activate.ps1
python env_utils.py
```

</details>

[If the script flags issues, see this section below.](#setup-verification-issues)

### Run Notebooks [More Info](#development-environment)

<details open>
<summary>Using uv (recommended)</summary>

```bash
uv run jupyter lab
```

</details>

<details>
<summary>Using pip</summary>

```bash
source .venv/bin/activate  # WinPS: .venv\Scripts\activate.ps1
jupyter lab
```

</details>


## 📚 Lessons
This repository contains five Modules that serve as introductions to many of LangSmith's most-used features.

---

### Module 1: Visibility while Building

- L1 Tracing Basics
- L2 Types of Runs
- L3 Alternative Ways to Trace
- L4 Conversational Threads

### Module 2: Testing Your Application

- L1 Datasets
- L2 Evaluators
- L3 Experiments
- L4 Analyzing Experiment Results
- L5 Pairwise Evaluation
- L6 Summary Evaluators

### Module 3: Prompt Engineering

- L1 Playground
- L2 Prompt Hub
- L3 Lifecycle
- L4 Prompt Canvas

### Module 4: Collecting Human Feedback

- L1 User Feedback
- L2 Annotation Queues

### Module 5: Monitoring in Production

- L1 Filtering
- L2 Online Evaluation
- L3 Automations
- L4 Monitoring
- L5 Dashboards


## 📖 Related Resources

### Setup Verification Issues

**What the verification procedure checks:**
- ✅ Python executable location and version (must be >=3.12, <3.14)
- ✅ Virtual environment is properly activated
- ✅ Required packages are installed with correct versions
- ✅ Packages are in the correct Python version's site-packages
- ✅ Environment variables (API keys) are properly configured

**Configuration Issues and Solutions:**

<details>
<summary>ImportError when running env_utils.py</summary>

If you see an error like `ModuleNotFoundError: No module named 'dotenv'`, you're likely running Python outside the virtual environment.

**Solution:**
- Use `uv run python env_utils.py` (recommended), or
- Activate the virtual environment first:
  - macOS/Linux: `source .venv/bin/activate`
  - Windows Powershell: `.venv\Scripts\activate.ps1`

</details>

<details>
<summary>Environment Variable Conflicts</summary>

If you see a warning about "ENVIRONMENT VARIABLE CONFLICTS DETECTED", you have API keys set in your system environment that differ from your .env file. Since `load_dotenv()` doesn't override existing variables by default, your system values will be used.

**Solutions:**
1. Do nothing and accept the system environment variable value
2. Unset the conflicting system environment variables for this shell session (commands provided in warning)
3. Use `load_dotenv(override=True)` in your notebooks to force .env values to take precedence
4. Update your .env file or shell init so the values are in agreement

</details>

<details>
<summary>LangSmith Tracing Errors</summary>

If you see "LANGSMITH_TRACING is enabled but LANGSMITH_API_KEY still has the example/placeholder value", you need to either:
1. Set a valid LangSmith API key in your .env file, or
2. Comment out or set `LANGSMITH_TRACING=false` in your .env file

Note: LangSmith is optional for evaluation and tracing. The course works without it.

</details>

<details>
<summary>Wrong Python Version</summary>

If you see a warning about Python version not satisfying requirements, you need Python >=3.12 and <3.14.

**Solution:**
- If using `uv`: Run `uv sync` which will automatically install the correct Python version
- If using pip: Install Python 3.12 or 3.13 using [pyenv](#python-virtual-environments) or from [python.org](https://www.python.org/downloads/)

</details>

### Python Virtual Environments

Managing your Python version is often best done with virtual environments. This allows you to select a Python version for the course independent of the system Python version.

<details open>
<summary>Using uv (recommended)</summary>

`uv` will install a version of Python compatible with the versions specified in the `pyproject.toml` in the `.venv` directory when running the `uv sync` specified above. It will use this version when invoking with `uv run`. For additional information, please see [uv](https://docs.astral.sh/uv/).
</details>

<details>
<summary>Using pyenv + pip</summary>

If you are using pip instead of uv, you may prefer using pyenv to manage your Python versions. For additional information, please see [pyenv](https://github.com/pyenv/pyenv).

```bash
pyenv install 3.12
pyenv local 3.12
python -m venv .venv
# WinPS:  Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope Process
source .venv/bin/activate  # WinPS: .venv\Scripts\activate.ps1
pip install -r requirements.txt
```

</details>

### Model Providers

If you don't have an OpenAI API key, you can sign up [here](https://openai.com/index/openai-api/). The course primarily uses gpt-4o and gpt-4o-mini which are inexpensive.  Note that the free plan has reduced limits, so a payment plan or pre-pay is recommended.

This course has been created using particular models and model providers.  You can use other providers, but you will need to update the API keys in the .env file and make some necessary code changes. LangChain supports many chat model providers. [More Info](https://docs.langchain.com/oss/python/integrations/providers/all_providers).

### Getting Started with LangSmith

- Create a [LangSmith](https://smith.langchain.com/) account
- Create a LangSmith API key

<img width="600" alt="LangSmith Dashboard" src="https://github.com/user-attachments/assets/e39b8364-c3e3-4c75-a287-d9d4685caad5" />

<img width="600" alt="LangSmith API Keys" src="https://github.com/user-attachments/assets/2e916b2d-e3b0-4c59-a178-c5818604b8fe" />

- Update the .env file you created with your new LangSmith API Key.
- Check that LANGSMITH_TRACING is uncommented and set to true.

For more information on LangSmith, see our docs [here](https://docs.langchain.com/langsmith/home).

**Note:** If you enable LangSmith tracing by setting `LANGSMITH_TRACING=true` in your .env file, make sure you have a valid `LANGSMITH_API_KEY` set. The environment verification script (`env_utils.py`) will warn you if tracing is enabled without setting a key.

Self-Hosted LangSmith

  If you are using a self-hosted version of LangSmith, you'll need to set this environment variable in addition to the others - see this [guide](https://docs.smith.langchain.com/self_hosting/usage) for more info
  ```
  LANGSMITH_ENDPOINT = "<your-self-hosted-url>/api/v1"
  ```

EU Instance

  If your LangSmith instance is set to the EU, you'll need to set this environment variable in addition to the others.
  ```
  LANGSMITH_ENDPOINT=https://eu.api.smith.langchain.com
  ```

### Environment Variables

This course uses the [dotenv](https://pypi.org/project/python-dotenv) module to read key-value pairs from the .env file and set them in the environment in the Jupyter notebooks. They do not need to be set globally in your system environment.

**Note:** If you have API keys already set in your system environment, they may conflict with the ones in your .env file. The `env_utils.py` verification script will detect and warn you about such conflicts.

This course sets the override option so existing environment variables should not cause a conflict.

### Development Environment

The course uses [Jupyter](https://jupyter.org/) notebooks. The Jupyter package is installed in the virtual environment and can be run as described above. Your may use **jupyter lab** or the simpler **jupyter notebook** if desired.  Jupyter notebooks can also be edited and run in VSCode or other VSCode variants such as Windsurf or Cursor.
