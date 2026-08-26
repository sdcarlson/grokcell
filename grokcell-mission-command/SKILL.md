---
name: grokcell-mission-command
description: >-
  Use when turning an ambiguous objective into durable mission intent — purpose,
  end state, priority stack, authority envelope, main effort, risk posture,
  escalation conditions, and termination criteria — so cells can execute without
  supervision while staying aligned.
---
# GrokCell Mission Command

🟡 Yellow. Intent, authority, and decentralized execution. Version 1.0.0.

**Unity of purpose + local freedom of action + fast decision loops + bounded risk.**

Mission Command does not tell every Grok what to do. It creates the conditions under which a competent subordinate can answer:

> **What should I do now, even if nobody can tell me?**

| Command governs | Command does not govern |
|---|---|
| why, what matters, what must be true at the end, what must not happen, who may decide what, where resources concentrate, when higher judgment is required | exact implementation, tool choice, internal sequencing, every subordinate task, routine local adaptation |

**The command layer should become less active as subordinate understanding becomes stronger.**

## Fast path

1. **Simple mission** → minimal packet: mission, purpose, done-when, priority, autonomous, approval-required. **Command complexity scales with mission complexity.**
2. **The intent, priority stack, or a decision principle already resolves it** → decide locally. Do not escalate.
3. **Reality invalidated the method** → adapt locally, register the deviation, notify if material.
4. **Genuine value judgment, authority gap, or risk beyond tolerance** → escalate **decision-ready**, with options, a recommendation, and a default if no response.
5. **Multi-cell, contested resources, material consequence, persistent, shifting priorities** → full packet.

**Never institutionalize paperwork for trivial missions.**

## 1. Command ≠ control

| **Command** — judgment | **Control** — information processing |
|---|---|
| purpose, desired outcome, priorities, acceptable risk, authority, main effort, strategic tradeoffs, termination | task state, ownership, dependencies, resource state, leases, deadlines, artifacts, synchronization, telemetry |

**Do not spend high-value reasoning on bookkeeping software can do deterministically. Do not ask deterministic infrastructure to make value judgments it cannot legitimately make.**

| Centralize | Decentralize |
|---|---|
| intent, priorities, authority policy, shared truth, scarce-resource decisions | execution, local decomposition, methods, sequencing, routine tradeoffs, adaptation |

**The commander's job is not to eliminate uncertainty — it is to make aligned action possible despite it.**

## 2. The three-part mission

| | Question | Example |
|---|---|---|
| **TASK** | What is accomplished now? | Construct a working prototype of the proposed architecture |
| **PURPOSE** | Why does it matter? | Determine whether the architecture is viable before committing the project to it |
| **END STATE** | What observable condition means success? | A representative prototype exists, critical assumptions are tested, limitations documented, and a go/revise/reject decision can be made from evidence |

Ordering: `PURPOSE → END STATE → TASK → METHOD`.

- Circumstances invalidate the **method** → preserve the task.
- Circumstances invalidate the **task** → preserve the purpose and end state.
- The **purpose** changes → the mission requires re-commanding.

## 3. Compiling intent

Human requests arrive as *"figure this out," "make this better," "get this ready."* Convert them into durable intent:

- **Purpose** — what larger result is this serving?
- **Key effects** — the few conditions that must be created.
- **Success image** — what reality looks like when done, **independent of method**.

**Keep intent stable. Plans change frequently; intent should not.**

### Intent quality test

| Test | Question |
|---|---|
| **Durable** | Would it remain useful if the original plan failed? |
| **Discriminating** | Does it help choose between two plausible actions? |
| **Compact** | Can a subordinate keep it active without loading a document? |
| **Outcome-oriented** | Does it describe effects rather than procedures? |
| **Bounded** | Are important prohibitions clear? |
| **Traceable** | Can every major subordinate objective explain how it serves this? |

Fails any → rewrite the intent.

### Compiler

```
RAW REQUEST → what does the user actually want to become true?
  → what few conditions define success? → what tradeoffs are implied?
  → what may the cell decide without asking?
  → what could cause harm, waste, or mission drift?
  → what would require human judgment?
  → what is the initial decisive constraint? → MISSION COMMAND PACKET
```

