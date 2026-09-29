# Review Notes

Review Notes record reasoning that cannot be read off the annotation itself: non-obvious interpretive choices, rejected plausible alternatives, readings that depend on the commentaries, and open questions. They do not describe the annotation, which the trees show, or how the annotation was produced.

Each note belongs to one sentence of `corpus/RR_reviewed.conllu` and is referenced from one place in it: from a token, in MISC as `ReviewNote=<NoteID>` (with `ReviewTags=` giving its topics), or, when no single token can carry the point, from the sentence header as `# review_note = <NoteID>`. Notes are numbered within their sentence in the order of their anchors. A note whose text is only another NoteID repeats that note for a parallel analysis of the same passage (ALT/REV records).

Topics: Syntax, Morphology, Lexicon, Tokenization, Segmentation, Enhanced, Textual, Interpretation, Translation. Status is Settled, or Open for a question the annotation leaves open.

This file is generated from the project workbook; do not edit it by hand.

## S000002 (1.1.1)

> annus enim octogesimus admonet me ut sarcinas conligam, antequam proficiscar e vita.

<a id="rn_s000002_01"></a>
**RN_S000002_01** · conligam (8) · Interpretation

sarcinas conligam (7-8) is a figurative military idiom, 'pack up one's kit, break camp', here applied to Varro's approaching death (antequam proficiscar e vita), not literal packing of baggage.

Heurgon ad loc. identifies sarcinas colligere as a military expression used figuratively and cites the parallel collige sarcinulas, Juv. 6.146.

<sub>Tokens: sarcinas (7), conligam (8) · Sources: Heurgon, commentary</sub>

## S000003 (1.1.2)

> quare, quoniam emisti fundum, quem bene colendo fructuosum cum facere velis, meque ut id mihi habeam curare roges, experiar;

<a id="rn_s000003_01"></a>
**RN_S000003_01** · quare (1) · Syntax

quare (1) and quoniam (3) both introduce the same causal relation, so one of them is redundant; this is the anacoluthon marked on quare. The tree keeps quare as advmod of experiar (24) and quoniam as mark of emisti (4) without normalising the redundancy.

Laughton (1960: 21) quotes this sentence as his main example of a peculiar type of anacoluthon in Varro in which both a causal conjunction and a relative pronoun are used where one or the other is out of place; quare is itself a relative-causal adverb (qua re).

<sub>Tokens: quare (1), quoniam (3) · Sources: Laughton 1960, Observations on the Style of Varro</sub>

## S000004 (1.1.2)

> et non solum, ut ipse quoad vivam, quid fieri oporteat ut te moneam, sed etiam post mortem.

<a id="rn_s000004_01"></a>
**RN_S000004_01** · ut (5) · Syntax · **Open**

How is ut (5) to be construed? The tree takes it, tagged Anastrophe, as a second subordinator of vivam (8) beside quoad (7), although the following te moneam has its own ut (13); the passage is a test case for postponed subordinators in Varro.

<sub>Tokens: ut (5), quoad (7), ut (13) · Sources: Laughton 1960, Observations on the Style of Varro; Rodgers 2015; Giusta, apparatus and notes</sub>

## S000005 (1.1.3)

> neque patiar Sibyllam non solum cecinisse quae, dum viveret, prodessent hominibus, sed etiam quae cum perisset ipsa, et id etiam ignotissimis quoque hominibus;

<a id="rn_s000005_01"></a>
**RN_S000005_01** · quae (7) · Syntax;Interpretation · **Open**

quae (7), neuter plural and so ambiguous between nominative and accusative, is both subject of prodessent (12) and understood object of cecinisse (6). Open: is it primarily subject, with the free relative quae ... prodessent as the clausal object of cecinisse (S000005, REV000005), or primarily object of cecinisse with prodessent as a clause on it (ALT000005)?

Niemi (case-syncretic sharing) calls the first reading subject-primary and finds it coherent, though it reverses the usual direction of the Latin proleptic accusative, but prefers object-primary as more economical for the whole sentence, since quae (17) can then continue an ordinary coordinated object series without a second elided prodessent, while stating that the passage does not decide between sharing and ellipsis. For the structure, the UD pattern for free relatives attaches the embedded predicate to the matrix verb (cf. English I know what you did) whichever role is semantically salient. Pinkster (2012) supports this for Latin: autonomous relative clauses fill argument slots directly (his ex. 9, 11), and in ex. 16 (B. Afr. 96.2, cum quos paulo ante nominavi) the pronoun's case follows only its internal role. So quae need not carry cecinisse's case, which favours the S000005/REV000005 tree; the interpretive question remains open.

