# SafePrompt plugin for Claude Code

Lets Claude check untrusted text for prompt injection before it acts on that text. It connects Claude Code to the SafePrompt MCP server at `https://mcp.safeprompt.dev/mcp` and adds a skill that tells Claude when to run the check.

## Install

```
/plugin install safeprompt@claude-plugins-official
```

Claude Code asks for your SafePrompt API key when you enable the plugin. Get a free key at https://dashboard.safeprompt.dev. The free tier covers 10,000 checks a month.

## What it adds

- **MCP server** `safeprompt` with two tools:
  - `validate_prompt` checks one text, up to 50,000 characters.
  - `validate_prompts` checks up to 100 texts in one call.
- **Skill** `check-untrusted-text` tells Claude to check web pages, fetched files, emails, comments and tool outputs before acting on them.

Each result says whether the text is safe. If it is not, the result gives the threat category and the reasoning.

## Limits

- Claude decides when to call the tool. To check every input in your own app, call the HTTP API or use the LangChain handler. See https://docs.safeprompt.dev.
- It checks the text you send. It does not inspect MCP tool descriptions from other servers.

## Privacy

Each text you check is sent to the SafePrompt API at api.safeprompt.dev for analysis. See https://safeprompt.dev/privacy.

## Support

https://safeprompt.dev/contact

## License

MIT
