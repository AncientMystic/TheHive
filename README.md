<img width="1200" src="https://github.com/AncientMystic/TheHive/blob/main/images/TheHive.jpg">

---

## Support development

If you want to support continued development:

- **Cash App:** `$AncientMystic144`
- **Monero (XMR):** `44FeV38E1xVV87EaynuNkxcBpmi2G5kSE5n1wPSYjezD87MwsPckBs7SvwJmTRJ15rA3TDYSLPTpY7jyzdVTu9Sv9mtoHpi`

---

# TheHive

**A sovereign intelligence that governs itself, runs locally, and proves what it knows.**

TheHive is not a chatbot with a memory. It is a self-running research ecosystem: a hive of workers that explore, compute, read, and propose; a queen that verifies before she remembers; and a ledger that makes every decision traceable. It runs on local hardware, without an LLM in its thinking loop, and it treats knowledge as something earned rather than generated.

> **Local. Private. Transparent. The opposite of a black box.**
>
> Every action is logged. Every move is reversible. Every consequence is measured. Nothing is forgiven into fact. Every mistake is corrected; every error becomes a lesson.

> **Status: Early Development (Preview).** The Hive is currently in active, private development. This repository serves as a public showcase of the architecture, philosophy, and early benchmark results. The core source code will be released soon. This README documents currently measured behavior.

---

## Why TheHive exists

Most AI systems optimize for the next fluent answer. TheHive optimizes for the next **defensible** answer.

That changes the architecture:

- **Verification is a first-class subsystem**, not a prompt instruction.
- **Memory is earned**, not accumulated from every conversation.
- **Uncertainty is visible**, not smoothed away.
- **Provenance is retained**, so a claim can be traced to the check that admitted it.
- **The owner stays in control**, because a research system for one professional should not behave like a multi-tenant chatbot.

The result is a system that is deliberately conservative at the point of commitment and aggressive at the point of testing.

---

## What the Hive is

The Hive is a self-running learning system. a small "hive" of AI agents, supervised by one "queen." The worker agents go out and find information (from web pages, feeds, chat, local documents and their own experiments), but they're never allowed to just declare something true. Instead, they hand their findings to the queen over a queue, like interns submitting reports for review. The queen only accepts a finding if it can actually be proven: either by running it (the math works, the code passes its tests) or by checking that at least two independent sources agree.

Everything the queen accepts is written into a tamper-proof record, like a lab notebook where every page is sealed and every entry can be traced and undone. Nothing enters the book unverified, nothing hides what happened before it, and every decision is logged. On top of that, the system helps itself improve: it notices what it knows least about and goes looking for answers, it can ask an external AI for a second opinion (but only trusts that opinion after checking it), it can split a big question into small pieces handled by different workers and merge the answers back together, and it can even find and fix bugs in its own code.

The result: a system that slowly and safely accumulates knowledge it can show its work for, and can answer your questions or do tasks in plain English while it does.

---

## How the hive handles data

The core idea: a system that proves what it claims. Most knowledge or classification systems work like a labeled filing cabinet — something gets sorted into a category because a person (or a model) said so. This system refuses to do that. Every claim it makes about a math problem — "this is a combinatorics question," "this answer is correct" — comes attached to an executable check: a small piece of code that, when run, either confirms the claim or fails. If something can't be verified by running it, the system doesn't pretend it can — it openly marks that item as "not yet gradable" and keeps it visible but inactive. So nothing silent slips in: the system never rehearses confidence it can't back up.

The categories grow instead of being fixed. A traditional taxonomy is drawn up by an author once and then it's done — a static tree of labels. Here, the tree itself is manufactured. You hand the system a topic like "integer partitions" or "rational arithmetic," and it drafts a category structure for that topic — what the classes are, how they differ, what distinguishes them — and then it audits its own draft: does each class actually behave differently from its neighbors when probed? Can we distinguish real members from near-misses? Only structures that pass this earning process get used. This is why the system can cover "unbounded" territory: it isn't limited to whatever an author foresaw; it has a repeatable method for turning any new topic into a verified domain, using the same spine every time.

