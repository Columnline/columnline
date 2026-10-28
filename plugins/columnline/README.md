# Columnline

Connect your AI to the work and knowledge enabled for your own Columnline account.

## Install

1. Choose **Columnline/columnline** as your marketplace source. Adding the marketplace makes the package available; it does not install it.
2. Install **Columnline** from that marketplace.
3. Sign in with your own Columnline account and verify access. Everyone uses this public package; no private GitHub access is required.

**Codex desktop:** Plugins → Add → Add a marketplace. Source: `Columnline/columnline`; Git ref: `main`; Sparse paths: empty. Add the marketplace, then find and install **Columnline**.

**Claude Desktop / Cowork:** Customize → Plugins → Add → Add marketplace → Add from a repository. Enter/select `Columnline/columnline` and click **Sync**. Find the package in Browse/Directory (it may appear under Code), click **+**, and finish installation. Repository access and web controls vary; use the direct connector fallback if this route is unavailable.

**Claude Code, local desktop session:** first add/sync the marketplace with the Claude Desktop steps above. Then use + beside the prompt → Plugins → Add plugin, install the package, and confirm it in Manage plugins. If this local Code browser does not show the marketplace, add it through the terminal-session route below. Local installation does not prove cloud-session availability.

**Claude Code, terminal session:** type `/plugin marketplace add Columnline/columnline`, then `/plugin install columnline@columnline` **inside Claude Code**, one at a time. Use `/mcp` there to sign in.

**Codex CLI:** run `codex plugin marketplace add Columnline/columnline` **in Terminal or PowerShell**, then run `codex`. Type `/plugins` **inside Codex** and install **Columnline**.

Sign in with your own Platform account. Choose Allow saving only when you want the connection to edit. Ask: **Check my Columnline access and show what I can do.**

If your AI client cannot install a marketplace, use the [signed-in setup page](https://columnline.com/mcp/connect) to connect directly. The connection works without a plugin. Installation does not add account permissions.

## Updates

Claude Code third-party marketplace auto-update is off by default. Enable it in marketplace settings if desired, or update manually.

Codex desktop: use Upgrade beside the marketplace. Codex terminal alternative: run `codex plugin marketplace upgrade` in Terminal/PowerShell. Claude Desktop: use marketplace Update/Sync and check the installed package. Claude Code: type `/plugin marketplace update` inside Claude Code, then check `/plugin` → Installed and update the package if offered. Refreshing the catalog and updating an installed package are separate steps. Confirm the installed version and start a new session.

The package teaches daily work review, Leads and Outreach, Sites performance, Content preparation, agent collaboration, source-backed Knowledge and Materials work, and careful Your Plan preparation. Its instructions never grant access. A tool may be unavailable for your role; use only what your live connection returns. Public directory listings are separate from this direct installation.

This repository is generated from Columnline's maintained source. Report a problem through your Columnline contact; changes belong in the source and arrive here as reviewed releases.

## Data and other services

The package declares one connection, Columnline (`https://api.columnline.dev/mcp/columnline` in Claude Code, Claude Desktop and Claude Cowork; `https://api.columnline.dev/mcp/openai` in ChatGPT and Codex). Everything it reads or saves goes through that connection as the signed-in person, within that person's role. With **Allow saving** on, it can store records in Columnline, such as leads and their contact details, drafts, Knowledge pages and plan changes. Columnline keeps those records until the customer archives or removes them, with their revision history. See the [privacy policy](https://columnline.com/privacy).

Some skills also use other services, only through connections the person has already added and signed in to themselves. The package carries no credentials for them:

- **Slack, Gmail, Google Drive, Figma:** read messages, files and links to prepare meeting agendas and check facts.
- **Attio and Fathom:** read relationships and call records to check facts behind Knowledge answers.
- **Instantly.AI or another campaign tool:** prepare a campaign the person reviews and approves before anything is sent.

When Knowledge is searched, Columnline sends the search text to OpenAI to find matching passages, as the privacy policy describes.

## Moving from Columnline Team

Install this public package, sign in as yourself, and verify an authorized real answer before removing the old Columnline Team package. Preserve unrelated connections. Google Workspace remains a separate connection. The private marketplace is retired only after replacement acceptance; removing a package does not automatically revoke a server grant.
