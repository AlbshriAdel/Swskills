# PLOS ONE LaTeX Template — Notes

**Fetched:** 2026-05-06

## Where to get the template

- **Official PLOS download page:** https://journals.plos.org/plosone/s/latex
- **Overleaf (zero-install, recommended):** https://www.overleaf.com/latex/templates/latex-template-for-plos-public-library-of-science-articles/wdmgcwzgvhnn

The PLOS-supplied zip contains:
- `plos_latex_template.tex` — main template skeleton
- `plos2015.bst` — BibTeX style for PLOS numbered references
- A short README describing required macros

> Note: this environment could not download the zip directly (PLOS's CDN returned 403 for the WebFetch client). Pull the template manually from Overleaf or the official URL above when you start writing.

## Required document class and packages

The template uses `article` document class with PLOS-specific macros and the following common packages: `amsmath`, `amssymb`, `graphicx`, `hyperref`, `cite`, `caption`, `microtype`. Do not change the document class.

## Submission rules specific to LaTeX

1. **Single `.tex` file.** If your manuscript is split across multiple `.tex` files during writing, concatenate them into one for final submission.
2. **No LaTeX-generated EPS for figures.** Vector EPS produced by LaTeX (psfrag, pgfplots EPS export, etc.) is rejected by PLOS production. Export figures from Adobe Illustrator or Inkscape (free) instead. Raster figures: TIFF 300–600 dpi.
3. **Bibliography:** use `\bibliographystyle{plos2015}` and a single `.bib` file. Numbered citations in square brackets via standard `\cite{}`.
4. **Figure captions:** each `\caption{}` begins with a bold short title, followed by the legend text. Figure label "Fig X" — use `\renewcommand{\figurename}{Fig}` if not already set in template.
5. **Mandatory statements:** Data Availability, Funding, Competing Interests, Author Contributions (CRediT), and Ethics statements live in the **submission system fields**, not in the `.tex` file. The manuscript file may include a brief mirror of the Data Availability and Ethics statements; financial disclosure should NOT appear in the manuscript file.
6. **Title:** ≤ 250 characters, sentence case.
7. **Short title:** entered in submission system (not in `.tex`), ≤ 50 characters.
8. **Abstract:** ≤ 300 words, single paragraph, no citations.

## Skeleton (for reference, simplified)

```latex
\documentclass[10pt,letterpaper]{article}
\usepackage[top=0.85in,left=2.75in,footskip=0.75in]{geometry}
\usepackage{amsmath,amssymb,graphicx,cite,hyperref}

\renewcommand{\figurename}{Fig}

\begin{document}

\title{Title in sentence case, $\le$250 characters}
\author{First Author$^{1}$, Second Author$^{1,2}$, \ldots}
\date{}
\maketitle

\section*{Abstract}
% $\le$300 words, single paragraph, no citations

\section*{Introduction}

\section*{Materials and methods}

\section*{Results}

\section*{Discussion}

\section*{Acknowledgments}

\bibliographystyle{plos2015}
\bibliography{refs}

\end{document}
```

## Verification checklist before submission

- [ ] Single `.tex` file.
- [ ] Title ≤ 250 characters; short title supplied separately ≤ 50 characters.
- [ ] Abstract ≤ 300 words; no citations in abstract.
- [ ] Numbered references using `plos2015.bst`; DOIs included where available.
- [ ] Figures are TIFF 300–600 dpi or EPS exported from Illustrator/Inkscape (NOT LaTeX-generated EPS).
- [ ] Figures cited as "Fig 1" etc.; figure legends placed after References.
- [ ] Tables editable, after figure legends.
- [ ] Data Availability Statement entered in submission system.
- [ ] Funding statement entered (with verbatim "no specific funding" sentence if unfunded).
- [ ] Competing Interests statement entered.
- [ ] CRediT roles assigned to every author.
- [ ] Ethics approval documents uploaded if human / animal research.
- [ ] AI-use disclosure added to Methods sub-section if any AI tool was used.
- [ ] Reporting checklist (CONSORT / PRISMA / ARRIVE / STROBE / etc.) attached as Supporting Information if applicable.
