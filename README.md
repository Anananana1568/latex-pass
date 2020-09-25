# LaTeX Pass

[![Build status](https://ci.appveyor.com/api/projects/status/0g8vduvn8aw58k4x/branch/master?svg=true)](https://ci.appveyor.com/project/yihui/latex-pass/branch/master)

Upload a LaTeX error log file, or a LaTeX document, or an R Markdown document to this repository, and I will tell you which LaTeX packages you need to install in your local LaTeX distribution so you can compile your documents to PDF. You will no longer be confused by LaTeX error messages like this:

```latex
! LaTeX Error: File `inconsolata.sty' not found.

Type X to quit or <RETURN> to proceed,
or enter new name. (Default extension: sty)

! Emergency stop.
<read *>

l.276 ^^M

!  ==> Fatal error occurred, no output PDF file produced!
```

## How does it work?

Depending on if you have a LaTeX error `.log` file, or a `.tex` document, or an `.Rmd` document, you may click one of the links below to edit the file in this repo, and follow the Github instructions to send a pull request.

- [`test.log`](https://github.com/yihui/latex-pass/edit/master/test.log): copy and paste your LaTeX error log into here.
- [`test.tex`](https://github.com/yihui/latex-pass/edit/master/test.tex): copy and paste your `.tex` file here.
- [`test.Rmd`](https://github.com/yihui/latex-pass/edit/master/test.Rmd): copy and paste your `.Rmd` file here (its output format should be PDF).

After you send the pull request, wait for about 2 minutes for [AppVeyor](https://ci.appveyor.com/project/yihui/latex-pass) to finish. After it finishes the job, you can click the `Details` link under your pull request to check the log on AppVeyor, which should tell you the list of LaTeX packages required to compile your document, e.g.,

```
Rscript 'latex-pass.R'

The missing packages identified from the LaTeX log are:
  inconsolata

If you are an R user using TinyTeX, you may install these packages via:
  tinytex::tlmgr_install(c("inconsolata"))

If you use TinyTeX but are not an R user, you may install these packages via command line:
  tlmgr install inconsolata
```

If you are familiar with GIT and Github, you can add or edit more than one file (e.g., multiple `.tex` and/or `.Rmd` files) to the repo and send a pull request.

By default, the LaTeX engine to compile `.tex` documents is `pdflatex`. If the document requires a different engine to compile, you may name your file with the engine name, e.g., `xelatex.tex` or `lualatex.tex`, or add a comment of the form `% !TeX program = ENGINE` to your document, e.g., `% !TeX program = xelatex`. The bibliography may be processed by either `bibtex` (default) or `biber`. You may add the bibliography engine name to the filename if you want to use one specifically, e.g., `test-bbier.tex`.

If you are compiling an Rmd document, please see [Section 3.3.7.1 of the _R Markdown Definitive Guide_](https://bookdown.org/yihui/rmarkdown/pdf-document.html#latex-engine) for how to specify the LaTeX engine in the Rmd document.
