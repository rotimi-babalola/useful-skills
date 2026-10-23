---
name: technical-writing
description: Write and edit documentation and technical explanations using ASD-STE100 Simplified Technical English structural rules plus the Google developer documentation style guide. Use this skill whenever you write or revise a README, guide, tutorial, API reference, docstring, code comment, changelog, PR description, or ticket — and also whenever you explain a technical concept, a design decision, an error, or a piece of code in chat. Use it even when the user just asks "how does X work" or "explain this", since explanations are documentation too.
---

# Technical writing

Two sources sit behind this skill and they disagree in one place. ASD-STE100 (Simplified
Technical English) exists because a maintenance technician on a tarmac cannot phone the
author to ask what a sentence meant, so it eliminates structural ambiguity and restricts
vocabulary. The Google developer documentation style guide targets a different reader — a
developer skimming for the thing they need — so it asks for a conversational tone and
permits contractions.

Resolve the conflict by tier: the structural rules are not negotiable, the terminology rules
are not negotiable, and the vocabulary restrictions are advisory.

**The overriding rule: never drop a fact, condition, qualifier, or scope limit in order to
satisfy a length or vocabulary rule.** A short sentence that is now slightly wrong is worse
than a long sentence that is right. When precision and simplicity genuinely conflict, keep
the precision and note the trade-off.

## Tier 1 — Structure (always apply)

**Sentence length.** Procedures and instructions: 20 words maximum. Descriptive prose: 25
words maximum. Do not omit the subject, verb, or article to hit the count — STE is explicit
that dropped words are worse than long sentences.

**One instruction per sentence.** Two actions means two sentences, or two numbered steps.

**Active voice.** The grammatical subject performs the action, so the reader always knows who
acts — the reader, the server, the build, or the library. Passive voice is acceptable only in
descriptive text where the actor is genuinely unknown or irrelevant.

- Write: The build adds provenance metadata to the container.
- Not: Provenance metadata is added to the container.

**Present tense.** Including when describing the result of a step. "The command validates the
schema", not "the command will validate the schema".

**Second person.** Address the reader as "you". Avoid "we" for instructions — it obscures who
acts. "We" is acceptable when describing a genuine decision by the authoring team.

**Conditions before instructions.** The reader needs to know whether a step applies before
they read the step.

- Write: If the bucket already exists, skip this step.
- Not: Skip this step if the bucket already exists.

**Lead with the conclusion.** State the outcome, the answer, or the recommendation first,
then the mechanism. A reader who stops after one paragraph should still have the answer.

**Paragraphs: six sentences maximum**, one topic each. A one-sentence paragraph is fine.

**Lists:** numbered for sequences, bulleted for unordered sets, description lists for
term/definition pairs. Keep list items grammatically parallel.

**No directional language.** Not "see the table above" or "as described below" — link to the
section or name it. Position changes with rendering and translation.

**Sentence case for headings and titles.** "Configure the upload hook", not "Configure The
Upload Hook".

**Serial commas.** "strings, arrays, and objects".

**Code and UI formatting.** Code font for code, filenames, and identifiers; bold for UI
elements the reader clicks. Give code elements a qualifying noun: "the `example.yaml` file",
not "`example.yaml`" standing alone as a subject.

## Tier 2 — Terminology (always apply)

**One term per concept, one concept per term, throughout the whole document.** If it is a
"dataset" in paragraph one, it is not a "data product" in paragraph four. Consistency matters
more than variety here; synonyms read as elegant to the author and as two different things to
the reader.

**Do not use the same word as a noun and a verb in close proximity.** "Set the request set"
forces the reader to parse twice.

**Avoid these ambiguous connectors:**

| Instead of | Write |
|---|---|
| since (meaning *because*) | because |
| as (meaning *because* or *while*) | because / while |
| while (meaning *although*) | although |
| once (meaning *after*) | after |
| should (meaning *must*) | must, or *we recommend* |

**Limit noun stacks to three words.** "Dataset page view event handler" is four; rewrite as
"the handler for `dataset.pageViewed` events".

**Expand an acronym at first use**, then use it consistently. Do not alternate between the
acronym and the expansion.

**No idioms, humour, cultural references, or seasonal framing.** They fail for non-native
readers and translate badly.

## Tier 3 — Word choice (advisory)

Prefer the plainest word that carries the meaning. See `references/word-choices.md` for
common substitutions in the spirit of STE's controlled dictionary.

The full standard restricts writers to roughly 900 approved words, each with one meaning and
one part of speech. That is correct for aircraft maintenance manuals and wrong for developer
documentation, where the domain vocabulary is the content. Apply it as a bias toward simpler
words, and take these explicit carve-outs from Google:

- **Contractions are allowed** — "don't", "can't". They keep the tone conversational.
- **Gerunds are allowed** as nouns and in headings — "Getting started", "logging". STE bans
  `-ing` verb forms; that ban costs more than it earns here.
- **Domain and technical terms stay.** Never simplify `idempotent`, `transaction`, or
  `pg-boss` into something vaguer. Define the term instead, once, at first use.
- **Exceed the word limits when precision requires it**, and prefer splitting the sentence
  before you consider cutting a qualifier.

## Applying this in chat explanations

Apply Tier 1 and Tier 2 in full. Relax the document-formatting rules — headings, numbered
procedures, and alt text are usually noise in a conversational answer.

For chat specifically: answer first, then explain. Keep the explanation in prose unless the
content is genuinely enumerable. Do not add a heading to a three-paragraph answer.

## Self-check before delivering

Read back over the draft and check:

1. Does any sentence exceed 20 words (procedure) or 25 (prose)? Split it.
2. Does any sentence contain two instructions? Split it.
3. Is every sentence's actor identifiable? Recast the passives that hide one.
4. Does any condition trail its instruction? Move it forward.
5. Has any concept picked up a second name? Unify them.
6. Does the first paragraph contain the answer?
7. Did anything get lost — a caveat, a limit, an "only when" — to satisfy a rule above? Put it
   back and let the sentence run long.
