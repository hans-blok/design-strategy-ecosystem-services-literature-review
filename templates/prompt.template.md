---
# ============================================================================
# TEMPLATE — GitHub prompt file (.prompt.md)
#
# Copy this file to .github/prompts/<agent-id>.<intent>.prompt.md.
#
# A prompt file is only a shortcut: it makes an existing agent callable from
# the chat "/" menu. All instructions live in the .agent.md file it points
# at — never duplicate them here. Deleting this file loses nothing except
# the shortcut.
#
# `agent:` must exactly match the `name:` of an existing agent file (a name,
# not a file path).
#
# Note: prompt files work in VS Code, Visual Studio and JetBrains. They are
# not read on GitHub.com or by Claude Code, which use their own mechanisms.
#
# Replace every [PLACEHOLDER] and delete these comment lines when done.
# ============================================================================
description: "[One line, shown in the \"/\" menu: what invoking this does.]"
agent: "[agent-id]"
---

Invoke [`[agent-id]`](../agents/[agent-id].agent.md).
