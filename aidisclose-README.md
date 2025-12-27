# aidisclose – Generative AI disclosure checklist for LaTeX

[![CTAN](https://img.shields.io/ctan/v/aidisclose)](https://ctan.org/pkg/aidisclose)
[![Version](https://img.shields.io/badge/version-1.4.0-blue)](https://github.com/joaomlourenco/aidisclose)
[![Date](https://img.shields.io/badge/date-2025--12--25-orange)](https://github.com/joaomlourenco/aidisclose)
[![License: LPPL 1.3c](https://img.shields.io/badge/license-LPPL%201.3c-blue)](https://www.latex-project.org/lppl/lppl-1-3c/)
[![LaTeX](https://img.shields.io/badge/LaTeX-LaTeX2e%202020%2F10%2F01%2B-brightgreen)](https://www.latex-project.org/)

**aidisclose** is a LaTeX package that helps authors produce clear, standardized disclosures describing how **Generative Artificial Intelligence (GAI)** tools were used in preparing a manuscript.

The package implements the **GAIDeT (Generative AI Delegation Taxonomy)**, enabling transparent, structured, and responsibility-aware AI disclosure aligned with emerging publisher and institutional policies.

Full documentation (complete taxonomy, commands, and examples) is available in **[aidisclose-doc.pdf](aidisclose-doc.pdf)**.

---

## Key ideas

- GAI tools are not authors and bear no responsibility for the final work
- Human authors retain full responsibility for accuracy, integrity, and compliance
- Disclosure is based on tasks delegated to GAI, not on tool branding

---

## Main features

- Checklist based on the GAIDeT taxonomy (50+ task identifiers)
- Automatic responsibility and disclosure statements
- Simple activation of delegated tasks via short taxonomy keys
- Optional listing of GAI tools used
- Numbered and unnumbered explanatory comments
- Configurable titles, symbols, and checklist layout

---

## Minimal usage example

```tex
\usepackage{aidisclose}

% Activate delegated tasks
\GAIactivate{c:idea}
\GAIactivate{l:search}
\GAIactivate{w:proof}

% Declare tools used
\GAItoolsUsed{ChatGPT, Claude}

% Render disclosure
\GAIrenderDeclaration{Alice Smith, Bob Jones}
```

This produces a complete disclosure section including:

- A responsibility statement
- A taxonomy-based checklist
- A tools-used declaration

---

## Installation

Via CTAN:

```bash
tlmgr install aidisclose
```

Or install manually by placing `aidisclose.sty` in your local `texmf` tree.

---

## Documentation

For details beyond this overview, please consult:

- [aidisclose-doc.pdf](aidisclose-doc.pdf) – complete manual
- [aidisclose-doc.tex](aidisclose-doc.tex) – LaTeX source of the documentation
- https://ctan.org/pkg/aidisclose

The PDF includes:

- The full GAIDeT taxonomy reference
- All public commands and options
- Advanced customization examples
- Best-practice guidance

---

## License

Released under the LaTeX Project Public License (LPPL) 1.3c or later.

---

Copyright © 2025 João M. Lourenço.  
Crafted with 💙 for reproducible scientific writing.
