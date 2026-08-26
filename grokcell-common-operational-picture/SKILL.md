---
name: grokcell-common-operational-picture
description: >-
  Use when a Grok needs to know what is happening now — orienting on join,
  recovering lost context, briefing command, distributing a change, or deciding
  who needs to be told something. Fuses intent, execution, intelligence, force,
  assurance, and risk into role-appropriate views.
---
# GrokCell Common Operational Picture

The federation's shared model of present reality. Version 1.0.0.

**What is happening now, what matters about it, and what does each element need to know?**

The COP sits between raw state and judgment: `RAW STATE → FUSION → SIGNIFICANCE → PICTURE → ALIGNED LOCAL DECISIONS`.

It is not a chat transcript, a task list, a metrics dashboard, a database dump, or a replacement for Mission Command.

## Fast path

Stop at the first rung that holds.

1. **Nothing decision-relevant changed** → update state silently. Do not notify anyone.
2. **One element is affected** → send that element a delta. Nobody else.
3. **The recipient already holds a valid picture** → send the delta plus its implication, not a rebrief.
4. **Agent is joining, recovering, or drifted** → send a full role-view snapshot.
5. **Main effort, authority, or a decisive assumption changed** → high-salience update to affected elements, and flag command attention if judgment is required.

If command attention is empty, say so: **command can remain quiet.**

## 1. What the COP owns

Each subsystem answers its own question. The COP answers what they mean *together*.

| Source | Answers |
|---|---|
| Mission Command | what matters — intent, priority, authority |
| Recon | what we know about the terrain |
| OpsGraph | state of work |
| Capability Registry | what we can field |
| Force Generation | what organization we are fielding |
| Sentinel | what we can trust |
| Sustainment | system health |
| **COP** | **what all of it means right now** |

The COP **references** canonical sources. It never becomes a competing mutable database of facts other systems own.

## 2. Common does not mean identical

One reality, many role-appropriate views. Shared truth, different bandwidth.

| Color | Default view emphasis | Default subscriptions |
|---|---|---|
| 🔴 Red | unknowns, claims, evidence, verification needs | assumption changes, contradictions, verification requests |
| 🔵 Blue | intent, interfaces, decisive tasks, changed assumptions | interfaces, task readiness, requirements, artifact deps |
| 🟢 Green | degraded systems, dependencies, recovery state | health degradation, failures, resource loss, recovery |
| 🟡 Yellow | priority, force, decisions, risks | main effort, priority, capability gaps, contention |
| 🟣 Purple | patterns, repeated friction, emerging gaps | repeated blockers/repairs, formation patterns, demand |

Role filtering may **remove** information. It must never **rewrite** truth. Two agents may hold different views; they must never hold contradictory views of a shared fact.

Agents may also subscribe explicitly by mission, cell, task, interface, artifact, capability, or event class.

## 3. Information minimization

Maximize `decision-relevant information ÷ attention consumed`.

Every field must answer: *could this change the recipient's action, interpretation, or readiness?* If no, do not push it.

## 4. Three nested pictures

### Strategic — for human / Mission Command

Mission purpose and end state, current phase, main effort, overall assessment (`ON_TRACK | AT_RISK | OFF_TRACK | COMPLETE`), decisive constraint, force posture, mission confidence, top 1–3 risks, unresolved command decisions, changes since last update, attention required.

Should fit on one screen.

### Operational — for cell leads / Force Generation / Yellow

Main effort and supported cell, active cells, critical path, blockers, verification queue, capability committed/reserve/gaps, unstable and changed interfaces, open and upcoming decisions, critical findings and unknowns, failed/conditional/stale assurance, current risks, next sync points.

### Local — for an executing agent

Mission purpose, current objective, owned tasks, supporting relationship, current inputs and artifact versions, relevant decisions, changed assumptions, blockers, available support, authority, next expected action, escalation triggers.

A Grok should resume useful work from the local picture plus its tasks and artifacts — **without reading mission chat history**.

## 5. Executive assessment

Every COP produces one concise assessment of **significance**, not a restatement of state.

> Prototype implementation is on track, but the main effort has shifted to Red because an unresolved API consistency assumption blocks integration. Forge remains productive on independent work. Sentinel capacity is sufficient. Green reserve remains uncommitted.

