# Assignment 4: Advanced LaTeX Features

## Objective
Build upon basic LaTeX knowledge to create more complex documents with advanced formatting, custom environments, and enhanced document structure.

## What I Learned

### Document Organization

**Multiple File Management:**
```latex
% Main document
\documentclass{article}
\input{preamble}        % Separate preamble
\begin{document}
\input{chapter1}        % Include chapters
\input{chapter2}
\end{document}
```

### Advanced Sectioning

**Custom Section Numbering:**
```latex
\setcounter{secnumdepth}{3}  % Number depth
\setcounter{tocdepth}{3}      % TOC depth
```

**Unnumbered Sections:**
```latex
\section*{Preface}
\addcontentsline{toc}{section}{Preface}
```

### Custom Commands and Environments

**Define New Commands:**
```latex
\newcommand{\myname}{Your Name}
\newcommand{\derivative}[2]{\frac{d#1}{d#2}}
```

**Usage:**
```latex
Author: \myname
The \derivative{f}{x} is...
```

**Custom Environments:**
```latex
\newenvironment{solution}
{\begin{proof}[Solution]}
{\end{proof}}

\begin{solution}
The solution is...
\end{solution}
```

### Page Layout Customization

**Margins:**
```latex
\usepackage[margin=1in]{geometry}
\usepackage[top=2cm, bottom=2cm, left=2.5cm, right=2.5cm]{geometry}
```

**Headers and Footers:**
```latex
\usepackage{fancyhdr}
\pagestyle{fancy}
\lhead{Left Header}
\chead{Center Header}
\rhead{Right Header}
\lfoot{Left Footer}
\cfoot{\thepage}
\rfoot{Right Footer}
```

### Advanced Lists

**Custom List Formatting:**
```latex
\usepackage{enumitem}

\begin{enumerate}[label=(\alph*)]
    \item First item
    \item Second item
\end{enumerate}

\begin{itemize}[label=$\diamond$]
    \item Diamond bullet
    \item Another point
\end{itemize}
```

**Custom Counters:**
```latex
\newcounter{mycounter}
\setcounter{mycounter}{1}
\themycounter
\stepcounter{mycounter}
```

### Advanced Typography

**Font Selection:**
```latex
\usepackage{times}      % Times font
\usepackage{helvet}     % Helvetica
\usepackage{courier}    % Courier

% Font sizes
{\tiny text}
{\small text}
{\large text}
{\Large text}
{\huge text}
```

**Text Alignment:**
```latex
\begin{center}
Centered text
\end{center}

\begin{flushleft}
Left aligned
\end{flushleft}

\begin{flushright}
Right aligned
\end{flushright}
```

### Advanced Floats

**Subfigures:**
```latex
\usepackage{subcaption}

\begin{figure}
\centering
\begin{subfigure}{0.45\textwidth}
    \includegraphics[width=\textwidth]{image1}
    \caption{First image}
\end{subfigure}
\hfill
\begin{subfigure}{0.45\textwidth}
    \includegraphics[width=\textwidth]{image2}
    \caption{Second image}
\end{subfigure}
\caption{Main caption}
\end{figure}
```

**Wrapped Figures:**
```latex
\usepackage{wrapfig}

\begin{wrapfigure}{r}{0.5\textwidth}
\centering
\includegraphics[width=0.48\textwidth]{image}
\caption{Wrapped figure}
\end{wrapfigure}
```

### Advanced Tables

**Long Tables:**
```latex
\usepackage{longtable}

\begin{longtable}{|c|c|c|}
\caption{Long table caption} \\
\hline
Header 1 & Header 2 & Header 3 \\
\hline
\endfirsthead

\multicolumn{3}{c}{{\tablename\ \thetable{} -- continued}} \\
\hline
Header 1 & Header 2 & Header 3 \\
\hline
\endhead

% Table content
Row 1 & Data & Data \\
% ... many rows
\end{longtable}
```

**Booktabs for Professional Tables:**
```latex
\usepackage{booktabs}

\begin{table}
\centering
\begin{tabular}{lcc}
\toprule
Item & Value 1 & Value 2 \\
\midrule
A & 1 & 2 \\
B & 3 & 4 \\
\bottomrule
\end{tabular}
\end{table}
```

### Advanced Math

**Aligned Equations:**
```latex
\begin{align}
f(x) &= x^2 + 2x + 1 \\
     &= (x+1)^2
\end{align}
```

**Custom Operators:**
```latex
\DeclareMathOperator{\Tr}{Tr}
\DeclareMathOperator*{\argmax}{arg\,max}
```

### Bibliography Management

**Advanced BibTeX:**
```latex
\usepackage[style=authoryear]{biblatex}
\addbibresource{references.bib}

\cite{key}
\parencite{key}
\textcite{key}

\printbibliography
```

### Hyperlinks and PDF Features

**Advanced Hyperref:**
```latex
\usepackage{hyperref}
\hypersetup{
    colorlinks=true,
    linkcolor=blue,
    filecolor=magenta,
    urlcolor=cyan,
    pdftitle={Document Title},
    pdfauthor={Author Name},
    pdfsubject={Subject},
    pdfkeywords={keyword1, keyword2}
}
```

### Code Listings

**Syntax Highlighted Code:**
```latex
\usepackage{listings}
\usepackage{xcolor}

\lstset{
    language=Python,
    basicstyle=\ttfamily\small,
    keywordstyle=\color{blue},
    commentstyle=\color{green},
    stringstyle=\color{red},
    numbers=left,
    numberstyle=\tiny,
    frame=single
}

\begin{lstlisting}
def hello():
    print("Hello, World!")
\end{lstlisting}
```

### Appendices

**Creating Appendices:**
```latex
\appendix
\section{First Appendix}
Content of appendix A

\section{Second Appendix}
Content of appendix B
```

### Indexing

**Creating an Index:**
```latex
\usepackage{makeidx}
\makeindex

Important term\index{term}

\printindex
```

### Advanced Document Classes

**Custom Title Page:**
```latex
\begin{titlepage}
\centering
\vspace*{1cm}
{\Huge\bfseries Document Title\par}
\vspace{2cm}
{\Large Author Name\par}
\vfill
{\large \today\par}
\end{titlepage}
```

## Important Packages Used

```latex
\usepackage{geometry}      % Page layout
\usepackage{fancyhdr}      % Headers/footers
\usepackage{enumitem}      % Custom lists
\usepackage{subcaption}    % Subfigures
\usepackage{wrapfig}       % Wrapped figures
\usepackage{longtable}     % Long tables
\usepackage{booktabs}      % Professional tables
\usepackage{listings}      % Code listings
\usepackage{hyperref}      % Hyperlinks
\usepackage{makeidx}       % Indexing
```

## Key Takeaways

- Custom commands reduce repetition
- Package selection enhances functionality
- Page layout affects readability
- Professional tables use booktabs
- Code can be syntax highlighted
- Multiple files organize large documents
- Hyperref adds PDF functionality

## Common Challenges Solved

1. **Long Documents**: Used `\input{}` for modular structure
2. **Custom Formatting**: Created new commands and environments
3. **Professional Tables**: Applied booktabs package
4. **Code Display**: Configured listings with colors
5. **Navigation**: Added hyperlinks throughout document

## Files

This assignment covered advanced LaTeX features documented in this README.

## Compilation

```bash
pdflatex assignment4.tex
pdflatex assignment4.tex  # For references
makeindex assignment4.idx  # If using index
pdflatex assignment4.tex  # Final compilation
```
