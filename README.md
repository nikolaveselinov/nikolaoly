# nikolaoly

`nikolaoly.sty` is a LaTeX package for olympiad problem sets, handouts, and lecture notes. It provides theorem styles, problem-list helpers, page and header formatting, optional Bulgarian support, TikZ/Asymptote integration, and some convenience math macros.

## Usage

Place `nikolaoly.sty` next to your source file and load it in the preamble:

```latex
\usepackage{nikolaoly}
```

Options can be combined in the usual way, for example:

```latex
\usepackage[secthm,sectionmark,diagrams]{nikolaoly}
```

See [`docs.md`](docs.md) for the option and command reference.

The package is based on Dylan Yu's original style file; attribution and licensing information are retained in `nikolaoly.sty`.
