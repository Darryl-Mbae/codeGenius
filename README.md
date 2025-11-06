# 🧠 CodeGenius: The Agentic Code-Documentation System

-----

## 💡 Overview

**CodeGenius** is an AI-powered, **multi-agent system** designed to automatically generate high-quality, comprehensive Markdown documentation for any public GitHub repository.

Built on the **Jac programming language** and the **Jaseci platform**, CodeGenius autonomously clones a repository, analyzes its structure and code relationships, and synthesizes a clear, human-readable report complete with explanatory diagrams. It is optimized for Python and Jac codebases but is generalizable to others.

-----

## ✨ Key Features

  * **Autonomous Documentation Generation:** Accepts a GitHub URL and produces a complete, structured Markdown document (`docs.md`).
  * **Multi-Agent Architecture:** Utilizes specialized, cooperating agents to handle different stages of the workflow, ensuring robustness and modularity.
  * **Code Context Graph (CCG):** Constructs a detailed graph representing relationships between functions, classes, and modules (e.g., function calls, inheritance, composition) to inform the documentation.
  * **Intelligent Planning:** The Supervisor agent uses a file-tree map and README summary to prioritize the documentation of high-impact files first.
  * **API Exposure:** Provides an HTTP interface (Jac server with walkers) to allow users to supply a repository URL and download the resulting documentation.

-----

## ⚙️ System Architecture: The Agent Pipeline

The system is implemented as a multi-agent pipeline, with each agent fulfilling a specialized role in the documentation workflow:

| Agent Role | Responsibility |
| :--- | :--- |
| **Code Genius (Supervisor)** | Orchestrates the entire workflow, receives the GitHub URL, delegates tasks to subordinate agents, and aggregates the final result. |
| **Repo Mapper** | Clones the repository, generates a structured file-tree representation (ignoring directories like `.git`), and produces a concise summary of the `README.md`. |
| **Code Analyzer** | Performs deep code analysis, uses a parser (e.g., Tree-sitter) to process source files, and constructs the **Code Context Graph (CCG)**. It also provides an API for querying relationships. |
| **DocGenie** | The final synthesis agent. Converts structured data from the Repo Mapper and Code Analyzer into a clear, well-organized Markdown document, integrating diagrams and citing CCG relationships. |

-----

## 🚀 Getting Started

### Prerequisites

To run CodeGenius, you'll need:

  * **Python 3.8+**
  * **Jaseci** (The Jac runtime environment)
  * **Git** (for cloning repositories)

### Installation

1.  **Clone the Repository:**

    ```bash
    git clone https://github.com/Darryl-Mbae/codeGenius.git
    cd codeGenius
    ```

2.  **Setup the Jaseci/Python Environment:**

      * It is highly recommended to use a virtual environment.
        ```bash
        python3 -m venv venv
        source venv/bin/activate  # On Linux/macOS
        # venv\Scripts\activate   # On Windows
        ```
      * Install Jaseci and any other Python dependencies (listed in `requirements.txt`, if present):
        ```bash
        pip install jaseci
        # pip install -r requirements.txt (if applicable)
        ```
      * Ensure your **LLM provider key** is set in the **`.env`** file. The primary reference implementation uses **`OPENAI_API_KEY`**, but the code may be adapted to use **Gemini API** keys.

3.  **Build and Run the Jac Server:**
    The Jac server exposes the API (walkers) for interacting with the agent.

    ```bash
    jac serve main.jac
    ```

    This command will launch the backend server. The API can then be interacted with using HTTP POST requests.

-----

## 📦 Repository Structure

| File/Directory | Purpose |
| :--- | :--- |
| `main.jac` | The main Jac program, defining the agents and high-level workflow. |
| `main.impl.jac` | Contains the implementation logic for the agents and their actions. |
| `requirements.jac` | Specifies necessary Jac and Python package dependencies. |
| `utils.py` | Python utility functions integrated with Jac via `py_module`. |
| `.env` | Environment file for secure configuration (e.g., API keys). |
| `repos/` | Local directory for cloned GitHub repositories during the documentation process. |
| `Assignment2.pdf` | The project specification document outlining the system's requirements. |

-----


http://googleusercontent.com/youtube_content/0
