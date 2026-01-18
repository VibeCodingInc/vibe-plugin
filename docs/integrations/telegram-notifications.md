# Telegram Push Notifications for /vibe

Get instant push notifications on Telegram when you receive DMs on /vibe.

## Overview

Instead of polling `/vibe inbox`, you can receive real-time push notifications via Telegram. When someone sends you a DM on /vibe, you'll get a Telegram message within seconds.

**Tradeoffs:**
- **Pros**: True push notifications, works on mobile, no need to have Claude Code open
- **Cons**: Requires setup (creating a bot, getting chat ID), adds external dependency

> **Note:** Client-native notifications (e.g., macOS notification center) would provide a smoother UX but require deeper integration with each Claude Code client. This Telegram approach works universally across all platforms.

## Setup Steps

### 1. Create a Telegram Bot

1. Open Telegram and search for **@BotFather**
2. Send `/newbot`
3. Choose a name for your bot (e.g., "My Vibe Notifier")
4. Choose a username (must end in `bot`, e.g., `my_vibe_notifier_bot`)
5. Save the **API token** BotFather gives you

### 2. Get Your Chat ID

1. Search for **@userinfobot** on Telegram
2. Start a conversation with it
3. It will reply with your user info including your **numeric chat ID**
4. Save this ID (it looks like `123456789`)

### 3. Start Your Bot

**Important:** You must message your bot first before it can send you notifications.

1. Find your bot in Telegram (search for the username you created)
2. Click **Start** or send any message
3. This authorizes the bot to message you

### 4. Link to /vibe

In Claude Code, run:

```
vibe notifications add telegram
```

When prompted:
1. Enter your **chat ID** from step 2
2. You'll receive a verification code in Telegram
3. Paste the code back to complete linking

### 5. Test It

Run:
```
vibe notifications test
```

You should receive a test notification in Telegram.

## Managing Notifications

```bash
# View current notification settings
vibe notifications

# Enable/disable Telegram notifications
vibe notifications enable telegram
vibe notifications disable telegram

# Remove Telegram integration
vibe notifications remove telegram
```

## Troubleshooting

### "Bot not responding"
- Make sure you started a conversation with your bot (Step 3)
- Check that your bot token is valid with BotFather

### "Invalid chat ID"
- Chat IDs are numeric only (e.g., `123456789`)
- Don't include any letters or special characters
- Get a fresh ID from @userinfobot

### "Verification code not received"
- Check that your bot is properly configured
- Ensure you've messaged your bot at least once
- Try the setup process again from Step 3

## Architecture

```
┌─────────────┐     ┌──────────────┐     ┌──────────┐
│   /vibe     │────▶│   Webhook    │────▶│ Telegram │
│   Server    │     │   Bridge     │     │   Bot    │
└─────────────┘     └──────────────┘     └──────────┘
                                               │
                                               ▼
                                         ┌──────────┐
                                         │   You!   │
                                         │  (push)  │
                                         └──────────┘
```

When you receive a DM on /vibe:
1. The /vibe server triggers a webhook
2. The webhook bridge formats the message
3. Your Telegram bot sends the notification
4. You get a push notification instantly

## Other Integrations

Looking for other notification options? See:
- [Discord Notifications](./discord-notifications.md) (coming soon)
- [Slack Notifications](./slack-notifications.md) (coming soon)
- [Native Notifications](./native-notifications.md) (planned)
