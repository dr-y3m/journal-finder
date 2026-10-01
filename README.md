# journal-finder — a Claude skill

Finds and ranks the best-fitting academic journals for a business, management or organization-studies manuscript. It runs a live deep search, then delivers a written submission strategy (stretch → target → safe) and an Excel shortlist showing each journal's FNEGE, CNRS, HCERES, CABS AJG, ABDC, Scopus (SJR) and Web of Science standing, with the source and edition of every value.

## How it works

1. **Intake**: full manuscript or title + abstract + keywords; journal language scope decided per manuscript.
2. **Manuscript fingerprint**: research question, constructs, theory, method, context, contribution, community.
3. **Candidate long list** from four channels: the reference list, recently published similar papers, open special issues, field knowledge.
4. **Fit screening** on each journal's official aims and scope (five dimensions, 0–5). Journals below 3.0 are excluded.
5. **Live ranking verification**, each value tagged O (official), S (secondary, edition named) or U (not verified).
6. **Practical profile**: time to first decision, acceptance rate, OA/APC, length limits, predatory red flags.
7. **Scoring**: prestige 40%, fit 35%, speed 15%, APC 10% by default, adjustable in the workbook.
8. **Deliverables**: report in chat + Excel shortlist built by `scripts/build_shortlist.py`.

## Structure

```
SKILL.md                       main instructions
references/ranking-sources.md  where and how each ranking is verified live
references/fit-rubric.md       anchors for the five fit dimensions
references/data-schema.md      JSON format consumed by the Excel builder
scripts/build_shortlist.py     builds the Excel workbook with live formulas
evals/evals.json               test cases used during development
```

## Installing in Claude

Download `journal-finder.skill` (or zip this folder) and add it under Settings → Capabilities → Skills in Claude.

## Status

Draft v0.1 — not yet tested on real manuscripts.

Author: Younès El Manzani (LAREQUOI, UVSQ – Université Paris-Saclay)
