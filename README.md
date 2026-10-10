# 🤖 BUBT Actions Bot (`actions-bot-tuhinxbd`)

A dedicated public GitHub Actions runner repository designed to execute automated scraping and data update workflows for the private **BUBT Server** repository.

---

## ⚡ Why This Repository Exists

- **Unlimited Actions Minutes**: Public repositories on GitHub have free, unlimited GitHub Actions runner execution time, whereas private repositories are capped at 2,000 minutes/month.
- **Data Protection**: The main `bubt-server` codebase remains **100% private**, while this public bot repository runs the compute jobs on a schedule and pushes the scraped JSON outputs back to the private repository.

---

## 🚀 Setup Instructions

To enable this bot to push updates to your private `bubt-server` repository, you need to configure **1 Secret** in this repository:

### 1. Generate a GitHub Personal Access Token (PAT)
1. Go to your GitHub **Settings** ➔ **Developer Settings** ➔ **Personal access tokens** ➔ **Tokens (classic)** (or Fine-grained token).
2. Generate a new token with:
   - Name: `BUBT_ACTIONS_BOT_PAT`
   - Scope: check **`repo`** (Full control of private repositories)
3. Copy the generated token string.

### 2. Add the Secret to this Repository
1. In this repository (`actions bot tuhinxbd` on GitHub), go to:
   **Settings** ➔ **Secrets and variables** ➔ **Actions**.
2. Click **New repository secret**.
3. Name: **`GH_PAT`**
4. Secret: Paste your Personal Access Token.
5. Click **Add secret**.

### 3. (Optional) Custom Repository Target
By default, the workflows target `tuhinx/bubt-server` on branch `master`. If your repository name or branch differs, you can set Repository Variables under **Settings ➔ Secrets and variables ➔ Actions ➔ Variables**:
- `TARGET_REPO` (e.g. `tuhinxbd/bubt-server` or `tuhinx/bubt-server`)
- `TARGET_BRANCH` (e.g. `master` or `main`)

---

## 📅 Workflows Included

| Workflow | File | Trigger Schedule | Action Performed |
| :--- | :--- | :--- | :--- |
| **Faculty Update** | `update_faculty.yml` | 1st of every month (00:00 UTC) + Manual | Scrapes all 12 departments, downloads avatars, generates `faculty_api.json`, pushes to `teachers/output/` |
| **Exam Routines** | `update_exams.yml` | Daily (01:00 UTC) + Manual | Downloads new routine PDFs, converts to JSON routines, pushes to `students/exam/` |
| **Courses** | `update_courses.yml` | Every Sunday (00:00 UTC) + Manual | Scrapes curriculum codes and titles, pushes to `students/course/api/` |
| **Master Runner** | `master_runner.yml` | Manual (`workflow_dispatch`) | Run any or all jobs on-demand with a single click |

---

## 🔒 Security

- Never commit tokens or secrets directly into repository code.
- All private repo authentication is handled strictly via GitHub Actions Secrets (`${{ secrets.GH_PAT }}`).