## 4. Priorities and principles

**"Everything is important" is command failure.** Define an ordered stack wherever tradeoffs are likely:

> 1. correctness · 2. evidence · 3. delivery speed · 4. elegance

Meaning *correct but inelegant beats elegant but incorrect* — **without requiring approval**.

**Priorities are decision compression** — they let local agents resolve future tradeoffs using prior command judgment.

**Decision principles** encode repeated tradeoffs so they never become permission requests:

> Prefer reversible implementation choices while core assumptions remain uncertain. · Prefer evidence from the actual environment over generalized assumptions. · Reuse verified existing infrastructure before constructing replacements. · Do not increase complexity unless it removes a demonstrated constraint.

**Command by negative space:** sometimes autonomy is best expressed as what *not* to do — *do not redesign unrelated modules, do not introduce a dependency without demonstrated need, do not modify protected configuration, do not optimize before correctness* — then leave everything else open.

## 5. Control mode

| Mode | Use when | Specify |
|---|---|---|
| **MISSION** | outcomes matter more than methods; multiple valid approaches; local information changes fast; work decomposable; actions reversible; competence strong | purpose, end state, priority, constraints, authority — **leave method local** |
| **HYBRID** | local initiative useful but some interfaces need synchronization; meaningful consequences; shared dependencies | intent, local freedom, interfaces, decision gates, approval boundaries |
| **DETAILED** | procedural task; exact reproducibility; synchronization dominates; deviation unacceptable; compliance; unusual irreversibility | the necessary procedure — **and do not generalize it beyond the component that requires it** |

**Default: MISSION where possible, HYBRID where necessary, DETAILED only where justified.**

## 6. Authority

**Autonomy without explicit authority produces hesitation. Authority must be legible.**

| Category | Meaning | Examples |
|---|---|---|
| **AUTONOMOUS** | decide and execute without asking | local decomposition, internal sequencing, reversible modifications, routine research, tool choice, temporary subcells |
| **EXECUTE AND NOTIFY** | act immediately, register the action | changing a significant internal interface, reallocating attached specialists, abandoning a planned branch, deviating from a noncritical assumption |
| **APPROVAL REQUIRED** | do not execute until authorized | irreversible external publication, spending above limit, destructive modification of protected assets, consequential scope expansion |
| **PROHIBITED** | not authorized under this mission | bypassing safety constraints, silently altering strategic objectives, **concealing material mission failure** |

**Decision rights vary by class** — implementation to the supported cell (autonomous); internal architecture to the technical lead (notify when shared interfaces change); mission priority reserved to command; verification acceptance to Sentinel (independent); external irreversible action to the human (approval).

The objective is `DECISION → LOWEST COMPETENT OWNER`, never `DECISION → HIGHEST AVAILABLE AUTHORITY`.

### Reversibility as the generic autonomy rule

| | Class | Default |
|---|---|---|
| R0 | trivial / immediately reversible | local authority |
| R1 | reversible at negligible cost | local authority |
| R2 | reversible with meaningful rework | local or notify-after |
| R3 | difficult or externally visible to reverse | explicit delegated authority or approval |
| R4 | effectively irreversible | human or designated authority |

This gives a general rule without enumerating every possible action in advance.

### Competence-aware autonomy

`Autonomy = f(competence, reversibility, intent clarity, consequence, interdependence)`

High competence + high reversibility + clear intent → high autonomy. Low confidence + high consequence + ambiguous intent → tighter control. **Tighten only where needed — never permanently reduce autonomy over one narrow weakness.**

**Trust is empirical and capability-specific:** mission alignment, completion reliability, evidence quality, escalation judgment, authority compliance, adaptation quality, verification history. High trust justifies broader authority, fewer checkpoints, larger scope; low trust justifies narrower authority, stronger verification, smaller scope, more support.

## 7. Disciplined initiative

A subordinate adapts without waiting when: existing instructions no longer fit reality, the purpose remains understood, the action serves the end state, it stays within authority, **and delay would reduce mission value**.

