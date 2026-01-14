# Vibe Plugin for Claude Code

Terminal-native social layer for Claude Code users.

## Installation

```bash
# Add the marketplace
claude plugin marketplace add https://github.com/bflynn4141/vibe-plugin

# Install the plugin
claude plugin install vibe@vibe-plugins

# Restart Claude Code
```

## Usage

Once installed, just say:
- **"vibe"** or **"let's vibe"** to start a session
- **"who's online"** to see who's around
- **"check messages"** to see your inbox
- **"dm @handle"** to message someone

Or use the slash command: `/vibe:start`

## What is /vibe?

/vibe is a social layer for developers building with Claude Code. It lets you:
- 👥 See who's online and what they're building
- 💬 Send DMs to other developers
- 🧠 Build memory about your connections
- 🎯 Discover people working on similar things

## Updating

When updates are available, the welcome card will show:
```
v1.0.0 · update available: v1.1.0 ⬆️
```

To update:
```bash
claude plugin update vibe@vibe-plugins
```

Then restart Claude Code.

## Alternative Install (curl)

If you prefer the traditional install:
```bash
curl -sL https://slashvibe.dev/install | bash
```

Note: The plugin method auto-updates CLAUDE.md instructions. The curl method requires manual updates.

## Repository Structure

```
vibe-plugin/
├── .claude-plugin/
│   └── marketplace.json      # Marketplace manifest
├── vibe/                     # The actual plugin
│   ├── .claude-plugin/
│   │   └── plugin.json       # MCP server definition
│   ├── skills/
│   │   └── vibe.md           # Natural language triggers
│   ├── commands/
│   │   └── start.md          # /vibe:start slash command
│   └── CLAUDE.md             # Instructions (updated with plugin!)
└── README.md
```

## Links

- **Live**: https://slashvibe.dev
- **API**: https://www.slashvibe.dev/api/
- **Support**: support@slashvibe.dev
