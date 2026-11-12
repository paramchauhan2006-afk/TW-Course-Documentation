# LaTeX Documentation

LaTeX is a high-quality typesetting system designed for producing technical and scientific documentation. This section documents learning from LaTeX assignments covering document structure, formatting, mathematical notations, and references.

## What is LaTeX?

LaTeX is a document preparation system that uses markup language to define document structure and formatting. Unlike WYSIWYG editors, LaTeX focuses on content and structure, automatically handling layout and typography.

## Key Concepts Learned

### Document Structure

**Basic Document Template:**
```latex
\documentclass[11pt]{article}
\begin{document}
% Content goes here
\end{document}
```

- **Preamble**: Area before `\begin{document}` for packages and configurations
- **Document Environment**: Contains the actual content
- **Document Classes**: article, report, book, letter

### Essential Commands

**Text Formatting:**
- `\textbf{text}` - Bold text
- `\textit{text}` - Italic text
- `\underline{text}` - Underlined text
- `\emph{text}` - Emphasized text

**Document Sections:**
- `\section{Title}` - Main section
- `\subsection{Title}` - Subsection
- `\subsubsection{Title}` - Sub-subsection
- `\label{name}` - Label for cross-referencing
- `\ref{name}` - Reference a labeled section

**Special Characters:**
- Reserved characters: `& $ # % _ { } ^ ~ \`
- Must be escaped with backslash: `\$ \& \# \% \_ \{ \}`

### Mathematical Notations

**Inline Math:**
```latex
$\alpha + \beta = \gamma$
```

**Display Math:**
```latex
$$
E = mc^2
$$
```

**Common Math Symbols:**
- Greek letters: `\alpha`, `\beta`, `\gamma`, `\delta`
- Superscripts: `x^2`
- Subscripts: `x_i`
- Fractions: `\frac{numerator}{denominator}`
- Square root: `\sqrt{x}`

### Lists and Enumerations

**Unordered Lists:**
```latex
\begin{itemize}
    \item First item
    \item Second item
\end{itemize}
```

**Ordered Lists:**
```latex
\begin{enumerate}
    \item First item
    \item Second item
\end{enumerate}
```

### Packages

Essential packages extend LaTeX functionality:

```latex
\usepackage{amsmath}    % Advanced math
\usepackage{amsthm}     % Theorem environments
\usepackage{graphicx}   % Images
\usepackage{hyperref}   % Hyperlinks
\usepackage{natbib}     % Bibliography
```

### Theorems and Definitions

```latex
\newtheorem{theorem}{Theorem}[section]

\begin{theorem}\label{thm1}
    Statement of theorem
\end{theorem}
```

### Quotations

- Double quotes: `` `quoted text' ``
- Single quotes: `` `single-quoted text' ``

### Spacing Rules

- Multiple spaces = single space
- Multiple blank lines = paragraph break
- Extra spaces/lines don't affect output
- Mid-sentence periods: use `\ ` (backslash space) after abbreviations

### Title and Author

```latex
\title{Document Title}
\author{Author Name}
\date{\today}
\maketitle
```

## Important Notes

1. **Whitespace**: LaTeX ignores extra spaces and blank lines beyond one paragraph break
2. **Compilation**: Documents must be compiled to generate PDF output
3. **Error Handling**: Missing braces or incorrect commands cause compilation errors
4. **Cross-References**: Use `\label{}` and `\ref{}` for automatic numbering
5. **Special Characters**: Always escape reserved characters

## Common Compilation Commands

```bash
pdflatex document.tex      # Compile to PDF
latex document.tex         # Compile to DVI
bibtex document           # Process bibliography
```

## Best Practices

- Always close every `\begin{}` with matching `\end{}`
- Use meaningful label names for references
- Keep preamble organized with comments
- Compile multiple times for references to resolve
- Use packages only when needed
- Comment complex code with `%`

## Learnings from Assignments

### Assignment 2: Mathematical Notations
- Typeset mathematical equations
- Used subscripts and superscripts
- Created fractions and special symbols
- Learned inline vs display math modes

### Assignment 3: Tables, Figures, and References
- Created professional tables with tabular environment
- Inserted and positioned figures
- Implemented cross-references
- Managed bibliographies with BibTeX

### Assignment 4: Advanced LaTeX Features
- Custom commands and environments
- Page layout customization with geometry
- Headers and footers with fancyhdr
- Professional tables with booktabs

### Assignment 5: Graphics and Diagrams
- Drew diagrams with TikZ
- Created flowcharts and block diagrams
- Generated plots with PGFPlots
- Designed mathematical diagrams

### Assignment 6: Advanced Topics
- Advanced theorem environments
- BibLaTeX bibliography management
- Algorithm pseudocode
- Glossaries and custom commands

## Resources

- LaTeX Project: https://www.latex-project.org/
- Overleaf Documentation: https://www.overleaf.com/learn
- CTAN: https://www.ctan.org/ (Package repository)
