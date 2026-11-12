# Assignment 6: Advanced LaTeX Topics

## Objective
Explore advanced LaTeX capabilities for professional document preparation including advanced formatting, bibliographies, cross-referencing, and document customization.

## What I Learned

### Advanced Document Structure

**Multi-part Documents:**
```latex
\documentclass{book}

\begin{document}

\frontmatter
% Title, preface, TOC
\tableofcontents

\mainmatter
% Main chapters
\chapter{Introduction}
\chapter{Methodology}

\backmatter
% Bibliography, appendices
\bibliography{references}
\appendix

\end{document}
```

### Custom Theorem Environments

**Creating Theorem Styles:**
```latex
\usepackage{amsthm}

\theoremstyle{plain}
\newtheorem{theorem}{Theorem}[section]
\newtheorem{lemma}[theorem]{Lemma}
\newtheorem{proposition}[theorem]{Proposition}

\theoremstyle{definition}
\newtheorem{definition}{Definition}[section]
\newtheorem{example}{Example}[section]

\theoremstyle{remark}
\newtheorem*{remark}{Remark}
\newtheorem*{note}{Note}
```

**Usage:**
```latex
\begin{theorem}[Pythagorean Theorem]
For a right triangle: $a^2 + b^2 = c^2$
\end{theorem}

\begin{proof}
Proof content...
\end{proof}

\begin{definition}[Prime Number]
A prime number is a natural number greater than 1...
\end{definition}
```

### Advanced Bibliography

**BibLaTeX Configuration:**
```latex
\usepackage[backend=biber,style=authoryear]{biblatex}
\addbibresource{references.bib}

% Citation commands
\cite{key}                    % Standard citation
\parencite{key}              % Parenthetical citation
\textcite{key}               % Textual citation
\autocite{key}               % Smart citation
\citeauthor{key}             % Author only
\citeyear{key}               % Year only
\citetitle{key}              % Title only

\printbibliography
```

**Multiple Bibliographies:**
```latex
\printbibliography[type=article,title={Articles}]
\printbibliography[type=book,title={Books}]
```

### Advanced Cross-Referencing

**Using cleveref Package:**
```latex
\usepackage{cleveref}

\cref{eq:1}           % Equation 1
\Cref{sec:intro}      % Section 1
\crefrange{eq:1}{eq:3} % Equations 1 to 3
```

**Hyperref Configuration:**
```latex
\usepackage{hyperref}
\hypersetup{
    colorlinks=true,
    linkcolor=blue,
    citecolor=green,
    filecolor=magenta,
    urlcolor=cyan,
    bookmarks=true,
    bookmarksopen=true,
    pdftitle={Document Title},
    pdfauthor={Author Name}
}
```

### Advanced Floats

**Side-by-Side Figures:**
```latex
\usepackage{subcaption}

\begin{figure}[htbp]
\centering
\begin{subfigure}[b]{0.45\textwidth}
    \includegraphics[width=\textwidth]{fig1}
    \caption{First subfigure}
    \label{fig:sub1}
\end{subfigure}
\hfill
\begin{subfigure}[b]{0.45\textwidth}
    \includegraphics[width=\textwidth]{fig2}
    \caption{Second subfigure}
    \label{fig:sub2}
\end{subfigure}
\caption{Overall caption}
\label{fig:main}
\end{figure}
```

**Continued Floats:**
```latex
\usepackage{caption}

\begin{figure}[htbp]
\ContinuedFloat
\caption{Long figure (continued)}
\end{figure}
```

### Advanced Tables

**Professional Tables with Booktabs:**
```latex
\usepackage{booktabs}

\begin{table}[htbp]
\centering
\caption{Professional table}
\begin{tabular}{@{}lrr@{}}
\toprule
Item & \multicolumn{2}{c}{Values} \\
\cmidrule(r){2-3}
     & Q1 & Q2 \\
\midrule
A    & 10 & 15 \\
B    & 20 & 25 \\
C    & 30 & 35 \\
\bottomrule
\end{tabular}
\end{table}
```

**Landscape Tables:**
```latex
\usepackage{rotating}

\begin{sidewaystable}
\centering
\caption{Wide table in landscape}
\begin{tabular}{...}
% Table content
\end{tabular}
\end{sidewaystable}
```

### Custom Page Styles

**Advanced Headers/Footers:**
```latex
\usepackage{fancyhdr}

\pagestyle{fancy}
\fancyhf{} % Clear all
\fancyhead[LE,RO]{\thepage}
\fancyhead[RE]{\leftmark}
\fancyhead[LO]{\rightmark}
\renewcommand{\headrulewidth}{0.4pt}
\renewcommand{\footrulewidth}{0pt}
```

### Algorithms and Pseudocode

**Algorithm Environment:**
```latex
\usepackage{algorithm}
\usepackage{algpseudocode}

\begin{algorithm}
\caption{Euclid's Algorithm}
\begin{algorithmic}[1]
\Procedure{Euclid}{$a,b$}
    \State $r \gets a \bmod b$
    \While{$r \neq 0$}
        \State $a \gets b$
        \State $b \gets r$
        \State $r \gets a \bmod b$
    \EndWhile
    \State \textbf{return} $b$
\EndProcedure
\end{algorithmic}
\end{algorithm}
```

