---
name: daily-inbox-briefing
description: 7am daily inbox triage: extract action items, send iMessage summary, add to-dos to Notion
---

Good morning! It's 7am. Run the daily inbox briefing:

## Step 1 — Fetch unread emails
Use the Gmail MCP tool `mcp__YOUR_GMAIL_MCP_ID__search_threads` with query `is:unread in:inbox -in:draft` and pageSize 50 to get unread emails from YOUR_EMAIL@gmail.com.

## Step 2 — Extract action items
For each email thread, review the sender, subject, and snippet. Identify:
- **Urgent items**: Need a reply or action TODAY (job applications with deadlines, appointments, government/legal correspondence, time-sensitive requests)
- **Normal items**: Should handle within a few days
- **FYI only**: Newsletters, promos, auto-confirmations — skip these

Group action items by sender. Write each action as a short, specific imperative ("Reply to recruiter", "Prepare for appointment tomorrow", etc.)

## Step 3 — Send iMessage summary
Use `mcp__Read_and_Send_iMessages__send_imessage` to send a concise morning briefing to recipient `YOUR_PHONE_NUMBER`.

Format the message like this (keep it readable on a phone screen):

```
☀️ Morning Briefing — [Today's Date]

📬 [N] unread • [N] action items

⚡ URGENT
• [Item]
• [Item]

📋 TODO
• [Item]
• [Item]

🗓️ TODAY
• [Any appointments or deadlines from emails]
```

Only include sections that have items. Keep the whole message under 300 words.

## Step 4 — Add to-dos to Notion
Use `mcp__YOUR_NOTION_MCP_ID__notion-create-pages` to add each urgent/normal action item as a page in the Notion "To-dos" database (ID: `YOUR_NOTION_DATABASE_ID`).

For each action item, create a page with:
- **Task**: the action item text
- **Status**: "To Do"
- **Priority**: "Urgent" or "Normal" based on classification
- **Due Date**: today's date
- **Source**: "Morning Briefing [Today's Date]"

## Step 5 — Log completion
After all steps, output a brief completion summary: how many emails processed, how many action items found, confirmation that iMessage was sent, and confirmation that Notion to-dos were created.