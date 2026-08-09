# COMETES - Team Project Report

This repository contains the LaTeX source files and build configuration for the **COMETES** team project report submitted as part of the Automotive Systems Master (ASM) program at Hochschule Esslingen in collaboration with ISAE-Supméca Paris.

## Project Overview

- **Project Name:** COMETES
- **Degree Program:** Automotive Systems Master (ASM)
- **Institution:** Hochschule Esslingen (Mobilität und Technik) & ISAE-Supméca (Institut Supérieur de Mécanique de Paris)
- **Time Period:** Summer Semester 2026 (March 2026 – August 2026)
- **Authors:** Annika Geiger, David Jung, Yanis Medjamia
- **Examiners:** Prof. Georg Mallebrein (First Examiner), Prof. Mathias Oberhauser (Second Examiner)
- **Partner University Representative:** Régis Plateaux

---

## Directory Structure

```text
project_report/
├── .github/
│   └── workflows/
│       └── build-latex.yml
├── .gitignore
├── .latexmkrc
├── README.md
├── WINDOWS_SETUP.md
├── bib/
│   └── bib.bib
├── chappers/
├── chapters/
│   ├── ch-aa-titel.tex
│   ├── ch-aa-vorspiel.tex
│   ├── ch-aa-zusfasg.tex
│   ├── ch-einleitung.tex
│   ├── ch-hauptteil.tex
│   ├── ch-schluss.tex
│   ├── ch-zz-anhang.tex
│   ├── ch-zz-bibEinfach.tex
│   ├── controller-and-simulation.tex
│   └── test.tex
├── fig/
│   ├── aa-titel/
│   │   ├── Bosch_4C_S.eps
│   │   ├── Bosch_4C_S.pdf
│   │   ├── HE_Logo_4c.eps
│   │   └── HE_Logo_4c.pdf
│   └── controller/
│       ├── Full_model.png
│       ├── PI_Speed_Controller.png
│       ├── P_Position_Controller.png
│       ├── cascaded_position_speed_pid.jpg
│       ├── motor_model.png
│       └── transmission_model.png
├── main.pdf
├── main.tex
└── preamble/
    ├── pre-class.tex
    ├── pre-hyphenation.tex
    ├── pre-newcommands.tex
    ├── pre-packages.tex
    ├── pre-tablecommands.tex
    ├── pre-tablesettings.tex
    └── pre-work.tex
```

---

## Document State Overview

- **Root Entry Document:** `main.tex`
- **PDF Build Status:** `main.pdf` built (1802.5 KB, last modified 2026-08-09 20:16:30)
- **Active Chapters Included (6 total):**
  - `ch-aa-titel.tex`: 43 lines, ~57 words
  - `ch-aa-zusfasg.tex` - *Brief Summary*: 13 lines, ~365 words
  - `ch-einleitung.tex` - *Introduction*: 37 lines, ~227 words
  - `controller-and-simulation.tex` - *Controller, Actuation and Simulation 	extbf{David Jung*: 446 lines, ~2822 words
  - `ch-schluss.tex` - *Conclusion*: 3 lines, ~7 words
  - `ch-zz-anhang.tex` - *Appendix chapter*: 4 lines, ~18 words
- **Total Source Metrics (Active Chapters):** ~546 lines / ~3496 words
- **Graphic Assets:** 10 files in `fig/`
- **Commented / Inactive Chapters:** `ch-hauptteil.tex`
- **Last Automated Structure Update:** 2026-08-09 20:16:49

---

## Compilation Instructions

### Quick Start (Linux / macOS / WSL)

The document is built from the main entry file [main.tex](main.tex).

Using `latexmk` (recommended):
```bash
latexmk -pdf main.tex
```

Using `pdflatex` directly:
```bash
pdflatex main.tex
pdflatex main.tex
```
*(Multiple passes are required to resolve cross-references, table of contents, and figure/table lists.)*

### Windows Setup

For detailed instructions on setting up TeX Live or MiKTeX on Windows and configuring VS Code with LaTeX Workshop, see [WINDOWS_SETUP.md](WINDOWS_SETUP.md).

---

## Document Settings & Encoding

- **Root Document:** Always compile from [main.tex](main.tex), not individual chapter files.
- **Encoding:** Files use `ISO-8859-1` (Latin1) encoding as specified in `preamble/pre-packages.tex`. Ensure editor settings maintain this encoding unless migrating the full repository.
- **Bibliography:** The report currently uses the simple inline bibliography in `chapters/ch-zz-bibEinfach.tex`. If switching to BibTeX (`bib/bib.bib`), enable the bibliography line in `main.tex` and run `bibtex`.

---

## License & Citation

This report is part of academic coursework for the Automotive Systems Master's program at Hochschule Esslingen and ISAE-Supméca. All rights reserved.