**State and trajectory are separate.** `current_state: AT_RISK / trajectory: IMPROVING` is a real and useful combination. Trajectory is `IMPROVING | STABLE | DEGRADING | UNKNOWN`, derived from blocker movement, critical-path movement, verification results, resource pressure, incident state, and capability availability — never from task-count velocity.

**Mission status** (operational mode, distinct from task state): FORMING, RECONNING, EXECUTING, CONVERGING, VERIFYING, RECOVERING, REPLANNING, COMPLETE, SUSPENDED.

## 6. Main effort

Must be unmistakable. Carries: objective, supported element, decisive constraint, why now, support required, and **reconsider when**.

On change, the delta must show: old main effort → why it changed → new main effort → who is now supported → what resource priorities changed. Always high salience.

**Phase drives color demand** and explains otherwise confusing force composition: Recon → Red-heavy; Build → Blue-heavy; Recovery → Green-heavy; Verification → independent Red; Institutionalization → Purple.

Chromatic state shows dominant color, main-effort color, active providers per color, color bottlenecks, and recent transitions. Use color where it compresses meaning (`🔴 FINDING`, `🟡 MAIN EFFORT CHANGE`, `🔵 ARTIFACT READY`, `🟢 RECOVERY COMPLETE`, `🟣 ROUTINE CANDIDATE`) — never as decoration.

## 7. Force posture

Show the organization presently fielded: cells with objective, supported color, members, status; enablers; independent assurance; reserve; fragility; pending recomposition. Command should never have to query Force Generation manually.

Force posture is **temporal** — show current force and expected next force when a phase transition approaches ("at the verification gate, Sentinel attaches and Scout detaches"). This buys anticipation.

**Reserve** appears only when operationally relevant: provider, capability, reason held, commit trigger.

**Capability gaps** with mission consequence get promoted: capability, severity, affected objective, current mitigation, command attention. Never bury a mission-blocking competence absence inside Registry detail. Flag fragility explicitly — *⚠ Green recovery: single ready Q4 provider*.

## 8. Execution compression

OpsGraph may hold 200 tasks. The COP holds decisive tasks, critical path, blocking tasks, verification gates, and major completions. Everything else stays queryable in OpsGraph.

A task earns COP visibility only if its state could materially change mission completion, main effort, critical path, force allocation, or a human decision.

**Blockers** are classed MISSION / MAIN_EFFORT / CRITICAL_PATH / LOCAL. Only the first three get broad visibility; local blockers stay local unless they propagate. Each carries object, class, cause, owner, resolution condition, downstream effect, elapsed time, escalation status — answering *why movement stopped and what removes the condition*.

Resolved blockers leave the active view. History lives in OpsGraph and AAR.

**Critical path**: tasks, current blocker, estimated pressure, latest change. Do not state precise durations when estimates are weak.

## 9. Knowledge state

Never blur these five: `verified_facts`, `supported_but_unverified`, `assumptions`, `unknowns`, `contradicted`. The distinction must be explicit in the rendering, not implied.

Recon may produce dozens of findings. The COP elevates only verified mission-relevant facts, critical assumptions, decision-critical unknowns, contradictions, and terrain changes — not raw research.

**Critical assumptions** are those whose failure would invalidate the main effort, the architecture, an accepted output, or the mission design. Each carries statement, confidence, owner, verification status, consequence if wrong.

**Unknowns** are CRITICAL / MATERIAL / TOLERABLE. Show critical and selected material ones. High uncertainty is itself operational information — *"root cause unknown after two independent diagnostic paths"* may change force posture.

**Contradictions:** when two authoritative streams disagree, never silently pick one. Expose claim A, claim B, decision impact, resolution owner. The contradiction is the information.

**Confidence marking** (`VERIFIED | HIGH | MODERATE | LOW | UNKNOWN`) is used where uncertainty affects decisions — not sprayed across routine facts.

**Freshness:** volatile claims show age (`API status: verified 7 minutes ago`); some carry `valid_until` / `reverify_when`. Stable facts need neither.

## 10. Assurance

Compress Sentinel output into: mission confidence, passed decisive outputs, conditional outputs, failed blocking outputs, stale verifications, residual risk. This answers *what parts of current reality are actually trusted?*

**Mission confidence** is not an average of task states. It synthesizes confidence in decisive assumptions, verification of decisive artifacts, stability of critical interfaces, and known residual risk. Use `HIGH | MODERATE | LOW | UNESTABLISHED`. No fake percentages. Where useful, split by domain — technical HIGH, data MODERATE, operational LOW.

