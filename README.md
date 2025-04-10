# N8N Workflows

Sharing some common work to help others out.

If you spot something, feel free to use Issues to raise suggestions, changes, recommdations or issues.

**List of Workflows**

- [365 Service Alerts Summary to Slack](#365-service-alerts-summary-to-slack)
- [Automatically document and backup N8N workflows](#automatically-document-and-backup-n8n-workflows)


## [365 Service Alerts Summary to Slack](workflows/365_Service_Alerts__Summarize_and_push_alert_to_Slack.json)

Intended for a dedicated Slack channel for outage notifications, and to be readable on mobile or desktop.

- Scans for M365 outage alert emails
- Checks if it impacts your users in specific countries (list manually defined), if the alert calls it out, and adjusts the summary accordingly.
- Uses Slack Blocks and provides a button to the M365 Incident (admin.microsoft.com)
- Cleans up by deleting the original alert email, after successful send to Slack
- Uses OpenAI's 4o-mini model, can be easily replaced with locally hosted Ollama or alternative service, with the same prompts.

_Don't like Slack?_ Can easily replace with [ntfy.sh](https://ntfy.sh/), Teams, Discord, or whatever platform you prefer.

**Download & Setup**

- [**Download & import the workflow**](workflows/365_Service_Alerts__Summarize_and_push_alert_to_Slack.json)
- Add your credentials (OpenAI, Slack bot connection)
- Modify the system prompt to call out the countries your users reside in

**Sample Slack Output**

![**Sample Slack Output**](img/365_Service_Alert_SlackOutput.png)

**Workflow diagram**

![**Workflow diagram**](img/365_Service_Alert_N8NEditorView.png)




## [Automatically document and backup N8N workflows](workflows/Automatically_document_n8n_workflows_directly_in_Notion_database.json)

Automatically backs up your workflows to Github and generates documentation in a Notion database.

- Weekly run, uses the "internal-infra" tag to look for new or recently modified workflows
- Uses a Notion database page to hold the workflow summary, last updated date, and a link to the workflow
- Uses OpenAI's 4o-mini to generate a summarization of what the workflow does
- Stores a backup of the workflow in GitHub (recommend a private repo)
- Sends notification to Slack channel for new or updated workflows

**Download & Setup**

- [**Download & import the workflow**](workflows/Automatically_document_n8n_workflows_directly_in_Notion_database.json)
- Add your credentials (N8N, Notion, Slack, GitHub)
- Insert your N8N hostname in the _Set fields_ block
- Insert your Notion database in the _Get notion page with workflow id_ block
- Change the "internal-infra" tag if desired

**Sample output in Notion**

![**Sample output in Notion**](img/Autodoc_backup_workflows_NotionOutput.png)

**Workflow diagram**

![**Autodoc and backup Workflow diagram**](img/Autodoc_backup_workflows_N8NEditorView.png)