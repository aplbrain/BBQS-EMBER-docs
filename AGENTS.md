# Agent instructions

Guidance for AI coding agents (and humans) working in this repository.

## What this repository is

User documentation for the EMBER Archive, built with MkDocs (Material theme) from the `docs/` directory and published to https://docs.emberarchive.org. See `README.md` for how to preview the site locally.

## Secondary, GitHub-only markdown

Some material is meant to be read on GitHub and is deliberately **not** part of the built site. It lives outside `docs/` so MkDocs never picks it up. Do not add it to `mkdocs.yml`, and do not move it under `docs/`.

- `user-stories/`: user stories for tools in the EMBER ecosystem. Its `README.md` explains the format and how to contribute, and `story-template.md` is the starting point for a new story. Each tool gets a folder with a `README.md` that introduces the tool and indexes its stories, plus one `story-<counter>-<descriptor>.md` file per story.

Style for these pages:

- Do not use task-list checkboxes (`- [ ]`). Acceptance criteria and similar lists are plain bullets.

## Mermaid diagrams

GitHub renders Mermaid natively in markdown files, so GitHub-only pages can use ` ```mermaid ` fences directly.

- **Do not insert `<br/>` (or `<br>`) line breaks in node or edge labels.** The renderer sizes and wraps labels on its own and the result looks better without manual breaks. Write labels as plain single-line text.
- Keep labels short enough to read at a glance; move detail into the surrounding prose instead of the diagram.
- **Lay flowcharts out vertically** (`flowchart TB`, or `TD`). A left-to-right chart grows as wide as the longest path, which forces horizontal scrolling on a laptop or phone; the same chart top-to-bottom stays within the reading column and scrolls the way a page normally does. Use `LR` only for a chart small enough to stay narrow, and check the rendered width before settling on it. Sequence diagrams are inherently horizontal, so keep the number of participants down instead.
- Diagram types known to render on GitHub and used here: `flowchart`, `sequenceDiagram`, `stateDiagram-v2`.

### Never let label text sit on top of a line

Mermaid draws message and edge labels with no background fill, so any line running behind a label shows through the gaps between the letters and makes it hard to read. Keep text and lines apart:

- **Sequence diagrams.** Order the participants so every message runs between two neighbouring lifelines; an arrow that spans a third participant puts its label on top of that participant's lifeline. Reordering is usually enough, and it is what story 1 does.
- **Self-messages.** A self-message (`A->>A: ...`) always centres its label on its own lifeline. Use `Note over A: ...` instead: notes are drawn as a filled box, so nothing shows through. Story 4 does this.
- **Flowcharts.** Edge labels are drawn with a background box, so they sit on the line cleanly and need no special handling.
- Set `%%{init: {"sequence": {"mirrorActors": false}}}%%` on sequence diagrams so the participant row is drawn once, at the top, rather than repeated at the bottom.

After changing a diagram, render it and look at it before pushing; a label that overlaps a lifeline is easy to miss when reading only the source.
