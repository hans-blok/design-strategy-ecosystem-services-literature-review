---
# ============================================================================
# TEMPLATE — GitHub Agent (.agent.md)
#
# Copy this file to .github/agents/<agent-id>.agent.md and fill it in.
#
# You are describing a professional function: one role, one responsibility,
# one clearly defined piece of work. Write it the way you would brief a new
# colleague — what the job is, what it needs to start, how it is done, what
# comes out, and where the job stops.
#
# `name` and `description` are the only fields you really need. The others
# are optional — leave a line out entirely if you have no reason to set it.
#
# Replace every [PLACEHOLDER] and delete these comment lines when done.
# ============================================================================

name: "[agent-id-in-kebab-case]"    # same as the filename, without .agent.md
description: >
  [One or two sentences: what this function does, written for someone
  picking it from a list.]

# Optional — omit any line you don't need:
# tools: ["*"]                      # which tools may be used; ["*"] = all, [] = none
# model: "[model-identifier]"       # omit to use the model of whoever calls this
---

# [Function name]

[One paragraph: the responsibility of this function, and who or what it works on.]

## Input

<!--
  What must this function receive before it can start working responsibly?

  Three things to settle per row: what comes in, where it comes from (the
  user, a known place in the workspace, or the result of another function),
  and whether the work can begin without it. For anything required, say what
  must actually be present — "a paper record" is vague, "a .json file with a
  paper_id" is checkable.

  Keep it in plain words. No schemas, no formats, no transport details.
-->

| Input | Source | Required |
|---|---|---|
| `[Input or artifact]` | `[Where it comes from]` | `[Yes/No — and what must be present]` |

If something required is missing, the function says so and stops. It does not
guess the missing part or quietly work around it.

## What it does

[The work performed on that input — the responsibility itself, not the input
and not the result. Be specific: "check each record against the schema and
flag the ones that fail" beats "process the data".]

## How it works

1. [Step]
2. [Step]
3. [Step]

## Concepts

<!--
  Which canonical concepts does this work depend on the meaning of?

  A concept is a term that already has an agreed, recorded definition — for
  example `Entity`, `Attribute` or `Logical Data Model`. List only the names
  here. Do NOT copy the definitions into this file: the definition lives in
  the canonical source and would go stale the moment it changes here.

  Naming a concept is a promise that this function uses the term in its
  agreed sense, not in a private one. Two or three concepts is normal; if
  the work needs no shared terminology, write "None." and move on.
-->

| Concept | Why it matters here |
|---|---|
| `[Concept name]` | [One line: what this function does with it.] |

## Rules

<!--
  Which recorded rules constrain how this work is done?

  Reference a rule by its identifier and the file it lives in — do not paste
  the rule text. The recorded rule stays the authority; a copy here is just
  a copy that can drift out of date.

  If this function needs a constraint that exists nowhere else, you may write
  it out in the last row. Check first that no recorded rule already covers
  it — referencing beats duplicating. Write "None." if nothing applies.
-->

| Rule | Source | Why it applies |
|---|---|---|
| `[RULE-ID]` | `[path/to/rules-file]` | [One line: what it constrains about this work.] |
| [function-specific] | — | [Only when no recorded rule covers it: the constraint, in one sentence.] |

## Output

[What this function produces: a file, an edit, a report in chat. Show a short
example if the exact format matters.]

## What it does not do

- [Work that falls outside this responsibility, and which function handles it instead.]
- [What to do when information is missing — usually: report it, don't invent it.]
