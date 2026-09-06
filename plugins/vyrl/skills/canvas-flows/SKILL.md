---
name: canvas-flows
description: Work with Vyrl canvases and media Flows when users want to find, inspect, edit, run, or check their Vyrl workflows.
---

# Vyrl Canvas and Flows

Use the connected Vyrl MCP tools and their current schemas. Account scopes can permit reads, edits, or runs independently. If connection or scope checks fail, explain the missing access; do not request passwords or tokens in conversation.

## Find and inspect

Use `list_canvases` to identify a Canvas, then `get_canvas` for its graph and revision. Use `list_flows` and `get_flow` to discover actual callable Flows and their input contracts. Follow returned pagination cursors. Do not invent IDs, model availability, input keys, or media URLs.

## Edit a Canvas

Read `get_canvas_node_catalog` before authoring unfamiliar node kinds or ports. Use `create_canvas` for a new starter graph. `update_canvas` commits immediately: send only the requested changes, a fresh operation UUID, and the revision from `get_canvas`. A stale revision requires rereading and reassessing the user's intended change. Retrying the same uncertain operation must reuse its operation ID and payload.

Canvas deletion is permanent and may be unavailable for the connected account. Only invoke `delete_canvas` after the user explicitly confirms the identified Canvas and permanent deletion; read its current revision first.

## Run and retrieve

Read `get_flow` before `run_flow` and resolve required inputs from its schema. Generative runs can spend Vyrl credits and transmit the selected inputs to media providers. A request to inspect or edit does not authorize a run. When the user requests a run, make its credit-spending nature clear; do not invent a price or claim it is free.

Use one UUID idempotency key per intended run. Retry an uncertain dispatch with the same key and inputs. On an idempotency mismatch, inspect the Canvas and existing run state rather than minting a new key automatically. Use `get_flow_run` with the returned Canvas, Flow, and run IDs to check progress. A queued or running job is not completed media. Report terminal errors without restarting the job automatically.

Show returned media links and the Canvas link (`https://vyrl.pro/canvas/<canvasId>`) only when the ID came from a tool. Summarize the result in plain language. Do not claim rendering, publishing to social platforms, refunds, or successful edits unless the tool result establishes them. Keep full graph JSON out of the answer unless requested.
