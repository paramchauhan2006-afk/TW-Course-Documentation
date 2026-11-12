# Assignment 5b: Beamer Presentation

## Objective
Create a professional presentation using the Beamer class in LaTeX, demonstrating effective slide design, content organization, and visual communication.

## What I Learned

### Beamer Document Structure

**Basic Template:**
```latex
\documentclass{beamer}

% Theme and Colors
\usetheme{Madrid}
\usecolortheme{default}

% Title Information
\title{Presentation Title}
\subtitle{Optional Subtitle}
\author{Your Name}
\institute{Your Institution}
\date{\today}

\begin{document}

% Title frame
\frame{\titlepage}

% Table of contents
\frame{\tableofcontents}

% Regular frames
\begin{frame}
\frametitle{Slide Title}
Content
\end{frame}

\end{document}
```

### Themes and Appearance

**Popular Themes:**
```latex
\usetheme{Madrid}
\usetheme{Berlin}
\usetheme{Warsaw}
\usetheme{Copenhagen}
\usetheme{AnnArbor}
\usetheme{CambridgeUS}
\usetheme{Singapore}
```

**Color Themes:**
```latex
\usecolortheme{default}
\usecolortheme{crane}
\usecolortheme{beaver}
\usecolortheme{dolphin}
\usecolortheme{orchid}
\usecolortheme{rose}
```

**Font Themes:**
```latex
\usefonttheme{default}
\usefonttheme{serif}
\usefonttheme{structurebold}
\usefonttheme{structureitalicserif}
```

### Creating Frames

**Basic Frame:**
```latex
\begin{frame}
\frametitle{Title}
\framesubtitle{Subtitle}
Frame content
\end{frame}
```

**Frame with Sections:**
```latex
\section{Introduction}
\begin{frame}{Introduction}
Content for introduction
\end{frame}

\section{Methodology}
\begin{frame}{Methodology}
Content for methodology
\end{frame}
```

### Content Organization

**Bullet Points:**
```latex
\begin{frame}{Key Points}
\begin{itemize}
    \item First important point
    \item Second important point
    \item Third important point
\end{itemize}
\end{frame}
```

**Numbered Lists:**
```latex
\begin{frame}{Steps}
\begin{enumerate}
    \item First step
    \item Second step
    \item Third step
\end{enumerate}
\end{frame}
```

**Description Lists:**
```latex
\begin{frame}{Definitions}
\begin{description}
    \item[Term 1] Definition of term 1
    \item[Term 2] Definition of term 2
    \item[Term 3] Definition of term 3
\end{description}
\end{frame}
```

### Overlays and Animations

**Using Pause:**
```latex
\begin{frame}{Progressive Reveal}
First content is visible
\pause

Second content appears after click
\pause

Third content appears after another click
\end{frame}
```

**Overlay Specifications:**
```latex
\begin{frame}{Controlled Appearance}
\begin{itemize}
    \item<1-> Always visible from slide 1
    \item<2-> Appears on slide 2
    \item<3-> Appears on slide 3
    \item<2-3> Visible only on slides 2-3
    \item<4> Visible only on slide 4
\end{itemize}
\end{frame}
```

**Uncover vs Only:**
```latex
\begin{frame}{Different Overlay Types}
\uncover<1->{This text is invisible but takes space}
\only<1>{This text disappears completely}
\visible<1->{Same as uncover}
\invisible<2>{Hidden on slide 2}
\end{frame}
```

### Blocks and Boxes

**Standard Block:**
```latex
\begin{frame}{Using Blocks}
\begin{block}{Block Title}
Important information in a highlighted box
\end{block}
\end{frame}
```

**Alert Block:**
```latex
\begin{alertblock}{Warning}
Critical or alert information
\end{alertblock}
```

**Example Block:**
```latex
\begin{exampleblock}{Example}
Example content or code
\end{exampleblock}
```

### Two-Column Layouts

**Side-by-Side Content:**
```latex
\begin{frame}{Two Columns}
\begin{columns}
\column{0.5\textwidth}
Left column content:
\begin{itemize}
    \item Point 1
    \item Point 2
\end{itemize}

\column{0.5\textwidth}
Right column content:
\begin{itemize}
    \item Point A
    \item Point B
\end{itemize}
\end{columns}
\end{frame}
```

**Columns with Images:**
```latex
\begin{frame}{Text and Image}
\begin{columns}
\column{0.6\textwidth}
Explanation text describing the image shown on the right side.

\column{0.4\textwidth}
\includegraphics[width=\textwidth]{image.png}
\end{columns}
\end{frame}
```

### Mathematics in Beamer

**Inline Math:**
```latex
\begin{frame}{Equation}
The famous equation $E = mc^2$ shows the relationship between energy and mass.
\end{frame}
```

**Display Math:**
```latex
\begin{frame}{Mathematical Expression}
The quadratic formula:
\[
x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}
\]
\end{frame}
```

**Theorem Environments:**
```latex
\begin{frame}{Theorem}
\begin{theorem}[Pythagorean Theorem]
In a right triangle: $a^2 + b^2 = c^2$
\end{theorem}

\begin{proof}
Proof content here...
\end{proof}
\end{frame}
```