Classification isn't one label — it's coordinates. A problem that passes through the system isn't filed under a single name. It gets positioned along several axes at once: which domain it belongs to, how hard it is, how novel it is relative to what's already been solved. The system keeps a map of these coordinates and tracks where it has rich, verified material and where the map is empty. That's how it decides what to work on next — and that decision isn't made by a hunch, but by a small adaptive engine that weighs uncertainty, novelty, and disagreement among different internal judges.

The system also thinks about how to think — and how to heal itself. Around the classification core there's a working vocabulary of reasoning styles: worked micro-examples of how to approach proof, verification, contradiction, and uncertainty, stored so that any part of the system can borrow a proven way of thinking rather than improvising. There's also a memory of past successes and failures — what got verified, what got repaired, what fell through — kept as an append-only record so history can't be rewritten. When the system finds a bug in its own code, there's a repair lane that tries fixes and only accepts one that actually runs clean; nothing is patched in on a model's word alone.

The honest summary. Think of it as a self-auditing curriculum: it invents new subject areas, demands that every section pass an executable test before students (its own internal agents) can study it, tracks not just what's known but what's confidently unknown, schedules its own review and exploration, and keeps a tamper-proof diary of every change it makes to itself. A taxonomy is a map; this project is a surveyor that manufactures the map, tests each border point before inking it, admits the blank areas, and keeps exploring the blanks.

---

## The shape of the hive

TheHive is not one model with a long prompt. It is a small society with a strict constitution.

### Workers propose

Thirteen worker classes explore different kinds of work: math, code, physics, quantum, esoteric, algorithms, scout, strategy, UI, research, sovereign, general, and oracle. They scan local documents, inboxes, feeds, web material, code, and their own generated experiments. They can split a question into smaller tasks and hand the pieces to other workers.

The important part is what they cannot do: **a worker cannot write a fact.** Workers queue findings. The queen disposes.

### The queen disposes

Only the queen writes durable memory. She claims a bounded batch, re-verifies each finding independently, and sends it through the promotion gates. A finding that fails is rejected, held, or parked — visibly, with a reason.

The queen is not a second opinion. She is the constitutional boundary between "a worker said it" and "the hive knows it."

### Two kinds of truth

TheHive separates claims that can be executed from claims that can only be corroborated.

- **Executable truth** covers math evaluation, rational and complex arithmetic, combinatorics, code execution, file existence and content checks, plan schemas, accessibility checks, research schemas, and sovereign audits. The check runs. It does not ask a model for a verdict.
- **Consensus truth** is quarantine-only. A claim needs at least two independent anchors to become a candidate. It still faces the same promotion gates.

A failed executable check simply rejects. There is no poison path where a bad test result gets argued into memory.

### The memory

The durable layer is local SQLite, one file per concern: facts, queue, quarantine, ledger, models, dialogue, and style. The ledger is hash-chained. Promotion writes a rollback snapshot. Facts carry provenance, confidence, and a trail back to the check that admitted them.

The queue is a sieve, not a conveyor belt. Exact duplicates, resolved-window repeats, content hashes, and a cosine paraphrase net catch the same idea arriving in different clothes. A duplicate reinforces the original instead of inflating the fact count.

### The loop

A tick runs the hive:

1. Workers learn, plan, and work.
2. The queen drains the queue.
3. Maintenance replays episodes, runs sleep abstraction, archives cold material, decays memory, and verifies the chain.

The loop is resumable. Kill it and restart it; it continues from the next tick. A watchdog notices dead ticks. The optional oracle can be attached for review, but it is off by default and its output still has to pass the same gates.

### It repairs itself

A doctor lane can find and fix bugs in the hive's own code. A proposed fix is accepted only if it runs clean. The same rule applies to the system's own models: a self-built model is promoted through the same evaluation teeth as anything else.

---

## How it compounds

TheHive does not train a giant model with gradients. It compounds small, measurable gains:

