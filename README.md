# VibeSynx plugins for Claude

This repository is a Claude Code plugin marketplace. It currently holds one
plugin, **vibesynx**, which connects Claude Code to the VibeSynx MCP server so
Claude can score your videos with cinematic-grade original music, or turn your
photos into a slideshow set to music.

```bash
claude plugin marketplace add galaxyontech/vibesynx-claude
claude plugin install vibesynx@vibesynx
```

Using claude.ai or the Claude desktop app instead? Add
`https://mcp.vibesynx.com/mcp` as a custom connector under Settings →
Connectors; no plugin needed.

See [`plugins/vibesynx/README.md`](plugins/vibesynx/README.md) for what the
plugin does, what it sends where, and how to disconnect.

The source of this repository is kept in the VibeSynx codebase under
`integrations/claude-plugin/` and published from there.
