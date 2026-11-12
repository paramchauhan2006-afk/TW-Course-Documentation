# Assignment 3: Tables, Figures, and References

## Objective
Learn to create and manage tables, insert figures, handle cross-references, and manage bibliographies in LaTeX documents.

## What I Learned

### Tables

**Basic Table Structure:**
```latex
\begin{table}[h]
\centering
\begin{tabular}{|c|c|c|}
\hline
Header 1 & Header 2 & Header 3 \\
\hline
Row 1 Col 1 & Row 1 Col 2 & Row 1 Col 3 \\
Row 2 Col 1 & Row 2 Col 2 & Row 2 Col 3 \\
\hline
\end{tabular}
\caption{Table caption}
\label{tab:example}
\end{table}
```

**Table Components:**
- `table` environment for positioning
- `tabular` environment for actual table
- `|` for vertical lines
- `\hline` for horizontal lines
- `&` separates columns
- `\\` ends rows

**Column Alignment:**
- `l` - left aligned
- `c` - center aligned
- `r` - right aligned
- `p{width}` - paragraph column with specified width

**Position Specifiers:**
- `h` - here (approximate)
- `t` - top of page
- `b` - bottom of page
- `p` - separate page
- `!` - override LaTeX positioning

### Figures

**Including Images:**
```latex
\usepackage{graphicx}

\begin{figure}[h]
\centering
\includegraphics[width=0.8\textwidth]{image.png}
\caption{Figure caption}
\label{fig:example}
\end{figure}
```

**Image Options:**
```latex
\includegraphics[width=5cm]{image}
\includegraphics[height=5cm]{image}
\includegraphics[scale=0.5]{image}
\includegraphics[angle=90]{image}
```

**Supported Formats:**
- PDF, PNG, JPG, EPS (with pdflatex)

### Cross-References

**Labeling:**
```latex
\section{Introduction}\label{sec:intro}
\begin{equation}\label{eq:einstein}
E = mc^2
\end{equation}
\begin{figure}\label{fig:plot}
...
\end{figure}
\begin{table}\label{tab:data}
...
\end{table}
```

**Referencing:**
```latex
See Section \ref{sec:intro}
As shown in Equation \ref{eq:einstein}
Figure \ref{fig:plot} illustrates...
Table \ref{tab:data} contains...
```

**Page References:**
```latex
...on page \pageref{sec:intro}
```

### Lists

**Itemized List:**
```latex
\begin{itemize}
    \item First item
    \item Second item
    \item Third item
\end{itemize}
```

**Enumerated List:**
```latex
\begin{enumerate}
    \item First item
    \item Second item
    \item Third item
\end{enumerate}
```

**Description List:**
```latex
\begin{description}
    \item[Term 1] Definition of term 1
    \item[Term 2] Definition of term 2
\end{description}
```

**Nested Lists:**
```latex
\begin{enumerate}
    \item Main item
    \begin{itemize}
        \item Sub item 1
        \item Sub item 2
    \end{itemize}
    \item Another main item
\end{enumerate}
```

### Bibliography

**BibTeX Method:**

Create `references.bib`:
```bibtex
@article{einstein1905,
    author = {Albert Einstein},
    title = {On the Electrodynamics of Moving Bodies},
    journal = {Annalen der Physik},
    year = {1905}
}
```

In LaTeX document:
```latex
\usepackage{natbib}

\cite{einstein1905}
\citep{einstein1905}  % (Author, Year)
\citet{einstein1905}  % Author (Year)

\bibliographystyle{plain}
\bibliography{references}
```

**Manual Bibliography:**
```latex
\begin{thebibliography}{99}
\bibitem{einstein}
A. Einstein, 
\textit{On the Electrodynamics of Moving Bodies},
Annalen der Physik, 1905.
\end{thebibliography}
```

### Colors

```latex
\usepackage{xcolor}

\textcolor{red}{Red text}
\colorbox{yellow}{Highlighted text}
```

### Hyperlinks

```latex
\usepackage{hyperref}

\href{https://example.com}{Link text}
\url{https://example.com}
```

## Advanced Table Features

**Multicolumn:**
```latex
\multicolumn{2}{|c|}{Merged Cells}
```

**Multirow:**
```latex
\usepackage{multirow}
\multirow{2}{*}{Text spanning 2 rows}
```

**Colored Tables:**
```latex
\usepackage{colortbl}
\rowcolor{gray}
\cellcolor{blue}
```

## Important Notes

1. **Compilation Order** (for bibliography):
   ```
   pdflatex document
   bibtex document
   pdflatex document
   pdflatex document
   ```

2. **Label Naming Convention:**
   - Sections: `sec:name`
   - Equations: `eq:name`
   - Figures: `fig:name`
   - Tables: `tab:name`

3. **Float Positioning**: LaTeX automatically positions figures/tables for best layout

4. **Graphics Path**:
   ```latex
   \graphicspath{{images/}}
   ```

5. **Table Tools**: Use online table generators for complex tables

## Common Mistakes Avoided

- Forgetting `\centering` in tables/figures
- Missing `&` column separators
- Incorrect number of columns in table rows
- Not compiling enough times for references
- Wrong file paths for images
- Missing required packages

## Key Takeaways

- Tables use `tabular` inside `table` environment
- Figures require `graphicx` package
- Cross-references automatically update
- Compile multiple times for references
- BibTeX simplifies bibliography management
- Float placement optimizes document layout

## Required Packages

```latex
\usepackage{graphicx}   % For images
\usepackage{natbib}     % For bibliography
\usepackage{hyperref}   % For hyperlinks
\usepackage{xcolor}     % For colors
\usepackage{multirow}   % For multirow tables
```

## Files

This assignment focused on tables, figures, and bibliography management documented in this README.

## Compilation

```bash
pdflatex assignment3.tex
bibtex assignment3
pdflatex assignment3.tex
pdflatex assignment3.tex
```
