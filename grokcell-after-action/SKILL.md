---
name: grokcell-after-action
description: >-
  Use at mission or phase completion, after a failure, near miss, surprise,
  recovery, or unusually good result, or when the same friction repeats.
  Converts evidence into scoped lessons and routes them to the system that can
  actually implement the change.
---
# GrokCell After Action / Organizational Learning

🟣 Purple. Version 1.0.0.

**What should the federation do differently, preserve, automate, teach, or stop doing because of what actually happened?**

`EXPERIENCE → EVIDENCE → RECONSTRUCT → COMPARE → EXPLAIN → LESSON → CHANGE → VERIFY`

**Experience ≠ learning.** Experience becomes learning only when future behavior changes. A beautiful retrospective with no behavioral consequence is documentation.

`OrganizationalLearning = Evidence × InterpretationQuality × ChangeAdoption × FutureValidation` — any factor near zero zeroes the product.

## Fast path

Stop at the first rung that holds.

1. **Routine, expected, low consequence, no surprise** → A0. No review. Do not manufacture lessons.
2. **Small but meaningful** → micro-AAR: expected / happened / surprise / preserve / change / route to. **This is the common case.**
3. **The lesson already exists** → add evidence to it. Do not create a duplicate.
4. **Meaningful mission** → standard AAR, a few high-value actions, routed to owners.
5. **Major failure, high consequence, unexpected success, or repeated friction** → deep AAR with causal structure.
6. **Cross-mission evidence challenges core doctrine** → federation-level review. Rare.

Trigger on plausible learning value, not on schedule: `LearningValue ≈ Novelty × Consequence × RecurrencePotential`.

## 1. Purple converts, it does not archive

Purple asks *what should survive this mission?* — knowledge, routine, tool, test, skill, capability, template, interface, doctrine, warning, or organizational pattern.

A report records what happened. After Action determines what it means, what should change, and **what should remain unchanged**.

Review success, failure, near miss, surprise, recovery, exceptional performance, unexpected efficiency, repeated friction, and completion. Failure-only review misses half the signal.

## 2. Outcome vs process

The most important Purple distinction:

| | Good outcome | Bad outcome |
|---|---|---|
| **Good process** | Preserve and refine — identify *what specifically* produced it, and whether it was context-dependent | Variance under uncertainty. Ask whether the risk was understood and the contingency appropriate — do not teach "never do that again" |
| **Bad process** | **Near miss disguised as success.** Treat seriously | Clearest improvement signal — but still ask what system conditions made the bad process locally reasonable |

**Success is not self-explanatory.** It may come from excellent process, favorable luck, a risk that never materialized, one expert compensating for bad organization, or requirements easier than expected. Never institutionalize successful behavior before understanding why it worked.

**Failure is not self-explanatory** either: bad decision, bad information, capability gap, coordination breakdown, unavoidable external change, a reasonable risk that materialized, implementation defect, or wrong mission framing.

**Resulting is the trap.** Outcome alone is not evidence of decision quality — in either direction.

## 3. Review depth

| | Use when |
|---|---|
| **A0 NONE** | routine, expected, low consequence, no surprise, no reusable insight |
| **A1 MICRO** | what worked / what did not / anything worth changing — a few fields |
| **A2 STANDARD** | meaningful mission: intent, timeline, surprises, decision review, lessons, routing |
| **A3 DEEP** | major failure, high consequence, unexpected success, complex multi-cell behavior, repeated friction |
| **A4 FEDERATION** | mission suggests changing core doctrine, command, force generation, or architecture. Rare |

Do not rewrite the constitution because one mission was strange.

## 4. Evidence before narrative

Do not start with *why do we think this happened?* Start with *what actually happened?*

Pull OpsGraph events, COP deltas, Sentinel records, Recon findings, artifact versions, force changes, decision records, recovery events. **Canonical mission history outranks agent recollection.** Memory may supplement evidence; it must never silently override it.

**Timeline:** reconstruct the minimum needed to see causal structure, not every event.

