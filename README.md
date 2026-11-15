# AutoXPP for Codex

**Autonomous D365 Finance & Operations development engine — for OpenAI Codex.**

AutoXPP brings AI-powered X++ development to [Codex](https://chatgpt.com/codex/): X++ coding, Visual Studio 2022 build & deploy, test authoring and execution, and browser automation — delivered as a Codex plugin of reusable skills backed by the AutoXPP MCP server.

This is the Codex edition of AutoXPP. The skill content is kept in sync with the Claude Code edition; only the packaging and a few tool-specific skills differ.

## Install

1. Add this marketplace in Codex:
   ```
   codex plugin marketplace add xplusplusai/autoxpp-for-codex
   ```
2. Open the plugin browser and install **AutoXPP**:
   ```
   /plugins
   ```
3. Start a new session, then configure your API key:
   ```
   $autoxpp-setup-api-key ak_your_key_here
   ```

Don't have a key? Subscribe at <https://xplusplus.ai/autoxpp.html>.

## First run

Before invoking any premium skill in a conversation, initialize the session once:

```
$autoxpp-init-session
```

## Skills

**Premium** (require an AutoXPP Pro API key)

| Skill | Purpose |
|-------|---------|
| `autoxpp-init-session` | Session initialization (run first) |
| `autoxpp-build` | VS 2022 build & deploy automation |
| `autoxpp-design-reviewer` | Pre-coding design gate |
| `autoxpp-dev-v2` | X++ coding agent |
| `autoxpp-load-integration-dev` | Role: Integration Developer |
| `autoxpp-load-lifecycle` | Lifecycle bootloader |
| `autoxpp-load-qa-engineer` | Role: QA Engineer |
| `autoxpp-load-senior-fo-dev` | Role: Senior FO Developer |
| `autoxpp-quality-supervisor` | Epistemic auditor |
| `autoxpp-req-analyzer` | Requirement decomposition |
| `autoxpp-test-composer` | Test case generation |
| `autoxpp-test-data-seeder` | Background data seeding |
| `autoxpp-tester` | Test execution & reporting |
| `autoxpp-watchdog` | Stall detection |

**Free** (no API key required)

- `autoxpp-browser-v2`
- `autoxpp-azure-devops`
- `autoxpp-sql-jit`
- `autoxpp-ude-switch`

**Onboarding** (free)

- `autoxpp-setup-api-key` — configure your API key and MCP connection

## Requirements

- [Codex](https://chatgpt.com/codex/) (CLI, ChatGPT desktop app, or IDE extension)
- Windows with Visual Studio 2022 for build/deploy skills
- An AutoXPP Pro API key for premium skills

## Support

- Product: <https://xplusplus.ai/autoxpp.html>
- Company: <https://xplusplus.ai>

---

© XPLUSPLUS.AI. Proprietary.
