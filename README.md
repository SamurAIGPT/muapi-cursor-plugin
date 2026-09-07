# muapi Cursor Plugin

![muapi logo](./logo.png)

Generate images, videos, and audio from **500+ AI models** — Flux, Midjourney, Veo, Seedance, Suno, and more — right inside Cursor, powered by [muapi.ai](https://muapi.ai)'s unified generative-media API.

This plugin connects Cursor to muapi's hosted [Model Context Protocol](https://modelcontextprotocol.io) server, so your agent can call image/video/audio generation tools, check results, and manage your account without leaving the editor.

## What you get

- **Image generation** — Flux (dev/schnell/kontext), Midjourney, Seedream, HiDream, Qwen, GPT-4o image, and more
- **Video generation** — Veo, Seedance, Wan, Kling, and other text-to-video / image-to-video models
- **Audio generation** — Suno and other music/speech models
- **Model discovery** — search muapi's catalog by keyword or category
- **Account tools** — check balance, manage API keys

19 tools total, proxied to the same REST API that powers [muapi.ai](https://muapi.ai).

## Setup

1. Install this plugin from the Cursor Marketplace.
2. Get an API key at [muapi.ai/dashboard](https://muapi.ai/dashboard).
3. When prompted, paste your key into the `MUAPI_API_KEY` variable (Cursor stores it securely and injects it into the MCP connection — it is never committed to this repo).
4. Ask your agent to generate an image, video, or audio clip.

## How it works

The plugin declares one MCP server (`mcp.json`) pointing at muapi's hosted Streamable HTTP endpoint, `https://api.muapi.ai/mcp`, authenticated with your key as a bearer token. Generation is asynchronous: a `generate` call returns a `request_id` immediately, and the agent polls `muapi_predict_result` until the job completes.

## Related Projects

- [MuAPI](https://muapi.ai) — Unified API for image, video, and audio generation across hundreds of AI models.
- [MuAPI MCP docs](https://muapi.ai/docs/mcp) — Full MCP setup guide for Cursor, Windsurf, Claude Code, and Claude Desktop.
- [MuAPI API reference](https://muapi.ai/docs/api-reference) — Endpoint and prediction lifecycle documentation for the REST API this plugin proxies.
- [MuAPI access keys](https://muapi.ai/access-keys) — Create the API key this plugin needs.
- [muapi-cli](https://github.com/SamurAIGPT/muapi-cli) — Terminal interface for the same API, including a stdio MCP server for Claude Code/Desktop.

## License

MIT