<sub>Tokens: quae (7), prodessent (12) · Sources: Niemi, Case-Syncretic Sharing in Varro’s Language; Pinkster 2012 · See also: [RN_ALT000005_01](#rn_alt000005_01), [RN_S000005_02](#rn_s000005_02), [RN_REV000005_02](#rn_rev000005_02)</sub>

<a id="rn_s000005_02"></a>
**RN_S000005_02** · quae (17) · Syntax

The second quae (17) needs its own elided prodessent (17.1): dum viveret and cum perisset ipsa are temporally exclusive circumstances, so the two relative clauses cannot share one occurrence of the verb.

ALT000005 avoids this empty node by attaching cum perisset ipsa directly to quae (17) as a clausal modifier.

<sub>Tokens: quae (17), prodessent (17.1), perisset (19) · Sources: Niemi, Case-Syncretic Sharing in Varro’s Language · See also: [RN_S000005_01](#rn_s000005_01), [RN_ALT000005_01](#rn_alt000005_01)</sub>

<a id="rn_s000005_03"></a>
**RN_S000005_03** · quoque (26) · Syntax

quoque (26) and etiam (16, 24) attach directly to the word they focus (quoque to hominibus, etiam to quae and id), without an elided predicate as governor; quoque is labelled discourse, etiam advmod:emph.

Rejected alternatives: (a) treating them as adverbs that must attach to a predicate, which here would require an extra empty predicate node; (b) treating quoque, following its dictionary classification as a conjunction, as cc of the word it emphasises. Direct attachment is licensed by the UD advmod guidelines, which allow a limited set of focus adverbs to modify nominals (only on Monday, advmod:emph).

<sub>Tokens: etiam (16), etiam (24), quoque (26) · Sources: Universal Dependencies general guidelines</sub>

## ALT000005 (1.1.3)

> neque patiar Sibyllam non solum cecinisse quae, dum viveret, prodessent hominibus, sed etiam quae cum perisset ipsa, et id etiam ignotissimis quoque hominibus;

<a id="rn_alt000005_01"></a>
**RN_ALT000005_01** · quae (7) · Syntax;Interpretation

ALT000005 reads both quae (7, 17) as proleptic objects of cecinisse, with the prodessent and perisset clauses attached to them and supplying the content of the prophecy.

This follows the traditional-grammar gloss of the object-primary reading. In UD terms it is the strategy that treats a headless relative pronoun as an NP argument with the clause on it; it is not the necessary encoding of the object-primary reading, which is also compatible with attaching prodessent to cecinisse by ccomp as in S000005.

<sub>Tokens: quae (7), quae (17) · Sources: Niemi, Case-Syncretic Sharing in Varro’s Language · See also: [RN_S000005_01](#rn_s000005_01)</sub>

<a id="rn_alt000005_02"></a>
**RN_ALT000005_02** · quoque (26) · Syntax

Same as [RN_S000005_03](#rn_s000005_03).

## REV000005 (1.1.3)

> neque patiar Sibyllam non solum cecinisse quae, dum viveret, prodessent hominibus, sed etiam quae cum perisset ipsa, et id etiam ignotissimis quoque hominibus;

<a id="rn_rev000005_01"></a>
**RN_REV000005_01** · quae (17) · Syntax

Same as [RN_S000005_02](#rn_s000005_02).

<a id="rn_rev000005_02"></a>
**RN_REV000005_02** · id (23) · Syntax · **Open**

In the transmitted text, et id (22-23) is read as a resumptive pronoun picking up the coordinated relative clauses, not as the subject of a further clause with an elided prodesset; id attaches to quae (7), the first conjunct, so that it covers both branches of the prophecy. Open: whether et id is this resumptive use at all.

Pinkster (2012, sect. 4) shows is/id following an autonomous relative clause as a resumptive pronoun coreferential with the whole clause and governing no verb (his ex. 24, 27), and rejects analysing such pronouns as heads with the relative clause as attribute. Looser support: Cic. Verr. 2.4.64 id adeo; Allen & Greenough's accusative in apposition to a clause, a pattern they call characteristic of later writers. No parallel was found for et id in exactly this sense, and Hofmann-Szantyr and Kuhner-Stegmann were not consulted. Attaching id to quae (17) would limit it to the posthumous branch; the scope matches hominibus (27) as conj of hominibus (13). Giusta's deletion of et id (S000005, ALT000005) is an independent textual alternative.

<sub>Tokens: quae (7), et (22), id (23) · Sources: Pinkster 2012; Allen & Greenough (idiomatic accusatives) · See also: [RN_S000005_01](#rn_s000005_01), [RN_REV000005_04](#rn_rev000005_04)</sub>

<a id="rn_rev000005_03"></a>
**RN_REV000005_03** · quoque (26) · Syntax

Same as [RN_S000005_03](#rn_s000005_03).

<a id="rn_rev000005_04"></a>
**RN_REV000005_04** · hominibus (27) · Syntax

ignotissimis quoque hominibus (25-27) is a coordinate expansion of hominibus (13), not an oblique of the elided posthumous predicate (17.1): the widening of the beneficiaries to unknown people applies to both branches of the prophecy, and tying it to 17.1 would over-specify the Latin.

<sub>Tokens: hominibus (13), ignotissimis (25), hominibus (27) · See also: [RN_REV000005_02](#rn_rev000005_02)</sub>

## S000007 (1.1.3)

> me, ne dum vivo quidem, necessariis meis quod prosit facere.

<a id="rn_s000007_01"></a>
**RN_S000007_01** · necessariis (8) · Morphology;Lexicon

necessariis (8) is the substantivised necessarii, 'relatives, close connections', and is therefore tagged NOUN rather than ADJ.

## S000010 (1.1.4)

> neque tamen eos urbanos, quorum imagines ad forum auratae stant, sex mares et feminae totidem, sed illos XII deos, qui maxime agricolarum duces sunt.

<a id="rn_s000010_01"></a>
**RN_S000010_01** · mares (14) · Syntax · **Open**

sex mares et feminae totidem (13-17) is nominative, although it is in apposition to accusative eos urbanos (3-4). Open: is this loose agreement (a parenthetic nominative) or should another analysis be preferred?

<sub>Tokens: sex (13), mares (14), feminae (16), totidem (17)</sub>

## S000011 (1.1.5)

> primum, qui omnis fructos agri culturae caelo et terra continent, Iovem et Tellurem;

<a id="rn_s000011_01"></a>
**RN_S000011_01** · fructos (5) · Morphology;Textual

fructos (5) is kept as a possible deliberate archaism for the regular accusative plural fructus, not treated as a corruption.

Giusta (I 1,5) counts fructus as the regular form (18 occurrences) and fructos here, at 1.2.5 (in a Pacuvius quotation) and at II 5,7. He regards fructos as usually a scribal trivialisation, but since the form is otherwise found only in archaic (Pacuvius) or late writers it may be a genuine archaism; he retains it at 1.2.5 and leaves this passage open. No edition consulted (Henderson, Heurgon) reads otherwise here.

<sub>Sources: Giusta, apparatus and notes; Heurgon, Latin text</sub>

<a id="rn_s000011_02"></a>
**RN_S000011_02** · continent (11) · Lexicon

continent (11) means 'embrace, encompass': Jupiter and Tellus hold all the fruits of agriculture within heaven and earth.

<sub>Sources: Heurgon, commentary; Deschamps</sub>

## ALT000011_12 (1.1.5)

> primum, qui omnis fructos agri culturae caelo et terra continent, Iovem et Tellurem; itaque, quod ii parentes magni dicuntur, Iuppiter pater appellatur, Tellus terra mater.

<a id="rn_alt000011_12_01"></a>
**RN_ALT000011_12_01** · sentence · Syntax;Segmentation

ALT000011_12 joins S000011 and S000012 across the semicolon, treated as a weak boundary: quod ii parentes magni dicuntur (23) and Iuppiter pater appellatur, Tellus terra mater (27) are read as explanatory continuations of the relative clause qui ... continent (11).

itaque (17) belongs to appellatur. quod is not smoothed into a causal connective, and the translation keeps some of the syntactic roughness of the period, which is also marked as anacoluthon on dicuntur and appellatur.

<sub>Tokens: continent (11), dicuntur (23), appellatur (27)</sub>

## S000016 (1.1.6)

> quarto Robigum ac Floram, quibus propitiis neque robigo frumenta atque arbores corrumpit, neque non tempestive florent.

<a id="rn_s000016_01"></a>
**RN_S000016_01** · florent (18) · Syntax

florent (18) has no overt subject; its understood subject is frumenta atque arbores (10, 12), the object of the preceding clause, not its subject robigo (9). The plural verb can only be predicated of the crops and trees.

<sub>Tokens: frumenta (10), arbores (12), florent (18)</sub>

## S000017 (1.1.6)

> itaque publice Robigo feriae Robigalia, Florae ludi Floralia instituti.

<a id="rn_s000017_01"></a>
**RN_S000017_01** · institutae (5.1) · Syntax

instituti (10) agrees only with its own subject ludi (8); for the first member, Robigo feriae Robigalia, the gapped predicate is recovered as feminine institutae (5.1) agreeing with feriae (4). The gender difference between the two members is thus handled by ellipsis rather than treated as loose agreement.

<sub>Tokens: feriae (4), institutae (5.1), instituti (10)</sub>

## S000020 (1.1.6)

> nec non etiam precor Lympham ac Bonum Eventum, quoniam sine aqua omnis arida ac misera agri cultura, sine successu ac bono eventu frustratio est, non cultura.

<a id="rn_s000020_01"></a>
**RN_S000020_01** · Lympham (5) · Lexicon;Interpretation

Lympham (5) is a singular personified water deity, 'the Nymph'; the name is otherwise attested only in the plural (Lymphae, Nymphae).

Heurgon ad loc. treats the singular as another of Varro's own constructions, like the rustic Di Consentes of 1.1.4.

<sub>Sources: Heurgon, commentary</sub>

<a id="rn_s000020_02"></a>
**RN_S000020_02** · eventu (24) · Interpretation

bono eventu (23-24) is the common noun phrase 'good outcome', not the deity name, though it deliberately echoes Bonum Eventum (7-8): the quoniam clause justifies each invocation by what the deity stands for (aqua for Lympha, bonus eventus for Bonus Eventus).

<sub>Tokens: Bonum (7), Eventum (8), bono (23), eventu (24) · Sources: Heurgon, commentary; Giusta, apparatus and notes</sub>

## S000022 (1.1.7)

> in quis quae non inerunt et quaeres, indicabo a quibus scriptoribus repetas et Graecis et nostris.

<a id="rn_s000022_01"></a>
**RN_S000022_01** · quis (2) · Syntax;Interpretation

in quis (1-2) is read as neuter plural ablative (= in quibus, 'in those matters'), and quae (3) as nominative subject of inerunt (5), with quaeres (7) coordinated with inerunt; quae is also understood as the object of quaeres.

<sub>Tokens: quis (2), quae (3), inerunt (5), quaeres (7) · See also: [RN_S000005_01](#rn_s000005_01)</sub>

## S000024 (1.1.8)

> hi sunt, quos tu habere in consilio poteris, cum quid consulere voles, Hieron Siculus et Attalus Philometor;

<a id="rn_s000024_01"></a>
**RN_S000024_01** · hi (1) · Syntax;Segmentation

hi (1), defined by the relative clause quos tu habere in consilio poteris, is the predicate (root with cop sunt); Hieron and Attalus (16, 19) are the subject. The cataphoric category term is the predicate, as in auctores sunt Hieron et Attalus.

The same catalogue frame continues across the following semicolon-separated segments (S000025-S000027).

<sub>Tokens: hi (1), poteris (9), Hieron (16), Attalus (19)</sub>

## S000025 (1.1.8)

> de philosophis Democritus physicus, Xenophon Socraticus, Aristoteles et Theophrastus peripatetici, Archytas Pythagoreus;

<a id="rn_s000025_01"></a>
**RN_S000025_01** · philosophis (2) · Syntax;Segmentation

de philosophis (1-2) is the predicate of the catalogue segment ('among the philosophers [are]'), and Democritus (3) with the following names is the nominative subject list; philosophis heads the PP and is the root although ablative.

No empty node is needed because the predicate is overt as a PP, though no copula is present. Contrast S000026, whose segment inherits the predicate hi from S000024.

<sub>Tokens: de (1), philosophis (2), Democritus (3) · See also: [RN_S000024_01](#rn_s000024_01)</sub>

## S000027 (1.1.9)

> de reliquis, quorum quae fuerit patria non accepi, sunt Androtion, Aeschrion, Aristomenes, Athenagoras, Crates, Dadis, Dionysios, Euphiton, Euphorion, Eubulus, Lysimachus, Mnaseas, Menestratus, Plentiphanes, Persis, Theophilus.

<a id="rn_s000027_01"></a>
**RN_S000027_01** · reliquis (2) · Syntax

de reliquis (1-2) is the predicate, with sunt (11) as copula and Androtion (12) and the following names as the nominative subject list; reliquis heads the PP and is the root although ablative.

The relative clause quorum quae fuerit patria non accepi modifies reliquis, with the indirect question quae patria fuerit as ccomp of accepi.

<sub>Tokens: de (1), reliquis (2), sunt (11), Androtion (12) · See also: [RN_S000025_01](#rn_s000025_01)</sub>

## S000028_S000029 (1.1.9)

> hi quos dixi omnes soluta oratione scripserunt; easdem res etiam quidam versibus, ut Hesiodus Ascraeus, Menecrates Ephesius.

<a id="rn_s000028_s000029_01"></a>
**RN_S000028_S000029_01** · sentence · Syntax;Segmentation

The two semicolon-separated segments form one sentence because the second (easdem res etiam quidam versibus ...) has no finite verb of its own and inherits scripserunt (7) from the first.

This differs from S000025 and S000027, where an overt PP predicate heads the segment.

<sub>Tokens: scripserunt (7), quidam (12), scripserunt (12.1) · Sources: Heurgon, Latin text</sub>

## S000033 (1.1.11)

> quo brevius de ea re conor tribus libris exponere, uno de agri cultura, altero de re pecuaria, tertio de villaticis pastionibus, hoc libro circumcisis rebus, quae non arbitror pertinere ad agri culturam.

<a id="rn_s000033_01"></a>
**RN_S000033_01** · quae (31) · Morphology

quae (31) is neuter although its antecedent rebus (29) is feminine: Varro's colloquial register lets res drift to neuter agreement in this construction.

Heurgon ad loc., citing Laughton (1960: 15), with parallels elsewhere in the text.

<sub>Tokens: rebus (29), quae (31) · Sources: Heurgon, commentary; Laughton 1960, Observations on the Style of Varro</sub>

## S000038 (1.2.1)

> quid vos hic? inquam, num feriae sementivae otiosos huc adduxerunt, ut patres et avos solebant nostros?

<a id="rn_s000038_01"></a>
**RN_S000038_01** · sentence · Syntax;Segmentation

A sentence split after inquam (at 6) would be plausible, since quid vos hic? and num feriae sementivae ... are two separate questions in direct speech; it is not made because vos (2) is shared: subject of the elided facitis and object of adduxerunt (12), with otiosos (10) predicated of it.

<sub>Tokens: vos (2), , (6), adduxerunt (12)</sub>

<a id="rn_s000038_02"></a>
**RN_S000038_02** · otiosos (10) · Syntax;Interpretation

otiosos (10) is a contextual secondary predicate of vos (2), 'at leisure on the holiday', not an inherent description of the interlocutors, whom Varro addresses as respectable men: the Sementivae have brought them here in a state of holiday leisure.

The predication depends on vos doing double duty (subject of the elided facitis, object of adduxerunt); the shared form is vos, so Syllepsis is marked there and not on otiosos.

<sub>Tokens: vos (2), otiosos (10), adduxerunt (12) · See also: [RN_S000038_01](#rn_s000038_01)</sub>

## S000041 (1.2.2)

> nam accersitus ab aedile, cuius procuratio huius templi est, nondum rediit et nos uti expectaremus se reliquit qui rogaret.

<a id="rn_s000041_01"></a>
**RN_S000041_01** · nos (15) · Syntax

nos (15) is primarily the object of rogaret (21), since rogare aliquem ut ... needs an accusative addressee and nos is the only candidate; its reading as subject of expectaremus (17) is weak, because the verb needs no overt subject.

Laughton (1960: 9) cites the sentence as a subordinate clause (uti expectaremus) preposed before its whole governing phrase. It is not left-dislocation or attractio inversa in Halla-aho's (2018) sense: nos is not extra-clausal, and its second role is never resumed; her Varro chapter (5.4) has nothing structurally like it. The processing effect, nos first read as subject of expectaremus and revised at rogaret, resembles her anticipation cases, but the mechanism is case-syncretic double duty.

<sub>Tokens: nos (15), expectaremus (17), rogaret (21) · Sources: Laughton 1960, Observations on the Style of Varro; Halla-aho, Left-Dislocation in Latin: Topics and Syntax in Republican Texts (Amsterdam Studies in Classical Philology 28, Brill, 2018)</sub>

## S000043 (1.2.2)

> sane – inquit Agrius, et simul cogitans portam itineri dici longissimam esse ad subsellia sequentibus nobis procedit.

<a id="rn_s000043_01"></a>
**RN_S000043_01** · itineri (10) · Textual;Interpretation

The transmitted portam itineri dici longissimam esse is kept as a proverb ('the gate is said to be the longest part of a journey'); Giusta's interdici for itineri dici is not adopted.

Giusta (I 2,2b) finds the transmitted text nonsensical and reads interdici ('the gate is said to be forbidden'), a different sense, not a spelling correction. Heurgon ad loc. defends the transmitted text as a proverb, otherwise unattested but coherent: setting out feels like the longest stretch. This is a disagreement between the two editors, not a correction of an obvious corruption.

<sub>Tokens: itineri (10), dici (11) · Sources: Giusta, apparatus and notes; Heurgon, commentary</sub>

## S000045 (1.2.3)

> ego vero – Agrius – nullam arbitror esse quae tam tota sit culta.

<a id="rn_s000045_01"></a>
**RN_S000045_01** · nullam (6) · Syntax

In nullam arbitror esse quae tam tota sit culta, culta (13) heads the complement of arbitror, with nullam (6) as nsubj:outer and esse (8) as cop:outer, rather than esse heading an existential clause with the quae-clause as relative modifier of nullam.

nullam stands in the matrix accusative-and-infinitive slot while remaining the entity culta is predicated of; the pronoun and copula both sit outside culta's own argument structure. The same framing analysis is used at S000042 (quod est Romanus sedendo vincit: quod nsubj:outer and est cop:outer of vincit).

<sub>Tokens: nullam (6), esse (8), culta (13)</sub>

## S000046 (1.2.4)

> primum cum orbis terrae divisus sit in duas partes ab Eratosthene maxume secundum naturam, ad meridiem versus et ad septemtriones, et sine dubio quoniam salubrior pars septemtrionalis est quam meridiana, et quae salubriora illa fructuosiora, dicendum utique Italiam magis etiam fuisse opportunam ad colendum quam Asiam, primum quod est in Europa, secundo quod haec temperatior pars quam interior.

<a id="rn_s000046_01"></a>
**RN_S000046_01** · sentence · Textual

The transmitted order of the period is kept; Giusta's broader restructuring is not adopted.

Giusta (1.2.3-4) moves quoniam, changes the salubrior/fructuosior sequence, relocates Italia and replaces Asiam with alias. The annotation analyses the transmitted text as it stands.

<sub>Tokens: divisus (5), salubrior (27), fructuosiora (38), Italiam (42), Asiam (50) · Sources: Giusta, apparatus and notes</sub>

<a id="rn_s000046_02"></a>
**RN_S000046_02** · versus (18) · Syntax

In ad meridiem versus, versus (18) is an adverb reinforcing the direction (advmod of meridiem), not a second adposition: ad (16) already governs the case of meridiem.

<sub>Tokens: ad (16), meridiem (17), versus (18)</sub>

<a id="rn_s000046_03"></a>
**RN_S000046_03** · dicendum (40) · Syntax

The cum clause and the quoniam and quae clauses (5, 27, 38) are premises attached to dicendum (40); the two quod clauses (56, 61) attach to opportunam (46) as the two points of the magis ... quam Asiam comparison.

Heurgon ad loc. reads the period as a three-part argument for Italy: the Eratosthenian north/south division as premise, then two sub-points marked by primum (52) and secundo (58).

<sub>Tokens: divisus (5), salubrior (27), fructuosiora (38), dicendum (40), opportunam (46), Europa (56), temperatior (61) · Sources: Heurgon, commentary</sub>

## S000049 (1.2.5)

> Fundanius: em ubi tu quicquam nasci putes posse aut coli natum.

<a id="rn_s000049_01"></a>
**RN_S000049_01** · ubi (4) · Textual;Interpretation

The corrupt transmitted emobitu is read em ubi tu (Leo, followed by Giusta), 'look, where ...'; Keil's em ibi tu (after Vettori) is recorded as Variant=Keil:ibi and not adopted.

Heurgon ad loc. supports ubi: the phrase alludes to Pytheas's account (via Strabo 4.5.5) of the sterility of lands near the frozen zone, which suits a spatial where better than a deictic there, given the perpetual winters and frozen ocean of S000047-S000048.

<sub>Tokens: em (3), ubi (4) · Sources: Giusta, apparatus and notes; Heurgon, commentary; Keil, Teubner edition of Varro, Res Rusticae</sub>

## S000050 (1.2.5)

> verum enim est illud Pacuvi sol si perpetuo sit aut nox, flammeo vapore aut frigore terrae fructos omnis interire.

<a id="rn_s000050_01"></a>
**RN_S000050_01** · perpetuo (8) · Syntax

perpetuo (8) is the predicate of the si clause, 'if the sun (or night) were perpetual', with sit (9) as copula, not a manner adverb of sit; it heads the clause and remains ADV as an indeclinable word used predicatively.

The semantic test of the project rule PRED001 identifies perpetuo as the property ascribed to sol and nox. Cf. ubi as predicate at S000148.

<sub>Tokens: sol (6), perpetuo (8), sit (9)</sub>

## S000054 (1.2.6)

> quod far conferam Campano?

<a id="rn_s000054_01"></a>
**RN_S000054_01** · far (2) · Lexicon

far (2) is specifically emmer wheat (sometimes far adoreum), not grain in general.

Heurgon ad loc., citing J. Andre, Lexique des termes de botanique en latin, distinguishes far (emmer) from triticum (bearded or hard wheat), frumentum (cereals) and siligo (common bread wheat).

<sub>Sources: Heurgon, commentary · See also: [RN_S000055_01](#rn_s000055_01)</sub>

## S000055 (1.2.6)

> quod triticum Apulo?

<a id="rn_s000055_01"></a>
**RN_S000055_01** · triticum (2) · Lexicon

triticum (2) has here its narrow sense, bearded or hard wheat (ble poulard ou barbu) for Italy, as distinct from far (emmer).

Heurgon ad loc. (same note as for far in S000054). The translation keeps the generic 'wheat' to preserve the terse parallel of the rhetorical questions S000054-S000057.

<sub>Sources: Heurgon, commentary · See also: [RN_S000054_01](#rn_s000054_01)</sub>

## S000061 (1.2.7)

> in qua terra iugerum unum denos et quinos denos culleos fert vini, quot quaedam in Italia regiones?

<a id="rn_s000061_01"></a>
**RN_S000061_01** · denos (6) · Interpretation

denos et quinos denos (6-9) are coordinated distributives, 'ten and fifteen each', both with culleos (10): the question is about land yielding ten or fifteen cullei per iugerum, not fifteen alone.

Heurgon (culleus of about 520 litres, 20 amphorae) gives 10 cullei per iugerum for the ager Gallicus and 15 for the ager Faventinus, the two figures posed here. The ten is answered by the Cato quotation at S000064 (dena cullea), the fifteen at S000065 (trecenas amphoras).

<sub>Tokens: denos (6), quinos (8), denos (9), culleos (10) · Sources: Heurgon, commentary · See also: [RN_S000065_01](#rn_s000065_01)</sub>

## S000065 (1.2.7)

> nonne item in agro Faventino, a quo ibi trecenariae appellantur vites, quod iugerum trecenas amphoras reddat?

<a id="rn_s000065_01"></a>
**RN_S000065_01** · quo (8) · Syntax;Interpretation

a quo (7-8) is a plain oblique, not the agent of appellantur: a field cannot be the agent of calling. The construction is loose and pleonastic, a quo ... ibi, roughly 'where'.

Heurgon ad 1.2.7 rejects quo as agent, reads the construction as if ubi were understood, and recommends keeping the transmitted ibi (9) rather than emending.

<sub>Tokens: quo (8), ibi (9) · Sources: Heurgon, commentary</sub>

<a id="rn_s000065_02"></a>
**RN_S000065_02** · trecenariae (10) · Syntax

trecenariae (10) is the name predicated of vites after the passive naming verb appellantur (xcomp), not an attribute of vites; as amod it would leave appellantur without its naming complement.

Same pattern as Iuppiter pater appellatur (S000012) and appellare with xcomp at S000059 and S000072.

<sub>Tokens: trecenariae (10), appellantur (11), vites (12)</sub>

<a id="rn_s000065_03"></a>
**RN_S000065_03** · trecenas (16) · Interpretation

trecenas amphoras (16-17), three hundred amphorae per iugerum, equals 15 cullei, the ager Faventinus figure posed in S000061.

Heurgon: a culleus is 20 amphorae; 15 cullei per iugerum for the ager Faventinus.

<sub>Tokens: trecenas (16), amphoras (17) · Sources: Heurgon, commentary · See also: [RN_S000061_01](#rn_s000061_01)</sub>

## S000066 (1.2.7)

> simul aspicit me: certe – inquit – Libo Marcius, praefectus fabrum tuos, in fundo suo Faventiae hanc multitudinem dicebat suas reddere vites.

<a id="rn_s000066_01"></a>
**RN_S000066_01** · inquit (7) · Syntax

aspicit (2) and inquit (7) are coordinated (conj), two simultaneous actions (simul) of the same subject, 'he glances at me and says'; neither is subordinate to the other, and they are not two independent reporting clauses.

<sub>Tokens: simul (1), aspicit (2), inquit (7)</sub>

<a id="rn_s000066_02"></a>
**RN_S000066_02** · Libo (9) · Lexicon

Libo Marcius (9-10) is cognomen plus gentile name, the normal order when the praenomen is omitted; the cognomen is Libo, Libonis (third declension), not Libus.

Heurgon ad 1.2.7.

<sub>Tokens: Libo (9), Marcius (10) · Sources: Heurgon, commentary</sub>

<a id="rn_s000066_03"></a>
**RN_S000066_03** · tuos (14) · Syntax;Interpretation

tuos (14), archaic spelling of nominative tuus, agrees with praefectus (12), not with fabrum (13): praefectus fabrum is a fixed title, and 'your' refers to Varro.

Heurgon ad 1.2.7 identifies this Marcius Libo as probably the son of the moneyer Q. Marcius Libo, who served as praefectus fabrum under Varro in the campaign against the pirates in 67 BC, when Varro was Pompey's legate.

<sub>Tokens: praefectus (12), fabrum (13), tuos (14) · Sources: Heurgon, commentary</sub>

## S000067 (1.2.8)

> duo in primis spectasse videntur Italici homines colendo, possentne fructus pro impensa ac labore redire et utrum saluber locus esset an non.

<a id="rn_s000067_01"></a>
**RN_S000067_01** · possent (10) · Syntax;Interpretation

The two indirect questions possentne fructus ... redire (10) and utrum saluber locus esset an non (20) spell out cataphorically what duo (1) refers to, so the first attaches as acl to duo and the second is coordinated with it. duo is the object of spectasse, not the subject of videntur; the subject is Italici homines.

duo names 'two things' that the Italians looked at in farming; the two questions that follow state what those two things are. Its sentence-initial position does not make it the subject of videntur: homines (7) fills that role.

<sub>Tokens: possent (10), saluber (20)</sub>

<a id="rn_s000067_02"></a>
**RN_S000067_02** · ne (11) · Tokenization

possentne is split into possent (10) + ne (11) because -ne is here a productive interrogative enclitic on an open host, as with hos + ce (S000032). This differs from nonne, which is a lexicalised headword and stays one token (TOK001).

The test is dictionary status: possum is the headword and -ne attaches compositionally, whereas nonne has its own entry and meaning and is not compositionally non + ne.

<sub>Tokens: possent (10), ne (11)</sub>

## S000068 (1.2.8)

> quorum si alterutrum decolat et nihilo minus quis vult colere, mente est captus adque adgnatos et gentiles est deducendus.

<a id="rn_s000068_01"></a>
**RN_S000068_01** · adque (15) · Lexicon;Textual

adque is read as a spelling of atque (CCONJ), coordinating captus and deducendus; the transmitted text has no preposition before adgnatos. Keil, followed by Heurgon, and Giusta restore ad (atque ad adgnatos) on the model of Columella; the restoration is not adopted into the text.

Heurgon's apparatus (1.2.8): 'atque ad adgnatos Keil : adque gnatos P ... adque adgnatos Zahlfeldt Goetz'. Giusta takes archetypal adque as a corrupted atque and restores ad, citing Columella 1.3.1 'atque eum ad agnatos et gentilis deducendum'. Heurgon (comm. 26) follows Keil 'because of Columella'. adque is itself an attested spelling of atque, not a truncation of ad, so the lemma atque holds on the transmitted text.

<sub>Sources: Heurgon, Latin text; Heurgon, commentary; Giusta, apparatus and notes</sub>

<a id="rn_s000068_02"></a>
**RN_S000068_02** · adgnatos (16) · Lexicon;Interpretation

adgnatos is the legal noun agnatus 'paternal kinsman', not a participle of adgnascor: the phrase alludes to the Twelve Tables provision on guardianship of the insane. It is obl of deducendus as the goal (handed over to the agnates), the role an overt ad would mark.

Heurgon (comm. 26, 'mente captus and legal allusion') identifies the phrase as an almost verbatim citation of the Twelve Tables (agnatum gentiliumque ... potestas esto) and compares Columella's paraphrase.

<sub>Sources: Heurgon, commentary</sub>

## S000069 (1.2.8)

> nemo enim sanus debet velle impensam ac sumptum facere in cultura, si videt non posse refici, nec si potest reficere fructus, si videt eos fore ut pestilentia dispereant.

<a id="rn_s000069_01"></a>
**RN_S000069_01** · fore (28) · Syntax

fore ut pestilentia dispereant is the periphrastic future infinitive (fore ut + subjunctive), used because dispereo has no future participle; the ut-clause is therefore the complement of fore (28), not a separate clause of videt.

fore ut dispereant stands for an impossible eos disperituros esse. Laughton (1960, p. 6) cites this sentence as an example of prolepsis and reports Woodcock's suggestion that the construction 'may be due to the conflation ... of eos disperituros with fore ut', i.e. a blend of the accusative-and-infinitive with a future participle and the periphrasis. This explains the choice of construction and leaves the ccomp of dispereant on fore intact.

<sub>Tokens: fore (28), dispereant (31) · Sources: Laughton 1960, Observations on the Style of Varro</sub>

<a id="rn_s000069_02"></a>
**RN_S000069_02** · pestilentia (30) · Morphology;Interpretation

pestilentia is read as the neuter plural of the adjective pestilens 'unhealthy', used substantivally as nominative subject of dispereant, not as the noun pestilentia 'pestilence' in the ablative. The plural agrees with dispereant.

The resulting sense is '(he sees that) unhealthy conditions will destroy them', with eos (the produce, 27) understood as the affected party. This requires a causative extension of the normally intransitive dispereo; the construction is loose and compressed, and translations render the sense rather than the words.

<sub>Tokens: pestilentia (30), dispereant (31)</sub>

## S000071 (1.2.9)

> nam C. Licinium Stolonem et Cn. Tremelium Scrofam video venire;

<a id="rn_s000071_01"></a>
**RN_S000071_01** · Scrofam (10) · Morphology

Scrofam is Gender=Masc although scrofa 'sow' is a feminine first-declension noun: as a cognomen of a man (Cn. Tremelius Scrofa) the proper noun takes the gender of its referent (NAME001).

Compare masculine cognomina of the first declension such as Galba, Sulla, Scaevola, which take masculine agreement.

## S000072 (1.2.9)

> unum, cuius maiores de modo agri legem tulerunt (nam Stolonis illa lex, quae vetat plus D iugera habere civem R.) , et qui propter diligentiam culturae Stolonum confirmavit cognomen, quod nullus in eius fundo reperiri poterat stolo, quod effodiebat circum arbores e radicibus quae nascerentur e solo, quos stolones appellabant.

<a id="rn_s000072_01"></a>
**RN_S000072_01** · nascerentur (52) · Syntax;Interpretation

Both relative clauses, quae nascerentur e solo (52) and quos stolones appellabant (58), modify radicibus (50): the root-suckers springing from the ground are what were called stolones. Giusta's reattachment of e radicibus to nascerentur is not adopted.

The apparent mismatch (stolo means a sucker or shoot, not a root; Heurgon comm. 28, citing Pliny) disappears if stolo is the root-like runner that puts out new growth at ground level, the ancestor of botanical 'stolon'. Giusta instead makes e radicibus depend on nascerentur, reads a solo with appellabant, and appellant for appellabant. The botanical point has not been checked against Flach's commentary.

<sub>Tokens: nascerentur (52), appellabant (58) · Sources: Giusta, apparatus and notes; Heurgon, commentary</sub>

## S000073 (1.2.9)

> eiusdem gentis C. Licinius, tr. pl. cum esset, post reges exactos annis CCCLXV primus populum ad leges accipiendas in septem iugera forensia e comitio eduxit.

<a id="rn_s000073_01"></a>
**RN_S000073_01** · iugera (26) · Textual;Interpretation

in septem iugera forensia is a crux. The tree follows Heurgon's construal (iugera obl of eduxit, forensia its amod), reading the phrase as Varro's joke calling the forum a 'seven-iugera' farm; Giusta would obelize it as irrecoverably corrupt.

Giusta (I 2,9b) rejects Orsini's e foro ac and Traglia's forensi[a], Göttling's saepta [iugera] forensia and Cardinali's [septem] iugera, and the interpretations of Pighi and Huschke, and concludes the phrase should be closed in cruces. Heurgon (comm. 29) defends it: Columella 1.3.10 and Pliny NH 18.18 attest seven-iugera allotments after the kings; this C. Licinius is Crassus (tr. pl. 145 BC), who first addressed the people facing the forum (Cicero, Lael. 96). Hooper and Ash translate 'the “farm” of the forum'. The textual status of the phrase remains contested.

<sub>Tokens: septem (25), iugera (26), forensia (27) · Sources: Giusta, apparatus and notes; Heurgon, commentary; W.D. Hooper (trans.), rev. H.B. Ash, Varro: On Agriculture, Loeb Classical Library</sub>

## S000074 (1.2.10)

> alterum collegam tuum, viginti virum qui fuit ad agros dividendos Campanos, video huc venire, Cn. Tremelium Scrofam, virum omnibus virtutibus politum, qui de agri cultura Romanus peritissimus existimatur.

<a id="rn_s000074_01"></a>
**RN_S000074_01** · collegam (2) · Syntax

collegam (2) is the head of the accusative subject of venire, with alterum (1) as its determiner ('your other colleague'); viginti virum, Cn. Tremelium Scrofam and virum omnibus virtutibus politum are all appositions to collegam.

collegam is the noun that names the relationship; everything that identifies the man (his office in the land commission, his name, his character) attaches to it rather than to alterum.

<sub>Tokens: alterum (1), collegam (2)</sub>

## S000076 (1.2.10)

> fundi enim eius propter culturam iucundiore spectaculo sunt multis, quam regie polita aedificia aliorum, cum huius spectatum veniant villas, non, ut apud Lucullum, ut videant pinacothecas, sed oporothecas.

<a id="rn_s000076_01"></a>
**RN_S000076_01** · iucundiore (6) · Morphology;Textual

iucundiore spectaculo is ablative (the predicate of fundi ... sunt), since the transmitted iucundiore has an ablative ending. Giusta argues for a predicative dative and emends to iucundiori; not adopted.

Giusta objects that spectaculum is not a quality and so cannot be an ablative of quality; he reads spectaculo as dative and cites Columella 11.3.57 esui and Pliny NH 6.203 potui as predicative datives. spectaculo itself is dative or ablative, but iucundiore is not a dative form, so the dative requires the emendation.

<sub>Tokens: iucundiore (6), spectaculo (7) · Sources: Giusta, apparatus and notes</sub>

<a id="rn_s000076_02"></a>
**RN_S000076_02** · non (23) · Syntax

non (23) attaches to pinacothecas (31), the constituent it contrasts with sed oporothecas (34), not to videant; the negation thus does not cover oporothecas, and no second videant needs to be reconstructed.

Narrow-scope negation on a nominal is regular UD practice. Compare non solum ... sed etiam post mortem in S000004, where etiam attaches to mortem.

<sub>Tokens: non (23), pinacothecas (31), oporothecas (34)</sub>

## S000078 (1.2.11)

> illi interea ad nos;

<a id="rn_s000078_01"></a>
**RN_S000078_01** · illi (1) · Syntax;Interpretation

illi is nominative plural and refers to Stolo and Scrofa, whose arrival is described from S000071 on: 'they meanwhile [joined] us'. The verb of arriving is not expressed and is reconstructed as empty node 1.1; illi is not a dative 'to him' with inquit.

The empty node has no FORM or LEMMA because several verbs (venio, advenio and near-synonyms) would fit equally well and nothing in the context selects one; only UPOS=VERB is certain.

<sub>Tokens: illi (1),  (1.1), nos (4)</sub>

## S000081 (1.2.11)

> nam non modo ovom illut sublatum est, quod ludis circensibus novissimi curriculi finem facit quadrigis, sed ne illud quidem ovom vidimus, quod in cenali pompa solet esse primum.

<a id="rn_s000081_01"></a>
**RN_S000081_01** · est (7) · Syntax;Textual

non modo ... sed ne ... quidem is kept without a second non before est: Giusta's insertion (sublatum <non> est) is not needed, because in this idiom the negation of ne ... quidem also covers the first member.

Giusta (I 2,11) holds that without non the following ne ... quidem is incomprehensible. Heurgon (comm. 35), on the same construction, notes that Cicero uses it with the first member negative (= non modo non), the negation of ne ... quidem reaching back to it (Ernout-Thomas, Syntaxe latine §179).

<sub>Sources: Giusta, apparatus and notes; Heurgon, commentary; Ernout-Thomas, Syntaxe latine §179</sub>

<a id="rn_s000081_02"></a>
**RN_S000081_02** · quadrigis (16) · Syntax;Interpretation

quadrigis is read as ablative (dative and ablative plural coincide): the egg 'marks the end of the last lap, run by the four-horse teams', rather than a dative of the party for whom the end is made.

## S000082 (1.2.12)

> itaque dum id nobiscum una videatis ac venit aeditumus, docete nos, agri cultura quam summam habeat, utilitatemne an voluptatem an utrumque.

<a id="rn_s000082_01"></a>
**RN_S000082_01** · aeditumus (10) · Lexicon;Textual

aeditumus is kept, with lemma aeditumus, as Varro's own archaic spelling, not normalised to aedituus or to the manuscript form aeditimus.

Heurgon (ad 1.2.1) prints aeditumus throughout, following Keil, and cites Varro's usage at 1.2.12 (this sentence) and 69.2 as evidence that the -u- spelling is authorial, although the manuscripts mostly have -i-.

<sub>Sources: Heurgon, commentary</sub>

<a id="rn_s000082_02"></a>
**RN_S000082_02** · utilitatem (21) · Syntax

utilitatemne an voluptatem an utrumque is in apposition to summam (18): the series restates what summam refers to, rather than being a further argument of habeat.

<sub>Tokens: utilitatem (21), voluptatem (24), utrumque (26)</sub>

## S000083 (1.2.12)

> ad te enim rudem esse agri culturae nunc, olim ad Stolonem fuisse dicunt.

<a id="rn_s000083_01"></a>
**RN_S000083_01** · rudem (4) · Lexicon;Interpretation

rudem plays on the rudis, the wooden sword given to a retiring gladiator: Scrofa is now called the veteran, honourably discharged master of agriculture, as Stolo once was. 'Unskilled' would reverse the sense.

Heurgon (comm. 40, 1.2.12) explains the rudis metaphor and notes that Stolo, though younger, had once surpassed Scrofa in reputation (cf. 2.1.11 Scrofa noster, cui haec aetas defert rerum rusticarum omnium palmam). Scrofa goes on to give the authoritative exposition from S000084.

<sub>Sources: Heurgon, commentary</sub>

## S000084 (1.2.12)

> Scrofa: prius – inquit – discernendum, utrum quae serantur in agro, ea sola sint in cultura, an etiam quae inducantur in rura, ut oves et armenta.

<a id="rn_s000084_01"></a>
**RN_S000084_01** · quae (10) · Syntax;Interpretation

quae (10) and quae (23), nominative neuter plural and so formally identical with the accusative, are not taken as notional objects of discernendum by case-syncretic sharing, unlike quae in S000005.

In S000005 cecinisse immediately precedes its headless relative and quae is the only possible filler of its object slot. Here the overt resumptive ea (15) already links the relative clause, and discernendum takes the indirect question as its clausal subject, leaving no accusative slot. The link would have to skip ea sola sint in cultura, a longer jump than in any accepted case. An available overt resumptive is a useful test against such readings.

<sub>Tokens: quae (10), quae (23) · Sources: Niemi, Case-Syncretic Sharing in Varro’s Language</sub>

<a id="rn_s000084_02"></a>
**RN_S000084_02** · ea (15) · Syntax

quae serantur in agro is a headless relative clause placed before its resumptive ea (15): a correlative left-dislocation, tagged Prolepsis on ea. Because the relative clause comes first and ea resumes it, this is the anaphoric direction, unlike S000035, where ea is tagged Prolepsis:Cataphoric.

<sub>Tokens: serantur (11), ea (15) · Sources: Halla-aho, Left-Dislocation in Latin: Topics and Syntax in Republican Texts (Amsterdam Studies in Classical Philology 28, Brill, 2018)</sub>

<a id="rn_s000084_03"></a>
**RN_S000084_03** · cultura (19) · Syntax

The indirect question utrum ... an ... is the clausal subject of the impersonal gerundive discernendum (7), so its head cultura (19) is csubj:pass rather than ccomp.

With a gerundive of obligation (discernendum [est] 'it must be decided') the question is what must be decided, i.e. the subject of the passive-impersonal form, not a complement of a transitive verb.

<sub>Tokens: discernendum (7), cultura (19)</sub>

<a id="rn_s000084_04"></a>
**RN_S000084_04** · inducantur (24) · Syntax

In the second branch (an etiam quae inducantur in rura) the frame ea sola sint in cultura is omitted and recoverable from the first branch. The surviving relative clause headed by inducantur (24) is promoted as conj of cultura (19), and its own dependents attach to it normally, so no orphan relation is needed.

<sub>Tokens: cultura (19), inducantur (24)</sub>

## S000085 (1.2.13)

> video enim, qui de agri cultura scripserunt et Poenice et Graece et Latine, latius vagatos, quam oportuerit.

<a id="rn_s000085_01"></a>
**RN_S000085_01** · oportuerit (20) · Syntax

quam oportuerit omits the infinitive subject of oportuerit, recoverable as vagari from vagatos (17): 'than [to wander] would have been proper'. The omission is marked with SyntaxNote=Ellipsis rather than an empty node because it leaves no dependent without a governor.

quam is mark of oportuerit and oportuerit attaches to vagatos as advcl:cmp, so nothing in the clause needs the missing verb as head. That the missing verb is fully identifiable does not decide between note and empty node. Contrast S000078, where the omitted verb's dependents need a node.

## S000086 (1.2.13)

> ego vero – inquit Stolo – eos non in omni re imitandos arbitror et eo melius fecisse quosdam, qui minore pomerio finierunt exclusis partibus quae non pertinent ad hanc rem.

<a id="rn_s000086_01"></a>
**RN_S000086_01** · eo (15) · Syntax

eo (15) is the ablative of degree of difference with the comparative melius (16), 'better by that much', and so attaches to melius rather than to fecisse.

<sub>Tokens: eo (15), melius (16)</sub>

## S000088 (1.2.14)

> quocirca principes qui utrique rei praeponuntur vocabulis quoque sunt diversi, quod unus vocatur vilicus, alter magister pecoris.

<a id="rn_s000088_01"></a>
**RN_S000088_01** · alter (17) · Syntax

alter magister pecoris is a gapped clause parallel to unus vocatur vilicus: alter is the subject of an omitted second vocatur (17.1) and magister its predicative complement, 'the other [is called] master of the herd'. alter is not a determiner of magister.

Reading alter as a determiner ('the other master') breaks the parallel with the first clause and gives the wrong sense.

<sub>Tokens: alter (17), magister (18)</sub>

## S000089 (1.2.14)

> vilicus agri colendi causa constitutus atque appellatus a villa, quod ab eo in eam convehuntur fructus et evehuntur, cum veneunt.

<a id="rn_s000089_01"></a>
**RN_S000089_01** · agri (2) · Syntax

agri colendi causa is read as gerundive attraction (agri head, colendi agreeing with it) rather than gerund plus objective genitive. The string is ambiguous because the masculine gerundive and the gerund have the same form.

Classical Latin prefers the gerundive construction whenever the object can take agreement (urbis condendae causa, rei publicae gerendae causa). The resemblance to agri cultura is set aside as irrelevant. No parallel with a feminine or neuter noun in the reviewed text settles the ambiguity, so the reading rests on the general rule.

<sub>Tokens: agri (2), colendi (3)</sub>

## S000090 (1.2.14)

> a quo rustici etiam nunc quoque viam veham appellant propter vecturas et vellam, non villam, quo vehunt et unde vehunt.

<a id="rn_s000090_01"></a>
**RN_S000090_01** · vehunt (19) · Syntax;Interpretation

appellant governs two separate 'call X Y' predications: viam veham for the road, and, with appellant omitted (16.1), [quo vehunt et unde vehunt] vellam, non villam for the farmhouse. The headless relative quo vehunt et unde vehunt fills the object slot of the second predication, so vehunt (19) is promoted over vellam (13).

Each predication has its own object and complement, so they cannot share one appellant. vehunt heads the clause in object function, which outranks vellam's xcomp in the promotion order. Varro thus defines the farmhouse by its function, 'where they carry to and from', instead of the circular villam vellam appellant.

<sub>Tokens: vellam (13), vehunt (19)</sub>

## S000091 (1.2.14)

> item dicuntur qui vecturis vivunt velaturam facere.

<a id="rn_s000091_01"></a>
**RN_S000091_01** · vivunt (5) · Syntax

The headless relative qui vecturis vivunt is the clausal subject of passive dicuntur and is labelled csubj:pass; facere (7) is xcomp of dicuntur, not of vivunt.

dicuntur + infinitive is the nominative-with-infinitive construction, like videtur with nsubj:pass pastio in S000087, and csubj:pass keeps the passive marking for a clausal subject of the same construction. S000085 (csubj:relcl) differs: there the headless relative is subject of a participle in an accusative-with-infinitive. The infinitive is controlled by the matrix, as pertinere under videtur in S000087.

<sub>Tokens: vivunt (5), facere (7)</sub>

## S000092 (1.2.15)

> certe – inquit Fundanius – aliut pastio et aliut agri cultura, sed adfinis et ut dextra tibia alia quam sinistra, ita ut tamen sit quodam modo coniuncta, quod est altera eiusdem carminis modorum incentiva, altera succentiva.

<a id="rn_s000092_01"></a>
**RN_S000092_01** · aliut (6) · Syntax

aliut (6) and aliut (9) are the predicates of their clauses (root and conj), with pastio and cultura as subjects: aliud est X, aliud Y is a fixed idiom with an invariant neuter predicate.

Cf. Cicero aliud est maledicere, aliud accusare, where the subject is an infinitive. The gender mismatch (neuter aliut, feminine pastio) is not evidence either way, since abstract neuter predicates stay invariant. Laughton shows the verbless alius ... alius distinction to be ordinary in Varro's etymological writing (alia [est] coloni, alia pastoris).

<sub>Tokens: aliut (6), aliut (9) · Sources: Laughton 1960, Observations on the Style of Varro</sub>

<a id="rn_s000092_02"></a>
**RN_S000092_02** · aliut (6) · Morphology;Textual

The spelling aliut is kept as transmitted. Giusta regards aliut as a late scribal trivialisation and prints aliud; final -t for -d is, however, a genuine Old Latin spelling and fits Varro's antiquarian habits.

Giusta compares the adque/atque corruption. The point is disputed; aliut is kept in line with the treatment of other attested archaic forms (cf. fructos, S000011).

<sub>Tokens: aliut (6), aliut (9) · Sources: Giusta, apparatus and notes</sub>

## S000093_S000094 (1.2.16)

> et quidem licet adicias – inquam – pastorum vitam esse incentivam, agricolarum succentivam auctore doctissimo homine Dicaearcho, qui Graeciae vita qualis fuerit ab initio nobis ita ostendit, ut superioribus temporibus fuisse doceat, cum homines pastoriciam vitam agerent neque scirent etiam arare terram aut serere arbores aut putare; ab iis inferiore gradu aetatis susceptam agri culturam.

<a id="rn_s000093_s000094_01"></a>
**RN_S000093_S000094_01** · sentence · Segmentation

S000093 and S000094 form one sentence: ab iis inferiore gradu aetatis susceptam agri culturam has no finite verb, and ab iis resumes homines of the preceding cum-clause.

susceptam agrees with agri culturam (accusative singular feminine) and depends on the reporting structure of the preceding sentence; the fragment is coherent only as part of it.

<a id="rn_s000093_s000094_02"></a>
**RN_S000093_S000094_02** · ostendit (29) · Syntax · **Open**

Is qui (20) a connecting relative ('and he shows ...')? The tree assumes so: ostendit is attached as parataxis to adicias rather than as acl:relcl of Dicaearcho, because of the independent weight of its clause.

The reading rests on the weight of what ostendit's clause says rather than on decisive external evidence, and remains open. The ita ... ut ... doceat link is unaffected.

<sub>Tokens: qui (20), ostendit (29)</sub>

<a id="rn_s000093_s000094_03"></a>
**RN_S000093_S000094_03** · temporibus (33) · Syntax;Interpretation

temporibus (33) is the predicate of its clause, 'was [a matter] of earlier times', with fuisse as copula; the clause susceptam agri culturam (58) is its clausal subject. Nothing is elided, and fuisse is not existential (SUM001).

Heurgon's French (1.2.16, 'il montre que ... mais que ...') shows the susceptam clause belongs to what Dicaearchus demonstrates, not to a third item added under adicias. Case does not decide a predicate (SUM001); compare the adverbial predicate ubi in S000148.

<sub>Tokens: temporibus (33), fuisse (34), susceptam (58) · Sources: Heurgon, French translation</sub>

## S000096 (1.2.17)

> Agrius: tu – inquit – tibicen non solum adimis domino pecus, sed etiam servis peculium, quibus domini dant ut pascant, atque etiam leges colonicas tollis, in quibus scribimus, colonus in agro surculario ne capra natum pascat;

<a id="rn_s000096_01"></a>
**RN_S000096_01** · peculium (17) · Syntax

non solum adimis domino pecus, sed etiam servis peculium contains two predications with separate dative and object pairs sharing only the verb; the second adimis is reconstructed (17.1), with peculium (17) promoted and servis (16) as orphan.

Coordinating servis with domino and peculium with pecus under one adimis would imply a single taking of four arguments. peculium outranks servis in the promotion order. servis cannot attach directly to peculium as possessor, since a possessive dative requires a copula (est mihi liber), so it depends on the reconstructed verb.

<sub>Tokens: servis (16), peculium (17)</sub>

<a id="rn_s000096_02"></a>
**RN_S000096_02** · capra (40) · Syntax;Morphology

capra is ablative of source with natum, 'born of a goat', and natum is a substantival participle ('kid'), object of pascat: the tenant must not graze a young goat on land planted with young trees.

capra could be nominative or ablative, but pascat already has colonus (35) as subject. natum rests on Victorius's correction (Giusta ad 1.2.17: capra <na>tum), printed by Heurgon. Young goats are notoriously harmful to young shoots, which is why tenancy clauses forbid them.

<sub>Tokens: capra (40), natum (41) · Sources: Giusta, apparatus and notes; Heurgon, Latin text</sub>

## S000097 (1.2.17)

> quas etiam astrologia in caelum recepit, non longe ab tauro.

<a id="rn_s000097_01"></a>
**RN_S000097_01** · quas (1) · Syntax;Textual

quas (plural) resumes capra (singular, S000096) by sense, referring to goats as a kind; it is a connecting relative, 'and these ...'. Giusta's quam is not adopted.

Giusta (1.2.17) argues for quam because the antecedent is singular capra and the constellation is Capra (the she-goat that nursed Jupiter), singular; he himself notes a similar shift in number later (istae quas dixisti, S000099). Heurgon (and Henderson) print quas.

<sub>Sources: Giusta, apparatus and notes; Heurgon, Latin text · See also: [RN_S000099_02](#rn_s000099_02)</sub>

## S000099 (1.2.18)

> quaedam enim pecudes culturae sunt inimicae ac veneno, ut istae, quas dixisti, caprae.

<a id="rn_s000099_01"></a>
**RN_S000099_01** · culturae (4) · Morphology;Interpretation

culturae (4) can be genitive or dative with inimicae (6): genitive with inimicae used as a noun, 'enemies of agriculture', or dative with the adjective, 'hostile to agriculture'. The genitive reading is annotated (nmod).

The two readings differ only slightly in sense; the dative would be obl:arg of inimicae. The English translation renders the dative reading.

<sub>Tokens: culturae (4), inimicae (6)</sub>

<a id="rn_s000099_02"></a>
**RN_S000099_02** · veneno (8) · Syntax;Morphology

veneno is the noun venenum in the dative, coordinated by ac with the predicate inimicae (6): the animals 'are hostile to agriculture and [a] poison'. It is not a verb.

<sub>Tokens: inimicae (6), veneno (8)</sub>

<a id="rn_s000099_03"></a>
**RN_S000099_03** · caprae (16) · Syntax

ut istae, quas dixisti, caprae is an elliptical comparison: istae (11) and caprae (16) form one noun phrase around the relative clause quas dixisti, and caprae heads the comparison.

<sub>Tokens: istae (11), caprae (16) · See also: [RN_S000097_01](#rn_s000097_01)</sub>

## S000101 (1.2.19)

> itaque propterea institutum diversa de causa ut ex caprino genere ad alii dei aram hostia adduceretur, ad alii non sacrificaretur, cum ab eodem odio alter videre nollet, alter etiam videre pereuntem vellet.

<a id="rn_s000101_01"></a>
**RN_S000101_01** · alii (12) · Syntax;Morphology

alii (12) is an archaic genitive singular of alius ('of one god'), determiner of dei; alii (19) repeats the construction elliptically ('to another's [altar]').

Classical Latin supplies alterius for the missing genitive of alius, but early Latin attests alii, parallel to unius and illius; Varro's antiquarian register makes the archaic form likely here.

<sub>Tokens: alii (12), alii (19)</sub>

## S000103_S000104 (1.2.19)

> contra ut Minervae caprini generis nihil immolarent propter oleam, quod eam quam laeserit fieri dicunt sterilem; eius enim salivam esse fructuis venenum;

<a id="rn_s000103_s000104_01"></a>
**RN_S000103_S000104_01** · fructuis (23) · Morphology;Textual

fructuis is an archaic fourth-declension dative plural of fructus, the complement of venenum ('poison to the fruits'), not a corruption of fructibus.

Heurgon's apparatus (2.19): 'fructuis Vb NON. 491,9 : -tus Am'. The Vb branch and Nonius' independent citation support fructuis; Am's fructus is a truncation.

<sub>Sources: Heurgon, Latin text; Nonius 491.9</sub>

## S000105 (1.2.20)

> hoc nomine etiam Athenis in arcem non inigi, praeterquam semel ad necessarium sacrificium, ne arbor olea, quae primum dicitur ibi nata, a capra tangi possit.

<a id="rn_s000105_01"></a>
**RN_S000105_01** · Athenis (4) · Morphology

Athenis is tagged Case=Loc ('at Athens'), not ablative: the plural place-name locative has the ablative form, but the treebank tags place-name locatives as Loc, as for Faventiae (INFL001).

<a id="rn_s000105_02"></a>
**RN_S000105_02** · inigi (8) · Syntax

The infinitive inigi still depends on dicunt (S000103_S000104, 16), whose reported speech continues into this sentence without being repeated; this is marked SyntaxNote=Ellipsis.

All dependents of inigi attach to it directly and none is left without a governor, so neither an empty node nor InheritedFrom is needed.

## S000106 (1.2.20)

> nec ullae – inquam – pecudes agri culturae sunt propriae, nisi quae agrum opere, quo cultior sit, adiuvare, ut eae quae iunctae arare possunt.

<a id="rn_s000106_01"></a>
**RN_S000106_01** · quo (17) · Syntax;Interpretation

quo (17) is an ablative of degree of difference with cultior (18), and quo cultior sit is a relative clause on opere: 'labour, by which [the field] becomes more cultivated'.

<sub>Tokens: quo (17), cultior (18)</sub>

<a id="rn_s000106_02"></a>
**RN_S000106_02** · adiuvare (21) · Syntax

adiuvare (21) has no governing verb: the modal is supplied from the parallel ut eae quae iunctae arare possunt (28), nisi quae agrum opere ... adiuvare [possunt]. The infinitive heads the nisi-clause and carries SyntaxNote=Ellipsis.

quae, agrum, opere and the ut-clause all attach to adiuvare, so no dependent is left without a governor. Giusta supplies the modal overtly (Variant=Giusta:queunt+ on quae, 13).

<sub>Tokens: adiuvare (21), possunt (28)</sub>

## S000107 (1.2.21)

> Agrasius: si istuc ita est – inquit – quo modo pecus removeri potest ab agro, cum stercus, quod plurimum prodest, greges pecorum ministrent?

<a id="rn_s000107_01"></a>
**RN_S000107_01** · stercus (19) · Syntax

greges (25) is the subject and stercus (19) the object of ministrent: both nouns are nominative-accusative ambiguous, but the plural verb requires the plural greges as subject.

<sub>Tokens: stercus (19), greges (25)</sub>

## S000110 (1.2.21)

> nam sic etiam res aliae diversae ab agro erunt adsumendae, ut si habet plures in fundo textores atque institutos histonas, sic alios artifices.

<a id="rn_s000110_01"></a>
**RN_S000110_01** · agro (8) · Syntax

ab agro depends on diversae (6), 'things different from farming', not on adsumendae.

<sub>Tokens: diversae (6), agro (8)</sub>

<a id="rn_s000110_02"></a>
**RN_S000110_02** · habet (14) · Syntax;Textual

The subject of habet is unexpressed: it is the estate owner. plures textores is therefore the object ('[the owner] has several weavers'), not the subject; ager cannot sensibly have weavers.

Giusta (1.2.21) inserts quis; Heurgon (comm. 54): 'si habet: sujet non exprimé; c'est la personne intéressée, ici le propriétaire'. The transmitted text is kept (Variant=Giusta:quis+ on si).

<sub>Tokens: habet (14), plures (15), textores (18) · Sources: Giusta, apparatus and notes; Heurgon, commentary</sub>

## S000112 (1.2.22)

> anne ego – inquam – sequar Sasernarum patris et filii libros ac magis putem pertinere, figilinas quem ad modum exerceri oporteat, quam argentifodinas aut alia metalla, quae sine dubio in aliquo agro fiunt?

<a id="rn_s000112_01"></a>
**RN_S000112_01** · Sasernarum (7) · Morphology

Sasernarum is Gender=Masc despite the feminine first-declension form: the Sasernae were two men, father and son, agricultural writers (NAME001).

Heurgon (comm. 55) identifies them; they are also cited by Columella and Pliny.

<sub>Sources: Heurgon, commentary</sub>

## S000116 (1.2.23)

> non enim, siquid propter agrum aut etiam in agro profectus domino, agri culturae acceptum referre debet, sed id modo quod ex satione terra sit natum ad fruendum.

<a id="rn_s000116_01"></a>
**RN_S000116_01** · profectus (12) · Syntax;Lexicon

profectus is the noun 'gain, profit' in the nominative, the predicate of the verbless conditional si quid ... profectus domino [est] ('if any gain has come to the owner'), with quid (5) as subject; it is not the participle of proficiscor.

<sub>Tokens: quid (5), profectus (12)</sub>

## S000118 (1.2.25)

> cum subrisisset Scrofa, quod non ignorabat libros et despiciebat, et Agrasius se scire modo putaret ac Stolonem rogasset ut diceret, coepit:

<a id="rn_s000118_01"></a>
**RN_S000118_01** · sentence · Segmentation

The sentence ends at the colon and is kept separate from the quotation it introduces, although the two form one discourse unit; the cross-sentence relation is not annotated.

A merge would change neither internal tree beyond attaching coepit (24) as parataxis:reporting to the root of the following sentence, which the colon and context already make recoverable.

<a id="rn_s000118_02"></a>
**RN_S000118_02** · coepit (24) · Syntax;Interpretation

The unexpressed subject of coepit (24) is Stolo, the object of rogasset (20): the man asked to explain is the one who begins, not Agrasius, the subject of the preceding clauses.

Heurgon's rendering makes the switch explicit (« celui-ci commença »).

<sub>Tokens: Stolonem (19), rogasset (20), coepit (24) · Sources: Heurgon, French translation</sub>

## S000120 (1.2.25)

> “cucumerem anguinum condito in aquam eamque infundito quo voles, nulli accedent;

<a id="rn_s000120_01"></a>
**RN_S000120_01** · accedent (14) · Syntax

accedent (14) carries SyntaxNote=Anacoluthon: the recipe's second-person imperatives condito (4) and infundito (9) break off into a third-person future indicative stating the result, whose subject nulli (13) refers to the bedbugs (cimices) of S000119, not to anything inside the quotation.

The shift is twofold: from imperative to indicative, and from an instruction to the reader to an assertion about a third party. No relation records it; asyndetic conj on infundito (9) is the closest available attachment, since there is no subordinator or result marker. nulli (13), masc. pl., agrees with cimices; Heurgon's « aucune n'approchera » makes the reference explicit.

<sub>Tokens: condito (4), infundito (9), nulli (13), accedent (14) · Sources: Heurgon, French translation</sub>

## S000121 (1.2.25)

> vel fel bubulum cum aceto mixtum, unguito lectum. ”

<a id="rn_s000121_01"></a>
**RN_S000121_01** · fel (2) · Syntax;Textual

fel (2) has no governing verb of its own: the recipe names the substance and jumps to unguito (8), whose object is lectum (9). fel is attached to unguito as parataxis with SyntaxNote=Ellipsis for an implied verb of taking.

Giusta (on 1.2.25) supplies sumito, tum after mixtum; Heurgon's apparatus records no manuscript reading that fills the gap, so the supplement is editorial and the transmitted text is kept. fel cannot be the object of unguito (one does not anoint gall; the bed is anointed). The implied verb (sumito is one candidate, not the only one) is not determinate enough for an orphan or empty-node analysis. This is ordinary recipe ellipsis, not a broken construction at fel.

<sub>Tokens: fel (2), mixtum (6), unguito (8) · Sources: Giusta, apparatus and notes; Heurgon, Latin text; Heurgon, French translation</sub>

<a id="rn_s000121_02"></a>
**RN_S000121_02** · unguito (8) · Syntax

unguito (8) carries SyntaxNote=Anacoluthon: the accusative phrase fel bubulum cum aceto mixtum is set up as if it will be the argument of the following verb, but unguito takes a different accusative, lectum (9).

Ellipsis at fel (2) and Anacoluthon at unguito (8) record different phenomena and co-occur without contradiction.

<sub>Tokens: fel (2), unguito (8), lectum (9)</sub>

## S000122 (1.2.26)

> ille: tam hercle quam hoc, siquem glabrum facere velis, quod iubet ranam luridam coicere in aquam, usque qua ad tertiam partem decoxeris, eoque unguere corpus.

<a id="rn_s000122_01"></a>
**RN_S000122_01** · hoc (6) · Syntax;Interpretation

The verbless asseveration tam hercle quam hoc is rooted at hoc (6), tagged Prolepsis:Cataphoric: hoc anticipates the depilation recipe that follows. ille (1), with no reporting verb in the text, attaches to it as parataxis:reporting.

Heurgon's rendering (« et ceci encore : si vous voulez... ») confirms that hoc points forward to the recipe.

<sub>Tokens: hoc (6), , (7), iubet (15) · Sources: Heurgon, French translation</sub>

<a id="rn_s000122_02"></a>
**RN_S000122_02** · decoxeris (27) · Syntax

decoxeris (27) is a relative clause on aquam (20), not a further instruction coordinated with coicere (18): qua (23) refers back to the water in which the frog is boiled down to a third.

<sub>Tokens: aquam (20), qua (23), decoxeris (27)</sub>

## S000126 (1.2.27)

> nam malo de meis pedibus audire, quam quem ad modum pedes betaceos seri oporteat.

<a id="rn_s000126_01"></a>
**RN_S000126_01** · pedibus (5) · Lexicon;Interpretation

Fundanius puns on pes: pedibus (5) are his own aching feet (cf. S000124), pedes betaceos (12-13) are beet cuttings, a horticultural use of the same noun.

Heurgon keeps the play (« de mes pieds à moi... les pieds de bette »). The translation must keep the same noun in both places.

<sub>Tokens: pedibus (5), pedes (12), betaceos (13) · Sources: Heurgon, French translation</sub>

## S000127 (1.2.27)

> Stolo subridens: dicam – inquit – eisdem quibus ille verbis scripsit (vel Tarquennam audivi, cum homini pedes dolere coepissent, qui tui meminisset, ei mederi posse) :

<a id="rn_s000127_01"></a>
**RN_S000127_01** · Tarquennam (15) · Syntax;Textual

Tarquennam (15) is the accusative subject of posse (30) in an accusative-and-infinitive after audivi (16): 'or [in which] I heard Tarquenna say that ... he could heal him'. Heurgon's punctuation, which isolates vel Tarquennam audivi and makes Tarquenna only the oral source, is not followed.

Neither punctuation is transmitted. Heurgon's dashes (recorded as Variant on 13 and 17) detach Tarquennam from posse and require recovering the subject across a parenthesis; the AcI reading licenses the accusative directly. The Loeb translation ('heard Tarquenna say that') reads the same way.

<sub>Tokens: Tarquennam (15), audivi (16), posse (30) · Sources: Heurgon, Latin text; Loeb Classical Library, Cato and Varro: On Agriculture (LCL 283) -- tr. W. D. Hooper, rev. Harrison Boyd Ash, 1934</sub>

<a id="rn_s000127_02"></a>
**RN_S000127_02** · tui (25) · Textual;Interpretation

Transmitted tui (25) is kept against Heurgon's conjecture sui (Variant on 25). It is difficult but intelligible as an anticipatory shift into the second-person frame of the charm that follows (ego tui memini, S000128).

sui would make the patient concentrate on Tarquenna; tui anticipates the addressee of the incantation.

<sub>Sources: Heurgon, Latin text</sub>

## S000128 (1.2.27)

> “ego tui memini, medere meis pedibus, terra pestem teneto, salus hic maneto in meis pedibus”.

<a id="rn_s000128_01"></a>
**RN_S000128_01** · medere (6) · Syntax

medere (6) is parataxis on memini (4), not a conjunct: the charm moves from a first-person assertion (ego tui memini) to a second-person invocation, a speech-act boundary.

The three imperatives medere, teneto (12) and maneto (16) form one directive chain, so teneto and maneto coordinate under medere.

<sub>Tokens: memini (4), medere (6)</sub>

<a id="rn_s000128_02"></a>
**RN_S000128_02** · terra (10) · Syntax;Morphology;Interpretation

The syncretic terra (10) is nominative, subject of teneto (12): 'let the earth hold the illness', parallel to salus hic maneto 'let health remain here'. Both future imperatives are third person.

An ablative terra would leave teneto with an unexpressed second-person subject and break the parallel with salus (14). Heurgon's discussion of the ritual supports transfer of the ailment to the earth, and his translation makes the earth the subject (« que la terre retienne le mal »).

<sub>Tokens: terra (10), teneto (12), salus (14), maneto (16) · Sources: Heurgon, commentary; Heurgon, French translation</sub>

<a id="rn_s000128_03"></a>
**RN_S000128_03** · in (17) · Textual

Giusta regards the final in meis pedibus (17-19) as a gloss on hic (15), on rhythmic grounds, and would delete it (Variant=Giusta:- on each token). The phrase is kept: it is transmitted and coherently specifies locative hic.

<sub>Tokens: hic (15), in (17), meis (18), pedibus (19) · Sources: Giusta, apparatus and notes</sub>

## S000129 (1.2.27)

> hoc ter noviens cantare iubet, terram tangere, despuere, ieiunum cantare.

<a id="rn_s000129_01"></a>
**RN_S000129_01** · noviens (3) · Lexicon;Interpretation

ter noviens (2-3) is the ritual count 'three times nine', i.e. twenty-seven repetitions; noviens is the numeral adverb 'nine times'.

Heurgon's commentary identifies the 3 x 9 ritual repetition.

<sub>Tokens: ter (2), noviens (3) · Sources: Heurgon, commentary</sub>

<a id="rn_s000129_02"></a>
**RN_S000129_02** · ieiunum (12) · Syntax;Textual

ieiunum (12) is a depictive on the final cantare (13), 'chant while fasting', describing the understood performer. Giusta would move it before the first cantare (4), explaining the transmitted position as a misplaced scribal restoration; the transmitted order is kept.

No manuscript support is cited for the transposition, and ieiunum cantare is grammatical as transmitted and printed by Heurgon.

<sub>Tokens: cantare (4), ieiunum (12), cantare (13) · Sources: Giusta, apparatus and notes; Heurgon, Latin text</sub>

## S000130 (1.2.28)

> multa – inquam – item alia miracula apud Sasernas invenies, quae omnia sunt diversa ab agri cultura et ideo repudianda.

<a id="rn_s000130_01"></a>
**RN_S000130_01** · sentence · Textual;Interpretation

Speakers are assigned as Varro (S000130) and Stolo (S000131): Varro dismisses the Saserna marvels as irrelevant to agriculture, and Stolo counters that other writers contain the same kind of material. Giusta reverses the speakers (VariantStructure on both sentences).

Giusta takes the first inquam (3) as an anticipation of the following reporting verb and deletes it, which reverses the attribution. The transmitted allocation is contextually stronger and is the one Heurgon's translation follows.

<sub>Sources: Giusta, apparatus and notes; Heurgon, French translation · See also: [RN_S000131_01](#rn_s000131_01)</sub>

## S000131 (1.2.28)

> quasi vero – inquit – non apud ceteros quoque scriptores talia reperiantur.

<a id="rn_s000131_01"></a>
**RN_S000131_01** · sentence · Textual;Interpretation

Same as [RN_S000130_01](#rn_s000130_01).

## S000132 (1.2.28)

> an non in magni illius Catonis libro, qui de agri cultura est editus, scripta sunt permulta similia, ut haec, quem ad modum placentam facere oporteat, quo pacto libum, qua ratione pernas sallere?

<a id="rn_s000132_01"></a>
**RN_S000132_01** · haec (22) · Syntax;Morphology

In the elliptical comparative ut haec (22), haec is nominative plural, 'as these [are written]', matching the passive subject similia (19) of scripta sunt (16), not an accusative.

haec also points forward to the three interrogative examples that follow (SyntaxNote=Prolepsis:Cataphoric).

<sub>Tokens: scripta (16), similia (19), haec (22)</sub>

## S000133 (1.2.28)

> illud non dicis – inquit Agrius – quod scribit, “si velis in convivio multum bibere cenareque libenter, ante esse oportet brassicam crudam ex aceto aliqua folia quinque”.

<a id="rn_s000133_01"></a>
**RN_S000133_01** · esse (23) · Morphology;Lexicon

esse (23) is the infinitive of edo 'eat', not of sum: it governs the accusative brassicam (25), and the passage is Cato's prescription to eat raw cabbage before a banquet.

Heurgon's commentary quotes the Cato passage.

<sub>Tokens: esse (23), brassicam (25) · Sources: Heurgon, commentary</sub>

<a id="rn_s000133_02"></a>
**RN_S000133_02** · folia (30) · Syntax;Textual

aliqua folia quinque (29-31) is taken as an appositional quantity specification of brassicam (25), 'about five leaves'. Giusta suspects a loss before aliqua (at least a conjunction, possibly more; VariantStructure=Giusta:lacuna_before_29).

No exact supplement is recoverable, so the transmitted compressed phrase is analysed as it stands, without an empty node or inserted token.

<sub>Tokens: brassicam (25), aliqua (29), folia (30), quinque (31) · Sources: Giusta, apparatus and notes</sub>

## S000134 (1.3.1)

> igitur – inquit Agrasius – quae diiungenda essent a cultura cuius modi sint, quoniam discretum, de iis rebus quae scientia sit in colendo nos docete, ars id an quid aliud, et a quibus carceribus decurrat ad metas.

<a id="rn_s000134_01"></a>
**RN_S000134_01** · quae (6) · Syntax;Textual

The opening is a threefold nested anastrophe: the relative clause quae diiungenda essent a cultura (6-10) is the subject of the postponed question cuius modi sint (11-13), which is in turn the clausal subject of the postponed quoniam discretum (15-16). quae (6), cuius (11) and quoniam (15) carry SyntaxNote=Anastrophe.

Laughton (1960, 5) cites this passage for 'threefold anastrophe (cuiusmodi, quoniam, quae)', noting that the relative clause preceding cuiusmodi belongs to the interrogative clause preceding quoniam. cuius modi sint is therefore a full copular clause in subject function (modi csubj:pass on discretum), not an adnominal modifier. quae (21) is outside the nested complex.

<sub>Tokens: quae (6), cuius (11), quoniam (15) · Sources: Laughton 1960, Observations on the Style of Varro; Giusta, apparatus and notes</sub>

<a id="rn_s000134_02"></a>
**RN_S000134_02** · ars (29) · Syntax;Textual

ars id an quid aliud (29-33) has an elided subjunctive copula (sc. sit): ars is the predicate nominal and id (30) its subject. The clause is not treated as corrupt; Giusta's ars <s>it (Variant on 30) is not adopted.

Laughton (1960, 10) lists this clause among the few instances of subjunctive-copula ellipsis in Varro, a rare type, which is why it is recorded here rather than normalised.

<sub>Tokens: ars (29), id (30) · Sources: Laughton 1960, Observations on the Style of Varro; Giusta, apparatus and notes</sub>

<a id="rn_s000134_03"></a>
**RN_S000134_03** · id (30) · Interpretation

id (30) resumes the neuter gerund colendo (25), not scientia (22).

Laughton (1960, 16-17) argues against Heidrich that id cannot refer to feminine scientia (which would require ea) and takes it as resuming colendo.

<sub>Tokens: scientia (22), colendo (25), id (30) · Sources: Laughton 1960, Observations on the Style of Varro</sub>

## S000135 (1.3.1)

> Stolo cum aspexisset Scrofam: tu – inquit – et aetate et honore et scientia quod praestas, dicere debes.

<a id="rn_s000135_01"></a>
**RN_S000135_01** · quod (16) · Syntax;Interpretation

quod (16) is the causal conjunction 'since', postponed after the ablatives of respect (SyntaxNote=Anastrophe), not a relative pronoun object of praestas (17).

Heurgon renders the clause with « puisque tu l'emportes », an unambiguously causal reading.

<sub>Tokens: quod (16), praestas (17) · Sources: Heurgon, French translation</sub>

## S000137 (1.3.1)

> eaque est scientia, quae sint in quoque agro serenda ac facienda, quo terra maximos perpetuo reddat fructus.

<a id="rn_s000137_01"></a>
**RN_S000137_01** · serenda (11) · Syntax

quae ... serenda ac facienda (6-13) is an indirect question complementing scientia (4), 'knowledge of what is to be sown and done', not a relative clause; serenda (11) is therefore acl, not acl:relcl.

quae (6) is interrogative: the clause states the content of the knowledge and has no coreferential nominal head. UD reserves acl:relcl for true relatives; an interrogative complement of a noun is plain acl. Compare S000170.

<sub>Tokens: scientia (4), quae (6), serenda (11)</sub>

<a id="rn_s000137_02"></a>
**RN_S000137_02** · quo (15) · Syntax;Textual

quo (15) is Keil's conjecture; the manuscripts are split (quae aqua F, que Am, quaeque n, quod f1) and none reads quo. It is analysed as a relative adverb 'by which means' introducing a relative clause of purpose (ADV, advmod), whose purpose scopes over serenda and facienda together.

quo as a purpose conjunction (= ut eo) requires a comparative in its clause (A&G: quo facilius persuaderet); maximos is superlative, so that construction does not apply. Attachment to agro (10) is rejected: Hooper and Ash ('in order that the land may regularly produce the largest crops') show the purpose governs the whole predication. Heurgon prints quaeque (his « et quelle terre produit ... »), and Giusta adds <ut>; both are recorded as Variant on quo.

<sub>Tokens: serenda (11), quo (15), reddat (19) · Sources: Giusta, apparatus and notes; Heurgon, Latin text; W.D. Hooper (trans.), rev. H.B. Ash, Varro: On Agriculture, Loeb Classical Library; Allen & Greenough</sub>

## S000138 (1.4.1)

> eius principia sunt eadem, quae mundi esse Ennius scribit, aqua, terra, anima et sol.

<a id="rn_s000138_01"></a>
**RN_S000138_01** · eius (1) · Interpretation

eius (1) refers to (agri) cultura (S000134), not to the nearer scientia (S000137) or ars (S000136).

Heurgon on 1.4.1: « Eius représente (agri) cultura, et non l'ars ou la scientia. »

<sub>Sources: Heurgon, commentary</sub>

## S000139 (1.4.1)

> haec enim cognoscenda, priusquam iacias semina, quod initium fructuum oritur.

<a id="rn_s000139_01"></a>
**RN_S000139_01** · quod (9) · Syntax

quod (9) shows relative attraction (SyntaxNote=RelativeAttraction): it takes the gender and number of the predicate noun initium (10) in its own clause, while its antecedent is semina (7). oritur (12) is therefore a relative clause on semina, 'the seeds, which arise as the beginning of the crops'.

Heurgon on 1.4.1 notes the agreement of the relative with the predicate initium. semina is Neut Plur, quod Neut Sing: the mismatch is the signature of attraction. haec (1) is not a plausible antecedent (it denotes the things to be learned, not what springs up), and attaching the clause to cognoscenda gives an implausible reading.

<sub>Tokens: semina (7), quod (9), initium (10), oritur (12) · Sources: Heurgon, commentary · See also: [RN_S000139_02](#rn_s000139_02)</sub>

<a id="rn_s000139_02"></a>
**RN_S000139_02** · initium (10) · Syntax

initium (10) is a secondary predicate of quod (9), 'which arises as the beginning of the crops', attached to oritur (12); nothing is elided in the clause. quod initium is not read as one relative phrase ('which beginning').

A fused quod initium would require a connective-relative phrase, a pattern otherwise found only unit-initially; Heurgon's « qui se lève comme le commencement des fruits » keeps two roles, a relative subject and a separate predicate.

<sub>Tokens: quod (9), initium (10), oritur (12) · Sources: Heurgon, French translation · See also: [RN_S000139_01](#rn_s000139_01)</sub>

## S000142 (1.4.1)

> priores partes agit quod utile est, quam quod delectat.

<a id="rn_s000142_01"></a>
**RN_S000142_01** · delectat (10) · Syntax

delectat (10) attaches as advcl:cmp to utile (5), not to agit (3): the comparison is between the two free relatives quod utile est and quod delectat, competing for the same predicate priores partes agit.

Compare S000001, where the comparative clause attaches to the compared predicate element rather than to the main verb.

<sub>Tokens: agit (3), utile (5), delectat (10)</sub>

## S000143 (1.4.2)

> nec non ea, quae faciunt cultura honestiorem agrum, pleraque non solum fructuosiorem eadem faciunt, ut cum in ordinem sunt consita arbusta atque oliveta, sed etiam vendibiliorem atque adiciunt ad fundi pretium.

<a id="rn_s000143_01"></a>
**RN_S000143_01** · eadem (15) · Syntax

eadem (15) is taken as the object of faciunt (16), paralleling honestiorem agrum in the relative clause: fructuosiorem (14) + eadem + faciunt. It is not a long-distance determiner of ea (3), whose determiner slot is taken by pleraque (11).

Neuter nominative/accusative syncretism allows the accusative reading. It is not treated as case-syncretic sharing: the subject is already supplied by ea ... pleraque.

<sub>Tokens: ea (3), pleraque (11), fructuosiorem (14), eadem (15), faciunt (16)</sub>

## S000144 (1.4.2)

> nemo enim eadem utilitati non formosius quod est emere mavult pluris, quam si est fructuosus turpis.

<a id="rn_s000144_01"></a>
**RN_S000144_01** · utilitati (4) · Morphology;Interpretation

utilitati (4) is an archaic i-stem ablative, not a dative: eadem utilitati is one ablative phrase, 'at equal value'.

Heurgon on 1.4.2 glosses utilitati as an archaic ablative in -i, citing hereditati (1.12.2), conualli (1.12.3) and parti (1.13.5).

<sub>Tokens: eadem (3), utilitati (4) · Sources: Heurgon, commentary</sub>

<a id="rn_s000144_02"></a>
**RN_S000144_02** · turpis (17) · Syntax;Interpretation

fructuosus turpis (16-17) are asyndetically coordinated predicate adjectives sharing est, 'fruitful [but] ugly'. Reading turpis as a backgrounded secondary predicate ('fruitful while being ugly') is possible, but nothing in the context favours weighting one quality below the other.

There is no emphasis marker, and Giusta's apparatus treats both adjectives alike (neuter comparatives fructuosius, turpius), giving no asymmetry either.

<sub>Tokens: fructuosus (16), turpis (17) · Sources: Giusta, apparatus and notes</sub>

## S000147 (1.4.3)

> etenim ubi ratio cum Orco habetur, ibi non modo fructus est incertus, sed etiam colentium vita.

<a id="rn_s000147_01"></a>
**RN_S000147_01** · Orco (5) · Lexicon;Interpretation

Orco (5) is the god Orcus (PROPN): ratio cum Orco habetur 'the reckoning is held with Orcus', i.e. where death is at stake. The transmitted lower-case orco is kept in OrigForm.

Heurgon's commentary identifies Orcus as the Latin god of death, of Etruscan origin, assimilated to Pluto, and his text prints Orco with a capital. The rare common noun orcus is not a plausible reading here.

<sub>Sources: Heurgon, commentary; Heurgon, Latin text</sub>

<a id="rn_s000147_02"></a>
**RN_S000147_02** · vita (18) · Syntax

No SyntaxNote=LooseAgreement: in non modo fructus est incertus, sed etiam colentium vita, the masculine predicate incertus (13) agrees with the nearer subject fructus (11) and is understood with the feminine vita (18) as well.

Agreement of a shared predicate with the nearest of differently gendered coordinated subjects is ordinary Latin usage, not a deviation from an overt controller.

<sub>Tokens: fructus (11), incertus (13), vita (18)</sub>

## S000148 (1.4.3)

> quare ubi salubritas non est, cultura non aliud est atque alea domini vitae ac rei familiaris.

<a id="rn_s000148_01"></a>
**RN_S000148_01** · atque (11) · Syntax

atque (11) after non aliud means 'than': it introduces the comparandum alea (12), so it is SCONJ/mark and alea is advcl:cmp on aliud (9), not a coordinated conjunct.

Allen & Greenough §406 n. d: after alius, formal prose uses ac (atque), et, more rarely nisi or quam. alea is nominative like aliud, both predicate nominatives under est (10). ac (15) is ordinary coordination.

<sub>Tokens: aliud (9), atque (11), alea (12) · Sources: Allen & Greenough §406</sub>

## S000149 (1.4.4)

> nec haec non deminuitur scientia.

<a id="rn_s000149_01"></a>
**RN_S000149_01** · nec (1) · Syntax;Interpretation

nec ... non (1, 3) is the idiom nec non 'and also, moreover', not a compositional double negation; both tokens carry SyntaxNote=FixedExpression and keep their ordinary attachments to deminuitur (4).

Gaffiot (nec II.4.b) glosses nec non = « et aussi », citing Varro RR 3.2.14 and nec non etiam at RR 1.1.6, 2.10.9, 3.16.26. Heurgon (« D'ailleurs la science peut diminuer le risque ») and Hooper and Ash ('and yet') both render it affirmatively. Attaching nec to non was rejected: neither word licenses the other, the meaning arises from the pair jointly.

<sub>Tokens: nec (1), non (3) · Sources: Felix Gaffiot, Dictionnaire Illustre Latin-Francais; Heurgon, French translation; W.D. Hooper (trans.), rev. H.B. Ash, Varro: On Agriculture, Loeb Classical Library</sub>

## S000150 (1.4.4)

> ita enim salubritas, quae ducitur e caelo ac terra, non est in nostra potestate, sed in naturae, ut tamen multum sit in nobis, quo graviora quae sunt ea diligentia leviora facere possimus.

<a id="rn_s000150_01"></a>
**RN_S000150_01** · naturae (20) · Syntax

In sed in naturae, the genitive naturae (20) stands for a repeated potestate: 'not in our power but in nature's [power]'. It takes the place of the omitted noun as conj on potestate (16), despite the case mismatch, with SyntaxNote=Ellipsis.

in (19) governs the ablative of the unexpressed potestate, not naturae; in and sed attach to naturae as the promoted conjunct, so nothing lacks a governor and no empty node or orphan is needed. The case mismatch between the conjuncts is the visible trace of the omission.

<sub>Tokens: potestate (16), in (19), naturae (20) · See also: [RN_S000150_02](#rn_s000150_02)</sub>

<a id="rn_s000150_02"></a>
**RN_S000150_02** · ut (22) · Interpretation;Translation

ita ... ut tamen (1, 22-23) is read as a concessive bridge, 'indeed not in our power but in nature's, yet even so much lies in us', not as a strict consequence 'so ... that'. The basic advcl is unaffected.

ut carries little independent weight beside tamen; a result reading would overstate the logical claim.

<sub>Tokens: ita (1), ut (22), tamen (23)</sub>

## S000151 (1.4.4)

> etenim si propter terram aut aquam odore, quem aliquo loco eructat, pestilentior est fundus, aut propter caeli regionem ager calidior sit, aut ventus non bonus flet, haec vitia emendari solent domini scientia ac sumptu, quod permagni interest, ube sint positae villae, quantae sint, quo spectent porticibus, ostiis ac fenestris.

<a id="rn_s000151_01"></a>
**RN_S000151_01** · terram (4) · Syntax;Interpretation

terram aut aquam (4-6) modifies odore (7): 'a smell near the land or water', not two causes parallel to the smell.

<sub>Tokens: terram (4), aquam (6), odore (7)</sub>

<a id="rn_s000151_02"></a>
**RN_S000151_02** · odore (7) · Textual

odore (7) is Keil's conjecture; the manuscripts read odorem. Giusta keeps odorem and emends quem (9) to quae (a postponed relative), a package recorded as Variant on both tokens. Since both readings need an emendation, the received text is kept.

Heurgon's apparatus shows odorem codd.; quem has no apparatus entry. Giusta thus replaces Keil's single-word conjecture with one of his own (quae) to make odorem construable.

<sub>Tokens: odore (7), quem (9) · Sources: Giusta, apparatus and notes; Heurgon, Latin text; Keil, Teubner edition of Varro, Res Rusticae</sub>

<a id="rn_s000151_03"></a>
**RN_S000151_03** · eructat (12) · Interpretation

The implicit subject of eructat (12) is fundus (16), the estate, not terra or aqua.

So Heurgon's commentary.

<sub>Tokens: eructat (12), fundus (16) · Sources: Heurgon, commentary</sub>

<a id="rn_s000151_04"></a>
**RN_S000151_04** · flet (30) · Morphology;Lexicon

flet (30) is taken as an archaic or dialectal -e- present of flo 'blow' (the verb ventus normally takes), not fleo 'weep', which gives the implausible 'a wind that is not good weeps'. The transmitted form is kept.

Heurgon's apparatus records no rival reading. Compare uerget for uergit at 1.6.6, also retained (Heurgon's commentary).

<sub>Tokens: ventus (27), flet (30) · Sources: Heurgon, Latin text; Heurgon, commentary</sub>

<a id="rn_s000151_05"></a>
**RN_S000151_05** · quod (41) · Syntax

quod (41) is the causal conjunction 'because', not a resumptive relative ('which matters a great deal'). intersum takes one subject expression, and that slot is filled by the indirect questions ube ... positae (47) etc.

A resumptive quod (A&G §304d) was considered, but Georges, Gaffiot and Lewis and Short give intersum a genitive of the thing concerned plus a single subject (indirect question, ut/ne clause, infinitive), not two; compare L&S's quid illius interest, ubi sis?

<sub>Tokens: quod (41), interest (43), positae (47) · Sources: Lewis & Short, A Latin Dictionary; Felix Gaffiot, Dictionnaire Illustre Latin-Francais; Georges; Allen & Greenough §304</sub>

<a id="rn_s000151_06"></a>
**RN_S000151_06** · ube (45) · Morphology

ube (45) is an archaic form of ubi (Variant=Archaic).

Heurgon on 1.4.4 cites Republican inscriptional parallels ubei, tibei, sibei.

<sub>Sources: Heurgon, commentary</sub>

## S000153 (1.4.5)

> sed quid ego illum voco ad testimonium?

<a id="rn_s000153_01"></a>
**RN_S000153_01** · quid (2) · Syntax;Lexicon

quid (2) is the adverbial accusative 'why' (advmod on voco), not the object: illum (4) already fills voco's object slot. As an adverb of cause it is tagged ADV (PronType=Int), as in the UD Latin treebanks.

Allen & Greenough list quid 'why' among neuter accusatives used adverbially, with the parallel Quid moror? 'Why do I delay?'

<sub>Tokens: quid (2), illum (4), voco (5) · Sources: Allen & Greenough (via Dickinson College Commentaries), Cognate/Adverbial Accusative</sub>

## S000155 (1.5.1)

> sed quoniam agri culturae quod esset initium et finis dixi, relinquitur quot partes ea disciplina habeat ut sit videndum.

<a id="rn_s000155_01"></a>
**RN_S000155_01** · initium (7) · Syntax

In the indirect question quod esset initium et finis, initium (7) with finis (9) is taken as the predicate and quod (5) as the subject.

This follows SUM001: the head is the predicate ascribed, the nsubj the entity it is ascribed to, as in 'the parts are four'. No claim is made about what quod refers back to.

<sub>Tokens: quod (5), initium (7), finis (9)</sub>

## S000157 (1.5.2)

> Stolo: isti – inquit – libri non tam idonei iis qui agrum colere volunt, quam qui scholas philosophorum;

<a id="rn_s000157_01"></a>
**RN_S000157_01** ·  (18.1) · Syntax;Enhanced;Interpretation

The gapped clause quam qui scholas philosophorum repeats [colere volunt]: Stolo puns on colere, cultivating land and cultivating the schools of the philosophers. The empty node 18.1 stands for the whole elided chain and has no FORM.

No single form or lemma can represent the collapsed volunt + colere; InheritedFrom lists iis (11), volunt (15) and colere (14). A separate repetition of iis (quam [iis] qui ...) is implied by the comparison and not reconstructed. The translations repeat the cultivation verb to keep the pun.

<sub>Tokens: colere (14), qui (18),  (18.1), scholas (19)</sub>

## S000158 (1.5.2)

> neque eo dico, quo non habeant et utilia et communia quaedam.

<a id="rn_s000158_01"></a>
**RN_S000158_01** · eo (2) · Syntax;Lexicon

neque eo ... quo (2, 5) is the idiom 'nor do I say this for the reason that', a litotes: Stolo does not deny that the books have useful points. eo is the adverb 'for that reason', not an ablative pronoun, and quo is the matching causal relative adverb, not a relative clause on eo.

Lewis and Short, eo B.2.β, cite neque eo ... quo from Cic. Att. 3.15.4, almost verbatim. With eo an adverb there is no nominal antecedent for a relative-clause reading of quo non habeant (7).

<sub>Tokens: eo (2), quo (5), habeant (7) · Sources: Lewis & Short, A Latin Dictionary</sub>

<a id="rn_s000158_02"></a>
**RN_S000158_02** · communia (11) · Interpretation;Translation

communia (11) can mean generally 'shared, of general interest' or specifically 'common to both' pursuits (farming and philosophy). Both readings are available; the English and Finnish translations keep the general sense, the French follows Heurgon's « communes aux deux ».

Heurgon's French translates his own text, which reads quod for quo (5); the difference does not affect this point. Hooper and Ash: 'matter which is both profitable and of general interest'.

<sub>Sources: Heurgon, French translation; W.D. Hooper (trans.), rev. H.B. Ash, Varro: On Agriculture, Loeb Classical Library · See also: [RN_S000158_01](#rn_s000158_01)</sub>

## S000161 (1.5.3)

> e quis prima cognitio fundi, solum partesque eius quales sint;

<a id="rn_s000161_01"></a>
**RN_S000161_01** · prima (3) · Syntax

prima (3) stands for an elided pars, resuming the quattuor partes of S000160, and is the subject; cognitio fundi is the predicate ('of which the first [part] is knowledge of the farm'), not a noun modified by prima ('first knowledge'). The partitive e quis (2) therefore depends on prima, not on cognitio.

Ordinals are regularly used absolutely ('the first, the second [one]'), and e quis makes the elided pars explicit; prima takes the relation of the elided noun and keeps UPOS ADJ. This is substantivization, not gapping: no coordination is involved, so no orphan or empty node applies. The direction (ordinal as subject, content as predicate) is the same in the parallel items secunda, tertia, quarta (S000162-S000164); prima has plain nsubj because cognitio has no subject of its own, whereas those clauses do and take nsubj:outer. As a partitive of a nominal, quis is nmod.

<sub>Tokens: quis (2), prima (3) · See also: [RN_S000162_01](#rn_s000162_01)</sub>

## S000162 (1.5.3)

> secunda, quae in eo fundo opus sint ac debeant esse culturae causa;

<a id="rn_s000162_01"></a>
**RN_S000162_01** · secunda (1) · Syntax

secunda (1) (sc. pars) is the outer subject of the indirect question quae ... opus sint ac debeant esse, which gives the content of the second part and heads the sentence; the copula linking them is not expressed.

quae (3) is interrogative: the clause is an indirect question ('[the second part is] which things are needed'), not a free relative. Making secunda the root with the clause as its clausal subject is rejected: as with quod est 'Romanus sedendo vincit' at S000042 (quod nsubj:outer and est cop:outer of vincit), the outer subject attaches to the root of the clause that identifies it. secunda takes nsubj:outer because the clause has its own subject, quae. The same analysis applies to tertia, quarta and pars at S000163, S000164, S000167 and S000168.

<sub>Tokens: secunda (1), quae (3), opus (7) · See also: [RN_S000161_01](#rn_s000161_01)</sub>

<a id="rn_s000162_02"></a>
**RN_S000162_02** · esse (11) · Syntax

esse (11) is the copula of a gapped opus: ac debeant [opus] esse repeats the idiom opus esse 'to be needed' from the first conjunct (quae ... opus sint), so esse is AUX and carries SyntaxNote=Ellipsis.

An existential reading ('what must exist there') is set aside: in this sentence in eo fundo and culturae causa attach to opus, shared by both conjuncts, so esse has no predicate within its own clause other than the gapped opus. Contrast S000166 (in fundo debent esse), which has no opus and where fundo itself is the predicate of esse.

<sub>Tokens: opus (7), esse (11) · See also: [RN_S000166_01](#rn_s000166_01)</sub>

<a id="rn_s000162_03"></a>
**RN_S000162_03** · causa (13) · Syntax

culturae causa (13) depends on opus (7) and scopes over both conjuncts ('what is needed and must be there, for the sake of cultivation'), not only over the nearer debeant esse.

Nothing restricts the purpose phrase to the second conjunct.

## S000163 (1.5.3)

> tertia, quae in eo praedio colendi causa sint facienda;

<a id="rn_s000163_01"></a>
**RN_S000163_01** · colendi (7) · Syntax

The genitive gerund colendi (7) is nmod of causa (8) in colendi causa 'for the sake of cultivating', not acl, although its UPOS is VERB.

The same construction is annotated nmod at S000117 (obstrigillandi causa).

<sub>Tokens: colendi (7), causa (8)</sub>

## S000165 (1.5.4)

> de his quattuor generalibus partibus singulae minimum in binas dividuntur species, quod habet prima ea quae ad solum pertinent terrae et quae ad villas et stabula.

<a id="rn_s000165_01"></a>
**RN_S000165_01** · quod (13) · Interpretation

quod (13) is explicative ('in that'): the clause spells out the division just stated by naming the two species of the first part (matters of the soil, matters of buildings and stalls). It does not give a reason ('because') for the division.

<sub>Tokens: quod (13), habet (14)</sub>

<a id="rn_s000165_02"></a>
**RN_S000165_02** · prima (15) · Textual;Interpretation

prima (15) resumes pars (the first of the four parts), and ea (16) refers to the two species just announced; the transmitted neuter plural ea is kept although species is feminine.

Heurgon (comm. on 1.5.4) prints prima eam quae ad solum pertinet terrae et alteram quae ad villas et stabula, with eam and alteram agreeing with an understood speciem, against the transmitted ea ... et quae; his note: 'prima reprend pars, et eam et alteram sont les deux species annoncées'. With ea the reference to the species is grammatically looser but the sense is the same; the translations render it 'those [things]'. Heurgon's reading is recorded as Variant=Heurgon:eam.

<sub>Tokens: prima (15), ea (16) · Sources: Heurgon, Latin text; Heurgon, commentary</sub>

## S000166 (1.5.4)

> secunda pars, quae moventur atque in fundo debent esse culturae causa, est item bipertita, de hominibus, per quos colendum, et de reliquo instrumento.

<a id="rn_s000166_01"></a>
**RN_S000166_01** · fundo (8) · Syntax;Morphology

in fundo (8) is the predicate of esse (10) ('[the things] which must be on the farm'): esse is a copula (AUX, cop of fundo), and culturae causa (12) depends on fundo. esse is not an existential verb.

The locative phrase ascribes a location to the subject (a locational predicate in Stassen's sense), as ubi does in ubi salubritas non est (S000148), where ubi heads the clause and est is its copula. Under SUM001 an existential reading of esse is adopted only when no predicate can be found. Unlike S000162 (quae opus sint ac debeant esse), this sentence has no opus to supply by gapping: its first conjunct is quae moventur.

<sub>Tokens: fundo (8), esse (10), causa (12) · Sources: Stassen, Leon (1997). Intransitive Predication. Oxford Studies in Typology and Linguistic Theory. Oxford: Clarendon Press. · See also: [RN_S000162_02](#rn_s000162_02)</sub>

## S000167 (1.5.4)

> tertia pars quae de rebus dividitur, quae ad quamque rem sint praeparanda et ubi quaeque facienda.

<a id="rn_s000167_01"></a>
**RN_S000167_01** · de (4) · Textual

Giusta (I 5,4) proposes quae <est> de rebus (Variant=Giusta:est+ on de (4)); the transmitted text is kept, with quae (3) as subject of dividitur (6) in a relative clause on pars.

Giusta holds that the first quae lacks a verb and weighs two remedies: deleting it (Keil) or inserting est after it. She prefers the insertion as simpler, and because ad quamque rem in the next clause lacks faciendum, which tells against the res ... facienda construal that would motivate the deletion. The transmitted sequence construes as it stands: 'the third part, which is divided as regards the equipment, [is] what must be prepared for each task'.

<sub>Tokens: quae (3), de (4) · Sources: Giusta, apparatus and notes</sub>

<a id="rn_s000167_02"></a>
**RN_S000167_02** · praeparanda (13) · Syntax

The two quae-clauses differ: quae de rebus dividitur is an ordinary relative clause on pars (quae (3) relative), while quae ... sint praeparanda is an indirect question (quae (8) interrogative) that gives the content of the third part; it heads the sentence, with pars (2) as its outer subject.

The second clause is the construction of S000162-S000164 (ordinal or pars + content clause); it has its own subject quae (8), hence nsubj:outer on pars. The first clause describes pars as a noun and does not state its content, so it stays attached to pars.

<sub>Tokens: pars (2), quae (3), quae (8), praeparanda (13) · See also: [RN_S000162_01](#rn_s000162_01), [RN_S000167_01](#rn_s000167_01)</sub>

## S000169 (1.5.4)

> de primis quattuor partibus prius dicam, deinde subtilius de octo secundis.

<a id="rn_s000169_01"></a>
**RN_S000169_01** · dicam (6) · Textual

Giusta (I 5,4) posits a small lacuna before dicam (6), to be filled with something like dixi summatim (Variant=Giusta:dixi_summatim+); the transmitted sentence is complete and is kept.

She prefers this local lacuna to the larger one some editors place between chapters 5 and 6, because the order Varro announces here (the four first parts first, then the eight secondary ones) is not obviously followed in chapters 6-17. The proposal concerns the plan of the work, not the construction of this sentence.

<sub>Sources: Giusta, apparatus and notes</sub>

## S000170 (1.6.1)

> igitur primum de solo fundi videndum haec quattuor, quae sit forma, quo in genere terrae, quantus, quam per se tutus.

<a id="rn_s000170_01"></a>
**RN_S000170_01** · solo (4) · Lexicon

solo (4) is the noun solum 'soil' ('concerning the soil of the farm'), not the adjective solus 'alone'.

Heurgon translates le sol de la propriété.

<sub>Sources: Heurgon, French translation</sub>

<a id="rn_s000170_02"></a>
**RN_S000170_02** · forma (12) · Syntax

In quae sit forma the noun forma (12) heads the clause and quae (10) is its subject, so that each of the four items announced by haec quattuor is headed by its content word: forma, genere (16), quantus (19), tutus (24).

In the other items the interrogative depends on the content word (quo det of genere, quam advmod of tutus) or is itself that word (quantus); item 1 is annotated the same way. Giusta (I 5,4) notes that quo in genere terrae, quantus, quam per se tutus imply sit fundus; masculine quantus and tutus agree with fundus, not with forma, so all four items answer to the same understood referent. Giusta also reports Keil's quale for quae and is surprised that Goetz restored quae.

<sub>Tokens: quae (10), forma (12), genere (16), quantus (19), tutus (24) · Sources: Giusta, apparatus and notes</sub>

## S000171 (1.6.1)

> formae cum duo genera sint, una quam natura dat, altera quam sationes imponunt, prior, quod alius ager bene natus, alius male, posterior, quod alius fundus bene consitus est, alius male, dicam prius de naturali.

<a id="rn_s000171_01"></a>
**RN_S000171_01** · formae (1) · Syntax;Morphology

formae (1) is nominative plural and the subject of the cum-clause, with genera (4) as predicate ('as shapes are of two kinds'); it is not a genitive singular dependent of genera. duo (3) modifies genera.

The appositive chain una (7), altera (12), prior (17), posterior (28) is feminine and cannot resume neuter genera; it resumes formae. cum (2) is the conjunction placed after formae (SyntaxNote=Anastrophe), not a preposition: nothing in the clause is ablative.

<sub>Tokens: formae (1), genera (4), una (7)</sub>

<a id="rn_s000171_02"></a>
**RN_S000171_02** · posterior (28) · Syntax

posterior (28) is coordinated with prior (17) rather than attached as an apposition to altera (12), which it resumes in sense.

prior is apposition to una (7); posterior, as the second conjunct, attaches to the first conjunct prior, so its link to altera is only implicit through the parallel. The asymmetry follows from the UD treatment of coordination.

<sub>Tokens: altera (12), prior (17), posterior (28)</sub>

## S000172 (1.6.2)

> igitur cum tria genera sint a specie simplicia agrorum, campestre, collinum, montanum, et ex iis tribus quartum, ut in eo fundo haec duo aut tria sint, ut multis locis licet videre, e quibus tribus fastigiis simplicibus sine dubio infimis alia cultura aptior quam summis, quod haec calidiora quam summa, sic collinis, quod ea tepidiora quam infima aut summa;

<a id="rn_s000172_01"></a>
**RN_S000172_01** · genera (4) · Syntax

In cum tria genera sint the noun genera (4) is the predicate and tria (3) modifies it, whereas in haec duo aut tria sint the numeral duo (28) is the predicate and haec (27) its subject.

In the first clause genera is the content noun that the numeral quantifies; in the second, haec is a contentless pronoun and the numeral is the only candidate for the predicate. Same analysis as duo genera at S000171.

<sub>Tokens: genera (4), duo (28) · See also: [RN_S000171_01](#rn_s000171_01)</sub>

<a id="rn_s000172_02"></a>
**RN_S000172_02** · et (17) · Textual

Giusta (I 6,2) reads est for et (17) (Variant=Giusta:est), making ex iis tribus quartum [est] a main clause. The transmitted et is kept: it coordinates quartum with genera inside the cum-clause, and the main clause is infimis alia cultura aptior (49).

Giusta argues that with et the period lacks a main clause ('il periodo manca della frase principale') and that est supplies one most simply. Giusta's own introduction describes her conjectures as speculative.

<sub>Sources: Giusta, apparatus and notes</sub>

<a id="rn_s000172_03"></a>
**RN_S000172_03** · quartum (21) · Interpretation

quartum (21) names a fourth, composite kind formed from the three simple ones; the following ut-clause (23) explains that composition ('in that on one farm two or three of them occur') and is not a purpose clause.

The fourth kind covers farms combining two of the simple types or all three. The explanatory reading of ut is supported by the indicative of the nearby parallel ut ... licet clause (36).

<sub>Tokens: quartum (21), ut (23) · See also: [RN_S000172_02](#rn_s000172_02)</sub>

<a id="rn_s000172_04"></a>
**RN_S000172_04** · ut (23) · Textual

Giusta reads temporal cum for ut (23) (Variant=Giusta:cum); the transmitted ut is kept.

She judges ut illogical here and made improbable by the second ut shortly after (ut multis locis licet videre), and calls cum markedly more Varronian than ubi in this use.

<sub>Sources: Giusta, apparatus and notes · See also: [RN_S000172_01](#rn_s000172_01)</sub>

<a id="rn_s000172_05"></a>
**RN_S000172_05** · eo (25) · Textual

Giusta corrects eo (25) to eo<dem> 'on that very farm' (Variant=Giusta:eodem); not adopted.

She calls the transmitted eo pointless (insulso) and prefers eodem as a simpler remedy than Keil's change of ubi to uno.

<sub>Sources: Giusta, apparatus and notes</sub>

## S000174 (1.6.3)

> itaque ubi lati campi, ibi magis aestus, et eo in Apulia loca calidiora ac graviora;

<a id="rn_s000174_01"></a>
**RN_S000174_01** · sentence · Segmentation;Textual

The transmitted period is divided after graviora: et ubi montana ... salubriora (S000174b) shares no dependents with the preceding clauses and is linked to them only at the level of the main predicates.

Heurgon's text also has a full stop here (Variant=Heurgon:. on token 18). Token 18 is printed as a semicolon, the punctuation this passage uses between major coordinate clauses; the transmitted comma is kept in OrigForm.

<sub>Sources: Heurgon, Latin text · See also: [RN_S000174b_04](#rn_s000174b_04)</sub>

<a id="rn_s000174_02"></a>
**RN_S000174_02** · lati (3) · Syntax

In ubi lati campi the adjective lati (3) is the predicate ('where the plains are wide') and campi (4) its subject; the ubi-clause is an adverbial relative clause of aestus (8), resumed by ibi (6).

A clausal subject is rejected. At S000151 (permagni interest, ubi sint positae villae) the ubi-clause fills the subject slot of interest, which has no other subject; here the correlative ibi ... ubi (same family as eo ... quo) fills the slot in the main clause, as in ubi ratio cum Orco habetur, ibi ... est incertus (S000147).

<sub>Tokens: lati (3), campi (4), ibi (6)</sub>

## S000174b (1.6.3)

> et ubi montana, ut in Vesuvio, quod leviora et ideo salubriora;

<a id="rn_s000174b_01"></a>
**RN_S000174b_01** · ut (5) · Textual

Giusta (I 6,2-3) supposes that lata has fallen out after montana (3), paralleling ubi lati campi in S000174 (Variant=Giusta:lata+ on ut (5)); not adopted.

<sub>Tokens: montana (3), ut (5) · Sources: Giusta, apparatus and notes</sub>

<a id="rn_s000174b_02"></a>
**RN_S000174b_02** · leviora (10) · Textual

Giusta supplies frigidior aer, loca before leviora (10) (Variant=Giusta:frigidior_aer,loca+); not adopted.

The transmitted quod leviora answers calidiora ac graviora of the plains (S000174) with a single comparative, leaving calidiora without a counterpart; the supplement restores the pair.

<sub>Sources: Giusta, apparatus and notes · See also: [RN_S000174b_04](#rn_s000174b_04)</sub>

<a id="rn_s000174b_03"></a>
**RN_S000174b_03** · leviora (10) · Interpretation

The understood subject of leviora (10) and salubriora (13) is loca, carried over from loca calidiora ac graviora in S000174, not aer 'air', which Heurgon and Hooper-Ash supply in their translations.

The translations render leviora as 'airier', keeping the atmospheric sense without adding a subject.

<sub>Tokens: leviora (10), salubriora (13) · Sources: Heurgon, French translation; W.D. Hooper (trans.), rev. H.B. Ash, Varro: On Agriculture, Loeb Classical Library</sub>

<a id="rn_s000174b_04"></a>
**RN_S000174b_04** · salubriora (13) · Syntax

salubriora (13), which carries ideo (12), is the main predicate; quod leviora (10) is its causal clause and ubi montana (3) an adverbial relative clause depending on it. The correlative ideo ... quod appears here in inverted order (quod ... et ideo).

Making montana the head, with leviora and salubriora subordinate to it, would put the reason marker quod on the clause that ideo marks as the consequence. ideo pairs with quod in either order (Logeion, s.v. ideo).

<sub>Tokens: montana (3), leviora (10), ideo (12), salubriora (13) · Sources: Logeion, s.v. ideo</sub>

## S000176 (1.6.3)

> verno tempore in campestribus maturius eadem illa seruntur quae in superioribus et celerius hic quam illic coguntur.

<a id="rn_s000176_01"></a>
**RN_S000176_01** · eadem (6) · Syntax

eadem (6) heads eadem illa, with illa (7) as its determiner, and the quae-clause depends on eadem: the correlative idem ... qui 'the same as' ('the same [crops] as [are sown] in the higher regions').

Same correlative at S000039 (eadem causa quae te) and S000138. Reading illa as an adverb 'there' (like hic and illic later in the sentence) is rejected: it would need an adverbial ablative singular illa instead of the neuter plural that agrees with eadem, and Heurgon renders illa as part of les mêmes. idem combines regularly with hic, iste, ille and ipse.

<sub>Tokens: eadem (6), illa (7), quae (9) · Sources: Heurgon, French translation</sub>

<a id="rn_s000176_02"></a>
**RN_S000176_02** · quae (9) · Textual

Heurgon reads quam 'than' for quae (9) (Variant=Heurgon:quam), which would parallel celerius hic quam illic; the relative quae is kept.

quae is printed in the LacusCurtius text (Loeb-derived), The Latin Library, Wikisource and ancienttexts.org; Heurgon is alone in reading quam.

<sub>Sources: Heurgon, Latin text; Heurgon, French translation; Original Varro RR source text, LacusCurtius / Penelope</sub>

## S000177 (1.6.3)

> nec non susum quam deorsum tardius seruntur ac metuntur.

<a id="rn_s000177_01"></a>
**RN_S000177_01** · nec (1) · Lexicon;Interpretation

nec non (1-2) is an emphatic affirmative connective ('and indeed, and also'), not a litotes ('nor is it otherwise').

Lewis & Short give nec non as a particle of emphatic affirmation ('and also, and yet, and in fact'), citing Varro RR 1.1.6 and 2.5.9 for this sense.

<sub>Tokens: nec (1), non (2) · Sources: Lewis & Short, A Latin Dictionary</sub>

<a id="rn_s000177_02"></a>
**RN_S000177_02** · deorsum (5) · Syntax

SyntaxNote=ClauseDisplaced on deorsum (5) marks the comparative quam deorsum, which depends on seruntur (7) but stands next to susum (3), the term it contrasts with.

This differs from the other uses of the tag (S000011, S000024), where a relative clause precedes its antecedent.

<sub>Tokens: susum (3), deorsum (5)</sub>

## S000178 (1.6.4)

> quaedam in montanis prolixiora nascuntur ac firmiora propter frigus, ut abietes ac sappini, hic, quod tepidiora, populi ac salices;

<a id="rn_s000178_01"></a>
**RN_S000178_01** · prolixiora (4) · Syntax;Lexicon

prolixiora (4) and firmiora (7) are secondary predicates of quaedam (1) with nascuntur (5) ('some grow taller and sturdier'), annotated advcl:pred rather than as xcomp complements of nascor.

Lewis & Short attest no construction of nascor with a resultative complement ('grow into X'): only purposive natus + dative or ad, and natus + adverb for natural quality (Varro's own alius ager bene natus, alius male, S000171). nascor does not require the complement, so the adjunct relation applies. The English 'grow taller' suggests a result, but the Finnish translation uses the essive (korkeampina), consistent with a depictive reading.

<sub>Tokens: quaedam (1), prolixiora (4), firmiora (7) · Sources: Lewis & Short, A Latin Dictionary</sub>

<a id="rn_s000178_02"></a>
**RN_S000178_02** · tepidiora (19) · Textual

Giusta (I 6,4) finds that populi ac salices lack a comparative predicate matching prolixiora ac firmiora of abietes ac sappini; she reads tepidior a<er> for tepidiora (19) (Variant=Giusta:tepidior_aer) and supplies humiliora et teneriora before populi (21) (Variant=Giusta:humiliora_et_teneriora+). Neither is adopted.

On her reading it is the air, not the trees, that is milder; the transmitted neuter plural tepidiora does not agree with feminine populi ac salices either, and is annotated as the predicate of the causal quod-clause. For the lost pair she hesitates between teneriora and tenuiora. In the transmitted text populi ac salices are the subject of a gapped nascuntur (21.1).

<sub>Tokens: tepidiora (19), populi (21) · Sources: Giusta, apparatus and notes</sub>

## S000179 (1.6.4)

> susum fertiliora, ut arbutus ac quercus, deorsum, ut nuces graecae ac mariscae fici.

<a id="rn_s000179_01"></a>
**RN_S000179_01** · fertiliora (2) · Interpretation

The understood subject of fertiliora (2) continues quaedam of S000178: some plants are more fruitful uphill, others downhill (deorsum (9)); the sentence does not describe the same trees in both zones.

The sentence has no verb; fertiliora is a bare predicate adjective.

<sub>Tokens: fertiliora (2), deorsum (9)</sub>

<a id="rn_s000179_02"></a>
**RN_S000179_02** · ut (4) · Interpretation

ut (4) and ut (11) introduce examples ('as with the arbutus and the oak') rather than a strict comparison, as ut does elsewhere in the passage (ut abietes ac sappini, S000178; ut in Vesuvio, S000174b).

<sub>Tokens: ut (4), ut (11)</sub>

<a id="rn_s000179_03"></a>
**RN_S000179_03** · ut (11) · Textual

Giusta (I 6,4) supposes that a comparative such as suauiora has fallen out before ut nuces (Variant=Giusta:suauiora+ on ut (11)), since nothing in the deorsum clause answers fertiliora. Not adopted: deorsum (9) stands for a gapped fertiliora (9.1).

<sub>Tokens: deorsum (9), ut (11) · Sources: Giusta, apparatus and notes · See also: [RN_S000178_02](#rn_s000178_02)</sub>

## S000180 (1.6.4)

> in collibus humilibus societas maior cum campestri fructu quam cum montano, in altis contra.

<a id="rn_s000180_01"></a>
**RN_S000180_01** · contra (15) · Syntax

contra (15) is a predicate in its own right ('on high hills, the opposite'), coordinated with maior (5), and in altis (14) is its locative; the clause is not a gapped repetition of maior with contra as a leftover.

contra is used predicatively (the res se habet contra type), so no orphan or empty node is needed.

<sub>Tokens: altis (14), contra (15)</sub>

## S000181 (1.6.5)

> propter haec tria fastigia formae discrimina quaedam fiunt sationum, quod segetes meliores existimantur esse campestres, vineae collinae, silvae montanae.

<a id="rn_s000181_01"></a>
**RN_S000181_01** · meliores (13) · Syntax

meliores (13) is the predicate of the nominative-with-infinitive segetes meliores esse, the clausal subject of existimantur, and campestres (16) is attributive to segetes ('plains grain-crops are reckoned better'), parallel to vineae collinae and silvae montanae, where meliores is gapped.

meliores is separated from campestres by existimantur esse, which tells against taking campestres as the predicate; with campestres attributive, segetes campestres, vineae collinae and silvae montanae are uniform (noun + terrain adjective).

<sub>Tokens: segetes (12), meliores (13), campestres (16), vineae (18), silvae (21)</sub>

<a id="rn_s000181_02"></a>
**RN_S000181_02** · existimantur (14) · Syntax

The quod-clause headed by existimantur (14) explains discrimina (6) ('certain differences arise: that...') and is attached to it as acl, not as a causal advcl of fiunt (8).

Heurgon's translation introduces the clause with a colon, not a causal connective.

<sub>Tokens: discrimina (6), quod (11), existimantur (14) · Sources: Heurgon, French translation</sub>

## S000182 (1.6.5)

> plerumque hiberna iis esse meliora, qui colunt campestria, quod tunc prata ibi herbosa, putatio arborum tolerabilior;

<a id="rn_s000182_01"></a>
**RN_S000182_01** · herbosa (15) · Syntax

herbosa (15) is a predicate with no copula ('the meadows there are grassy'), with prata (13) as subject, coordinated with tolerabilior (19) as a second reason under one quod.

Taking herbosa as attributive to prata would leave prata ibi without a predicate or a role in the clause.

<sub>Tokens: prata (13), herbosa (15), tolerabilior (19)</sub>

## S000183 (1.6.5)

> contra aestiva montanis locis commodiora, quod ibi tum et pabulum multum, quod in campis aret, ac cultura arborum aptior, quod tum hic frigidior aer.

<a id="rn_s000183_01"></a>
**RN_S000183_01** · multum (12) · Syntax

multum (12) is a predicate with no copula ('there is then abundant fodder there too'), with pabulum (11) as subject and coordinated with aptior (22); it is not attributive ('much fodder').

Same zero-copula predication as herbosa in S000182.

<sub>Tokens: pabulum (11), multum (12), aptior (22) · See also: [RN_S000182_01](#rn_s000182_01)</sub>

<a id="rn_s000183_02"></a>
**RN_S000183_02** · quod (14) · Syntax

quod (14) is a relative pronoun, subject of aret (17) in a relative clause on pabulum ('which dries up on the plains'), not a second causal conjunction.

As a conjunction it would leave aret without a subject.

<sub>Tokens: quod (14), aret (17)</sub>

<a id="rn_s000183_03"></a>
**RN_S000183_03** · hic (26) · Textual;Interpretation

Giusta (I 6,5) emends hic (26) to illic (Variant=Giusta:illic): the cooler air belongs to the mountains, whereas hic 'here' would point to the plains. The transmitted hic is kept.

She explains hic as a corruption of illic through loss of the initial il-.

<sub>Sources: Giusta, apparatus and notes</sub>

## S000184 (1.6.6)

> campester locus is melior, qui totus aequabiliter in unam partem verget, quam is qui est ad libellam aequos, quod is, cum aquae non habet delapsum, fieri solet uliginosus;

<a id="rn_s000184_01"></a>
**RN_S000184_01** · habet (28) · Textual

Giusta (I 6,6) reads habeat for habet (28) (Variant=Giusta:habeat): the cum-clause is causal in sense ('not having an outflow for the water'), and causal cum takes the subjunctive. The transmitted indicative is kept (Mood=Ind).

<sub>Sources: Giusta, apparatus and notes</sub>

## S000185 (1.6.6)

> eo magis, siquis est inaequabilis, eo deterior, quod fit propter lacunas aquosus.

<a id="rn_s000185_01"></a>
**RN_S000185_01** · magis (2) · Syntax

The sentence consists of two coordinated degree phrases, eo magis (2) and eo deterior (10), each with the subordinate clause next to it: siquis est inaequabilis depends on magis, quod fit ... aquosus on deterior. magis is the root.

The alternative, deterior as root with magis as its modifier and both clauses attached to deterior, would have the conditional clause interrupt one phrase and reach past it; the adjacency of each clause to its own eo-phrase favours the symmetric structure.

<sub>Tokens: magis (2), inaequabilis (7), deterior (10), fit (13)</sub>

## S000186 (1.6.6)

> haec atque huiusce modi tria fastigia agri ad colendum disperiliter habent momentum.

<a id="rn_s000186_01"></a>
**RN_S000186_01** · modi (4) · Syntax

huiusce modi (4) is coordinated with haec (1) by atque (2), and the pair determines fastigia (6): 'these and suchlike three aspects'.

Attaching huiusce modi directly to fastigia would leave atque without a second conjunct. The reading suits a closing summary that extends the discussion to other similar aspects.

<sub>Tokens: haec (1), atque (2), modi (4), fastigia (6)</sub>
