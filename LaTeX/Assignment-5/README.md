# Assignment 5: LaTeX Graphics and Diagrams

## Objective
Learn to create and incorporate graphics, diagrams, and visual elements in LaTeX documents using various tools and packages.

## What I Learned

### Picture Environment

**Basic Drawing:**
```latex
\begin{picture}(width,height)(x-offset,y-offset)
\put(x,y){object}
\end{picture}
```

**Drawing Elements:**
```latex
\begin{picture}(100,100)
\put(0,0){\line(1,0){100}}      % Horizontal line
\put(0,0){\line(0,1){100}}      % Vertical line
\put(0,0){\line(1,1){70}}       % Diagonal line
\put(50,50){\circle{30}}        % Circle
\put(50,50){\circle*{5}}        % Filled circle
\put(20,80){\vector(1,0){40}}   % Arrow
\put(10,10){\framebox(30,20){Text}}  % Box with text
\end{picture}
```

### TikZ Graphics

**Basic TikZ Setup:**
```latex
\usepackage{tikz}
\usetikzlibrary{shapes,arrows,positioning}

\begin{tikzpicture}
% Drawing commands
\end{tikzpicture}
```

**Drawing Shapes:**
```latex
\begin{tikzpicture}
% Lines
\draw (0,0) -- (2,2);
\draw (0,0) -- (2,0) -- (2,2) -- cycle;

% Rectangles
\draw (0,0) rectangle (2,1);
\fill[blue] (3,0) rectangle (5,1);

% Circles
\draw (6,0.5) circle (0.5);
\fill[red] (8,0.5) circle (0.3);

% Ellipse
\draw (10,0.5) ellipse (1 and 0.5);
\end{tikzpicture}
```

**Nodes and Labels:**
```latex
\begin{tikzpicture}
\node[circle,draw] (A) at (0,0) {A};
\node[rectangle,draw] (B) at (2,0) {B};
\node[diamond,draw] (C) at (1,2) {C};

\draw[->] (A) -- (B);
\draw[->] (B) -- (C);
\draw[->] (C) -- (A);
\end{tikzpicture}
```

### Flowcharts

**Creating Flowcharts:**
```latex
\usepackage{tikz}
\usetikzlibrary{shapes.geometric,arrows}

\tikzstyle{startstop} = [rectangle, rounded corners, 
                         minimum width=3cm, minimum height=1cm,
                         text centered, draw=black, fill=red!30]
\tikzstyle{process} = [rectangle, minimum width=3cm, 
                       minimum height=1cm, text centered, 
                       draw=black, fill=orange!30]
\tikzstyle{decision} = [diamond, minimum width=3cm, 
                        minimum height=1cm, text centered, 
                        draw=black, fill=green!30]
\tikzstyle{arrow} = [thick,->,>=stealth]

\begin{tikzpicture}[node distance=2cm]
\node (start) [startstop] {Start};
\node (pro1) [process, below of=start] {Process 1};
\node (dec1) [decision, below of=pro1, yshift=-0.5cm] {Decision?};
\node (pro2a) [process, below of=dec1, yshift=-0.5cm] {Process 2a};
\node (pro2b) [process, right of=dec1, xshift=2cm] {Process 2b};
\node (stop) [startstop, below of=pro2a] {Stop};

\draw [arrow] (start) -- (pro1);
\draw [arrow] (pro1) -- (dec1);
\draw [arrow] (dec1) -- node[anchor=east] {yes} (pro2a);
\draw [arrow] (dec1) -- node[anchor=south] {no} (pro2b);
\draw [arrow] (pro2b) |- (pro1);
\draw [arrow] (pro2a) -- (stop);
\end{tikzpicture}
```

### Block Diagrams

**System Diagrams:**
```latex
\begin{tikzpicture}[auto, node distance=2cm,>=latex']
\node [draw, rectangle] (input) {Input};
\node [draw, rectangle, right of=input] (process) {Process};
\node [draw, rectangle, right of=process] (output) {Output};

\draw[->] (input) -- (process);
\draw[->] (process) -- (output);
\end{tikzpicture}
```

### PGFPlots for Graphs

**2D Plotting:**
```latex
\usepackage{pgfplots}
\pgfplotsset{compat=1.18}

\begin{tikzpicture}
\begin{axis}[
    title={Function Plot},
    xlabel={$x$},
    ylabel={$f(x)$},
    grid=major
]
\addplot[blue,thick] {x^2};
\addplot[red,thick] {x^3};
\legend{$x^2$,$x^3$}
\end{axis}
\end{tikzpicture}
```

**Bar Charts:**
```latex
\begin{tikzpicture}
\begin{axis}[
    ybar,
    xlabel={Category},
    ylabel={Values},
    symbolic x coords={A,B,C,D},
    xtick=data
]
\addplot coordinates {(A,20) (B,35) (C,45) (D,30)};
\end{axis}
\end{tikzpicture}
```

