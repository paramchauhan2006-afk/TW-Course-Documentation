# Beamer Presentations

Beamer is a LaTeX document class for creating presentations. It produces PDF slideshows with professional appearance, supporting all LaTeX features including mathematical formulas, graphics, and animations.

## What is Beamer?

Beamer extends LaTeX to create presentation slides with:
- Structured slide layouts
- Professional themes and color schemes
- Mathematical typesetting support
- Overlay specifications for animations
- Table of contents generation
- Navigation symbols

## Key Concepts Learned

### Basic Beamer Structure

```latex
\documentclass{beamer}

\usetheme{Madrid}
\usecolortheme{default}

\title{Presentation Title}
\author{Your Name}
\institute{Institution}
\date{\today}

\begin{document}

\frame{\titlepage}

\begin{frame}
\frametitle{Slide Title}
Content goes here
\end{frame}

\end{document}
```

### Document Class Options

```latex
\documentclass[aspectratio=169]{beamer}  % 16:9 ratio
\documentclass[handout]{beamer}          % Handout mode
\documentclass[notes]{beamer}            % Notes mode
```

### Creating Frames (Slides)

**Basic Frame:**
```latex
\begin{frame}
\frametitle{Title}
\framesubtitle{Subtitle}
Content
\end{frame}
```

**Frame with Sections:**
```latex
\frame{\titlepage}
\frame{\tableofcontents}

\section{Section Name}
\begin{frame}{Frame Title}
Content
\end{frame}
```

### Themes and Appearance

**Presentation Themes:**
```latex
\usetheme{Madrid}
\usetheme{Berlin}
\usetheme{Warsaw}
\usetheme{Copenhagen}
```

**Color Themes:**
```latex
\usecolortheme{default}
\usecolortheme{crane}
\usecolortheme{beetle}
\usecolortheme{seagull}
```

**Font Themes:**
```latex
\usefonttheme{default}
\usefonttheme{serif}
\usefonttheme{structurebold}
```

### Lists and Itemization

**Itemize:**
```latex
\begin{frame}{Items}
\begin{itemize}
    \item First point
    \item Second point
    \item Third point
\end{itemize}
\end{frame}
```

**Enumerate:**
```latex
\begin{enumerate}
    \item First step
    \item Second step
    \item Third step
\end{enumerate}
```

**Description:**
```latex
\begin{description}
    \item[Term 1] Definition
    \item[Term 2] Definition
\end{description}
```

### Overlays and Animations

**Incremental Display:**
```latex
\begin{itemize}
    \item<1-> Appears on slide 1
    \item<2-> Appears on slide 2
    \item<3-> Appears on slide 3
\end{itemize}
```

**Pause Command:**
```latex
First content
\pause
Second content appears after click
\pause
Third content appears after another click
```

**Overlay Specifications:**
```latex
\only<1>{Visible only on slide 1}
\uncover<2>{Appears on slide 2}
\visible<3>{Visible on slide 3}
\invisible<1>{Hidden on slide 1}
```

### Blocks

**Standard Block:**
```latex
\begin{block}{Block Title}
Block content
\end{block}
```

**Alert Block:**
```latex
\begin{alertblock}{Important}
Alert content
\end{alertblock}
```

**Example Block:**
```latex
\begin{exampleblock}{Example}
Example content
\end{exampleblock}
```

### Columns

```latex
\begin{columns}
\column{0.5\textwidth}
Left column content

\column{0.5\textwidth}
Right column content
\end{columns}
```

### Mathematical Content

**Inline Math:**
```latex
The equation $E = mc^2$ shows...
```

**Display Math:**
```latex
\begin{equation}
\int_{0}^{\infty} e^{-x} dx = 1
\end{equation}
```

**Theorem Environments:**
```latex
\begin{theorem}[Pythagorean Theorem]
$a^2 + b^2 = c^2$
\end{theorem}
```

### Images

```latex
\begin{frame}{Image}
\begin{figure}
\centering
\includegraphics[width=0.6\textwidth]{image.png}
\caption{Figure caption}
\end{figure}
\end{frame}
```

### Tables

```latex
\begin{frame}{Data Table}
\begin{table}
\centering
\begin{tabular}{|c|c|c|}
\hline
Header 1 & Header 2 & Header 3 \\
\hline
Data 1 & Data 2 & Data 3 \\
\hline
\end{tabular}
\caption{Table caption}
\end{table}
\end{frame}
```

### Navigation

**Table of Contents:**
```latex
\frame{\tableofcontents}
```

**Section-wise TOC:**
```latex
\frame{\tableofcontents[currentsection]}
```

**Disable Navigation Symbols:**
```latex
\setbeamertemplate{navigation symbols}{}
```

### Highlighting

```latex
\alert{Important text}
\textbf{Bold text}
\textit{Italic text}
\textcolor{red}{Colored text}
```

### Speaker Notes

```latex
\note{These are speaker notes}
\note[item]{Note point 1}
\note[item]{Note point 2}
```

## Title Page Elements

```latex
\title[Short Title]{Full Presentation Title}
\subtitle{Subtitle if needed}
\author[Short Name]{Full Name}
\institute[Short Inst]{Full Institution Name}
\date{\today}
\logo{\includegraphics[height=1cm]{logo.png}}
```

## Bibliography

```latex
\begin{frame}[allowframebreaks]{References}
\bibliographystyle{plain}
\bibliography{references}
\end{frame}
```

## Important Notes

1. **Frame Size**: Standard is 128mm × 96mm (4:3 ratio)
2. **Overlay**: Use overlay specifications for progressive reveal
3. **Fragile Frames**: Use `[fragile]` option for verbatim content
4. **Allowframebreaks**: For frames that may span multiple slides

## Common Options

**Frame Options:**
```latex
\begin{frame}[fragile]        % For verbatim
\begin{frame}[allowframebreaks] % Multiple pages
\begin{frame}[plain]          % No header/footer
\begin{frame}[shrink]         % Shrink content
```

## Best Practices

1. **Keep slides simple** - one concept per slide
2. **Use overlays sparingly** - don't overdo animations
3. **Consistent theme** - stick to one theme throughout
4. **Readable fonts** - use large enough text
5. **Limit bullet points** - 3-5 points per slide
6. **Visual hierarchy** - use blocks and emphasis
7. **High-quality images** - use vector graphics when possible

## Common Mistakes Avoided

- Too much text on slides
- Inconsistent formatting
- Overusing animations
- Poor color contrast
- Missing frame titles
- Not testing on projector

## Key Takeaways

- Beamer integrates LaTeX features into presentations
- Professional themes available out of the box
- Overlay system enables progressive disclosure
- Mathematical content renders beautifully
- PDF output ensures compatibility
- Structured approach to slide organization

## Required Packages

```latex
\usepackage{graphicx}   % Images
\usepackage{amsmath}    % Math
\usepackage{hyperref}   % Links
\usepackage{tikz}       % Graphics
```

## Compilation

```bash
pdflatex presentation.tex
pdflatex presentation.tex  # Twice for TOC
```

## Files

- Beamer presentation source files (.tex)
- Generated presentations (.pdf)
- Presentation images folder
