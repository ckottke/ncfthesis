# ncfthesis: a LaTeX class for New College of Florida theses

## Getting started

Download LaTeX [here](https://www.latex-project.org/get/), or consider using a cloud based service like [Overleaf](https://www.overleaf.com/).

Put [`ncfthesis.cls`](ncfthesis.cls) in your directory alongside your source file.
To use this class for your document, your source file should begin with
`\documentclass{ncfthesis}`.  A [template file](template.tex) (and [bibliography](template.bib)) are provided
for reference, and a minimal example follows. 

This class is based on the LaTeX `report` class, with `chapter` as
the highest organizational unit, followed by `section`, `subsection`, etc. (Technically `part` 
is available above chapters, but this is not often used.) All options recognized by `report` may be passed to `ncfthesis`.

## Minimal example
```latex
\documentclass{ncfthesis}

\title{My Thesis Title}
\author{A Student}
\division{Division of Natural Sciences}
\sponsor{Dr.~Christopher Kottke}{Assistant Professor of Mathematics}
\degreemonth{April}
\degreeyear{2020}
\thesisdate{May 10, 2020}

\begin{document}

\frontmatter

\maketitle

% Optional dedication and acknowledgements sections. (See below)

\begin{abstract}
Abstract goes here.
\end{abstract}

% Optional table of contents.

\mainmatter

% Thesis content starts here.

\end{document}
```
See [`template.tex`](template.tex) for a more substantial example.

## Available macros
These should appear in the preamble (before the `\begin{document}` line):
* `\title` Required.
* `\author` Required.
* `\division` Required.
* `\degreemonth` and `\degreeyear` Required. These are the month and year of your baccalaureate exam.
* `\thesisdate` Required. This is the date that appears on the signature lines for your signed library copy.
* `\sponsor` Required. Takes two arguments (thesis sponsor's name, and title). For multiple sponsors, simply add additional `\sponsor` lines.
* `\degree` Optional. The default is `Bachelor of Arts`.

These appear after `\begin{document}` and are responsible for setting the front matter:

* `\frontmatter` Sets page numbering to roman for front matter.
* `\maketitle` Required. Sets title page. 
* `\begin{dedication}` and `\end{dedication}` Optional. Should come directly after title page if used.
* `\begin{acknowledgements}` and `\end{acknowledgements}` Optional. Should come after dedication and before abstract if used.
* `\begin{abstract}` and `\end{abstract}` Required. The abstract page also has the signature lines for your sponsor(s).
* `\tableofcontents` Optional. Generates table of contents. If used, it should come at the end of the front matter.
* `\mainmatter` Resets page numbering to arabic after all the front matter.


## Available options
The `\documentclass` line takes optional arguments, including the following:
* `12pt`, `11pt`, or `10pt` Sets the font size. `12pt` is the default.
* `singlespace` Typesets in single space instead of double space. Note that double space is required for the final version.
* `twoside` For printing double sided. This arranges the margins for double sided printing and makes new chapters start on odd numbered pages. The default is appropriate for single sided printing. Either may be used for your final copy.
* `nobind` Gives symmetric margins, as opposed to the offset margins required for binding a physical copy. 
* `dots` Uses dots instead of a solid line for the signature line.

For example, to use minimal paper when printing drafts (not for your official copy!):
```latex
\documentclass[10pt,singlespace,nobind]{ncfthesis}   
```

In addition, you may use any option recognized by the `report` class (such as `reqno`, `twocolumn`, etc).

## Recommended packages
For best results, the following packages are endorsed:
* `\usepackage{amsmath,amssymb}`, and (if you need theorem environments) `\usepackage{amsthm}` will provide the AMS packages for [serious math typesetting](http://www.texdoc.net/texmf-dist/doc/latex/amsmath/amsldoc.pdf).
* `\usepackage{hyperref}` will make your references clickable and the associated PDF will have a navigable table of contents. (If I am getting an electronic copy of your thesis, please do this!) If the colored boxes bother you, try `\usepackage[colorlinks]{hyperref}` or `\usepackage[hidelinks]{hyperref}`.
* `\usepacakge{subfiles}` allows you to modularize your document (consider having one file per chapter). See [this guide](https://www.overleaf.com/learn/latex/Multi-file_LaTeX_projects)  or [the official documentation](http://mirrors.ctan.org/macros/latex/contrib/subfiles/subfiles.pdf) for details.
* `\usepackage{tikz}` for [figures](http://mirrors.ctan.org/graphics/pgf/base/doc/pgfmanual.pdf), `\usepackage{pgfplots}` for [plotting data](http://mirrors.ctan.org/graphics/pgf/contrib/pgfplots/doc/pgfplots.pdf), or `\usepackage{graphicx}` if you will [include external images](http://mirrors.ctan.org/macros/latex/required/graphics/grfguide.pdf).
* `\usepackage[utf8]{inputenc}` for UTF-8 character encoding.
