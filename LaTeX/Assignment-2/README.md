# Assignment 2: Mathematical Notations and Equations

## Objective
Master mathematical typesetting in LaTeX including equations, symbols, arrays, matrices, and advanced mathematical environments.

## What I Learned

### Inline vs Display Math

**Inline Math:**
```latex
$E = mc^2$
```
Math within text flow.

**Display Math:**
```latex
$$
\int_{0}^{\infty} e^{-x} dx = 1
$$
```
Math on separate line, centered.

### Mathematical Operators and Symbols

**Greek Letters:**
```latex
$\alpha, \beta, \gamma, \delta$
$\Gamma, \Delta, \Theta, \Lambda$
```

**Superscripts and Subscripts:**
```latex
$x^2, x^{n+1}$      % Superscript
$x_i, x_{i,j}$      % Subscript
```

**Fractions:**
```latex
$\frac{numerator}{denominator}$
$\frac{a+b}{c+d}$
```

**Roots:**
```latex
$\sqrt{x}$          % Square root
$\sqrt[n]{x}$       % nth root
```

**Summation and Integration:**
```latex
$\sum_{i=1}^{n} x_i$
$\int_{a}^{b} f(x) dx$
$\prod_{i=1}^{n} x_i$
```

### Mathematical Functions

```latex
$\sin(x), \cos(x), \tan(x)$
$\log(x), \ln(x), \exp(x)$
$\lim_{x \to \infty} f(x)$
```

### Matrices and Arrays

**Simple Matrix:**
```latex
$\begin{matrix}
a & b \\
c & d
\end{matrix}$
```

**Bracketed Matrix:**
```latex
$\begin{pmatrix}
a & b \\
c & d
\end{pmatrix}$
```

**Determinant:**
```latex
$\begin{vmatrix}
a & b \\
c & d
\end{vmatrix}$
```

### Equation Environments

**Single Equation:**
```latex
\begin{equation}\label{eq1}
E = mc^2
\end{equation}
```

**Multiple Equations (aligned):**
```latex
\begin{align}
x &= a + b \\
y &= c + d
\end{align}
```

**Multi-line Equation:**
```latex
\begin{multline}
f(x) = a_0 + a_1 x + a_2 x^2 \\
+ a_3 x^3 + a_4 x^4
\end{multline}
```

### Mathematical Symbols

**Relations:**
```latex
$\leq, \geq, \neq, \approx$
$\equiv, \sim, \propto$
$\in, \notin, \subset, \subseteq$
```

**Binary Operators:**
```latex
$\times, \div, \pm, \mp$
$\cdot, \ast, \star$
$\cap, \cup, \setminus$
```

**Arrows:**
```latex
$\rightarrow, \leftarrow, \Rightarrow, \Leftarrow$
$\uparrow, \downarrow, \leftrightarrow$
```

**Special Symbols:**
```latex
$\infty, \partial, \nabla, \exists, \forall$
$\emptyset, \angle, \perp, \parallel$
```

### Advanced Features

**Brackets Sizing:**
```latex
$\left( \frac{a}{b} \right)$
$\left[ \sum_{i=1}^{n} x_i \right]$
```
`\left` and `\right` automatically size brackets.

**Text in Math Mode:**
```latex
$x \text{ where } x > 0$
```

**Cases:**
```latex
f(x) = \begin{cases}
x^2 & \text{if } x \geq 0 \\
-x^2 & \text{if } x < 0
\end{cases}
```

### Spacing in Math Mode

```latex
$a\,b$      % thin space
$a\:b$      % medium space
$a\;b$      % thick space
$a\quad b$  % quad space
$a\qquad b$ % double quad
```

## Important Notes

1. **Compilation**: Use `pdflatex` multiple times for equation numbering
2. **Packages**: Require `amsmath` for advanced features
3. **Spacing**: LaTeX handles math spacing automatically
4. **Alignment**: Use `&` for alignment points in environments
5. **Labels**: Use `\label{}` for equation references

## Common Mistakes Avoided

- Forgetting dollar signs for inline math
- Not using `\left` and `\right` for bracket sizing
- Missing `&` alignment characters
- Incorrect environment names
- Missing required packages

## Key Takeaways

- LaTeX excels at mathematical typesetting
- Inline math for text-embedded expressions
- Display math for standalone equations
- Automatic spacing and sizing
- Extensive symbol library available
- Equation numbering and referencing system

## Required Packages

```latex
\usepackage{amsmath}    % Essential for equations
\usepackage{amssymb}    % Additional symbols
\usepackage{amsthm}     % Theorem environments
```

## Files

This assignment focused on mathematical notations and equations documented in this README.

## Compilation

```bash
pdflatex assignment2.tex
pdflatex assignment2.tex  # Run twice for references
```
