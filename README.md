# Varro RR Public Repository

Public export of the Varro *Res rusticae* treebank project: the corpus in its current review state, and a working pilot of the annotation-manual documentation. Both are approved subsets of a private working repository, exported verbatim (byte-identical for the corpus files).

## Corpus

- [`corpus/RR_reviewed.conllu`](corpus/RR_reviewed.conllu): the reviewed corpus (bronze/silver review status) -- the current state of the treebank proper.
- [`corpus/RR_pending.conllu`](corpus/RR_pending.conllu): material not yet reviewed.
- [`corpus/RR_UD_ALDT.conllu`](corpus/RR_UD_ALDT.conllu): an audited UD-vs-ALDT/PDT comparison tree for one batch of sentences (S000036-S000091), sentence-aligned 1:1 with `RR_reviewed.conllu` by `sent_id`. Its `DEPS` column holds the ALDT/PDT-style analytical tree for comparison, not this project's own Enhanced Dependencies; internal review-workflow annotation (review notes, tags, editorial-variant and syntax-note markup) is omitted here and should be looked up in `RR_reviewed.conllu` by `sent_id` instead.

These are working exports, not a finished release: `RR_pending.conllu` will shrink and `RR_reviewed.conllu` will grow as review continues, and both may be regenerated wholesale rather than diffed incrementally.

## Documentation

- [`documentation/annotation-guidelines.md`](documentation/annotation-guidelines.md): working outline and drafted introductory chapters of the annotation manual.

The document describing how this manual relates to the private policy, workflow, validation, and source registers (`documentation-plan.md`) is itself internal planning material rather than reader-facing content, and is kept in the private repository only.

## Status

This is a working export, not a stable release:

- most UPOS, FEATS, and dependency-relation sections of the manual are represented by structured placeholders;
- manual examples are provisional unless explicitly identified as accepted project analyses;
- the private workbook and internal policy register remain authoritative during development;
- the manual will be regenerated and edited for reader-friendliness as its structure stabilizes;
- corpus files may be replaced wholesale on the next export rather than updated incrementally.

## Editorial principles (documentation)

1. Present the annotation scheme as a coherent linguistic system, not as a spreadsheet export.
2. State criteria before examples.
3. Treat examples as illustrative rather than exhaustive.
4. Distinguish general Universal Dependencies policy, Latin UD practice, harmonized Latin conventions, and project-specific decisions.
5. Keep internal identifiers available for traceability in the private documentation, but omit them from the main public exposition unless they help the reader.
6. Connect conceptual annotation layers to their concrete CoNLL-U representation from the outset.

## Inspiration

The manual's overall presentation takes inspiration from the clear layered organization of the *Guidelines for the Ancient Greek Dependency Treebank 2.5*. The Varro RR scheme itself follows Universal Dependencies rather than the Prague-style scheme used by that document.
