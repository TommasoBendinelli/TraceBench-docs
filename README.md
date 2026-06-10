# tsENV Docs

LaTeX-based documentation and paper material for tsENV.

## Structure

- `manual/src/` contains source `.tex` documents.
- `manual/docs_order_manifest.txt` lists the render order for documents in
  `manual/src/`.
- `manual/support/` provides shared document styling.
- `render_all_pdf.sh` compiles documents into `pdf/`.
- `build/` contains temporary LaTeX build files and is ignored by Git.
- `pdf/` contains rendered PDFs and is ignored by Git except for `.gitkeep`.

## Usage

Render documentation from this repository root:

```sh
./render_all_pdf.sh [--combine] [--sync_to_drive]
```

Each PDF is written as `project_name_tex_file_name.pdf`, where the project name
is the folder name after `docs-`. Combined outputs use the same project-name
prefix.

With `--combine`, the script builds the combined manual PDFs. With
`--sync_to_drive`, it updates only existing built PDFs in
`My Drive/android_pdf`; missing Drive files are skipped, and replacing an
existing file updates its Google Drive version history.

Force a clean rebuild:

```sh
./render_all_pdf.sh --force
```

The script requires `latexmk`, `pdflatex`, and a LaTeX installation with the
packages used by `manual/support/`. Creating combined PDFs with `--combine` also
requires Ghostscript (`gs`).
