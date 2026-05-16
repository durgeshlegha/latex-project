# B.Tech. Thesis - LaTeX Source

**Title:** Assessment of Railroad Ballast Degradation under Modified
Drop-Weight Impact Loading Conditions and Image-Based Morphological Analysis

**Authors:** Durgesh Kumar Legha (2270007), Sandeep Patel (2280043)
**Supervisor:** Dr. Dinesh Gundavaram
**Institution:** Gati Shakti Vishwavidyalaya, Vadodara (April 2026)

The compiled output is `main.pdf` (~85 pages, colour-themed, fully
cross-referenced and hyperlinked).

## Build

The thesis uses BibTeX for references and `makeglossaries` for the
abbreviations list, so the build runs in five steps:

```bash
pdflatex  main.tex
bibtex    main
makeglossaries main
pdflatex  main.tex
pdflatex  main.tex      # final pass for hyperref / cross-references
```

Or, with `latexmk` (recommended):

```bash
latexmk -pdf -bibtex -shell-escape main.tex
```

## Project layout

```
.
├── main.tex                  # Master file: preamble + \include directives
├── references.bib            # BibTeX bibliography database
├── chapters/
│   ├── glossary.tex          # Acronym definitions (used by \gls / \acrshort)
│   ├── 00_titlepage.tex
│   ├── 01_declarations.tex   # candidate / supervisor / approval certificates
│   ├── 02_acknowledgements.tex
│   ├── 03_abstract.tex
│   ├── 04_outcomes.tex       # journals, patents, conferences, QR
│   ├── 05_abbreviations.tex  # auto-generated via \printglossary
│   ├── 06_symbols.tex
│   ├── 07_chapter1_introduction.tex
│   ├── 08_chapter2_literature.tex
│   ├── 09_chapter3_methodology.tex
│   ├── 10_chapter4_impact_results.tex
│   ├── 11_chapter5_morphology.tex
│   ├── 12_chapter6_conclusions.tex
│   ├── 13_references.tex     # placeholder (bibliography emitted from main.tex)
│   ├── 14_appendix_a.tex     # tabulated data excerpts
│   └── 15_appendix_b.tex     # Python morphological-analysis script
└── figures/                  # 35 figures extracted from the original Word source
```

## Required LaTeX packages

`geometry`, `lmodern`, `microtype`, `setspace`,
`amsmath`, `mathtools`, `siunitx`,
`graphicx`, `float`, `booktabs`, `tabularx`, `longtable`, `multirow`,
`adjustbox`, `makecell`, `xcolor` (with `table` option), `caption`,
`subcaption`,
`hyperref`, `cleveref`, `natbib`, `glossaries`,
`enumitem`, `fancyhdr`, `listings`, `titlesec`,
`tcolorbox` (with `most` library), `tikz`.

On Debian / Ubuntu these are provided by:

```bash
sudo apt-get install texlive-latex-base texlive-latex-recommended \
                     texlive-latex-extra texlive-fonts-recommended \
                     texlive-fonts-extra texlive-science \
                     lmodern texlive-bibtex-extra
```

## Highlights of this LaTeX version

### Content fixes vs. the original Word document

* **Canonical T1-T9 mapping** consistent across all chapters and
  Appendix A. The mapping follows Appendix A.1 (the laboratory record):
  T1 = PUBM-FB-300, T2 = RUBM-FB-300, T3 = UR-FB-300, T4 = UR-RB-300,
  T5 = RUBM-RB-450, T6 = PUBM-RB-450, T7 = UR-RB-450, T8 = RUBM-RB-300,
  T9 = PUBM-RB-300.
* **Removed impossible labels** in Chapter 4 (T2 "RUBM-FB-450" and
  T4 "UR-RB-450" -> corrected to RUBM-FB-300 and UR-RB-300; the
  FB+450 cells are explicitly excluded by the experimental design).
* **Corrected ranking analysis** in Section 4.3.2 -- the original claim
  that "the same ranking holds" at low energy on the rigid base is
  arithmetically wrong (T9 PUBM 0.972% > T8 RUBM 0.667%). The thesis
  now reports the actual finding: pad performance is energy- and
  base-dependent, and PUBM is not uniformly the best mat.
* **Renumbered duplicate Figure 3.15** in the original to 3.16.
* **Added missing Section 1.3** (the original jumped from 1.2 to 1.4).

### Structural improvements

* **`siunitx` units throughout** (`\SI{275}{\kilo\pascal}`,
  `\SIrange{20}{65}{\milli\metre}` etc.)~--- consistent thin-space
  behaviour and non-break units.
* **Chapter-prefixed equation, figure, and table numbering**
  (Eq. 3.4, Fig. 4.2, Table 5.1, ...).
* **Custom macros** for repeated symbols
  (`\FIIN`, `\PoneM`, `\PtwoM`, `\Ke`, `\Vch`, etc.) so that subscripts
  remain typographically identical wherever they appear.
* **`siunitx` test-label macro** `\testlabel{T7}` for sans-serif test
  identifiers.
* **`natbib` author-year citations** (`\citep{Selig1994}`,
  `\citet{Nimbalkar2012}`) replacing all inline `(Author, Year)`
  strings. The bibliography is auto-sorted and de-duplicated.
* **`glossaries` package** with `\gls{...}` and `\acrshort{...}` for
  acronyms -- automatic full-form on first use, abbreviated thereafter,
  hyperlinked to the List of Abbreviations.
* **`cleveref` cross-references** (`\cref{tab:imp-FIIN}`,
  `\Cref{fig:morph-sphericity}`) that auto-prefix with "Table" / "Figure"
  / "Section" etc.
* **Colour-themed tables** with blue header rows and zebra-striped
  body rows (GSV-blue palette).
* **Decorative chapter headings** -- "CHAPTER N" label paired with
  a large blue chapter title.

### Custom semantic boxes

Four `tcolorbox` environments visually distinguish four kinds of
emphasis in the body text:

| Environment    | Colour | Purpose                                  |
|----------------|--------|------------------------------------------|
| `finding`      | Blue   | Key findings, conclusions                |
| `mechanism`    | Green  | Mechanistic explanations                 |
| `caveat`       | Red    | Limitations, things to be careful about  |
| `thesisnote`   | Purple | Side observations, clarifying notes      |

### Custom symbol macros

| Macro       | Renders       | Macro    | Renders        |
|-------------|---------------|----------|----------------|
| `\FIIN`     | FI_IN         | `\Ke`    | K_e            |
| `\PoneM`    | P_{0.075}     | `\Vch`   | V_ch           |
| `\PtwoM`    | P_{20}        | `\Ach`   | A_ch           |
| `\Deq`      | D_eq          | `\dmax`  | d_max          |
| `\Ap`       | A_p           | `\dV`    | %ΔV            |
| `\Ab`       | A_b           | `\dPsi`  | %ΔΨ            |
| `\dC`       | %ΔC           | `\DegC`  | °C             |

## Notes

* All in-text equations and display equations use `amsmath` environments.
* All cross-references are labelled and clickable.
* The Python listing in Appendix B uses the `listings` package with
  syntax highlighting.
* The bibliography is in `references.bib` and uses `plainnat`
  (alphabetical author--year). Re-style by changing the
  `\bibliographystyle{...}` line in `main.tex` to e.g. `unsrtnat` or
  `chicago`.
