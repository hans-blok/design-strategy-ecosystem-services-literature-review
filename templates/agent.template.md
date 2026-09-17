---
# ============================================================================
# TEMPLATE — GitHub Agent (.agent.md)
#
# Copy this file to .github/agents/<agent-id>.agent.md and fill it in.
# One file = one agent = one job.
#
# `name` and `description` are the only fields you really need. The others
# are optional — leave a line out entirely if you have no reason to set it.
#
# Replace every [PLACEHOLDER] and delete these comment lines when done.
# ============================================================================

name: "[agent-id-in-kebab-case]"    # same as the filename, without .agent.md
description: >
  [One or two sentences: what this agent does, written for someone picking
  it from a list.]

# Optional — omit any line you don't need:
# tools: ["*"]                      # which tools the agent may use; ["*"] = all, [] = none
# model: "[model-identifier]"       # omit to use the model of whoever calls the agent
---

# [Agent name]

[One paragraph: what this agent is for, and who or what it works on.]

## What it does

[The task, concretely. Name the files, folders or input it works with.
Be specific: "read every .json file in papers/" beats "process the data".]

## How it works

1. [Step]
2. [Step]
3. [Step]

## Output

[What the agent produces: a file, an edit, a report in chat. Show a short
example if the exact format matters.]

## What it does not do

- [Things that are explicitly out of scope.]
- [What to do when information is missing — usually: report it, don't invent it.]
