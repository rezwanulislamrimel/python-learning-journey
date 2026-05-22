# 🐍 Python Programming Mastery

<p align="center">
  <img src="https://img.shields.io/badge/Language-Python%203.x-blue?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/IDE-VS%20Code-blueviolet?style=for-the-badge&logo=visual-studio-code&logoColor=white" alt="VS Code">
  <img src="https://img.shields.io/badge/CI%2FCD-Jenkins%20%26%20Actions-D24939?style=for-the-badge&logo=jenkins&logoColor=white" alt="CI/CD">
  <img src="https://img.shields.io/badge/Version%20Control-Git%20%26%20GitHub-orange?style=for-the-badge&logo=github&logoColor=white" alt="Git">
</p>

---

### 🎯 Objective
A meticulously structured repository dedicated to tracking my core programming progression in Python. This space documents my journey from foundational syntax to advanced software engineering concepts, including Object-Oriented Programming (OOP), robust exception handling, and automated functional scripts integrated with hybrid CI/CD infrastructure (Jenkins & GitHub Actions).

---

## 📂 Repository Architecture

```text
├── .github/workflows/         # GitHub Actions CI pipeline configuration
│   └── python-ci.yml
├── 01-Fundamentals/           # Syntaxes, variables, inputs, and memory models
├── 02-Control-Flow/           # Logical operators, conditionals, and iteration blocks
├── 03-Data-Structures/         # Complex collections (Lists, Dicts, Tuples, Sets)
├── 04-Functions-and-Modules/  # Functional programming, scopes, and modularity
├── 05-Advanced-Utilities/     # Built-in APIs (Math, RegEx, JSON, Datetime)
├── 06-Error-and-File-Handling/ # Exception isolation and File System I/O operations
├── 07-OOP-Concepts/           # Production-ready Object-Oriented paradigms
└── 08-Projects/               # Standalone utility-based applications


---

## 🔄 CI/CD Pipeline Automation

To simulate modern DevOps practices, this repository is configured with a dual **Continuous Integration (CI)** framework leveraging both **Jenkins** and **GitHub Actions**.

### 1. GitHub Actions (Cloud-Based CI)

Automated syntax checking and script execution run directly on GitHub-hosted runners upon every `push` or `pull_request` to the `main` branch.

* **Configuration File:** `.github/workflows/python-ci.yml`
* **Workflow Steps:**
name: Python Application CI

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
    - name: Checkout Repository
      uses: actions/checkout@v4

     Alexander
    - name: Set up Python
      uses: actions/setup-python@v5
      with:
        python-level: '3.x'

    - name: Install Dependencies
      run: |
        python -m pip install --upgrade pip
        # pip install -r requirements.txt

    - name: Execute Main Application
      run: |
        # Example trigger for script verification
        python3 08-Projects/your_script_name.py


### 2. Jenkins (On-Premises CI)

Integrated locally on an **Ubuntu/Linux** environment, receiving instant payload triggers via **GitHub Webhooks** tunneled through **Ngrok**.

---

## ⚙️ Requirements & Execution

### Setup Environment

```bash
# Clone the repository
git clone [https://github.com/rezwanulislamrimel/your-python-repo-name.git](https://github.com/rezwanulislamrimel/your-python-repo-name.git)

# Navigate to the workspace
cd your-python-repo-name

```

### Run Scripts Locally

```bash
python3 01-Fundamentals/filename.py

```

---

## 👤 Author

<div align="center">

**Rezwanul Rimel**

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/rezwanulrimel/)
[![Email](https://img.shields.io/badge/Email-D14836?style=flat-square&logo=gmail&logoColor=white)](mailto:rezwanul.rimel97@gmail.com)

*Built for mastering python fundamentals and practicing automated testing architecture.*
⭐ *If this repository helps your learning journey, feel free to give it a star!* ⭐ feel free to give it a star!* ⭐