```
T0 mission begins → T1 Recon identifies API assumption → T2 Blue builds against it
→ T3 interface changes externally → T4 Sentinel detects incompatibility
→ T5 main effort shifts Red → T6 Green repairs → T7 Sentinel passes
```

**Decision points** — places where another action was realistically available — record the state and information available *then*, the owner, visible options, choice, rationale, result.

**Hindsight discipline:** never ask *why didn't they know what we know now?* Ask *what evidence existed at the time?* Classify the outcome as FORESEEABLE / PARTIALLY / NOT REASONABLY FORESEEABLE / UNKNOWN — this bounds what lesson is justified.

**Counterfactuals** are useful only if the alternative was available, authorized, sufficiently known, and plausible at the decision point. Do not invent options using hindsight.

## 5. Surprise and expectation gap

`LearningSignal = ExpectedState − ObservedState`

Every meaningful review asks **what surprised us?** Record expectation, observation, consequence, why the expectation existed, future implication. Surprise exposes hidden assumptions better than generic reflection.

**Positive surprise matters:** *one cross-trained Grok completed work expected to need three agents* → Force Generation may be overstaffing this mission class. Positive surprise often reveals excess bureaucracy.

**Negative surprise:** *routine verification failed on a supposedly stable interface* → could be underestimated volatility, insufficient verification freshness, or stale artifact intelligence. Do not jump to one explanation.

**Explicit predictions** ("integration will take one pass", "API semantics are stable") get compared against reality. Prediction error is high-value organizational data.

**Assumptions** are classified VALIDATED / SUPPORTED / UNTESTED / CONTRADICTED / IRRELEVANT. A mission can succeed while a critical assumption stays untested — never mark that validated.

## 6. Subsystem review

Ask only what is relevant to this mission.

| System | Ask |
|---|---|
| **Recon** | Which unknowns were found before execution? Which were missed? Which PIRs actually changed a decision? Where did collection continue past its value? |
| **Mission Command** | Was intent clear? Were priorities discriminating? Was authority at the right level? Were escalations unnecessary? Too much or too little intervention? |
| **Force Generation** | Cell too large or too small? Required colors present? Independence held? Did reserve matter? Which provider became the real bottleneck? Did cross-training eliminate handoffs? |
| **OpsGraph** | Did graph state reflect reality? Dependencies correct? Tasks too coarse or fragmented? Leases useful? Work orphaned? Did maintenance become overhead? |
| **COP** | Did agents know what mattered? Were important deltas delivered? Was anything lost in overload? Did stale state cause work? Did the human get noise? |
| **Sentinel** | What was caught? What escaped? What was falsely rejected? Did assurance depth match consequence? Could a recurring check be automated? |
| **Blue** | How fast did real effect appear? What rework occurred? Was the artifact larger than necessary? Did interfaces stabilize early enough? What pattern should be reused? |
| **Green** | How fast was degradation contained? Was evidence preserved? Did repair target cause or symptom? Could recovery be automated? Has this failed before? |
| **Sustainment** | Could degradation have been detected earlier? Was reserve real? Were trends visible? Which WATCH state should have escalated sooner? |
| **Capability Registry** | Did it predict provider performance? What was over- or under-estimated? What hidden strength appeared? What gap emerged? |
| **Chromatic** | Was the dominant color correct? Did the supported color shift at the right time? Were cross-color calls useful? Did one color saturate the mission? |

**Color imbalance signals:** too much 🔴 = analysis paralysis; 🔵 = construction before understanding; 🟢 = firefighting; 🟡 = coordination bureaucracy; 🟣 = meta-work.

## 7. Causal structure

Do not ask only *what was the root cause?* Complex missions contain interacting elements:

```
CONDITION A └─
             ├──► EVENT X ──► FAILURE ──► MISSION EFFECT
CONDITION B ┘        └── amplified by C
```

