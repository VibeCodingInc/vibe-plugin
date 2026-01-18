# /vibe - Terminal-Native Social

You have /vibe installed - a social layer for Claude Code users.

## 🎯 THE GOLDEN RULE

When user says **"vibe"**, **"let's vibe"**, or **"start vibe"**:
1. Call `vibe_start` - this ONE tool gives you everything
2. The tool output displays automatically - **DO NOT repeat it in your response**
3. After the tool runs, just use AskUserQuestion for next actions (no text response needed)

**DO NOT** call `vibe_who` and `vibe_inbox` separately when starting a session. Use `vibe_start`.

## 🎭 No Extra Text

After calling /vibe tools:
- **DON'T** add intro text like "Let me check..." or "Here's what's happening..."
- **DON'T** repeat/echo the tool output - it's already displayed automatically
- **DO** just proceed to AskUserQuestion if needed, or stay silent
- The tool output IS the response - nothing else needed

## Key Commands

| User Says | You Call | Notes |
|-----------|----------|-------|
| "vibe", "let's vibe" | `vibe_start` | Shows welcome card with stats |
| "who's online" | `vibe_who` | Only if they specifically ask |
| "check messages" | `vibe_inbox` | Only if they specifically ask |
| "dm @handle" | `vibe_dm` | Send a message |
| "vibe bye" | `vibe_bye` | End session |

## 🪄 Making It Magical

For ALL /vibe operations, follow these patterns to keep things clean:

**Sending Messages (`vibe_dm`):**
- Call the tool silently
- After success, just say: "✓ Sent to @handle"
- Don't announce "I'm going to send a message..."

**Remembering (`vibe_remember`):**
- Call the tool silently - NEVER announce parameters
- After success: "✓ Remembered about @handle"
- This happens in the background, user doesn't need details

**Recalling (`vibe_recall`):**
- Call silently before composing messages
- Weave memories naturally into your response
- Don't say "Let me check my memories..."

**Reactions (`vibe_ping`, `vibe_react`):**
- Call silently
- Brief confirm: "✓ Pinged @handle" or "🔥 Reacted to @handle"

**Status (`vibe_status`):**
- Call silently
- Brief confirm: "✓ Status: shipping"

## 💬 Compose Flow

When user wants to message someone:
1. Silently call `vibe_recall @handle` first (get context)
2. Use memories to draft a personalized message
3. Show the draft and ask for approval
4. Call `vibe_dm` silently
5. Confirm: "✓ Sent to @handle"

**Example good flow:**
```
User: "message seth about the integration"
You: [silently calls vibe_recall @seth]
You: "Here's a draft based on your previous conversation:

   Hey @seth - following up on the Vibe × Ping integration
   we discussed. Ready to explore Option A (rev split)?

   Send this?"
User: "yes"
You: [silently calls vibe_dm]
You: "✓ Sent to @seth"
```

## 🔄 Task Completion Notifications

When completing work that originated from a /vibe conversation:

1. **Remember who requested the work** - When you read a DM asking for something, note the handle and request
2. **Complete the work** - Do whatever they asked
3. **Offer to notify** - When offering next actions, include "Tell [person] it's done"
4. **Use compose flow** - If selected: draft → approval → `vibe_dm` → confirm

**Example:**
```
[After completing docs that @seth requested via DM]
AskUserQuestion options:
- "Tell Seth the docs are ready" ← contextual loop-closing
- "Push to remote"
- "Continue editing"
```

## 🚫 What NOT To Do

- ❌ "I'm going to call vibe_remember with handle @seth and observation..."
- ❌ "Let me use vibe_dm to send your message..."
- ❌ Showing raw tool parameters to user
- ❌ Announcing tool calls before making them
- ❌ Repeating tool output after it displays

## ✅ What TO Do

- ✅ Call tools silently (no announcement)
- ✅ Brief confirmations after success
- ✅ Natural conversation flow
- ✅ Use AskUserQuestion for choices
- ✅ Let tool output speak for itself

## 📡 Simplified Hints

Tool outputs may include a small hint comment like:
```
<!-- vibe: surprise_suggestion @scriptedfantasy -->
<!-- vibe: structured_triage_recommended (5) -->
<!-- vibe: suggest_discovery -->
```

When you see these, use AskUserQuestion appropriately:
- `surprise_suggestion @handle` → "Message @handle?"
- `structured_triage_recommended (N)` → "You have N unread. Triage?"
- `suggest_discovery` → "Find people to connect with?"

These hints are intentionally minimal - just context for you, not code for users to see.

## 🔄 Updates

The welcome card shows your current version and whether an update is available.
To update the plugin, run:
```bash
claude plugin update vibe@vibe-plugins
```
Then restart Claude Code.
