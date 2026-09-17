# Design Strategy & Ecosystem Services — Literature Review

A structured extraction workflow for a literature review of ~120 scientific papers.
For every paper three things are recorded: the **design strategy**, the **ecosystem
services** addressed, and the **study location** — each with a supporting quote, a page
number and a confidence level.

The point of this repository is to make the review *repeatable and auditable* instead of
a one-off spreadsheet exercise: one machine-readable record per paper, validated against
a schema, from which tables, maps and cross-tabs are generated.

---


### Vocabulary before coding

The largest time sink in a review like this is not reading the papers; it is discovering
halfway through that "green roof", "vegetated roof" and "rooftop greening" have been coded
as three different strategies. Agree the controlled vocabulary up front:

- **Design strategy** — an explicit code list, maintained in `methodology/`. Add new codes
  deliberately, and re-check earlier papers when you do.
- **Ecosystem services** — use an established classification such as
  [CICES](https://cices.eu/) or the TEEB categories (provisioning / regulating / cultural /
  supporting) rather than inventing one. It saves discussion and makes results comparable
  with other reviews.
- **Locations** — name, country, and decimal-degree coordinates. Coordinates make a map
  possible later; add them at extraction time, not afterwards.

Code 5–10 papers first, review the vocabulary, then continue. A short calibration round
early is far cheaper than recoding 120 papers late.


---

## Creating an agent for this workspace

Repetitive review work — validating records, checking a batch of extractions, summarising
what is still flagged — is worth handing to an agent. The `agent-designer` in
`.github/agents/` builds one for you, from templates in `templates/`.

**Where to run it.** Prompt files in `.github/prompts/` are read by Copilot Chat in VS Code,
Visual Studio and JetBrains. Open Copilot Chat and type `/agent-designer.design-agent`.
Claude Code does not read that folder; it needs its own file in `.claude/commands/`.

**What to have ready.** Fill in this form and paste it into the chat. Answer what you know;
leave the rest blank and the designer will ask or make a reasoned assumption.

```text
Goal (one sentence):
  [What should this do for me?]

Responsibility:
  [The one job. If you need "and" twice, it is probably two agents.]

Input:
  [What it receives — a file, a folder, a question — and where that comes from.]
  [What must be present before it can start.]

Output:
  [What comes out: a new file, an edited file, a list in chat.]
  [What it should look like — one example line is enough.]

Needs access to:
  [Files, folders or schemas it must read, e.g. schemas/paper.schema.json]

Must not:
  [Anything it should leave alone — e.g. never modify files in papers/]
```

The two answers that actually block progress are the goal and the output. "Something with my
papers" is not enough to start from; "list every record that is still flagged for review" is.

**What you get back.** An `.agent.md` file in `.github/agents/`, optionally a `.prompt.md`
shortcut in `.github/prompts/`, and an explanation of the choices that were not obvious.
Read that explanation — the second agent is much easier to design than the first.

A good first one: an agent that checks the records in `papers/` against
`schemas/paper.schema.json` and reports which are incomplete or flagged. You already know
what its answer should look like, which makes it a fair test of whether the design is right.

---

## Documentation site

Project documentation is published with MkDocs Material:

```bash
pip install -r requirements-docs.txt
mkdocs serve      # local preview at http://127.0.0.1:8000
mkdocs build      # static site into site/
```

---

## Status

Corpus, extraction scripts and results are still to be added. The schema in `schemas/` is
the current contract for what a paper record must contain — start there before writing any
extraction code.
