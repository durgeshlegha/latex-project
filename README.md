# B.Tech. Thesis - LaTeX Source

**Title:** Assessment of Railroad Ballast Degradation under Modified
Drop-Weight Impact Loading Conditions and Image-Based Morphological Analysis

**Authors:** Durgesh Kumar Legha (2270007), Sandeep Patel (2280043)
**Supervisor:** Dr. Dinesh Gundavaram
**Institution:** Gati Shakti Vishwavidyalaya, Vadodara (April 2026)

## Build

```bash
pdflatex main.tex
pdflatex main.tex   # second pass for cross-references / ToC
pdflatex main.tex   # third pass (optional) for hyperref bookmarks
```

The compiled output is `main.pdf` (~83 pages).

## Project layout

```
.
├── main.tex                 # Master file: preamble + \include directives
├── chapters/
│   ├── 00_titlepage.tex
│   ├── 01_declarations.tex  # candidate / supervisor / approval certificates
│   ├── 02_acknowledgements.tex
│   ├── 03_abstract.tex
│   ├── 04_outcomes.tex      # journals, patents, conferences, QR
│   ├── 05_abbreviations.tex
│   ├── 06_symbols.tex
│   ├── 07_chapter1_introduction.tex
│   ├── 08_chapter2_literature.tex
│   ├── 09_chapter3_methodology.tex
│   ├── 10_chapter4_impact_results.tex
│   ├── 11_chapter5_morphology.tex
│   ├── 12_chapter6_conclusions.tex
│   ├── 13_references.tex
│   ├── 14_appendix_a.tex    # tabulated data excerpts
│   └── 15_appendix_b.tex    # Python morphological-analysis script
└── figures/                 # All 35 figures extracted from the Word source
```

## Required LaTeX packages

`geometry`, `lmodern`, `microtype`, `amsmath`, `mathtools`, `siunitx`,
`graphicx`, `booktabs`, `tabularx`, `longtable`, `multirow`, `adjustbox`,
`makecell`, `caption`, `subcaption`, `hyperref`, `cleveref`, `enumitem`,
`fancyhdr`, `xcolor`, `listings`, `titlesec`, `setspace`, `float`.

On Debian / Ubuntu these are provided by:
```bash
sudo apt-get install texlive-latex-base texlive-latex-recommended \
                     texlive-latex-extra texlive-fonts-recommended \
                     texlive-fonts-extra texlive-science lmodern
```

## Custom macros (defined in `main.tex`)

| Macro       | Renders          | Macro    | Renders            |
|-------------|------------------|----------|--------------------|
| `\FIIN`     | FI_IN            | `\Ke`    | K_e                |
| `\PoneM`    | P_{0.075}        | `\Vch`   | V_ch               |
| `\PtwoM`    | P_{20}           | `\Ach`   | A_ch               |
| `\Deq`      | D_eq             | `\dmax`  | d_max              |
| `\Ap`       | A_p              | `\dV`    | %ΔV                |
| `\Ab`       | A_b              | `\dPsi`  | %ΔΨ                |
| `\dC`       | %ΔC              | `\DegC`  | °C                 |

## Notes

* All units use `siunitx` for consistent typography
  (`\SI{20}{\milli\metre}`, `\SIrange{275}{523}{\kilo\pascal}`, etc.).
* All in-text equations and display equations use `amsmath` environments.
* All cross-references are labelled (`\label{...}`) and can be referenced
  with `\cref{...}`/`\Cref{...}` via the `cleveref` package.
* The Python listing in Appendix B uses the `listings` package with
  syntax highlighting.
