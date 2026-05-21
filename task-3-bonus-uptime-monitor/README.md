# Bonus Task — Uptime Monitor

## Overview

This n8n workflow monitors the deployed TaskPilot web application:

`https://taskpilot-swart.vercel.app/`

The workflow runs every 5 minutes, sends an HTTP request to the app, checks the response status code, tracks response time, and sends a Discord alert if the app is unhealthy.

## Workflow Logic

1. **Schedule Trigger** runs every 5 minutes.
2. **Prepare Monitor Check** stores the target URL, start time, and response-time threshold.
3. **HTTP Ping** sends a GET request to the TaskPilot URL.
4. **Build Uptime Result** calculates:
   - HTTP status code
   - response time
   - health status
   - failure reason
5. **IF Node** checks whether the app is unhealthy.
6. If unhealthy, the workflow sends an alert to Discord.
7. If healthy, the workflow logs the successful check.

## Alert Criteria

An alert is sent if:

- HTTP status code is not `200`
- OR response time is greater than `3000ms`
- OR the HTTP request fails after retry attempts

## Retry Logic

The HTTP request node is configured with:

- `retryOnFail: true`
- `maxTries: 3`
- `waitBetweenTries: 2000ms`

This prevents temporary network failures from immediately triggering false alerts.

## Credentials / Secrets

The Discord webhook URL is not hard-coded.

Set it as an environment variable before starting n8n:

```bash
export DISCORD_WEBHOOK_URL="https://discord.com/api/webhooks/YOUR_WEBHOOK_ID/YOUR_WEBHOOK_TOKEN"
npx n8n
```

Do not commit a real webhook URL to GitHub.

## Deliverables

- `Bonus_UptimeMonitor_PiyushKumar.json`
- Screenshot of the imported workflow canvas