**Conditional truth must stay visible:** *"lease subsystem is verified provided datastore semantics remain version 4."* Downstream work depends on that condition.

**Verification is version-bound.** `PASS → material change → STALE`. A stale PASS must never keep rendering as trusted. If the artifact is still decisive, update immediately.

## 11. Decisions

Three horizons: **DECIDED**, **OPEN NOW**, **APPROACHING**.

Every open decision names who legitimately decides (human, Mission Command, cell lead, technical owner, Sentinel), and where applicable a `latest_useful_time` and `default_if_unresolved`. Cue decisions *before* they become blockers.

Broad discussion is not a substitute for decision authority.

Once a legitimate owner decides, record the decision but preserve any surviving uncertainty. "Command chose Route A" does not mean "Route A is objectively superior."

**Command attention** is isolated explicitly: what requires higher judgment now, why, and by when. Do not show the human seventeen agent updates that reduce to *no decision required; main effort continues*. Protect human attention aggressively.

## 12. Risk and resources

Distinguish **critical active**, **emerging**, and **accepted** risk. Do not list every conceivable failure.

A risk *may* occur; an issue *has* occurred. Never blur them.

Risk objects: statement, probability (qualitative unless numeric evidence exists), consequence, status, mitigation, owner, trigger, mission impact.

A risk becomes COP-worthy when signals show rising relevance — *verification queue growing + fixed Sentinel capacity + approaching release gate* = emerging assurance bottleneck.

**Resources** appear only where scarcity affects mission decisions (compute constrained, human approval pending, quota limited, Sentinel bandwidth saturated). Contention records competing demands, main-effort effect, decision owner — Yellow needs it, Blue usually does not.

## 13. Artifacts and interfaces

Only decisive artifacts enter the broad COP: artifact, version, state, verification, plus what changed and what is stale. Artifact Intelligence owns the full map.

**Interfaces** shared by multiple cells are marked `STABLE | PROVISIONAL | CHANGING | BROKEN` with version, consumers, owner, last change. This is what stops parallel cells from acting on incompatible assumptions.

An interface change is high salience and must **propagate impact**, not merely announce itself: affected cells → artifact invalidation → possible verification staleness.

## 14. Distribution

**Delta-first.** Default is *current local picture + material delta*. Agents already holding valid state need changes, not full rebriefs.

| Send | When |
|---|---|
| Snapshot | agent joins, agent recovers, major replan, drift suspected |
| Delta | normal continuous operation |

Every picture is **versioned** with the source versions it was built from. Recipients can then detect staleness — and a version gap is not automatically a reload; determine whether the intervening changes actually affect that agent.

For each material delta, compute what objects are affected and route only to owners, supporting cells, decision owners, and verification owners. That is information discipline.

**Event priority:**

| | |
|---|---|
| P0 CRITICAL | mission / authority / safety failure |
| P1 DECISIVE | main effort, critical path, major assumption |
| P2 MATERIAL | important local or cross-cell change |
| P3 ROUTINE | persist, never interrupt |

**Interrupt only** when the information invalidates current action, changes priority, changes authority, changes an interface, or reveals blocking risk. Otherwise update silently. Shared state exists to *reduce* interruptions.

**Progressive disclosure:** SUMMARY → DETAIL → RAW SOURCE, pulled on demand. High-consequence assertions carry provenance (`recon:PIR-03`, `sentinel:V-42`, `opsgraph:E-918`) so evidence can be inspected without being shipped.

**Update triggers** (immediate): main effort change, phase change, critical blocker, critical assumption invalidated, high-severity verification failure, force recomposition, critical capability loss, major interface change, human decision, mission status change. Routine task events batch.

Cadence is **event-driven**, not clock-driven. Periodic reconciliation still runs for consistency: COP references match canonical sources, no stale decisive entries, force matches Registry readiness, main effort matches command.

## 15. Fusion, not aggregation

Fusion requires semantic interpretation. Never paste three source lines side by side.

Raw:
```
Scout finds API incompatibility.
T42 becomes BLOCKED.
Forge stops integration.
Sentinel invalidates prior compatibility check.
```
COP delta:
> 🔴 **MAIN-EFFORT CHANGE** — The compatibility assumption is contradicted. Integration is blocked. Prior compatibility verification is stale. Red now owns resolution of the API contract. Blue continues independent implementation only.