### Advanced Math Features

**Custom Operators:**
```latex
\DeclareMathOperator{\Tr}{Tr}
\DeclareMathOperator*{\argmax}{arg\,max}
\DeclareMathOperator*{\argmin}{arg\,min}
```

**Math Environments:**
```latex
% Split equation
\begin{equation}
\begin{split}
f(x) &= (x+1)^2 \\
     &= x^2 + 2x + 1
\end{split}
\end{equation}

% Gathered equations
\begin{gather}
a = b \\
c = d
\end{gather}

% Aligned at multiple points
\begin{alignat}{2}
x &= y & \quad \text{by assumption} \\
  &= z & \quad \text{by substitution}
\end{alignat}
```

### Custom Commands

**Complex Commands:**
```latex
% Command with default argument
\newcommand{\derivative}[2][x]{\frac{d#2}{d#1}}

% Usage
\derivative{f}      % df/dx
\derivative[t]{f}   % df/dt

% Command with optional and required args
\newcommand{\vector}[2][n]{%
    \mathbf{#2} \in \mathbb{R}^{#1}
}

% Usage
\vector{v}          % v ∈ ℝⁿ
\vector[3]{v}       % v ∈ ℝ³
```

### Conditional Compilation

**Using ifthen:**
```latex
\usepackage{ifthen}

\newboolean{showsolutions}
\setboolean{showsolutions}{true}

\ifthenelse{\boolean{showsolutions}}{
    \newcommand{\solution}[1]{%
        \textbf{Solution:} #1
    }
}{
    \newcommand{\solution}[1]{}
}
```

### Document Customization

**Adjusting Spacing:**
```latex
% Line spacing
\usepackage{setspace}
\onehalfspacing
% or
\doublespacing

% Paragraph spacing
\setlength{\parskip}{1em}
\setlength{\parindent}{0pt}
```

**Section Formatting:**
```latex
\usepackage{titlesec}

\titleformat{\section}
    {\Large\bfseries}
    {\thesection}
    {1em}
    {}
    [\titlerule]
```

### Glossaries and Acronyms

**Creating Glossaries:**
```latex
\usepackage{glossaries}
\makeglossaries

\newglossaryentry{latex}{
    name=LaTeX,
    description={A document preparation system}
}

\newacronym{api}{API}{Application Programming Interface}

% Usage
\gls{latex}
\acrfull{api}  % Full form
\acrshort{api} % Short form

\printglossaries
```

### Including External Files

**Code Listings:**
```latex
\usepackage{listings}

\lstinputlisting[
    language=Python,
    caption={Python script}
]{script.py}
```

**Importing Data:**
```latex
\usepackage{pgfplotstable}

\pgfplotstabletypeset[
    col sep=comma,
    columns/name/.style={string type},
    columns/value/.style={fixed,precision=2}
]{data.csv}
```

### PDF Manipulation

**Including PDF Pages:**
```latex
\usepackage{pdfpages}

\includepdf[pages=1-3]{external.pdf}
\includepdf[pages={1,3,5}]{document.pdf}
```

### Internationalization

**Multiple Languages:**
```latex
\usepackage[english,french,german]{babel}

\selectlanguage{german}
Dies ist deutscher Text.

\selectlanguage{english}
This is English text.
```

### Advanced Numbering

**Custom Counters:**
```latex
\newcounter{problem}
\setcounter{problem}{0}

\newcommand{\problem}{%
    \stepcounter{problem}%
    \textbf{Problem \theproblem:}
}
```

### Package Management

**Checking Package Version:**
```latex
\listfiles  % Add to preamble

% Check if package is loaded
\@ifpackageloaded{hyperref}{
    % hyperref is loaded
}{
    % hyperref is not loaded
}
```

## Essential Advanced Packages

```latex
\usepackage{amsthm}         % Theorems
\usepackage{biblatex}       % Bibliography
\usepackage{cleveref}       % Smart references
\usepackage{booktabs}       % Professional tables
\usepackage{algorithm}      % Algorithms
\usepackage{algpseudocode}  % Pseudocode
\usepackage{fancyhdr}       % Headers/footers
\usepackage{titlesec}       % Section formatting
\usepackage{glossaries}     % Glossaries
\usepackage{pdfpages}       % Include PDFs
```

## Key Takeaways

- Theorem environments for mathematical content
- BibLaTeX offers advanced citation control
- Cleveref simplifies cross-referencing
- Booktabs creates professional tables
- Custom commands reduce repetition
- Fancyhdr customizes page layout
- Glossaries manage terminology
- Multiple bibliographies organize references

## Best Practices

1. Use semantic commands over formatting
2. Separate content from presentation
3. Create reusable custom commands
4. Use packages for specialized tasks
5. Maintain consistent document structure
6. Comment complex code
7. Version control for large documents

## Files

This assignment focused on advanced LaTeX topics and techniques documented in this README.

## Compilation

For documents with bibliography and glossary:
```bash
pdflatex Assignment-6.tex
biber Assignment-6
makeglossaries Assignment-6
pdflatex Assignment-6.tex
pdflatex Assignment-6.tex
```

## Common Use Cases

- Academic papers with theorems
- Technical reports with algorithms
- Books with multiple chapters
- Documents with extensive references
- Papers requiring specific formatting
- Multi-language documents
