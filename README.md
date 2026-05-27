# RU APA7 MSc Thesis

> A well-architected LaTeX project using the CTAN **apa7** document class for a Master's thesis at Reykjavik University, formatted for peer-reviewed journal publication.

## Prerequisites

| Requirement | Version | Notes |
|---|---|---|
| TeX Distribution | TeX Live 2023+ or MacTeX 2023+ | Must include `apa7`, `biblatex-apa` |
| Compiler | **LuaLaTeX** | Required for `fontspec` font loading |
| Bibliography | **Biber** | Required by `biblatex-apa` |
| Build Tool | **Latexmk** (recommended) | Automates multi-pass compilation |

### Quick Install Check

```bash
# Verify tools are available
lualatex --version
biber --version
latexmk --version

# Verify apa7 package is installed
kpsewhich apa7.cls
```

## Build Instructions

### Using Latexmk (Recommended)

```bash
# Full build (compiles LuaLaTeX → Biber → LuaLaTeX → LuaLaTeX)
latexmk

# Watch mode — auto-recompile on file changes
latexmk -pvc

# Clean auxiliary files
latexmk -c

# Clean everything including PDF
latexmk -C
```

### Manual Compilation

```bash
lualatex main.tex
biber main
lualatex main.tex
lualatex main.tex
```

The triple compilation is needed for:
1. First pass: Generate `.aux` file with citation keys
2. Biber: Process bibliography
3. Second pass: Resolve references
4. Third pass: Finalize cross-references and page numbers

## Project Structure

```
RU_APA7_Thesis/
├── main.tex                    # Master document (entry point)
├── preamble/
│   ├── packages.tex            # All \usepackage declarations
│   ├── metadata.tex            # Title, author, affiliation variables
│   ├── formatting.tex          # Custom formatting & hyperref setup
│   └── macros.tex              # Convenience commands & abbreviations
├── frontmatter/
│   ├── abstract.tex            # English abstract (max 300 words)
│   ├── abstract_is.tex         # Icelandic abstract (Útdráttur)
│   ├── dedication.tex          # Dedication page
│   ├── acknowledgments.tex     # Acknowledgments
│   ├── abbreviations.tex       # List of abbreviations
│   ├── glossary.tex            # Glossary of terms
│   └── symbols.tex             # List of symbols
├── chapters/
│   ├── 01_introduction.tex     # Introduction
│   ├── 02_literature.tex       # Literature Review
│   ├── 03_methods.tex          # Methods
│   ├── 04_results.tex          # Results
│   ├── 05_discussion.tex       # Discussion
│   └── 06_conclusion.tex       # Conclusion
├── appendices/
│   ├── appendix_a.tex          # Appendix A: Survey Instrument
│   └── appendix_b.tex          # Appendix B: Supplementary Tables
├── figures/                    # Figure files (.png, .pdf, .eps)
├── tables/                     # Standalone table files (optional)
├── references/
│   └── references.bib          # BibTeX bibliography database
├── .gitignore                  # LaTeX-specific gitignore
├── .latexmkrc                  # Latexmk configuration
├── LICENSE                     # MIT License
└── README.md                   # This file
```

## APA7 Configuration

| Setting | Value |
|---|---|
| Document class | `apa7` (CTAN) |
| Mode | `man` (professional manuscript) |
| Font size | 12pt |
| Paper | A4 |
| Figures | Inline (`floatsintext`) |
| Citations | `biblatex-apa` with `biber` |
| Font | TeX Gyre Termes (Times New Roman equivalent) |

## APA7 Heading Levels

| Level | LaTeX Command | Rendering |
|---|---|---|
| 1 | `\section{}` | Centered, Bold |
| 2 | `\subsection{}` | Flush Left, Bold |
| 3 | `\subsubsection{}` | Flush Left, Bold Italic |
| 4 | `\paragraph{}` | Indented, Bold, Period. Text continues. |
| 5 | `\subparagraph{}` | Indented, Bold Italic, Period. Text continues. |

## Citation Quick Reference

```latex
% Parenthetical citation: (Author, Year)
\parencite{Vial2019}

% Narrative citation: Author (Year)
\textcite{Vial2019}

% Multiple citations: (Author1, Year; Author2, Year)
\parencite{Vial2019,Duchek2020}

% Citation with page number: (Author, Year, p. 42)
\parencite[p.~42]{Vial2019}

% Direct quote attribution: Author (Year) stated "..." (p. 42)
\textcite[p.~42]{Vial2019}
```

## Customization

### Changing Author Details

Edit `preamble/metadata.tex` — all metadata is defined as LaTeX commands:

```latex
\newcommand{\thesisTitle}{Your Title Here}
\newcommand{\thesisAuthor}{Your Name}
\newcommand{\thesisSupervisor}{Dr.\ Supervisor Name}
% ... etc.
```

### Adding a Chapter

1. Create a new file in `chapters/` (e.g., `07_new_chapter.tex`)
2. Add `\input{chapters/07_new_chapter}` in `main.tex`

### Adding References

Add BibTeX entries to `references/references.bib` and cite them with `\parencite{}` or `\textcite{}`.

## Draft Utilities

The template includes draft-mode helpers (remove before final submission):

```latex
\todo{Remember to update this section}   % Red TODO marker
\fixme{Check this calculation}            % Orange FIXME marker
\note{Consider adding more detail}        % Blue NOTE marker
\lipsum[1]                                % Generate dummy paragraph
```

## License

This template is provided under the MIT License. See [LICENSE](file:///Users/fomaximus/github/RU_APA7_Thesis/LICENSE) for details. The `apa7` document class is maintained by Daniel A. Weiss on [CTAN](https://ctan.org/pkg/apa7).
