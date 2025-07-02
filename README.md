🔐 Secret Management Demo using GitHub Actions



📌 Project Overview
This project demonstrates how to securely manage and use secrets like API keys, tokens, or credentials in GitHub Actions workflows.

It leverages GitHub Secrets to safely inject sensitive values into CI/CD pipelines — without exposing them in logs or code. This is crucial for real-world automation, especially when deploying, calling APIs, or logging into services.

🗂️ Repository Structure
graphql
Copy
Edit
secret-management-demo/
├── .github/
│   └── workflows/
│       └── secrets-demo.yml     # GitHub Actions workflow definition
├── run.py                       # Optional Python script to use secrets
└── README.md                    # Project documentation
🚀 Workflow Functionality
✅ Retrieves secrets securely from GitHub (e.g., API_KEY, USERNAME)

✅ Logs values with masking (***)

✅ Demonstrates use of secrets in:

Echo/log statements

curl request (API auth demo)

Python script (environment variable access)

🔧 GitHub Secrets Used
You need to configure the following repository-level secrets:

Secret Name	Example Value	Purpose
API_KEY	12345-SECRET-KEY	Used in mock API request
USERNAME	captain_copper	Sample value for logging

⚙️ Workflow Trigger
This workflow runs automatically on every push:

yaml
Copy
Edit
on: [push]
🧪 Sample Workflow Steps
🧾 Checkout the repository

🔐 Load and print secrets (masked in logs)

🌐 Call mock API using curl and API_KEY

🐍 Run run.py script that uses secrets via environment variables

🐍 Python Script Example (Optional)
run.py

python
Copy
Edit
import os
print("Using secrets in Python:")
print("API_KEY_SECRET:", os.getenv("API_KEY_SECRET"))
print("USERNAME:", os.getenv("USERNAME"))
🔒 Output Example (Logs)
sql
Copy
Edit
Using USERNAME: ***
Using API_KEY: ***
GitHub automatically masks all secret values in logs to ensure no sensitive data is exposed.

📦 How to Run This Project
🌀 Clone the repository

🔐 Add secrets under
Settings → Secrets and Variables → Actions

🟢 Push any commit

📋 Go to Actions tab and inspect logs for masked secret use

📘 Topics Covered
✅ GitHub Actions CI/CD basics

✅ Secure secret management using secrets.<NAME>

✅ Workflow design with real usage (curl, script)

✅ Masked logging and environment variables

