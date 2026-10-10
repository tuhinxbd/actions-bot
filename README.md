# 🤖 Actions Runner Bot

A dedicated GitHub Actions runner repository designed to execute scheduled data pipelines and synchronization workflows.

---

## ⚡ Overview

- **Automated Workflows**: Executes periodic data extraction, processing, and index synchronization on a set cron schedule.
- **Privacy & Security**: Zero sensitive endpoints, target repository names, or credentials are hardcoded. All authentication and target mapping are managed securely via GitHub Actions secrets.

---

## 📅 Pipelines

| Pipeline | File | Schedule |
| :--- | :--- | :--- |
| **Faculty Sync** | `update_faculty.yml` | 1st of every month (00:00 UTC) + Manual trigger |
| **Routine Sync** | `update_exams.yml` | Daily (01:00 UTC) + Manual trigger |
| **Academic Sync** | `update_courses.yml` | Weekly on Sunday (00:00 UTC) + Manual trigger |
| **Master Runner** | `master_runner.yml` | Manual trigger (`workflow_dispatch`) with custom task selection |

---

## 🔒 Security Best Practices

- All repository operations run in isolated GitHub-hosted Ubuntu runners.
- Credentials and private repository identifiers are masked automatically in GitHub logs.
