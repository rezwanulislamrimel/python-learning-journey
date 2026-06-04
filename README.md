<div align="center">

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=200&section=header&text=Python%20Programming%20Mastery&fontSize=38&fontColor=ffffff&fontAlignY=38&desc=Fundamentals%20%E2%80%A2%20OOP%20%E2%80%A2%20Jenkins%20%7C%20GitHub%20Actions%20%7C%20Ngrok&descAlignY=58&descSize=16" />

<br/>

![Python](https://img.shields.io/badge/Python%203.x-3776AB?style=for-the-badge&logo=python&logoColor=white)
![VS Code](https://img.shields.io/badge/VS%20Code-007ACC?style=for-the-badge&logo=visualstudiocode&logoColor=white)
![Jenkins](https://img.shields.io/badge/Jenkins-D24939?style=for-the-badge&logo=jenkins&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white)
![Ngrok](https://img.shields.io/badge/Ngrok-1F1E37?style=for-the-badge&logo=ngrok&logoColor=white)
![Git](https://img.shields.io/badge/Git-F05032?style=for-the-badge&logo=git&logoColor=white)

<br/>

![Status](https://img.shields.io/badge/Status-In%20Progress-orange?style=flat-square)
![Modules](https://img.shields.io/badge/Modules-8-3776AB?style=flat-square)
![CI/CD](https://img.shields.io/badge/CI%2FCD-Jenkins%20%2B%20Actions-2088FF?style=flat-square)
![Webhook](https://img.shields.io/badge/Webhook-Ngrok%20Tunnel-1F1E37?style=flat-square)

</div>

---

## 📌 Overview

A meticulously structured repository dedicated to tracking core programming progression in **Python**. This space documents the journey from foundational syntax to advanced software engineering concepts — including **Object-Oriented Programming (OOP)**, robust exception handling, and automated functional scripts integrated with a **hybrid CI/CD infrastructure** powered by Jenkins, GitHub Actions, and Ngrok.

---

## 🎯 Objectives

- 🐍 Build a solid foundation in Python syntax and core concepts
- 🏛️ Master Object-Oriented Programming paradigms
- 🧩 Work with data structures, modules, and built-in APIs
- 🛡️ Implement robust exception and file handling
- 🔁 Automate pipelines with Jenkins and GitHub Actions
- 🌐 Integrate GitHub Webhooks via Ngrok for local CI triggering
- 🚀 Build standalone utility-based Python projects

---

## 📂 Repository Architecture

```text
python-programming-mastery/
│
├── 📁 .github/
│   └── 📁 workflows/
│       └── python-ci.yml          # GitHub Actions CI pipeline
│
├── 📁 01-Fundamentals/            # Syntax, variables, inputs, memory models
├── 📁 02-Control-Flow/            # Conditionals, logical operators, iteration
├── 📁 03-Data-Structures/         # Lists, Dicts, Tuples, Sets
├── 📁 04-Functions-and-Modules/   # Functional programming, scopes, modularity
├── 📁 05-Advanced-Utilities/      # Math, RegEx, JSON, Datetime APIs
├── 📁 06-Error-and-File-Handling/ # Exception isolation, File System I/O
├── 📁 07-OOP-Concepts/            # Production-ready OOP paradigms
├── 📁 08-Projects/                # Standalone utility-based applications
│
├── 📄 Jenkinsfile                 # Jenkins pipeline definition
├── 📄 README.md
└── 📄 .gitignore
```

---

## 🔄 CI/CD Pipeline Architecture

This repository simulates a modern DevOps environment using a **dual CI framework** — combining cloud-based automation via **GitHub Actions** and on-premises pipeline execution via **Jenkins** with **Ngrok webhook tunneling**.

```
Developer Push / PR
        │
        ▼
  ┌─────────────────────────────────────────┐
  │             GitHub Repository            │
  └──────────┬──────────────────┬───────────┘
             │                  │
             ▼                  ▼
  ┌──────────────────┐  ┌───────────────────────────┐
  │  GitHub Actions  │  │  GitHub Webhook Payload    │
  │  (Cloud CI)      │  │  ──────────────────────▶   │
  │                  │  │       Ngrok Tunnel          │
  │  ubuntu-latest   │  │  ──────────────────────▶   │
  │  runner          │  │    Jenkins (Local/Ubuntu)   │
  └──────────────────┘  └───────────────────────────┘
```

---

## ⚙️ GitHub Actions — Cloud CI

Automated syntax checking and script execution run on **GitHub-hosted runners** upon every `push` or `pull_request` to the `main` branch.

**Configuration:** `.github/workflows/python-ci.yml`

```yaml
name: Python Application CI

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    name: Python CI — Syntax Check & Execution
    runs-on: ubuntu-latest

    steps:
      - name: Checkout Repository
        uses: actions/checkout@v4

      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.x'

      - name: Install Dependencies
        run: |
          python -m pip install --upgrade pip
          # pip install -r requirements.txt

      - name: Syntax Check (flake8)
        run: |
          pip install flake8
          flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics

      - name: Execute Main Application
        run: |
          python3 08-Projects/your_script_name.py
```

### Workflow Stages

```
Push / PR to main
       │
       ▼
┌──────────────────┐
│ Checkout Repo    │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│ Set up Python 3.x│
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│ Install Deps     │
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│ Syntax Check     │  ← flake8
└────────┬─────────┘
         │
         ▼
┌──────────────────┐
│ Execute Script   │
└──────────────────┘
```

---

## 🏗️ Jenkins — On-Premises CI

Jenkins runs locally on an **Ubuntu/Linux** environment and receives instant webhook payload triggers from GitHub via an **Ngrok tunnel**.

### Jenkinsfile

```groovy
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/rezwanulislamrimel/python-programming-mastery.git'
            }
        }

        stage('Set up Python') {
            steps {
                sh 'python3 --version'
                sh 'python3 -m pip install --upgrade pip'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh '''
                    pip install flake8
                    # pip install -r requirements.txt
                '''
            }
        }

        stage('Syntax Check') {
            steps {
                sh 'flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics'
            }
        }

        stage('Run Application') {
            steps {
                sh 'python3 08-Projects/your_script_name.py'
            }
        }

    }

    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed. Please review the logs.'
        }
    }
}
```

---

## 🌐 Ngrok — Webhook Tunnel Setup

**Ngrok** exposes the local Jenkins server to the internet, allowing GitHub to deliver webhook payloads directly to the on-premises Jenkins instance.

### How It Works

```
GitHub Webhook
      │
      │  POST https://<ngrok-id>.ngrok.io/github-webhook/
      ▼
┌─────────────────┐
│   Ngrok Tunnel  │  ← Exposes localhost to internet
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Jenkins Local   │  ← localhost:8080
│ (Ubuntu/Linux)  │
└─────────────────┘
```

### Ngrok Setup Steps

```bash
# Step 1 — Start Ngrok tunnel on Jenkins port
ngrok http 8080

# Step 2 — Copy the forwarding URL
# Example: https://a1b2c3d4.ngrok.io

# Step 3 — Add webhook in GitHub
# Repo → Settings → Webhooks → Add webhook
# Payload URL: https://a1b2c3d4.ngrok.io/github-webhook/
# Content type: application/json
# Trigger: Just the push event ✓
```

---

## ▶️ Local Setup & Execution

```bash
# Clone the repository
git clone https://github.com/rezwanulislamrimel/python-programming-mastery.git

# Navigate to the workspace
cd python-programming-mastery

# Run any module script
python3 01-Fundamentals/filename.py
python3 07-OOP-Concepts/filename.py
python3 08-Projects/your_script_name.py
```

---

## 📚 Learning Modules

<details>
<summary><b>📦 01 — Fundamentals</b></summary>

<br/>

- Syntax, variables, data types
- User input and type casting
- Memory models and references

</details>

<details>
<summary><b>🔀 02 — Control Flow</b></summary>

<br/>

- Conditionals (`if`, `elif`, `else`)
- Logical operators
- Loops (`for`, `while`), `break`, `continue`

</details>

<details>
<summary><b>🗂️ 03 — Data Structures</b></summary>

<br/>

- Lists, Tuples, Sets, Dictionaries
- Comprehensions
- Nested collections

</details>

<details>
<summary><b>⚙️ 04 — Functions & Modules</b></summary>

<br/>

- Function definitions, scopes, closures
- `*args`, `**kwargs`
- Importing and building modules

</details>

<details>
<summary><b>🔧 05 — Advanced Utilities</b></summary>

<br/>

- `math`, `re`, `json`, `datetime` built-in APIs
- String formatting and manipulation
- Regular expressions

</details>

<details>
<summary><b>🛡️ 06 — Error & File Handling</b></summary>

<br/>

- `try`, `except`, `finally`, `raise`
- Custom exceptions
- File I/O: read, write, append

</details>

<details>
<summary><b>🏛️ 07 — OOP Concepts</b></summary>

<br/>

- Classes, constructors, instances
- Inheritance, encapsulation, polymorphism
- Dunder methods and abstraction

</details>

<details>
<summary><b>🚀 08 — Projects</b></summary>

<br/>

- Standalone utility-based Python applications
- Real-world problem solving
- CI/CD integrated script execution

</details>

---

## 🏆 Skills Demonstrated

<div align="center">

![Python](https://img.shields.io/badge/Python%203.x-3776AB?style=flat-square)
![OOP](https://img.shields.io/badge/OOP-Concepts-6366f1?style=flat-square)
![Jenkins](https://img.shields.io/badge/Jenkins%20Pipeline-D24939?style=flat-square)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat-square)
![Ngrok](https://img.shields.io/badge/Ngrok%20Tunneling-1F1E37?style=flat-square)
![Webhooks](https://img.shields.io/badge/GitHub%20Webhooks-181717?style=flat-square)
![CI/CD](https://img.shields.io/badge/CI%2FCD%20Automation-16a34a?style=flat-square)
![Exception Handling](https://img.shields.io/badge/Exception%20Handling-ef4444?style=flat-square)
![File I/O](https://img.shields.io/badge/File%20I%2FO-f97316?style=flat-square)

</div>

---

## 👨‍💻 Author

<div align="center">

### Rezwanul Rimel
**SQA Engineer**

*Performance Testing · API Testing · Manual Testing · Test Automation*

[![GitHub](https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/rezwanulislamrimel)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://linkedin.com/in/Rezwanulrimel)
[![Email](https://img.shields.io/badge/Email-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:rezwanul.rimel97@gmail.com)

*Built for mastering Python fundamentals and practicing automated testing architecture.*

</div>

---

<div align="center">

⭐ **If this repository helps your learning journey, consider giving it a star!** ⭐

<img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=gradient&customColorList=6,11,20&height=100&section=footer" />

</div>
