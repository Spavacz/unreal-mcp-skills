# unreal-mcp-skills

Agent skills for working with Unreal Engine through its MCP server (EditorToolset).

| Skill | What it does |
|---|---|
| [unreal-mcp-blueprint-reading](skills/unreal-mcp-blueprint-reading/SKILL.md) | Inspect Blueprints without marking them dirty, so the editor does not ask to save or check them out of source control. |

Verified in UE 5.8.4.

## Install

Claude Code plugin marketplace:

```
/plugin install unreal-mcp-skills --marketplace Spavacz/unreal-mcp-skills
```

Any agent, via the skills CLI:

```
npx skills add Spavacz/unreal-mcp-skills
```

Or copy a folder from `skills/` into `~/.claude/skills/` (Claude Code) or your agent's skills folder.
