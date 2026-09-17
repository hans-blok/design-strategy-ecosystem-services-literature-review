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
