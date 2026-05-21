# Automation & QA Developer Assessment — Piyush Kumar

## Overview
This repository contains my submission for the Automation & QA Developer take-home skills assessment.

The submission includes:
- Task 1: Web App QA & Debug Report
- Task 2: n8n API Integration Workflow
- Task 3 / Bonus: Uptime Monitor Workflow

---

## Task 1 — Web App QA & Debug Report

I tested the TaskPilot / TaskTracker web application deployed at:

https://taskpilot-swart.vercel.app/

The QA report covers:
- Public landing page review
- Authentication page review
- Protected dashboard redirect behavior
- Profile route handling
- Branding consistency
- Footer readability
- User-facing UX issues

Files:
- `task-1-qa-report/Task1_QA_Report_PiyushKumar_Updated.pdf`
- `task-1-qa-report/screenshots/`

---

## Task 2 — n8n API Integration Workflow

This workflow creates an hourly GitHub Automation and QA digest.

It performs:
1. Schedule trigger every 1 hour
2. GitHub Search API request
3. Transformation to sort and keep top 5 repositories
4. README enrichment using a second GitHub API endpoint
5. Conditional branch based on repository stars
6. Discord notification output
7. Error handling using failure checks and alert branches

Files:
- `task-2-n8n-workflow/Task2_Workflow_PiyushKumar.json`
- `task-2-n8n-workflow/README.md`
- `task-2-n8n-workflow/TASK2_IMPORT_AND_TEST_STEPS.md`
- `task-2-n8n-workflow/.env.example`
- `task-2-n8n-workflow/screenshots/`

---

## Task 3 / Bonus — Uptime Monitor

This optional bonus workflow monitors the TaskPilot live app.

It performs:
1. Schedule trigger every 5 minutes
2. HTTP request to check the live app
3. Status code validation
4. Response-time tracking
5. Retry handling
6. Discord alert if the app is unhealthy

Files:
- `task-3-bonus-uptime-monitor/Bonus_UptimeMonitor_PiyushKumar.json`
- `task-3-bonus-uptime-monitor/README.md`
- `task-3-bonus-uptime-monitor/BONUS_IMPORT_AND_TEST_STEPS.md`
- `task-3-bonus-uptime-monitor/.env.example`
- `task-3-bonus-uptime-monitor/screenshots/uptime-monitor-workflow.png`

---

## Loom Video

Loom video link:

https://www.loom.com/share/bf451406819948debf0ba94cd5cade84

---

## Notes

No credentials or secrets are committed in this repository. Webhook URLs should be configured locally using environment variables.