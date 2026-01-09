# nikolaoly.sty – Complete Beginner's Guide

**This style file is based on [Yu Dylan's](https://github.com/Yu-Dylan/) original LaTeX style package, with extensive modifications and enhancements.**

A comprehensive LaTeX package for creating beautiful, professional-looking olympiad problems, lecture notes, and handouts with customizable theorem styles, problem helpers, and modern design options.

**Table of Contents**
- [Getting Started](#getting-started)
- [Installation](#installation)
- [First Document](#first-document)
- [Package Options (Themes & Features)](#package-options-themes--features)
- [Using Theorems](#using-theorems)
- [Working with Problem Sets](#working-with-problem-sets)
- [Color Customization](#color-customization)
- [Fonts and Language Support](#fonts-and-language-support)
- [Page Layout and Headers](#page-layout-and-headers)
- [Math Macros & Shortcuts](#math-macros--shortcuts)
- [Boxes and Callouts](#boxes-and-callouts)
- [Diagrams and Graphics](#diagrams-and-graphics)
- [Advanced Features](#advanced-features)
- [Title Page Decorations](#title-page-decorations)
- [Troubleshooting](#troubleshooting)
- [Complete Examples](#complete-examples)

---

## Getting Started

### What is nikolaoly.sty?

`nikolaoly.sty` is a LaTeX style package that adds professional design and layout features specifically for:
- **Olympiad problems and competitions** (hence the name)
- **Lecture notes and handouts**
- **Problem sets with point markers**
- **Mathematical documents** with fancy theorem blocks

The package provides:
- **Various theorem environments** with multiple color themes (default, retro, dark mode)
- **Problem-set formatting** with points, required markers, and icons
- **Easy color customization**
- **Bulgarian language support** for labels and text
- **Pre-configured fonts and layouts** optimized for readability
- **Various useful math shortcuts** (operators, bracket styles, inequality symbols)
- **Diagram and Asymptote support**

---

## Installation

### Step 1: Obtain the Package

Get the `nikolaoly.sty` file from the repository or your source.

### Step 2: Place the File

Place `nikolaoly.sty` in **one** of these locations:

**Option A: Same directory as your document** (simplest)
```
my-project/
  └── article.tex
  └── nikolaoly.sty
```

**Option B: System-wide TeX directory** (for reuse)
```bash
# On Linux/Mac:
cp nikolaoly.sty ~/texmf/tex/latex/nikolaoly/
texhash ~/texmf

# On Windows, check your MiKTeX directory structure
```

### Step 3: Install Dependencies

The package will automatically load most dependencies. However, ensure you have:
- A modern TeX distribution (TeX Live 2021+, MiKTeX 21+, or MacTeX)
- For Bulgarian: `texlive-lang-cyrillic` (or equivalent)
- For chess diagrams: `texlive-games` 
- For Asymptote: `asymptote` binary installed

```bash
# Ubuntu/Debian
sudo apt-get install texlive-games texlive-lang-cyrillic asymptote

# macOS
brew install asymptote
# TeX Live should include the rest

# Windows
# Use MiKTeX Package Manager or your installation method
```

### Step 4: Load the Package

In your `.tex` file, after `\documentclass`:
```latex
\usepackage{nikolaoly}
```

That's it! Your document now has access to all features.

---

## First Document

Here's a minimal example to get you started:

```latex
\documentclass{article}
\usepackage{nikolaoly}

\title{My First Document}
\author{Your Name}
\date{\today}

\begin{document}

\nikolatitle % Creates a styled title page

\begin{theorem}
If $a, b > 0$, then $\sqrt{ab} \leq \frac{a+b}{2}$.
\end{theorem}

\begin{proof}
We have $(a-b)^2 \geq 0$, which gives $a^2 + b^2 \geq 2ab$.
Adding $2ab$ to both sides and taking the square root yields the result.
\end{proof}

\end{document}
```

**To compile:**
```bash
pdflatex article.tex
```

---

## Package Options (Themes & Features)

When loading the package, add options in square brackets:
```latex
\usepackage[option1, option2]{nikolaoly}
```

### Visual Themes

| Option | Effect | Default |
|--------|--------|---------|
| `retro` | Use retro color palette (pastel blues, pinks, greens) | OFF |
| `darkmode` | Black page background with white text; dark theorem boxes | OFF |
| `sleek` | Convenience preset; enables `secthm`, `mdthm`, `colorsec` | OFF |

**Example:**
```latex
\usepackage[retro]{nikolaoly}        % Retro colors
\usepackage[darkmode]{nikolaoly}     % Dark mode
\usepackage[retro, darkmode]{nikolaoly}  % Retro dark mode
```

### Typography & Fonts

| Option | Effect | Default |
|--------|--------|---------|
| `cabin` | Use the Cabin font family (sans-serif) | OFF |
| `bulgarian` | Load Bulgarian language support (Cyrillic) | OFF |

### Page Layout

| Option | Effect | Default |
|--------|--------|---------|
| `fancy` / `nofancy` | Fancy headers and footers | ON |
| `hdr` / `nohdr` | Include headers in fancy layout | ON |
| `titlemark` / `sectionmark` | Show document title (titlemark) or section (sectionmark) in header | titlemark ON |
| `titledecorations` / `notitledecorations` | Show decorative squares on title page | **OFF** (changed in v2.1) |
| `sectionleaves` / `nosectionleaves` | Show decorative leaf icons (🌿) before section numbers | **OFF** |

**Example:**
```latex
\usepackage[nofancy]{nikolaoly}       % No fancy headers
\usepackage[hdr, titlemark]{nikolaoly}  % Headers with title
\usepackage[titledecorations]{nikolaoly}  % Enable title page decorations
\usepackage[sectionleaves]{nikolaoly}  % Enable leaf icons in section headings
\usepackage[titledecorations, sectionleaves]{nikolaoly}  % Both enabled
```

### Theorem System

| Option | Effect | Default |
|--------|--------|---------|
| `thm` / `nothm` | Load the theorem system | ON |
| `secthm` / `nosecthm` | Number theorems within sections (e.g., 2.1, 2.2) | OFF |
| `mdthm` / `nomdthm` | Use mdframed-based theorem styling (requires `pkg`) | OFF |

### Features

| Option | Effect | Default |
|--------|--------|---------|
| `diagrams` / `nodiagrams` | Load diagram and tikz-cd support | OFF |
| `asy` / `noasy` | Asymptote support for graphics | ON |
| `hints` | Enable hints/answers system | OFF |
| `href` / `nohref` | Colored hyperlinks with `hyperref` | ON |
| `colorsec` / `nocolorsec` | Color section headings (KOMA-Script only) | OFF |

### Other Options

| Option | Effect | Default |
|--------|--------|---------|
| `nosetup` | Skip page setup; sets `thm=OFF` | OFF |
| `nopkg` | Disable auxiliary package loading | OFF |
| `nopts` | Suppress point markers in problem lists | OFF |
| `noauthor` | Skip author formatting | OFF |

---

## Complete Package Options Reference

This section provides documentation of every option available in `nikolaoly.sty`, including technical details about what each option does internally.

### Visual Theme Options

#### `retro`
- **Default:** OFF
- **Effect:** Activates a retro color palette with pastel shades
- **Colors Defined:** `retropink`, `retroblue`, `retrogreen`, `retrocyan`, `retropurple`, `retroorange`, `retroindigo`, `retrolavender`, `retrograss`
- **Use Case:** Academic papers, nostalgic design, softer color schemes
- **Example:**
  ```latex
  \usepackage[retro]{nikolaoly}
  \changemaincolor{retropink}
  ```

#### `darkmode`
- **Default:** OFF
- **Effect:** Inverts the color scheme for dark backgrounds
  - Sets page background to black
  - Sets text color to white
  - Adjusts theorem boxes for dark backgrounds
  - Modifies `\vocab` command highlighting
- **Dependencies:** Automatically loads `pagecolor`, `afterpage`
- **Use Case:** Night reading, presentations, reducing eye strain
- **Example:**
  ```latex
  \usepackage[darkmode]{nikolaoly}
  ```
- **Note:** Works well with `retro` for retro-dark combination

#### `sleek`
- **Default:** OFF
- **Effect:** Convenience preset that enables multiple features at once:
  - `secthm=ON` (section-numbered theorems)
  - `mdthm=ON` (mdframed theorem boxes)
  - `colorsec=ON` (colored section headings)
- **Use Case:** Long documents like lecture notes, books, or extensive problem sets
- **Example:**
  ```latex
  \usepackage[sleek]{nikolaoly}
  % Equivalent to:
  % \usepackage[secthm, mdthm, colorsec]{nikolaoly}
  ```

### Typography & Font Options

#### `cabin`
- **Default:** OFF
- **Effect:** Changes the document font family to Cabin (a humanist sans-serif)
- **Technical:** Sets main font to `\fontfamily{Cabin-TLF}`
- **Requires:** Cabin font package installed (usually in `texlive-fonts-extra`)
- **Use Case:** Modern, clean documents; presentations; sans-serif preference
- **Example:**
  ```latex
  \usepackage[cabin]{nikolaoly}
  ```

#### `bulgarian`
- **Default:** OFF
- **Effect:** Enables Bulgarian language support with Cyrillic encoding
  - Loads T2A font encoding (Cyrillic)
  - Loads UTF-8 input encoding
  - Loads `babel` with Bulgarian language
  - Translates all theorem environment names to Bulgarian
  - Changes fonts to Cyrillic-compatible variants (e.g., Computer Modern Super for `\merri`)
- **Requires:** `texlive-lang-cyrillic` or equivalent
- **Translations:** every label is translated
- **Example:**
  ```latex
  \usepackage[bulgarian]{nikolaoly}
  \begin{theorem}  % Displayed as "Теорема 1"
  ```
- **Fallback:** If T2A encoding unavailable, provides transliteration

### Page Layout Options

#### `fancy` / `nofancy`
- **Default:** `fancy` ON
- **Effect:** 
  - `fancy=ON`: Uses `fancyhdr` for styled headers/footers with author, title, date, page numbers
  - `nofancy=OFF`: Plain page style (no headers/footers)
- **Layout Details (fancy ON):**
  - **Header Left (even pages):** Page number
  - **Header Right (odd pages):** Author name
  - **Header Center:** Document title or section name (see `titlemark`)
  - **Footer Center:** Page number
- **Example:**
  ```latex
  \usepackage[nofancy]{nikolaoly}  % Minimal layout
  ```

#### `hdr` / `nohdr`
- **Default:** `hdr` ON
- **Effect:** Controls whether headers are displayed when `fancy` is enabled
  - `hdr=ON`: Headers visible
  - `nohdr=OFF`: Suppresses headers but keeps footers
- **Dependencies:** Only works when `fancy=ON`
- **Example:**
  ```latex
  \usepackage[fancy, nohdr]{nikolaoly}  % Footers only
  ```

#### `titlemark` / `sectionmark`
- **Default:** `titlemark` ON
- **Effect:** Controls what appears in the document header
  - `titlemark=ON`: Displays `\thetitle` in header center
  - `sectionmark=OFF`: Displays `\rightmark` (current section name) in header center
- **Use Case:**
  - `titlemark`: Short documents, problem sets, handouts
  - `sectionmark`: Long documents with many sections, books
- **Example:**
  ```latex
  \usepackage[sectionmark]{nikolaoly}  % Show section names
  ```

#### `titledecorations` / `notitledecorations`
- **Default:** `notitledecorations` (OFF) as of v2.1
- **Effect:** Controls TikZ-based geometric decorations on title page
  - `titledecorations=ON`: Adds colorful geometric pattern to top-right of title
  - `notitledecorations=OFF`: Plain title page
- **Visual:** Creates interconnected rounded lines and shapes using `\maincolor` and `\secondcolor`
- **Dependencies:** Requires TikZ
- **Change in v2.1:** Previously defaulted to ON; now OFF for cleaner default appearance
- **Example:**
  ```latex
  \usepackage[titledecorations]{nikolaoly}
  \changemaincolor{Blue}
  \changesecondcolor{Cyan}
  \nikolatitle  % Title with blue/cyan decorations
  ```

#### `sectionleaves` / `nosectionleaves`
- **Default:** `nosectionleaves` (OFF)
- **Effect:** Adds FontAwesome leaf icons (`\faEnvira` 🌿) before section numbers
  - `sectionleaves=ON`: Displays `🌿1` for section 1, `🌿1.1` for subsection 1.1
  - `nosectionleaves=OFF`: Standard numbering without icons
- **Applies To:** `\section`, `\subsection`, `\subsubsection`
- **Color:** Leaf icons rendered in `\maincolor`
- **Requirements:** KOMA-Script class (`scrartcl`, `scrreprt`, `scrbook`) for best results
- **Added:** v2.1
- **Example:**
  ```latex
  \documentclass{scrartcl}
  \usepackage[sectionleaves, colorsec]{nikolaoly}
  \changemaincolor{ForestGreen}
  \section{Introduction}  % Shows: 🌿1 Introduction (in green)
  ```

### Theorem System Options

#### `thm` / `nothm`
- **Default:** `thm` ON
- **Effect:** Controls whether theorem-like environments are defined
  - `thm=ON`: Defines `theorem`, `lemma`, `corollary`, `proposition`, `definition`, `example`, `remark`, `fact`, `exercise`, `claim`, `conjecture`, `algorithm`, `notation`, `abuse`, `question`, `answer`, `moral`, `walkthrough`, etc.
  - `nothm=OFF`: Skips all theorem environment definitions
- **Use Case for OFF:** When using custom theorem packages or definitions
- **Example:**
  ```latex
  \usepackage[nothm]{nikolaoly}  % Define your own theorems
  ```

#### `secthm` / `nosecthm`
- **Default:** `nosecthm` (OFF)
- **Effect:** Controls theorem numbering scheme
  - `secthm=ON`: Numbers theorems within sections (Theorem 1.1, 1.2, 2.1, 2.2, ...)
  - `nosecthm=OFF`: Numbers theorems globally (Theorem 1, 2, 3, ...)
- **Technical:** Sets `\numberwithin{theorem}{section}`
- **Use Case for ON:** Long documents with many sections
- **Enabled by:** `sleek` preset
- **Example:**
  ```latex
  \usepackage[secthm]{nikolaoly}
  \section{Algebra}
  \begin{theorem}  % Theorem 1.1
  ...
  \end{theorem}
  \section{Geometry}
  \begin{theorem}  % Theorem 2.1
  ...
  \end{theorem}
  ```

#### `mdthm` / `nomdthm`
- **Default:** `nomdthm` (OFF)
- **Effect:** Changes theorem styling to use `mdframed` boxes
  - `mdthm=ON`: Theorems appear in colored boxes with borders
  - `nomdthm=OFF`: Standard LaTeX theorem style with colored labels
- **Visual Difference:**
  - OFF: "**Theorem 1** (Name). Statement..."
  - ON: Entire theorem in colored box with heading
- **Dependencies:** Requires `mdframed` package
- **Enabled by:** `sleek` preset
- **Example:**
  ```latex
  \usepackage[mdthm]{nikolaoly}
  \changemaincolor{RoyalBlue}
  \begin{theorem}  % Appears in blue box
  ```

### Feature Toggle Options

#### `diagrams` / `nodiagrams`
- **Default:** `nodiagrams` (OFF)
- **Effect:** Loads additional diagram packages
  - `diagrams=ON`: Loads `tikz-cd` for commutative diagrams
  - `nodiagrams=OFF`: Only basic TikZ loaded
- **Use Case:** Category theory, abstract algebra, topology
- **Example:**
  ```latex
  \usepackage[diagrams]{nikolaoly}
  \begin{tikzcd}
    A \arrow{r}{f} & B \\
    C \arrow{u}{g} & D \arrow{u}{h}
  \end{tikzcd}
  ```

#### `asy` / `noasy`
- **Default:** `asy` ON
- **Effect:** Controls Asymptote graphics support
  - `asy=ON`: Enables `asymptote` package and inline Asymptote code
  - `noasy=OFF`: Disables Asymptote (useful if not installed)
- **Requirements:** External `asy` binary must be installed and in PATH
- **Use Case:** Complex 3D graphics, technical diagrams, geometry
- **Example:**
  ```latex
  \usepackage[asy]{nikolaoly}
  \begin{asy}
    import graph;
    draw((0,0)--(1,1));
  \end{asy}
  ```

#### `patchasy`
- **Default:** OFF
- **Effect:** Applies compatibility patches for Asymptote integration
- **Technical:** Internal option for fixing Asymptote/LaTeX interaction issues
- **Use Case:** Enable if experiencing Asymptote compilation errors

#### `hints`
- **Default:** OFF
- **Effect:** Enables hint collection system for problem sets
  - Defines `\begin{hint}...\end{hint}` environment
  - Collects hints and displays them with `\makehints`
- **Use Case:** Problem sets where hints appear at the end
- **Example:**
  ```latex
  \usepackage[hints]{nikolaoly}
  \prob[5]{Algebra}{Solve $x^2 = 4$.}
  \begin{hint}
  Consider both positive and negative roots.
  \end{hint}
  % ... more problems ...
  \makehints  % Displays all hints
  ```

#### `href` / `nohref`
- **Default:** `href` ON
- **Effect:** Controls `hyperref` package loading
  - `href=ON`: Loads `hyperref` with colored links
  - `nohref=OFF`: Skips `hyperref` (for faster compilation or when conflicts exist)
- **Link Colors (when ON):**
  - Internal links: Main color
  - Citations: Blue
  - URLs: Dark blue
- **Example:**
  ```latex
  \usepackage[nohref]{nikolaoly}  % No hyperlinks
  ```

#### `colorsec` / `nocolorsec`
- **Default:** `nocolorsec` (OFF)
- **Effect:** Colors section headings
  - `colorsec=ON`: Section/subsection numbers and titles rendered in `\maincolor`
  - `nocolorsec=OFF`: Standard black headings
- **Requirements:** KOMA-Script document class (`scrartcl`, `scrreprt`, `scrbook`)
- **Enabled by:** `sleek` preset
- **Works With:** `sectionleaves` option
- **Example:**
  ```latex
  \documentclass{scrartcl}
  \usepackage[colorsec]{nikolaoly}
  \changemaincolor{Maroon}
  \section{Colored Heading}  % Displays in maroon
  ```

### Advanced Control Options

#### `nosetup`
- **Default:** OFF
- **Effect:** Disables automatic page setup and formatting
  - Skips geometry/margin configuration
  - Disables theorem system (`thm=OFF`)
  - Allows full manual control
- **Use Case:** Integration with existing document setups, custom templates
- **Example:**
  ```latex
  \usepackage[nosetup]{nikolaoly}  % Just load commands, no layout
  ```

#### `nopkg`
- **Default:** OFF
- **Effect:** Prevents loading of auxiliary packages
  - Does not load: `listings`, `mathrsfs`, `textcomp`, `microtype`, and others
  - Only loads essential packages
- **Use Case:** Conflict resolution, minimal installations
- **Example:**
  ```latex
  \usepackage[nopkg]{nikolaoly}
  ```

#### `nopdf`
- **Default:** OFF
- **Effect:** Skips PDF-specific enhancements
- **Use Case:** DVI output, compatibility mode

#### `noauthor`
- **Default:** OFF
- **Effect:** Suppresses author name formatting in headers/footers
- **Example:**
  ```latex
  \usepackage[noauthor]{nikolaoly}  % No author in header
  ```

#### `nopts`
- **Default:** OFF
- **Effect:** Disables point value display in problem lists
  - `\prob[5]{...}` will not show "[5 points]"
- **Use Case:** Practice problems, non-graded problem sets
- **Example:**
  ```latex
  \usepackage[nopts]{nikolaoly}
  \prob[5]{Algebra}{Problem text}  % "[5]" not shown
  ```

#### `ht`
- **Default:** OFF
- **Effect:** Internal flag for specialized typesetting
- **Use Case:** Advanced users only

### Combining Options

Options can be combined in any order. Here are recommended combinations:

**For Long Academic Documents:**
```latex
\usepackage[sleek, sectionmark, cabin]{nikolaoly}
```

**For Problem Sets with Style:**
```latex
\usepackage[titledecorations, sectionleaves, retro]{nikolaoly}
```

**For Dark Mode Presentations:**
```latex
\usepackage[darkmode, retro, colorsec]{nikolaoly}
```

**For Bulgarian Academic Papers:**
```latex
\usepackage[bulgarian, sleek, titledecorations]{nikolaoly}
```

**For Minimal Setup:**
```latex
\usepackage[nofancy, nothm, nopkg]{nikolaoly}
```

---

## Using Theorems

The package provides multiple theorem-like environments, all styled automatically.

### Available Theorem Types

The package provides an extensive collection of theorem-like environments. All environments support optional titles in square brackets and starred variants for unnumbered versions.

#### Mathematical Theorems

```latex
\begin{theorem}[Optional Name]
Statement of your theorem.
\end{theorem}

\begin{lemma}[Optional Name]
A supporting result.
\end{lemma}

\begin{corollary}[Optional Name]
A consequence of the theorem.
\end{corollary}

\begin{proposition}[Optional Name]
A related fact.
\end{proposition}

\begin{claim}[Optional Name]
A statement to be proved.
\end{claim}

\begin{conjecture}[Optional Name]
An unproven statement.
\end{conjecture}

\begin{postulate}[Optional Name]
An assumed principle.
\end{postulate}

\begin{law}[Optional Name]
A fundamental principle or rule.
\end{law}
```

**Shortcuts Available:**
- `\prop` = `\begin{proposition}`..`\end{proposition}`

#### Definitions and Concepts

```latex
\begin{definition}[Optional Term]
Define a concept.
\end{definition}

\begin{notation}[Optional Context]
Establish notation.
\end{notation}

\begin{abuse}[Optional Context]
Notation abuse explanation.
\end{abuse}
```

**Shortcuts:**
- `\defn` = `\begin{definition}`..`\end{definition}`

#### Examples and Illustrations

```latex
\begin{example}[Optional Context]
An illustrative example.
\end{example}

\begin{moral}[Optional Lesson]
A key takeaway or lesson.
\end{moral}

\begin{walkthrough}[Optional Title]
Step-by-step solution guide.
\end{walkthrough}
```

**Shortcuts:**
- `\walk` = `\begin{walkthrough}`..`\end{walkthrough}`

#### Problems and Exercises

```latex
\begin{exercise}[Optional Topic]
A practice problem for the reader.
\end{exercise}

\begin{problem}[Optional Source]
A formal problem statement.
\end{problem}

\begin{question}[Optional Context]
A question to consider.
\end{question}
```

#### Facts and Observations

```latex
\begin{fact}[Optional Context]
A useful fact.
\end{fact}

\begin{remark}[Optional Topic]
An additional note or observation.
\end{remark}
```

#### Algorithms and Procedures

```latex
\begin{algorithm}[Optional Name]
Step-by-step computational procedure.
\end{algorithm}
```

#### Proof Structures

```latex
\begin{proof}[Optional Method]
Your proof here.
\end{proof}

\begin{soln}  % Shortcut for solution
Solution to the problem.
\end{soln}

\begin{answer}  % For direct answers
The answer is 42.
\end{answer}

\begin{subproof}[Optional Subgoal]
Nested proof within a proof.
\end{subproof}
```

#### Induction Helpers

For mathematical induction proofs:

```latex
\begin{proof}
We proceed by induction.

\begin{basecase}
For $n=1$, we have...
\end{basecase}

\begin{induction}
Assume true for $n=k$. We show for $n=k+1$...
\end{induction}
\end{proof}
```

**Environment Names:**
- `\begin{basecase}` – Base case of induction
- `\begin{induction}` – Inductive step
- **Bulgarian:** Automatically translated to "База" and "Индуктивна стъпка"

#### Case Analysis

```latex
\begin{proof}
We consider two cases.

\begin{case}
When $x > 0$, we have...
\end{case}

\begin{case}
When $x \leq 0$, we have...
\end{case}
\end{proof}
```

### Non-Numbered Variants

Add an asterisk `*` to suppress numbering for any environment:

```latex
\begin{remark*}
This remark is not numbered.
\end{remark*}

\begin{lemma*}
This lemma is not numbered either.
\end{lemma*}

\begin{theorem*}[Fundamental Theorem]
Important but unnumbered theorem.
\end{theorem*}

\begin{example*}
Unnumbered example.
\end{example*}
```

**Works for:** All theorem-type environments

### Complete List of Available Environments

| Environment | Description | Numbered | Starred Version |
|-------------|-------------|----------|-----------------|
| `theorem` | Mathematical theorem | ✓ | ✓ |
| `lemma` | Supporting result | ✓ | ✓ |
| `corollary` | Direct consequence | ✓ | ✓ |
| `proposition` | Statement to prove | ✓ | ✓ |
| `claim` | Assertion | ✓ | ✓ |
| `conjecture` | Unproven statement | ✓ | ✓ |
| `postulate` | Assumed principle | ✓ | ✓ |
| `law` | Fundamental rule | ✓ | ✓ |
| `definition` | Concept definition | ✓ | ✓ |
| `notation` | Notation establishment | ✓ | ✓ |
| `abuse` | Notation abuse note | ✓ | ✓ |
| `example` | Illustrative example | ✓ | ✓ |
| `moral` | Key lesson | ✓ | ✓ |
| `walkthrough` | Step-by-step guide | ✓ | ✓ |
| `exercise` | Practice problem | ✓ | ✓ |
| `problem` | Formal problem | ✓ | ✓ |
| `question` | Question | ✓ | ✓ |
| `fact` | Useful fact | ✓ | ✓ |
| `remark` | Additional note | ✓ | ✓ |
| `algorithm` | Procedure | ✓ | ✓ |
| `proof` | Proof environment | ✗ | ✗ |
| `soln` | Solution (proof variant) | ✗ | ✗ |
| `answer` | Answer (proof variant) | ✗ | ✗ |
| `subproof` | Nested proof | ✗ | ✗ |
| `basecase` | Induction base | ✗ | ✗ |
| `induction` | Inductive step | ✗ | ✗ |
| `case` | Case in analysis | ✗ | ✗ |

### Example Document

```latex
\documentclass{article}
\usepackage{nikolaoly}

\title{Inequalities}
\author{Jane Doe}

\begin{document}
\nikolatitle

\begin{theorem}[AM-GM Inequality]
For non-negative reals $a_1, a_2, \ldots, a_n$:
$$\sqrt[n]{a_1 a_2 \cdots a_n} \leq \frac{a_1 + a_2 + \cdots + a_n}{n}$$
\end{theorem}

\begin{proof}
By convexity of the logarithm.
\end{proof}

\begin{remark*}
Equality holds if and only if all $a_i$ are equal.
\end{remark*}

\end{document}
```

---

## Working with Problem Sets

### Basic Problem List

Use the `\problems` command to start a problem section:

```latex
\documentclass{article}
\usepackage{nikolaoly}

\title{Problem Set 1}
\author{Math Club}

\begin{document}
\nikolatitle

\problems  % Starts a new "Problems" section

\prob{Algebra}{Solve $x^2 - 5x + 6 = 0$.}

\prob{Geometry}{Prove that opposite angles in a cyclic quadrilateral sum to $180°$.}

\prob{Combinatorics}{How many ways can you arrange 5 books on a shelf?}

\end{document}
```

### Adding Point Values

Specify points in square brackets:

```latex
\prob[5]{Algebra}{Solve $x^2 - 5x + 6 = 0$.}
\prob[7]{Geometry}{Prove that opposite angles in a cyclic quadrilateral sum to $180°$.}
\prob[3]{Combinatorics}{How many ways can you arrange 5 books on a shelf?}
```

### Required vs. Optional Problems

Use `\req` for required problems (marked with a rook ♜):

```latex
\minpt{10}  % Display "Minimum: 10 points"

\prob[5]{Easy}{Easy problem.}
\prob[7]{Medium}{Medium problem.}
\req[5]{Hard}{This problem is required!}
```

### Disabling Point Markers

If you don't want points displayed:

```latex
\usepackage[nopts]{nikolaoly}
```

### Problem Tags

Add custom tags (in parentheses after the number):

```latex
\prob[5]{(Vieta's Formulas)}{Find the sum of roots of $x^2 + 3x - 4 = 0$.}
```

---

## Color Customization

### Quick Color Change

Change the main color anywhere in your document:

```latex
\changemaincolor{Red}        % Uses xcolor color names
\changemaincolor{Blue}
\changemaincolor{Green}
\changemaincolor{Purple}
```

### Using HTML Color Codes

```latex
\changemaincolorhtml{FF5733}  % Coral
\changemaincolorhtml{1F77B4}  % Blue
\changemaincolorhtml{2CA02C}  % Green
```

### Secondary Color (for accents)

```latex
\changesecondcolor{Orange}
\changesecondcolorhtml{FFA500}
```

### Retro Palette Colors

If using the `retro` option, these colors are predefined:

```latex
\changemaincolor{retropink}      % Soft pink
\changemaincolor{retroblue}      % Dusty blue
\changemaincolor{retrogreen}     % Teal-green
\changemaincolor{retrocyan}      % Cyan
\changemaincolor{retropurple}    % Purple
\changemaincolor{retroorange}    % Orange
\changemaincolor{retroindigo}    % Indigo
\changemaincolor{retrolavender}  % Lavender
\changemaincolor{retrograss}     % Grass green
```

### Complete Example

```latex
\documentclass{article}
\usepackage[retro]{nikolaoly}

\title{Colorful Document}
\author{Your Name}

\begin{document}
\nikolatitle

\changemaincolor{retropink}
\begin{theorem}
Pink theorem.
\end{theorem}

\changemaincolor{retroblue}
\begin{lemma}
Blue lemma.
\end{lemma}

\end{document}
```

---

## Fonts and Language Support

### Changing Document Fonts

Use the `cabin` option for a sans-serif font:

```latex
\usepackage[cabin]{nikolaoly}
```

### Language Support: Bulgarian

To write documents in Bulgarian with proper Cyrillic encoding:

```latex
\usepackage[bulgarian]{nikolaoly}

\begin{document}

\begin{theorem}
Това е теорема на български.
\end{theorem}

\end{document}
```

**Notes:**
- All theorem labels (Theorem, Lemma, Definition, etc.) automatically translate to Bulgarian.
- The `bulgarian` option loads proper font encodings (T2A) for Cyrillic.
- Requires `texlive-lang-cyrillic` or equivalent.

### Font Commands

Three font styles are available:

```latex
{\alegreyafont This text uses Alegreya font.}
{\notofont This text uses Noto Sans.}
{\merri This text uses Merriweather Sans.}
```

---

## Page Layout and Headers

### Default Layout

By default, nikolaoly sets up:
- Fancy headers and footers
- Author name and date in the header
- Page numbers in the footer
- Optimized margins and text width

### Disable Fancy Layout

```latex
\usepackage[nofancy]{nikolaoly}
```

### Control What Shows in the Header

```latex
% Show the document title in the header (default)
\usepackage[titlemark]{nikolaoly}

% Show the current section in the header instead
\usepackage[sectionmark]{nikolaoly}

% No headers at all
\usepackage[nohdr]{nikolaoly}
```

### Accessing Document Metadata

Use these commands to reference your title/author/date:

```latex
\thetitle    % Current document title
\theauthor   % Current author
\thedate     % Current date
```

---

## Math Macros & Shortcuts

The package provides a considerable amount (150+) of shortcuts to speed up typesetting. All commands are designed to avoid conflicts with common packages.

### Brackets and Delimiters

Automatically sized delimiters:

```latex
\cbrt{x}         % Cube root: ∛x
\floor{x}        % Floor: ⌊x⌋
\ceiling{x}      % Ceiling: ⌈x⌉
\paren{x+y}      % Parentheses: (x+y) [auto-sized]
\vangle{a,b,c}   % Angle brackets: ⟨a,b,c⟩
\abs{x}          % Absolute value: |x|
\norm{v}         % Norm: ||v||
```

**Usage Example:**
```latex
$\floor{\frac{n}{2}} + \ceiling{\frac{n}{2}} = n$
$\abs{x-y} \leq \abs{x} + \abs{y}$
$\norm{v + w} \leq \norm{v} + \norm{w}$
```

### Accents and Decorations

Shorthand for common decorations:

```latex
\ol{AB}          % Overline: $\overline{AB}$
\ul{x}           % Underline: $\underline{x}$
\wt{A}           % Widetilde: $\widetilde{A}$
\wh{AB}          % Widehat: $\widehat{AB}$
\eps             % Varepsilon: ε (replaces \epsilon)
```

**Geometry-Specific:**
```latex
\seg{AB}         % Segment: $\overline{AB}$
\ray{AB}         % Ray with arrow: $\overrightarrow{AB}$
\arc{AB}         % Arc: $\wideparen{AB}$
```

### Number Sets and Blackboard Bold Letters

Standard number sets:

```latex
\NN              % Natural numbers: ℕ
\ZZ              % Integers: ℤ
\QQ              % Rationals: ℚ
\RR              % Reals: ℝ
\CC              % Complex numbers: ℂ
\FF              % Field (e.g., \FF_p): 픽
\PP              % Projective space: ℙ
```

**All Available Blackboard Letters:**
```latex
\BB, \CC, \DD, \EE, \FF, \GG, \HH, \II, \JJ, \KK, \LL, \MM
\NN, \PP, \QQ, \RR, \ZZ
```

**Usage Examples:**
```latex
For all $x \in \RR$, we have $x^2 \ge 0$.
The field $\FF_p$ has characteristic $p$.
The function $f: \ZZ \to \NN$ counts divisors.
```

### Mathematical Operators

#### Number Theory
```latex
\gcd(a,b)        % Greatest common divisor: gcd(a,b)
\lcm(a,b)        % Least common multiple: lcm(a,b)
\cis(\theta)     % cos + i·sin: cis θ
```

#### Algebra and Group Theory
```latex
\Aut(G)          % Automorphisms: Aut(G)
\Inn(G)          % Inner automorphisms: Inn(G)
\Gal(K/F)        % Galois group: Gal(K/F)
\Syl_p(G)        % Sylow p-subgroups: Syl_p(G)
\GL(n,\FF)       % General linear group: GL(n,𝔽)
\SL(n,\FF)       % Special linear group: SL(n,𝔽)
\sign(\sigma)    % Sign of permutation: sign(σ)
\charin          % Characteristic (with space): "char "
```

#### Analysis and Topology
```latex
\diam(S)         % Diameter: diam(S)
\rank(A)         % Matrix rank: rank(A)
\Hom(X,Y)        % Homomorphisms: Hom(X,Y)
```

#### Optimization
```latex
\argmin_{x}      % arg min (with subscript)
\argmax_{x}      % arg max (with subscript)
```

### Inequalities and Summations

#### Olympiad-Style Summations

For inequality problems involving cyclic or symmetric sums:

```latex
\cycsum          % Cyclic sum: ∑_{cyc}
\symsum          % Symmetric sum: ∑_{sym}
\cycprod         % Cyclic product: ∏_{cyc}
\symprod         % Symmetric product: ∏_{sym}
```

**Usage Example:**
```latex
\[
\cycsum a^2b \ge \symsum abc
\]
% Displays as: ∑_{cyc} a²b ≥ ∑_{sym} abc
```

#### Inequality Symbols

```latex
\peq             % Preceq: ⪯
\seq             % Succeq: ⪰
\pe              % Prec: ⪷
\se              % Succ: ⪸
```

### Geometry Shortcuts

#### Angles
```latex
\dang            % Directed/measured angle: ∠
\dg              % Degree symbol: °
```

**Usage:**
```latex
$\dang ABC = 60\dg$
$\dang BAC + \dang ABC + \dang BCA = 180\dg$
```

#### Lines and Segments
```latex
\seg{AB}         % Segment AB with overline: $\overline{AB}$
\ray{AB}         % Ray AB with arrow: $\overrightarrow{AB}$
\arc{AB}         % Arc AB with wide paren: $\wideparen{AB}$
```

### Common Helpers and Utilities

#### Fractions and Powers
```latex
\half            % One-half: ½ (as \frac{1}{2})
\ts{n}           % Superscript: n^th (renders as $n^{\mathrm{th}}$)
\inv             % Inverse: ^{-1}
```

**Usage:**
```latex
$\half(a+b) = \frac{a+b}{2}$
$f\inv(x)$ is the inverse function
The $n\ts$ term is $a_n = 2^n$
```

#### Categories and Morphisms
```latex
\id              % Identity morphism: id
\taking{f}       % Arrow with label: →^f (as \xrightarrow{f})
\catname{Cat}    % Category name: 𝒞𝒶𝓉 (sans-serif)
```

**Usage:**
```latex
$f: A \taking{iso} B$ denotes an isomorphism
$\id_X$ is the identity on $X$
```

#### Definitions and Emphasis
```latex
\defeq           % Defined as: ≝ (as \overset{\text{def}}{=})
\vocab{term}     % Vocabulary highlight (colored, bold, slanted)
\alert{important}% Alias for \vocab
```

**Usage:**
```latex
A group $G$ is \vocab{abelian} if $ab = ba$ for all $a,b \in G$.
Let $S \defeq \{1, 2, 3\}$ be our set.
```

#### Special Characters
```latex
\SX              % Calligraphic X: 𝒳
\SW              % Calligraphic W: 𝒲
```

### Chess Notation (Bonus)

If `skak` package is installed:

```latex
\BlackPawnOnWhite   \BlackRookOnWhite   \BlackKnightOnWhite
\BlackBishopOnWhite \BlackQueenOnWhite  \BlackKingOnWhite
```

If not installed, falls back to bold text: **P**, **R**, **N**, **B**, **Q**, **K**.

### Custom Environments

#### Inline Lists
```latex
\begin{parlist}
\item First
\item Second
\item Third
\end{parlist}
```
Creates an inline enumeration: (i) First (ii) Second (iii) Third

#### Gobble Environment
```latex
\begin{gobble}
This content is completely hidden and won't appear in output.
Useful for commenting out large blocks.
\end{gobble}
```

### Complete Quick Reference Table

| Command | Output | Category |
|---------|--------|----------|
| `\NN, \ZZ, \QQ, \RR, \CC` | ℕ, ℤ, ℚ, ℝ, ℂ | Number sets |
| `\abs{x}` | \|x\| | Delimiters |
| `\floor{x}, \ceiling{x}` | ⌊x⌋, ⌈x⌉ | Delimiters |
| `\norm{v}` | ‖v‖ | Delimiters |
| `\ol{x}, \ul{x}` | $\overline{x}$, $\underline{x}$ | Accents |
| `\wt{X}, \wh{X}` | $\widetilde{X}$, $\widehat{X}$ | Accents |
| `\seg{AB}, \ray{AB}, \arc{AB}` | $\overline{AB}$, $\overrightarrow{AB}$, $\wideparen{AB}$ | Geometry |
| `\dang, \dg` | ∠, ° | Geometry |
| `\cycsum, \symsum` | ∑_{cyc}, ∑_{sym} | Inequalities |
| `\gcd, \lcm` | gcd, lcm | Number theory |
| `\Aut, \Gal, \GL, \SL` | Aut, Gal, GL, SL | Algebra |
| `\half` | ½ | Fractions |
| `\inv` | $^{-1}$ | Powers |
| `\defeq` | ≝ | Relations |
| `\vocab{x}` | **x** (colored) | Emphasis |

---

### Common Helpers

```latex
\half            % One-half fraction: ½
\ts{n}           % Superscript: $n^{\mathrm{th}}$
\id              % Identity operator: id
\taking{f}       % Right arrow: →f
\inv             % Inverse: $^{-1}$
\defeq           % Defined equal: $\overset{\text{def}}{=}$
\mailto{john@example.com}  % Email link
```

---

## Boxes and Callouts

The package provides specialized box environments for highlighting important content, organizing information, and creating visual emphasis.

### Notation Box

For listing notation and conventions at the beginning of documents:

```latex
\begin{notation}
\item $\RR$ denotes the set of real numbers.
\item $[n]$ denotes the set $\{1, 2, \ldots, n\}$.
\item $\binom{n}{k}$ is the binomial coefficient.
\item For a triangle $ABC$, $AB=c, BC=a, CA=b$.
\end{notation}
```

**Style:** Styled theorem box with "Notation" header
**Use Case:** Establishing conventions, symbol definitions, abbreviations

### Definition Box (Alternative Form)

Besides the `definition` theorem environment, you can use `defn` shorthand:

```latex
\begin{defn}[Continuous Function]
A function $f: \RR \to \RR$ is continuous at $x=a$ if for every $\eps > 0$, there exists $\delta > 0$ such that $|x-a| < \delta$ implies $|f(x) - f(a)| < \eps$.
\end{defn}
```

**Note:** This is equivalent to `\begin{definition}...\end{definition}`

### Keywords Box

For metadata and document tags:

```latex
\begin{keywords}
inequality, Cauchy-Schwarz, optimization, convexity, AM-GM
\end{keywords}
```

**Style:** Simple box with "Keywords:" label
**Use Case:** Problem categorization, search optimization
**Output:** Displays as comma-separated list

### Caution / Warning Box

To highlight common mistakes or warnings:

```latex
\begin{caution}
This approach is incorrect because it assumes $x \neq 0$ without justification!
\end{caution}
```

**Visual:** Red warning box with danger symbol (⚠)
**Use Case:** Common errors, pitfalls, things to avoid
**Alternative Name:** Can also use `\begin{warning}`

### Question Box

For posing questions or exercises inline:

```latex
\begin{question}
What is the relationship between $e^{i\pi}$ and $-1$?
\end{question}
```

**Style:** Boxed environment with "Question" header
**Use Case:** Thought questions, discussion prompts, reflection points

### Boxed Paragraph with Custom Title

General-purpose colored box with optional heading:

```latex
\begin{boxpar}[Important Note]
This is a boxed paragraph with a colored heading.
It can span multiple lines and includes formatted text.
Use this for highlighting key insights or important reminders.
\end{boxpar}
```

**Customization:** The optional argument becomes the box title
**Use Case:** General emphasis, key takeaways, summaries
**Without Title:**
```latex
\begin{boxpar}
Plain boxed content without a title.
\end{boxpar}
```

### Difficulty Callout (Hard Problem Marker)

Special marker for difficult content:

```latex
\begin{hardbox}
This problem requires advanced techniques from algebraic topology!
Warning: This is very challenging.
\end{hardbox}
```

**Visual:** Lightning bolt icons (⚡) appear in the margin
**Style:** Emphasized box indicating high difficulty
**Use Case:** Olympiad problems, advanced exercises, challenge sections

### Abuse of Notation Box

For explaining intentional notation abuse:

```latex
\begin{abuse}
We write $\ZZ/n\ZZ$ to mean both the quotient group and the ring of integers modulo $n$, with the meaning clear from context.
\end{abuse}
```

**Style:** Theorem-style environment with "Abuse of Notation" label
**Use Case:** Clarifying ambiguous notation, warning about shortcuts

### Custom Box Colors

Box colors automatically adapt to your chosen `\maincolor` and `\secondcolor`. To change:

```latex
\changemaincolor{Red}
\begin{theorem}
This theorem box will be red-themed.
\end{theorem}

\changemaincolor{Blue}
\begin{caution}
This caution box will be blue-themed.
\end{caution}
```

### Visual Emphasis Commands

#### Vocabulary Highlighting

```latex
A group is \vocab{abelian} if all its elements commute.
```

**Effect:** The word "abelian" appears in bold, slanted, colored text
**Color Scheme:**
- **Default:** Violet
- **Dark Mode:** Light violet (adjusted for dark backgrounds)
- **Retro Mode:** Retro pink

#### Alert (Alias)

```latex
\alert{Important term} is highlighted.
```

**Note:** `\alert` is an alias for `\vocab`

#### Danger Sign Symbol

```latex
\dangersign\ This is dangerous!
```

**Output:** Red triangle with exclamation mark: ⚠
**Scaled Version:**
```latex
\dangersign[3ex]  % Larger symbol
```

### Horizontal Rules

```latex
\hrulebar
```

**Effect:** Inserts a thin horizontal line with spacing
**Use Case:** Visual section breaks, separating content

### Special Email Formatting

```latex
Contact: \mailto{professor@university.edu}
```

**Output:** Clickable email link in typewriter font
**Requires:** `href` option enabled (default)

### Plus Email (Author Addition)

```latex
\author{John Doe \plusemail{john.doe@example.com}}
```

**Effect:** Adds email on a new line below author name in styled format

### Complete Box Reference

| Environment | Purpose | Visual Style |
|-------------|---------|--------------|
| `notation` | List notations/conventions | Theorem box, itemized |
| `keywords` | Document tags | Simple text with "Keywords:" |
| `caution` / `warning` | Warnings and common errors | Red box with ⚠ symbol |
| `question` | Inline questions | Boxed with "Question" label |
| `boxpar[title]` | General emphasis box | Colored box, optional title |
| `hardbox` | Difficulty marker | Box with ⚡ lightning icons |
| `abuse` | Notation abuse explanation | Theorem-style environment |

---

## Diagrams and Graphics

### Enabling Diagrams

```latex
\usepackage[diagrams]{nikolaoly}
```

### TikZ Diagrams

TikZ is always loaded and ready:

```latex
\begin{tikzpicture}
  \draw (0,0) circle (1);
  \draw (0,0) -- (1,0);
  \node at (0.5, -0.3) {$r=1$};
\end{tikzpicture}
```

### Commutative Diagrams (with `diagrams` option)

```latex
\begin{tikzcd}
  A \arrow{r}{f} \arrow{d}{g} & B \arrow{d}{h} \\
  C \arrow{r}{k} & D
\end{tikzcd}
```

### Asymptote Graphics (if installed)

Enable with (default on, or explicitly):

```latex
\usepackage[asy]{nikolaoly}

\begin{asy}
size(200);
draw((0,0)--(1,0)--(1,1)--(0,1)--cycle);
\end{asy}
```

---

## Advanced Features

### Hints and Answers System

Enable with:

```latex
\usepackage[hints]{nikolaoly}
```

Then use:

```latex
\prob[5]{}{Solve for $x$: $2x + 3 = 7$.}
\begin{hint}
Subtract 3 from both sides.
\end{hint}

\makehints  % Include collected hints
```

### Section Numbering for Theorems

```latex
\usepackage[secthm]{nikolaoly}

\section{Inequalities}
\begin{theorem}  % This is theorem 1.1
...
\end{theorem}

\begin{lemma}   % This is lemma 1.2
...
\end{lemma}

\section{Geometry}
\begin{theorem}  % This is theorem 2.1
...
\end{theorem}
```

### Colored Section Headings (KOMA-Script)

Works with `scrartcl`, `scrreprt`:

```latex
\documentclass{scrartcl}
\usepackage[colorsec]{nikolaoly}

\section{Introduction}      % Colored heading
\section{Main Results}      % Colored heading
```

---

## Title Page Decorations

### Enabling Title Decorations (Opt-in, v2.1+)

Starting with version 2.1, title decorations are **OFF by default**. To enable the decorative geometric pattern on your title page:

```latex
\usepackage[titledecorations]{nikolaoly}

\begin{document}
\nikolatitle  % Produces styled title with geometric decoration
\end{document}
```

### Without Decorations (Default)

```latex
\usepackage{nikolaoly}  % No decorations by default

\begin{document}
\nikolatitle  % Plain title, no decoration
\end{document}
```

You can also explicitly disable them if needed:

```latex
\usepackage[notitledecorations]{nikolaoly}
```

### What Are Title Decorations?

Title decorations add an elegant TikZ-based geometric pattern in the top-right corner of your title page, featuring:
- Rounded lines in your main color (`\maincolor`)
- Accent lines in your secondary color (`\secondcolor`)
- Multiple interconnected geometric shapes
- Professional, modern appearance perfect for handouts and problem sets

### Manual Title (Alternative)

If you prefer to style the title yourself without using `\nikolatitle`:

```latex
\documentclass{article}
\usepackage{nikolaoly}

\title{My Document}
\author{Your Name}
\date{\today}

\begin{document}

\maketitle  % Standard LaTeX title (no special formatting)

Content starts here...

\end{document}
```

---

## Section Leaf Icons

### Enabling Section Leaves (Opt-in, v2.1+)

Section leaves add a decorative leaf icon (🌿 using FontAwesome's `\faEnvira`) before section numbers. This is **OFF by default**.

To enable:

```latex
\usepackage[sectionleaves]{nikolaoly}

\section{Introduction}  % Will display: 🌿1 Introduction
\subsection{Background}  % Will display: 🌿1.1 Background
```

### Without Leaves (Default)

```latex
\usepackage{nikolaoly}  % No leaf icons

\section{Introduction}  % Will display: 1 Introduction
```

### Visual Effect

**With `sectionleaves`:**
- Section headings: `🌿1 Introduction`
- Subsection headings: `🌿1.1 Background`
- Subsubsection headings: `🌿1.1.1 Details`

**Without `sectionleaves` (default):**
- Section headings: `1 Introduction`
- Subsection headings: `1.1 Background`
- Subsubsection headings: `1.1.1 Details`

The leaf icon is rendered in your main color (`\maincolor`) for visual consistency.

### Combining with Colored Sections

For best results, combine section leaves with colored section headings:

```latex
\documentclass{scrartcl}  % Required for colorsec
\usepackage[sectionleaves, colorsec]{nikolaoly}

\section{Chapter One}  % Colored heading with leaf icon
```

---

## Troubleshooting

### Common Issues

**Q: The document won't compile. What's wrong?**

A: Check these steps:
1. Is `nikolaoly.sty` in the same directory as your `.tex` file or in your TEXMF path?
2. Try: `pdflatex --interaction=nonstopmode article.tex` to see the full error.
3. If you see font warnings, ensure you have all fonts installed (especially for Bulgarian).

**Q: Theorems look plain (no color boxes). How do I enable the fancy styling?**

A: Make sure you load the package with options. Try:
```latex
\usepackage{nikolaoly}  % Default is already fancy
```

If still plain, check that you're not using `\usepackage[nomdthm]{nikolaoly}`.

**Q: How do I change the color scheme?**

A: Use:
```latex
\usepackage[retro]{nikolaoly}       % Retro colors
\usepackage[darkmode]{nikolaoly}    % Dark mode
\changemaincolor{Blue}              % Change anytime
```

**Q: Can I use this with book or report classes?**

A: Yes. The package detects KOMA-Script classes and falls back to `fancyhdr` for others. Both work, but layout might differ slightly.

**Q: Bulgarian text doesn't appear. What's the issue?**

A: Install Cyrillic support:
```bash
# Ubuntu/Debian
sudo apt-get install texlive-lang-cyrillic

# Then use:
\usepackage[bulgarian]{nikolaoly}
```

**Q: Can I have some theorems with my custom styling?**

A: Define your own `\newmdtheoremenv` or use standard `\newtheorem` if you need full control.

**Q: The title page looks bare. Where are the decorations?**

A: Decorations are on by default. If missing:
1. Check that you're using `\nikolatitle` (not `\maketitle`).
2. Ensure no `\usepackage[notitledecorations]{nikolaoly}` is set.
3. Confirm you're in a KOMA-Script document class like `scrartcl` (decorations work best there).

---

## Complete Examples

### Example 1: Olympiad Problem Set

```latex
\documentclass{scrartcl}
\usepackage[retro, sleek]{nikolaoly}

\title{Regional Olympiad 2024}
\author{Mathematical Association}
\date{January 15, 2024}

\begin{document}
\nikolatitle

\problems
\minpt{20}

\prob[5]{Algebra}{
  Solve for all real $x$:
  $$x^3 + 3x^2 - 4x - 12 = 0$$
}

\prob[6]{Geometry}{
  In triangle $ABC$, let $I$ be the incenter. Prove that
  $$\angle BIC = 90° + \frac{\angle A}{2}$$
}

\req[9]{Combinatorics}{
  Find the number of sequences $(a_1, a_2, \ldots, a_{10})$ where
  each $a_i \in \{0, 1\}$ and at least two consecutive terms are $1$.
}

\end{document}
```

### Example 2: Lecture Notes with Dark Mode

```latex
\documentclass{scrartcl}
\usepackage[darkmode, bulgarian]{nikolaoly}

\title{Алгебра}
\author{Проф. Иван Иванов}
\date{\today}

\begin{document}
\nikolatitle

\section{Групи}

\begin{definition}
Група $(G, \cdot)$ наричаме множество $G$ с операция $\cdot$, такава, че:
\begin{enumerate}
  \item ...
\end{enumerate}
\end{definition}

\begin{example}
$(\ZZ, +)$ е абелева група...
\end{example}

\end{document}
```

### Example 3: Minimal Example Handout

```latex
\documentclass{article}
\usepackage[sleek, colorsec]{nikolaoly}

\title{Introduction to Inequalities}
\author{Math Department}

\begin{document}
\nikolatitle

\section{Basic Inequalities}

\begin{theorem}[Arithmetic Mean – Geometric Mean]
For non-negative reals $a_1, \ldots, a_n$:
$$\frac{a_1 + \cdots + a_n}{n} \geq \sqrt[n]{a_1 \cdots a_n}$$
Equality holds iff all $a_i$ are equal.
\end{theorem}

\begin{proof}
Proof goes here.
\end{proof}

\begin{remark*}
This is one of the most useful inequalities in competitions.
\end{remark*}

\begin{example}
For $a, b > 0$: $\sqrt{ab} \leq \frac{a+b}{2}$, with equality iff $a = b$.
\end{example}

\section{Applications}

\begin{exercise}
Show that for $a, b, c > 0$ with $abc = 1$:
$$a + b + c \ge 3$$
\end{exercise}

\end{document}
```

---

## Additional Resources

- **Theorem names** are automatically translated for Bulgarian documents.
- **Colors** are from the `xcolor` package, so any valid xcolor name works.
- **Fonts** use the `fontenc` package; ensure `LuaTeX` or `XeTeX` for advanced font features.
- **TikZ** is preloaded with common libraries; see TikZ documentation for advanced graphics.
- **Asymptote** requires the external `asy` binary; ensure it's in your PATH.

## Getting Help

If you encounter issues:
1. Check the [Troubleshooting](#troubleshooting) section above
2. Review the complete package source in `nikolaoly.sty` for inline comments
3. Run pdflatex with `--interaction=nonstopmode` for detailed error output
4. Ensure all package dependencies are installed
5. Reach out to [Nikola Veselinov](https://nikolaveselinov.github.io/)

---

## Changelog

### Version 2.1 (January 2026)
- **BREAKING CHANGE:** Title decorations now **OFF by default** (use `titledecorations` option to enable)
- **NEW:** Added `sectionleaves` option for decorative leaf icons (🌿) in section headings (OFF by default)
- **NEW:** Added `nosectionleaves` option for explicit control
- Improved Bulgarian language support
- Enhanced documentation with comprehensive option reference
- Added complete theorem environment listing
- Expanded math macro documentation

### Version 2.0 (January 2025)
- Original comprehensive release
- Based on Yu Dylan's style file with extensive enhancements
- Added Bulgarian language support
- Added dark mode and retro color schemes
- Comprehensive theorem environments
- 150+ math shortcuts

---

**Version:** 2.1 (January 2026)
**License:** Boost Software License 1.0

---

## Quick Start Checklist

- [ ] Install `nikolaoly.sty` in your document directory or TEXMF path
- [ ] Install required dependencies: `texlive-fonts-extra`, `texlive-science`, `texlive-lang-cyrillic` (for Bulgarian)
- [ ] Choose your options: `retro`, `darkmode`, `sleek`, `bulgarian`, `titledecorations`, `sectionleaves`, etc.
- [ ] Use `\nikolatitle` for styled title page
- [ ] Use `\changemaincolor{...}` to customize colors
- [ ] Explore theorem environments: `theorem`, `lemma`, `definition`, `example`, etc.
- [ ] Try math shortcuts: `\RR`, `\abs{x}`, `\floor{x}`, `\cycsum`, etc.
- [ ] Add boxes for emphasis: `notation`, `caution`, `boxpar`, `hardbox`
- [ ] For problem sets: Use `\problems`, `\prob[pts]{topic}{text}`, `\req`
- [ ] Compile with: `pdflatex document.tex`

**Happy typesetting!**
