# Design Strategy & Ecosystem Services — Literature Review

A structured extraction workflow for a literature review of ~120 scientific papers.
For every paper three things are recorded: the **design strategy**, the **ecosystem
services** addressed, and the **study location** — each with a supporting quote, a page
number and a confidence level.

The point of this repository is to make the review *repeatable and auditable* instead of
a one-off spreadsheet exercise: one machine-readable record per paper, validated against
a schema, from which tables, maps and cross-tabs are generated.

## Where to start

- **[Startup](startup.md)** — hoe je in deze workspace zelf een agent maakt, en wat je
  daarvoor kunt voorbereiden.

## This site

Only the contents of `docs/` are published here. The repository itself holds the schema
(`schemas/paper.schema.json`), the agent definitions (`.github/agents/`) and the templates
(`templates/`); see the README in the repository for those.
