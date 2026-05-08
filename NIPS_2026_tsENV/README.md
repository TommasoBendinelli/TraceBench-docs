# NIPS_2026_tsENV

This directory now contains a complete NeurIPS-style manuscript for `tsENV`, ported from `overleaf_paper/main.tex` and adapted to the local `neurips_2023` template.

Structure:

- `main.tex`: NeurIPS entrypoint
- `abstract_intro.tex`: abstract and introduction
- `related_work.tex`: related work section
- `benchmark_overview.tex`: benchmark overview and construction
- `experiments.tex`: experimental setup, results, conclusion, and impact statement
- `appendix.tex`: manuscript appendix aggregator that includes the shared appendix sources from `../`
- `nips_layout_config.tex`: generated margin override config written by `build.sh`
- `references.bib`: local bibliography copied from the Overleaf paper
- `plots/`, `tables/`, `pictures/`: local assets required by the manuscript

Build from this directory with:

```bash
./build.sh
```

Optional padding overrides:

```bash
./build.sh --left-padding -25mm --right-padding +25mm
```

The build script writes `nips_layout_config.tex` with the requested left/right padding, then builds the manuscript with explicit `pdflatex` / `bibtex` passes. The manuscript appendix is self-contained in this directory through local appendix source copies included by `appendix.tex`.

The script remains the supported entrypoint:

```bash
./build.sh --left-padding -25mm --right-padding +25mm
```

The build script outputs:

- `main.pdf`

Notes:

- The folder name follows the requested `NIPS_2026_tsENV` naming.
- The official NeurIPS 2026 author kit was not publicly available in this repository context when the scaffold was created, so this paper continues to use the locally vendored `neurips_2023` style file with the active conference metadata patched to NeurIPS 2026.
- The manuscript is self-contained within this directory for LaTeX sources, bibliography, and referenced assets.
- The Overleaf sync checkout is `overleaf_paper/`, with remote `https://git@git.overleaf.com/69f25cd14bb6afbfe9c86435`.
