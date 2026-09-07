# Columnline

Connect your AI to the work and knowledge enabled for your own Columnline account.

## Install

1. Choose **Columnline/columnline** as your marketplace source. Adding the marketplace makes the package available; it does not install it.
2. Install **Columnline** from that marketplace.
3. Sign in to its connections with your own accounts and verify access.

**Codex desktop:** Plugins → Add → Add a marketplace. Source: `Columnline/columnline`; Git ref: `main`; Sparse paths: empty. Add the marketplace, then find and install **Columnline**.

**Claude Desktop / Cowork:** Customize → Plugins → Add → Add marketplace → Add from a repository. Enter/select `Columnline/columnline` and click **Sync**. Find the package in Browse/Directory (it may appear under Code), click **+**, and finish installation. Repository access and web controls vary; use the direct connector fallback if this route is unavailable.

**Claude Code, local desktop session:** first add/sync the marketplace with the Claude Desktop steps above. Then use + beside the prompt → Plugins → Add plugin, install the package, and confirm it in Manage plugins. If this local Code browser does not show the marketplace, add it through the terminal-session route below. Local installation does not prove cloud-session availability.

**Claude Code, terminal session:** type `/plugin marketplace add Columnline/columnline`, then `/plugin install columnline@columnline` **inside Claude Code**, one at a time. Use `/mcp` there to sign in.

**Codex CLI:** run `codex plugin marketplace add Columnline/columnline` **in Terminal or PowerShell**, then run `codex`. Type `/plugins` **inside Codex** and install **Columnline**.

Sign in with your own Platform account. Choose Allow saving only when you want the connection to edit. Ask: **Check my Columnline access and show what I can do.**

If your AI client cannot install a marketplace, use the [signed-in setup page](https://columnline.com/mcp/connect) to connect directly. The connection works without a plugin. Installation does not add account permissions.

## Updates

Codex desktop: use Upgrade beside the marketplace. Codex terminal alternative: run `codex plugin marketplace upgrade` in Terminal/PowerShell. Claude Desktop: use marketplace Update/Sync and check the installed package. Claude Code: type `/plugin marketplace update` inside Claude Code, then check `/plugin` → Installed and update the package if offered. Refreshing the catalog and updating an installed package are separate steps. Confirm the installed version and start a new session.

The package teaches discovery, source-backed Knowledge work, and careful Your Plan preparation. Its instructions never grant access. A tool may be unavailable for your role; use only what your live connection returns. Public directory listings are separate from this direct installation.

This repository is generated from Columnline's maintained source. Report a problem through your Columnline contact; changes belong in the source and arrive here as reviewed releases.