| Element | Meaning |
|---|---|
| Trigger | what initiated it |
| Precondition | what made it possible |
| Contributing factor | raised probability or consequence without alone causing it — stale docs, high load, weak interface contract, missing reserve |
| Amplifier | increased blast radius — e.g. missing idempotency multiplies an unrelated fault |
| Detection failure | *why did we discover this when we did?* Missing monitor, late gate, undelivered delta, missed dependency. Earlier detection is often cheaper than preventing every fault |
| Recovery weakness | *once it failed, why was restoration easy or hard?* No known-good state, poor checkpoint, single Green expert — or clean rollback and excellent event history, which is a strength to preserve |
| Organizational cause | unclear ownership, duplicated authority, wrong color package, expert hoarding, overloaded Sentinel, human approval bottleneck |

Not every lesson belongs in code.

**Local rationality:** assume the agent's action was reasonable given its local picture. What information, priority, and believed authority did it have? This exposes system design flaws that blame conceals.

**Blame is low-information.** "Forge made a mistake" teaches nothing. "Forge operated against interface v3 because its local COP never received the v4 change event" is actionable.

**But blameless ≠ no accountability, and blameless ≠ vague.** Say precisely *"Forge used a superseded interface version"* if true — then ask why that version was locally available as current. Capability evidence still updates when performance genuinely demonstrates a limitation.

**Near misses** — unacceptable conditions existed but material failure did not (wrong state nearly published; no Green reserve during an unstable migration; a lease conflict resolved by timing luck). Priority follows `PotentialConsequence × Plausibility`, **not observed damage**. Learning without paying the full failure cost is the cheapest learning available.

**Heroic success** is the mirror image: watch for outcomes that depended on one exceptional provider compensating for system weakness. Do not encode "always assign Forge-2." Fix the missing state mechanism.

## 8. Lessons

A lesson carries: observation, interpretation, evidence, **applies when**, **does not apply when**, confidence, consequence, recommended change, owner system, validation. **A lesson without scope is dangerous.**

**Scoping.** Bad: *"Always use more Recon."* Good: *"When implementation depends on undocumented external interface semantics, run a targeted runtime probe before committing Blue architecture."* Specific enough to act, broad enough to reuse.

Avoid both failure modes: **overgeneralization** (*"never use parallel agents"* after one coupled task failed → *"do not parallelize across unstable shared interfaces"*) and **undergeneralization** (*"only fix T42"* when a missing invariant clearly spans all tasks).

**Confidence** is LOW / MODERATE / HIGH. One mission usually yields MODERATE.

**Types route differently:**

| Type | Example | Route to |
|---|---|---|
| Factual | published API timeout semantics differ from observed | Artifact Intelligence, Recon memory |
| Procedural | run interface compatibility probe before migration | Routine Compiler, skill update |
| Capability | Forge-4 demonstrated Q4 recovery diagnostics | Capability Registry |
| Organizational | 🔴🔵 pair outperformed three-agent handoff | Force Generation formation memory |
| Assurance | current checks cannot detect stale decision inputs | Sentinel |
| Doctrinal | default authority rule causes repeated low-value escalation | Mission Command doctrine review (high bar) |
| Infrastructural | every recovery requires manual lease inspection | Routine Compiler, Forge |

**Compression:** three stale artifacts, two wrong implementations, and one verification failure may all reduce to *interface-version changes are not invalidating downstream artifacts*. One strong lesson beats six weak ones.

**Before creating a lesson, search existing lessons, routines, doctrine, and failure patterns.** If it exists, strengthen its evidence.

**Collision:** "split work aggressively" vs "keep integration tightly coupled" — do not overwrite or average. Find the moderating variable (*high decomposability → split; low → integrate*). Conditional doctrine is stronger doctrine.

## 9. Change routing

Every accepted lesson terminates somewhere: NO CHANGE, local practice, Capability Registry, Force Generation, Routine Compiler, Artifact Intelligence, Sentinel, Sustainment, Recovery, Forge, Mission Command, or doctrine review.

**"No change" is a valid, evidence-backed conclusion** when process was appropriate, risk was understood, and the outcome was variance. Never manufacture corrective action to justify the review.

**Purple identifies change; the appropriate color executes it.** 🟣 lesson → 🔵 build / 🟢 repair / 🟡 command / 🔴 verify. Purple must not absorb every corrective action.

