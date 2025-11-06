# 🧠 CodeGenius: The Agentic Code-Documentation System

> [cite_start]**CodeGenius** is an AI-powered, multi-agent system designed to automatically generate high-quality, comprehensive Markdown documentation for any public GitHub repository[cite: 3].

|  |  |
| :---: | :---: |

---

## 💡 Overview

[cite_start]**CodeGenius** is an **AI-powered, multi-agent system** built on the **Jac programming language** and the **Jaseci platform**[cite: 3]. [cite_start]It operates autonomously: given a GitHub URL, it clones the repository, analyzes its structure and code relationships, and synthesizes a clear, human-readable documentation report[cite: 33].

[cite_start]While the system is optimized for **Python** and **Jac** codebases, its design is generalizable to other languages[cite: 34].

---

## ✨ Key Features

* [cite_start]**Autonomous Documentation Generation:** Accepts a GitHub URL and produces a complete, structured Markdown document (`docs.md`)[cite: 33, 66].
* [cite_start]**Multi-Agent Architecture:** Utilizes specialized, cooperating agents to handle different stages of the workflow, ensuring robustness and modularity[cite: 35].
* [cite_start]**Code Context Graph (CCG):** Constructs a detailed graph capturing relationships between functions, classes, and modules (e.g., function calls, inheritance) to inform deep analysis and documentation[cite: 48, 49].
* [cite_start]**Intelligent Planning:** The **Supervisor** agent uses a file-tree map and README summary to prioritize the documentation of high-impact files first[cite: 40, 61].
* [cite_start]**API Exposure:** Provides an HTTP interface (Jac server with walkers) to allow a user to supply a repository URL and download the generated documentation[cite: 67].

---

## ⚙️ System Architecture: The Agent Pipeline

[cite_start]The system is implemented as a multi-agent pipeline, where each agent fulfills a specialized role in the documentation workflow[cite: 37, 38]:

| Agent Role | Responsibility |
| :--- | :--- |
| **Code Genius (Supervisor)** | [cite_start]Orchestrates the workflow, receives the GitHub URL, delegates tasks, and aggregates intermediate results to assemble the final documentation[cite: 39]. |
| **Repo Mapper** | [cite_start]Clones the repository, generates a structured **file-tree representation** (ignoring directories like `.git`), and produces a concise **README summary** for planning[cite: 41, 43, 44, 59]. |
| **Code Analyzer** | [cite_start]Performs deep code analysis, parses source files (e.g., using Tree-sitter), and constructs the **Code Context Graph (CCG)**[cite: 46, 47, 48]. [cite_start]It provides APIs to the Supervisor for querying relationships[cite: 50]. |
| **DocGenie** | [cite_start]Synthesizes the final documentation, converting structured data from other agents into a well-organized Markdown document with necessary sections and diagrams[cite: 51, 52, 54]. |

---

## 🚀 Getting Started

### Prerequisites

To run CodeGenius, you'll need:

* **Python 3.8+**
* [cite_start]**Jaseci** (The Jac runtime environment) [cite: 30]
* **Git** (for cloning repositories)

### Installation

1.  **Clone the Repository:**

    ```bash
    git clone [https://github.com/Darryl-Mbae/codeGenius.git](https://github.com/Darryl-Mbae/codeGenius.git)
    cd codeGenius
    ```

2.  **Setup the Jaseci/Python Environment:**

    * [cite_start]It is highly recommended to use a virtual environment[cite: 84]:
        ```bash
        python3 -m venv venv
        source venv/bin/activate  # On Linux/macOS
        # venv\Scripts\activate   # On Windows
        ```
    * Install Jaseci and any other Python dependencies (as defined in `requirements.jac` and potentially a `requirements.txt`):
        ```bash
        pip install jaseci
        # Install other Python packages if necessary
        ```
    * Ensure your **LLM provider key** is set in the **`.env`** file. [cite_start]The implementation may use **`OPENAI_API_KEY`** or **Gemini API** keys[cite: 13, 14].

3.  **Build and Run the Jac Server:**
    [cite_start]The Jac server exposes the API (walkers) for interacting with the agent[cite: 19, 67].

    ```bash
    jac serve main.jac
    ```

    [cite_start]This command will launch the backend server, exposing the API via walkers defined in `main.jac`[cite: 20].

---

## 📦 Repository Structure

| File/Directory | Purpose |
| :--- | :--- |
| `main.jac` | The main Jac program, defining the agents and high-level workflow. |
| `main.impl.jac` | Contains the implementation logic for the agents and their actions. |
| `requirements.jac` | Specifies necessary Jac and Python package dependencies. |
| `utils.py` | [cite_start]Python utility functions integrated with Jac via `py_module`[cite: 73]. |
| `.env` | [cite_start]Environment file for secure configuration (e.g., API keys)[cite: 13]. |
| `repos/` | [cite_start]Local directory for cloned GitHub repositories during analysis[cite: 58]. |
| `Assignment2.pdf` | [cite_start]The project specification document outlining the system's requirements[cite: 32]. |
