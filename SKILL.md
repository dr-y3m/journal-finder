---
name: journal-finder
description: Deep-searches the web to find and rank the best-fitting academic journals for a business, management or organization-studies manuscript, then delivers a written submission strategy plus an Excel shortlist giving each journal's current FNEGE, CNRS, HCERES, CABS AJG, ABDC, Scopus (SJR) and Web of Science standing, every value sourced. Use this skill whenever the user asks where to submit or publish a paper, which journal suits their article, wants target journals, a journal shortlist or a submission cascade, needs a new outlet after a rejection, or asks in French ("quelle revue", "où soumettre", "revue cible", "trouver une revue pour mon article", "cibler une revue classée FNEGE"), even when they only paste a title and abstract or attach a manuscript and ask where it could go. Not for reviewing a manuscript as an editor or referee, and not for writing or polishing the manuscript itself.
---

# Journal Finder

Find the journals where a management manuscript has the best chance of being accepted *and* counted: high enough in the rankings that matter to the author, close enough in scope and conversation to survive the editor's desk. The result is a submission strategy (stretch → target → safe) backed by verified rankings, not a list of famous journals.

## Two rules that come before everything else

**Rankings are looked up, never remembered.** Every ranking value in the report and the Excel must come from a source consulted during this run, with its edition and URL recorded. When a value can't be found, write "not verified". Authors use these labels in evaluation settings (FNEGE, CNRS and HCERES carry real weight in French assessments), and lists change between editions (FNEGE 2022 vs 2025, ABDC 2022 vs 2025), so a remembered rank is often a stale one. A blank cell costs the author a minute; a wrong "FNEGE 1" can cost a submission cycle. The same rule covers metrics, review times, APCs, special issues and the recent papers listed for each journal: report only what was actually seen.

**Fit opens the door; prestige decides the order.** The default weighting puts prestige first, but a journal enters the shortlist only if its fit score reaches the gate (3.0 out of 5). A top-ranked journal whose scope doesn't match produces a desk rejection, which costs weeks or months and gains nothing. Inside the gate, prestige leads.

## Workflow

Eight phases. A full run typically needs 30–60 searches and fetches. Don't cut verification to save calls; save calls by harvesting several facts from each page you open (a journal homepage often shows impact factor, CiteScore, review times and sometimes AJG or ABDC levels at once).

Use today's date from context to define "recent" (the last five years) and to keep only calls for papers whose deadline hasn't passed.

### Phase 0 — Intake

