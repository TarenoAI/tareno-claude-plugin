# Tareno for Claude

Tareno connects Claude to the social accounts already linked to a user's Tareno workspace. It supports analytics and content strategy, media discovery, drafts, approval-backed scheduling and publishing, and action-status tracking.

## Authentication

When Claude asks to connect Tareno, complete the OAuth sign-in on `https://tareno.co`. Every user must have an active Tareno account; the plugin never accepts or asks users to paste API keys.

## Safety model

Analytics and discovery tools are read-only. Drafts remain private in Tareno. Scheduling, publishing, scheduled edits, and deletion create an approval action in Tareno before any consequential change can happen. Review and approve that action in Tareno, then use the returned action status to confirm the outcome.

## Install

The public Claude Directory listing is not live yet. A custom MCP connection can use `https://tareno.co/api/mcp` independently of directory publication.

For Claude Code:

```text
claude plugin marketplace add TarenoAI/tareno-claude-plugin
claude plugin install tareno@tareno-plugins
```

Then run `/reload-plugins` and connect Tareno from the MCP connection flow.

For Claude chat and Cowork, add a custom connector named Tareno with the same MCP URL, then sign in to your Tareno account. Availability depends on your Claude plan and organization settings.

## Examples

- Show my connected social accounts.
- Analyze the last month and explain any gaps or stale data.
- Create platform-specific drafts from this campaign brief.
- Show this week's scheduled posts and flag content gaps.

## Privacy

The plugin connects to Tareno's hosted MCP at `https://tareno.co/api/mcp` and uses the account permissions approved during OAuth sign-in. Account-specific tools can return social account details, posts, media, and analytics to Claude. The plugin does not bundle account data, credentials, local executable scripts, or a local database. Tareno's handling of service data is described in its [privacy policy](https://tareno.co/legal/privacy).

## Directory publication

Submit this plugin folder as a Plugin bundle and submit the hosted MCP separately as an MCP connector through [Claude's developer portal](https://claude.ai/directory/manage). The portal reads the plugin from GitHub and requires a paid Claude plan. Complete validation and live Claude testing before publication; this README is not evidence of directory approval.

## Support

- Website: https://tareno.co
- Documentation: https://tareno.co/docs/mcp
- Support: https://tareno.co/help
- Privacy: https://tareno.co/legal/privacy
- Terms: https://tareno.co/legal/terms
