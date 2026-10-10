# 🤖 Actions Runner Bot

A dedicated public GitHub Actions runner repository designed to execute scheduled data pipelines and synchronization workflows for private backend repositories.

---

## ⚡ Overview

- **Automated Workflows**: Executes periodic data extraction, processing, and index synchronization on a set cron schedule.
- **Privacy & Security**: Zero sensitive endpoints, target repository names, or credentials are hardcoded. All authentication and target mapping are managed securely via GitHub Secrets.

---

## 🚀 Configuration

To configure the runner, define the following **Repository Secrets** under **Settings ➔ Secrets and variables ➔ Actions**:

| Secret Name | Required | Description |
| :--- | :--- | :--- |
| `GH_PAT` | **Yes** | Personal Access Token (classic) with `repo` scope to read/push to your private target repository. |
| `TARGET_REPO` | **Yes** | Full target repository path in format `owner/repo-name`. |

*(Optional)* Under **Settings ➔ Secrets and variables ➔ Actions ➔ Variables**:
- `TARGET_BRANCH`: Target branch to checkout and push (default is `master`).

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
