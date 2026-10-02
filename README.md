# Tareno for Claude

Connect Claude to your Tareno workspace to inspect social accounts, analyze performance, prepare content drafts, and request scheduling or publishing with review in Tareno. This repository contains the Claude plugin and its marketplace catalog. The hosted MCP service is https://tareno.co/api/mcp.

## Install in Claude Code

```text
claude plugin marketplace add TarenoAI/tareno-claude-plugin
claude plugin install tareno@tareno-plugins
```

Run `/reload-plugins`, then complete the Tareno OAuth connection when prompted. An active Tareno account is required. No API key needs to be pasted into Claude.

## Claude chat and Cowork

Add a custom connector named Tareno with the URL `https://tareno.co/api/mcp`, then sign in to Tareno. Availability depends on your Claude plan and organization settings.

The official Claude Directory listing is pending. Publication of this repository does not imply approval or listing by Anthropic.

## Package and support

The plugin source is in [`plugins/tareno`](plugins/tareno), including its manifest, MCP configuration, README, and social-operations skill. See the [plugin README](plugins/tareno/README.md) for examples, authentication, and the approval workflow.

- [Website](https://tareno.co)
- [Documentation](https://tareno.co/docs/mcp)
- [Support](https://tareno.co/help)
- [Privacy](https://tareno.co/legal/privacy)
- [Terms](https://tareno.co/legal/terms)

License: Proprietary, as declared in the plugin manifest.
