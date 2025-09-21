# EPFL LSE Master Thesis Template
This repository provides a **LaTeX template** specifically designed for **Master’s students in Life Sciences Engineering (LSE)** at EPFL.


⚠️ Note: This is *not* an official EPFL template, but a community resource. Always confirm any mandatory formatting rules with your supervisor or section.

---

## Preview

You can view the compiled sample PDF of this template here:

[View `main.pdf`](./main.pdf)

## How to build the PDF
You have two simple options to compile `main.tex` into `main.pdf`.

### Option 1 — Overleaf (no install)
1. Click the green “Code” button in this repo and choose “Download ZIP”.
2. Go to [Overleaf](https://www.overleaf.com), create a new project, and “Upload Project”.
3. Upload the ZIP of this repository.
4. Overleaf will compile automatically. If not, click “Recompile”.

### Did you know? GitHub + Overleaf

> Did you know? You can save your code in a GitHub repository like this one and import your repo directly into Overleaf. 
> After that, in Overleaf, you can also push your changes or pull new changes from GitHub manually. 
> So if you'd like, you can just fork this repo to get started.
> P.S. This requires Overleaf Pro, available for free for EPFL students by creating your account with your EPFL email.

### Option 2 — Local build (VS Code or any IDE)

#### Quickstart
Pick your OS and paste the commands into a terminal. This installs LaTeX + biber and clones the repo.

Windows (PowerShell):
```powershell
# Install MiKTeX (includes biber), Git, and VS Code using winget
winget install -e --id MiKTeX.MiKTeX
winget install -e --id Git.Git
winget install -e --id Microsoft.VisualStudioCode

# Clone the repository
git clone https://github.com/Rayjine/epfl-lse-master-thesis-template.git
cd epfl-lse-master-thesis-template

# Open in VS Code (or open VS Code and File → Open Folder…)
code .
```

macOS (Terminal with Homebrew):
```bash
# Install MacTeX (TeX Live for macOS) without GUI apps
brew install --cask mactex-no-gui

# Ensure core packages are present (biber, biblatex, Nature style, latexmk)
sudo tlmgr update --self
sudo tlmgr install biber biblatex biblatex-contrib latexmk csvsimple

# Install Git and (optionally) VS Code
brew install git
brew install --cask visual-studio-code

# Clone the repository and open in VS Code
git clone https://github.com/Rayjine/epfl-lse-master-thesis-template.git
cd epfl-lse-master-thesis-template
code .
```

Ubuntu/Debian:
```bash
sudo apt update
sudo apt install -y texlive texlive-latex-extra texlive-biblatex-extra biber latexmk git
git clone https://github.com/Rayjine/epfl-lse-master-thesis-template.git
cd epfl-lse-master-thesis-template
```

Fedora:
```bash
sudo dnf install -y texlive-scheme-medium texlive-biblatex texlive-biblatex-nature texlive-csvsimple biber latexmk git
git clone https://github.com/Rayjine/epfl-lse-master-thesis-template.git
cd epfl-lse-master-thesis-template
```

Arch:
```bash
sudo pacman -S --needed texlive-most texlive-latexextra biber latexmk git
# If the 'nature' style is missing on your TeX Live installation:
sudo pacman -S texlive-bibtexextra
git clone https://github.com/Rayjine/epfl-lse-master-thesis-template.git
cd epfl-lse-master-thesis-template
```

Note: If your distribution splits TeX packages differently and `biber` or the `nature` style is still missing after the quickstart commands, install them via your package manager (e.g., `texlive-bibtexextra` on Arch).

#### Build in VS Code (LaTeX Workshop)
1. Install the VS Code extension “LaTeX Workshop” (by James Yu):
   - VS Code → Extensions (Ctrl+Shift+X) → search “LaTeX Workshop” → Install
   - Or via Command Palette (Ctrl+Shift+P): “Extensions: Install Extensions” and search
2. Open the repository folder in VS Code (File → Open Folder… or `code .`).
3. Build the PDF:
   - Click the TeX icon in the Activity Bar → “Build LaTeX project”, or
   - Press Ctrl+Alt+B, or
   - Command Palette (Ctrl+Shift+P) → “LaTeX Workshop: Build LaTeX project”.
4. View the PDF:
   - LaTeX Workshop opens the PDF in a built‑in viewer, and `main.pdf` is also saved at the project root.

### Alternative — Docker (no local install)
If you have Docker:
```bash
docker run --rm -v "$PWD":/workdir -w /workdir texlive/texlive \
  latexmk -pdf -interaction=nonstopmode -halt-on-error main.tex
```

## Project layout

```
epfl-lse-master-thesis-template/
├─ figures/                  # images (e.g., logo, cell example)
├─ sections/                 # chapter files (introduction, methods, ...)
├─ main.tex                  # entry point for compilation
├─ frontpage.tex             # title page
├─ bibliography.bib          # references database
├─ .gitignore                # ignores LaTeX build artifacts
└─ README.md
```

## Bibliography
This template uses `biblatex` with `backend=biber` and `style=nature` by default. To cite, add entries in `bibliography.bib` and reference them with `\parencite{key}`.

## Cleaning build artifacts
You can clean intermediates with:
```bash
latexmk -C
```
This repository includes a `.gitignore` to avoid committing LaTeX intermediates.

## Troubleshooting
* **Missing packages**: Use your OS package manager to install missing TeX packages or switch to the Docker build.
* **Empty bibliography**: Ensure you have at least one `\cite{...}` that exists in `bibliography.bib`, then rerun the build (or `latexmk`).
* **Figure not found**: Check the relative path (e.g., `figures/cell.png`) and that the file exists.
* **Float placement warnings**: These are usually harmless. Use `[htbp]` placement specifiers to give LaTeX more flexibility.

---

If you have suggestions or find issues, feel free to open an issue or PR.