A useful action is specific, owned, bounded, causally connected, and verifiable. *"Be more careful"* is not an improvement. *"Invalidate verification whenever the input decision version changes"* is.

`ActionPriority ≈ RecurrencePotential × ExpectedConsequence × Effectiveness ÷ ImplementationCost` — qualitative where data is thin.

Before accepting: would this actually prevent recurrence? Is it necessary? Sufficient? Or does it just move the failure elsewhere?

### Persistence ladder

```
NOTE → INDEXED KNOWLEDGE → CHECKLIST/TEMPLATE → SKILL RULE
    → AUTOMATED ASSERTION → TOOL/ROUTINE → ARCHITECTURAL CONSTRAINT
```

Climb only as recurrence justifies rigidity. Institutionalization buys efficiency and costs adaptability — a hard-coded routine is cheaper and less flexible than judgment. Prefer active encoding over passive notes when recurrence is high: an automatic interface-version assertion beats a note saying "remember to check interface versions."

**Learning must pay rent.** Do not emit fifty lessons and thirty-two follow-ups from a minor mission. A few changes with meaningful expected effect.

### Handoffs

AAR emits candidates; the owning system decides implementation.

- **Routine Compiler** gets `routine_candidate`: repeated behavior, trigger, inputs, outputs, current manual cost, judgment required, evidence, expected reuse. AAR never compiles routines itself.
- **Artifact Intelligence** gets artifacts repeatedly reused, misunderstood, obsolete, or missing from discovery.
- **Sentinel** gets new invariants, regression tests, reverify triggers, assurance-depth rules.
- **Sustainment** gets new WATCH signals, health objectives, readiness checks, queue thresholds.
- **Green** gets failure signatures, containment improvements, rollback paths, evidence-preservation requirements.
- **Blue** gets interface redesigns, missing instrumentation, test harnesses, tool candidates. Specify the effect, not the implementation.
- **Yellow** gets authority, priority, reserve, and escalation policy candidates. Mission Command decides.
- **Capability Registry** gets evidence updates. Purple never self-promotes agents.

**White doctrine** changes only on strong cross-mission evidence — persistent ownership ambiguity across mission classes, systematic failure of authority semantics, a genuinely distinct recurring function the chromatic model lacks. Prefer adjusting composition grammar over inventing a sixth color.

## 10. Learning loops

**Single-loop** changes how we act (add a validation check) — right for local defects.

**Double-loop** questions the rule itself: *why is the rule this way? Is the assumption wrong? Should the policy change?* Instead of adding another approval, change the authority boundary that keeps creating the bottleneck. Use only when evidence points beyond local execution.

**Triple-loop**, rarely: *is the organization learning effectively?* Signals that the machinery itself is broken — AARs create actions nobody implements, the same lesson is rediscovered monthly, doctrine grows while performance does not.

## 11. Closure and validation

Action states: PROPOSED → ACCEPTED → IMPLEMENTING → VALIDATING → ADOPTED, or REJECTED / SUPERSEDED. **Proposed is not organizational change. Implemented is not validated learning.**

A lesson closes only when the change is adopted and validated, explicitly rejected with rationale, superseded, or archived as a hypothesis for want of evidence. Not when the review ends.

**The test:** *if the same terrain appears tomorrow, will the federation behave differently?* If no, learning has not propagated.

**Validation** records the change, the later mission, expected effect, observed effect, and result: VALIDATED / MIXED / INVALIDATED / INCONCLUSIVE.

**Doctrine promotion:** `OBSERVATION → LESSON → REPEATED EVIDENCE → VALIDATED PATTERN → DOCTRINE`. A doctrine change request states the current rule, observed problem, cross-mission evidence, proposed rule, expected effect, risks, and validation plan.

## 12. Memory hygiene

**Patterns worth storing:** failure patterns (signature, conditions, mechanism, recovery, prevention, confidence) feed Green and Sustainment; success patterns (mission shape, enabling conditions, behavior, outcome, scope) keep the organization from forgetting *why things work*; formation patterns (mission shape, chromatic signature, composition, evidence count, strengths, limitations) become priors for Force Generation — **never immutable teams**.

