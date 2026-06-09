# Rockaway Q / QAQ Brain MCP

This connects Claude Code or Codex to the read-only Rockaway Q / QAQ brain.

After setup, you can chat naturally and ask questions like:

```text
Use the Rockaway brain to answer this: what do we know about this project?
Use the Rockaway brain to find recent notes about this customer.
Use the Rockaway brain to find open blockers around this workflow.
Use the Rockaway brain to enrich this CSV.
```

This repository connects the Rockaway Q / QAQ brain and installs a small Rockaway brain skill so Claude Code or Codex knows how to ask it questions.

## What You Install

This one setup gives you both pieces:

```text
1. The read-only Rockaway Q / QAQ brain connection.
2. The Rockaway QBrain skill.
```

After setup, the skill command is:

```text
$rockaway-qbrain
```

Use that command at the start of your message when you want Claude Code or Codex to use the Rockaway Q / QAQ brain.

## Install On Windows

Open PowerShell and paste:

```powershell
irm https://raw.githubusercontent.com/zabrodsk/rockaway-q-brain-mcp/main/setup.ps1 | iex
```

The setup asks for your bearer token. The token is hidden while you type.

After setup finishes, restart Claude Code or Codex if it was already open.

## Install On Mac Or Linux

Open Terminal and paste:

```bash
bash -c "$(curl -fsSL https://raw.githubusercontent.com/zabrodsk/rockaway-q-brain-mcp/main/bootstrap.sh)"
```

The setup asks for your bearer token. The token is hidden while you type.

After setup finishes, restart Claude Code or Codex if it was already open.

## What Gets Connected

```text
MCP name: rockaway-q
MCP URL:  http://100.102.180.108:8788/rockaway-q/mcp
Access:   read-only
```

The brain connection is read-only. It can help answer questions, summarize context, and enrich CSVs, but it cannot edit the brain.

## How To Use It

After setup, use this skill command:

```text
$rockaway-qbrain
```

The easiest pattern is:

```text
$rockaway-qbrain Use the Rockaway brain to answer this: ...
```

Examples:

```text
$rockaway-qbrain Use the Rockaway brain to answer this: what do we know about this project?
$rockaway-qbrain Use the Rockaway brain to find the latest customer context.
$rockaway-qbrain Use the Rockaway brain to find notes related to the onboarding workflow.
```

For CSV or spreadsheet lookup, tell Codex or Claude:

```text
$rockaway-qbrain Use the Rockaway brain to enrich this CSV.
```

Useful output columns are `row`, `match`, `confidence`, `summary`, `next step`, and `sources`.

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
