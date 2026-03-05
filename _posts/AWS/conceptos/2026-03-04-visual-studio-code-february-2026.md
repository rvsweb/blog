---
title: "Visual Studio Code February 2026"
categories:
  - VS Code
tags:
  - release
toc: true
toc_label: "In this update"
---

Welcome to the February 2026 release of Visual Studio Code. This release makes agents practical for longer-running and more complex tasks, giving you more control and visibility, new ways to extend agents, and smarter session management.

*   **Agent plugins**: install prepackaged bundles of skills, tools, and hooks from the Extensions view
*   **Agentic browser tools**: let the agent drive the browser to interact with your app and verify its own changes
*   **Session memory**: persist plans and guidance across conversation turns
*   **Context compaction**: manually compact conversation history to free up context space
*   **Fork a chat session**: create a new, independent session that inherits conversation history to explore alternative approaches
*   **Agent Debug panel**: get real-time visibility into agent events, tool calls, and loaded customizations
*   **Chat accessibility**: use chat to its fullest with screen reader improvements, keyboard navigation, and notification signals
*   **Create agent customizations from chat**: generate prompts, skills, agents, and hooks directly from a conversation
*   **Kitty graphics protocol**: render high-fidelity images directly in the integrated terminal

> If you'd like to read these release notes online, go to [Updates on code.visualstudio.com](https://code.visualstudio.com/updates).

