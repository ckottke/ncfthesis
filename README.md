# ncfthesis: a LaTeX class for New College of Florida theses

## Getting started

Make sure [`ncfthesis.cls`](ncfthesis.cls) is in your directory alongside your source file.
To use this class for your document, your source file should begin with
`\documentclass{ncfthesis}`.  A [template file](template.tex) (and [bibliography](template.bib)) are provided
for reference. The class file is based on the `report` class, with `chapter`s as
the highest organizational unit, followed by `section`s, `subsection`s, etc. (Technically `part`s 
are available above chapters, but are rarely used.)

## Minimal example
See [template.tex](template.tex) for more options.
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

## Available macros
These should appear in the preamble (before the `\begin{document}` line):
* `\title` Required.
* `\author` Required.
* `\division` Required.
* `\degree` Optional. The default is `Bachelor of Arts`.
* `\degreemonth` and `\degreeyear` Required. These are the month and year of your baccalaureate exam.
* `\thesisdate` Required. This is the date that appears on the signature lines for your signed library copy.
* `\sponsor` Required. Takes two arguments (thesis sponsor's name, and title). For multiple sponsors, simply add additional `\sponsor` lines.

These appear after `\begin{document}` and are responsible for setting the front matter:

* `\frontmatter` Sets page numbering to roman for front matter.
* `\maketitle` Required. Sets title page. 
* `\begin{abstract}` and `\end{abstract}` Required. The abstract page also has the signature lines for your sponsor(s).
* `\begin{dedication}` and `\end{dedication}` Optional. Should come directly after title page if used.
* `\begin{acknowledgements}` and `\end{acknowledgements}` Optional. Should come after dedication and before abstract if used.
* `\tableofcontents` Optional. Generates table of contents. If used, it should come at the end of the front matter.
* `\mainmatter` Resets page numbering to arabic after all the front matter.


## Available options
The `\documentclass` line takes optional arguments, including the following.
* `12pt`, `11pt`, or `10pt` Sets the font size. `12pt` is the default.
* `singlespace` Typesets in single space instead of double space. Note that double space is required for the final version.
* `twoside` For printing double sided. This arranges the margins for double sided printing and makes new chapters start on odd numbered pages. The default is appropriate for single sided printing. Either may be used for your final copy.
* `nobind` Gives symmetric margins, as opposed to the offset margins required for binding a physical copy. 
* `dots` Uses dots instead of a solid line for the signature line.

For example, to use minimal paper when priting drafts (not for your official copy!):
```latex
\documentclass[10pt,singlespace,twosided,nobind]{ncfthesis}   
```

In addition, you may use any option recognized by the `report` class (such as `reqno`, `twocolumn`, etc).

## Recommended packages
For best results, the following packages are endorsed:
* `amsmath`, `amssymb` and (if you need theorem environments) `amsthm`, the AMS packages for serious math typesetting.
* `hyperref` will make your references clickable and the associated pdf will have a navigable table of contents. If the colored boxes bother you, try `\usepackage[colorlinks]{hyperref}` or `\usepackage{hidelinks]{hyperref}`.
* `subfiles` allows you to modularize your document (consider having one file per chapter).
* `tikz` for figures, `pgfplots` for plotting data, or `graphicx` if you will include external images.
* `inputenc` with the `utf8` option for UTF-8 character encoding.