Then: `ACT → REGISTER DEVIATION → UPDATE COMMON STATE → NOTIFY IF MATERIAL`, recording previous plan, changed condition, action taken, intent alignment, authority basis, expected effect.

**Do not punish justified adaptation by demanding retrospective permission for a properly delegated decision.**

**Two-level-up:** every cell knows its task, the parent purpose, and the strategic purpose.

> Task: build a benchmark harness → Parent: determine whether architecture B outperforms A → Strategic: choose the architecture most likely to support the next phase.

**This is what makes useful initiative possible when local conditions change.**

**Nested intent:** `USER → FEDERATION → MISSION → CELL → TASK`. Every level answers *how does my purpose serve the purpose above me?* **No coherent answer means the task is probably misaligned.**

## 8. Main effort and support

> The mission component whose success currently contributes most directly to the end state, and therefore receives preferential support.

Carries objective, supported element, rationale, priority access, and **reconsider when**. Main effort is **temporary** — it migrates as the decisive constraint migrates.

**Supporting efforts** name what they support and the minimum effect they must provide. **Supporting elements must know what they support** — otherwise they optimize locally in ways that do not help the mission.

**Resources follow marginal mission value, not even distribution and not personalities.** Specify priority access for the main effort, protected reserve, and constrained resources — notably **human attention: use only for value judgment, irreversible action, mission conflict.**

**Reserve is optionality, not idle bureaucracy** — it exists to exploit unexpected opportunities, sudden bottlenecks, failures, new evidence, verification surges, and changed priorities. **Do not preserve it mechanically when the mission clearly requires full commitment.**

## 9. Risk and uncertainty

Express **acceptable** risk, never merely "be careful":

> reversible internal error: moderate · wasted compute: moderate · broken dev branch: low · protected data loss: near zero · unauthorized external action: zero

> *Prefer rapid reversible experimentation while preserving protected assets and requiring approval for irreversible external effects.*

**A research exploration and a production migration must not receive identical authority envelopes.**

### Uncertainty policy

| Class | Handling |
|---|---|
| **EXPLORABLE** — cheaply resolved by research, test, experiment | investigate locally |
| **REVERSIBLE** — mistakes cheap to undo | act, measure, adapt |
| **CONSEQUENTIAL** — wrong assumptions would materially alter the mission | verify before commitment |
| **VALUE-LADEN** — requires preference, not discovery | escalate to the legitimate decision owner |

**This is what stops agents asking humans factual questions they can answer themselves.**

## 10. Escalation

**Command information requirements** are the few facts that could materially change higher-level decisions — evidence the primary technical assumption is invalid; discovery that the end state is unreachable within current authority; resource conflict threatening the main effort; verification failure indicating the accepted architecture is unsound; a newly discovered alternative with materially higher expected value. **Everything else stays local.**

**Escalation filter — before escalating, ask:** can this be resolved through existing intent? the priority stack? decision principles? existing authority? local experimentation? direct liaison? available evidence? **Yes → do not escalate.**

**Classes:** VALUE (a legitimate preference decision — *both designs work; one favors simplicity, one extensibility*) · AUTHORITY · RISK · INTENT (purpose ambiguous or contradictory) · PRIORITY · RESOURCE · TERMINATION.

**Never escalate an unprocessed problem.** Send: class, decision required, why local resolution is insufficient, relevant context, options with effect/cost/risk, **recommendation**, default if no response, latest useful decision point.

**The higher authority must be able to decide without reconstructing the entire mission.**

**Default-if-no-response** prevents paralysis: reversible work continues · research continues · high-cost commitment pauses · irreversible action does not execute · protected assets preserve current state.

## 11. Mission orders and updates

A subordinate order carries only what is needed for aligned autonomous execution: task, purpose, end state, priority, constraints, authority, supported by, supporting, outputs, verification, **report only if**. **Avoid prescribing method** unless synchronization, procedure, or risk requires it.

**Command handshake** — before major autonomous execution the receiving cell validates that it understands the mission, purpose, end state, priority stack, main effort, its authority, its prohibitions, what requires escalation, and what evidence counts as complete. **Computed and recorded silently — no conversational ceremony. Surface only unresolved material ambiguity.**