**Cross-mission aggregation** is higher-value than any single review: what repeats? Same bottleneck, same capability gap, same verification escape, same overstaffing, same escalation. No fixed occurrence threshold — weigh frequency, consequence, similarity, causal coherence. One catastrophic structural flaw justifies immediate action; three minor coincidences may not.

`LearningSignal ≈ EvidenceQuality × Recurrence × Consequence × Transferability`

**Transferability:** does this apply to this task, this artifact family, this mission class, this color combination, or the whole federation? Scope accordingly.

**Expiry:** volatile lessons record environment, recheck trigger, last confirmed. Do not let historical knowledge fossilize into false doctrine. Contradicted lessons are marked INVALIDATED with reason and history preserved, never silently deleted. Materially changed lessons get a new version.

**Forgetting is healthy.** Retire lessons when the environment changed, the failure became impossible, the capability was compiled away, the lesson was invalidated, or doctrine superseded it. An organization that only remembers becomes constrained by obsolete history.

Purple periodically merges, compresses, invalidates, archives, and compiles. **Useful memory, not maximal memory.** Store at operational resolution — not every debug thought, just *artifact version changes must invalidate dependent verification*.

**Forgotten lesson:** when a known failure repeats despite an existing lesson, the problem is *propagation*, not discovery. Was the lesson retrievable? Encoded into workflow? Was the skill loaded? Was the assertion absent? This usually cues Routine Compiler.

**Provenance:** every durable rule must answer *why do we do this?* with *"because missions M12, M19, M23 demonstrated X, and change C7 reduced Y."* This is what prevents ritualized rules detached from their origin.

## 13. Judgment and disagreement

Human input belongs on value judgments, intent interpretation, subjective success criteria, and preference tradeoffs. Never ask a human to reconstruct a mechanical timeline OpsGraph already holds.

Different Groks may interpret differently. Preserve shared evidence plus competing hypotheses rather than forcing consensus for cosmetic closure. Record a minority hypothesis when the evidence is plausible and the consequence meaningful — not every speculative disagreement.

**Unknown is valid.** *"We do not know why this improved"* beats an invented reusable lesson. The action is to collect better evidence next time.

Overall AAR confidence follows evidence completeness, causal clarity, alternative explanations, reproducibility, and cross-mission support.

## 14. Anti-patterns

| Anti-pattern | Why it fails |
|---|---|
| **Storytelling** | A compelling narrative falsely compresses complex reality; evidence outranks elegance |
| **Hindsight certainty** | Judges past decisions with future knowledge |
| **Blame** | Reduces system failure to an identity; teaches nothing |
| **No accountability** | Avoiding capability updates when evidence genuinely shows a limitation |
| **Root-cause monoculture** | Forces one cause onto interacting conditions for administrative neatness |
| **Action-item flood** | Ten weak actions are worse than two strong ones |
| **"Be more careful"** | Exhortation without structural support does not persist |
| **Doctrine after one event** | Globalizes local experience prematurely |
| **Failure-only review** | Misses near misses and unusual success |
| **Resulting** | Treats outcome as proof of decision quality |
| **Archive and forget** | A lesson in a document has not entered behavior |
| **Purple empire** | Learning bureaucracy examining every task; activity must justify cost |
| **Meta-work escape** | Retrospection displacing the next decisive mission |
| **Learning without validation** | Assumes a change worked because it shipped |
| **Lesson accumulation** | More lessons is not better; prune, merge, invalidate, compile |
| **False universality** | Every lesson needs an applicability boundary |
| **Template tyranny** | Structure should aid reasoning, not force identical narratives |

## 15. Sequence

```
LOAD intent, end state, OpsGraph history, COP deltas, Recon findings,
     force history, Sentinel records, recovery/sustainment events, artifact lineage
 → RECONSTRUCT minimal timeline → decision points → expectation gaps → surprises
 → CLASSIFY outcome vs process → causal structure → strengths, failures, near misses
 → EXTRACT candidate lessons → scope → rate evidence → search existing → merge duplicates
 → IDENTIFY change options → estimate value → accept/reject → route to owner
 → REGISTER actions → VALIDATE against future missions → UPDATE memory → CLOSE
```

