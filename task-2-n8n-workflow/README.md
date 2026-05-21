# Task 2 — n8n API Integration Workflow

## Candidate
Piyush Kumar

## Workflow Name
GitHub Automation QA Digest

## Overview
This n8n workflow creates an hourly digest of GitHub repositories related to automation and QA. It fetches public repository data, transforms the response into a top-5 list, enriches the top repository with README metadata, applies a threshold-based IF condition, and sends the final digest to Discord.

## APIs Used
1. **GitHub Search Repositories API**
   - Endpoint: `https://api.github.com/search/repositories`
   - Purpose: Fetch repositories matching the query `n8n automation qa`.

2. **GitHub Repository README API**
   - Endpoint pattern: `https://api.github.com/repos/{owner}/{repo}/readme`
   - Purpose: Enrich the top repository with README metadata.

## Why These APIs
GitHub APIs are public, reliable, easy to test, and relevant to an Automation & QA Developer role because they provide developer ecosystem data. They also support a clean two-step integration pattern: search first, then enrich a selected result.

## Workflow Steps
1. **Schedule Trigger**
   - Runs every 1 hour.

2. **HTTP - Search GitHub Repositories**
   - Calls the GitHub Search API.
   - Uses query parameters to fetch repositories related to automation and QA.
   - `Continue On Fail` is enabled.

3. **IF - GitHub Search Failed?**
   - Checks whether the first API call failed or returned an unexpected response.
   - Routes failures to an error notification path.

4. **Code - Sort and Keep Top 5**
   - Sorts repositories by star count.
   - Keeps only the top 5 repositories.
   - Builds a clean digest payload.

5. **HTTP - Enrich Top Repo README**
   - Calls a second GitHub endpoint to fetch README metadata for the top repository.
   - `Continue On Fail` is enabled so the workflow still produces a fallback digest if README enrichment fails.

6. **Code - Format Final Digest**
   - Formats the final message for the notification channel.
   - Includes whether enrichment succeeded or fallback behavior was used.

7. **IF - Top Repo Stars > 1000?**
   - Routes the result based on the threshold:
     - More than 1000 stars: high-interest digest.
     - 1000 or fewer stars: normal digest.

8. **Discord Output**
   - Sends the final digest to Discord using a webhook URL stored in the n8n environment variable `DISCORD_WEBHOOK_URL`.

## Transformation Logic
The Code node:
- Reads the GitHub API response.
- Filters invalid repository records.
- Sorts repositories by `stargazers_count` in descending order.
- Keeps the top 5 repositories.
- Extracts name, URL, description, stars, forks, language, owner, and repo name.
- Builds a readable digest message.

## Error Handling
The workflow does not fail silently:
- HTTP nodes use `Continue On Fail`.
- The first API response is checked by an IF node.
- If the GitHub Search API fails, a Discord error alert is sent.
- If transformation fails because no repositories are returned, a Discord fallback alert is sent.
- If README enrichment fails, the workflow still sends a digest using the repository URL as fallback.

## Credentials and Secrets
No secrets are hard-coded in the exported workflow. The Discord webhook URL should be configured as an n8n environment variable:

```bash
DISCORD_WEBHOOK_URL=https://discord.com/api/webhooks/YOUR_WEBHOOK_ID/YOUR_WEBHOOK_TOKEN
```

For local testing, start n8n with this environment variable available. Do not commit a real Discord webhook URL to GitHub.

## Files to Submit
- `Task2_Workflow_PiyushKumar.json`
- `screenshots/workflow-canvas.png`
- `screenshots/successful-execution.png`
- This README file