**Shared understanding test:** command has failed if agents independently interpret the mission in materially incompatible ways. Where ambiguity risk is high, compare concise restatements of purpose, expected end state, primary constraint, local authority — and resolve divergence early. **Do not repeatedly rebrief once understanding is established.**

**Issue deltas, not rewrites.** A command update names what it supersedes, the previous and new value, the reason, downstream effect, and whether acknowledgement is required. Everything unchanged remains valid.

Common deltas: main effort changed · priority changed · constraint added · authority expanded · resource withdrawn · assumption invalidated · end state modified.

**Propagate by impact:** command change → affected tasks, cells, assumptions, resources, verification → **replan only the affected region.** Never restart the organization from zero.

## 12. Exception-based command

Higher command should normally hear about: mission-changing discovery, authority exception, major risk, main-effort failure, cross-cell conflict, termination condition.

**Not** every search, file changed, minor implementation choice, passing test, or local decision.

**Silence from a healthy cell is not a problem.** The common operational picture provides visibility without conversational reporting.

**Command friction is a real cost.** Every approval, report, briefing, handoff, and synchronization consumes mission capacity. If an exchange does not alter a decision, prevent material conflict, transfer necessary knowledge, allocate resources, change authority, or reduce significant uncertainty — **remove it**.

**Command span:** do not create cells faster than command can maintain coherent intent and allocation. If one node is managing too many unrelated efforts, **do not add reporting** — group missions, delegate subcommand, clarify intent, automate control, or separate the federation. **A command node governs decisions, not tasks.**

## 13. Completion and termination

**Success is measured in effects, not activity.** Not *"researched topic, wrote code, ran tests"* but *"the technical uncertainty preventing the decision has been resolved."* State the observable effect, the required evidence, and the acceptance method.

**Verification command** sets *how much confidence is required*, not how Sentinel achieves it: required level, what must be established, acceptable residual uncertainty. **Never command tests that do not serve a decision.** For high-consequence decisions, verification authority stays meaningfully independent of the executing cell.

**Terminate explicitly** on: end state achieved and verification passed · a critical constraint making the end state unreachable · strategic objective superseded · expected additional value below cost · explicit human stop.

**Do not let mission inertia consume resources after the objective no longer justifies them.**

**Abort / pivot:** cells may recommend reassessment with original assumption, new evidence, impact on end state, options (continue / modify / pivot / terminate), recommendation, authority required. **If the pivot preserves intent and stays inside delegated authority, pivot locally. If it changes strategic purpose, escalate.**

## 14. Interfaces

| System | Command supplies → System owns |
|---|---|
| **ODA** | mission, purpose, end state, priorities, main effort, constraints, authority, risk, information requirements, verification standard, escalation triggers → local organization, subtasks, split/merge, liaison, enabler requests, method, sequencing. **Do not invade ODA responsibilities** |
| **Recon** | *what decision must this reconnaissance enable?* — never "research everything about X" → terrain, knowns, unknowns, critical assumptions, existing assets, constraints, mission shapes, capability needs. Command may then revise the packet |
| **Force Generation** | objective, priority, main effort, risk, authority, resource ceilings → minimum viable detachment, attachments, reserve, supported/supporting relationships |
| **OpsGraph** | mission-level objectives → task state, ownership, dependencies, leases, blockers. **Observe task state without becoming the scheduler** |
| **Sentinel** | what must be trustworthy, and how consequentially → how to establish that confidence |
| **COP** | intent, priority, authority, main effort, command decisions → facts, tasks, owners, artifacts, risks, resources, mission state. **Command decisions reference current shared state, never conversation** |

## 15. Failure diagnosis

When a cell fails, diagnose **why** before changing the architecture:

| Cause | Meaning |
|---|---|
| INTENT | did not understand purpose |
| CAPABILITY | lacked required competence |
| RESOURCE | lacked tools or capacity |
| CONTROL | dependencies and state poorly managed |
| AUTHORITY | could not act without excessive escalation |
| VERIFICATION | bad work was accepted |
| EXECUTION | had what it needed and performed poorly |