## 16. Quality check

Before closing: Did we reconstruct what actually happened, from evidence rather than memory? What surprised us? Did we separate outcome from process quality? Are we judging decisions on information available at the time? What conditions produced the result? What worked that should be preserved? What nearly failed despite success? What failed despite reasonable process? What lesson generalizes, and what is its scope? What should change, who owns it, and how will we know it worked? **Are we creating more process than value?**

## 17. Metrics

Repeated failure rate, repeated lesson rate, lesson-to-action rate, action completion, validated learning rate, invalidated lessons, routine candidates, capability updates, formation updates, doctrine change frequency, retrospective overhead, learning propagation time, near-miss capture rate.

- **Repeated failure rate** should fall for already-understood failure classes. If not: the lesson was not operationalized, a routine is missing, retrieval failed, or the action was ineffective.
- **Repeated lesson rate** — if reviews keep rediscovering the same lesson while behavior stays the same, Purple is failing.
- **Lesson-to-action rate** should *not* be driven toward 100%. Track whether *high-priority* lessons are acted upon.
- **Validated learning rate** = changes with demonstrated future benefit ÷ implemented changes. This measures whether Purple is learning or merely changing.
- **Doctrine change frequency** — after every mission is overfitting; never despite repeated evidence is rigidity.
- **Retrospective overhead** = AAR effort ÷ mission effort. High on routine missions means Purple saturation.
- **Propagation time** from lesson discovered to behavior changed. Shorter, without quality loss, means a more adaptive federation.

Do not optimize AAR count, lesson count, or action count. Optimize **validated improvement in future mission behavior**.

## 18. Constitution

1. Experience is not learning; a lesson is not learned until future behavior changes.
2. Review intensity follows learning value. Do not manufacture lessons from routine work.
3. Evidence precedes narrative; canonical state outranks recollection.
4. Reconstruct only the timeline needed to understand causality.
5. Judge decisions using information available at the time.
6. Good outcome does not prove good process; bad outcome does not prove bad process.
7. Good outcomes may conceal near misses; near misses are priced by potential, not damage.
8. Preserve successful mechanisms when evidence supports them.
9. Ask what surprised us; prediction errors are high-value signals.
10. Do not force one root cause; distinguish trigger, precondition, contributor, amplifier, detection failure, recovery weakness.
11. Analyze local rationality. Blame is low-information; blamelessness is not vagueness and does not remove empirical accountability.
12. Lessons carry scope, evidence, confidence, and their non-applicability conditions.
13. "No change" is a valid conclusion. Prefer few high-value actions over floods.
14. Purple identifies change; the appropriate color executes it.
15. Route each lesson to the system that owns implementation.
16. White doctrine changes require strong cross-mission evidence.
17. Contradictory lessons get scoped, never averaged — look for the moderating variable.
18. Encode at the least rigid level that removes the recurring friction.
19. Proposed is not adopted; implemented is not validated.
20. Repeated known failure signals propagation failure, not discovery failure.
21. Volatile lessons expire; invalidated lessons stay traceable; obsolete lessons retire.
22. Preserve provenance from experience to rule.
23. Human judgment goes to values and intent, not mechanical reconstruction.
24. Unknown beats invented causal certainty; disagreement may remain explicit.
25. Learning effort must pay rent. Purple must not become a bureaucracy.
26. The best AAR makes the next mission measurably easier, safer, faster, or clearer.

## Done when

Every sufficiently informative mission changes the probability distribution of success on the next one:

```
UNKNOWN PROBLEMS → MISSION EXPERIENCE → ORGANIZATIONAL LEARNING
 → ROUTINES, TOOLS, CAPABILITIES, BETTER COMPOSITION, BETTER ASSURANCE
 → LESS FRICTION, LESS REDISCOVERY, LESS REPEATED FAILURE, MORE AUTONOMY
 → HARDER MISSIONS BECOME CHEAPER
```

The deepest persistent unit is not the team and not even capability. It is **capability that can learn from its own use**.