Read the manuscript. If a file is attached, read all of it, including the reference list (use the file-reading or pdf-reading skill if its content isn't already in context). Then set the input mode:

- **Full mode**: the reference list is available, so all four search channels work.
- **Light mode**: only title, abstract and keywords. The citation channel is missing, so invite the author to paste 10–15 key references. Proceed without them if they decline, and say in the report that the shortlist rests on less evidence.

Settle three things before searching, in a single round of questions (use the ask_user_input tool where available):

1. Journal language scope for this manuscript: English only, English and French, or French only. Propose the manuscript's language as the default.
2. Hard constraints: an open-access mandate, a deadline (for instance an evaluation campaign), a maximum APC.
3. Journals to exclude (already rejected the paper, conflicts of interest). Ask this one in prose, since it needs free text.

If the author has already answered these or says "just run it", don't ask. Default to English plus the manuscript's language, no exclusions, no mandate.

### Phase 1 — Manuscript fingerprint

Extract, in a few words each: research question; core constructs; theoretical lens; method and design (e.g., PLS-SEM on a cross-sectional survey, n = 312; three-level meta-analysis; multiple-case study); empirical context (country, sector, firm size); level of analysis; contribution type (theory-testing, theory-building, methodological, review, practice-oriented); the scholarly community addressed (quality and operations management, innovation, entrepreneurship, HRM, IS, strategy…); five to eight keywords.

In full mode, tally the journals in the reference list. Journals cited three or more times, especially with recent articles, show which conversations the paper joins and are strong candidates.

Show the fingerprint in a few lines and continue. Stop and ask only if the paper could plausibly belong to two communities with different journal sets (say, an HRM home or an innovation home), because the answer changes everything downstream. Offering two sub-lists is also fine.

### Phase 2 — Candidate long list (25–40 journals)

Gather candidates through four channels and record which channel(s) produced each one; agreement across channels is itself a signal.

**A. Citation channel** (full mode): the journals heavily cited in the manuscript.

**B. Similar-papers channel**: 6–10 web searches, each from a different angle: construct pairs, construct + theory, construct + context, construct + method, the research question in plain words. See where closely related papers from the last five years appeared. For each journal, keep up to three of the closest papers (title, year, URL or DOI). They become the "papers to engage with" in the report, which helps the author show the editor that the manuscript joins the journal's own conversation.

**C. Special-issues channel**: search for open calls for papers on the topic (publisher sites such as Emerald, Elsevier, Wiley, Taylor & Francis, Springer and SAGE, plus journal sites). Keep only calls with a deadline after today; record title, deadline and URL. A well-fitting special issue is often the best way in, so flag it prominently.

**D. Field-knowledge channel**: add journals you know to be central to the community identified in Phase 1. These are seeds only. They go through the same checks as every other candidate, and nothing about them (rankings, scope, review times) is taken from memory.

When French-language journals are in scope, include francophone management journals relevant to the topic as seeds to verify, for example Revue Française de Gestion, M@n@gement, Management International, RIMHE, Finance Contrôle Stratégie, Gestion 2000, Revue Française de Gestion Industrielle, Innovations, Systèmes d'Information et Management.

Deduplicate (watch for renamed journals and hijacked clones) and drop obvious misfits with a one-line reason; they go to the Excluded sheet.

### Phase 3 — Fit screening

For each candidate, open the official aims-and-scope or author-guidelines page. Search first to surface the official URL (prefer the publisher's site), then fetch it. Score the five fit dimensions in `references/fit-rubric.md` (scope, conversation, method, context, contribution), each from 0 to 5, and write a one- or two-sentence rationale in your own words.

When the method is one that editors disagree about (PLS-SEM, single-source cross-sectional surveys, student samples, meta-analysis, qualitative work in quantitative-leaning journals), check the journal's stance: search for editorials or author-guideline passages on it. The Journal of Operations Management's 2015 editorial against PLS-SEM is the classic example of a stance that should push the method score down to 0–1.

Apply the gate: a fit below 3.0 sends the journal to Excluded, with the reason. From those that pass, keep the 12–15 strongest for deep verification. If many pass, keep a spread of prestige levels so that all three tiers can be filled.

### Phase 4 — Ranking verification

Follow `references/ranking-sources.md`. For each list it gives the current edition, where the official data sits, which secondary sources are acceptable, and how to record confidence:

- **O**: official list or database consulted in this run
- **S**: explicit secondary source naming the list and edition (publisher or journal page, university library list)
- **U**: not verified

Work efficiently. Open each consolidated official document once (for example the FNEGE 2025 list) and look up every candidate in it; harvest metrics already visible on the journal pages opened in Phase 3; then run targeted searches for the remaining gaps. Mark a journal "Not listed" only after checking the official full list (confidence O); otherwise it is "not verified". If the author has attached a ranking file in the conversation, treat it as an official source.

### Phase 5 — Practical profile

For each shortlisted journal, record what the journal or publisher reports, with the year: days from submission to first decision, acceptance rate, open-access model and APC (and whether the APC is mandatory), length limits, review model. Watch for signs of predatory or hijacked journals: a domain that doesn't match the publisher, promised acceptance within days, discontinued Scopus coverage, a homepage built around the APC. Exclude any journal that raises them, and say why.

### Phase 6 — Scoring and strategy

The Excel script computes the scores (see `references/data-schema.md`); you supply the inputs. Default weights are prestige 40%, fit 35%, speed 15%, APC 10%. The author can change them for a run ("this time speed matters most"; pass them in the JSON) or later in the workbook's Settings sheet, where every score recalculates.

Prestige is the weighted mean of the verified rankings, each mapped to a 0–5 scale (list weights: FNEGE 30%, AJG 25%, ABDC 20%, CNRS 10%, SJR quartile 10%, WoS quartile 5%). Unverified lists drop out of the mean instead of counting as zero. A verified "Not listed" counts as zero, because an unlisted journal doesn't count in the evaluation that list serves; the exception is CNRS, whose list dates from 2020, so absence there is left out of the mean rather than penalised. HCERES is shown but not scored, since it is derived from FNEGE and CNRS. Tiers follow prestige: Stretch ≥ 4.25, Target 3.0–4.24, Safe < 3.0.

Then build the submission cascade: usually one stretch journal (only if its fit is at least 4), two or three targets and one or two safe options, ordered so that reformatting between steps stays small (similar length limits and article structure). If a fitting special issue is open, place it where its deadline allows.

### Phase 7 — Deliverables

**1. Excel shortlist.** Read the xlsx skill's SKILL.md if it hasn't been read in this conversation. Write the JSON described in `references/data-schema.md` to `/home/claude/journal_data.json`, then run:

```bash
python <this-skill-dir>/scripts/build_shortlist.py /home/claude/journal_data.json /mnt/user-data/outputs/<short-title>_journal_shortlist.xlsx
```

The script applies the fit gate, orders the journals, writes live formulas, runs the xlsx skill's `recalc.py` and prints the result. Fix anything it reports (`errors_found`, or an `error` key), then share the file with present_files.

**2. Report in chat**, in the author's language (French or English), with this structure:

- **Manuscript fingerprint**: three to five lines.
- **Recommended strategy**: the cascade, with one sentence of rationale per step.
- **Journal profiles** for the top six to eight: why it fits (scope and conversation, in your own words); a rankings line such as "FNEGE 2025: 2 · AJG 2024: 3 · ABDC 2025: A · SJR Q1"; a practical line (time to first decision, APC, length); desk-rejection risks specific to this manuscript; two or three recent papers to engage with.
- **Open special issues** worth considering, with deadlines.
- **Verification notes**: editions used and which values remain unverified.
- A pointer to the Excel file for the full comparison, the sources and the adjustable weights.

Write the profiles as short prose rather than a wall of bullets; the Excel carries the tabular detail.

## Edge cases

- **After a rejection**: exclude the rejecting journal. If the author shares the decision letter or reviews, use them to adjust the fingerprint (for instance, reviewers judged the contribution practice-oriented, so practitioner-friendly journals deserve more weight).
- **Interdisciplinary papers**: offer two sub-lists, one per community.
- **Outside business and management**: the ranking lists lose relevance. Say so, and rely on SJR, WoS and fit.
- **No web access**: say that the skill depends on live search. Offer a preliminary list clearly labelled "unverified, from model knowledge, check before use", with every ranking cell left empty.
