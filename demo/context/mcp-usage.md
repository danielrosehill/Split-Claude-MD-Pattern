# MCP Selection and Usage

MCP servers extend your capabilities with external services.

In addition to project-level MCPs, the user has MCPs installed at the user level. Use them with these guidelines.

## Context7

Use Context7 liberally to check up-to-date API and SDK documentation. If you suspect a script may be failing due to outdated syntax, invoke Context7 proactively. No permission needed.

## Docker Hub

The Docker Hub MCP allows searching for images and checking tags. Use it when Alex asks about container images or needs to find official/community images for services.

## Slack

Alex uses Slack for team communication at Cascade Labs.

- Send messages to channels or DMs when asked
- Default workspace: `cascadelabs`
- Common channels: `#engineering`, `#incidents`, `#deploys`
- When posting incident updates, always include severity level and affected services

## Grafana

The Grafana MCP connects to the homelab monitoring stack at 192.168.1.30:3000.

Use it to:
- Query dashboards for system metrics
- Check alerts and their status
- Pull performance data when debugging issues

## Time

Provides the current time and date. Your training data timestamps are stale — use this tool when you need the actual current time.

## GitHub

The GitHub MCP provides enhanced repository management beyond the `gh` CLI. Use for complex operations like cross-repo searches, organization management, and PR workflows.
