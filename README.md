# Claude Code CLI Setup

My personal Claude Code CLI setup on Windows 11

## Prerequisites

- Install [Node.js](https://nodejs.org/en)
- Install [Git for Windows](https://git-scm.com/install/windows)
- Install [Claude Code](https://code.claude.com/docs/en/quickstart)

## CLAUDE.md

My [CLAUDE.md](CLAUDE.md) that is located at ```~\.claude\CLAUDE.md```

Inspired by [Andrej Karpathy](https://github.com/multica-ai/andrej-karpathy-skills/blob/main/CLAUDE.md) and [this prompt here](https://github.com/disler/fixing-smartass-opus-5/blob/main/sr_opus_5_system_prompt.md).

## Marketplaces and Plugins

The plugins i find actually useful
```bash
# pptx docx xlsx skills from anthropic
claude plugin marketplace add anthropics/skills
claude plugin install document-skills@anthropic-agent-skills

# microsoft documentation mcp (good when you work in the MS ecosystem)
claude plugin marketplace add microsoftdocs/mcp
claude plugin install microsoft-docs@microsoft-docs-marketplace

# great skill for diagrams
claude plugin marketplace add cathrynlavery/diagram-design
claude plugin install diagram-design@diagram-design

# great for development
claude plugin marketplace add anthropics/claude-code

claude plugin install frontend-design@claude-plugins-official   # fronted design
claude plugin install csharp-lsp@claude-plugins-official        # for c# development
claude plugin install typescript-lsp@claude-plugins-official    # for ts development
claude plugin install context7@claude-plugins-official          # for documentation fetching
claude plugin install playwright@claude-plugins-official        # for automated browser testing
```

## Settings

My preferred settings in ```~\.claude\settings.json```

| Key | Value | Effect |
| --- | --- | --- |
| `model` | `opus` | default model |
| `modelSettings` | opus-5 `xhigh`, sonnet-5 `high` | per-model reasoning effort |
| `permissions.defaultMode` | `auto` | auto-approve mode on start |
| `cleanupPeriodDays` | 365 | keep transcripts for a year |
| `statusLine` | `node ~/.claude/statusline.js`, refresh 10s | custom status line |
| `voice` / `voiceEnabled` | enabled, `hold` mode | push-to-talk voice input |
| `skipDangerousModePermissionPrompt` | `true` | suppress the bypass-permissions warning |
| `remoteControlAtStartup` | `true` | connect Remote Control on launch |
| `terminalProgressBarEnabled` | `true` | terminal progress bar |
| `inputNeededNotifEnabled` / `agentPushNotifEnabled` | `true` | push notifications |

Environment variables set under `env`:

| Variable | Value | Effect |
| --- | --- |  --- |
| `CLAUDE_CODE_GIT_BASH_PATH` | path to Git for Windows `bash.exe` | Was required on my installation |
| `MAX_MCP_OUTPUT_TOKENS` | `100000` | Enables Claude to read more tokens from MCP output |
| `CLAUDE_CODE_FILE_READ_MAX_OUTPUT_TOKENS` | `100000` | Enables Claude to read more tokens from files |
| `CLAUDE_CODE_NO_FLICKER` | `1` | Better UX in the Terminal |
| `CLAUDE_CODE_DISABLE_ARTIFACT` | `1` | Optional: Disable it if you dont use it to save tokens |
| `ENABLE_CLAUDEAI_MCP_SERVERS` | `0` | Optional: Disable it if you dont use it to save tokens |

## Additional Tools

I also have those tools installed:

| Tool | Link | Effect |
| --- | --- |  --- |
|  Rust Token Killer | [https://www.rtk-ai.app/](https://www.rtk-ai.app/) | Saves tokens by compacting certain tool outputs before Claude reads them |
|  Claude Tap | [https://github.com/liaohch3/claude-tap]( https://github.com/liaohch3/claude-tap) | Helps you analyse how Claude Code CLI actually works and what context is transmitted |




## When using API-Key
When using an API-Key from another provider then Anthropic, those ```settings.local.json``` worked fine for me:

```
{
    "env": {
        "ANTHROPIC_BASE_URL": "...",
        "ANTHROPIC_API_KEY": "...",
        "ANTHROPIC_DEFAULT_HAIKU_MODEL": "claude-haiku-4-5*",
        "ANTHROPIC_DEFAULT_SONNET_MODEL": "claude-sonnet-5*[1m]",
        "ANTHROPIC_DEFAULT_OPUS_MODEL": "claude-opus-5*[1m]",
        "ENABLE_TOOL_SEARCH": "true",
        "CLAUDE_CODE_MAX_CONTEXT_TOKENS": "1000000",
        "ANTHROPIC_BETAS": "context-1m-2025-08-07"
    }
}
```