Raw: *Green restores service; Sentinel verifies; four tasks unblock.*
> 🟢 **RECOVERY COMPLETE** — Service restored and independently verified. Downstream execution unblocked. Trajectory changed DEGRADING → IMPROVING. Green reserve may detach.

Every delta explains its **implication**, not merely its occurrence.

### Significance test

Does the event affect mission intent, main effort, critical path, authority, capability coverage, assurance, an interface, resource allocation, or a human decision? If none — it is local or background.

`Significance ≈ MissionImpact × Urgency × DecisionRelevance × Propagation`

### Assessment ≠ observation

Observation: *4 tasks waiting for Sentinel.* Assessment: *Sentinel capacity is likely to become the next critical constraint.*

Both are useful. The COP may generate assessments, but must mark them as assessments with their basis and confidence. Never present interpretation as observed fact.

## 16. Consistency and honesty

The COP is a useful cross-subsystem sentinel. Check main effort vs supported element, OpsGraph completion vs Sentinel result, Registry readiness vs force membership, artifact version vs verification version.

Impossible combinations (`task COMPLETE` + `required verification FAIL`) emit `COP_INCONSISTENCY`. Do not hide it.

When canonical sources conflict, expose sources, disagreement, operational effect, and resolution owner. **The COP must not invent reconciliation.**

If source state is incomplete, say so: `completeness: PARTIAL, missing: [Green-2 readiness]`. Never produce false coherence. **UNKNOWN beats a silent omission that implies health.**

**Common picture ≠ consensus.** Maintain shared facts plus explicit competing assessments where they matter — *Red thinks the database is the bottleneck, Blue does not, here is the evidence needed* — which itself cues Recon.

## 17. Continuity

**Drift** is an agent's internal model diverging from mission reality — acting on an old interface, pursuing a superseded task, using an invalidated assumption, asking a resolved question. When an agent emits an event referencing a stale version, return `STATE_UPDATE_REQUIRED` before it takes substantial incompatible action.

**Context loss recovery:** load doctrine → load local COP → load owned tasks → load decisive artifacts → continue. Enough for most recoveries without reading old chat.

**New provider joins** with: mission purpose, cell objective, main effort, supported/supporting relationship, current state, decisive assumptions, required interfaces, owned task, recent relevant deltas. Not full mission history.

**Handoff:** the COP supplies situational understanding (purpose, state, main effort, task, important changes, assumptions, artifact versions, risks, open questions); OpsGraph owns the transaction semantics.

**Disconnected operation:** freeze a local picture (version, intent, local objective, known state, assumptions, authority, sync conditions) before going offline. On reconnect, run local events against current COP → delta analysis → conflicts → reconcile. Never blindly overwrite either side.

## 18. Security

Not every agent needs every sensitive datum. Role views respect authority, permissions, and mission relevance.

Never copy secrets, credentials, or tokens into shared COP state. The COP may say *"external credential dependency unresolved"* without exposing the credential.

## 19. Anti-patterns

| Anti-pattern | Why it fails |
|---|---|
| **Dashboardism** — 40 charts, 70 metrics, all-green lights | Metrics that do not change decisions are noise |
| **Raw log stream** | A firehose is not a picture; fusion and priority are the job |
| **Chat summary** | Records what was said, not what is true now |
| **Single giant context** — federation-wide dump to everyone | Destroys attention, context budget, specialization |
| **False green** — "healthy" on task counts while the decisive assumption is unverified | Mission status follows decisive effects |
| **Warning saturation** | If everything is urgent, nothing is salient |
| **Historical clutter** | Closed blockers and superseded decisions crowd out present reality |
| **Duplicate truth** — maintaining a parallel mutable copy of OpsGraph state | Guarantees divergence; reference and materialize instead |
| **Interpretation as fact** | Destroys the ability to audit reasoning |
| **Over-notification** — waking five Groks for one background completion | Update state; notify only affected elements |
| **Commander as status poller** | If command must ask "what is everyone doing?", the COP failed |
| **Agent as status reporter** | Agents emit structured events; the COP writes prose, not them |
| **Perfect picture delusion** | The goal is sufficient shared understanding for current decisions, not omniscience |

## 20. Sizing