- **Episodes and traces** turn each task into a reward signal. Bandits learn which strategies pay, per domain and per task kind.
- **Quality-diversity archives** keep elite tasks and mutate or mate them, so the curriculum improves itself instead of repeating.
- **RND novelty** measures surprise without consuming it: scoring peeks; only promotion and hold paths train.
- **FSRS/Leitner memory** gives facts a forgetting curve, a review schedule, and a reason to be pulled again.
- **Sleep abstraction** clusters verified rows into reusable templates — compression from episodes into skills.
- **A self-model** is trained from the hive's own style and promoted facts, then distilled and gated before it serves chat.
- **A style voice** is learned separately from facts, so the queen can sound like herself without contaminating what she knows.
- **Tiers, not deletion.** Old material moves to the attic; dead rows are tombstoned with reasons and stay recheckable. Nothing learned is silently lost.
- **Gamified durability.** XP ledgers, achievements, class trees, anti-farm rules, and offline accrual make overnight improvement visible. The point is not to turn research into a game; it is to reward durable gains over chatter.

This is the "constantly evolving" part of the image, implemented as counters, schedules, archives, and gates — not as a slogan.

---

## It talks, but conversation is not memory

Chat is a layer over the same machinery, not a second brain. It routes intent, recalls scored facts, delegates probes to workers, and composes an answer with structural honesty:

- Empty recall becomes "I don't know yet."
- Low confidence is labeled.
- A code block can be re-executed.
- A failed execution becomes a queued probe, not a confident guess.
- Conversation can teach style and queue research, but it cannot assert knowledge.

The optional oracle can be asked for a second opinion. It is never trusted on its word.

---

## Tests

The following test notes are preserved from the repository's original README. They were run with live qwen and are not the same as the local deterministic benchmark pass documented below.

```
the hive finds and fixes, not just proves

8 blind temp-file snippets, live qwen

  hive
    found:  8/8 with runtime proof
    fixed:  8/8

  Raw qwen (read only)
    found:  3/8
    fixed:  opines only, no verification
```

Note: During these tests, The Hive also found another bug in the files checked, which had been missed by multiple major online models. proving it can use a small 4B model with an intelligence score of 12.4 to beat major models scoring 40-50. it drastically improves not only performance but model intelligence as well.

---

```
doing some more basic testing on the middleware api aspect of the hive 

TASK: what is 144/12
  Raw qwen: 2.99 s (token gen)
  Hive:     0.24 s — Answer (math): 144/12 = 12
  Verdict:  hive 12× faster via deterministic synth, zero tokens

TASK: formulate invitation reply
  Raw qwen: 5.25 s
  Hive:     3.8 s — packaged oracle lane
  Verdict:  hive ~1.4× faster, tightened system prompt

TASK: bug hunt mutable_state.py
  Raw qwen: 16.9 s
  Hive:     6.6 s (hive-Q, same qwen model)
  Verdict:  same findings, 2.6× faster packaging

TASK: bug hunt offbyone.py
  Raw qwen: 11.3 s
  Hive:     8.4 s
  Verdict:  same findings, faster

TASK: bug hunt none_trap.py
  Raw qwen: 9.6 s
  Hive:     9.2 s
  Verdict:  same findings

TASK: execution proofs
  Raw qwen: — (only opines)
  Hive:     3/3 fail → all bugs PROVEN by running them
  Verdict:  the gap reading can't close

TASK: fix round-trip
  Raw qwen: raw proposes fixes (2.3–5.1 s)
  Hive:     hive verifies all 3 → PASS in 0.11 s each
  Verdict:  machine-verified, not eyeballed


WHAT THIS ACTUALLY DEMONSTRATES

1. The hive wins twice over the raw model: on latency (packaged lane prompts are tighter; 
synth fast-paths skip token generation for any model callable deterministically) and on correctness 
— every verdict is a receipt on the ledger, not prose.

2. The real differentiator is execution: raw and hive-Q both read the code (same qwen weights — identical findings as expected). 
But the hive's code_run gate ran all three planted-bug snippets and produced runtime proof (pass: False) in milliseconds — 
behavior like the mutable-default state carryover is proven, not guessed. 
And when raw's fixes came back, the hive verified all three to PASS in ~0.1 s each.

3. Receipts everywhere: hive answers carry provenance; raw answers are just text.
```

---

## What works today

The numbers below are not the pitch. They are the receipts.