**Insiders:** Want to try new features as soon as possible? You can download the nightly [Insiders build](https://code.visualstudio.com/insiders/) and try the latest updates as soon as they are available.

## Agent controls

Whether you are debugging an agent's behavior, tweaking approval flows, or handing work off to a background process, these updates give you more visibility and control over how agents run.

### Background agents

With background agents, you can hand off tasks to Copilot CLI, while still keeping track of them in VS Code. We have made several improvements to align the capabilities and experience of background agents with local and cloud agents.

*   **Context compaction**: Copilot automatically compacts the conversation history when the context window reaches its limit. You can now also manually trigger compaction for background agents with the `/compact` slash command.
*   **Use /slash commands**: chat customization options like prompt files, hooks, and skills are now also available in background agent sessions as slash commands.
*   **Rename background agent sessions**: you can now rename your background agent sessions to keep track of them more easily.

### Claude agents

Last month, we added Claude agents, enabling you to interact with the Claude Agent SDK using Claude models included in your GitHub Copilot subscription.

This month, we've expanded this experience with new features and improvements:

*   **Steering and queuing** to let you send follow-up messages mid-conversation to alter the agent's approach or to queue up additional requests.
*   **Session renaming**
*   **Context window rendering with compaction**
*   **Additional slash commands**
    *   `/compact` for on-demand compaction
    *   `/agents` to manage custom agents
    *   `/hooks` to manage Claude hooks
*   Add the `getDiagnostics` tool to let the agent access editor and workspace problems
*   **Significant performance improvements**

More improvements are planned. Share your feedback on GitHub!

### Agent Debug panel (Preview)

With different agent customizations like hooks, skills, and custom agents, it can sometimes be difficult to understand what happens when you send a message to an agent. The Agent Debug panel gives you deeper visibility into your chat sessions and how your chat customizations are loaded.

The Agent Debug panel shows chat events in real time, including chat customization events, system prompts, tool calls, and more. You can see exactly which prompt files, skills, hooks, and other customizations are loaded for a session, making it easier to understand and troubleshoot your agent configuration. This replaces the old Diagnostics chat action with a richer, more detailed view.

Open the panel from the Command Palette with **Developer: Open Agent Debug Panel**, or select the gear icon at the top of the Chat view and choose **View Agent Logs**.

The panel also includes a chart view that displays a visual hierarchy of events, so you can quickly understand the structure and sequence of what happens during a chat session.

This experience is still in preview, so try it out and share your feedback!

> **Note**: The Agent Debug panel is currently only available for local chat sessions. Log data is not persisted, so you can only view logs for chat sessions from your current VS Code session.

### Slash commands for enabling auto approval

You can now toggle global auto approve directly from the chat input using slash commands, without navigating to settings:

*   `/autoApprove` enables global auto approve for all tools
*   `/disableAutoApprove` disables global auto approve
*   `/yolo` and `/disableYolo` are aliases for the same commands.

> **CAUTION**: Global auto approve skips all tool confirmation prompts, letting the agent run tools and terminal commands without waiting for your approval. This can speed up longer, multi-step tasks but means you won't have the opportunity to cancel potentially destructive actions. Make sure you understand the security implications before enabling it and consider using terminal sandboxing for additional protection.

### Edit and ask mode changes

Setting: `chat.editMode.hidden`

As agents have evolved, agent mode now handles everything edit mode can do and more, with better performance and reliability. Edit mode is now hidden from the agent picker by default, so users benefit from the most capable mode without having to choose between options. You can bring it back by disabling the `chat.editMode.hidden` setting.

Ask mode is now backed by a custom agent definition, making it a fully agentic experience. This resolves previous limitations, such as requiring a new session when switching between ask and agent mode.

Both changes demonstrate how to customize your own agents. If you prefer edit mode or want your own version of ask mode, create a custom agent that matches your needs by defining its tools, prompt, and language model. When you disable `chat.editMode.hidden`, you can select the **View edit agent** action in the agent picker to view the agent declaration that powers edit mode, which can serve as a starting point for your own custom agent.

Learn how to create custom agents in the custom agents documentation.

### Ask questions tool

The `askQuestions` tool, which presents a question carousel UI during chat interactions, has been moved into VS Code core. This improves reliability when canceling requests and enables the tool to work consistently across different contexts, including subagents.

When the carousel is active, you can now send a steering message without needing to reply to or dismiss pending questions first. This allows you to redirect the agent's response on the fly, even in the middle of a question sequence. Use the keyboard to navigate between questions with `Alt+N` (next) and `Alt+P` (previous).

### Prevent auto-suspend during chat

VS Code now asks the operating system not to automatically suspend the machine while a chat request is running. You can step away from your computer without worrying about interrupting the agent's response.

Note that closing the lid of an unplugged laptop still triggers suspension.

## Agent extensibility

Agents are only as useful as the tools and customizations you give them. This release makes it easier to extend what agents can do, from installable plugin bundles to browser automation and new code-aware tools.

### Agent plugins (Experimental)

Settings: `chat.plugins.enabled`, `chat.plugins.marketplaces`, `chat.plugins.paths`

VS Code now supports agent plugins, which are prepackaged bundles of chat customizations. Plugins can contain skills, commands, agents, MCP servers, and hooks.

You can search and install agent plugins directly from the Extensions view within VS Code. Enter `@agentPlugins` in the search box or run the **Chat: Plugins** command from the Command Palette.

By default, VS Code retrieves plugins from the `copilot-plugins` and `awesome-copilot` repos. You can configure more sources via the following settings:

*   `chat.plugins.marketplaces`: add additional plugin marketplaces by specifying GitHub or plain git repositories. The setting can also support Claude-style marketplaces such as `anthropics/claude-code`.
*   `chat.plugins.paths`: register local plugin directories by specifying their paths and enabling or disabling them.

Learn more about agent plugins in the agent plugins documentation.

### Agentic browser tools (Experimental)

Setting: `workbench.browser.enableChatTools`

In the previous release, we added a new integrated browser in VS Code desktop which lets you interact with web pages directly within the editor. But what if your agent could autonomously use this browser and validate changes to your website while it's building it?

In this release, we added a set of tools for agents to read and interact with the integrated browser. As the agent interacts with the page, it sees updates to page content and any errors and warnings in the console. The tools work out of the box without the need to install any extra dependencies.

*   **Page navigation**: `openBrowserPage`, `navigatePage`
*   **Page content and appearance**: `readPage`, `screenshotPage`
*   **User interaction**: `clickElement`, `hoverElement`, `dragElement`, `typeInPage`, `handleDialog`
*   **Custom browser automation**: `runPlaywrightCode`

These tools give agents the ability to perform simultaneous authoring and verification of web apps and close the development loop for agents.

By default, pages opened by the agent run in private, in-memory sessions. This gives you control over what browsing data the agent can access. To give the agent access to a specific web page in the integrated browser, you can explicitly share the page with the agent to give temporary access and any saved data.

To try out the new tools, enable `workbench.browser.enableChatTools` and enable the browser tools in the chat tools picker.

Get started with the browser agent testing guide for a step-by-step tutorial.

### Create agent customizations from chat

You can now generate agent customization files directly from a chat conversation by using new `/create-*` slash commands in agent mode:

*   `/create-prompt`: generate a reusable prompt file
*   `/create-instruction`: generate an instruction file for project conventions
*   `/create-skill`: extract a multi-step workflow into a skill package
*   `/create-agent`: create a specialized custom agent persona
*   `/create-hook`: create a hook configuration for lifecycle automation

Each command guides you through the creation process and lets you choose between user-level (account-wide) or workspace-level (project-specific) storage.