### Including Graphics

**Single Image:**
```latex
\begin{frame}{Figure}
\begin{figure}
\centering
\includegraphics[width=0.7\textwidth]{diagram.png}
\caption{Figure caption}
\end{figure}
\end{frame}
```

**Multiple Images:**
```latex
\begin{frame}{Comparison}
\begin{figure}
\centering
\includegraphics[width=0.45\textwidth]{image1.png}
\hfill
\includegraphics[width=0.45\textwidth]{image2.png}
\caption{Side-by-side comparison}
\end{figure}
\end{frame}
```

### Tables in Presentations

**Simple Table:**
```latex
\begin{frame}{Data Table}
\begin{table}
\centering
\begin{tabular}{|l|c|r|}
\hline
Item & Quantity & Price \\
\hline
A & 10 & \$5 \\
B & 20 & \$8 \\
C & 15 & \$6 \\
\hline
\end{tabular}
\caption{Sample data}
\end{table}
\end{frame}
```

### Code Display

**Verbatim Code:**
```latex
\begin{frame}[fragile]{Code Example}
\begin{verbatim}
def factorial(n):
    if n == 0:
        return 1
    return n * factorial(n-1)
\end{verbatim}
\end{frame}
```

Note: `[fragile]` option is required for frames with verbatim content.

### Navigation and Structure

**Table of Contents:**
```latex
\frame{\tableofcontents}
```

**Section-wise TOC:**
```latex
\frame{\tableofcontents[currentsection]}
```

**Hide Navigation:**
```latex
\setbeamertemplate{navigation symbols}{}
```

**Outline at Section Start:**
```latex
\AtBeginSection[]
{
  \begin{frame}{Outline}
    \tableofcontents[currentsection]
  \end{frame}
}
```

### Highlighting and Emphasis

**Text Emphasis:**
```latex
\begin{frame}{Emphasis}
\alert{Important text in alert color}

\textbf{Bold text}

\textit{Italic text}

\textcolor{red}{Colored text}

\structure{Text in structure color}
\end{frame}
```

### Title Page Customization

**Enhanced Title Information:**
```latex
\title[Short Title]{Full Presentation Title}
\subtitle{Subtitle if needed}
\author[Short Name]{Full Author Name}
\institute[Short]{Full Institution Name}
\date{\today}
\logo{\includegraphics[height=0.8cm]{logo.png}}
```

### Frame Options

**Special Frame Types:**
```latex
\begin{frame}[plain]          % No header/footer
\begin{frame}[fragile]        % For verbatim
\begin{frame}[shrink]         % Shrink content
\begin{frame}[allowframebreaks]  % Multiple slides
```

### Beamer with Graphics

**TikZ in Beamer:**
```latex
\begin{frame}{Diagram}
\begin{tikzpicture}
\node[circle,draw] (A) at (0,0) {A};
\node[circle,draw] (B) at (2,0) {B};
\draw[->] (A) -- (B);
\end{tikzpicture}
\end{frame}
```

### Bibliography

**Including References:**
```latex
\begin{frame}[allowframebreaks]{References}
\bibliographystyle{plain}
\bibliography{references}
\end{frame}
```

## Design Best Practices

1. **Keep It Simple**: One concept per slide
2. **Visual Hierarchy**: Use size and color for importance
3. **Consistent Style**: Same theme throughout
4. **Readable Fonts**: Large enough to read from distance
5. **Limited Bullet Points**: 3-5 points maximum
6. **White Space**: Don't overcrowd slides
7. **Progressive Disclosure**: Reveal points gradually
8. **High-Quality Images**: Use vector graphics when possible

## Common Presentation Structure

```latex
1. Title slide
2. Outline/Table of Contents
3. Introduction
4. Background/Literature Review
5. Methodology
6. Results
7. Discussion
8. Conclusions
9. Future Work
10. Thank You / Questions
11. References
```

## Key Takeaways

- Beamer integrates LaTeX power into presentations
- Professional themes available out-of-box
- Overlay system for progressive disclosure
- Mathematical content renders beautifully
- PDF output ensures compatibility
- Full control over appearance and behavior
- Suitable for technical and academic presentations

## Essential Packages

```latex
\usepackage{graphicx}   % For images
\usepackage{tikz}       % For diagrams
\usepackage{amsmath}    % For math
\usepackage{hyperref}   % For links
```

## Files

This assignment focused on creating professional presentations with Beamer documented in this README.

## Compilation

```bash
pdflatex assignment5b.tex
pdflatex assignment5b.tex  # Second run for TOC and references
```

For presentations with bibliography:
```bash
pdflatex assignment5b.tex
bibtex assignment5b
pdflatex assignment5b.tex
pdflatex assignment5b.tex
```

## Viewing the Presentation

The generated PDF can be viewed in:
- Adobe Acrobat Reader (full-screen mode: Ctrl+L)
- PDF viewers with presentation mode
- Any PDF reader (page-by-page navigation)
