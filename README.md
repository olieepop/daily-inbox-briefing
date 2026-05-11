# Daily Inbox Briefing

A [Claude Cowork](https://www.anthropic.com) scheduled task that runs every morning at 7am to triage your Gmail inbox, send a concise iMessage summary to your phone, and log action items directly into a Notion database — no manual effort required.

## What it does

1. **Fetches** up to 50 unread emails from your Gmail inbox
2. **Classifies** each thread as Urgent, Normal, or FYI (skipped)
3. **Sends** a formatted iMessage briefing to your phone
4. **Creates** Notion to-do entries for every action item, tagged by priority and due date
5. **Logs** a completion summary in the session

## Prerequisites

You'll need the following connectors installed and authenticated in Claude Cowork:

| Connector | Purpose |
|---|---|
| Gmail | Read unread inbox threads |
| iMessage (Read and Send) | Send morning briefing to your phone |
| Notion | Create to-do entries |

## Setup

### 1. Install connectors
In Cowork, go to **Settings → Connectors** and connect Gmail, iMessage, and Notion.

### 2. Find your MCP IDs
Each connector is assigned a unique ID when installed. To find yours, ask Claude:
> "What are the MCP tool names available for Gmail and Notion?"

Your Gmail MCP ID will look like: `mcp__xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx__search_threads`

### 3. Create the Notion database
In your Notion workspace, create a database called **To-dos** with these properties:

| Property | Type | Options |
|---|---|---|
| Task | Title | — |
| Status | Select | To Do (red), Done (green) |
| Priority | Select | Urgent (red), Normal (yellow) |
| Due Date | Date | — |
| Source | Text | — |

Note the database ID from the URL: `https://notion.so/YOUR_DATABASE_ID`

### 4. Configure SKILL.md
Open `SKILL.md` and replace the following placeholders:

| Placeholder | Replace with |
|---|---|
| `YOUR_GMAIL_MCP_ID` | Your Gmail connector MCP ID |
| `YOUR_EMAIL@gmail.com` | Your Gmail address |
| `YOUR_PHONE_NUMBER` | Your phone number (digits only, e.g. `14155550123`) |
| `YOUR_NOTION_MCP_ID` | Your Notion connector MCP ID |
| `YOUR_NOTION_DATABASE_ID` | Your Notion To-dos database ID |

### 5. Install the scheduled task
In Claude Cowork, create a new scheduled task pointing to this `SKILL.md` and set it to run daily at 7am (or your preferred time).

## Customization

- **Run time**: Change the schedule to any time that suits your morning routine
- **Email volume**: Adjust `pageSize` in Step 1 (max 50)
- **Classification rules**: Edit the criteria in Step 2 to match what's urgent for you
- **Message format**: Modify the iMessage template in Step 3
- **Multiple Gmail accounts**: Connect additional Gmail connectors and add a second `search_threads` call in Step 1, merging results before classification

## License

MIT
