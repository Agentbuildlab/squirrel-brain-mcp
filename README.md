# Squirrel Brain — MCP Server

Give your AI agent a memory and a body on the user's iPhone. **Squirrel Brain** is an iOS app with a hosted **Model Context Protocol (MCP)** server, so Claude, ChatGPT, OpenClaw, or any agent can set real alarms, read the user's day, file photos to boards, append to a forever note, and even **ring the user's phone** — all on the user's behalf.

- 🌐 Website: https://squirrelbrainapp.com
- 🔌 Connect / docs: https://squirrelbrainapp.com/mcp · https://squirrelbrainapp.com/mcp-docs

## Why this exists
Claude and ChatGPT can't, on their own, set a real time-based alarm or reminder on your phone. Squirrel Brain's MCP server gives them that — a genuine on-device action layer, not just stored text.

## Connect
This is a **remote, hosted** server. Get a personal key in the Squirrel Brain iOS app (**Settings → API keys**; it starts with `sb_`), then add to any MCP client:

```json
{
  "mcpServers": {
    "squirrel-brain": {
      "url": "https://geczbtsjfbvfukdzdemr.supabase.co/functions/v1/mcp-server",
      "headers": {
        "X-API-Key": "sb_your_key_here",
        "Authorization": "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImdlY3pidHNqZmJ2ZnVrZHpkZW1yIiwicm9sZSI6ImFub24iLCJpYXQiOjE3Nzc4NTA1OTksImV4cCI6MjA5MzQyNjU5OX0.Rdn6ujhp8t1qJNBmAc8VmV5xst10tpSzXh5tt6VCptM",
        "apikey": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJzdXBhYmFzZSIsInJlZiI6ImdlY3pidHNqZmJ2ZnVrZHpkZW1yIiwicm9sZSI6ImFub24iLCJpYXQiOjE3Nzc4NTA1OTksImV4cCI6MjA5MzQyNjU5OX0.Rdn6ujhp8t1qJNBmAc8VmV5xst10tpSzXh5tt6VCptM"
      }
    }
  }
}
```

The `Authorization`/`apikey` values above are the public gateway key — safe to hardcode. Your `sb_` key is personal; keep it secret.

## Tools (31)
- **Capture & save:** create_item, create_alarm, create_link, add_to_forever_note
- **Reminders & the call:** cell_alert (rings your phone), cancel_alarm, list_alarms
- **Recall the user's brain:** search_items, list_items, get_item, get_daily_brief, get_overdue_items, get_nudge_candidates, list_boards, get_agent_context, get_user_profile, get_current_time
- **Organize & update:** update_item, mark_item_done, move_to_board, remove_from_forever_note
- **Reach the human:** notify_human, send_portal_message, get_portal_messages
- **Account & cleanup:** get_squirrel_brain_help, get_api_key_usage, rotate_api_key, delete_item, delete_items_by_status, delete_items_by_maker, delete_portal_messages

Full parameters: https://squirrelbrainapp.com/mcp-docs

## License
MIT © Acorn Labs LLC
