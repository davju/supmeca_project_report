# Windows setup for compiling this project

This project is a LaTeX document rooted at [main.tex](main.tex). The current build metadata shows it compiles with `pdflatex`, and the document is set up as a KOMA-Script `scrbook` project with several common LaTeX packages.

## 1. Install a TeX distribution

Use one of these on Windows:

- **MiKTeX** if you want packages to install automatically when they are missing.
- **TeX Live** if you want a fuller offline installation.

Make sure the following tools are available on your PATH after installation:

- `pdflatex`
- `latexmk` (recommended)
- `bibtex` if you later enable the bibliography block in the source

## 2. Open the project at the repository root

Open the folder that contains [main.tex](main.tex). Do not open a chapter file directly, because the root document pulls in the preamble and chapter files from relative paths.

The main include structure is:

- [main.tex](main.tex)
- [preamble/pre-class.tex](preamble/pre-class.tex)
- [preamble/pre-packages.tex](preamble/pre-packages.tex)
- [preamble/pre-work.tex](preamble/pre-work.tex)
- files under [chapters/](chapters/)

## 3. Compile from the root file

From PowerShell or the TeX distribution shell, run:

```powershell
latexmk -pdf main.tex
```

If `latexmk` is not available, compile manually with `pdflatex`:

```powershell
pdflatex main.tex
pdflatex main.tex
pdflatex main.tex
```

Running it multiple times is normal because the table of contents, figure list, table list, and cross-references need extra passes.

## 4. Use the correct encoding

The source files are configured for **Latin1 / ISO-8859-1** input in [preamble/pre-packages.tex](preamble/pre-packages.tex). That means:

- Keep the `.tex` files in the same encoding they already use.
- If your editor saves files as UTF-8 by default, do not convert only part of the project.
- If you plan to migrate the project to UTF-8 later, convert the whole source tree consistently and then update the input encoding setting.

## 5. If package errors appear

The document depends on standard packages such as KOMA-Script, `babel` with German support, `hyperref`, `csquotes`, `mathtools`, `lmodern`, and table/figure packages.

If Windows reports a missing package:

- In MiKTeX, allow on-demand package installation.
- In TeX Live, install the missing package through TeX Live Manager.

## 6. Bibliography note

The project currently uses a simple bibliography block in [chapters/ch-zz-bibEinfach.tex](chapters/ch-zz-bibEinfach.tex). The BibTeX-based bibliography line in [main.tex](main.tex) is commented out.

That means the default build does **not** require BibTeX.

If you uncomment the BibTeX bibliography later, you will need to run `bibtex` as part of the build.

## 7. Common Windows pitfalls

- Compile from the project root so relative image and chapter paths resolve correctly.
- Do not rename the `chapters/`, `preamble/`, `fig/`, or `bib/` folders unless you update the `\input` and `\include` paths.
- If you see font or package warnings, use a fuller TeX installation rather than a minimal one.
- If line endings or encoding are changed by Windows tooling, verify that the document still compiles before continuing edits.

## 8. Recommended VS Code setup

If you use VS Code on Windows, LaTeX Workshop is the simplest way to build this project.

### Install the extension

1. Open VS Code.
2. Go to Extensions.
3. Install **LaTeX Workshop** by James Yu.
4. Restart VS Code if prompted.

### Open the project correctly

Open the workspace folder that contains [main.tex](main.tex). LaTeX Workshop should then treat that file as the main document. If it does not, open [main.tex](main.tex) and use the command palette action to set it as the root file for the session.

### Configure LaTeX Workshop

Create or edit `.vscode/settings.json` in the repository root and add a build recipe that uses `latexmk`:

```json
{
	"latex-workshop.latex.autoBuild.run": "onSave",
	"latex-workshop.latex.recipe.default": "latexmk (pdf)",
	"latex-workshop.latex.recipes": [
		{
			"name": "latexmk (pdf)",
			"tools": ["latexmk"]
		}
	],
	"latex-workshop.latex.tools": [
		{
			"name": "latexmk",
			"command": "latexmk",
			"args": [
				"-pdf",
				"-interaction=nonstopmode",
				"-synctex=1",
				"%DOC%"
			]
		}
	],
	"latex-workshop.view.pdf.viewer": "tab"
}
```

If you prefer manual compilation, replace the recipe with a `pdflatex` tool and run it multiple times to resolve references.

### Recommended editor settings

These settings make LaTeX Workshop behave well with this project:

- Enable build on save so the PDF updates automatically.
- Keep the PDF viewer inside VS Code for easier navigation.
- Use `latexmk` instead of a single `pdflatex` pass so cross-references settle correctly.
- Do not change the document encoding in the editor unless you plan to convert the whole project from Latin1 to UTF-8.

### Useful commands

With LaTeX Workshop installed, these commands are the ones you will use most often:

- `LaTeX Workshop: Build LaTeX project`
- `LaTeX Workshop: View LaTeX PDF`
- `LaTeX Workshop: Set root file`
- `LaTeX Workshop: Clean up auxiliary files`

### If VS Code cannot find the tools

If LaTeX Workshop says it cannot find `pdflatex` or `latexmk`, add the TeX distribution's `bin` folder to your Windows PATH and restart VS Code. A full TeX Live or MiKTeX installation should provide the required executables.

## 9. Quick checklist

- [ ] TeX distribution installed
- [ ] `pdflatex` available on PATH
- [ ] `latexmk` available on PATH
- [ ] Opened the repository root in the editor
- [ ] Compiled [main.tex](main.tex)
- [ ] Verified the PDF output
