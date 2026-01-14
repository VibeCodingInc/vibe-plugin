---
description: Start a vibe session - shows who's online and unread messages
allowed-tools: mcp__vibe__vibe_start, mcp__vibe__vibe_init, mcp__vibe__vibe_who, mcp__vibe__vibe_inbox, mcp__vibe__vibe_dm, mcp__vibe__vibe_recall, mcp__vibe__vibe_bye
---

# Vibe Start

Call `vibe_start` to show the welcome dashboard.

## Behavior

1. If user not initialized, ask for:
   - **Handle**: Their X/Twitter handle (e.g., @davemorin)
   - **Building**: What they're working on (one line)

2. For returning users, show dashboard with:
   - Who's online
   - Unread message count
   - People in memory

3. After dashboard displays, use AskUserQuestion for next actions based on state:
   - If unread messages > 0: "You have X unread. Check inbox?"
   - If interesting people online: "X just came online - message them?"
   - Otherwise: Offer compose, discover, or browse options

## Server Hints

The server may return hints in the response. When you see hints like:
- `surprise_suggestion` → Proactively suggest connecting
- `structured_triage_recommended` → Offer inbox triage options
- `suggest_discovery` → Offer to find people to connect with

Use AskUserQuestion to present these as natural options.
