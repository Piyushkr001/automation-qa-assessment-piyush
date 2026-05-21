# Task 2 — Import and Testing Steps

## 1. Open n8n
Use one of these options:

```bash
npx n8n
```

Then open:

```txt
http://localhost:5678
```

## 2. Configure Discord Webhook Secret
Set your Discord webhook URL as an environment variable before starting n8n.

Example:

```bash
export DISCORD_WEBHOOK_URL="https://discord.com/api/webhooks/YOUR_WEBHOOK_ID/YOUR_WEBHOOK_TOKEN"
npx n8n
```

Do not put the real webhook URL directly inside the exported JSON before pushing to GitHub.

## 3. Import Workflow
1. Open n8n.
2. Click Workflows.
3. Click Import from File.
4. Select `Task2_Workflow_PiyushKumar.json`.

## 4. Test Workflow
1. Click Execute Workflow.
2. Confirm the GitHub Search node returns data.
3. Confirm the Code node returns top repositories.
4. Confirm the README enrichment node runs.
5. Confirm the IF node routes the result.
6. Confirm Discord receives the digest.

## 5. Required Screenshots
Add these screenshots to:

```txt
task-2-n8n-workflow/screenshots/
```

Required screenshot names:

```txt
workflow-canvas.png
successful-execution.png
```

## 6. Final Folder Structure
```txt
task-2-n8n-workflow/
├── Task2_Workflow_PiyushKumar.json
├── README.md
├── .env.example
├── TASK2_IMPORT_AND_TEST_STEPS.md
└── screenshots/
    ├── workflow-canvas.png
    └── successful-execution.png
```
