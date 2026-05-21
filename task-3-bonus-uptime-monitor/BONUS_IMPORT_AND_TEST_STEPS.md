# Bonus Task Import and Screenshot Steps

## 1. Start n8n

```bash
export DISCORD_WEBHOOK_URL="YOUR_DISCORD_WEBHOOK_URL"
npx n8n
```

Open:

```txt
http://localhost:5678
```

## 2. Import the workflow

Import this file into n8n:

```txt
Bonus_UptimeMonitor_PiyushKumar.json
```

## 3. Test the workflow

Click **Execute Workflow**.

The healthy path should show a successful execution log when the app returns status code 200.

## 4. Test the alert path

To test the alert branch, temporarily change the target URL in the **Code - Prepare Monitor Check** node to an invalid URL, such as:

```txt
https://taskpilot-swart.vercel.app/not-found-test
```

Run the workflow again.

The IF node should route to the Discord alert branch.

After testing, change the URL back to:

```txt
https://taskpilot-swart.vercel.app/
```

## 5. Take the required screenshot

Take one screenshot showing the full workflow canvas.

Save it as:

```txt
bonus-uptime-monitor/screenshots/uptime-monitor-workflow.png
```
