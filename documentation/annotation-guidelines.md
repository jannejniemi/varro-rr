# Varro RR Annotation Guidelines

> **Work in progress, 13 October 2026.** This document sets out the structure of the Varro RR annotation manual, with prose drafted throughout. It is not yet a release-authoritative specification.

## Contents

1. [Introduction](#1-introduction)
   1. [Scope of the treebank](#11-scope-of-the-treebank)
   2. [Annotation layers and the CoNLL-U format](#12-annotation-layers-and-the-conll-u-format)
   3. [Key concepts](#13-key-concepts)
   4. [Sources of authority](#14-sources-of-authority)
   5. [How to use these guidelines](#15-how-to-use-these-guidelines)
2. [Lemmas and Parts of Speech](#2-lemmas-and-parts-of-speech)
   1. [General lemma and UPOS principles](#21-general-lemma-and-upos-principles)
   2. [The UPOS inventory](#22-the-upos-inventory)
   3. [The `DET` / `PRON` boundary](#23-the-det--pron-boundary)
   4. [Lexicalized participles and the `ADJ` / `VERB` boundary](#24-lexicalized-participles-and-the-adj--verb-boundary)
   5. [Copular and auxiliary uses of *sum*](#25-copular-and-auxiliary-uses-of-sum)
   6. [Foreign, corrupt, and unanalysed material](#26-foreign-corrupt-and-unanalysed-material)
3. [Morphological Features](#3-morphological-features)
   1. [Core features](#31-core-features)
   2. [Classificatory features](#32-classificatory-features)
   3. [Compatibility features](#33-compatibility-features)
4. [Basic Syntax](#4-basic-syntax)
   1. [Predicates and roots](#41-predicates-and-roots)
   2. [Voice and the passive](#42-voice-and-the-passive)
   3. [Subjects](#43-subjects)
   4. [Objects, obliques, and adverbial modifiers](#44-objects-obliques-and-adverbial-modifiers)
   5. [Nominal modification](#45-nominal-modification)
   6. [Clausal complements](#46-clausal-complements)
   7. [Adverbial clauses](#47-adverbial-clauses)
   8. [Relative clauses](#48-relative-clauses)
   9. [Coordination](#49-coordination)
   10. [Copulas and auxiliaries](#410-copulas-and-auxiliaries)
   11. [Fixed expressions and flat structures](#411-fixed-expressions-and-flat-structures)
   12. [Parataxis and reported speech](#412-parataxis-and-reported-speech)
   13. [Discourse elements](#413-discourse-elements)
   14. [Punctuation](#414-punctuation)
   15. [Choosing between relations](#415-choosing-between-relations)
5. [Enhanced Syntax](#5-enhanced-syntax)
   1. [General Enhanced principles](#51-general-enhanced-principles)
   2. [Propagated and shared dependents](#52-propagated-and-shared-dependents)
   3. [Empty nodes](#53-empty-nodes)
   4. [Ellipsis](#54-ellipsis)
   5. [Secondary predication](#55-secondary-predication)
   6. [Syllepsis](#56-syllepsis)
   7. [`InheritedFrom` metadata](#57-inheritedfrom-metadata)
6. [Latin and Varronian Constructions](#6-latin-and-varronian-constructions)
   1. [Ablative absolute](#61-ablative-absolute)
   2. [*Participium coniunctum* and secondary predication](#62-participium-coniunctum-and-secondary-predication)
   3. [Accusative and infinitive](#63-accusative-and-infinitive)
   4. [Gerund and gerundive](#64-gerund-and-gerundive)
   5. [Free relative clauses](#65-free-relative-clauses)
   6. [Comparison](#66-comparison)
   7. [Ellipsis and orphan structures](#67-ellipsis-and-orphan-structures)
   8. [Reporting expressions and dialogue](#68-reporting-expressions-and-dialogue)
   9. [Active and passive supines](#69-active-and-passive-supines)
   10. [Dislocation and prolepsis](#610-dislocation-and-prolepsis)
   11. [Retrievable Varronian constructions recorded with `SyntaxNote`](#611-retrievable-varronian-constructions-recorded-with-syntaxnote)
7. [Text, Discourse, and Review Metadata](#7-text-discourse-and-review-metadata)
   1. [Accepted text and original form](#71-accepted-text-and-original-form)
   2. [Token-local variants](#72-token-local-variants)
   3. [Structural variants](#73-structural-variants)
   4. [Alternative and revised sentence records](#74-alternative-and-revised-sentence-records)
   5. [Speaker attribution](#75-speaker-attribution)
   6. [`DiscourseMode`](#76-discoursemode)
   7. [`SyntaxNote`](#77-syntaxnote)
   8. [Review notes and tags](#78-review-notes-and-tags)
   9. [Review status](#79-review-status)

---

## 1. Introduction

### 1.1 Scope of the treebank

The Varro RR treebank annotates Varro's *Res rusticae* in Universal Dependencies (UD), following harmonized Latin UD conventions and adding a small number of stated treebank-specific decisions. Where UD is underspecified for Latin, the Prague-style tradition of the Ancient Latin Dependency Treebank (ALDT) informs the decision; boxes marked *ALDT comparison* set out the contrasts (Section 1.5).

Besides the dependency trees, the CoNLL-U records carry textual normalization, editorial variants, alternative analyses, speaker and discourse labels, review notes, review status, and labels for constructions that ordinary dependency queries cannot find.

### 1.2 Annotation layers and the CoNLL-U format

A [CoNLL-U](https://universaldependencies.org/format.html) file is a sequence of sentence records separated by a blank line. One token row may carry lexical, morphological, Basic, Enhanced, and treebank-specific information; the subsections below take these layers one by one.

#### 1.2.1 Sentence records and sentence metadata

A record consists of `#` comment lines with sentence metadata, then one row per syntactic word, multiword-token range, or empty node in ascending `ID` order, with no blank lines inside the record:

```conllu
# sent_id = S000001
# edition_loc = 1.1.1
# text = otium si essem consecutus, Fundania, ...
# review_status = silver
# speaker = Narrator
```

The keys that identify and structure the record:

- `sent_id`: the unique sentence identifier, stable once assigned.
- `edition_loc`: the text location (for example `1.2.17`), with section numbering as in the working text (LacusCurtius). A sentence that crosses a section boundary lists every section it covers, in text order, separated by a semicolon (`# edition_loc = 1.2.3;1.2.4`); the first token of each later section carries `NextLoc` (Section 1.2.7).
- `text`: the accepted surface text, lower-cased at the sentence boundary; `text_old`: the transmitted text before that normalization.
- `text_en`, `text_fr`, `text_fi`: English, French, and Finnish translations.
- `source_sentence` / `source_sentences` and `alt_type`: on an alternative record, the sentence or sentences it derives from and, for a resegmentation, the kind of divergence (Section 7.4).

Review status, speaker, and structural variants have their own keys, treated in Chapter 7. A silver or gold record carries no working markers: they are removed when the sentence is committed at silver.

#### 1.2.2 Columns, tokens, and lexical representation

Each row has ten tab-separated fields:

| # | Field | Content |
|---|---|---|
| 1 | `ID` | Word index, multiword-token range, or decimal empty-node index |
| 2 | `FORM` | Accepted surface form |
| 3 | `LEMMA` | Lemma |
| 4 | `UPOS` | Universal part of speech |
| 5 | `XPOS` | Not used; `_` |
| 6 | `FEATS` | Morphological features |
| 7 | `HEAD` | Basic governor (`0` for the root) |
| 8 | `DEPREL` | Basic relation to `HEAD` |
| 9 | `DEPS` | Enhanced dependencies |
| 10 | `MISC` | Other token metadata |

An empty field is `_`. A syntactic-word row always has `LEMMA`, `UPOS`, `HEAD`, and `DEPREL`. Tokenization is part of the annotation: changing a token boundary renumbers the later tokens and every reference to them.

#### 1.2.3 Multiword tokens

A multiword token is one orthographic token that contains more than one syntactic word. Its row has a range `ID` (`4-5`), the surface form in `FORM`, and `_` elsewhere; each syntactic word then has its own row with an integer `ID` inside the range and a full analysis.

**Corpus examples**

- *id nobiscum una videatis* ‘you look into this together with us’ (S000082): *nobis* (4) `obl`; *cum* (5) `case`. The orthographic token nobiscum is a multiword token (range 4-5) split into two syntactic words, each with its own analysis.

#### 1.2.4 Morphological annotation

`FEATS` holds `Feature=Value` pairs in alphabetical order, separated by vertical bars:

```conllu
Case=Acc|Gender=Neut|InflClass=IndEurO|Number=Sing
```

`TraditionalMood`, which names the gerund, gerundive, and supine, is a `MISC` key, not a feature (Section 3.3.2).

#### 1.2.5 Basic dependency syntax

`HEAD` and `DEPREL` form the Basic tree: every syntactic word has exactly one governor and one relation, and the root is governed by `0`. Where ellipsis or sharing makes the structure richer than a tree, the Basic layer chooses one analysis and the Enhanced layer adds the rest.

#### 1.2.6 Enhanced dependency syntax and empty nodes

`DEPS` holds the Enhanced graph as a `|`-separated list of `head:relation` pairs, one per incoming edge. It adds to the Basic tree and never replaces it. In this treebank `DEPS` is sparse until gold: it lists only the edges that differ from the Basic tree, and only of the kinds listed in Section 5.1.

An empty node has a decimal `ID` (`17.1`) and stands for an elided predicate (Section 5.3). `FORM` is filled where the elided word is clear from context, and `UPOS` may stand in for it; `LEMMA`, `XPOS`, `FEATS`, `HEAD`, and `DEPREL` are always `_`, and the node's whole contribution is in `DEPS`.

**Corpus examples**

- *non solum adimis domino pecus, sed etiam servis peculium* ‘you not only take the flock from the master, but also [take] their savings from the slaves’ (S000096): *adimis* (17.1) `DEPS` 10:conj, `InheritedFrom=S000096:10`; *peculium* (17) `DEPS` 17.1:obj; *servis* (16) `DEPS` 17.1:obl:arg. The empty node 17.1 has FORM filled and LEMMA, HEAD and DEPREL left as _; its whole contribution is carried by DEPS.

#### 1.2.7 `MISC`: treebank metadata and analytical notes

`MISC` is a `|`-separated list of `Key=Value` pairs, with the keys in alphabetical order. The keys fall into unrelated groups:

- textual history and normalization: `OrigForm`, `SpaceAfter`, `Lang` (Section 7.1);
- editorial variation: `Variant` (Section 7.2);
- speaker and discourse: `Speaker`, `DiscourseMode` (Sections 7.5, 7.6);
- retained reasoning: `ReviewNote`, `ReviewTags` (Section 7.8);
- construction labels: `SyntaxNote` (Section 7.7);
- lexical and morphological compatibility: `LemmaNorm` (Section 2.1), `TraditionalMood` (Section 3.3.2);
- Enhanced provenance: `InheritedFrom` (Section 5.7);
- section changes inside a sentence: `NextLoc`.

`NextLoc=<loc>` marks the first token (the first syntactic word, where that token is a multiword token) of each section after the first in a sentence whose `edition_loc` lists more than one section. Its value equals the corresponding entry of `edition_loc` (`NextLoc=1.2.4`). Unlike UD's `Ref`, which is written on every token, `NextLoc` marks only the change.

**Corpus examples**

- *otium si essem consecutus* ‘if I had obtained leisure’ (S000001): *otium* (1) `OrigForm=Otium`, `Variant=Giusta:Prius+`, `DiscourseMode=Preface`. A single MISC field holds a record of the transmitted capitalization, an editor's variant reading and a discourse label side by side, with no linguistic relation between them.

#### 1.2.8 File-level consistency requirements

- A dependency reference is valid only within its own sentence's current numbering.
- An empty node is referred to by its decimal `ID` exactly as assigned.
- `sent_id` is unique across the file, alternative records included; an alternative record points to its source through `source_sentence` or `source_sentences`.

### 1.3 Key concepts

#### 1.3.1 Dependencies, headedness, and flat structures

Annotating a construction means first choosing its head, then labelling the relations of its dependents. The head is not necessarily the first word, the finite verb, the morphologically richest word, or the word an English translation renders as a verb.

Use ordinary headed relations wherever a head can be identified. A flat relation ([`flat`](https://universaldependencies.org/u/dep/flat.html), `flat:name`, `flat:foreign`, `flat:gov`) is for a construction with no adequate internal head, or one that a UD convention treats as headless; its first word is the technical head by convention, which says nothing about prominence. Unity of meaning, a naming function, or idiomaticity is not by itself evidence for a flat analysis.

> [!NOTE]
> **ALDT comparison.** UD's flat relations have no direct counterpart in Prague-style treatments of coordination, apposition, or multiword expressions. Comparisons with PDT-style annotation explain the differences; they are not conversion rules.

**Corpus examples**

- *quos Cassius Dionysius Uticensis vertit* ‘which Cassius Dionysius of Utica translated’ (S000030): *Cassius* (17) `nsubj`; *Dionysius* (18) `flat:name`; *Uticensis* (19) `amod`. The first name component is the technical head of the flat:name span and carries its external relation; the modifying adjective attaches to that head by an ordinary relation.

#### 1.3.2 Predication in dependency grammar

The predicate is the syntactic centre of a clause, and it need not be a finite verb.

> [!WARNING]
> **Traditional grammar.** Traditional *predicate* and *predicative* do not map onto dependency relations. A traditional "predicative" may be a primary nonverbal predicate, a selected predicative complement, a secondary predicate, an apposition, or an attribute; the annotation identifies which structure is present.

Choosing the predicate is choosing the clause head, and it is decided by meaning, not by form or position. The predicate is the element that supplies what is asserted, ascribed, or asked about an argument already established in the clause: it brings the new information, and the element it is predicated of is the subject. An event, membership of a class, a property, a location, or a degree on a scale (quantity, measure) can each be predicated, by a declinable or an indeclinable word alike.

> **Background.** This typology follows Stassen (1997), on which the UD guidelines for [nonverbal predication and copulas](https://universaldependencies.org/v2/copula.html) build: event, class, property, and location predicates, each realized by whatever formal means a language has. Quantity and measure expressions predicate a degree on a scale in the same way.

The clause head may therefore be a lexical verb, an adjective, a noun, a numeral or other quantity expression, an adverb or prepositional phrase, or, under ellipsis, a promoted surviving element.

Three errors give a wrong clause head:

- taking a copula or auxiliary as head because it is the clause's only finite verb (Section 1.3.3);
- promoting a stranded dependent under ellipsis without first checking whether the predicate is recoverable (Sections 1.3.6 and 4.1.2);
- taking the first or most obvious word when the predicate stands elsewhere.

Run the test on every clause, subordinate clauses and indirect questions included, before attaching the clause. If the predicate is not obvious, look further; never fall back on a default head. Where the decision is hard, annotate the best-supported candidate and give the reasoning in a review note (Section 7.8).

A form of *sum* is ordinarily a copula or an auxiliary; neither the presence of *sum* nor a traditional "existential" label decides its analysis, only what is predicated in the clause (Section 1.3.3).

**Corpus examples**

- *utilissimus autem is ager* ‘that land, moreover, is most useful’ (S000145): *utilissimus* (1) `root`, `ADJ`; *ager* (4) `nsubj`. A property predicate heads its clause, here with no copula expressed.
- *ubi salubritas non est* ‘where healthiness is not [present]’ (S000148): *ubi* (2) `advcl`, `ADV`; *salubritas* (3) `nsubj`; *est* (5) `cop`. A location predicate: the indeclinable adverb heads its clause, and the copula depends on it.
- *quarto Robigum ac Floram* ‘fourth, [I invoke] Robigus and Flora’ (S000016): *Robigum* (2) `root`, `DEPS` 2.1:obj; *quarto* (1) `orphan`. The verb is elided; the surviving object is promoted to Basic root, while the Enhanced layer keeps it as the object of the empty node standing for the verb.

#### 1.3.3 Nonverbal predication and the copula

In a nonverbal predication the predicate heads the clause, and the copula *sum* is `AUX` attached to it as [`cop`](https://universaldependencies.org/u/dep/cop.html).

![Dependency tree of si est homo bulla (S000001): bulla heads the clause, with si as mark, est as cop, and homo as nsubj](figures/copula_S000001.svg)

*Figure 1.* *si est homo bulla* ‘if man is a bubble’ (S000001). The dashed arrow above *bulla* is the relation of the whole clause to the rest of the sentence, whose head is not shown.

*bulla* is the predicate and carries the clause's relation to the sentence (`advcl`); *homo* is its `nsubj`; *est* is `cop` and *si* `mark`, both attached to the predicate.

```text
Nonverbal predication           predicate is head; sum is AUX, cop
Periphrastic verbal form        verbal form is head; sum is AUX, aux or aux:pass
```

The choice depends on the function of *sum* in the clause, not on its lemma.

**Finding the predicate.** Every clause with a form of *sum* has a predicating element; the task is to find it (Section 1.3.2). The examples in these guidelines (an adjective, a noun, a numeral, a locative adverb, an interrogative) are not a checklist.

**Question words.** The semantic test decides whether an interrogative is the predicate, and the predicate is usually the element with more content:

- *Quis ille est?* ‘Who is he?’ (constructed): *quis* is the predicate (`root`), *ille* its `nsubj`.
- *Quis dux est?* ‘Who is the leader?’ (constructed): *dux* is the predicate, *quis* its `nsubj`; if the leader has already been identified and the question asks who that person is, *quis* is the predicate.

An interrogative or relative word paired with a separate content word leaves the predicate to that word; one that stands alone can itself be the predicate (see the examples below).

**Existential *sum*.** Take *sum* as a lexical verb (‘exist’) only after the predicate search has failed, and give the reasoning in a review note. It is then `VERB`, heads its clause, and takes `nsubj` (or `csubj` for a relative clause). Test *sunt qui* X first for the copular reading *sunt [ei] qui* X, with the relative clause as predicate, the understood *ei* as `nsubj:outer`, and *sunt* as `cop:outer` (Section 4.10.2); only if that fails is it ‘[those who] X exist’, with the relative clause as `csubj` and *sunt* as `VERB`.

> **Background.** A lexical *sum* is very rare in Classical Latin. Cicero's *omnium qui sunt, qui fuerunt, qui futuri sunt* (*Fam.* 11.21.1) is a clear instance, and the perfect forms *fuit*, *fuerunt* also occur euphemistically for ‘is dead’. In UD_Latin-CIRCSE none of the 427 tokens of *sum* is tagged `VERB`. Most clauses traditionally called existential are nominal predications with a copula, sometimes with a clause as the predicate.

> [!NOTE]
> **ALDT comparison.** ALDT makes the copula the head of *si est homo bulla*, with the subject (`Sb`) and the nominal predicate (`Pnom`) attached to it. This treebank inverts that headedness: *bulla* heads the clause, *homo* is its `nsubj`, and *est* depends on it as `cop`. The two schemes agree on the roles and differ on which word is structurally in charge, which changes what every other relation in the clause attaches to.

**Corpus examples**

- *bulla* is the predicate and the head of its clause, and it carries the clause's own relation to the sentence (`advcl`, since the clause is conditional);
- *homo* is its subject;
- *est* supports the predication as `cop`, and the subordinator *si* attaches to the predicate as `mark`;
- *Quis ille est?* ‘Who is he?’: *quis* is the predicate (`root`) and *ille* its `nsubj`, since the question carries more content than a bare demonstrative.
- *Quis dux est?* ‘Who is the leader?’: *dux* is the predicate (`root`) and *quis* its `nsubj`, since being the leader is the content and *quis* only selects the person.
- *si est homo bulla* ‘if man is a bubble’ (S000001): *est* (30) `cop`, `AUX`; *homo* (31) `nsubj`. The sentence of Figure 1: the noun bulla heads its clause, and both est and homo depend on it.
- *agri culturae quod esset initium et finis* ‘what the beginning and end of agriculture was’ (S000155): *initium* (7) `ccomp`; *quod* (5) `nsubj`; *esset* (6) `cop`. In the indirect question, the noun initium is the content of the answer and heads the clause; the interrogative quod only selects.
- *quae sit forma* ‘what its shape is’ (S000170): *forma* (12) `appos`; *quae* (10) `nsubj`; *sit* (11) `cop`. quae only asks which shape; forma carries the content, so forma is the predicate and quae its subject.
- *solum partesque eius quales sint* ‘of what sort its soil and its parts are’ (S000161): *quales* (11) `acl`; *solum* (7) `nsubj`; *sint* (12) `cop`. An interrogative standing alone can itself be the predicate: quales supplies the property asked about, and solum is its subject.

#### 1.3.4 Secondary predication

A secondary predicate adds a predication to a clause without replacing its primary predicate, typically a state, role, or circumstance holding of a participant during the main event.

**Optional secondary predicate.** An adjunct, `advcl:pred`: the clause is complete without it. Attach it to the predicate of its clause, never to the nominal it describes, whether that nominal is overt or not.

**Selected predicative complement.** Where the predicate selects the predication and its subject is controlled by a matrix argument, use `xcomp`. The test is valency: if the clause is grammatical without the element, it is an adjunct. Figures 2 and 3 compare the two.

![Dependency tree of comites … incolumes reduxit (S000154): reduxit heads the clause, with comites as obj and incolumes as advcl:pred](figures/advcl_pred_S000154.svg)

*Figure 2.* *comites … incolumes reduxit* ‘brought his companions … back safe’ (S000154). *incolumes* is an optional secondary predicate: *reduxit comites* is complete without it. It attaches to the verb as `advcl:pred`, not to *comites*.

![Dependency tree of quem … fructuosum … facere velis (S000003): facere is xcomp of velis, with quem as obj and fructuosum as xcomp of facere](figures/xcomp_S000003.svg)

*Figure 3.* *quem … fructuosum … facere velis* ‘which you wish to make productive’ (S000003). *fructuosum* is selected by *facere*: ‘to make it’ needs the result it is made into, so the adjective is `xcomp`, and its understood subject is the object *quem*.

**Absolute predication.** An ablative absolute has its own subject and is `advcl:abs` (Section 6.1).

**Attribute.** An adjective, participle, or noun that characterizes or identifies a nominal is `amod`, `acl`, or `appos`. Agreement does not distinguish an attribute from a secondary predicate; Section 4.15.3 sets out the test by part of speech.

**Open point.** Whether secondary predication extends to nominal predication with copula-like verbs (*fio*, *evado*, with a predicative `xcomp`) has not been examined as a class. Until it is, such cases follow the distinctions above.

**Corpus examples**

- *suos comites ac familiam incolumes reduxit* ‘brought his companions and household back safe’ (S000154): *incolumes* (40) `advcl:pred`, `DEPS` 41:advcl; *comites* (37) `DEPS` 40:nsubj. An optional secondary predicate with an overt co-referent: the clause is complete without incolumes.
- *quem bene colendo fructuosum cum facere velis* ‘which you wish to make productive by cultivating it well’ (S000003): *fructuosum* (10) `xcomp`; *quem* (7) `obj`. A selected predicative complement: facere requires the predication fructuosum, which holds of its object quem.
- *iis igitur deis ad venerationem advocatis ego referam* ‘therefore, with those gods summoned for veneration, I shall recount’ (S000021): *advocatis* (6) `advcl:abs`; *deis* (3) `nsubj:pass`. An ablative absolute brings its own subject, independent of the main clause's arguments.

#### 1.3.5 Arguments, complements, and adjuncts

Arguments are selected by the predicate; adjuncts add optional circumstances. The distinction underlies the choice between `obj` and `obl`, `obl:arg` and `obl`, `ccomp` or `xcomp` and `advcl`, and `xcomp` and `advcl:pred` (Section 4.15). Case and plausibility do not decide it: the governor's valency does.

**Corpus examples**

- *commodius tibi haec scriberem* ‘I would write these things to you more suitably’ (S000001): *haec* (10) `obj`; *tibi* (9) `obl:arg`; *commodius* (8) `advmod`. Two selected participants of scribo beside an optional manner adjunct.
- *Graeca lingua Sextilio praetori misit* ‘sent [them] in Greek to the praetor Sextilius’ (S000030): *Sextilio* (26) `obl:arg`; *lingua* (25) `obl`. The dative recipient is selected by mitto; the ablative of manner is an adjunct.

#### 1.3.6 Overt, omitted, and reconstructed structure

Unexpressed material is annotated in one of these ways:

- a null subject or an omitted copula: nothing is added;
- an ellipsis after which every surviving word keeps its governor: `SyntaxNote=Ellipsis` (Section 5.4);
- an ellipsis that strands dependents: promotion with `orphan` in the Basic tree (Section 4.1.2) and an empty node in the Enhanced layer (Section 5.3);
- a physical gap in the transmitted text: `orphan:missing` (Section 4.1.3).

A word promoted under ellipsis may become the Basic root without being the semantic predicate; the promotion is a repair required by the tree format.

**Corpus examples**

- *si est homo bulla, eo magis senex* ‘if man is a bubble, an old man is all the more so’ (S000001): *senex* (36) `advcl:cmp`, `DEPS` 36.1:nsubj; *eo* (34) `orphan`; *bulla* (36.1) `DEPS` 32:advcl:cmp. Head ellipsis: senex is promoted and eo takes orphan in the Basic tree, while an empty node reconstructs the elided predicate in the Enhanced layer.
- *quod ibi fructus certus* ‘because there the yield is reliable’ (S000145): *certus* (14) `advcl`; *fructus* (13) `nsubj`. An omitted copula needs no reconstruction: the adjectival predicate heads the clause and every dependent keeps an ordinary governor.

#### 1.3.7 Annotation criteria and illustrative examples

The stated criteria define a category; examples illustrate it. A construction missing from the examples is not thereby excluded, several examples do not form a closed list, and corpus frequency or a precedent does not settle an uncertain case.

Examples are chosen in this order of preference:

1. a corpus example, trimmed to the relevant words;
2. a real Latin example from another author, cited;
3. a corpus example adapted to show the other side of a contrast, labelled “adapted from” its sentence;
4. a minimal constructed example, labelled “constructed”.

### 1.4 Sources of authority

In order of precedence:

1. general Universal Dependencies (the framework and the CoNLL-U format);
2. Latin Universal Dependencies (Latin-specific features, relations, and conventions);
3. harmonized Latin annotation, as set out in Gamba and Zeman (2023a, 2023b);
4. treebank-specific decisions, only where the levels above leave a point open.

A treebank-specific deviation is stated, narrowly scoped, and justified. Parser output, corpus frequency, and precedent are evidence, not authority.

### 1.5 How to use these guidelines

Chapter 1 gives the format and the concepts the later chapters assume. Chapters 2 and 3 cover lemmas, parts of speech, and features; Chapter 4 the Basic relations one by one, with decision guides in Section 4.15; Chapter 5 the Enhanced layer; Chapter 6 the named Latin constructions; Chapter 7 the textual, discourse, and review metadata.

The figures are drawn from the corpus rows. Each box shows the form, the lemma in italics, and the part of speech; arrows point from head to dependent, blue where the dependent follows its head and purple where it precedes it, and the highlighted box is the word the figure is about. A figure shows only the words it names: an ellipsis in the bottom row marks words left out, and a dashed grey arrow marks a relation to a head outside the figure. A few figures use the Flat view: the words in one row, Basic relations above them and Enhanced edges below.

Three kinds of box are set off from the instructions: a plain quoted block gives background; a blue *Note* box compares the analysis with ALDT/PDT-style Latin treebanking; a yellow *Warning* box flags a point where traditional grammar does not map directly onto the annotation.

---

## 2. Lemmas and Parts of Speech

### 2.1 General lemma and UPOS principles

Fix the lemma and the [UPOS](https://universaldependencies.org/u/pos/) category before the features, which depend on them. Morphology follows harmonized Latin UD, with [`InflClass`](https://universaldependencies.org/la/feat/InflClass.html) wherever the class is determinable (Section 3.3.1). `XPOS` is not used.

Where `LEMMA` is a by-form with an enclitic or suffix that the dictionary does not list separately, `LemmaNorm` in `MISC` gives the dictionary headword, so that a search by dictionary lemma finds the token: *hosce* and *huiusce* have `LEMMA` *hice* and `LemmaNorm=hic`.

**Corpus examples**

- *hosce ipsos … redegit Diophanes* ‘Diophanes reduced these very [works]’ (S000032): *hosce* (1) `LemmaNorm=hic`. LEMMA records the by-form hice; LemmaNorm gives the dictionary headword.

### 2.2 The UPOS inventory

**Nominal categories.**

- [`NOUN`](https://universaldependencies.org/u/pos/NOUN.html): common noun. An indeclinable noun has no `InflClass`.
- [`PROPN`](https://universaldependencies.org/u/pos/PROPN.html): proper noun; a Greek-declined name takes `Variant=Greek`.
- [`PRON`](https://universaldependencies.org/u/pos/PRON.html) and [`DET`](https://universaldependencies.org/u/pos/DET.html): Section 2.3.
- [`ADJ`](https://universaldependencies.org/u/pos/ADJ.html): adjective, including comparative, superlative, and diminutive forms, ordinals, distributives (`NumType=Dist`), and lexicalized participles (Section 2.4).
- [`NUM`](https://universaldependencies.org/u/pos/NUM.html): cardinal numeral, written as a word, or as a Roman numeral, digits, or a reference (`NumForm`), in which case it has no `Case`, `Gender`, or `Number`.

**Verbal categories.** [`VERB`](https://universaldependencies.org/u/pos/VERB.html) is the lexical verb in all its forms; the gerund, gerundive, and supines are treated in Section 3.1.2. [`AUX`](https://universaldependencies.org/u/pos/AUX.html) is *sum* as copula or auxiliary (Section 2.5).

**Adverbs and adpositions.** [`ADV`](https://universaldependencies.org/u/pos/ADV.html) is unfeatured unless it has `Degree`, a lexical `AdvType`, or a pronominal `PronType` or `NumType`. The connective *vero* is `ADV`; *itaque*, like *enim*, *igitur*, and *nam*, is `PART`. [`ADP`](https://universaldependencies.org/u/pos/ADP.html) is the preposition, without `AdpType`; only enclitic *cum* (*nobiscum*, Section 1.2.3) takes `AdpType=Post`.

**Function words.** [`CCONJ`](https://universaldependencies.org/u/pos/CCONJ.html) and [`SCONJ`](https://universaldependencies.org/u/pos/SCONJ.html) take `Polarity=Neg` when negative; a pronominal subordinator such as *quo* takes `PronType=Rel` on `SCONJ`. [`PART`](https://universaldependencies.org/u/pos/PART.html) is unfeatured, or takes `Polarity=Neg`, `Form=Emp`, or `PartType=Int`. [`INTJ`](https://universaldependencies.org/u/pos/INTJ.html) is unfeatured.

**Other.** [`PUNCT`](https://universaldependencies.org/u/pos/PUNCT.html) has no features. [`X`](https://universaldependencies.org/u/pos/X.html) is for unanalysed material (Section 2.6).

**Corpus examples**

- *comprendit libris XXIIX* ‘gathered [it] into twenty-eight books’ (S000030): *XXIIX* (14) `NUM`, `NumForm=Roman`, `nummod`. A numeral given as a Roman numeral carries no Case, Gender or Number.
- *Hieron Siculus et Attalus Philometor* ‘Hieron the Sicilian and Attalus Philometor’ (S000024): *Hieron* (16) `PROPN`, `Variant=Greek`. A proper noun whose nominative in -on follows the Greek rather than the Latin paradigm.
- *quo graviora quae sunt ea diligentia leviora facere possimus* ‘whereby, by that diligence, we can make lighter the things that are heavier’ (S000150): *quo* (29) `SCONJ`, `PronType=Rel`, `mark`. A pronominal subordinator takes the PronType value of its lemma.

### 2.3 The `DET` / `PRON` boundary

`DET` is a closed lexical list (demonstratives and identity words, indefinites and quantifiers, possessives, pronominal quantifiers with `NumType=Card`), not the relation `det`. A lemma on the list is `DET` wherever it occurs, also when it stands alone: *hic*, *ille*, *iste*, *idem*, *ipse*, *quidam*, *quisque*, *nullus*, *totus*, *multus*. *aliquis* is not on the list and is `PRON`. `PRON` is for pronouns outside the list: personal, relative, and interrogative. A homonym of another category takes that category (*hic* ‘here’ is `ADV`).

**Exceptions decided by use.**

- *is* is `DET` with `PronType=Dem` and no `Person` in demonstrative use: adnominal (*is ager*); antecedent of a clause it points forward to (*is qui*, *id quod*); the correlative ablative (*eo magis … quod*); *et id* ‘and that too’; set against another referent. It is `PRON` with `PronType=Prs` and `Person=3` when it refers back to an entity or proposition already in the discourse (*eius*, *ab ea*). When both readings fit, use `PRON`.
- Indefinite *quis* after *si*, *nisi*, *ne*, *num*, *quo*, *quanto*, *ubi*, or *cum* is `PRON` with lemma *quis* and `PronType=Ind`, also when it modifies a noun (relation `det`). Where the edition writes the two as one word (*siquis*, *nequid*), split it as a multiword token, *si* or *ne* (`SCONJ`, `mark`) + *quis*; lexicalized compounds (*siquidem*, *nequaquam*) are not split.

**Corpus examples**

- *hos nobilitate Mago Carthaginiensis praeteriit* ‘Mago the Carthaginian surpassed these men in fame’ (S000030): *hos* (1) `DET`, `obj`. A closed-list demonstrative used substantivally, as the object, is still DET.
- *ego hic … vivere non possum* ‘here I cannot live’ (S000051): *hic* (2) `ADV`, `advmod:lmod`. The adverb hic ‘here’ is a separate homonym of the determiner and is tagged by its own category.
- *utilissimus autem is ager* ‘that land, moreover, is most useful’ (S000145): *is* (3) `DET`, `PronType=Dem`, `det`. The adnominal use is demonstrative: DET.
- *itaque dum id nobiscum una videatis* ‘so, while you look into this together with us’ (S000082): *id* (3) `PRON`, `PronType=Prs`, `Person=3`, `obj`. id refers back to what has just been said: the anaphoric pronoun.
- *siqua in re quaeres* ‘if you seek [something] in any matter’ (S000008): *si* (12) `SCONJ`, `mark`; *qua* (13) `PRON`, `PronType=Ind`, `det`. The edition's siqua is split as a multiword token; the indefinite stays PRON although it modifies re.

### 2.4 Lexicalized participles and the `ADJ` / `VERB` boundary

A participle is `ADJ` once it has lexicalized as an adjective, describing independently of the verb's valency; otherwise it stays `VERB`, whatever the English gloss suggests. A lexicalized participle takes `VerbForm=Part` only where harmonized practice treats the lexeme as deverbal, and `Degree` only where the adjective has its own comparative or superlative.

**Corpus examples**

- *res aliae diversae ab agro* ‘other things, different from farming’ (S000110): *diversae* (6) `ADJ`, `VerbForm=Part`, `amod`. A lexicalized participle of diverto, used descriptively; VerbForm=Part records its deverbal status.
- *qui res dispersas comprendit* ‘who gathered the scattered material together’ (S000030): *dispersas* (11) `VERB`, `acl`. An ordinary perfect passive participle remains VERB even where English renders it as an adjective.

### 2.5 Copular and auxiliary uses of *sum*

*sum* as copula or auxiliary is `AUX`, never `VERB` (Sections 1.3.2, 1.3.3). It has no `Voice`. Lexical *sum* (Section 1.3.3) is `VERB`.

**Corpus examples**

- *qui salubrior est quam alii* ‘which is healthier than others’ (S000145): *est* (7) `AUX`, `cop`; *salubrior* (6) `acl:relcl`. Copular sum: the adjective heads the relative clause.
- *omnes domus repletae essent aegrotis* ‘all the houses had been filled with the sick’ (S000154): *essent* (16) `AUX`, `aux:pass`; *repletae* (15) `conj`. Passive auxiliary sum: the participle repletae heads its clause (here a conjunct), and essent depends on it.
- *otium si essem consecutus* ‘if I had obtained leisure’ (S000001): *essem* (3) `AUX`, `aux`. Tense auxiliary with a deponent participle.

### 2.6 Foreign, corrupt, and unanalysed material

Every word that is not Latin takes `Foreign=Yes` ([foreign expressions](https://universaldependencies.org/foreign.html)). A Greek word that is analysed takes its own category and features, `Lang=grc`, and no Latin lemma or inflectional class (Section 7.1). Only material left unanalysed is `X`, without Latin features. A gap in the transmitted text is a single token `…` with `DiscourseMode=Lacuna` (Section 7.6); a word governed by the gap takes `orphan:missing` (Section 4.1.3).

**Corpus examples**

- *qui inscribuntur φυτῶν ἱστορίας* ‘which are entitled History of Plants’ (S000156): *ἱστορίας* (18) `NOUN`, `Lang=grc`; *φυτῶν* (17) `nmod`. A Greek title given a real grammatical analysis: ordinary UPOS and relations, Lang=grc, and no Latin InflClass.

## 3. Morphological Features

Features fall into three tiers:

- **core features** (Section 3.1): case, gender, number, the verbal features, person, and degree. They must agree with the syntactic analysis: a subject's case, a finite verb's person and number, a participle's agreement with its noun;
- **classificatory features** (Section 3.2): lexical classifications, some of them relevant to the syntax (`PronType` on relative and interrogative words, `Poss`, `Polarity`), others mainly to interpretation (`NameType`);
- **compatibility features** (Section 3.3): `InflClass` and the traditional mood and tense labels, kept for Latin UD.

### 3.1 Core features

#### 3.1.1 Case, gender, and number

[`Case`](https://universaldependencies.org/u/feat/Case.html): `Nom`, `Acc`, `Gen`, `Dat`, `Abl`, `Voc`, `Loc`. Use `Voc` only for direct address, not for a nominative in apposition to it. Use `Loc` only for the surviving locatives (town names, *domi*, *ruri*, *humi*); an ordinary place expression is a preposition with the ablative or accusative.

[`Gender`](https://universaldependencies.org/u/feat/Gender.html): `Masc`, `Fem`, `Neut`, as the grammatical gender of the word. `Com` is not used.

[`Number`](https://universaldependencies.org/u/feat/Number.html): `Sing`, `Plur`.

**Corpus examples**

- *in fundo suo Faventiae* ‘on his estate at Faventia’ (S000066): *Faventiae* (19) `Case=Loc`; *fundo* (17) `Case=Abl`. The locative survives on a town name; the ordinary place expression takes a preposition with the ablative.
- *Fundania, commodius tibi haec scriberem* ‘Fundania, I would write these things to you more suitably’ (S000001): *Fundania* (6) `Case=Voc`, `vocative`; *tibi* (9) `Case=Dat`.

#### 3.1.2 Verb form, mood, tense, aspect, and voice

[`VerbForm`](https://universaldependencies.org/u/feat/VerbForm.html): `Fin` (every form with a `Mood`), `Inf`, `Part`, and, following harmonized Latin UD, `Conv` for the active supine and `Vnoun` for the ablative supine (tagged `NOUN`; Section 6.9). The gerund and the gerundive are `VerbForm=Part` with `Aspect=Prosp` and `Voice=Pass`: the gerund carries `Case` only, the gerundive `Case`, `Gender`, and `Number`. UD's `Ger`, `Gdv`, and `Sup` are not used; the traditional names are recorded in `TraditionalMood` (Section 3.3.2).

[`Mood`](https://universaldependencies.org/u/feat/Mood.html), on finite forms only: `Ind`, `Sub`, `Imp`.

[`Tense`](https://universaldependencies.org/u/feat/Tense.html), on finite forms: `Pres`, `Past`, `Fut`, `Pqp`. [`Aspect`](https://universaldependencies.org/u/feat/Aspect.html): `Imp`, `Perf`, `Prosp`. Tense and aspect are factored separately: the imperfect is `Aspect=Imp|Tense=Past`, the perfect `Aspect=Perf|Tense=Past` (never a tense value of its own). `Prosp` marks the future participle, the gerund, and the gerundive. `Aspect=Inch` is not used: *-sco* verbs are `Aspect=Imp`.

[`Voice`](https://universaldependencies.org/u/feat/Voice.html): `Act`, `Pass`. Deponents take the voice of their form (`Pass`). No form of *sum* carries `Voice`.

**Corpus examples**

- *hanc multitudinem dicebat suas reddere vites* ‘he used to say that his vines yielded this quantity’ (S000066): *dicebat* (22) `Aspect=Imp`, `Tense=Past`; *reddere* (24) `VerbForm=Inf`. The imperfect indicative is imperfective aspect combined with past tense.
- *cum huius spectatum veniant villas* ‘when they come to view his villas’ (S000076): *spectatum* (19) `VerbForm=Conv`, `Aspect=Prosp`. The active supine.
- *res aliae … erunt adsumendae* ‘other things will have to be taken on’ (S000110): *adsumendae* (10) `VerbForm=Part`, `Aspect=Prosp`, `Voice=Pass`, `Gender=Fem`. The gerundive: a prospective passive participle agreeing in case, gender and number with its subject res.

#### 3.1.3 Person

[`Person`](https://universaldependencies.org/u/feat/Person.html): `1`, `2`, `3`, on finite verbs and personal pronouns. The possessor features `Person[psor]` and `Number[psor]` are treated with the possessives (Section 3.2.1).

**Corpus examples**

- *otium si essem consecutus* ‘if I had obtained leisure’ (S000001): *essem* (3) `Person=1`, `Number=Sing`.

#### 3.1.4 Degree

[`Degree`](https://universaldependencies.org/u/feat/Degree.html): `Cmp` for the comparative, `Abs` for the superlative, `Dim` for true diminutive forms (*homunculus*, *dormito*). The positive degree carries no `Degree` (Section 2.1). `Sup` and `Equ` are not used.

**Corpus examples**

- *utilissimus autem is ager qui salubrior est quam alii* ‘that land, moreover, is most useful which is healthier than others’ (S000145): *utilissimus* (1) `Degree=Abs`; *salubrior* (6) `Degree=Cmp`.
- *commodius tibi haec scriberem* ‘I would write these things to you more suitably’ (S000001): *commodius* (8) `Degree=Cmp`, `ADV`.

### 3.2 Classificatory features

#### 3.2.1 Pronoun, numeral, and possessive features

[`PronType`](https://universaldependencies.org/la/feat/PronType.html): `Prs`, `Dem`, `Rel`, `Int`, `Ind`, `Neg`, `Tot`, `Con`, `Rcp`. `Emp` and `Art` are not used.

[`Poss`](https://universaldependencies.org/u/feat/Poss.html) and [`Reflex`](https://universaldependencies.org/u/feat/Reflex.html) take only `Yes` and are omitted otherwise. `Reflex` is lexical: it marks a reflexive form whatever its use in the clause; a reciprocal use is recorded by `PronType`.

[`NumType`](https://universaldependencies.org/u/feat/NumType.html): `Card`, `Ord`, `Dist`, `Mult`. Distributives are `ADJ` with `NumType=Dist` and no `PronType`; on `DET`, `NumType` is only `Card`. [`NumForm`](https://universaldependencies.org/la/feat/NumForm.html) records how a numeral is written (word, Roman numeral, digits, reference); the non-word forms generally take no `Case`, `Gender`, or `Number`. [`NumValue`](https://universaldependencies.org/la/feat/NumValue.html) is used only on *unus* (`1`) and *ambo* (`2`, with `PronType=Tot`).

`Person[psor]` and `Number[psor]` give the person and number of the possessor on a possessive, independently of the word's own agreement features; both go with `Poss=Yes`.

**Corpus examples**

- *iugerum unum denos et quinos denos culleos fert* ‘one iugerum bears ten and fifteen cullei each’ (S000061): *unum* (5) `NumValue=1`, `NumType=Card`; *denos* (6) `ADJ`, `NumType=Dist`. A distributive is an adjective, without PronType.
- *in fundo suo* ‘on his own estate’ (S000066): *suo* (18) `Reflex=Yes`, `Poss=Yes`, `PronType=Prs`.
- *omnes domus repletae essent* ‘all the houses had been filled’ (S000154): *omnes* (13) `PronType=Tot`.
- *non hic Varro noster* ‘[did] not this Varro of ours’ (S000154): *noster* (4) `Poss=Yes`, `Person[psor]=1`, `Number[psor]=Plur`, `Number=Sing`. The possessor features (first person plural) are independent of the determiner's own agreement number.
- *socerum meum* ‘my father-in-law’ (S000037): *meum* (8) `Person[psor]=1`, `Number[psor]=Sing`.

#### 3.2.2 Polarity, abbreviation, and other lexical features

[`Variant`](https://universaldependencies.org/la/feat/Variant.html): `Greek` for Greek inflection on a Latin word (not a Greek loan inflected regularly), `Archaic` for a form treated as an archaic variant (not an ordinary old spelling).

Other lexical features, where they apply:

- [`Abbr=Yes`](https://universaldependencies.org/u/feat/Abbr.html): an abbreviation;
- [`AdvType`](https://universaldependencies.org/la/feat/AdvType.html) (`Loc`, `Tim`): a lexically spatial or temporal adverb or subordinator, assigned by the lexeme, not by context;
- [`Compound=Yes`](https://universaldependencies.org/la/feat/Compound.html): a univerbation whose parts are still discernible (*scilicet*);
- [`Form=Emp`](https://universaldependencies.org/la/feat/Form.html): an emphatic form of a function word (*egomet*, *sese*);
- [`Polarity=Neg`](https://universaldependencies.org/u/feat/Polarity.html): grammatical negation;
- [`PartType`](https://universaldependencies.org/u/feat/PartType.html) (`Int`, `Emp`): a particle whose function `Form` or `Polarity` does not already record;
- [`Foreign=Yes`](https://universaldependencies.org/u/feat/Foreign.html): a word that is not Latin, analysed or not (Section 2.6).

**Corpus examples**

- *Hieron Siculus* ‘Hieron the Sicilian’ (S000024): *Hieron* (16) `Variant=Greek`; *Siculus* (17) `NameType=Nat`.
- *equidem innumerabiles mihi videntur* ‘for my part, they seem countless to me’ (S000156): *equidem* (1) `Form=Emp`, `PART`. An expanded, emphatic form of the particle quidem.

#### 3.2.3 `NameType`

[`NameType`](https://universaldependencies.org/u/feat/NameType.html): `Ast`, `Cal`, `Com`, `Geo`, `Giv`, `Let`, `Lit`, `Met`, `Nat`, `Rel`, `Sur`, `Oth`.

- `Giv`: a praenomen, or a single personal name (a Greek name); a legendary mortal.
- `Sur`: a *nomen gentilicium* or a *cognomen*.
- `Rel`: gods and mythological beings.
- `Nat`: an ethnic or place adjective that refers to people: part of a name (*Amphilochus Atheniensis*), an attribute of a person or group (*eques Romanus*, *Graeci scriptores*), or used as a noun (*Mediolanenses*).
- `Geo`: a place, and an ethnic or place adjective that does not refer to people (*ager Campanus*, *lingua Graeca*).

The `Gender` of a personal name follows the person, not the noun it derives from: *Scrofa* is `Masc`.

**Corpus examples**

- *C. Licinius* ‘Gaius Licinius’ (S000073): *C* (3) `Abbr=Yes`, `NameType=Giv`; *Licinius* (5) `NameType=Sur`, `flat:name`. The praenomen is Giv, the nomen Sur.
- *Agrium equitem R.* ‘Agrius, a Roman knight’ (S000037): *Agrium* (13) `NameType=Sur`; *R* (15) `Abbr=Yes`, `NameType=Nat`. Romanus refers to a person, so it is Nat.
- *Graeca lingua Sextilio praetori* ‘in Greek to the praetor Sextilius’ (S000030): *Graeca* (24) `NameType=Geo`; *Sextilio* (26) `NameType=Sur`. Graeca qualifies a language, not people, so it is Geo.

### 3.3 Compatibility features

> These features are kept for conformity with Latin UD practice and are not used by this treebank's own analysis.

#### 3.3.1 `InflClass` and `InflClass[nominal]`

[`InflClass`](https://universaldependencies.org/la/feat/InflClass.html) gives the inflectional class:

- nominal: `IndEurA` (1st declension), `IndEurO` (2nd), `IndEurX` (3rd, consonant stems), `IndEurI` (3rd, i-stems, including adjectives, determiners, numerals, and present participles of that class), `IndEurU` (4th), `IndEurE` (5th), `LatPron` (pronominal declension);
- verbal: `LatA` (1st conjugation), `LatE` (2nd), `LatX` (3rd), `LatI` (4th), `LatI2` (mixed, *capio*; also *inquam*, *aio*, and *coepio* in every form);
- `LatAnom`: anomalous verbs and the personal pronouns.

The class is that of the form, not of the lemma: first-class adjectives and determiners (possessives, ordinals, and distributives included), and the nominal layer of participles and gerundives, are `IndEurA` in the feminine and `IndEurO` in the masculine and neuter. An indeclinable word carries no `InflClass` (`InflClass=Ind` is not used).

[`InflClass[nominal]`](https://universaldependencies.org/la/feat/InflClass-nominal.html) gives the declension of a verbal form that also declines (participle, gerund, gerundive, supine), alongside its verbal `InflClass`.

**Corpus examples**

- *otium si essem consecutus* ‘if I had obtained leisure’ (S000001): *consecutus* (4) `InflClass=LatX`, `InflClass[nominal]=IndEurO`; *essem* (3) `InflClass=LatAnom`; *otium* (1) `InflClass=IndEurO`. The participle carries both its verbal conjugation and, at the nominal layer, the declension it inflects by.
- *qui res dispersas comprendit* ‘who gathered the scattered material together’ (S000030): *res* (10) `InflClass=IndEurE`; *dispersas* (11) `InflClass[nominal]=IndEurA`; *qui* (9) `InflClass=LatPron`.

#### 3.3.2 `TraditionalMood`

`TraditionalMood` is a `MISC` key, not a feature (Section 1.2.4). Its values `Gerundium`, `Gerundivum`, and `Supinum` distinguish the gerund, the gerundive, and the supine from an ordinary participle, since the UD `VerbForm` values for them are not used (Section 3.1.2).

`TraditionalTense` is not annotated.

**Corpus examples**

- *quem bene colendo fructuosum cum facere velis* ‘which you wish to make productive by cultivating it well’ (S000003): *colendo* (9) `TraditionalMood=Gerundium`, `VerbForm=Part`.
- *haec enim cognoscenda* ‘for these things must be learned’ (S000139): *cognoscenda* (3) `TraditionalMood=Gerundivum`, `VerbForm=Part`.
- *cum huius spectatum veniant villas* ‘when they come to view his villas’ (S000076): *spectatum* (19) `TraditionalMood=Supinum`, `VerbForm=Conv`.

## 4. Basic Syntax

Basic dependency syntax attaches every syntactic word to exactly one governor with a labelled relation (Section 1.2.5). This chapter is organized by base relation. Each relation has an entry in the same format:

- **Use:** when the relation applies.
- **Do not use for:** the neighbouring relations, with the test that separates them.
- **Head and dependent:** what the relation attaches, and to what.
- **Examples**, with a tree figure where the snippet does not show the structure.
- **Subtypes:** a table of the subtypes used under the relation. A subtype refines its base relation and is used only where its own condition is positively met; otherwise the plain relation applies.

A few subtypes change what the annotator has to decide, not only what the label says, and have entries of their own: the passive subtypes (Section 4.2), the `:outer` family (Section 4.10.2), `advcl:pred` and `advcl:abs` (Sections 4.7.3 and 4.7.4), the relative-clause subtypes (Section 4.8), `flat:name` (Section 4.11.3), the reported-speech family (Section 4.12.2), and `orphan:missing` (Section 4.1.3). Section 4.15 gathers the most frequent choices between relations as decision guides. The `dislocated` family is treated with its construction in Section 6.10.

### 4.1 Predicates and roots

Identify the predicate before attaching anything to it. The predicate of a clause is the element that supplies what is asserted, ascribed, or asked about an established argument (Section 1.3.2); it is never chosen by position or by finiteness. Once identified, it heads every relation UD assigns to a clause head: the clause's own external relation (`root`, or `advcl`, `ccomp`, `xcomp` and their subtypes where the clause is embedded), its subject, its subordinator (`mark`), its copula (`cop`), and its trailing punctuation.

#### 4.1.1 `root`

**Use** [`root`](https://universaldependencies.org/u/dep/root.html) for the single word that depends on the virtual root node `0`: the predicate of the main clause, or, under ellipsis, the element promoted in its place (Section 4.1.2). Every sentence has exactly one.

**Do not use for** any word that has a governor within the sentence.

**Head and dependent.** Head: the virtual root node. Dependent: the main predicate, of any part of speech, or a promoted element.

![Dependency tree of quattuor sunt partes summae (S000160): the numeral quattuor is the root, with sunt as cop and partes as nsubj](figures/quantity_S000160.svg)

*Figure 4.* *quattuor sunt partes summae* ‘the chief parts are four’ (S000160). A quantity predicate: what is asserted about the parts is their number, so the numeral is the root, and the copula and the counted noun depend on it.

**Examples**

- *agri culturae … quattuor sunt partes summae* ‘the chief parts of agriculture are four’ (S000160): *quattuor* (8) `root`; *sunt* (9) `cop`; *partes* (10) `nsubj`. The sentence of Figure 4: the numeral supplies what is asserted about the parts, so it, not the copula, is the root.

#### 4.1.2 `orphan`

**Use** [`orphan`](https://universaldependencies.org/u/dep/orphan.html) under head ellipsis, for a dependent whose ordinary relation to the promoted element would misrepresent that element's role. When the predicate of a clause is elided, promote one surviving element to its structural slot:

1. If a copula or auxiliary survives, promote it. Its dependents keep their ordinary relations; none of them takes `orphan`, since the surviving copula or auxiliary already counts as predicational material.
2. If no predicational material survives (pure gapping), promote one of the stranded dependents; the others attach to it with `orphan`.

A single clause with no coordinate partner can show the first pattern: the elided lexical predicate leaves its copula or auxiliary heading the clause, bearing the clause's external relation and still tagged `AUX`. In *quae … opus sint ac debeant esse* (S000162), for example, *opus* is understood again after *debeant esse*, and the surviving *esse* heads its clause as `xcomp` under *debeant*.

**Do not use for** an omission that leaves every surviving word with a governor whose ordinary relation still holds: that omission is marked with `SyntaxNote=Ellipsis` instead (Section 5.4). Exactly one of the two treatments applies (Section 4.15.9). Do not use `orphan` for a coordinating conjunction, or for any dependent whose ordinary relation to the promoted element still holds.

**Head and dependent.** Head: the promoted element. Dependent: whatever the elided predicate would have governed. `orphan` is a Basic relation only; the Enhanced layer attaches the orphaned words to an empty node standing for the elided predicate (Section 5.3).

**Examples**

- *quod triticum Apulo?* ‘what wheat [shall I compare] with the Apulian?’ (S000055): *triticum* (2) `root`; *Apulo* (3) `orphan`; *conferam* (2.1) `DEPS` 0:root. No predicational material survives, so the stranded object is promoted to root and the other remnant takes orphan; the elided conferam is restored from the preceding sentence as an empty node.
- *ad te enim rudem esse agri culturae nunc, olim ad Stolonem fuisse dicunt* ‘for they say the wooden sword of agriculture is with you now, [and] once was with Stolo’ (S000083): *fuisse* (13) `conj`, `AUX`; *Stolonem* (12) `obl`; *olim* (10) `advmod:tmod`. The predicate rudem is elided in the second conjunct; the surviving copula fuisse is promoted, and its dependents keep their ordinary relations rather than orphan.

#### 4.1.3 `orphan:missing`

**Use** [`orphan:missing`](https://universaldependencies.org/la/dep/orphan-missing.html) where the governing element is missing not through the author's ellipsis but through a physical gap in the transmitted text (manuscript damage, a lacuna). Do not reconstruct the missing content silently: the relation marks the gap and its probable connections, leaving the uncertainty visible in the annotation.

**Do not use for** material the author left out (Section 4.1.2).

In the text, the gap is the single token `…` with `DiscourseMode=Lacuna` (Section 7.6).

### 4.2 Voice and the passive

Voice is a property of the predicate, and it affects every clause type. Annotate it once, on the predicate, and let three relations follow from it:

- the subject of a passive predicate is `nsubj:pass` (nominal) or `csubj:pass` (clausal);
- a passive auxiliary is `aux:pass`;
- an expressed agent is `obl:agent`.

The subtypes are licensed by the voice of the governing predicate alone, never by the subject's own form or position.

#### 4.2.1 Passive subjects: `nsubj:pass` and `csubj:pass`

**Use** [`nsubj:pass`](https://universaldependencies.org/u/dep/nsubj-pass.html) for the nominal subject of a passive predicate, and [`csubj:pass`](https://universaldependencies.org/u/dep/csubj-pass.html) for a clausal one. Test the voice of the governing predicate: a clausal subject of a passive verb takes `csubj:pass` whatever the voice of the verb inside the clause, and the clause's own subject takes `nsubj:pass` only if that inner verb is itself passive.

**Do not use for** the subject of an active or deponent predicate (`nsubj`, `csubj`), or of a copular clause (the copula has no voice).

**Head and dependent.** Head: the passive predicate. Dependent: as for `nsubj` and `csubj` (Section 4.3).

**Examples**

- *scribit cimices quem ad modum interfici oporteat* ‘he writes how bugs ought to be killed’ (S000119): *cimices* (2) `nsubj:pass`; *interfici* (6) `csubj`; *oporteat* (7) `ccomp`. The infinitive clause is the subject of impersonal oporteat, and its own subject is nsubj:pass because interfici is passive.
- *sic factum ut … hirci immolarentur* ‘thus it came about that goats were sacrificed’ (S000102): *immolarentur* (11) `csubj:pass`; *hirci* (10) `nsubj:pass`; *factum* (2) `root`. The ut-clause is the subject of passive factum; inside it, hirci is the subject of passive immolarentur.

#### 4.2.2 Passive auxiliary: `aux:pass`

**Use** [`aux:pass`](https://universaldependencies.org/u/dep/aux-pass.html) for a form of *sum* that marks passive voice on a participle: the perfect passive (*repletae essent*) and the passive periphrastic, *sum* with a gerundive of obligation (Section 6.4), as in the harmonized Latin treebanks. The participle or gerundive is the head.

**Do not use for** a copula with a participle that describes a resulting state rather than a passive event (`cop`; Section 4.15.6), or a tense auxiliary with an active or deponent participle (`aux`; Section 4.10.3). Whether a participle has lexicalized into an adjective is settled at the part-of-speech layer (Section 2.4), not here.

**Examples**

- *omnes domus repletae essent aegrotis* ‘all the houses had been filled with the sick’ (S000154): *essent* (16) `aux:pass`; *repletae* (15) `conj`; *domus* (14) `nsubj:pass`. The participle heads its clause; the auxiliary and the passive subject depend on it.

#### 4.2.3 The agent: `obl:agent`

**Use** [`obl:agent`](https://universaldependencies.org/u/dep/obl-agent.html) for the expressed agent of a passive predicate, typically *a/ab* with the ablative. The test is whether the participant would be the subject of the corresponding active clause.

**Do not use for** an instrument or cause, which may be marked alike but would not be the active subject (`obl`). The dative of agent with a gerundive follows the same test.

**Examples**

- *accersitus ab aedile … nondum rediit* ‘summoned by the aedile, he has not yet returned’ (S000041): *aedile* (4) `obl:agent`; *ab* (3) `case`; *nondum* (12) `advmod:tmod`.
- *vilicus … appellatus a villa* ‘the steward [was] named after the villa’ (S000089): *villa* (9) `obl`. *a villa* looks like an agent, but the villa would not be the subject of the active clause: it is what the steward is named after.

### 4.3 Subjects

#### 4.3.1 `nsubj`

**Use** [`nsubj`](https://universaldependencies.org/u/dep/nsubj.html) for a nominal that is the syntactic subject of a predicate. In a copular clause the head is the nonverbal predicate, not the copula (Section 1.3.3), so the governor of `nsubj` need not be a verb.

**Do not use for** a clausal subject (`csubj`), or the subject of a passive predicate (`nsubj:pass`, Section 4.2).

**Head and dependent.** Head: the predicate of the clause. Dependent: `NOUN`, `PROPN`, `PRON`; also `ADJ` substantivized or under ellipsis.

**Examples**

- *si est homo bulla* ‘if man is a bubble’ (S000001): *homo* (31) `nsubj`; *bulla* (32) `advcl`; *est* (30) `cop`. The subject depends on the nominal predicate bulla, not on the copula.

**Subtypes**

| Subtype | Use for | See |
|---|---|---|
| `nsubj:pass` | the subject of a passive predicate | Section 4.2.1 |
| `nsubj:outer` | the subject of a copular clause whose predicate is itself a clause | Section 4.10.2 |
| [`nsubj:cleft`](https://universaldependencies.org/la/dep/nsubj-cleft.html) | the residual subject of a cleft sentence, where a copular predication puts an extracted element into focus and a relative clause with an overt antecedent recovers the gap | — |

#### 4.3.2 `csubj`

**Use** [`csubj`](https://universaldependencies.org/u/dep/csubj.html) for a clause that is the subject of a predicate. Before assigning `advcl` or `acl` to a subordinate clause, check whether the matrix predicate needs a subject that no nominal fills: an impersonal verb (*oportet*, *convenit*) or a passive verb of judging or deciding with no nominal subject. Where it does, test `csubj` first.

**Do not use for** a nominal subject (`nsubj`); a clause filling a complement slot (`ccomp`, `xcomp`); a clause modifying the predicate as an adjunct (`advcl`).

**Head and dependent.** Head: the predicate of the clause. Dependent: the head of the subject clause, finite, non-finite, or nonverbal.

**Examples**

- *quo quicque tempore in eo fundo fieri conveniat* ‘at what time it is fitting for each thing to be done on that farm’ (S000164): *fieri* (9) `csubj`; *conveniat* (10) `root`. The infinitive clause is the subject of impersonal conveniat.

**Subtypes**

| Subtype | Use for | See |
|---|---|---|
| `csubj:pass` | the clausal subject of a passive predicate | Section 4.2.1 |
| `csubj:outer` | the clausal subject of a copular clause whose predicate is itself a clause | Section 4.10.2 |
| `csubj:relcl` | a free relative clause as the subject | Section 4.8 |
| `csubj:reported` | a reported clause as the subject of a passive verb of saying | Section 4.12.2 |
| [`csubj:cleft`](https://universaldependencies.org/la/dep/csubj-cleft.html) | the residual subject of a cleft sentence, where the relative clause has no antecedent | — |

### 4.4 Objects, obliques, and adverbial modifiers

#### 4.4.1 `obj`

**Use** [`obj`](https://universaldependencies.org/u/dep/obj.html) for the most core non-subject argument of a predicate: the participant most directly affected by, or undergoing, what the predicate expresses. Decide by whether the case marks a core argument of this particular predicate, not by the case alone: an argument in a non-core case is `obl` (usually `obl:arg`) even where traditional grammar calls it an object.

**Do not use for** a non-core argument or adjunct (`obl`); a clausal complement (`ccomp`, `xcomp`). Where a predicate takes two objects, the more directly affected is `obj` and the other `iobj`.

**Head and dependent.** Head: the predicate. Dependent: `NOUN`, `PROPN`, `PRON`, or a substantivized `ADJ`.

**Examples**

- *otium si essem consecutus, Fundania, commodius tibi haec scriberem* ‘if I had obtained leisure, Fundania, I would write this to you more conveniently’ (S000001): *Fundania* (6) `vocative`; *tibi* (9) `obl:arg`; *haec* (10) `obj`; *commodius* (8) `advmod`.

#### 4.4.2 `iobj`

**Use** [`iobj`](https://universaldependencies.org/u/dep/iobj.html) only for the second object of the verbs *doceo*, *celo*, *posco*, *flagito*, and *rogo*. Extend the list only with a recorded justification.

**Do not use for** an ordinary dative argument. A dative is oblique (`obl:arg` or `obl`) unless there is positive evidence that it marks a core argument of that predicate; morphological case alone is never such evidence.

#### 4.4.3 `obl`

**Use** [`obl`](https://universaldependencies.org/u/dep/obl.html) for a nominal dependent of a predicate that is not one of its core arguments: an oblique argument or an adjunct. `obl` is the default for a nominal in that position; use a subtype only where its own condition is positively met.

**Do not use for** a nominal dependent of a nominal (`nmod`: the governor decides, not the nominal's own form or meaning); an adverbial realized as an adverb (`advmod`); a core argument (`nsubj`, `obj`, `iobj`).

**Head and dependent.** Head: the predicate (a verb, adjective, adverb, or nonverbal predicate). Dependent: `NOUN`, `PROPN`, `PRON`, or a substantivized `ADJ`.

**Examples**

- *iis igitur deis ad venerationem advocatis* ‘with those gods invoked for veneration’ (S000021): *venerationem* (5) `obl`; *ad* (4) `case`. An adjunct of purpose: plain obl.

**Subtypes**

| Subtype | Use for | Example |
|---|---|---|
| [`obl:arg`](https://universaldependencies.org/u/dep/obl-arg.html) | an oblique the predicate's own valency selects, as against an adjunct; it takes precedence over a semantic subtype where both would apply (Section 4.15.1) | *tibi* (S000001:9) |
| [`obl:lmod`](https://universaldependencies.org/u/dep/obl-lmod.html) | place where, to which, or from which, realized as a nominal | *in eo fundo* (S000164:8) |
| [`obl:tmod`](https://universaldependencies.org/u/dep/obl-tmod.html) | time, realized as a nominal | *post mortem* (S000004:20) |
| `obl:agent` | the agent of a passive predicate | Section 4.2.3 |
| [`obl:cmp`](https://universaldependencies.org/la/dep/obl-cmp.html) | a bare nominal standard of comparison with no overt *quam*; the nominal counterpart of `advcl:cmp` | *Italia* (S000044; Section 6.6) |

#### 4.4.4 `advmod`

**Use** [`advmod`](https://universaldependencies.org/u/dep/advmod.html) for a non-clausal modifier realized as an adverb, modifying a predicate, an adjective, another adverb, or, in limited cases, a nominal. The criterion is formal: the same meaning realized as a case-marked nominal or an adpositional phrase is `obl`.

**Do not use for** an adverbial realized as a nominal or adpositional phrase (`obl`); a clausal modifier (`advcl`); a particle or connective adverb that links the clause to the surrounding discourse (`discourse`, Section 4.13).

**Head and dependent.** Head: the predicate, or the word modified. Dependent: `ADV` (and `PART` for negation and focus particles).

**Examples**

- *et non solum … ut te moneam, sed etiam post mortem* ‘and to advise you not only [while I live] but even after death’ (S000004): *non* (2) `advmod:neg`; *etiam* (18) `advmod:emph`; *mortem* (20) `obl:tmod`. non attaches to solum, the word it scopes over, and etiam to the phrase it focuses, not to the predicate.

**Subtypes**

| Subtype | Use for | Example |
|---|---|---|
| [`advmod:neg`](https://universaldependencies.org/la/dep/advmod-neg.html) | a negative particle; attach it to what the negation scopes over, not automatically to the predicate | *non* (S000004:2) |
| [`advmod:emph`](https://universaldependencies.org/u/dep/advmod-emph.html) | a focus or emphasis marker; attach it to the constituent it focuses | *etiam* (S000105:3) |
| [`advmod:lmod`](https://universaldependencies.org/u/dep/advmod-lmod.html) | place, realized as an adverb (the adverbial counterpart of `obl:lmod`) | *ibi* (S000174:6) |
| [`advmod:tmod`](https://universaldependencies.org/la/dep/advmod-tmod.html) | time, realized as an adverb (the adverbial counterpart of `obl:tmod`) | *nondum* (S000041:12) |

#### 4.4.5 `case`

**Use** [`case`](https://universaldependencies.org/u/dep/case.html) for an adposition, attached to the nominal it introduces, never to the predicate on which that nominal depends. A case ending is part of the noun and recorded in `FEATS`.

**Do not use for** a subordinator introducing a clause (`mark`): `case` marks nominals, `mark` marks clauses. The words of a frozen multiword preposition take `fixed` among themselves (Section 4.11.1).

#### 4.4.6 `vocative`

**Use** [`vocative`](https://universaldependencies.org/u/dep/vocative.html) for a nominal addressing the person or thing spoken to, attached to the main predicate of its sentence. Read a nominal that is clearly vocative in intent as vocative even where the clause's other argument slots are filled, or its subject is null.

**Do not use for** a nominal filling an argument slot of the predicate.

**Examples**: *Fundania* (S000001:6), in the first example of Section 4.4.1.

### 4.5 Nominal modification

#### 4.5.1 `nmod`

**Use** [`nmod`](https://universaldependencies.org/u/dep/nmod.html) for a nominal dependent of a nominal: a genitive, or a nominal with an adposition (which attaches to it as `case`). Every Latin genitive possessor, including a genitive pronoun such as *eius*, takes plain `nmod`; UD's `nmod:poss` is not used in Latin.

**Do not use for** a nominal dependent of a predicate (`obl`); a nominal that renames its head (`appos`); a nominal that predicates a circumstance of its head (`advcl:pred`, Section 4.15.3). A numeral used as a label rather than a quantity is `nmod` despite its `NUM` category.

**Head and dependent.** Head: a nominal. Dependent: `NOUN`, `PROPN`, `PRON`, or a substantivized `ADJ`.

**Examples**

- *eius principia sunt eadem* ‘its elements are the same’ (S000138): *eius* (1) `nmod`, `Case=Gen`. A genitive pronoun used possessively takes plain nmod, not det:poss.

#### 4.5.2 `amod`

**Use** [`amod`](https://universaldependencies.org/u/dep/amod.html) for an adjective modifying a nominal. For a participle, follow the part of speech already assigned (Section 2.4): a participle tagged `ADJ` is `amod`, one tagged `VERB` is `acl`.

**Do not use for** a clausal modifier, including a participle tagged `VERB` (`acl`); a secondary predicate (`advcl:pred`); a determiner (`det`); a cardinal numeral (`nummod`). An ordinal numeral is `ADJ` and takes `amod`.

> *Cato senex* read as ‘old Cato’ characterizes Cato: `amod`. The same words read as ‘Cato, when old’ state a circumstance holding of him: `advcl:pred`. The two readings agree alike, so only meaning decides (Section 4.15.3).

**Examples**

- *quos Cassius Dionysius Uticensis vertit* ‘which Cassius Dionysius of Utica translated’ (S000030): *Cassius* (17) `nsubj`; *Dionysius* (18) `flat:name`; *Uticensis* (19) `amod`. The name itself is flat; the descriptive adjective of origin is an ordinary amod outside it.

#### 4.5.3 `acl`

**Use** [`acl`](https://universaldependencies.org/u/dep/acl.html) for a clause modifying a nominal: a participle tagged `VERB`, a content clause dependent on a noun, or any other clause attached to a nominal. The clause may be finite or non-finite.

**Do not use for** a clause modifying a predicate (`advcl`); a clause renaming or restating a clause (`parataxis`, `conj:expl`).

**Head and dependent.** Head: a nominal. Dependent: the head of the modifying clause.

**Subtypes**

| Subtype | Use for | See |
|---|---|---|
| `acl:relcl` | a relative clause with an overt antecedent | Section 4.8 |

#### 4.5.4 `det`

**Use** [`det`](https://universaldependencies.org/u/dep/det.html) for a word tagged `DET` modifying a nominal (Section 2.3): demonstratives, identity words, indefinites and quantifiers, including an indefinite quantifier that expresses an approximate quantity.

**Do not use for** an adjective (`amod`) or a cardinal numeral (`nummod`).

**Examples**

- *necessariis meis quod prosit facere* ‘to do what may benefit my family’ (S000007): *meis* (9) `det:poss`.

**Subtypes**

| Subtype | Use for | Example |
|---|---|---|
| [`det:poss`](https://universaldependencies.org/u/dep/det-poss.html) | every possessive adjective tagged `DET` with `Poss=Yes` (*meus*, *tuus*, *suus*, *noster*, *vester*) | *meis* (S000007:9) |

#### 4.5.5 `nummod`

**Use** [`nummod`](https://universaldependencies.org/u/dep/nummod.html) for a cardinal numeral expressing the quantity of the nominal it modifies.

**Do not use for** an ordinal (`ADJ`, `amod`); an indefinite quantifier (`DET`, `det`); a numeral used as a label (`nmod`). Where the number is what is asserted, the numeral is the predicate (Figure 4).

**Examples**

- *scribam tibi tres libros indices* ‘I shall write for you three books as guides’ (S000008): *tres* (4) `nummod`; *indices* (6) `appos`.

#### 4.5.6 `appos`

**Use** [`appos`](https://universaldependencies.org/u/dep/appos.html) for a nominal that renames, defines, or re-identifies the referent of an adjacent nominal, agreeing with it in case. Both halves must be complete nominals that could be exchanged with the same reference. The requirement is by part of speech: a `NOUN`, `PROPN`, or `PRON` qualifies also when it heads a copular clause of its own; a `VERB` never does. Attach every appositive of one nominal directly to that nominal; never chain them.

**Do not use for**:
- a nominal that modifies rather than renames (`nmod`);
- a multiword name whose parts do not refer independently (`flat:name`);
- a nominal predicating a circumstance of its head (`advcl:pred`);
- a verb-headed clause: UD restricts `appos` to two nominals. A clause elaborating a noun is `acl`; a clause restating a clause is `parataxis` or `conj:expl`.

The restatement of a conjunct at equal standing, rather than a backgrounded renaming, is `conj:expl` (Section 4.9.1).

**Examples**: *indices* (S000008:6), in the example of Section 4.5.5.

- *haec quattuor … quae sit forma* ‘these four things … what its shape is’ (S000170): *forma* (12) `appos`; *quae* (10) `nsubj`; *sit* (11) `cop`. forma is a noun heading a copular clause of its own (Section 1.3.3), and as a noun it can be appos.
- *ex radicibus trinis, et quae ipse … animadverti* ‘from three roots, both what I myself have observed …’ (S000035): *animadverti* (14) `acl`; *radicibus* (4) `root`. The clause naming the roots is headed by a verb, so it is acl, not appos.

### 4.6 Clausal complements

#### 4.6.1 `ccomp`

**Use** [`ccomp`](https://universaldependencies.org/u/dep/ccomp.html) for a clause that fills a core argument slot of the governing predicate and supplies its own subject. Finiteness is not the criterion: the accusative and infinitive is a non-finite complement with its own accusative subject and takes `ccomp` (Section 6.3); a complement may equally be finite, participial, or verbless.

**Do not use for** a complement whose subject is obligatorily controlled by a matrix argument (`xcomp`); an adjunct clause (`advcl`); a clause dependent on a nominal (`acl`).

**Head and dependent.** Head: the governing predicate. Dependent: the head of the complement clause.

**Examples**

- *C. Licinium Stolonem … video venire* ‘I see Gaius Licinius Stolo coming’ (S000071): *venire* (12) `ccomp`; *C* (2) `nsubj`. The accusative-and-infinitive has its own accusative subject and takes ccomp; the name C. Licinius Stolo is headed by its first element, C.

**Subtypes**

| Subtype | Use for | See |
|---|---|---|
| `ccomp:relcl` | a free relative clause filling the complement slot | Section 4.8 |
| `ccomp:reported` | reported speech within the dialogue, governed by the reporting verb | Section 4.12.2 |

#### 4.6.2 `xcomp`

**Use** [`xcomp`](https://universaldependencies.org/u/dep/xcomp.html) for a complement with no subject of its own, whose understood subject is obligatorily controlled by a fixed argument of the matrix clause, with no other reading possible. The complement may be an infinitive or a nonverbal predicate (Figure 3).

**Do not use for** a complement with its own subject, including the accusative and infinitive (`ccomp`); an optional predicative element the clause is grammatical without (`advcl:pred`, Section 4.15.4).

**Head and dependent.** Head: the controlling predicate. Dependent: the head of the complement.

**Examples**

- *ne arbor olea … a capra tangi possit* ‘so that the olive tree cannot be touched by a goat’ (S000105): *tangi* (28) `xcomp`; *arbor* (17) `nsubj`. The understood subject of tangi is controlled by the subject of possit.

**Subtypes**

| Subtype | Use for | See |
|---|---|---|
| [`xcomp:relcl`](https://universaldependencies.org/la/dep/xcomp-relcl.html) | a free relative clause as an open complement | Section 4.8 |

### 4.7 Adverbial clauses

#### 4.7.1 `mark`

**Use** [`mark`](https://universaldependencies.org/u/dep/mark.html) for the word that marks a clause as subordinate, attached to the subordinate clause's own head, never to the matrix clause: complementizers, adverbial subordinators, and an uninflected relative introducer that fills no role in its clause.

**Do not use for** a relative or interrogative word that fills an argument or modifier slot in its clause (it takes the relation of that slot); an adposition (`case`); a coordinating conjunction (`cc`).

#### 4.7.2 `advcl`

**Use** [`advcl`](https://universaldependencies.org/u/dep/advcl.html) for a clause modifying a predicate as an adjunct, in any adverbial relation: temporal, causal, conditional, concessive, purposive, resultative.

**Do not use for** a clause modifying a nominal (`acl`); a clause that is an argument of the predicate (`ccomp`, `csubj`, `xcomp`; Section 4.15.5); a non-clausal modifier (`advmod`).

**Head and dependent.** Head: the predicate modified. Dependent: the head of the modifying clause, finite or non-finite.

**Examples**

- *haec enim cognoscenda, priusquam iacias semina, quod initium fructuum oritur* ‘for these things must be learnt before you sow the seed, which comes up as the beginning of the crop’ (S000139): *priusquam* (5) `mark`; *iacias* (6) `advcl`; *initium* (10) `advcl:pred`; *quod* (9) `DEPS` 10:nsubj. initium states what the seed is when it comes up; the Enhanced graph adds the nsubj edge from initium to its overt co-referent quod.

**Subtypes**

| Subtype | Use for | See |
|---|---|---|
| [`advcl:cmp`](https://universaldependencies.org/la/dep/advcl-cmp.html) | a comparative clause, typically with *quam* or *ut*; a bare nominal remnant of an elided comparative predicate still takes it | Section 6.6 |
| [`advcl:relcl`](https://universaldependencies.org/u/dep/advcl-relcl.html) | an adverbial clause introduced by a relative word; a correlative (*ibi*, *ideo*) in the main clause marks it as adverbial | Section 4.8 |
| `advcl:pred` | a secondary predicate | Section 4.7.3 |
| `advcl:abs` | an ablative absolute | Section 4.7.4 |

#### 4.7.3 Secondary predicates: `advcl:pred`

**Use** [`advcl:pred`](https://universaldependencies.org/la/dep/advcl-pred.html) for a bare noun, adjective, or participle that supplies a second, concurrent predication about an argument of the clause (Section 1.3.4). Attach it to the predicate of the clause, never to the nominal it describes, whether that nominal is overt or elided (Figure 2).

**Do not use for** an element that characterizes the nominal rather than stating something that holds of it in the situation (`amod`, `acl`, `appos`, or, with the nominal elided, the argument relation itself; Section 4.15.3); an element the predicate's valency requires (`xcomp`; Section 4.15.4).

**Enhanced layer.** Where the co-referent nominal is overt, add two Enhanced edges: a plain `advcl` edge from the predicate to the predicative word, and an edge from the predicative word to the co-referent (`nsubj` in the attested pattern). Where it is elided, add none (Section 5.5).

> **Background.** What makes a bare noun, adjective, or participle predicate at all is a covert predicational link, the equivalent of a copula. Latin cannot express that link, since *sum* has no participle, so nothing has been elided from the text; the link is simply never overt. With a participle as the predicating element, this is what traditional grammar calls *participium coniunctum* (Section 6.2).

**Examples**

- *haec enim cognoscenda, priusquam iacias semina, quod initium fructuum oritur* ‘for these things must be learnt before you sow the seed, which comes up as the beginning of the crop’ (S000139): *priusquam* (5) `mark`; *iacias* (6) `advcl`; *initium* (10) `advcl:pred`; *quod* (9) `DEPS` 10:nsubj. initium states what the seed is when it comes up; the Enhanced graph adds the nsubj edge from initium to its overt co-referent quod.
- *quaedam in montanis prolixiora nascuntur … propter frigus, ut abietes ac sappini* ‘some things grow taller in the mountains … because of the cold, as firs and pines do’ (S000178): *prolixiora* (4) `advcl:pred`, `DEPS` 5:advcl; *ut* (11) `mark`; *abietes* (12) `advcl:cmp`. abietes is the bare nominal remnant of an elided comparative clause and still takes advcl:cmp.

#### 4.7.4 Ablative absolute: `advcl:abs`

**Use** [`advcl:abs`](https://universaldependencies.org/la/dep/advcl-abs.html) for an ablative nominal with a predicate agreeing with it (typically a participle, also an adjective or noun) forming a predication independent of the main clause. The test is formal: the agreeing ablative pair. The semantic relation (temporal, causal, concessive) is not recorded. Attach the ablative noun to its own predicate as `nsubj` (`nsubj:pass` with a passive participle), and the predicate to the main clause's predicate (Section 6.1, Figure 8).

**Do not use for** a construction whose ablative subject is coreferent with an argument of the main clause (`advcl:pred`).

**Examples**

- *iis igitur deis ad venerationem advocatis ego referam* ‘these gods, then, having been called upon in worship, I shall report [the conversations]’ (S000021): *advocatis* (6) `advcl:abs`; *deis* (3) `nsubj:pass`.

### 4.8 Relative clauses

An adnominal relative clause modifying an overt nominal antecedent takes [`acl:relcl`](https://universaldependencies.org/u/dep/acl-relcl.html), one subtype of the more general clausal-modifier relation [`acl`](https://universaldependencies.org/u/dep/acl.html). What licenses `acl:relcl` specifically is the presence, inside the modifying clause, of a relative word — a form of *qui*, or a relative adverb — coreferential with the antecedent and filling an argument or modifier role inside that clause; finiteness is not a criterion in Latin, and the clause's own head may be a finite verb, a participle, or a nonverbal predicate with no verb at all. A clause introduced by an interrogative word is an indirect question, not a relative clause, however similar the surface form.

A free (headless) relative clause — no overt antecedent — is not adnominal at all: the relative word does double duty, filling a role inside its own clause while the whole clause fills a role in the matrix one, and the relation is named for that outer role instead — [`csubj:relcl`](https://universaldependencies.org/la/dep/csubj-relcl.html) as a clausal subject, `ccomp:relcl`/`xcomp:relcl` as a clausal complement (Section 4.6), `advcl:relcl` as an adverbial (Section 4.7). All four apply the same general mechanism of combining a core relation with the `:relcl` subtype, and none is a treebank-specific device.

Annotate the relative word for its role inside its own clause (`nsubj`, `obj`, `obl`, `advmod` and so on); the `:relcl` subtype of the outer relation records the clause's role outside it.

| Subtype | Clause role | Antecedent |
|---|---|---|
| [`acl:relcl`](https://universaldependencies.org/u/dep/acl-relcl.html) | modifier of a nominal | overt nominal |
| [`csubj:relcl`](https://universaldependencies.org/la/dep/csubj-relcl.html) | subject | none (free relative) |
| [`ccomp:relcl`](https://universaldependencies.org/la/dep/ccomp-relcl.html) | complement with its own subject | none (free relative) |
| [`xcomp:relcl`](https://universaldependencies.org/la/dep/xcomp-relcl.html) | open complement | none (free relative) |
| [`advcl:relcl`](https://universaldependencies.org/u/dep/advcl-relcl.html) | adverbial | the preceding predication, often answered by a correlative |

Free relatives as a construction are treated in Section 6.5.

**Examples**

- *arbor olea, quae primum dicitur ibi nata* ‘the olive tree, which is said to have first grown there’ (S000105): *dicitur* (22) `acl:relcl`; *quae* (20) `nsubj:pass`.
- *qui colunt deorsum, magis aestate laborant* ‘those who farm low down suffer more in summer’ (S000175): *colunt* (2) `csubj:relcl`; *qui* (1) `nsubj`.
- *se reliquit qui rogaret* ‘he left [someone] who would ask’ (S000041): *rogaret* (21) `ccomp:relcl`; *qui* (20) `nsubj`. A free relative fills the complement slot of reliquit; qui is annotated for its role inside its own clause.
- *ubi lati campi, ibi magis aestus* ‘where the plains are wide, there the heat is greater’ (S000174): *lati* (3) `advcl:relcl`; *ibi* (6) `advmod:lmod`; *campi* (4) `nsubj`. The correlative ibi fills the slot in the main clause, so the verbless ubi-clause is adverbial, not a clausal subject.

### 4.9 Coordination

#### 4.9.1 `conj`

**Use** [`conj`](https://universaldependencies.org/u/dep/conj.html) for each non-first conjunct of a coordination, attached to the first conjunct: from the first to the second, from the first to the third, and so on, never to a shared external head and never chained through the intervening conjuncts. Coordination may be asyndetic. In the Basic tree a dependent shared by the conjuncts attaches to the first conjunct only; its Enhanced edges to the other conjuncts are not yet added (Section 5.2).

**Do not use for** the conjunction itself (`cc`); juxtaposed units with no coordination (`parataxis`, Section 4.15.7).

**Examples**

- *aqua, terra, anima et sol* ‘water, earth, air and sun’ (S000138): *terra* (14) `conj`; *anima* (16) `conj`; *sol* (18) `conj`; *et* (17) `cc`. All three later conjuncts attach to aqua, and only sol, which carries the conjunction, has a cc dependent.
- *et Poenice et Graece et Latine* ‘in Punic, in Greek and in Latin’ (S000085): *Graece* (12) `conj`; *Latine* (14) `conj`; *et* (13) `cc`. Graece and Latine both attach to Poenice, not to each other; each et attaches to the conjunct it introduces.
- *hoc ter noviens cantare iubet, terram tangere, despuere, ieiunum cantare* ‘he bids [one] chant this twenty-seven times, touch the ground, spit, chant fasting’ (S000129): *tangere* (8) `conj`; *despuere* (10) `conj`; *cantare* (13) `conj`. Asyndetic coordination: no conjunction, every later infinitive attached to the first cantare.

**Subtypes**

| Subtype | Use for |
|---|---|
| [`conj:expl`](https://universaldependencies.org/la/dep/conj-expl.html) | an explicative conjunct that restates, reformulates, or expands the preceding one rather than adding a parallel item, often introduced by *scilicet* or *id est*. It differs from apposition by status: the explicative conjunct is coordinated at equal standing, where an apposition backgrounds the renaming element. |

#### 4.9.2 `cc`

**Use** [`cc`](https://universaldependencies.org/u/dep/cc.html) for a coordinating conjunction, attached to the conjunct it introduces, not to the first conjunct. In a series, only a conjunct that carries a conjunction has a `cc` dependent. A sentence-initial coordinating conjunction with no coordination in the sentence still takes `cc`, attached to the head of the clause.

**Do not use for** a subordinating conjunction (`mark`).

### 4.10 Copulas and auxiliaries

#### 4.10.1 `cop`

**Use** [`cop`](https://universaldependencies.org/u/dep/cop.html) for a form of *sum* linking a subject to a nonverbal predicate; the predicate is the head (Section 1.3.3). Tag the copula `AUX`. Every clause built on *sum* has a predicating element to find; a predicate that is not immediately obvious is a reason to look further, not to make *sum* the head. A form of *sum* carries the clause's external relation only where the predicate is itself a clause (Section 4.10.2) or is elided (Section 4.1.2).

**Do not use for** a form marking tense or voice on a verbal predicate (`aux`, `aux:pass`; Section 4.15.6); a verb with lexical content of its own taking a predicative complement (`xcomp`).

**Head and dependent.** Head: the nonverbal predicate (`ADJ`, `NOUN`, `PRON`, `DET`, `NUM`, `ADV`; for an adpositional phrase, its noun). Dependent: the copula.

**Examples**

- *quod utile est* ‘what is useful’ (S000142): *utile* (5) `csubj:relcl`; *est* (6) `cop`.

#### 4.10.2 Copular clauses with a clausal predicate: `nsubj:outer`, `csubj:outer`, `cop:outer`

**Use** [`nsubj:outer`](https://universaldependencies.org/u/dep/nsubj-outer.html) (or [`csubj:outer`](https://universaldependencies.org/u/dep/csubj-outer.html) for a clausal subject) for the subject of a copular clause whose predicate is itself a clause, and [`cop:outer`](https://universaldependencies.org/la/dep/cop-outer.html) for its copula.

The deciding test for the `:outer` subtypes is that the predicate of the copular clause is itself a clause. They show that the subject belongs to the outer copular clause and is not the subject of the clause nested inside it. Where the predicate is a noun, an adjective, or anything else that is not a clause, the plain relations apply: in *ea est scientia* (S000137) *ea* is plain `nsubj` of *scientia*. Only the subject and the copula of the outer clause take the subtypes; other dependents keep their ordinary relations.

![Dependency tree of quod est Romanus sedendo vincit (S000042): vincit heads the clause, with quod as nsubj:outer, est as cop:outer, Romanus as nsubj and sedendo as advcl](figures/outer_S000042.svg)

*Figure 5.* *quod est “Romanus sedendo vincit”* ‘which is “the Roman wins by sitting still”’ (S000042). The proverb is the predicate of the relative clause, and its head *vincit* heads the whole copular clause. *vincit* already has a subject of its own, *Romanus*, so the relative pronoun *quod*, the subject of the outer predication, is `nsubj:outer`, and the copula *est* is `cop:outer`.

The copula is often elided, and `nsubj:outer` then stands without a `cop:outer` partner; the missing copula is not a reason to doubt the analysis. The subtypes are easy to over-apply to ordinary copular clauses, so every use is justified in a review note.

**Enumerated items.** In a list such as the parts of agriculture (*prima …, secunda …*, from S000161 on), the content of each item heads its clause, and the ordinal is its `nsubj`, or `nsubj:outer` where that clause already has a subject of its own. No copula is supplied and no empty node is added.

**Examples**

- *vetus proverbium, quod est “Romanus sedendo vincit”* ‘the old proverb, which is “the Roman wins by sitting still”’ (S000042): *quod* (7) `nsubj:outer`; *est* (8) `cop:outer`; *Romanus* (10) `nsubj`; *vincit* (12) `acl:relcl`. The copular predicate is itself a clause with its own subject, so the outer subject and copula take the :outer subtypes.
- *nullam arbitror esse quae tam tota sit culta* ‘I think there is none that is so wholly cultivated’ (S000045): *sit* (12) `aux:pass`; *culta* (13) `ccomp`; *esse* (8) `cop:outer`; *nullam* (6) `nsubj:outer`. sit supports a passive process (being cultivated), while the outer copula esse supports the clausal predicate headed by culta.
- *quarta, quo quicque tempore in eo fundo fieri conveniat* ‘the fourth [part is] at what time it is fitting for each thing to be done on that farm’ (S000164): *quarta* (1) `nsubj:outer`; *conveniat* (10) `root`; *fieri* (9) `csubj`. The copula is elided; conveniat has its own subject, the infinitive clause, so the list item quarta is the outer subject.
- *e quis prima cognitio fundi* ‘of which the first is knowledge of the farm’ (S000161): *prima* (3) `nsubj`; *cognitio* (4) `root`. The predicate cognitio has no subject of its own, so the list item takes plain nsubj.

#### 4.10.3 `aux`

**Use** [`aux`](https://universaldependencies.org/u/dep/aux.html) for a function word expressing tense, mood, aspect, or evidentiality on a verbal predicate, which remains the head; in Latin, a form of *sum* with an active or deponent participle.

**Do not use for** the passive auxiliary (`aux:pass`, Section 4.2.2); a copula (`cop`); a verb with lexical content taking a clausal complement (`xcomp`, `ccomp`).

**Examples**

- *otium si essem consecutus* ‘if I had obtained leisure’ (S000001): *essem* (3) `aux`; *consecutus* (4) `advcl`.

**Subtypes**

| Subtype | Use for | See |
|---|---|---|
| `aux:pass` | the passive auxiliary, including *sum* in the passive periphrastic | Section 4.2.2 |

### 4.11 Fixed expressions and flat structures

#### 4.11.1 `fixed`

**Use** [`fixed`](https://universaldependencies.org/u/dep/fixed.html) only for an expression on the closed list of fully grammaticalized multiword function words. Attach every word of the expression to its first word, which carries `ExtPos` for the part of speech of the whole. An expression is never admitted because it feels idiomatic.

**Do not use for** a multiword expression of content words (`flat`); a sequence whose parts keep their own functions (ordinary relations).

**Examples**

- *quem ad modum quidque te in colendo oporteat facere* ‘how you ought to do each thing in farming’ (S000008): *quem* (18) `advmod`, `ExtPos=ADV`; *ad* (19) `fixed`; *modum* (20) `fixed`. Both later words of quem ad modum attach to its first word, which carries ExtPos for the whole expression.

#### 4.11.2 `flat`

**Use** [`flat`](https://universaldependencies.org/u/dep/flat.html) for a multiword expression in which no component passes the head test, attaching every component to the first word (Section 1.3.1). Look for an internal head first: an expression with real internal syntax takes ordinary relations even where it looks like a single unit.

**Do not use for** a grammaticalized function-word expression (`fixed`); independently referring nominals in apposition (`appos`).

**Subtypes**

| Subtype | Use for |
|---|---|
| `flat:name` | a multi-token proper name (Section 4.11.3) |
| [`flat:foreign`](https://universaldependencies.org/u/dep/flat-foreign.html) | a quoted foreign-language span whose internal syntax is not analysed; a single unanalysed foreign word is marked `Foreign=Yes` instead (Section 3.2.2), and a loanword takes its ordinary relation |
| [`flat:gov`](https://universaldependencies.org/la/dep/flat-gov.html) | a partitive-like pairing whose second, oblique-case element is coreferential with the first rather than modifying it: *urbs Romae* ‘the city of Rome’, where Rome is the city |

#### 4.11.3 Names: `flat:name`

**Use** [`flat:name`](https://universaldependencies.org/u/dep/flat-name.html) for the components of a multi-token proper name, chiefly the Roman *praenomen*, *nomen*, and *cognomen*, attached to the first component. Keep the flat span minimal: a descriptive adjective, a determiner, or an embedded phrase in a name or title takes its ordinary relation.

**Examples**

- *quos Cassius Dionysius Uticensis vertit* ‘which Cassius Dionysius of Utica translated’ (S000030): *Cassius* (17) `nsubj`; *Dionysius* (18) `flat:name`; *Uticensis* (19) `amod`. The name itself is flat; the descriptive adjective of origin is an ordinary amod outside it.

### 4.12 Parataxis and reported speech

#### 4.12.1 `parataxis`

**Use** [`parataxis`](https://universaldependencies.org/u/dep/parataxis.html) for two units placed side by side with no coordination, subordination, or argument relation between them. The head of the first unit governs; the head of the second is the `parataxis` dependent. The dependent need not be a full clause, and a connective that is not a conjunction between the units does not make the relation coordination or subordination.

**Do not use for** a conditional or other marked subordinate clause (`advcl`, `acl`, `ccomp`, `csubj`), even where a correlative answers it; coordination (`conj`, Section 4.15.7); an element in an argument relation to the head.

**Examples**

- *ego tui memini, medere meis pedibus* ‘I remember you: heal my feet’ (S000128): *memini* (4) `root`; *medere* (6) `parataxis`.

#### 4.12.2 Reported speech: `parataxis:reporting`, `ccomp:reported`, `csubj:reported`

Reported speech forms a small, tightly coupled family of three relations. [`parataxis:reporting`](https://universaldependencies.org/la/dep/parataxis-reporting.html) marks a reporting clause outside the dialogue: the narrator's frame around a speaker's words, predominantly *inquam* or *inquit*, which does not govern the words it frames. [`ccomp:reported`](https://universaldependencies.org/la/dep/ccomp-reported.html) marks reported speech within the dialogue: whatever one of the speakers says belongs to the dialogue, so when a speaker reports or quotes words, Cato's for instance, the reporting verb in that speaker's utterance governs them as its object. [`csubj:reported`](https://universaldependencies.org/la/dep/csubj-reported.html) marks a reported clause in subject position of a passive verb of saying, the only position in which a reported-speech subject can arise at all, since an active saying verb's reported content is its object and therefore takes `ccomp:reported` instead.

> **Background.** Keeping the narrative frame out of `ccomp:reported` is a deliberate departure from harmonized Latin practice, which extends that relation even to a reporting verb interrupting a quotation; it holds the frame of the dialogue apart from the dialogue itself.

**Examples**

- *ecquam cultiorem Italia vidistis? inquit.* ‘“have you seen any [land] more cultivated than Italy?” he said’ (S000044): *inquit* (18) `parataxis:reporting`; *vidistis* (16) `root`. The quoted question is the root; the reporting verb attaches to it and does not govern it.
- *illud non dicis – inquit Agrius – quod scribit, si velis … ante esse oportet brassicam crudam* ‘you do not mention this, said Agrius, what he writes: “if you want …, you must first eat raw cabbage”’ (S000133): *inquit* (5) `parataxis:reporting`; *oportet* (24) `ccomp:reported`. The narrator's frame stands outside the dialogue; Agrius's quotation of Cato is inside it, governed by *scribit* (9).

### 4.13 Discourse elements

#### 4.13.1 `discourse`

**Use** [`discourse`](https://universaldependencies.org/u/dep/discourse.html) for a word whose contribution is pragmatic rather than propositional and which plays no part in the clause's argument structure: an interjection, a pragmatic or connective particle (*enim*, *igitur*, *itaque*, *quoque*), a connective adverb, a list enumerator. Attach it to the head of the nearest relevant unit, normally the clause. Function decides, not part of speech: an adverb that links its clause to the surrounding discourse without modifying an individual word (*vero*) is `discourse` and stays `ADV`.

**Do not use for** an adverb that modifies an individual word or phrase, or adds to the content of the clause (time, place, manner, degree) (`advmod`); a focus particle scoping over a specific constituent (`advmod:emph`): *etiam* ‘even’ is `advmod:emph`, *quoque* ‘also’ is `discourse`.

**Examples**

- *vocabulis quoque sunt diversi* ‘they are also different in their titles’ (S000088): *quoque* (8) `discourse`.
- *hoc nomine etiam Athenis in arcem non inigi* ‘for this reason, even at Athens, [goats] are not driven onto the Acropolis’ (S000105): *etiam* (3) `advmod:emph`; *Athenis* (4) `obl`. etiam attaches to the constituent it focuses, Athenis, not to the predicate.
- *voltis igitur … usurpemus* ‘do you want us, then, to make use of …’ (S000042): *igitur* (2) `discourse`; *voltis* (1) `root`.
- *itaque prius ostendam* ‘so I shall first show’ (S000034): *itaque* (1) `PART`, `discourse`. The connective particle relates the clause to what precedes and modifies no single word.

### 4.14 Punctuation

#### 4.14.1 `punct`

**Use** [`punct`](https://universaldependencies.org/u/dep/punct.html) for retained punctuation, attached to a content word (under ellipsis, a promoted element may bear it). A token attached by `punct` never has dependents of its own. Attach:

- punctuation separating conjuncts to the following conjunct;
- punctuation before or after a dependent unit to that unit;
- punctuation inside a unit at the highest node that keeps the tree projective;
- both members of paired punctuation (quotation marks, brackets, paired commas or dashes) to the same word, normally the head of the enclosed span, unless that would make the tree non-projective.

**Examples**

- *aqua, terra, anima et sol* ‘water, earth, air and sun’ (S000138): *,* (13) `punct`; *,* (15) `punct`. Each comma attaches to the conjunct that follows it (terra, anima).
- *quod est “Romanus sedendo vincit”* ‘which is “the Roman wins by sitting still”’ (S000042): *“* (9) `punct`; *”* (13) `punct`. Both quotation marks attach to vincit, the head of the enclosed span.
- *otium si essem consecutus, Fundania, commodius tibi haec scriberem* ‘if I had obtained leisure, Fundania, I would write this to you more conveniently’ (S000001): *,* (5) `punct`; *,* (7) `punct`. The comma after consecutus attaches to the conditional clause it closes, and the comma after Fundania to the vocative.

### 4.15 Choosing between relations

Each guide below states a question annotators meet often, the test that answers it, and a pair of examples. Figures for the pairs follow in a later revision.

#### 4.15.1 `obj`, `obl:arg`, or `obl`?

**Test.** Is the nominal a core argument of this predicate, marked by a case that marks core arguments of this verb (normally the accusative)? Then `obj`. Is it oblique, but selected by the predicate, so that its case or adposition is dictated by this verb rather than carrying its own meaning? Then `obl:arg`. Otherwise it is an adjunct: `obl`, or a semantic subtype (`obl:lmod`, `obl:tmod`).

- *commodius tibi haec scriberem* (S000001): *haec* (10) `obj`; *tibi* (9) `obl:arg`, the dative selected by *scribo*.
- *iis igitur deis ad venerationem advocatis* (S000021): *venerationem* (5) `obl`, an adjunct of purpose.

#### 4.15.2 `nmod`, `amod`, or `det`?

**Test.** A nominal dependent of a nominal (a genitive, or a phrase with an adposition) is `nmod`. An adjective is `amod`. A word tagged `DET` is `det` (`det:poss` for a possessive adjective). The part of speech, fixed first (Chapter 2), decides.

- *eius principia* (S000138): *eius* (1) `nmod`, a genitive pronoun.
- *Cassius Dionysius Uticensis* (S000030): *Uticensis* (19) `amod`.
- *non hic Varro noster* (S000154): *hic* (2) `det`; *noster* (4) `det:poss`.

#### 4.15.3 Attribute or secondary predicate?

**Test.** Does the word characterize the nominal (attribute), or state something that holds of it in the situation the clause describes (secondary predicate)? The two agree alike, so form cannot decide. Then check whether the nominal it goes with is overt or elided. The two variables give four cases:

- **Attribute, nominal overt:** the relation the word's part of speech takes as a modifier (`amod`, `acl`, `appos`, `det`), attached to the nominal.
- **Attribute, nominal elided:** the word stands for the nominal and takes that nominal's own relation (`obj`, `nsubj` and so on).
- **Secondary predicate, co-referent overt:** `advcl:pred`, attached to the predicate of the clause, and two Enhanced edges (below).
- **Secondary predicate, co-referent elided:** `advcl:pred`, attached to the predicate of the clause, and no Enhanced edge.

| Part of speech | Attribute, nominal overt | Attribute, nominal elided | Secondary predicate, co-referent overt | Secondary predicate, co-referent elided |
|---|---|---|---|---|
| `ADJ` | *comites incolumes reduxit* ‘he brought the unharmed companions back’: `amod` | *incolumes reduxit* ‘he brought the unharmed back’: `obj` | *comites incolumes reduxit* ‘he brought the companions back unharmed’: `advcl:pred` + Enhanced edges | *incolumes reduxit* ‘he brought them back unharmed’: `advcl:pred` |
| participle (`VERB`) | *aeditumus accersitus ab aedile nondum rediit* ‘the sacristan summoned by the aedile has not returned yet’: `acl` | *accersitus ab aedile nondum rediit* ‘the one summoned by the aedile has not returned yet’: `nsubj` | *aeditumus accersitus ab aedile nondum rediit* ‘the sacristan, having been summoned by the aedile, has not returned yet’: `advcl:pred` + Enhanced edges | *accersitus ab aedile nondum rediit* ‘having been summoned by the aedile, he has not returned yet’: `advcl:pred` |
| `NOUN` | *Cicero consul coniurationem oppressit* ‘the consul Cicero crushed the conspiracy’: `appos` | *consul coniurationem oppressit* ‘the consul crushed the conspiracy’: `nsubj` | *Cicero consul coniurationem oppressit* ‘Cicero, as consul, crushed the conspiracy’: `advcl:pred` + Enhanced edges | *consul coniurationem oppressit* ‘as consul, he crushed the conspiracy’: `advcl:pred` |
| `DET` | *consuli uni hoc licet* ‘this is permitted to the one consul’: `det` | — | *consuli uni hoc licet* ‘this is permitted to the consul alone’: `advcl:pred` + Enhanced edges | — |

The first two rows are adapted from S000154 and S000041; the noun row is a school-grammar example; the determiner row shows that the pattern is not limited to the other three. The same contrast in one phrase: *Cato senex*, ‘old Cato’ (`amod`) against ‘Cato, when old’ (`advcl:pred`).

| | Nominal overt | Nominal elided |
|---|---|---|
| **Attribute** | ![Adapted tree: comites incolumes reduxit with incolumes as amod of comites](figures/adj_attr_overt.svg) | ![Adapted tree: incolumes reduxit with incolumes as obj of reduxit](figures/adj_attr_elided.svg) |
| **Secondary predicate** | ![Corpus tree S000154: comites … incolumes reduxit with incolumes as advcl:pred of reduxit](figures/adj_pred_overt_S000154.svg) | ![Adapted tree: incolumes reduxit with incolumes as advcl:pred of reduxit](figures/adj_pred_elided.svg) |

*Figure 6.* The adjective row of the table as trees. The secondary predicate with overt co-referent (bottom left) is the corpus sentence S000154, as in Figure 2; the other three are adapted from it. Each column has the same words; only the reading, and with it the head of *incolumes*, differs.

**Enhanced layer.** Where the co-referent is overt, add two edges in `DEPS`:

- on the predicative word, a plain `advcl` edge to the predicate of the clause (the `:pred` subtype is not needed once the predication's subject is explicit);
- on the co-referent nominal, an edge from the predicative word, labelled with the role the nominal plays in the secondary predication (`nsubj` in every attested instance).

Where the co-referent is elided, add nothing: the Basic `advcl:pred` edge stands alone.

![Flat view of comites … incolumes reduxit (S000154): Basic obj and advcl:pred arcs above the words, Enhanced nsubj and advcl arcs below](figures/advcl_pred_enhanced_S000154.svg)

*Figure 7.* *comites … incolumes reduxit* (S000154) in the Flat view: the Basic relations above the words, the two Enhanced edges below them. *incolumes* has a plain `advcl` edge from *reduxit*, and *comites* an `nsubj` edge from *incolumes*.

The two corpus cases, with the columns that matter (`DEPS` lists the edges the Enhanced layer adds):

*suos comites ac familiam incolumes reduxit* ‘he brought his companions and household back unharmed’ (S000154, co-referent overt; Figure 2):

| ID | FORM | UPOS | HEAD | DEPREL | DEPS |
|---|---|---|---|---|---|
| 37 | comites | `NOUN` | 41 | `obj` | `40:nsubj` |
| 40 | incolumes | `ADJ` | 41 | `advcl:pred` | `41:advcl` |
| 41 | reduxit | `VERB` | 0 | `root` | `_` |

*accersitus … nondum rediit* ‘having been summoned, he has not yet returned’ (S000041, co-referent elided):

| ID | FORM | UPOS | HEAD | DEPREL | DEPS |
|---|---|---|---|---|---|
| 2 | accersitus | `VERB` | 13 | `advcl:pred` | `_` |
| 13 | rediit | `VERB` | 0 | `root` | `_` |

A third case, a noun with an overt co-referent: *quod initium fructuum oritur* (S000139): *initium* (10) `advcl:pred`, `DEPS` 12:advcl; *quod* (9) `DEPS` 10:nsubj.

#### 4.15.4 `xcomp`, `ccomp`, or `advcl:pred`?

**Test.** Does the predicate require the element (valency)? If not, a predicative element is an adjunct: `advcl:pred`. If it does, does the complement have its own subject (`ccomp`, including the accusative and infinitive), or is its subject obligatorily an argument of the matrix clause (`xcomp`)?

- *C. Licinium Stolonem … video venire* (S000071): *venire* (12) `ccomp`, with its own accusative subject.
- *quem … fructuosum … facere velis* (S000003, Figure 3): *facere* (12) `xcomp` of *velis*, and *fructuosum* (10) `xcomp` of *facere*, whose understood subject is its object *quem*.
- *comites … incolumes reduxit* (S000154, Figure 2): *incolumes* (40) `advcl:pred`; *reduxit comites* is complete without it.

#### 4.15.5 `advcl`, `ccomp`, or `csubj`?

**Test.** Does the clause fill an argument slot of the predicate? If it fills the subject slot, which no nominal fills (typically with an impersonal or passive verb), it is `csubj`; if it fills a complement slot, `ccomp` (or `xcomp`). If it fills no slot and modifies the predicate, it is `advcl`.

- *quem ad modum interfici oporteat* (S000119): *interfici* (6) `csubj` of impersonal *oporteat*.
- *C. Licinium Stolonem … video venire* (S000071): *venire* (12) `ccomp`.
- *otium si essem consecutus* (S000001): *consecutus* (4) `advcl`, a conditional adjunct.

#### 4.15.6 `cop` or `aux:pass`?

**Test.** The two constructions a passive participle can head — a passive process and an ordinary nominal predication with a copula — share an identical surface string, and the choice between `aux:pass` and `cop` turns on what the clause actually asserts, not on the form: “the treaty was signed at the White House” asserts the signing event (`aux:pass`), while “the treaty was signed in red ink” asserts a resulting state of the document (`cop`), with the identical participle and auxiliary form dividing the same way in Latin as in this illustrative English pair. Where the reading turns on whether the participle itself has lexicalized into an adjective, that question is settled at the UPOS layer (Section 2.4) rather than redecided here.

- *omnes domus repletae essent aegrotis* (S000154): *essent* (16) `aux:pass`: the houses were filled, a passive event with its instrument *aegrotis*.

#### 4.15.7 `conj` or `parataxis`?

**Test.** Are the units parallel members of one construction, with or without a conjunction, sharing the same function? Then `conj`. Are they independent units placed side by side, each with its own force, with no conjunction and no shared function? Then `parataxis`.

- *hoc ter noviens cantare iubet, terram tangere, despuere, ieiunum cantare* (S000129): asyndetic `conj`: four infinitives, all complements of *iubet*.
- *ego tui memini, medere meis pedibus* (S000128): *medere* (6) `parataxis`: a statement and an imperative juxtaposed.

#### 4.15.8 Headed or free relative clause?

**Test.** Does the relative clause have an overt antecedent it modifies? Then `acl:relcl`, attached to the antecedent. If not, it is a free relative: attach it by the relation of its role in the matrix clause with the `:relcl` subtype (Section 4.8). In both, the relative word takes the relation of its role inside its own clause.

- *arbor olea, quae primum dicitur ibi nata* (S000105): *dicitur* (22) `acl:relcl`, antecedent *arbor*.
- *qui colunt deorsum, magis aestate laborant* (S000175): *colunt* (2) `csubj:relcl`, no antecedent.

#### 4.15.9 Ellipsis: `orphan`, or `SyntaxNote=Ellipsis`?

**Test.** Does the omission leave a word without a governor whose ordinary relation still holds? Then promote and use `orphan` where needed (Section 4.1.2), with an empty node in the Enhanced layer (Section 5.3). If every surviving word keeps a governor whose relation still holds, change nothing in the tree and mark the omission with `SyntaxNote=Ellipsis` (Section 5.4). The decision is structural: how confidently the missing word can be identified does not matter.

- *quod triticum Apulo?* (S000055): *triticum* (2) `root`; *Apulo* (3) `orphan`; the elided *conferam* is an empty node.
- *hoc nomine etiam Athenis in arcem non inigi* (S000105): *inigi* (8) `root`, `SyntaxNote=Ellipsis`; the verb of saying is understood, but every word keeps its governor.

## 5. Enhanced Syntax

The Enhanced layer (Section 1.2.6) adds to the Basic tree what its single-head format cannot hold. This chapter states what is added before gold and how.

### 5.1 General Enhanced principles

The framework is UD's [Enhanced Dependencies](https://universaldependencies.org/u/overview/enhanced-syntax.html). Until gold, `DEPS` records only accepted structure that differs from the Basic tree, and exactly these three kinds:

1. ellipsis: an empty node where the Basic tree has an `orphan`, with its edges (Sections 5.3, 5.4);
2. secondary predication with an overt co-referent: two edges (Section 5.5);
3. syllepsis: the second role of a form that has two (Section 5.6).

Nothing else is added: not a rejected or provisional reading, and not a construction whose analysis is still open. `nsubj:outer`, `csubj:outer`, and `cop:outer` are Basic relations with no Enhanced counterpart. The full Enhanced graph is completed at gold.

### 5.2 Propagated and shared dependents

A dependent shared by coordinated predicates attaches in the Basic tree to the first conjunct only (Section 4.9). The Enhanced graph can add an edge from it to each further conjunct. This propagation is not yet annotated across the corpus: it is either applied in a corpus-wide pass or completed at gold. Until then, do not add propagation edges; those already present, such as the two in S000089 below, are kept.

**Corpus examples**

- *vilicus … constitutus atque appellatus a villa* ‘the steward [was] appointed … and named after the villa’ (S000089): *vilicus* (1) `nsubj:pass`, `DEPS` 7:nsubj:pass; *appellatus* (7) `conj`. The shared subject attaches in the Basic tree to the first conjunct, constitutus; the Enhanced graph adds its edge to the second conjunct, appellatus.

### 5.3 Empty nodes

Add an empty node only where the Basic tree has an [`orphan`](https://universaldependencies.org/u/dep/orphan.html) (Section 4.1.2), and always add one there. Without an orphan, the omission takes `SyntaxNote=Ellipsis` and no node (Section 5.4).

- `ID`: decimal, placed where the elided word would plausibly stand.
- `DEPS`: the node's own attachment, the relation the elided predicate would have (`9:conj`). Required.
- `FORM`: the elided form where the context makes it clear; `UPOS` may stand in for it. Never filled merely to complete the row.
- `LEMMA`, `XPOS`, `FEATS`, `HEAD`, `DEPREL`: `_`.
- `MISC`: only `InheritedFrom` (Section 5.7) and a review note carried with the node.

The promoted word and each `orphan` then carry an edge back to the node with the relation they have to the elided predicate (*servis* → `17.1:obl:arg`).

**Corpus examples**

- *non solum adimis domino pecus, sed etiam servis peculium* ‘you take away not only the flock from the master, but also [you take away] the savings from the slaves’ (S000096): *adimis* (17.1) `DEPS` 10:conj; *peculium* (17) `DEPS` 17.1:obj; *servis* (16) `orphan`, `DEPS` 17.1:obl:arg. The empty node stands for the elided second adimis; the promoted peculium and the orphaned servis each carry an edge back to it.

### 5.4 Ellipsis

An omission that leaves a dependent without a governor is resolved by promotion and `orphan` (Section 4.1.2) together with an empty node (Section 5.3). `orphan` and `orphan:missing` are Basic relations only.

An omission after which every surviving word keeps a governor whose ordinary relation still holds is marked with `SyntaxNote=Ellipsis` on the word that would govern or be governed by the missing one, and the tree is not changed. The choice between the two is structural: it depends on whether something is left without a governor, not on how certainly the missing word can be identified. A verb repeated word for word from a parallel clause still takes `SyntaxNote=Ellipsis` if nothing is left ungoverned.

The elided word may be named after a colon, in the form it would take in the text: `SyntaxNote=Ellipsis:aram`. Naming is optional; use it where it makes the analysis clearer, and only for a word the context recovers with certainty.

**Corpus examples**

- *hoc nomine etiam Athenis in arcem non inigi* ‘for this reason [they say] that not even at Athens is [a goat] driven onto the citadel’ (S000105): *inigi* (8) `root`, `SyntaxNote=Ellipsis`. The governing verb of saying is carried over from the preceding sentence; every dependent of inigi keeps its governor, so no empty node is added.
- *ad alii dei aram hostia adduceretur, ad alii non sacrificaretur* ‘that a victim should be brought to the altar of one god, at that of another it should not be sacrificed’ (S000101): *alii* (19) `obl:lmod`, `SyntaxNote=Ellipsis:aram`. The second ad alii repeats the construction without aram; the genitive takes the place of the missing noun in the tree, and every word keeps its governor.
- *quo pacto libum* ‘by what method [one ought to make] a libum’ (S000132): *libum* (33) `conj`, `DEPS` 33.1:obj; *pacto* (32) `orphan`, `DEPS` 33.1:obl; *facere* (33.1) `DEPS` 28:conj. Nothing verbal survives in the second question: libum is promoted, pacto is its orphan, and the empty node stands for the elided facere.

### 5.5 Secondary predication

With an overt co-referent, `advcl:pred` adds two edges (Section 4.15.3): on the predicative word, a plain `advcl` edge to the predicate; on the co-referent, an edge from the predicative word with its role (`nsubj`). With the co-referent elided, nothing is added. `advcl:abs` adds nothing: its subject is not an argument of the main clause.

**Corpus examples**

- *quaedam in montanis prolixiora nascuntur* ‘some things grow taller in the mountains’ (S000178): *prolixiora* (4) `advcl:pred`, `DEPS` 5:advcl; *quaedam* (1) `DEPS` 4:nsubj.

### 5.6 Syllepsis

A single overt form that has an accepted second role in another clause gets that role as an Enhanced-only edge, [`obj:syllepsis`](https://universaldependencies.org/u/dep/obj.html) or [`nsubj:syllepsis`](https://universaldependencies.org/u/dep/nsubj.html); its primary role stays in the Basic tree. Nothing is elided. The two subtypes are never Basic relations and are not part of the UD inventory; they are this treebank's own. Every instance carries `SyntaxNote=Syllepsis` and a review note setting out the analysis.

**Corpus examples**

- *quae non inerunt et quaeres* ‘[the things] which will not be included and [which] you will ask about’ (S000022): *quae* (3) `nsubj`, `DEPS` 7:obj:syllepsis, `SyntaxNote=Syllepsis`. quae is the Basic subject of inerunt and, on the Enhanced layer only, the object of quaeres.

### 5.7 `InheritedFrom` metadata

`InheritedFrom=<sent_id>:<token_id>`, usually on an empty node, names the token the elided content is taken from, also within the same sentence. Use it only for a real derivation from an identifiable token that is not repeated on the surface, not for a merely similar construction.

**Corpus examples**

- *quod triticum Apulo?* ‘what wheat [shall I compare] with the Apulian?’ (S000055): *conferam* (2.1) `InheritedFrom=S000054:3`; *triticum* (2) `DEPS` 2.1:obj. The empty node's content derives from conferam in the preceding sentence, which is not repeated here.

## 6. Latin and Varronian Constructions

This chapter gathers the annotation of named Latin constructions, whose parts are spread over the earlier chapters, from the most central to the more specialized.

### 6.1 Ablative absolute

See also Sections 4.7.3 and 4.7.4.

Annotate as `advcl:abs` an ablative nominal with an agreeing predicate (participle, adjective, or noun) forming a predication independent of the main clause. The test is formal; the semantic relation (temporal, causal, concessive) is not recorded. Attach the ablative noun to the absolute predicate as `nsubj`, or `nsubj:pass` with a passive participle, and the predicate to the main predicate as `advcl:abs`. Record a participle's voice as its form shows, also where a passive form has an active sense. If the ablative subject is coreferent with an argument of the main clause, the construction is not absolute: use `advcl:pred`.

![Dependency tree of quibus propitiis … robigo … corrumpit (S000016): corrumpit has propitiis as advcl:abs and robigo as nsubj; quibus is nsubj of propitiis](figures/ablative_absolute_S000016.svg)

*Figure 8.* *quibus propitiis … robigo … corrumpit* ‘when they are propitious, blight does not destroy …’ (S000016). The absolute predicate *propitiis* has its own subject *quibus* (Robigus and Flora), which is not an argument of *corrumpit*, whose subject is *robigo*.

**Corpus examples**

- *quibus propitiis* ‘when they [Robigus and Flora] are propitious’ (S000016, Figure 8): an adjective as the absolute predicate.
- *iis … deis ad venerationem advocatis* ‘with those gods having been invoked for veneration’ (S000021) and *exclusis partibus quae non pertinent ad hanc rem* ‘excluding parts which do not pertain to this matter’ (S000086): participial, with the noun as `nsubj:pass`.

### 6.2 *Participium coniunctum* and secondary predication

See also Sections 4.7.3 and 4.15.3.

A participle used as a secondary predicate is `advcl:pred`, annotated like any other secondary predicate: attached to the predicate of its clause, with the two Enhanced edges when the co-referent is overt, and none when it is elided (Section 4.15.3). Without an overt co-referent: *accersitus … nondum rediit* ‘having been summoned, he has not yet returned’ (S000041).

> [!WARNING]
> **Traditional grammar.** *Participium coniunctum* names only the participial case. A noun or adjective predicates in the same way and takes the same annotation, as *initium* in *quod initium fructuum oritur* ‘which comes up as the beginning of the crop’ (S000139).

Whether secondary predication extends to nominal predication with copula-like verbs such as *fio* and *evado* is an open point (Section 1.3.4).

### 6.3 Accusative and infinitive

See also Section 4.6.

Attach the accusative subject to the infinitive as `nsubj`, never to the matrix verb, and the infinitive to the matrix predicate as `ccomp`, whatever its tense or voice. A control infinitive inside the construction is `xcomp` of its own governor: in *Tarquennam audivi … ei mederi posse* ‘I heard that Tarquenna could heal him’ (S000127), *Tarquennam* is `nsubj` of *posse*, *posse* is `ccomp` of *audivi*, and *mederi* is `xcomp` of *posse*.

**Corpus examples**

- *Agrasius se scire modo putaret* ‘Agrasius thought that only he knew’ (S000118): *se* (14) `nsubj`, `Case=Acc`; *scire* (15) `ccomp`. The accusative subject depends on the infinitive, and the infinitive clause is the ccomp of the matrix verb.

### 6.4 Gerund and gerundive

See also Sections 3.1.2 and 4.2.2.

Both are `VerbForm=Part` with `Aspect=Prosp` and `Voice=Pass`, distinguished by `TraditionalMood` (`Gerundium`, `Gerundivum`); UD's `Ger` and `Gdv` are not used (Section 3.1.2).

**Gerund.** Attach it by its case and construction: a genitive with a noun is `nmod`; with a preposition, `obl` (the preposition `case`); a bare ablative of means or manner, `advcl`. It keeps its own verbal dependents: in *quem bene colendo fructuosum … facere velis* (S000003), *colendo* is `advcl` of *facere*.

**Gerundive.**

- *Gerundive for gerund* (attraction): ordinary relations. Where the noun heads the phrase, the gerundive is its `acl` (*agri colendi causa*, S000089); with *ad*, the gerundive heads the phrase as `advcl` and its noun is `nsubj:pass` (*ad leges accipiendas*, S000073).
- *Passive periphrastic*: *sum*, often omitted, is `aux:pass` of the gerundive (Section 4.2.2); a dative of agent follows Section 4.2.3.
- *Impersonal gerundive*: a neuter singular gerundive with no nominal subject takes `SyntaxNote=ImpersonalGerundive` (S000084 *discernendum*, whose only subject is the *utrum* clause; S000170 *videndum*, which does not agree with the plural *haec quattuor* annotated as its subject). Do not use it for a personal neuter gerundive, a gerund, or attraction.

**Corpus examples**

- *obstrigillandi causa figlinas reprehendis* ‘you criticize the clay pits for the sake of finding fault’ (S000117): *obstrigillandi* (12) `nmod`, `TraditionalMood=Gerundium`. A genitive gerund complementing the noun causa.
- *haec enim cognoscenda* ‘for these things must be learned’ (S000139): *cognoscenda* (3) `root`, `TraditionalMood=Gerundivum`; *haec* (1) `nsubj:pass`. A personal passive periphrastic with its auxiliary omitted: the gerundive agrees with its subject haec, so no SyntaxNote is needed.
- *prius – inquit – discernendum, utrum … ea sola sint in cultura* ‘first, he said, it must be determined whether … those things alone belong to cultivation’ (S000084): *discernendum* (7) `SyntaxNote=ImpersonalGerundive`; *cultura* (19) `csubj:pass`. The impersonal gerundive has no nominal subject and no copula; its only subject is the utrum clause.

### 6.5 Free relative clauses

See also Section 4.8.

Annotate the relative word for its role inside its own clause; the clause takes the `:relcl` subtype of its role in the matrix clause. In *cecinisse quae … prodessent hominibus* ‘prophesied what would benefit people’ (S000005), *prodessent* is `ccomp:relcl` of *cecinisse*; *quae* also has an Enhanced `obj:syllepsis` edge to *cecinisse* (Section 5.6), independently of the free relative.

**Corpus examples**

- *qui de agri cultura scripserunt … latius vagatos* ‘[that those] who have written on agriculture … have wandered too widely’ (S000085): *scripserunt* (8) `csubj:relcl`; *qui* (4) `nsubj`. A free relative filling the subject slot of vagatos; qui is annotated for its role inside its own clause.

### 6.6 Comparison

See also Sections 3.1.4, 4.4.3, and 4.7.2.

Use `obl:cmp` for a bare nominal standard with no *quam* (*ecquam cultiorem Italia vidistis?* ‘have you seen any [land] more cultivated than Italy?’, S000044: *Italia* `obl:cmp`), and `advcl:cmp` for a clausal standard (*priores partes agit quod utile est, quam quod delectat*, S000142: *delectat* `advcl:cmp`). A standard with *quam* whose comparative predicate is elided, leaving only a nominal, is still `advcl:cmp`.

### 6.7 Ellipsis and orphan structures

See also Sections 4.1.2, 5.3, 5.4, and 4.15.9.

**With promotion and an empty node.** In *Iuppiter pater appellatur, Tellus terra mater* ‘Jupiter is called Father, Tellus Mother Earth’ (S000012), the second *appellatur* is elided. *Tellus* (13) is promoted as `conj` of *appellatur*; *mater* (15) cannot be labelled against *Tellus* and takes `orphan`; *terra* (14) keeps its `nmod`. The empty node 15.1 stands for the elided verb (`DEPS` 11:conj); *Tellus* has `DEPS` 15.1:nsubj:pass and *mater* 15.1:xcomp, the relations *Iuppiter* and *pater* have in the first clause.

**Without.** In *hoc nomine etiam Athenis in arcem non inigi* (S000105), a verb of saying is understood from the preceding sentence, but every word keeps its governor: *inigi* is `root`, marked `SyntaxNote=Ellipsis`, and no empty node is added. In *segetes meliores existimantur esse campestres, vineae collinae, silvae montanae* ‘plain grain-crops are reckoned the better ones, hill vineyards, mountain forests’ (S000181), the predicate *meliores* is not repeated in the second and third members, but *vineae* (18) and *silvae* (21) attach to it as `conj` and their adjectives keep their `amod`; nothing is left without a governor, so *vineae* and *silvae* take `SyntaxNote=Ellipsis` and no empty node is added.

Compressed recipe style with a recoverable predicate is ordinary ellipsis, not `Anacoluthon` (Section 6.11).

### 6.8 Reporting expressions and dialogue

See Section 4.12.2.

> **Background.** The *Res rusticae* is a dialogue, so reported speech is structurally central in the corpus. The narrator's frame (`parataxis:reporting`) is kept apart from reported speech within the dialogue (`ccomp:reported`); the relations are defined in Section 4.12.2.

**Corpus examples**

- *Agrasius: vos … ecquam cultiorem Italia vidistis? inquit* ‘Agrasius said: you … have you seen any [land] more cultivated than Italy?’ (S000044): *inquit* (18) `parataxis:reporting`. The reporting verb depends on the root of the reported question.
- *quod scribit, si velis in convivio multum bibere … ante esse oportet brassicam crudam* ‘what he writes: “if you want to drink a lot at a banquet …, you must first eat raw cabbage”’ (S000133): *oportet* (24) `ccomp:reported`. Agrius quotes Cato within the dialogue, so the quotation is governed by *scribit*.

### 6.9 Active and passive supines

See also Section 3.1.2.

The active supine (`VerbForm=Conv`) is `xcomp` of the verb of motion, keeping its own dependents: in *huius spectatum veniant villas* ‘they come to view his villas’ (S000076), *spectatum* is `xcomp` of *veniant* and governs *villas*. The ablative supine is `NOUN` with `VerbForm=Vnoun`, attached as `obl` to the adjective it qualifies (*mirabile dictu*).

### 6.10 Dislocation and prolepsis

The `dislocated` family and its companion `SyntaxNote` values are treated only here.

**Test.** Use `dislocated` only when both hold:

1. a constituent stands at the periphery of the clause (fronted or postposed), outside its core relations;
2. a separate element inside the clause fills the role that constituent would otherwise fill.

If the element inside the clause is instead the head that the peripheral constituent modifies, the construction is adnominal (relative clause, apposition, modifier). Try the ordinary analyses first (adnominal relative, apposition, complement or clausal subject, argument in marked word order); use `dislocated` only when they fail.

**Subtype.** Always use one, naming the type of the dislocated element itself, not the role of its counterpart inside the clause: `dislocated:advcl`, `dislocated:ccomp`, `dislocated:csubj`, `dislocated:nsubj`, `dislocated:obj`, `dislocated:obl`.

> **Background.** In Latin treebanks the family occurs mostly in Late Antique, biblical, and early medieval charter Latin; the largest Latin treebank does not use it at all. Applying it to classical technical prose calls for care in identifying an instance, not for treating the relation as unavailable.

**A boundary case.** At S000041, *nos* stands early, before the subordinate clause that seems to license it, but it is not dislocated: it is the `obj` of *rogaret* in the Basic tree, and its second role, subject of *expectaremus*, is an Enhanced syllepsis edge (Section 5.6). The same token doing a second job is exactly what `dislocated` excludes.

**Related `SyntaxNote` values.**

- `Anastrophe`: word-order inversion that a tree query cannot find reliably (*si* S000001:2, *cum* S000003:11, *quod* S000135:16).
- `Prolepsis`: a detached, anticipatory constituent whose resumption is not recoverable from local dependencies.
- `Prolepsis:Cataphoric`: a demonstrative or similar form anticipating a later catalogue or clause (*hi* at the head of S000024; *ea* at the head of S000035).
- `ClauseDisplaced`: a displaced clause whose displacement the tree and word order do not show, such as a relative clause before its antecedent (S000011, S000024) or a comparative clause fronted next to the word it contrasts (S000177). Subtypes: `ClauseDisplaced:Connective`, a connecting relative; `ClauseDisplaced:Afterthought`, a postposed afterthought, used only once that reading is independently established.
- `RelativeAttraction` belongs with this group but is treated in Section 6.11.

> **Background.** The historical development of prolepsis in Latin, including its concentration in Varro among republican writers, is traced in Halla-aho (2012).

**Corpus examples**

- *utrum quae serantur in agro, ea sola sint in cultura* ‘whether the things which are sown in the field, those alone belong to cultivation’ (S000084): *ea* (15) `SyntaxNote=Prolepsis`, `nsubj`.
- *et aetate et honore et scientia quod praestas* ‘because you excel in age, in honour and in knowledge’ (S000135): *quod* (16) `SyntaxNote=Anastrophe`, `mark`. The subordinator follows the constituents of its own clause instead of opening it.
- *quorum si alterutrum decolat* ‘if either of these fails’ (S000068): *quorum* (1) `SyntaxNote=ClauseDisplaced:Connective`, `nmod`. A connecting relative: quorum links back to the preceding sentence rather than introducing a relative clause.

### 6.11 Retrievable Varronian constructions recorded with `SyntaxNote`

These values add to the Basic and Enhanced analysis; they never replace it.

> **Background.** On Varro's style and language more generally, see Heurgon (1950), Laughton (1960), and Chahoud (2016).

- `LooseAgreement`: agreement following sense or reference rather than the grammatical controller, which could otherwise look like an annotation error (S000015:7 *venit*, S000072:56 *quos*, S000097:1 *quas*).
- `SubjectChange`: an unexpressed subject switch that the overt `nsubj` relations do not show; not merely because coordinated clauses have different overt subjects (S000016:18 *florent*).
- `Anacoluthon`: a constructional break, abandoned plan, incompatible continuation, or missing governor that the tree has to regularize. Not for long periods, ordinary ellipsis (Section 6.7), asyndeton, recipe compression, or word order alone. At S000121:2, *fel*: the recipe opens with *fel bubulum cum aceto mixtum* as if it were the object of a verb of taking and continues with *unguito*, whose object is *lectum*; the tree attaches *fel* to *unguito* as `obl`, since the gall is what the bed is anointed with, which does not record the break.
- `RelativeAttraction`: a relative-clause element whose case is attracted to its antecedent's, which could otherwise be mistaken for an error or a variant (S000139:9 *quod*).
- `PartitiveApposition`: a part-term in apposition to the whole, typically in reversed order (distributive *quisque*; *id genus*, *hoc genus*, *omne genus*). It differs from ordinary apposition (Section 4.5.6) by the part-whole relation and the order.
- `AdnominalPP`: a prepositional phrase modifying a noun directly, with no verbal governor present or recoverable (*in capite apex* ‘the projection at the top’); a recoverable verbal governor takes `SyntaxNote=Ellipsis` instead (Section 6.7).

**Corpus examples**

- *ab his enim cibus et potio venit e fundo* ‘for from these food and drink comes from the farm’ (S000015): *venit* (7) `SyntaxNote=LooseAgreement`, `Number=Sing`; *cibus* (4) `nsubj`. A singular verb with a coordinated subject.
- *neque robigo frumenta atque arbores corrumpit, neque non tempestive florent* ‘neither does blight damage the crops and trees, nor do they fail to flower in season’ (S000016): *florent* (18) `SyntaxNote=SubjectChange`, `conj`. The understood subject of florent is frumenta atque arbores, the object of the preceding clause, not its subject robigo.

## 7. Text, Discourse, and Review Metadata

This chapter covers what surrounds the analysis: the surface text, editorial variants, alternative records, speaker and discourse labels, construction labels, review notes, and review status. All of it is in `MISC` or in sentence-level comment lines (Sections 1.2.1, 1.2.7); none of it is a relation, a part of speech, or a feature.

### 7.1 Accepted text and original form

`text` is the accepted text and `text_old` the transmitted text (Section 1.2.1). `OrigForm` gives a token's transmitted form where the token itself was normalized, for example a capital or a punctuation mark. It comes with the text and is corrected only for a change of proper-noun capitalization or punctuation.

`SpaceAfter=No` (general UD) marks a token not followed by a space; there is no `SpaceAfter=Yes`. [`Lang`](https://universaldependencies.org/foreign.html) gives the language of a token analysed as non-Latin (`Lang=grc` for Greek), always with `Foreign=Yes` (Section 2.6).

**Corpus examples**

- *cum consedissemus, Agrasius: vos …* ‘when we had sat down, Agrasius (said): you …’ (S000044): *cum* (1) `OrigForm=Cum`; *:* (5) `OrigForm=,`; *Agrasius* (4) `SpaceAfter=No`. OrigForm keeps the transmitted capital and the transmitted comma where the accepted text has lower case and a colon; SpaceAfter=No marks that the colon follows Agrasius without a space.
- *… qui inscribuntur φυτῶν ἱστορίας et alteri φυτικῶν αἰτίων.* ‘… which are entitled History of Plants, and others Causes of Plants’ (S000156): *ἱστορίας* (18) `Lang=grc`, `Case=Gen`; *φυτῶν* (17) `nmod`. The Greek book titles are analysed as Greek (Lang=grc) with ordinary relations and features, not left unanalysed as foreign material.

### 7.2 Token-local variants

`Variant=Source:reading` records a reading proposed by an editorial witness and anchored on one accepted token. It is the default device for a variant; Section 7.3 covers what one token cannot carry.

The sources are labels from a fixed list:

- the editions: `Loeb` (the working text, so normally implicit), the Budé editor of the book (`Heurgon`, `Guiraud`), `Goetz2`, `Keil`, `Giusta`, `Flach`, `Walter`;
- the sources cited in the Loeb apparatus: `MSS` (the manuscripts), `EarlyEditions`, `EditioPrinceps`, `Editors` (other editors generally), and named scholars (`Schneider`, `Pontedera`, `Scaliger`, and others).

The reading takes one of these forms:

- a replacement: `Variant=Keil:possem`;
- an omission of the token: a bare hyphen, `Variant=Giusta:-` (`Variant=Loeb:-` where the Loeb text deletes a word the working text keeps);
- an addition: anchored on the token that follows the insertion point, with a trailing `+`, `Variant=Giusta:Prius+`;
- a reading replacing a span of tokens: written once, on one token of the span, with the others marked `Source:CF_<anchor_id>`.

Several witnesses with the same reading are joined by a comma before the colon (`Variant=Heurgon,Keil:atque`); several distinct readings on one token are separated by a semicolon.

**Corpus examples**

- *otium si essem consecutus …* ‘if I had obtained leisure …’ (S000001): *otium* (1) `Variant=Giusta:Prius+`. Giusta proposes inserting Prius before the first word of the sentence; the addition is anchored on the following token, otium.
- *… meque ut id mihi habeam curare roges …* ‘… and (since) you ask me to see to it that I keep this for myself …’ (S000003): *me* (15) `Variant=Giusta:aeque`; *que* (16) `Variant=Giusta:CF_15`. Giusta's single reading aeque replaces the two tokens me and que; the reading is written once, on me, and que points to it.
- *… mente est captus adque adgnatos et gentiles est deducendus.* ‘… he is out of his mind and must be handed over to his agnates and clansmen’ (S000068): *adque* (15) `Variant=Heurgon,Keil:atque`; *adgnatos* (16) `Variant=Giusta,Heurgon,Keil:ad+`. Witnesses with the same reading are joined by a comma; the insertion of ad is anchored on the following token.
- *ut istae, quas dixisti, caprae* ‘as those goats which you mentioned’ (S000099): *dixisti* (14) `Variant=Heurgon,Walter:dixti;MSS:dixi`. Two distinct readings, separated by a semicolon: Heurgon and Walter print dixti, the manuscripts have dixi.

### 7.3 Structural variants

`VariantStructure`, a sentence-level key, records a variant that no single token can carry: an omission of more than a token, a transposition, a move across sentences, a change of punctuation or segmentation, or a different speaker attribution. It names its source and, where possible, the token numbers. Working markers such as `witness_gap` never appear in silver or gold records.

**Corpus examples**

- *an Phrygia magis vitibus cooperta, quam Homerus appellat ἀμπελόεσσαν, quam haec?* ‘or is Phrygia, which Homer calls vine-clad, more covered with vines than this one?’ (S000059): *magis* (3) `advmod`; *vitibus* (4) `obl`; *cooperta* (5) `root`. The sentence header carries VariantStructure = Giusta:transpose_3-5_after_10: Giusta moves magis vitibus cooperta after ἀμπελόεσσαν, a transposition that no single token can carry.
- *multa – inquam – item alia miracula apud Sasernas invenies …* ‘you will find, I said, many other marvels of the same kind in the Sasernas …’ (S000130): *inquam* (3) `Speaker=Varro`, `Variant=Giusta:-`. Giusta assigns the turn to Stolo, recorded in the header as VariantStructure = Giusta:speaker_Stolo; the accompanying omission of inquam is token-local and stays a Variant.

### 7.4 Alternative and revised sentence records

Where a passage admits more than one defensible segmentation or analysis, the alternatives are kept side by side. An alternative record has its own `sent_id` with the prefix `ALT` or `REV`, points to its source with `source_sentence` or `source_sentences`, and, for a resegmentation, has `alt_type = period_segmentation`. Which analysis the release carries is decided at gold.

### 7.5 Speaker attribution

`Speaker` names the speaker of every token; the sentence-level `speaker` key repeats it, and the token value is authoritative if the two differ. The narrative frame of a quoted turn (*inquit Agrius*) has the speaker of the turn and is marked by `DiscourseMode` (Section 7.6). Varro's own turns, framed by *ego … inquam*, have `Speaker=Varro`. Speaker labels come with the text and are corrected only where an overt verb of speaking (*inquam*, *inquit*) shows a turn change that the labels miss.

**Corpus examples**

- *cum consedissemus, Agrasius: vos, qui multas perambulastis terras, … vidistis? inquit.* ‘when we had sat down, Agrasius said: you, who have travelled through many lands, … have you seen …?’ (S000044): *vos* (6) `Speaker=Agrasius`; *Agrasius* (4) `nsubj`; *inquit* (18) `parataxis:reporting`. One speaker holds the whole sentence, so the sentence-level speaker (Agrasius) mirrors the token-level value.
- *multa – inquam – item alia miracula apud Sasernas invenies …* ‘you will find, I said, many other marvels of the same kind in the Sasernas …’ (S000130): *inquam* (3) `Person=1`, `Speaker=Varro`. The first-person verb of speaking marks the turn as Varro's own.

### 7.6 `DiscourseMode`

`DiscourseMode` labels the discourse section of each token:

- `Preface`: Varro's dedication;
- `Dialogue`: the speakers' words, Varro's own turns included;
- `Narrative`: the narrator's frame, including *inquit* or *inquam* outside the dialogue;
- `Lacuna`: the token `…` that stands for a gap in the transmitted text; it keeps the `Speaker` of the passage it interrupts.

It has no sentence-level key, since a sentence may mix dialogue and narrative. Within such a sentence the `Narrative` span identifies the reporting frame (Section 4.12.2). Like `Speaker`, it comes with the text and is corrected only for a missed turn change.

**Corpus examples**

- *Scrofa: prius – inquit – discernendum …* ‘Scrofa said: first it must be determined …’ (S000084): *Scrofa* (1) `DiscourseMode=Narrative`; *inquit* (5) `DiscourseMode=Narrative`, `parataxis:reporting`; *discernendum* (7) `DiscourseMode=Dialogue`. A mixed sentence: the narrative span is the reporting frame around the quoted turn.
- *otium si essem consecutus, Fundania, commodius tibi haec scriberem …* ‘if I had obtained leisure, Fundania, I would write these things to you more suitably …’ (S000001): *otium* (1) `DiscourseMode=Preface`.
- *dicitur aut cretosa … sic ab aliis generum discriminibus mixta* ‘is called either chalky … so, mixed by the other distinctions of kinds’ (S000246): *…* (70) `DiscourseMode=Lacuna`, `Speaker=Scrofa`. The lacuna token keeps the speaker of the passage it interrupts.

### 7.7 `SyntaxNote`

`SyntaxNote` labels a construction that the Basic and Enhanced annotation, or another key, does not make reliably findable. A value is justified for either of two reasons:

- ambiguity resolution: something interpretively important, such as an elided predicate, is missing from the tree without affecting any relation;
- research findability: a Varronian stylistic feature is represented correctly in the tree, but a simple query cannot find it.

Apply a value when a plausible case is noticed, even under some uncertainty: a false positive is filtered out later, a false negative is lost. Use the shortest applicable value. The format is `SyntaxNote=<value>[:<subtype>]`; for `Ellipsis` the part after the colon may instead name the elided word (`Ellipsis:aram`, Section 5.4). Several values on one token are separated by a semicolon (`SyntaxNote=Prolepsis;Syllepsis`).

The values are defined with their constructions: `FixedExpression` in Section 4.11; `ImpersonalGerundive` in Section 6.4; `Ellipsis` and `Syllepsis` in Sections 5.4 and 5.6; `Anastrophe`, `Prolepsis`, `Prolepsis:Cataphoric`, `ClauseDisplaced` and its subtypes, `LooseAgreement`, `SubjectChange`, `Anacoluthon`, `RelativeAttraction`, `PartitiveApposition`, and `AdnominalPP` in Sections 6.10 and 6.11.

**Corpus examples**

- *Scrofa: prius – inquit – discernendum …* ‘Scrofa said: first it must be determined …’ (S000084): *discernendum* (7) `SyntaxNote=ImpersonalGerundive`, `root`. Ambiguity resolution: the gerundive has no overt nominal subject (its subject is the utrum clause), and its impersonal status is not recoverable from the Basic tree alone.
- *otium si essem consecutus …* ‘if I had obtained leisure …’ (S000001): *si* (2) `SyntaxNote=Anastrophe`, `mark`. Research findability: the postponed subordinator is correctly attached in the tree, but its position is hard to query for.

### 7.8 Review notes and tags

A review note gives the reasoning that the annotation does not show: a non-obvious choice, a plausible alternative and the reason against it, a decision that rests on a commentary or an edition, or a genuine alternative reading of the Latin. It does not repeat what the annotation already records, and it never asks a question, raises a doubt about policy or procedure, or records workflow history. The notes are published as `documentation/review_notes.md`.

- **One note, one point, one anchor.** A note belongs to one sentence and is anchored on the token that heads the issue (`ReviewNote=RN_<sent_id>_<NN>`, with `ReviewTags`); a note on a short list of tokens is anchored on the first and names the others. Only a point no token can carry (segmentation, a merge or split, speaker assignment) is anchored on the header (`# review_note`, `# review_tags`).
- **Numbering.** Notes are numbered within the sentence in anchor order, header notes first. Several notes on one token are listed in number order, separated by semicolons, and `ReviewTags` is the union of their topics.
- **Topics**: `Syntax`, `Morphology`, `Lexicon`, `Tokenization`, `Segmentation`, `Enhanced`, `Textual`, `Interpretation`, `Translation`.
- **Status**: `Settled`, or `Open` where the note states a genuine alternative reading that the evidence leaves open, giving both readings.

An alternative or revised record (Section 7.4) has its own note, which refers to the note on the primary sentence.

**Corpus examples**

- *certe – inquit Fundanius – aliut pastio et aliut agri cultura …* ‘certainly, said Fundanius, husbandry is one thing and agriculture another …’ (S000092): *aliut* (6) `ReviewNote=RN_S000092_01;RN_S000092_02`, `ReviewTags=Syntax;Morphology;Textual`. Two notes anchored on one token, listed in number order; the tags are the union of their topics (the first on the predicate analysis, the second on keeping the spelling aliut against Giusta's aliud).
- *… mente est captus adque adgnatos et gentiles est deducendus.* ‘… he is out of his mind and must be handed over to his agnates and clansmen’ (S000068): *adque* (15) `ReviewNote=RN_S000068_01`; *adgnatos* (16) `ReviewNote=RN_S000068_02`, `ReviewTags=Lexicon;Interpretation`. Notes are numbered within the sentence in the order of their anchor tokens.

### 7.9 Review status

`review_status` records how much verification a sentence has had, not which analysis it has.

#### 7.9.1 Review-status values

- No key: the sentence has not entered the pipeline.
- `ore`: an automatically produced baseline (morphology and a Basic tree), made once before review.
- `bronze`: a first pass that adds construction labels, variants, commentary evidence, translations, and Enhanced structure, without adjudicating the analysis; bronze material is never authority for an analysis.
- `silver`: the routine review level: the analysis is adjudicated by a human, text, syntax, and policy compliance are checked, and the reasoning is kept in review notes.
- `gold`: the release level: every validation passes, open notes are closed, and the choice among alternative records is made.

#### 7.9.2 Per-field status metadata

`FieldStatusN` is a temporary per-column marker inherited from earlier work, where N is the column (3 `LEMMA`, 4 `UPOS`, 5 `XPOS`, 6 `FEATS`, 7 `HEAD`, 8 `DEPREL`, 9 `DEPS`). Its values are `p` (raw production or parser value), `q` (flagged as uncertain), `r` (reviewed, or imported from an earlier reference annotation), `s` (accepted at silver), `g` (adjudicated at gold), and `_` (no annotation evidence). It informs ore and bronze; no new values are produced, and it is removed when a sentence is committed at silver, so silver and gold records carry none.

## References

- [Universal Dependencies](https://universaldependencies.org/)
- Bamman, D., & Crane, G. (2006). "The Design and Use of a Latin Dependency Treebank." In J. Hajič & J. Nivre (Eds.), *[Proceedings of the Fifth Workshop on Treebanks and Linguistic Theories (TLT 2006)](https://ufal.mff.cuni.cz/tlt2006/pdf/110.pdf)* (pp. 67–78). Institute of Formal and Applied Linguistics.
- PerseusDL, [Guidelines for the Ancient Greek Dependency Treebank 2.5](https://github.com/PerseusDL/treebank_data/blob/master/AGDT2/guidelines/Greek_guidelines_2.5.md)
- Prague Dependency Treebank, [project overview](https://ufal.mff.cuni.cz/pdt3.0)
- Gamba, F., & Zeman, D. (2023a). ["Universalising Latin Universal Dependencies: A Harmonisation of Latin Treebanks in UD."](https://aclanthology.org/2023.udw-1.2/) *Proceedings of the Sixth Workshop on Universal Dependencies (UDW, GURT/SyntaxFest 2023)*, 7–16.
- Gamba, F., & Zeman, D. (2023b). ["Latin Morphology through the Centuries: Ensuring Consistency for Better Language Processing."](https://aclanthology.org/2023.alp-1.7/) *Proceedings of the Ancient Language Processing Workshop*, 59–67.
- Halla-aho, H. (2012). "A Historical Perspective on Latin Proleptic Accusatives." *De lingua Latina: Revue de Linguistique Latine du Centre Alfred Ernout*, 7.
- Halla-aho, H. (2018). *[Left-Dislocation in Latin: Topics and Syntax in Republican Texts](https://library.oapen.org/handle/20.500.12657/38059)* (Amsterdam Studies in Classical Philology, 28). Brill.
- Heurgon, J. (1950). "L'effort de style de Varron dans les *Res rusticae*." *Revue de Philologie*, 24, 57–78.
- Stassen, L. (1997). *[Intransitive Predication](https://academic.oup.com/book/48571)* (Oxford Studies in Typology and Linguistic Theory). Clarendon Press.
- Laughton, E. (1960). ["Observations on the Style of Varro."](https://www.jstor.org/stable/637584) *The Classical Quarterly*, 10(1), 1–28.
- Chahoud, A. (2016). "Varro's Latin and Varro on Latin." In R. Ferri & A. Zago (Eds.), *[The Latin of the Grammarians: Reflections about Language in the Roman World](https://www.brepols.net/products/IS-9782503566276-1)* (Corpus Christianorum. Lingua Patrum, 8). Brepols.
