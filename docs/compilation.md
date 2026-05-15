# Compilation Guide

After the extension generates a `diff_<old>_to_<new>_<file>.tex`, compile it with any standard LaTeX engine.

## Using `pdflatex` (Most Common)

```bash
cd /path/to/your/project
pdflatex diff_old_to_new_file.tex
open diff_old_to_new_file.pdf   # macOS
# xdg-open diff_old_to_new_file.pdf  # Linux
```

## Using `xelatex` (Unicode Support)

```bash
xelatex diff_old_to_new_file.tex
```

Use `xelatex` if your document contains non-ASCII characters or uses Unicode fonts.

## Using `lualatex` (Modern Alternative)

```bash
lualatex diff_old_to_new_file.tex
```

## Matching Your Journal Template

To make the compiled PDF mirror your journal's fonts and spacing:

```bash
pdflatex -jobname=tracked-change "\input{diff_old_to_new_file.tex}"
```

This compiles the diff using the same preamble processing path, so custom macros and fonts match your main document.

## What's in the Diff File?

The generated `.tex` contains:

- Original content with **deletions** marked: `\textcolor{red}{\sout{deleted text}}`
- New content with **additions** marked: `\textcolor{blue}{added text}`
- All preamble, packages, and macros from the original files
- Compilable as-is; no additional dependencies beyond TeX Live/MacTeX

## Resolving Compilation Errors

| Error | Solution |
|---|---|
| Missing packages | The diff inherits packages from your original `.tex`. Install missing packages via `tlmgr` or your TeX distribution manager. |
| Encoding issues | Try `xelatex` or add `\usepackage[utf8]{inputenc}` to the preamble. |
| Large files / memory errors | Increase TeX memory: `pdflatex -interaction=nonstopmode diff_....tex` |
| `\sout` undefined | Add `\usepackage{soul}` or `\usepackage{ulem}` to the preamble of the diff file. |
| Bibliography errors | Run `bibtex diff_....aux` between `pdflatex` passes if the diff includes `\cite` commands. |

## Auto-Preview with LaTeX Workshop

If you have the [LaTeX Workshop](https://marketplace.visualstudio.com/items?itemName=James-Yu.latex-workshop) extension installed, open the generated diff `.tex` in VS Code and it will compile and preview automatically.
