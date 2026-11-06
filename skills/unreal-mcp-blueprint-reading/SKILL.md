---
name: unreal-mcp-blueprint-reading
description: Read or inspect Unreal Engine Blueprints through unreal-mcp (EditorToolset BlueprintTools) without marking the asset dirty. Use before calling read_graph_dsl, get_node_type_pins, find_node_types, find_nodes or get_node_infos on a Blueprint you only want to look at, not change.
---

# Reading Blueprints without dirtying them

Verified in UE 5.8.4 with the EditorToolset MCP server.

Some "read" tools in `BlueprintTools` write to the graph: `get_node_type_pins` spawns a real
node in the graph and removes it, and `read_graph_dsl` does the same on a graph that has
nodes. The graph ends unchanged but the package is marked dirty, so the editor asks the user
to save and to check the asset out of source control.

- When only reading, use `find_nodes`, `get_node_infos`, `get_connected_subgraph` and
  `find_node_types`; they do not touch the asset.
- Use `get_node_type_pins` and `read_graph_dsl` only on a Blueprint you are about to edit
  anyway.
- `AssetTools.is_dirty` tells whether an asset is marked. If you dirtied an asset you did not
  mean to change, tell the user and ask them not to save it.

After an engine update, recheck which tools dirty: save a scratch Blueprint, call the tool,
then `is_dirty`.
