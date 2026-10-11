# 🤖 Actions Runner Bot

A dedicated GitHub Actions runner repository designed to execute scheduled data pipelines and synchronization workflows.

---

## ⚡ Overview

- **Automated Workflows**: Executes on-demand data extraction, processing, and index synchronization via manual triggers.
- **Privacy & Security**: Zero sensitive endpoints, target repository names, or credentials are hardcoded. All authentication and target mapping are managed securely via GitHub Actions secrets.

---

## 📅 Pipelines

| Pipeline | File | Schedule |
| :--- | :--- | :--- |
| **Faculty Sync** | `update_faculty.yml` | Manual trigger (`workflow_dispatch`) |
| **Routine Sync** | `update_exams.yml` | Manual trigger (`workflow_dispatch`) |
| **Academic Sync** | `update_courses.yml` | Manual trigger (`workflow_dispatch`) |
| **Master Runner** | `master_runner.yml` | Manual trigger (`workflow_dispatch`) with custom task selection |

---

## 🔒 Security Best Practices

- All repository operations run in isolated GitHub-hosted Ubuntu runners.
- Credentials and private repository identifiers are masked automatically in GitHub logs.
