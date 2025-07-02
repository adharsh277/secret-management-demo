🔐 Secret Management Demo using GitHub Actions





📌 Project Overview

This repository presents a formal demonstration of managing and utilizing encrypted secrets within GitHub Actions for secure and efficient CI/CD workflows. The project aims to simulate real-world automation practices for software delivery pipelines that require handling sensitive credentials.

Key objectives include:

Secure storage of secrets using GitHub's encrypted secrets feature

Accessing secrets within workflow environments

Ensuring secrets remain masked in workflow logs

Using secrets in actual tasks like API authentication and script execution

🛠️ Technologies and Tools

Category

Tool/Service

CI/CD

GitHub Actions

Secret Storage

GitHub Encrypted Secrets

Language

Python

Scripting

Bash, Curl

SCM

Git

🗂️ Repository Structure
secret-management-demo/
├── .github/
│   └── workflows/
│       └── secrets-demo.yml     # GitHub Actions workflow definition
├── run.py                       # Python script to demonstrate secret usage
└── README.md                    # Project documentation

🔐 Secrets Configuration

To run this workflow, define the following repository-level secrets:

Secret Name

Example Value

Purpose

API_KEY

12345-SECRET-KEY

Used for secure API requests

USERNAME

captain_copper

Sample username for demo

⚙️ Workflow Functionality

The CI/CD pipeline performs the following actions:

Checkout source code from the repository

Retrieve secrets and inject them into the environment

Print secrets safely using masked logging

Use curl to simulate an API call with a secret token

Execute a Python script that accesses secrets from environment variables

🧪 Sample Workflow Configuration

name: Secret Management Demo

on: [push]

jobs:
  use-secrets:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Print secrets securely
        run: |
          echo "Using USERNAME: $USERNAME"
          echo "Using API_KEY: $API_KEY"
        env:
          USERNAME: ${{ secrets.USERNAME }}
          API_KEY: ${{ secrets.API_KEY }}

      - name: Call API with secret
        run: curl -H "Authorization: Bearer $API_KEY" https://httpbin.org/bearer
        env:
          API_KEY: ${{ secrets.API_KEY }}

      - name: Run Python script using secrets
        run: python run.py
        env:
          API_KEY_SECRET: ${{ secrets.API_KEY }}
          USERNAME: ${{ secrets.USERNAME }}

🐍 Python Script: run.py
import os
print("Using secrets in Python:")
print("API_KEY_SECRET:", os.getenv("API_KEY_SECRET"))
print("USERNAME:", os.getenv("USERNAME"))

📋 How to Use This Project

Fork or clone this repository

Navigate to Settings → Secrets and Variables → Actions

Add the required secrets: API_KEY, USERNAME

Push a commit to trigger the workflow

Review logs under the Actions tab to verify masking and behavior