**Do not respond to every failure with tighter centralized control.** Centralization is appropriate only when it addresses the actual cause.

### Command failure modes

| Failure | Result |
|---|---|
| **Micromanagement** — specifying how competent cells do ordinary work | latency ↑, initiative ↓, command bottleneck ↑ |
| **Vague intent** — "make it good" | local optimization, divergent interpretations, rework |
| **Authority ambiguity** | permission-seeking, hesitation, shadow decisions |
| **Priority inflation** — everything is P0 | no real priority exists |
| **Status addiction** — information requested but not used for decisions | reporting burden, context pollution, less execution |
| **Planning rigidity** — original sequence preserved after assumptions changed | **obedient failure** |
| **Autonomy dogma** — decentralizing despite high coupling or irreversible risk | integration failure |
| **Control dogma** — centralizing because centralized visibility exists | coordination saturation |

## 16. Sequence

```
PARSE objective → recover strategic context → identify purpose → define end state
 → identify critical constraints → construct priority stack
 → estimate risk and reversibility → select control mode → define authority envelope
 → identify initial main effort → identify information requirements
 → define escalation conditions → define verification standard
 → ISSUE PACKET → hand to Recon / Force Generation / cell
```

**Do not overplan implementation before reconnaissance** unless the environment is already well understood.

**Then run an exception-driven loop:** intent → decentralized execution → common state → material change? → no: continue; yes: does it require command judgment? → no: local adapt; yes: update command. **The commander's default state is not intervening.**

## 17. Checks

**Commander's check:** Do they know why? What success looks like? What matters most? What they may decide? What they may not do? When you need to know? Do they have what they need? **Am I specifying method without a real reason? If I disappear, can they continue usefully?**

If the last answer is no, **command is incomplete**.

**Subordinate check before escalating:** What does the intent imply? The priority stack? Is this within my authority? Is the action reversible? Can evidence resolve it? Can I coordinate laterally? Would delay reduce mission value? **Does this actually require a value judgment?**

## 18. Metrics

Clarification requests ↓ · unnecessary escalations ↓ · authority violations → zero · intent alignment ↑ · decision latency ↓ · replanning cost ↓ · mission completion ↑ · command overhead ↓ · local adaptation quality ↑ · human attention per mission ↓.

`CommandEfficiency = aligned autonomous decisions ÷ (interventions + clarification requests + coordination burden)`

**The strongest signal of good mission command:** *subordinate cells encounter situations that were never explicitly predicted and still choose actions the commander would endorse.*

## 19. Constitution

1. Purpose outranks procedure; intent survives the failure of the original plan.
2. Every mission requires an observable end state.
3. Priorities exist to resolve future tradeoffs; authority must be explicit enough to enable action.
4. Decisions belong at the lowest competent level; centralized visibility does not imply centralized execution.
5. Local initiative is expected when reality invalidates instructions — and must stay aligned with intent and authority.
6. Main effort receives preferential support; supporting activity exists to increase mission effect, not local metrics.
7. Resources follow mission value, not organizational ownership; reserve preserves the ability to adapt.
8. Human attention is a strategic resource.
9. Escalate decisions, not raw problems; communicate exceptions rather than narrating execution.
10. Use detailed control only where coupling, procedure, or consequence requires it.
11. Replan affected regions rather than restarting missions.
12. Verification intensity follows consequence.
13. **Command should make itself progressively less necessary.**

## Done when

Mission Command succeeds when higher authority can become **quiet**. The ideal command system does not produce dependent agents — it produces **aligned autonomous action**:

```
CLEAR INTENT → SHARED UNDERSTANDING → BOUNDED AUTHORITY
  → DECENTRALIZED DECISION → FAST LOCAL ADAPTATION → VERIFIED MISSION EFFECT
```

Command intervenes only where its unique judgment creates more value than local initiative. When choosing between **more instructions** and **better intent, better priorities, clearer authority, better shared state** — prefer the second.

A cell should know enough of the mission, hold enough authority, and understand enough of the commander's priorities that when instructions stop matching reality, **the mission does not stop with them.**
