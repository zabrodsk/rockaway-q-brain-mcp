# Rockaway Q / QAQ Brain MCP

This connects Claude Code or Codex to the read-only Rockaway Q / QAQ brain.

After setup, you can chat naturally and ask questions like:

```text
What does the Q brain know about this project?
Search the Q / QAQ brain for recent notes about this customer.
What open blockers do we have around this workflow?
Which pages mention this initiative?
```

This repository is only for the MCP connection. It does not install any extra workflow.

## Install On Windows

Open PowerShell and paste:

```powershell
irm https://raw.githubusercontent.com/zabrodsk/rockaway-q-brain-mcp/main/setup.ps1 | iex
```

The setup asks for your bearer token. The token is hidden while you type.

## Install On Mac Or Linux

Open Terminal and paste:

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/zabrodsk/rockaway-q-brain-mcp/main/bootstrap.sh)"
```

The setup asks for your bearer token. The token is hidden while you type.

## What Gets Connected

```text
MCP name: rockaway-q
MCP URL:  http://100.102.180.108:8788/rockaway-q/mcp
Access:   read-only
```

Available brain tools include search, query, page reads, links, backlinks, and stats. The MCP cannot edit the brain.

## How To Use It

After setup, restart Claude Code or Codex if it was already open.

Then ask normal questions:

```text
Use the Rockaway Q brain to summarize what we know about this project.
Search the Q / QAQ brain for the latest customer context.
What notes in the Q brain mention the onboarding workflow?
```

To verify from a terminal:

```powershell
codex mcp list
```

You should see `rockaway-q`.

## Need A Token?

Ask the Rockaway brain admin for a Rockaway Q / QAQ bearer token. You also need access to the private network where `100.102.180.108` is reachable.

## Setup Guide

Open or download the guide:

[Rockaway Q Brain MCP Guide.pdf](docs/Rockaway%20Q%20Brain%20MCP%20Guide.pdf)
