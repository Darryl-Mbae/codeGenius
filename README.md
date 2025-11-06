# 🧠 CodeGenius: The Agentic Code-Documentation System

> **CodeGenius** is an AI-powered, multi-agent system designed to automatically generate high-quality, comprehensive Markdown documentation for any public GitHub repository.

---

<p align="center">
  <img src="https://github.com/user-attachments/assets/a31c6c8d-80d9-467f-9b98-7a7df3da6ca6" alt="Laptop showing CodeGenius documentation" width="70%">
  &nbsp;&nbsp;&nbsp;&nbsp;
  <img src="https://github.com/user-attachments/assets/47413f11-507e-40e7-b118-f0a4db1c982d" alt="Phone showing CodeGenius documentation" width="20%">
</p>

---

## 💡 Overview

**CodeGenius** is an **AI-powered, multi-agent system** built on the **Jac programming language** and the **Jaseci platform**. It operates autonomously: given a GitHub URL, it clones the repository, analyzes its structure and code relationships, and synthesizes a clear, human-readable documentation report.

While the system is optimized for **Python** and **Jac** codebases, its design is generalizable to other languages.

---

## ✨ Key Features

* **Autonomous Documentation Generation:** Accepts a GitHub URL and produces a complete, structured Markdown document (`docs.md`).
* **Multi-Agent Architecture:** Utilizes specialized, cooperating agents to handle different stages of the workflow, ensuring robustness and modularity.
* **Code Context Graph (CCG):** Constructs a detailed graph capturing relationships between functions, classes, and modules (e.g., function calls, inheritance) to inform deep analysis and documentation.
* **Intelligent Planning:** The **Supervisor** agent uses a file-tree map and README summary to prioritize the documentation of high-impact files first.
* **API Exposure:** Provides an HTTP interface (Jac server with walkers) to allow a user to supply a repository URL and download the generated documentation.

---

## ⚙️ System Architecture: The Agent Pipeline

The system is implemented as a multi-agent pipeline, where each agent fulfills a specialized role in the documentation workflow:

| Agent Role | Responsibility |
| :--- | :--- |
| **Code Genius (Supervisor)** | Orchestrates the workflow, receives the GitHub URL, delegates tasks, and aggregates intermediate results to assemble the final documentation. |
| **Repo Mapper** | Clones the repository, generates a structured **file-tree representation** (ignoring directories like `.git`), and produces a concise **README summary** for planning. |
| **Code Analyzer** | Performs deep code analysis, parses source files (e.g., using Tree-sitter), and constructs the **Code Context Graph (CCG)**. It provides APIs to the Supervisor for querying relationships. |
| **DocGenie** | Synthesizes the final documentation, converting structured data from other agents into a well-organized Markdown document with necessary sections and diagrams. |

---

## 🚀 Getting Started

### Prerequisites

To run CodeGenius, you'll need:

* **Python 3.8+**
* **Jaseci** (The Jac runtime environment)
* **Git** (for cloning repositories)

### Installation

1.  **Clone the Repository:**

    ```bash
    git clone [https://github.com/Darryl-Mbae/codeGenius.git](https://github.com/Darryl-Mbae/codeGenius.git)
    cd codeGenius
    ```

2.  **Setup the Jaseci/Python Environment:**

    * It is highly recommended to use a virtual environment:
        ```bash
        python3 -m venv venv
        source venv/bin/activate  # On Linux/macOS
        # venv\Scripts\activate   # On Windows
        ```
    * Install **Jaseci** and any other Python dependencies:
        ```bash
        pip install jaseci
        # pip install -r requirements.txt (if available)
        ```
    * Ensure your **LLM provider key** is set in the **`.env`** file (e.g., `OPENAI_API_KEY` or a Gemini key).

3.  **Build and Run the Jac Server:**
    The Jac server exposes the API (walkers) for interacting with the agent.

    ```bash
    jac serve main.jac
    ```

    This command will launch the backend server.

---

## 📦 Repository Structure

| File/Directory | Purpose |
| :--- | :--- |
| `main.jac` | The main Jac program, defining the agents and high-level workflow. |
| `main.impl.jac` | Contains the implementation logic for the agents and their actions. |
| `requirements.jac` | Specifies necessary Jac and Python package dependencies. |
| `utils.py` | Python utility functions integrated with Jac via `py_module`. |
| `.env` | Environment file for secure configuration (e.g., API keys). |
| `repos/` | Local directory for cloned GitHub repositories during analysis. |
| `Assignment2.pdf` | The project specification document outlining the system's requirements. |
