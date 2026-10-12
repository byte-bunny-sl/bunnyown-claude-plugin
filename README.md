# BunnyOwn for Claude

BunnyOwn is the platform behind direct-booking websites for small businesses:
villas, boats, tours, restaurants and clubs. This plugin connects Claude to
your BunnyOwn workspace, so you can manage the work in conversation:

- websites, pages and blog posts;
- listings and photos;
- calendars and bookings;
- booking processes and the messages your guests receive.

## What it connects to

The plugin declares one remote MCP server, `https://mcp.bunnyown.com/mcp`,
run by Byte Bunny S.L. It is the same server as the BunnyOwn connector in
Claude's directory. The plugin contains no code of its own, no hooks and no
scripts. It also adds two skills, which are instructions Claude follows when
you ask for these tasks:

- **Set up a booking website.** Describe what you rent or sell. Claude then
  shapes the listing type, adds the listings, writes the pages and connects
  the booking process. You confirm each step that changes your public
  website.
- **Edit a guest message.** Claude reads the message and the placeholders it
  may use, and shows you a preview with sample data. It saves your new
  wording only after you agree.

## Install

In Claude, add BunnyOwn from the directory. In Claude Code, run:

```
/plugin install bunnyown --marketplace byte-bunny-sl/bunnyown-claude-plugin
```

## Sign-in and access

Sign-in is OAuth to BunnyOwn. The first time Claude uses a BunnyOwn tool,
you sign in with your BunnyOwn account, choose one workspace and approve the
connection. No key or password is stored in the plugin or pasted into
Claude.

The connection can do only what your role in that workspace allows, and
BunnyOwn checks your membership on every request. To use a second
workspace, add a second connection.

## What is sent where

When Claude calls a BunnyOwn tool, the request goes to BunnyOwn. The result
comes back to Claude, under your agreement with Anthropic. That result can
include personal data held in your workspace, such as a guest's name on a
booking.

The tools never return guests' identity documents, payment card details or
API keys. They cannot take payments or make refunds; refunds are made on the
BunnyOwn dashboard.

## Disconnect

In the BunnyOwn dashboard, open Settings → Connections and press
Disconnect. You can also uninstall the plugin or remove the connector in
Claude.

## Requirements and help

You need a BunnyOwn account that belongs to a workspace; start at
[bunnyown.com](https://bunnyown.com).

- Help: [bunnyown.com/support/ai](https://bunnyown.com/support/ai)
- Privacy: [bunnyown.com/privacy](https://bunnyown.com/privacy)
- Terms: [bunnyown.com/terms](https://bunnyown.com/terms)
- Support: hello@bytebunny.com