**Scatter Plots:**
```latex
\begin{tikzpicture}
\begin{axis}[
    scatter,
    only marks
]
\addplot table {data.txt};
\end{axis}
\end{tikzpicture}
```

### Trees and Hierarchies

**Simple Tree:**
```latex
\usepackage{tikz}
\usetikzlibrary{trees}

\begin{tikzpicture}
\node {Root}
    child {node {Child 1}
        child {node {Grandchild 1}}
        child {node {Grandchild 2}}
    }
    child {node {Child 2}
        child {node {Grandchild 3}}
    };
\end{tikzpicture}
```

### Circuit Diagrams

**Using CircuiTikZ:**
```latex
\usepackage{circuitikz}

\begin{circuitikz}
\draw (0,0) to[battery] (0,2)
            to[resistor] (2,2)
            to[lamp] (2,0)
            to[short] (0,0);
\end{circuitikz}
```

### Coordinate Systems

**Plotting Points:**
```latex
\begin{tikzpicture}
% Cartesian coordinates
\draw[->] (-1,0) -- (5,0) node[right] {$x$};
\draw[->] (0,-1) -- (0,5) node[above] {$y$};

% Points
\fill (1,1) circle (2pt) node[above right] {$A$};
\fill (3,2) circle (2pt) node[above right] {$B$};
\fill (2,4) circle (2pt) node[above right] {$C$};

% Connecting points
\draw (1,1) -- (3,2) -- (2,4) -- cycle;
\end{tikzpicture}
```

### Positioning and Alignment

**Relative Positioning:**
```latex
\begin{tikzpicture}[node distance=1cm and 2cm]
\node[draw] (a) {A};
\node[draw, right=of a] (b) {B};
\node[draw, below=of a] (c) {C};
\node[draw, below=of b] (d) {D};

\draw[->] (a) -- (b);
\draw[->] (a) -- (c);
\draw[->] (b) -- (d);
\draw[->] (c) -- (d);
\end{tikzpicture}
```

### Colors and Styles

**Color Usage:**
```latex
\usepackage{xcolor}

\begin{tikzpicture}
\draw[red, thick] (0,0) -- (2,0);
\draw[blue, dashed] (0,1) -- (2,1);
\draw[green, dotted, very thick] (0,2) -- (2,2);
\fill[yellow!50] (0,0) rectangle (1,1);
\fill[cyan!30] (1,1) rectangle (2,2);
\end{tikzpicture}
```

### Mathematical Diagrams

**Geometry Diagrams:**
```latex
\begin{tikzpicture}
% Triangle
\coordinate (A) at (0,0);
\coordinate (B) at (4,0);
\coordinate (C) at (2,3);

\draw (A) -- (B) -- (C) -- cycle;

% Labels
\node[left] at (A) {$A$};
\node[right] at (B) {$B$};
\node[above] at (C) {$C$};

% Angles
\draw (A) +(0.5,0) arc (0:56:0.5);
\node at (0.8,0.3) {$\alpha$};
\end{tikzpicture}
```

### Including External Images

**Combining Graphics:**
```latex
\begin{figure}
\centering
\begin{tikzpicture}
% TikZ drawing
\draw[thick] (0,0) rectangle (2,2);
% Include external image
\node at (1,1) {\includegraphics[width=1.8cm]{photo.jpg}};
\end{tikzpicture}
\caption{Combined graphics}
\end{figure}
```

## Essential Packages

```latex
\usepackage{tikz}
\usepackage{pgfplots}
\usepackage{circuitikz}
\usepackage{xcolor}

\usetikzlibrary{shapes}
\usetikzlibrary{arrows}
\usetikzlibrary{positioning}
\usetikzlibrary{trees}
\usetikzlibrary{shapes.geometric}
```

## Key Takeaways

- TikZ is powerful for creating diagrams
- PGFPlots handles mathematical plotting
- Picture environment for simple drawings
- Flowcharts visualize processes
- Circuit diagrams possible with CircuiTikZ
- Positioning library simplifies layouts
- Colors enhance visual communication

## Common Use Cases

1. **Flowcharts**: Algorithm visualization
2. **Block Diagrams**: System architecture
3. **Graphs and Plots**: Data visualization
4. **Trees**: Hierarchical structures
5. **Circuit Diagrams**: Electrical systems
6. **Geometric Figures**: Mathematical illustrations

## Files

This assignment focused on graphics and diagrams in LaTeX documented in this README.

## Compilation

```bash
pdflatex assignment5.tex
```

For complex TikZ diagrams, may need multiple compilations:
```bash
pdflatex assignment5.tex
pdflatex assignment5.tex
```
