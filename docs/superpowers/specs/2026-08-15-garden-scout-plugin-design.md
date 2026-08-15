# Garden Scout Plugin Design

## Goal

Create a personal Codex plugin named `garden-scout` from the supplied Garden Scout skill. Keep its source in the private `cgb37/bh-garden-scout` repository and make it available through the default personal marketplace.

## Structure

The repository is the plugin root and will contain `.codex-plugin/plugin.json`, `skills/garden-scout/SKILL.md`, and the existing `docs/` material. No hooks, MCP servers, apps, scripts, or assets are needed.

## Marketplace

Install a scaffolded copy at `~/plugins/garden-scout` and add it to the default personal marketplace at `~/.agents/plugins/marketplace.json`. Use standard marketplace defaults and preserve existing entries and metadata.

## Behavior

The plugin exposes the Garden Scout skill exactly as supplied: concise plant identification and South Florida nursery guidance, plus workspace note creation when the user asks to save a plant.

## Validation and Version Control

Validate the repository plugin and installed copy with the plugin-creator validator. Commit all current repository content, including `docs/`, to the initial `main` branch and push it to the existing private GitHub origin.

## Distribution

This is a personal plugin, not a team marketplace. Informal family sharing can use the Codex Share link for the personal marketplace entry.
