# aidisclose — Generative AI disclosure checklist and statements

[![CTAN](https://img.shields.io/ctan/v/aidisclose)](https://ctan.org/pkg/aidisclose)
[![License: LPPL 1.3c](https://img.shields.io/badge/license-LPPL%201.3c-blue)](https://www.latex-project.org/lppl/lppl-1-3c/)
[![LaTeX](https://img.shields.io/badge/LaTeX-LaTeX2e%202020%2F10%2F01%2B-brightgreen)](https://www.latex-project.org/)

## Overview

**aidisclose** is a LaTeX package that helps authors produce a clear, structured disclosure of how **Generative Artificial Intelligence (GAI)** tools were used when preparing a manuscript.

The **aidisclose** package provides:

- a taxonomy-based checklist of delegated tasks (GAIDeT-style identifiers);
- a responsibility statement attributing final responsibility to the human author(s);
- reporting of the GAI tools used;
- optional additional comments (numbered or unnumbered);
- a single command to render the whole disclosure block.

GAI tools are not listed as authors and do not bear responsibility for the final outcomes.

## Installation

### Via CTAN

```text
tlmgr install aidisclose
```

### Manual installation

Place `aidisclose.sty` either next to your document or in a local `texmf` tree.

## Quick start

```tex
\usepackage{aidisclose}

% —————————————————————————————————————————————————————
% Configuration 

% Optional: customize the title (short, long, and optional sectioning command)
\GAIdiscloseTitle[AI disclosure]{Generative AI Disclosure Statement}[section]

% Select checklist items from the taxonomy
% The full list is available in the aidisclose-doc.pdf file
\GAIactivate{c:idea}
\GAIactivate{l:search}

% Declare tools used
\GAItoolsUsed{ChatGPT-5.2, Gemini-3}

% Optional: add comments
% non-stared comments are numbered sequentially
% stared comments are not numbered
\begin{GAIcomment}
GAI tools were used for language editing only.
\end{GAIcomment}

\begin{GAIcomment*}
No GAI tools were used for data analysis.
\end{GAIcomment*}

% —————————————————————————————————————————————————————
% Declaration rendering 

% Render the disclosure (optional argument = number of columns, default 3)
\GAIrenderDeclaration[3]{Alice Smith, Bob Jones}
```

## Public interface

### `\GAIrenderDeclaration`

Render the full disclosure block (title, statement, checklist, tools, comments).

```tex
\GAIrenderDeclaration[<cols>]{<authors>}
```

- `<cols>`: number of columns used for the checklist (default: `3`)
- `<authors>`: comma-separated author list

Examples:

```tex
\GAIrenderDeclaration{Jane Doe}
\GAIrenderDeclaration[2]{Jane Doe, John Doe, Mary Doe}
```

### `\GAIdiscloseTitle`, `\GAIdiscloseTitleLong`, `\GAIdiscloseTitleShort`

Set the title used when rendering the disclosure.

```tex
\GAIdiscloseTitle[<short>]{<long>}[<sectioning cmd>]
```

- If `<short>` is omitted, it defaults to `<long>`.
- If `<sectioning cmd>` is omitted/blank, the package picks `\chapter` when available, otherwise `\section`.

Examples:

```tex
\GAIdiscloseTitle{Disclosure of Delegation to Generative AI}
\GAIdiscloseTitle[Disclosure]{Disclosure of Delegation to Generative Artificial Intelligence}[\section*]

% Retrieve stored titles
\GAIdiscloseTitleLong
\GAIdiscloseTitleShort
```

### `\GAIactivate`

Activate a checklist item by its taxonomy identifier (e.g., `c:idea`, `l:search`).

```tex
\GAIactivate{<id>}
```

Example:

```tex
\GAIactivate{c:idea}
\GAIactivate{w:edit}
```

### `\GAItoolsUsed`

Declare the tools used (comma-separated list). This text is rendered as a sentence in the disclosure.

```tex
\GAItoolsUsed{<tool list>}
```

Example:

```tex
\GAItoolsUsed{ChatGPT-5.2, Gemini 3 Pro}
```

### `GAIcomment` and `GAIcomment*` environments

Add comments to the disclosure:

- `GAIcomment` is **numbered** and increments an internal counter.
- `GAIcomment*` is **unnumbered** and does not increment the counter.

```tex
\begin{GAIcomment}
...
\end{GAIcomment}

\begin{GAIcomment*}
...
\end{GAIcomment*}
```

### `\GAIsetChecklistFontSize` (optional)

Change the font size used when rendering the checklist:

```tex
\GAIsetChecklistFontSize{\small}
```

(The default in the package is `\smaller`.)

### `\GAIsetCheckmarkSymbol` (optional)

Change the symbol used inside the framed checkbox:

```tex
\GAIsetCheckmarkSymbol{\checkmark}
```

This also updates the internal width so checked/unchecked boxes align.

## Dependencies

`aidisclose` uses only standard LaTeX packages:

- `expl3`
- `xparse`
- `amssymb`
- `multicol`
- `enumitem`
- `relsize`

## Documentation

See `aidisclose-doc.tex` for the full manual, including the list of supported taxonomy identifiers and more examples.

## License

This package is distributed under the **LaTeX Project Public License (LPPL) 1.3c** or later.

## Disclaimer

This package helps authors format disclosures; it does not enforce any specific policy. Authors remain fully responsible for the manuscript content and for compliance with institutional, publisher, or legal requirements regarding the use of Generative AI tools.
