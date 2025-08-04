# enumsub - Aligned inline sublists for enumitem

## Overview

The `enumsub` package provides seamless integration between `enumitem` and inline sublists with perfect alignment and automatic numbering. It solves the common alignment inconsistencies that occur when trying to combine `enumitem` and `tasks` packages.

## Features

- Perfect alignment of inline sub-items with dynamic label styling
- Multiple numbering schemes (Roman, alphabetic, Arabic)
- Customizable spacing and dimensions
- Easy-to-use semicolon-separated syntax
- Non-breaking inline layout with consistent spacing
- Multiple convenience aliases
- Automatic counter reset at each `\item`

## Quick Start

```latex
\documentclass{article}
\usepackage[roman]{enumsub}  % Options: roman, alpha, arabic

\begin{document}
\begin{enumerate}
  \item Main question
  \begin{enumerate}
    \item \enumsub{yes; no; maybe}
    \item \enumsub{option A; option B}
  \end{enumerate}
\end{enumerate}
\end{document}
```

## Installation

### Manual Installation
1. Download `enumsub.dtx` and `enumsub.ins`
2. Run: `latex enumsub.ins`
3. Move `enumsub.sty` to your LaTeX tree
4. Run: `texhash` (if using TeX Live)

### Generate Documentation
```bash
pdflatex enumsub.dtx
makeindex -s gind.ist enumsub.idx
makeindex -s gglo.ist -o enumsub.gls enumsub.glo
pdflatex enumsub.dtx
pdflatex enumsub.dtx
```

## Package Options

| Option   | Description                    | Example Output |
|----------|--------------------------------|----------------|
| `roman`  | Roman numerals (default)      | (i), (ii), (iii) |
| `alpha`  | Alphabetic numbering           | (a), (b), (c) |
| `arabic` | Arabic numerals                | (1), (2), (3) |

## Commands

### Main Command
- `\enumsub{item1; item2; item3}` - Creates aligned inline sublists

### Aliases
- `\subparts{...}` - Same as `\enumsub`
- `\AutoSubpartsAligned{...}` - Same as `\enumsub`
- `\inlineparts{...}` - Same as `\enumsub`

### Customization
- `\setenumsublabelwidth{width}` - Adjust label column width
- `\setenumsubitemwidth{width}` - Adjust item column width

### Predefined Styles
- `mainq` - Main question style
- `subq` - Sub-question style

## Examples

### Basic Usage
```latex
\begin{enumerate}[label=\textbf{\arabic*.}]
  \item What is your favorite color?
  \begin{enumerate}[label=\textbf{(\alph*)}]
    \item \enumsub{red; blue; green}
    \item \enumsub{yellow; purple}
  \end{enumerate}
\end{enumerate}
```

### With Different Numbering
```latex
\usepackage[alpha]{enumsub}
% Now \enumsub produces (a), (b), (c) instead of (i), (ii), (iii)
```

### Custom Spacing
```latex
\setenumsublabelwidth{3em}
\setenumsubitemwidth{2cm}
\enumsub{longer option 1; longer option 2}
```

## Comparison with Other Packages

| Package | Inline Layout | enumitem Integration | Auto Alignment | Custom Numbering |
|---------|---------------|---------------------|----------------|------------------|
| `enumsub` | ✅ | ✅ | ✅ | ✅ |
| `tasks` | ✅ | ❌ | ❌ | ✅ |
| `tablists` | ❌ | ❌ | ✅ | ❌ |
| `multenum` | ❌ | ❌ | ✅ | ❌ |

## Problem Solved

This package specifically addresses the alignment issues when combining `enumitem` and `tasks`:

**Before (misaligned):**
```
1. Question
   (a) option 1    option 2
       ↑ misaligned with enumitem labels
```

**After (perfectly aligned):**
```
1. Question
   (a) (i) option 1    (ii) option 2
       ↑ perfect alignment maintained
```

## Requirements

- LaTeX2e (2020/10/01 or later)
- `enumitem` package
- `xparse` package
- `array` package
- `etoolbox` package

## Compatibility

- Works with all standard document classes
- Compatible with `babel` and `polyglossia`
- Works with `hyperref`
- Compatible with `beamer`

## Changelog

### Version 1.0 (2025-08-04)
- Initial release
- Basic `\enumsub` functionality
- Package options for numbering styles
- Customizable spacing
- Multiple command aliases

## License

This work may be distributed and/or modified under the conditions of the LaTeX Project Public License, either version 1.3c of this license or (at your option) any later version.

## Support

- **Issues:** [GitHub Issues](https://github.com/srikanth-mk/enumsub-tex/issues)
- **Email:** srbsmohankumar@gmail.com

## Contributing

Contributions are welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request

## Acknowledgments

This package was inspired by questions on TeX StackExchange about alignment issues between `enumitem` and `tasks` packages. Special thanks to the LaTeX community for identifying this common problem.
[Stack Exchange Issue](https://tex.stackexchange.com/questions/749213/aligning-the-labels-from-enumerate-and-task)