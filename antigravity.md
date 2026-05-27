# AI Agent Guidelines (antigravity.md)

This file contains instructions, constraints, and guidelines for AI coding assistants (like Antigravity, Claude, or Cursor) working on this Reykjavik University MSc Thesis LaTeX project.

---

## 🛠️ Compilation & Build Environment

> [!IMPORTANT]
> **Compiler Constraint:** You MUST compile this project using **LuaLaTeX** and **Biber**. 
> Do **NOT** use `pdfLaTeX` or `pdftex`, as the project loads OpenType system fonts using `fontspec` (`TeX Gyre Termes` and `TeX Gyre Heros`).

### Build Sequence
To build the project cleanly, run:
```bash
latexmk -lualatex -bibtex -f main.tex
```
To clean auxiliary files, run:
```bash
latexmk -C
```

---

## 📐 Document Structure & Layout Constraints

### 1. Double-Sided odd Page Alignment
*   **Rule:** Every major front matter section (Copyright, Abstract, Preface, Acknowledgments, lists, Glossary) and Chapter 1 (Introduction) MUST start on an **odd (right-hand) page** in the final PDF.
*   **Implementation:** Use the custom command `\RUcleardoublepage` in [main.tex](file:///Users/fomaximus/github/RU_APA7_Thesis/main.tex) immediately preceding each section input. This automatically inserts blank, unnumbered even pages where required for print binding.
*   **Paging Flow:** Do not modify the page counter manual overrides in `main.tex`.

### 2. Heading Numbering (APA7 Standard)
*   **Rule:** Do **NOT** enable section numbering for headings in the main body or back matter. 
*   **Implementation:** Keep `\setcounter{secnumdepth}{0}` active in [preamble/formatting.tex](file:///Users/fomaximus/github/RU_APA7_Thesis/preamble/formatting.tex). All sections (including references and appendices) must remain unnumbered to conform to standard APA 7th edition manuscript format.

### 3. Hyperlink Styling (Print-Ready Standard)
*   **Rule:** Hyperlinks (citations, cross-references, URLs, DOIs) must render as **black text** with no underlines to ensure a clean layout when printed in black and white.
*   **Implementation:** Ensure `urlcolor=black`, `linkcolor=black`, and `citecolor=black` are set inside the `\hypersetup` block in [preamble/formatting.tex](file:///Users/fomaximus/github/RU_APA7_Thesis/preamble/formatting.tex).

### 4. Single-Spaced Front Matter Lists
*   **Rule:** The Table of Contents, List of Tables, List of Figures, List of Abbreviations, Glossary, and List of Symbols must be single-spaced.
*   **Implementation:** Wrap these front matter include blocks inside a `singlespace` environment in `main.tex`.

---

## 📁 Repository Architecture & Configurable Locations

*   **Preamble / Variables:** When updating thesis parameters (title, author, degree, supervisor names, examiner, date), edit **ONLY** [preamble/metadata.tex](file:///Users/fomaximus/github/RU_APA7_Thesis/preamble/metadata.tex). Do not hardcode values in `main.tex` or front matter files.
*   **Front Matter Files:** Located in `frontmatter/`.
*   **Main Chapters:** Located in `chapters/` (ordered sequentially `01_introduction.tex`, `02_literature.tex`, etc.).
*   **Glossary Layout:** If adding terms to [frontmatter/glossary.tex](file:///Users/fomaximus/github/RU_APA7_Thesis/frontmatter/glossary.tex), use a `tabular` environment with paragraph width columns (`p{width}`) to enable word wrapping and prevent horizontal overflowing.
*   **Appendices:** Located in `appendices/`.
*   **References:** Bibliography database is located in [references/references.bib](file:///Users/fomaximus/github/RU_APA7_Thesis/references/references.bib) and citations should follow standard `biblatex-apa` guidelines.
