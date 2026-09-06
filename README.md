# Vyrl for Claude Code

Find and edit Vyrl canvases, inspect callable Flows, run requested media workflows, and retrieve outputs.

This is a self-hosted Claude Code plugin marketplace maintained by AAC Ventures LLC. It is not an Anthropic directory listing or an Anthropic endorsement.

## Connect

You need a Vyrl account and a personal MCP token with the permissions needed for your task. Create/manage the token in [Vyrl profile settings](https://vyrl.pro/profile). Keep the token out of chats, source control, and screenshots.

Set `VYRL_MCP_TOKEN` securely in the environment that launches Claude Code. The plugin sends it as an Authorization header only to `https://vyrl.pro/api/mcp`. It does not embed a shared credential or use the ChatGPT-specific OAuth client.

In Claude Code:

```text
/plugin marketplace add solarx56/vyrl-claude
/plugin install vyrl@vyrl-plugins
```

Use `/mcp` to check the connection, then ask to inspect a Canvas or use `/vyrl:canvas-flows`. If a token is missing, invalid, expired, or revoked, configure a valid token in the environment and reconnect. Never paste credentials into a conversation.

## Example requests

- Show my Vyrl canvases and callable Flows.
- Create a Canvas named Campaign draft and summarize its starter graph.
- Inspect the inputs and outputs of this Flow without running it.

Edits commit immediately. Generative runs can spend Vyrl credits and send selected inputs to media providers. Run only when requested. Permanent deletion requires explicit confirmation and the appropriate token permissions. Available models and successful outputs must come from live tool responses.

## Privacy and support

The plugin passes requests to Vyrl using the connected account permissions. Requested generations may involve media providers. See [Vyrl privacy](https://vyrl.pro/privacy) and [terms](https://vyrl.pro/terms). Contact andrew@vyrl.pro.

## Distribution status

The full connector is not eligible for Anthropic’s hosted directory under its current exclusion of AI image, video, and audio generation. See [review criteria](https://claude.com/docs/connectors/building/review-criteria). This repository provides direct Claude Code installation only. The authenticated tools and media-generation path must be tested in the user’s environment; manifest validation alone does not establish a successful run.
