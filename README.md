# Flow Relay

Flow Relay turns the activity of your connected engineering and operations tools into project context that your AI assistant can use. This plugin connects ChatGPT, Codex, Claude, Cursor, VS Code and GitHub Copilot, Antigravity, Gemini CLI, Mistral Vibe, OpenClaw and Hermes to the hosted Flow Relay MCP server and adds four skills for the most common workflows.

## What you can do

- Ask grounded questions about a project and get answers with citations back to the underlying events.
- Read or generate project handoffs, correlation insights, onboarding briefs, architecture briefs and release notes.
- Inspect and update the project plan: work items, dependencies, evidence links, change approvals and the RAID register.
- Check portfolio health and simulated P50, P80 and P95 finish dates.

## Skills

- get-started: connect your account, list your projects and pick the active one.
- project-handoff: read the latest handoff or generate a new one.
- project-onboarding: prepare a role-specific onboarding brief.
- weekly-status: compile a short status from the plan, the risks, the forecast and recent activity.

## Install

### ChatGPT and Codex

Open the plugin directory in ChatGPT or Codex, search for Flow Relay and install it. To test a build before the listing is live, upload the OpenAI package (a ZIP that holds plugin.json and mcp.json at its root) from the plugins page of the OpenAI platform. Connect your account through the OAuth consent screen the first time a tool runs.

### Claude Code

```
/plugin marketplace add flow-relay/flowrelay-agent-plugin
/plugin install flow-relay@flow-relay
```

Then run /mcp and sign in to Flow Relay.

### claude.ai and Claude Desktop

Download this repository as a ZIP from GitHub. In Claude open Customize, then Plugins, then Add and Upload plugin, and select the file. Connect Flow Relay from the Connectors tab of the plugin. To add a single skill, zip one skill folder and upload it from Customize, then Skills.

### Cursor

Open Customize in Cursor, search the marketplace for Flow Relay and install it. Until the listing is live you can add the MCP server with the one-click buttons on https://www.flowrelay.it/downloads.

### VS Code and GitHub Copilot

```
copilot plugin marketplace add flow-relay/flowrelay-agent-plugin
copilot plugin install flow-relay@flow-relay
```

In VS Code, open **Chat: Open Customizations** or clone this repository and add its path to `chat.plugins.paths` in `settings.json`.

### Antigravity

```
agy plugin install https://github.com/flow-relay/flowrelay-agent-plugin
```

Then authenticate the Flow Relay MCP server from the Customizations page.

### Gemini CLI

```
gemini extensions install https://github.com/flow-relay/flowrelay-agent-plugin
```

Then run /mcp auth flowrelay.

### Mistral Vibe

Copy this repository to ~/.vibe/plugins/flow-relay or to .vibe/plugins/flow-relay in a trusted project. Run /reload-plugins and sign in with /mcp login flowrelay (run /mcp to see the exact server name).

### Hermes

```
hermes skills tap add flow-relay/flowrelay-agent-plugin
hermes skills install flow-relay/flowrelay-agent-plugin/get-started
```

Hermes installs the skills. Add the endpoint https://www.flowrelay.it/mcp in the MCP configuration of Hermes to give them the tools.

### OpenClaw

```
openclaw mcp set flowrelay url "https://www.flowrelay.it/mcp"
openclaw mcp set flowrelay transport "streamable-http"
```

To link the skills from a local clone of this repository, run `openclaw plugins install -l ./flow-relay`.

### Other MCP clients

Any MCP client can use the endpoint https://www.flowrelay.it/mcp (Streamable HTTP with OAuth 2.1) or the npm package @flowrelay/mcp-server with an API key. The guide is at https://www.flowrelay.it/docs/mcp.

## Data and permissions

The plugin contains no scripts and runs no local code. Your assistant talks to https://www.flowrelay.it/mcp over HTTPS. Requests carry the arguments your assistant chooses for a tool (a project id or a question for example) and responses return project data that your account can access: handoffs, activity events, work plans and risk registers.

Sign-in uses OAuth 2.1 with the scopes mcp:read, mcp:ai and mcp:write, so grant only what you need. The tools only read your connected engineering and operations tools. The tools that write act on your Flow Relay project plan and register; the one exception is the Discord tool, which posts a message or an artifact to a channel you choose. Every tool carries MCP annotations that say whether it only reads or can change or delete data, so your client can ask before it runs one. Your client stores the OAuth tokens and the plugin stores nothing.

## Privacy, terms and support

- Privacy policy: https://www.flowrelay.it/privacy
- Terms of service: https://www.flowrelay.it/terms
- Support: https://www.flowrelay.it/support

## License

AGPL-3.0-or-later. See the LICENSE file.
