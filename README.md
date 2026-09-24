# Varro RR Public Repository

A Universal Dependencies treebank of Varro's *Res rusticae*: the corpus in its current review state, and the accompanying annotation manual.

## Background

This treebank's choice of framework continues a specific line of prior work rather than starting from a blank slate: dependency-based treebanking for Ancient Greek and Latin, developed from the 1990s onward within the Prague School tradition and continued by the Ancient Greek and Latin Dependency Treebank (AGLDT) and its Perseus-associated successors, more recently converted into and harmonized under Universal Dependencies. This treebank draws on both traditions rather than treating UD as a self-sufficient theoretical starting point: categories and interpretive habits inherited from the older, more philologically oriented Prague/AGLDT tradition inform decisions in the annotation manual wherever UD's own guidance is underspecified for Latin. Where the manual sets out a specific point of contrast with that tradition's own analysis, it marks the spot with a callout box labelled "ALDT comparison" (for example, Section 1.3.3, on nonverbal predication) -- [`corpus/RR_UD_ALDT.conllu`](corpus/RR_UD_ALDT.conllu), described below, gives the fullest such comparison as an actual parallel analysis rather than a discussion in prose.

## Corpus

- [`corpus/RR_reviewed.conllu`](corpus/RR_reviewed.conllu): the reviewed corpus (bronze/silver review status) -- the current state of the treebank proper.
- [`corpus/RR_pending.conllu`](corpus/RR_pending.conllu): material not yet reviewed.
- [`corpus/RR_UD_ALDT.conllu`](corpus/RR_UD_ALDT.conllu): an audited UD-vs-ALDT/PDT comparison tree for one batch of sentences (S000036-S000091), sentence-aligned 1:1 with `RR_reviewed.conllu` by `sent_id`. Its `DEPS` column holds the ALDT/PDT-style analytical tree for comparison, not this treebank's own Enhanced Dependencies; internal review-workflow annotation (review notes, tags, editorial-variant and syntax-note markup) is omitted here and should be looked up in `RR_reviewed.conllu` by `sent_id` instead.

`RR_pending.conllu` will shrink and `RR_reviewed.conllu` will grow as review continues; both may be replaced wholesale on a future export rather than updated incrementally.

## Browsing the corpus

**[Open the live browser](https://jannejniemi.github.io/varro-rr/conllu-browser.html)** -- dependency trees (Basic and Enhanced), a flat table view, and per-sentence metadata for any sentence in the corpus. Use the *Reviewed* / *Pending* / *ALDT comparison* buttons to load the matching file.

[`conllu-browser.html`](conllu-browser.html) is the self-contained, client-side viewer behind that link: nothing is sent anywhere, it parses and renders entirely in your browser. If you'd rather run it yourself instead of using the hosted copy -- cloned locally, or served some other way -- the same *Reviewed*/*Pending*/*ALDT comparison* buttons work wherever the page is served over http(s); opened directly as a local file, browsers block it from reading its neighbouring files, so use "Open file…" or drag one of the `corpus/*.conllu` files onto the page instead.

## Documentation

- [`documentation/annotation-guidelines.md`](documentation/annotation-guidelines.md): the annotation manual, covering the treebank's full structure -- lexicon and morphology, Basic and Enhanced syntax, Latin and Varronian constructions, and text/discourse/provenance metadata. Its overall presentation takes inspiration from the *Guidelines for the Ancient Greek Dependency Treebank 2.5*; the annotation scheme itself follows Universal Dependencies rather than that document's Prague-style scheme.

A companion planning document, describing how this manual relates to this treebank's internal policy, workflow, and validation records, is kept in the private repository only.