### Deterministic verification lanes

TheHive does not ask a model whether an answer is correct. It runs the check.

Four verifier lanes are implemented and measured:

| Lane | Calls | Correct accepted | Tampered rejected | False accepts | False rejects | Throughput | p50 | p95 |
|---|---:|---:|---:|---:|---:|---:|---:|---:|
| Math | 1,000 | 500 / 500 | 500 / 500 | 0 | 0 | 875.9 calls/s | 0.858 ms | 2.335 ms |
| Rational | 1,000 | 500 / 500 | 500 / 500 | 0 | 0 | 4,078.4 calls/s | 0.189 ms | 0.600 ms |
| Complex | 1,000 | 500 / 500 | 500 / 500 | 0 | 0 | 710.7 calls/s | 1.170 ms | 2.916 ms |
| Combinatorics | 1,000 | 500 / 500 | 500 / 500 | 0 | 0 | 1,309.2 calls/s | 0.606 ms | 1.561 ms |

Each lane was exercised with 500 valid claims and 500 tampered claims. The verifier accepted every valid claim and rejected every tampered claim.

A separate capability report measured:

- **240 / 240 graded claims correct**
- **48 / 48 tampered claims caught**
- **Mutation score 1.000**

### Domain gates

Each implemented domain has a gate suite and a mutation suite:

| Domain | Gate suite | Mutation suite | Errors | Mutation score |
|---|---:|---:|---:|---:|
| Complex | 64 / 64 | 27 / 27 | 0 | 1.000 |
| Rational | 80 / 80 | 10 / 10 | 0 | 1.000 |
| Combinatorics | 96 / 96 | 11 / 11 | 0 | 1.000 |

The gates are not just “does the happy path work.” They check that the domain evaluator catches deliberately corrupted claims.

### Scale behavior

At the largest measured tick count:

| Domain | Graded | Distinct claims | Wall time | Errors | Mutation score |
|---|---:|---:|---:|---:|---:|
| Complex | 1,024 | 267 | 2.43 s | 0 | 1.000 |
| Rational | 1,280 | 10 | 1.51 s | 0 | 1.000 |
| Combinatorics | 1,536 | 11 | 1.73 s | 0 | 1.000 |

These are single-process measurements, not distributed throughput claims. They show that the gate path remains stable as the number of generated claims grows.

### Code execution gate

Executable claims are run, not judged by opinion.

- **30 / 30 snippets passed**
- **9.07 executions/s**
- **p50 107.2 ms**
- **p95 148.7 ms**
- **max 165.1 ms**

### Sandbox refusals

The sandbox was probed with hostile inputs designed to escape, persist, or abuse execution.

- **22 / 22 probes refused**
- **0 exceptions raised**
- **Refusal rate 1.000**
- **Section wall time 6.3 ms**

The sandbox is not a promise in a system prompt. It is a boundary that was tested.

### Recall

A recall benchmark seeded 500 facts and ran 100 queries.

| Metric | Result |
|---|---:|
| Top-1 accuracy | **1.000** |
| Queries per second | **1.1** |
| p50 latency | **876 ms** |
| p95 latency | **1,081 ms** |

This is a correctness result at a small scale, not a production latency claim. The separate recall gate (n=12) also measured top-1 1.000, recall@3 1.000, and MRR 1.000.

### Queue deduplication

The queue was tested with 500 unique submissions followed by 500 exact duplicates.

| Metric | Result |
|---|---:|
| Unique rows after unique batch | 500 |
| Rows after duplicate batch | 500 |
| Dedupe ratio | **1.000** |
| Unique intake rate | 15.5 /s |
| Duplicate rejection rate | 59.9 /s |

Duplicates reinforce the existing row instead of bloating the queue.

### Ledger integrity

The ledger is append-oriented and tamper-evident.

| Metric | Result |
|---|---:|
| Entries | 3,000 |
| Append rate | 28.7 /s |
| Verification rate | 39,694.5 /s |
| Chain intact | **true** |
| Tamper detected | **true** |
| Restore verified | **true** |

The ledger test appends entries, verifies the chain, tampers with the record set, confirms detection, and confirms restoration.

