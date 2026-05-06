# Voc-6G — PLOS ONE Submission Notes

These notes track everything that still needs the author's attention before
submission and document what was changed mechanically.

## What changed (mechanical)

- **Preamble.** Added `\usepackage{tikz}` + `\usetikzlibrary{arrows.meta,positioning}`
  (used by Fig 1) and `\usepackage{booktabs}` (used by every table).
  Defined `\providecommand{\VocSixG}{Voc-6G}` so the manuscript compiles.
- **Title.** Filled in from the IEEE draft: *"Voc-6G: a CyberTwin-enabled
  intelligent task migration framework for 6G mmWave vehicular edge computing."*
  Sentence case, well under the 250-character cap.
- **Author block.** Reduced to a placeholder skeleton (3 slots and 1 affiliation)
  marked `[Author One] / [Department] / [corresponding.author@institution.edu]`.
  **You must fill these in before submission.** The IEEE source has the same
  block as anonymous, so no real names were available to carry over.
- **Author Summary.** Deleted. PLOS ONE explicitly does not accept this section.
- **Section formatting.** All `\section{}` and `\subsection{}` switched to the
  starred form (`\section*{}` / `\subsection*{}`) per the PLOS template style.
- **Section names.** "System Architecture" → "Materials and methods".
  "Implementation Details" → "Implementation details".
  "Experimental Evaluation" → "Results". "Related Work" → "Related work".
- **Cross-references.** Replaced 5 broken `Section~\ref{sec:*}` calls (which
  no longer resolve to numbers because the sections are unnumbered) with
  `\nameref{...}`-based references.
- **Roadmap paragraph** at the end of the introduction rewritten to drop
  numbered section pointers.
- **Figure references.** `Fig.~\ref{...}` → `Fig~\ref{...}` (PLOS uses
  `Fig 1`, no period, in body text).
- **Bibliography.** `\bibliography{Paper-Latex/references_v2}` →
  `\bibliography{references_v2}` so BibTeX resolves when the manuscript is
  compiled from the directory containing the `.tex` file.
- **Hard-coded ref.** `Table~IV` → `Table~\ref{tab:main_results}`.
- **Broken ref.** `Appendix Table~\ref{tab:mcnemar}` (no such table) replaced
  with neutral wording ("summarized below").
- **Acknowledgments / Author contributions / Funding / Competing interests /
  Data availability / Use of generative AI tools** sections all added in
  template form before the bibliography.
- **Humanizer pass** applied to prose to remove AI-style vocabulary (see the
  agent CHANGELOG that follows this file in the next commit).

## What you still need to do

### High priority — required for submission

1. **Author block** (`paper/plos.tex` ~line 180): fill in real names,
   affiliations, ORCID iDs (recommended), and the corresponding-author email.
2. **Author contributions** section: replace the `[Author One/Two/Three]` CRediT
   roles with one row per author and the actual roles each played.
3. **Funding statement**: keep the verbatim "no specific funding" sentence
   only if true; otherwise list each funder + grant number + funder role.
4. **Competing interests**: confirm or amend.
5. **Data availability statement**: insert the real DOI / accession number
   for the CyberTwin dataset and any model checkpoints. PLOS will reject
   without this. Recommended public repositories: Zenodo, figshare, OSF,
   Dryad, or a permanent-tagged GitHub release.
6. **Generative AI disclosure**: replace the placeholder with either
   (a) the negative declaration ("No generative AI tools were used …") or
   (b) a description of what tool was used, how, validated how, and what
   was affected. PLOS requires one of these.
7. **Acknowledgments**: list any people / facilities / software not covered
   by the formal credits.

### Medium priority — strongly recommended

8. **DOIs in the bibliography.** All 49 entries in `references_v2.bib`
   currently lack `doi = {...}` fields. PLOS strongly recommends DOIs.
   Quickest path: run the bib through https://doi.crossref.org/simpleTextQuery
   or use the [`doi2bib`](https://www.doi2bib.org/) service.
9. **Ethics statement.** This study uses CyberTwin-simulated and CRAWDAD
   public data — no human subjects and no animal research, so no IRB/IACUC
   statement is required. If you re-run any experiment with human or animal
   data, add an ethics statement.

### Low priority — production / acceptance

10. **Figures.** All 12 PNGs are at the resolutions below. PLOS accepts PNG
    at submission, but production requires **TIFF (300–600 dpi) or vector
    EPS** for accepted manuscripts. Plan to regenerate from the source
    (matplotlib `savefig(dpi=600, format="tiff")` or export from
    Illustrator/Inkscape as EPS — **not** LaTeX-generated EPS).

    | File | Pixels | Notes |
    |---|---|---|
    | `architecture.png` | 800 × 400 | Orphan; the `.tex` uses TikZ for Fig 1 |
    | `fig_model_comparison.png` | 3175 × 1173 | OK |
    | `fig_radar.png` | 1739 × 1364 | OK |
    | `fig_cql_comparison.png` | 2774 × 974 | OK |
    | `fig_multiseed.png` | 2774 × 974 | OK |
    | `fig_confusion_matrices.png` | 2957 × 1974 | OK |
    | `fig_fpr_fnr.png` | 2374 × 973 | OK |
    | `fig_variants.png` | 1975 × 974 | OK |
    | `fig_federated_convergence.png` | 1973 × 974 | OK |
    | `fig_per_method_success.png` | 2374 × 974 | OK |
    | `fig_lstm_predictions.png` | 1974 × 1974 | OK |
    | `fig_latency_success.png` | 2573 × 974 | OK |

    Width budget at PLOS: single column ≤13.2 cm, 1.5-column ≤19.05 cm.

11. **Reporting checklist.** This is an ML benchmark study, so no CONSORT/
    PRISMA/STROBE/ARRIVE applies. Reviewers may request the **TRIPOD-AI**
    checklist (predictive ML reporting). Optional, not mandatory.

## How to compile

From `/home/user/Swskills/paper/`:

```bash
pdflatex plos.tex
bibtex plos
pdflatex plos.tex
pdflatex plos.tex
```

The repo doesn't have a TeX engine installed, so I couldn't verify the
compile here. If you hit a missing-package error, install texlive-pictures
(for tikz) and texlive-publishers (for booktabs).

## Files

- `paper/plos.tex` — manuscript (the file you submit)
- `paper/references_v2.bib` — bibliography (49 entries)
- `paper/plos2025.bst` — PLOS BibTeX style
- `paper/figs/` — 12 PNG figures (regenerate as TIFF/EPS for production)
- `paper/IEEEtran.cls` — unused for the PLOS build (kept for the IEEE draft)
- `paper/voc6g_paper_v2.tex` — IEEE draft (kept for reference)
- `writing_outputs/plos-one-research-article/journal/` — journal-intelligence
  outputs (`journal_profile.yaml`, `ai_policy.md`, etc.)
