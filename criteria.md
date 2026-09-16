# Acceptance criteria — The Unofficial Guide

Five criteria that say what "working" means for this system, written in unit 1
**before** any results existed.

An acceptance criterion names a target: a number, a count, a rate, or something
a person could plainly observe. *"Retrieval works"* is an opinion. *"For at
least 4 of my 5 test questions, the top results include a chunk containing the
answer"* is a criterion.

Under each one, write a sentence or two on **why that target** and not a
stricter or looser one. A reason that says something about your corpus or your
pipeline earns credit; *"80% seemed reasonable"* does not.

> Missing your own targets next unit costs you nothing. Setting a target so
> easy you can't miss it does.

---

## 1. Retrieved chunks contain the answer

For at least 4 of my 5 test questions, the retrieved chunks include one that
contains the answer.

**Why this target:**
<!-- e.g. "One of my questions is about a topic only two documents mention, so
     I expect that one to be hard." -->

---

## 2. Every answer names a source

Every answer the system produces names at least one source document.

**Why this target:**
<!-- Why all five and not four? What about your setup makes that achievable —
     or what would have to go wrong for it not to be? -->

---

## 3. The relevance gate stops out-of-corpus questions

When I ask a question my documents clearly don't cover, the relevance gate
stops it and the system returns "I don't have enough information about that" —
in at least 4 of 5 tries.

<!-- The five questions are the ones in `OUT_OF_SCOPE` at the bottom of
     `questions.py`, and `run_eval.py` puts them through the gate and writes
     what happened into your run log. Swap them for your own if you'd rather —
     just keep five of them, or the "4 of 5" above has nothing to be 4 of. -->

**Why this target:**
<!-- What did your distances look like when you set the cutoff in Milestone 4?
     Was there a clean gap, or did the two groups overlap? -->

---

## 4. Chunks don't cut a fact in half

At least 4 of 5 sampled chunks: no sentence containing a time, price,
distance, or date is cut off at the start or end of the chunk. (To check:
read the sentence with the number in it — does it start and end inside the
chunk, or does it run off the edge?)

**Why this target:** Some of my documents put a bunch of different towns'
facts into one paragraph — like "Kestrelford's pubs serve 12 to 2 and 6 to
8:30" right next to a sentence about a different town. If my chunks are the
wrong size, they could cut a sentence like that in half and lose the actual
number. I said 4 of 5 instead of 5 of 5 because I noticed a couple of these
paragraphs are so packed that I'm not sure any chunk size handles them
perfectly.

---

## 5. The named source contains the fact used in the answer

For at least 4 of 5 test questions, the exact fact used in the answer appears
somewhere in the document named as the source. (To check: take the fact out
of the answer, open the cited file, and search for it.)

**Why this target:** My corpus has a guide for each town (like
`guide_kestrelford.md`) but also guides organized by topic (like
`guide_eating.md`) that mention every town. A question about Kestrelford's
food hours is actually answered in `guide_eating.md`, not
`guide_kestrelford.md`, so it would be easy for the system to name the wrong
file just because it has the town's name in it. Criterion 2 only checks that
some source gets named — this one checks that the source it names is the
one that actually backs up the answer.



---

<!-- ─────────────────────────────────────────────────────────────────────────
     UNIT 2 — read this before you change anything above.

     If a criterion turns out to be BROKEN rather than merely unmet, you can
     revise it, and that earns credit. But never delete or edit the original
     line. Add the revision underneath it, like this:

         ## 1. Retrieved chunks contain the answer

         For at least 4 of my 5 test questions, the retrieved chunks include
         one that contains the answer.

         **Why this target:** ...

         > **Revised in unit 2:** For at least 4 of 5 questions, the top three
         > results contain the answer.
         >
         > **Why revised:** I couldn't judge "the chunks include one that
         > contains the answer" the same way twice — I scored two questions
         > differently on Monday than on Wednesday. The new version is
         > something I can actually check.

     That's a revision because the criterion couldn't be MEASURED.

     Lowering a target because you missed it is not a revision, and it costs
     you the point:

         ✗ "I said 4 of 5 but got 2 of 5, so 2 of 5 is more realistic."

     A number you missed stays where it is, gets diagnosed, and gets a fix
     attempted. That's where the points are.

     The whole reason the originals stay visible is so someone can see what you
     said before you knew the answer.
     ───────────────────────────────────────────────────────────────────────── -->
