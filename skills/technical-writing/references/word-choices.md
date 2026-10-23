# Word choices

Advisory, not enforced. These follow the principle behind ASD-STE100's controlled dictionary —
pick one word for one meaning and prefer the plainest option — without importing the full
900-word restriction, which is too tight for developer documentation.

Read this file when editing prose for clarity, or when a sentence feels heavier than the idea
it carries. Skip it when the words in question are domain terms.

## Pick one synonym and keep it

STE's core move is choosing a single word from each synonym cluster. The specific choice
matters less than the consistency, but these are reasonable defaults:

| Prefer | Over |
|---|---|
| start | begin, commence, initiate, kick off |
| make sure | verify, confirm, ensure, validate (except where *validate* is the technical operation) |
| use | utilise, leverage, employ |
| about | approximately, roughly, circa |
| before | prior to, in advance of |
| after | subsequent to, following |
| because | due to the fact that, owing to, since |
| if | in the event that, in the case that |
| to | in order to, so as to |
| can | is able to, has the ability to |
| must | is required to, shall |
| help | facilitate, enable (when *enable* is not the technical operation) |
| enough | sufficient |
| show | display, surface, expose (except as UI or API terms) |
| get | obtain, acquire, retrieve (except as the HTTP verb or method name) |
| find | locate, identify |
| let | permit, allow (when describing what a feature makes possible) |
| more than | in excess of |
| most | the majority of |
| now | at this point in time, currently |
| then | subsequently, thereafter |

## Cut these outright

They add length without adding meaning:

- *basically*, *essentially*, *simply*, *just*, *obviously*, *of course*, *actually*
- *very*, *quite*, *rather*, *fairly*, *somewhat*
- *please note that*, *it is important to note that*, *keep in mind that*
- *in terms of*, *with respect to*, *as far as X is concerned*
- *there is / there are* openings — recast with a real subject

"Simply" and "just" are worth singling out: they tell a stuck reader that their problem is
trivial, which is both unhelpful and often untrue.

## Words with more than one meaning

Each of these carries two readings. Use the unambiguous alternative when the context does not
force a single interpretation.

| Word | Ambiguity | Fix |
|---|---|---|
| once | after / one time | after, one time |
| since | because / from that time | because, from |
| as | because / while / in the role of | because, while, acting as |
| while | during / although | during, although |
| may | permission / possibility | can, might |
| should | recommendation / obligation | we recommend, must |
| follow | come after / obey | comes after, obey |
| fall | move downward / decrease | drop, decrease |
| clear | unambiguous / to remove | unambiguous, remove |
| replace | swap in / substitute for | put in place of, substitute for |
| only | scope depends on placement | reposition next to what it modifies |

## Anthropomorphism

Products do not want, think, know, or decide. Reserve those verbs for people.

- Write: The scheduler retries the job after 30 seconds.
- Not: The scheduler knows to try again.
- Write: The validator rejects the payload.
- Not: The validator doesn't like the payload.

An exception worth keeping: established terms of art like *listener*, *observer*, and
*handler* are fine. So is "the function returns" — that is standard usage, not
anthropomorphism.

## Excessive claims

Avoid *easy*, *simple*, *quick*, *just*, *seamless*, *effortless*, *robust*, *powerful*,
*best-in-class*. Describe the mechanism and let the reader judge. Also avoid promising
future behaviour — do not pre-announce features, deprecations, or timelines in
documentation.