**Minimal** (small mission): purpose, main effort, current state, owner, blocker, latest change, done when. No dashboard.

**Standard**: mission, phase, main effort, force, decisive tasks, blockers, critical assumptions, mission confidence, risks, decisions, changes since last picture.

**Full**: the complete model, used selectively for multiple cells, high consequence, dynamic force, scarce resources, multiple decision owners, or rapidly shifting terrain.

## 21. Generation and loop

```
LOAD command → opsgraph → recon → force → capability → assurance → resources
  → IDENTIFY main effort, decisive tasks, knowns/unknowns, risks, open decisions, material changes
  → DETECT source conflicts → ASSESS situation
  → GENERATE master picture → role views → DISTRIBUTE relevant deltas only
```

Live loop: canonical event → impact analysis → COP-worthy? → if no, persist silently; if yes, update master picture → identify affected recipients → generate deltas → distribute.

## 22. Quality checks

**Master picture** must answer: what is the mission, what phase, what is the main effort, who is supported, what is the decisive constraint, what is blocked, which critical assumption is least secure, what can we trust, what changed, what requires a decision, what capability is missing, what is our reserve, where is this heading. If it cannot, it is not operationally useful.

**Local picture** must answer: why am I here, what do I own, what is currently true that affects me, what changed, who supports me, what interfaces must I respect, what output is expected, what triggers escalation, what do I do next.

**Command picture** must answer: are we on track, what is decisive, what is at risk, is the force correctly composed, do we need to shift resources, what requires my judgment — and **can I remain quiet?** If the last answer is yes, the COP is working.

Accuracy outranks presentation: a polished summary built on stale data is worse than an ugly correct snapshot. Timeliness outranks completeness for volatile state — correct information delivered after the decision is worthless. And relevance outranks truth-in-the-abstract: *"Scout completed the repository map yesterday"* is true and useless if the architecture has since changed.

## 23. Metrics

Stale-picture incidents, decision-relevant update latency, context-reconstruction time, duplicated status requests, agent state divergence, missed critical deltas, irrelevant interruptions, command attention events, mission drift events, source conflicts detected, compression ratio.

Compression ratio (raw state ÷ decision-relevant state) should be high — but never at the cost of losing mission significance. Measure delivered items against items that actually affected a recipient's decision. The goal is relevance, not visibility.

The ultimate measure: **how often can a competent Grok take the correct next action without asking someone to reconstruct the situation?**

## 24. Constitution

1. The COP represents current mission reality, not conversation history.
2. Canonical sources stay authoritative; the COP fuses, never duplicates ownership.
3. Common truth does not require identical views — but views must never contradict.
4. Distribute by decision relevance; every element gets the minimum sufficient picture.
5. Strategic, operational, and local pictures are distinct.
6. Main effort and supported relationships must remain unmistakable.
7. Compress task lists into decisive operational state.
8. Facts, assumptions, unknowns, contradictions, and assessments stay distinguishable.
9. Mission confidence follows decisive evidence, not task volume.
10. Verification is version-bound; stale confidence must be visible.
11. Risks and active issues are different.
12. Resources and capability gaps appear in proportion to mission consequence.
13. Interface changes propagate to affected consumers with their implications.
14. Delta is the default; snapshots are for joining, recovery, replan, or drift.
15. Every picture is versioned and agents know when theirs is stale.
16. High-salience interruption requires high decision relevance; routine state updates silently.
17. Fuse multiple source events into one meaningful statement.
18. Assessment never masquerades as fact.
19. Source conflicts are exposed, not silently reconciled.
20. A partial picture says it is partial; UNKNOWN beats false certainty.
21. Common picture does not mean forced consensus; decision authority is separate from truth.
22. The human sees decisions, risks, and significance — not agent chatter.
23. Command should not poll; agents should not write status prose.
24. Historical clutter leaves the active picture.
25. The COP succeeds when the federation sees one reality while acting through many autonomous local perspectives.

## Done when

A Grok joining this mission does not ask *"what has everyone been talking about?"* — it reads its picture and knows:

> The mission is X. We are in phase Y. The main effort is Z because that constraint is decisive. This cell is supported. These facts are verified; these assumptions remain open. This interface changed and my task depends on it. Sentinel has not yet accepted the current artifact. Green reserve is available. No human decision is presently required.

That is shared orientation — what lets decentralized execution stay coherent without continuous central control.
