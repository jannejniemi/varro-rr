# Varro RR Annotation Guidelines

> **Working pilot version, 20 September 2026.** This document demonstrates the proposed structure and opening chapters of the Varro RR annotation manual. It is not yet an exhaustive or release-authoritative specification.

## Contents

1. [Introduction](#1-introduction)
   1. [Scope of the treebank](#11-scope-of-the-treebank)
   2. [Annotation layers and their CoNLL-U representation](#12-annotation-layers-and-their-conll-u-representation)
   3. [Key concepts](#13-key-concepts)
   4. [Sources of authority](#14-sources-of-authority)
   5. [How to use these guidelines](#15-how-to-use-these-guidelines)
2. [CoNLL-U format and project serialization](#2-conll-u-format-and-project-serialization)
3. [Lemmas and parts of speech](#3-lemmas-and-parts-of-speech)
4. [Morphological features](#4-morphological-features)
5. [Basic syntax](#5-basic-syntax)
6. [Enhanced syntax](#6-enhanced-syntax)
7. [Latin and Varronian constructions](#7-latin-and-varronian-constructions)
8. [Text, variation, and discourse metadata](#8-text-variation-and-discourse-metadata)
9. [Review status and provenance](#9-review-status-and-provenance)

---

## 1. Introduction

### 1.1 Scope of the treebank

The Varro RR treebank provides a morphologically and syntactically annotated representation of Varro's *Res rusticae*. Its primary annotation framework is Universal Dependencies (UD), supplemented by harmonized Latin conventions and a limited set of explicit project decisions required by the text, the research questions, or the review workflow.

The treebank represents more than a sequence of dependency trees. Its CoNLL-U records may also preserve textual normalization, editorial variants, alternative analyses, speaker and discourse information, review notes, workflow status, and selected linguistic observations that cannot be recovered economically from ordinary dependency queries alone.

The purpose of these guidelines is to explain that combined system as a coherent annotation model. They are organized for readers and annotators by linguistic topic. The underlying policy registry, validation catalogue, workflow definitions, and source register remain separate structured resources.

### 1.2 Annotation layers and their CoNLL-U representation

The project distinguishes conceptual annotation layers, but stores them together in CoNLL-U records. A single token row may therefore carry lexical, morphological, Basic-syntactic, Enhanced-syntactic, provenance, and project-specific information.

At a first approximation:

- sentence-level text, identity, status, and provenance are stored in comment lines beginning with `#`;
- tokenization is represented primarily by `ID` and `FORM`;
- lexical analysis is represented primarily by `LEMMA` and `UPOS`;
- morphological analysis is represented primarily by `FEATS`;
- Basic dependency syntax is represented by `HEAD` and `DEPREL`;
- Enhanced dependency syntax is represented by `DEPS`;
- token-level project metadata is represented by `MISC`.

This mapping is introduced here so that the conceptual layers remain connected to the file format throughout the manual. Section 2 gives the full serialization reference.

#### 1.2.1 Text and sentence metadata

Sentence metadata is written as comment lines before the token rows. Typical examples include:

```conllu
# sent_id = S000001
# edition_loc = 1.1.1
# text = otium si essem consecutus, Fundania, ...
# review_status = silver
# speaker = Narrator
```

The internal policy model calls this layer `S.META`. That is a policy category, not a literal CoNLL-U column name. In the file, sentence metadata is serialized as `# key = value` comments.

#### 1.2.2 Tokenization and lexical representation

The first five CoNLL-U fields are:

```text
ID    FORM    LEMMA    UPOS    XPOS
```

`ID` identifies ordinary syntactic words, multiword-token ranges, or decimal-ID empty nodes. `FORM` records the accepted surface token, `LEMMA` its lemma, and `UPOS` its Universal Part-of-Speech category. `XPOS` is not used as an independent project tagset and is normally `_`.

Tokenization decisions are part of the annotation. A change in token boundaries may renumber every later token in the sentence and therefore affects dependency references as well as forms.

#### 1.2.3 Morphological annotation

Morphological features are stored in `FEATS` as alphabetically ordered `Feature=Value` pairs separated by vertical bars:

```conllu
Case=Acc|Gender=Neut|InflClass=IndEurO|Number=Sing
```

Some morphology-related compatibility metadata is stored in `MISC` rather than `FEATS`. In particular, `TraditionalMood` and `TraditionalTense` preserve traditional Latin categories alongside the harmonized UD feature analysis. Their storage location does not make them discourse or review features: `MISC` is a serialization field containing several conceptually different kinds of metadata.

#### 1.2.4 Basic dependency syntax

Basic dependency syntax is stored in:

```text
HEAD    DEPREL
```

Every syntactic-word row has one Basic governor, except that the sentence root is governed by the virtual root node `0`. `HEAD` gives the governor's token ID and `DEPREL` gives the relation between the dependent and that governor.

The Basic layer is a tree. It therefore requires one root and one incoming Basic relation per syntactic word. Where ellipsis or sharing makes the linguistic structure richer than a single tree can express, the Basic layer selects one structural analysis and the Enhanced layer may add further information.

#### 1.2.5 Enhanced dependency syntax

Enhanced dependency syntax is stored in `DEPS`. Unlike the Basic layer, the Enhanced representation may form a graph: a token may have more than one incoming relation, and decimal-ID empty nodes may represent elided predicates or other reconstructed structure where project policy licenses them.

Enhanced syntax does not replace the Basic tree. It adds information that the Basic representation cannot encode without violating its single-head structure.

#### 1.2.6 Project metadata and analytical notes

Token-level project metadata is stored in `MISC`. Important categories include:

- textual history, such as `OrigForm`;
- editorial variation, such as `Variant`;
- speaker and discourse information, such as `Speaker` and `DiscourseMode`;
- references to retained reasoning, such as `ReviewNote` and `ReviewTags`;
- special-construction labels, such as `SyntaxNote`;
- compatibility and provenance information, such as `InheritedFrom`;
- temporary review and workflow markers.

These attributes share a storage field but do not form one linguistic layer. Each is governed by its own definition and lifecycle.

### 1.3 Key concepts

#### 1.3.1 Dependencies, headedness, and flat structures

Dependency annotation represents a construction by identifying a head and attaching its dependents to it with labeled relations. The first question is therefore not which label to choose, but which element organizes the construction syntactically.

A head is not necessarily:

- the first word;
- the finite verb;
- the morphologically richest word;
- the word named first in traditional grammar;
- the word translated by an English verb.

Ordinary dependencies should be used whenever a syntactic head can be identified. A flat structure is appropriate only where no component is an adequate internal head, or where an applicable annotation convention deliberately treats the components as structurally parallel.

In UD relations such as `flat`, `flat:name`, and `flat:foreign`, the first component is used as the technical head by convention. This does not assert that it is semantically more important than the following components. In `flat:gov`, the conventional first-word headedness may even stand in explicit tension with the second element's semantic prominence.

This use of *flat* is specific to UD. It should not be assumed to correspond directly to every Prague-style treatment of coordination, apposition, multiword expressions, or formally headless constructions. Comparisons with PDT-style annotation are explanatory aids, not conversion rules.

**Practical principle:** make every reasonable effort to identify ordinary internal syntax before selecting a flat relation. Apparent unity of meaning, naming function, or idiomaticity is not by itself evidence for flatness.

#### 1.3.2 Predication in dependency grammar

A predicate is the syntactic center of a predication. It is not necessarily a finite verb.

This differs from several traditional uses of *predicate* and *predicative*. Traditional grammar may use *predicate* for everything said about a subject, or may assume that a finite verb heads the clause because it carries person, tense, and mood. It may use *predicative* for several formally similar constructions that dependency grammar must distinguish structurally.

In these guidelines, predicate identification is a head-selection problem. The clause predicate may be:

- a lexical verb;
- an adjective in a nonverbal predication;
- a noun in an identity or classification predication;
- an adverb or adpositional expression functioning as the primary predication;
- a promoted surviving element when the semantic predicate is elided.

Traditional terminology provides useful evidence, but it does not map mechanically to dependency relations. A traditional “predicative” may correspond to a primary nonverbal predicate, a selected predicative complement, an optional secondary predicate, an apposition, or an attributive modifier. The annotation must identify which structure is actually present.

Existential and presentational clauses require particular care. Neither of the following inferences is sufficient:

```text
form of sum → therefore sum is a copula
traditional existential label → therefore sum must be a lexical root
```

The analysis must ask what is being predicated and what contribution *sum* makes in the clause. Depending on the construction, a form of *sum* may be a pure copula, a verbal auxiliary, or a genuine existential or lexical predicate.

#### 1.3.3 Nonverbal predication and the copula

In a pure nonverbal predication, the nonverbal predicate heads the clause. A pure copula is attached to that predicate with `cop`; a verbal copula is tagged `AUX`, not `VERB`.

A simplified example is:

```conllu
1	homo	homo	NOUN	_	Case=Nom|Gender=Masc|Number=Sing	3	nsubj	_	_
2	est	sum	AUX	_	Mood=Ind|Number=Sing|Person=3|Tense=Pres|VerbForm=Fin	3	cop	_	_
3	bulla	bulla	NOUN	_	Case=Nom|Gender=Fem|Number=Sing	0	root	_	_
```

Here:

- `bulla` is the predicate and root;
- `homo` is its subject;
- `est` supports the predication as `cop`;
- the finite copula is not the clause head merely because it carries verbal morphology.

A practical three-way distinction is:

```text
Pure nonverbal predication
    nonverbal predicate is head; sum is AUX with cop

Periphrastic verbal construction
    lexical verbal form is head; sum is AUX with aux or aux:pass

Genuine existential or lexical sum
    sum is the verbal predicate and may be VERB and the clause head
```

This is not a lemma-based classification. The same surface form must be analyzed according to its function in the particular clause.

#### 1.3.4 Secondary predication

Secondary predication adds another predication to a clause without replacing its primary predicate. It commonly expresses a state, role, or circumstance that holds of a participant while the main event or state holds.

The concept is broader than any one dependency relation. The most important distinctions are:

**Optional secondary predication**

An optional secondary predicate is an adjunct. In the project it is typically represented by `advcl:pred`. The clause remains structurally complete without it.

**Selected predicative complement**

A predicate may require or select another predication. Where the understood subject of that complement is obligatorily controlled by a matrix argument, the analysis is typically `xcomp`, not `advcl:pred`.

**Absolute secondary predication**

An ablative absolute brings its own subject and is represented by `advcl:abs`. Its independence from the main clause's arguments distinguishes it from ordinary secondary predication.

**Attributive or identifying modification**

An adjective, participle, or noun may characterize or identify a nominal rather than assert a circumstance holding of it in the clause. Such structures take relations such as `amod`, `acl`, or `appos`, depending on their form and function.

The morphology of attributive and secondary-predicative expressions may be identical. The distinction therefore cannot be read off agreement alone. The annotator must determine whether the expression characterizes the nominal or contributes an additional predication to the clause.

#### 1.3.5 Arguments, complements, and adjuncts

A predicate's arguments are participants or propositions selected by its lexical or constructional requirements. Adjuncts add optional circumstances such as time, place, manner, cause, or condition.

This distinction underlies several important relation choices:

- `obj` versus `obl`;
- `obl:arg` versus plain `obl`;
- `ccomp` or `xcomp` versus `advcl`;
- `xcomp` versus `advcl:pred`;
- selected locatives versus ordinary locative modifiers.

Morphological case and semantic plausibility do not settle argument status on their own. The analysis must consider the governor's valency and whether the dependent is required or selected in that construction.

#### 1.3.6 Overt, omitted, and reconstructed structure

Latin frequently leaves material unexpressed. Dependency annotation must distinguish several different situations:

- an ordinary null subject recoverable from verbal morphology;
- an omitted copula that does not require structural reconstruction;
- an ellipsis that leaves all surviving elements with ordinary governors;
- head ellipsis that strands dependents and requires promotion with `orphan`;
- an Enhanced reconstruction that licenses a decimal-ID empty node;
- a physical gap in the transmitted text.

Not every understood element is represented by an empty node. Not every clause without an overt finite verb contains an ellipsis that the tree must reconstruct. The deciding question is what structure the annotation needs in order to represent the surviving relations without distortion.

A promoted element under ellipsis may become the Basic root even though it is not the semantic predicate. This is a structural repair required by the tree format, not a claim that the promoted word has become a lexical predicate.

#### 1.3.7 Annotation criteria and illustrative examples

Definitions and stated criteria determine what an annotation category licenses. Examples illustrate those criteria but do not define their limits.

Accordingly:

- the absence of a construction from the examples does not make it unlicensed;
- the presence of several examples does not turn them into a closed inventory;
- corpus frequency does not determine grammatical availability;
- current non-attestation may reflect the reviewed range rather than the language;
- a rule should remain interpretable if every example is removed.

Examples should follow the governing criterion, not precede it. Where a case remains uncertain, the uncertainty should be recorded explicitly rather than concealed by treating a precedent as an automatic answer.

### 1.4 Sources of authority

The project distinguishes four kinds of authority:

1. **General Universal Dependencies**, governing the cross-linguistic framework and the CoNLL-U format.
2. **Latin Universal Dependencies**, governing Latin-specific features, relations, and documented conventions.
3. **Harmonized Latin annotation**, used where a shared Latin-treebank convention has been adopted across relevant resources.
4. **Project-specific decisions**, used only where the project deliberately chooses or defines a convention not settled by the preceding levels.

Project-specific policy does not silently override UD. Deliberate deviations must be stated as such, scoped narrowly, and given a rationale. Parser output, corpus frequency, and precedent are evidence rather than authority.

When sources appear to conflict, the operative project guideline states which source governs the case. The source register and internal policy register preserve the supporting references and decision history.

### 1.5 How to use these guidelines

The documentation has two complementary forms:

- this manual gives a reader-oriented explanation organized by linguistic topic;
- the internal policy register gives the complete row-level inventory, exact controlled values, authority, applicability restrictions, cross-references, and validation links.

A reader should normally begin here. Maintainers, validators, and review agents may then follow internal references to the policy and rule registers.

The main public exposition avoids internal identifiers where they do not help comprehension. Private documentation may retain identifiers such as policy, rule, workflow, and validation IDs for traceability.

---

## 2. CoNLL-U Format and Project Serialization

> **Pilot placeholder.** This section will expand the preview in Section 1.2 into a complete field-by-field reference, including sentence comments, ordinary token rows, multiword tokens, decimal-ID empty nodes, ordering conventions, and project-specific metadata serialization.

Planned subsections:

- sentence records and blank-line separation;
- the ten CoNLL-U columns;
- ordinary syntactic-word rows;
- multiword-token rows;
- empty-node rows;
- `FEATS`, `DEPS`, and `MISC` serialization;
- sentence metadata keys;
- file-level consistency requirements.

## 3. Lemmas and Parts of Speech

> **Pilot placeholder.** This section will explain lemma policy and each UPOS category in a linguistically meaningful order, with special attention to Latin boundary decisions.

Planned subsections:

- general lemma and UPOS principles;
- `ADJ`, `ADP`, `ADV`, `AUX`, `CCONJ`, `DET`, `INTJ`, `NOUN`, `NUM`, `PART`, `PRON`, `PROPN`, `PUNCT`, `SCONJ`, `VERB`, and `X`;
- the `DET` / `PRON` boundary;
- lexicalized participles and the `ADJ` / `VERB` boundary;
- copular and auxiliary uses of *sum*;
- foreign, corrupt, and unanalyzed material.

## 4. Morphological Features

> **Pilot placeholder.** This section will group feature values by grammatical category rather than reproducing the policy-register row order.

Planned subsections:

- case, gender, and number;
- `InflClass` and `InflClass[nominal]`;
- degree;
- aspect, mood, tense, voice, and verb form;
- person and possessor features;
- pronoun and numeral features;
- name type, variant, form, polarity, and related lexical features;
- `TraditionalMood` and `TraditionalTense`.

## 5. Basic Syntax

> **Pilot placeholder.** This section will describe ordinary Basic dependency analysis and relation families, beginning with predicate and root identification.

Planned subsections:

- predicates and roots;
- subjects;
- objects and oblique arguments;
- nominal modification;
- clausal complements;
- adverbial clauses;
- relative clauses;
- coordination;
- copulas and auxiliaries;
- apposition, fixed expressions, and flat structures;
- parataxis and reporting clauses;
- discourse elements;
- punctuation.

## 6. Enhanced Syntax

> **Pilot placeholder.** This section will distinguish additions to the Enhanced graph from alternative Basic analyses.

Planned subsections:

- general Enhanced principles;
- propagated and shared dependents;
- empty nodes;
- ellipsis;
- secondary predication;
- syllepsis;
- `InheritedFrom` metadata;
- Basic-compatible derivative files and round-tripping.

## 7. Latin and Varronian Constructions

> **Pilot placeholder.** This section will bring together rules that are distributed across UPOS, FEATS, relations, Enhanced syntax, metadata, and validation in the internal registers.

Planned subsections:

- ablative absolute;
- *participium coniunctum* and secondary predication;
- gerund and gerundive;
- active and passive supines;
- accusative and infinitive;
- free relative clauses;
- comparison;
- dislocation and prolepsis;
- ellipsis and orphan structures;
- reporting expressions and dialogue;
- retrievable Varronian constructions recorded with `SyntaxNote`.

## 8. Text, Variation, and Discourse Metadata

> **Pilot placeholder.** This section will explain how the accepted annotation is kept distinct from textual witnesses, alternatives, and retained reasoning.

Planned subsections:

- accepted text and original form;
- token-local variants;
- structural variants;
- alternative and revised sentence records;
- speaker attribution;
- `DiscourseMode`;
- review notes and tags;
- `SyntaxNote`.

## 9. Review Status and Provenance

> **Pilot placeholder.** This section will explain status values as data provenance rather than annotation labels.

Planned subsections:

- material not yet admitted to the pipeline;
- ORE as a one-time technical baseline stage;
- bronze, silver, and gold review levels;
- per-field status metadata;
- elevation from bronze to silver;
- unresolved findings;
- diagnostic ORE, bronze, and silver corpora.

---

## References for the pilot structure

- Universal Dependencies, [CoNLL-U Format](https://universaldependencies.org/format.html)
- Universal Dependencies, [`cop`: copula](https://universaldependencies.org/u/dep/cop.html)
- Universal Dependencies, [`flat`: flat multiword expression](https://universaldependencies.org/u/dep/flat.html)
- Universal Dependencies, [Enhanced Dependencies](https://universaldependencies.org/u/overview/enhanced-syntax.html)
- PerseusDL, [Guidelines for the Ancient Greek Dependency Treebank 2.5](https://github.com/PerseusDL/treebank_data/blob/master/AGDT2/guidelines/Greek_guidelines_2.5.md)
- Prague Dependency Treebank, [project overview](https://ufal.mff.cuni.cz/pdt3.0)