### Promotion is deliberately conservative

Promotion is where a verified claim becomes durable memory. It is the most gated step in the system.

In a cold calibration window:

- **100 claims submitted**
- **100 claims verified**
- **1 claim promoted**
- **99 claims held** by the calibration gate
- **1 fact stored**

The held claims were verified but not admitted: their information gain stayed below the gate’s floor after the calibration window detected miscalibration. This is the intended behavior. Verification answers “is this true?” Promotion also asks “does this teach the system something it does not already know, and is the system calibrated enough to trust the commitment?”

A separate synthetic warm-window run, used only to measure steady-state throughput, promoted **52 / 100** claims at **2.3 promotions/s** before the calibration gate re-engaged. That run is a simulation of a warmed window, not a production state.

---

## Test posture

The full suite is not presented as “all green.” It is presented as measured.

| Suite | Result |
|---|---|
| Full suite | **791 passed, 11 failed, 1 deselected** in 384.63 s |
| Known-failure isolation | **11 failed, 51 passed** in 97.23 s |
| Core verifier subset | **197 passed, 0 failed** in 16.22 s |
| Capability report | **240 / 240 graded, 48 / 48 tampered, mutation 1.000** |
| Domain gates | **Complex 64/64 + 27/27; Rational 80/80 + 10/10; Combinatorics 96/96 + 11/11** |
| Recall gate | **Top-1 1.000, recall@3 1.000, MRR 1.000** (n=12) |

The 11 failures are one known deterministic regression in the chat reply wrapper: every failure collapses to the same fallback string, `Not found in available sources.` They are isolated from the verifier core. The core subset is green. The full suite is reported with the failure count because a test report that hides a known failure is not a test report.

---

## Measured live state

The following counts were read from the live system at measurement time. They describe state, not capacity.

<details>
<summary>Show live-state counts</summary>

| Store | Count |
|---|---:|
| Facts | 3,064 |
| Queue rows | 8,844 |
| Queue: promoted | 2,314 |
| Queue: rejected | 1,854 |
| Queue: verified | 4,676 |
| Ledger entries | 82,345 |
| Quarantine rows | 110,637 |
| Quarantine: machine-held | 110,636 |
| Quarantine: human-held | 1 |
| Oracle queue | 250,333 |
| Oracle receipts | 335 |
| Episodes | 3,375 |
| Bandit arms | 114 |
| Flow stats | 95 |
| QD cells | 21 |
| Models | 240 |
| Training runs | 242 |
| Style exemplars | 500 |
| N-grams | 2,007 |
| Dialogue turns | 200 |
| Dialogue attic | 3,213 |
| Entities | 500 |
| Entity attic | 11,917 |

</details>

The large quarantine and oracle-queue counts are not failures. They are the visible cost of keeping unverified material out of durable memory.

---

## Scope

The measured working tree contains:

- **803 test functions**
- **~54,518 lines of Python**
- **43 core Python modules**
- **17 swarm modules**
- **3 GUI Python modules**
- **30 JavaScript files**
- **2 HTML files**
- **1 CSS file**
- **3 domain specification files**

The core source remains private during preview. This README is the public description of behavior and evidence, not a build guide or a source dump.

---

## Design principles

1. **Verify before remember.** A claim that cannot be checked does not become durable memory.
2. **Proposal is cheap; commitment is expensive.** Models generate candidates. Gates decide what survives.
3. **Local, private, transparent.** The system is the opposite of a black box.
4. **Every action is logged; every move is reversible; every consequence is measured.**
5. **No topic limits; no forgiveness into fact.** The hive may explore anything. What it may remember is still gated by proof.
6. **Every mistake is corrected; every error becomes a lesson.** Repair is a lane, not a promise.
7. **Report the failure count.** A test report that hides a known failure is marketing, not evidence.

---

## The ambition

The image says it plainly: **The Hive is the future. Making datacenters obsolete.**

a local system can verify, remember, and improve without a datacenter behind every answer. The long-term aim is a sovereign intelligence that owns its own memory, shows its work, and gets better while you sleep.

**TheHive is early. The gates are real. The numbers above are measured.**
