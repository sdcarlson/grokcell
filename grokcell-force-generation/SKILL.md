---
name: grokcell-force-generation
description: >-
  Use when forming a mission cell, deciding whether to add or remove a provider,
  splitting or merging cells, replacing a failed agent, or checking whether the
  current organization still fits the problem. Compiles capability and color
  requirements into the smallest viable force.
---
# GrokCell Force Generation

The organizational compiler. Version 1.0.0.

**What is the smallest, strongest, correctly composed organization we should field for this mission right now?**

Never "how many agents can we use?" — always "what combination of capabilities creates the required effect with the least coordination burden?"

`maximize: Mission Effect ÷ (Agent Time + Coordination + Compute + Human Attention)`

**The organization follows the problem. The problem is never forced through a favorite organization.**

## Fast path

Stop at the first rung that holds.

1. **One obvious qualified, ready provider** → assign it. No optimization. Most tasks stop here.
2. **A validated routine or tool covers the capability** → use it instead of an agent.
3. **One cross-trained provider covers every required color** → solo cell, unless independence is required.
4. **Independence, parallelism, or a genuinely absent capability is required** → add exactly the provider that supplies it.
5. **No provider satisfies a critical requirement** → declare the gap. Never invent competence.

**The marginal-provider test.** Before adding anyone: *what specific bottleneck does this remove? What new capability does it add? What parallel work does it unlock? What failure does it protect against?* No answer → do not add.

## 1. Not staffing

Staffing asks *who is free?* Force Generation asks: what effects are required, what capabilities produce them, which must coexist, which must stay independent, which provider combination covers them, what stays in reserve, what is the coordination cost, what happens if one member fails — **and only then**, who deploys.

```
MISSION → MISSION SHAPE → CAPABILITY REQUIREMENTS → CHROMATIC REQUIREMENTS
  → CONSTRAINTS → AVAILABLE PROVIDERS → CANDIDATES → FITNESS → MINIMUM VIABLE CELL
```

Deterministic where possible, judgment-driven where necessary.

## 2. Request and package

**Input — force generation request:** mission purpose and end state, main effort, problem shape, decomposability, required capabilities, chromatic requirements (dominant, supported, supporting, independent assurance, conditional), authority, resource constraints, risk posture, assurance level, existing cells, reserve requirements, urgency, expected duration.

Infer missing values from Mission Command, Recon, and the Registry. **Do not ask the human for information the federation already holds.**

**Output — force package:** supported element, cell lead, members, color signature, capability coverage, attached enablers, independent assurance, reserve, command relationships, task subgraph, authority envelope, expected coordination cost, capability gaps, fragility, **formation rationale**, `recompose_when`, `dissolve_when`.

This is an operational object, not a recommendation.

## 3. Minimum viable GrokCell

> The smallest combination of providers that safely satisfies the mission's capability, independence, resilience, authority, and coordination requirements.

`minimize Cost(C)` subject to `Coverage ≥ Requirement`, `Independence satisfied`, `Authority sufficient`, `Readiness sufficient`, `Fragility ≤ tolerance`.

**Small is not automatically better. Small is better when the required effects stay covered.**

Always derive required capabilities *before* querying who exists — otherwise design gets biased toward whoever is visible.

## 4. Compiling color into providers

| Mission shape | Signature |
|---|---|
| Unknown implementation | uncertainty 🔴 → construction 🔵 → independent acceptance 🔴 |
| Unknown system failure | diagnosis 🔴 + recovery 🟢 → verification 🔴 |

Color describes function; it never implies one agent per color. Required 🔴🔵🟢 covered by Agent A (🔴🔵) + Agent B (🟢) is **complete coverage** — do not add a third agent for symmetry.

**Dominant color ≠ supported color.** A mission may be dominantly 🔵 while the supported element is 🔴 because an unknown interface is the current bottleneck. **Reinforce the supported element even when its color differs from the mission's overall mode.**

Every package names one supported element and states what effect each supporting element produces. Supporting elements increase the supported element's effectiveness; they do not become co-owners of the result.

## 5. Coverage

Classify every requirement:

| | |
|---|---|
| CRITICAL | mission cannot safely succeed without it |
| HIGH | strongly affects success probability |
| USEFUL | improves efficiency or quality |
| OPTIONAL | nice to have |

Only CRITICAL and selected HIGH requirements should drive initial cell size. Never bloat a team with optional capabilities.

**Coverage is not average strength.** One absent critical capability makes coverage INCOMPLETE no matter how exceptional the cell is elsewhere.

## 6. Providers

Candidates are AGENTS, ROUTINES, TOOLS, SERVICES, or EXTERNAL ENABLERS. Not every capability needs a Grok.

**Prefer a validated deterministic provider for deterministic work; prefer a reasoning agent where ambiguity, adaptation, or judgment matters.** The cheapest reliable provider that meets requirements generally wins.

If the Registry offers `routine: Q4 schema validation, cost minimal` alongside `Scout: Q4 schema validation, cost high`, take the routine. **Protect agent cognition for work machines cannot already do reliably.**

### Same agent or another agent

| Same agent | Another agent |
|---|---|
| capability validated | independent assurance required |
| task small | parallelism materially useful |
| context continuity valuable | specialized competence significantly better |
| parallelism unnecessary | work can safely split |
| independence unnecessary | cognitive separation has value |

**Independence is structural and non-negotiable.** A Forge at 🔵 Q5 / 🔴 Q4 could build and verify — but if assurance is independent A3, add a second qualified Red provider. Headcount minimization never erases required independence.

**Cross-trained agents are the enabler of small cells** — they cut handoffs, context transfer, synchronization, and size. Value T-shaped capability, but only on Registry evidence.

**The omni-agent penalty is real:** excessive skill loading, no verification independence, context saturation, single-point failure, mission interference. The goal is the minimum coherent cell, not one super bot.

## 7. Coordination and coupling

Every added provider costs communication, handoffs, synchronization, context transfer, conflict, and state management.

`CoordCost ≈ Handoffs + Sync + SharedStateContention + ContextTransfer`

Never optimize capability strength while ignoring organizational friction.

**Decomposability drives structure** (Recon supplies the assessment):

| Decomposability | Formation |
|---|---|
| High — independent outputs, stable interfaces, limited shared state | split aggressively |
| Medium | small cell + explicit synchronization |
| Low | keep reasoning integrated |

Tightly coupled work gets *worse* with more agents. **Do not create fake parallelism.**

## 8. Selection

For nontrivial missions generate **1–3** plausible packages — not dozens. E.g. *A: 2 agents, high context continuity* · *B: 3 agents, strong specialization, higher coordination* · *C: 2 agents + routine, lowest cost, slightly weaker adaptability*.

`Fitness ≈ Coverage + Readiness + Complementarity + ContextAffinity + Reliability + Resilience − CoordinationCost − LoadPenalty − ScarcityCost − IndependenceViolations`

A reasoning framework — do not pretend arbitrary coefficients produce objective truth.

**Every formation explains itself:** why these providers, why this size, why this supported element, why these colors, why these enablers, why this reserve, what alternative was rejected. Compact rationale makes debugging and AAR possible.

### Filters before fitness

- **Authority** — `min(Registry ceiling, Mission Command grant)`. Never field a cell that cannot operationally perform its own mission.
- **Tools** — repositories, browser, terminal, APIs, services, environment. Never discover a tool gap after formation when the Registry already knew.
- **Environment** — a Q3 provider already inside the repository may beat a Q4 provider with zero context for a small urgent task. **Reason in total mission latency.**
- **Load** — an overloaded expert loses to a slightly weaker ready provider. Capability is only useful if deployable.

If ideal capability is unavailable, declare it: missing capability, substitute, added risk, mitigation, command approval required. **Never let degraded coverage be presented as full coverage.**

## 9. Mass, economy, reserve

**Main effort gets the strongest justified capability.** If the decisive constraint is the core concurrency model, committing the Q5 distributed-systems Grok is correct. Do not preserve an expert in reserve while the decisive constraint stays blocked.

**Economy of force:** secondary efforts get *minimum sufficient* capability. Resources follow mission effect.

**Scarcity is opportunity cost.** Spending the only Q4 recovery provider on routine debugging may leave the federation without strategic recovery reserve. Account for it.

**Reserve is capability-specific**, not generic — a mission on unstable infrastructure needs Green reserve more than another Blue builder. Reserve may be agents, capabilities, compute, tool quota, or human attention. Ask: *what uncertainty could require rapid reinforcement?*

**Reserve is not sacred.** Commit it when the main effort is blocked, a high-value opportunity appears, a critical provider is lost, verification surges, or priority changes. **A reserve never used while the decisive effort fails is organizational waste.**

**Conditional enablers** attach on a trigger (`attach_when: migration-path-selected`), which avoids early bloat. Every attachment carries purpose, authority, expected duration, and `detach_when`.

**Detach** when the output is delivered, the capability is no longer decisive, the phase changed, marginal contribution is low, or another element needs the scarce capability more. Temporary enablers must never become permanent bureaucracy — and a cell must not hoard a specialist whose local contribution is now marginal while another cell has decisive need.

## 10. Recomposition

Formation is continuous, not one-time: *does the current organization still match the current problem topology?* Actions: REINFORCE, REDUCE, SPLIT, MERGE, ATTACH, DETACH, REASSIGN, REPLACE, SHIFT SUPPORT.

**Triggers:** main effort changes, critical assumption invalidated, decomposability changes, capability gap discovered, agent fails, tool access changes, repeated verification failure, major phase completes, resource constraint changes, new high-value branch appears. **Not every trivial event.**

| Action | When |
|---|---|
| **Reinforce** | `ExpectedMarginalEffect > CoordinationCost` — critical path blocked, capability queue growing, supported element overloaded, clearly independent parallel branch, verification bottleneck. Add *the capability that removes the constraint*, not another generic Grok |
| **Reduce** | uncertainty resolved, phase complete, coordination cost rising, capability no longer required, routine replaced agent work. Smaller organizations regain tempo |
| **Split** | independent objectives, dropping dependency density, low artifact contention, each subcell retains sufficient color coverage — plus purpose, authority, inputs, owner, capabilities, sync conditions |
| **Merge** | cross-branch dependencies rising, unstable shared interfaces, conflicting decisions, integration became the main effort. For coupling, never tidiness |
| **Replace** | demonstrated capability mismatch, degraded readiness, lost tool access, unacceptable load, repeated verification failure |

**Split coverage test:** a split is invalid if a child cell loses a critical capability it still requires — 🔴🔵🟢 splitting into a 🔵-only child with unresolved Red intelligence fails unless Red support remains accessible.

**Replacement must clear the context bar:** `ReplacementBenefit > HandoffCost + ContextReconstructionCost`. A slightly weaker familiar agent often beats a stronger cold one. **Prefer context affinity** — immersion in the repository, domain, artifact family, or mission state is a hidden force multiplier.

**Stability is a real resource.** Only change when `ExpectedGain > TransitionCost`. Apply hysteresis: reversing a recent composition decision needs stronger evidence than maintaining it. Repeated attach/detach/attach cycles are a diagnostic signal — bad requirement model, poor registry data, unclear main effort, or overreactive scheduling — emit it rather than continuing to churn.

**Provider failure:** preserve OpsGraph state → inspect checkpoint → query Registry → estimate reconstruction cost → assign replacement or restructure → transfer lease. Do not restart the mission unnecessarily.

**Prefer graceful degradation.** A cell of Forge 🔵🟢 / Scout 🔴🔵 / Sentinel 🔴 keeps limited Blue if Forge disappears. That beats brittle specialization.

**Fragility** is recorded, not necessarily eliminated: capability, provider, consequence if lost, mitigation (cross-trained backup, routine, reserve, checkpoint, documented handoff). Single points must be *understood*.

## 11. Archetypes

| | Composition | Use for |
|---|---|---|
| **Solo** | one cross-trained provider | small, reversible, low-coupling, no independence requirement. Not under-resourcing if the package is genuinely sufficient |
| **Pair** | supported operator + complementary capability | 🔴+🔵 recon and build · 🔴+🟢 diagnose and recover · 🔵+🔴 build and independently verify · 🟡+🔵 directed decisive build. Strong multiplication, low coordination |
| **Triad** | Integrator + Scout + Forge (COHERE / SENSE / MAKE) | the default high-autonomy cell for ambiguous engineering. Sentinel attaches independently when assurance requires |
| **Detachment** | 3–5 cross-functional providers | complex missions. Five should be exceptional next to two or three |
| **Multi-cell** | several detachments, each owning a mission effect | only with evidence requiring it |

**Task-organize around effect, never function.** Not "Research Team / Coding Team / Testing Team" but "Cell A: make ingestion pipeline viable / Cell B: resolve UI architecture." Each cell may hold multiple colors.

**Cell lead** is a function, not a requirement. It becomes useful with multiple members, shared output, moderate-to-high coupling, or external coordination. The lead owns local coherence, intent preservation, and integration — **not continuous permission-giving**. Select for mission understanding, adequate domain capability, state discipline, escalation judgment, and integration competence — **not automatically the strongest specialist**. And the lead need not be Yellow: a Blue-supported build cell can have a Blue integrator. Yellow enters for mission-level priority, authority, or cross-cell resources.

## 12. Depth and phasing

| | Consider |
|---|---|
| **F0 trivial** | one obvious qualified provider — no optimization |
| **F1 standard** | capability, load, context |
| **F2 structured** | + color coverage, complementarity, independence, reserve, coordination |
| **F3 complex** | + multiple cells, resource conflict, critical path, fragility, contingent attachments |

Use the minimum required depth. **Formation depth scales with the cost of being wrong.**

**Rapid formation** for urgent missions: identify the decisive capability → select a ready sufficient provider → attach minimal complementary support → begin → refine after initial Recon. Never delay urgent action seeking a theoretically perfect team.

**Phase-based design:** Phase 1 🔴-heavy recon → Phase 2 🔵-heavy build → Phase 3 independent 🔴 verification → Phase 4 🟣 institutionalization. Do not keep all phase capabilities committed throughout. At each gate: detach obsolete capabilities, attach next-phase capabilities, update the supported element and its support.

## 13. Gaps and investment

When no viable force satisfies the requirement: ATTACH an external enabler, TRAIN/cross-qualify, BUILD a routine or tool, MODIFY the mission approach, REDUCE the requirement if authorized, or DEFER. **Surface the gap; never invent competence.**

Force Generation does not train by default — do not delay an urgent mission to cross-train when a qualified enabler exists, unless building that capacity *is* the mission.

Repeated formation friction emits a capability investment signal (capability, demand, scarcity, observed cost, recommendation) for Purple.

**Look for force multipliers:** if every mission attaches a Red agent for deterministic validation, the answer is a validation routine, not a standing Red slot. Surface it.

**Human attention** is a strategic capability — value judgment, strategic preference, irreversible approval — never generic labor. If many tasks await the same human decision, **do not add agents**: the constraint is decision authority. Report a human-attention bottleneck to Yellow.

## 14. Interfaces

| System | Boundary |
|---|---|
| **Mission Command** | owns what matters, authority, risk, main effort. Force Generation may *recommend* a main-effort change; it cannot redefine strategic priority |
| **Recon** | owns terrain, unknowns, dependencies, decomposability. Do not redo Recon unless formation reveals an information gap |
| **Chromatic Doctrine** | supplies the functional language; Force Generation compiles it into providers |
| **Capability Registry** | says what we *have*; Force Generation decides what we *field*. The Registry never self-assigns |
| **ODA** | governs how the cell behaves once formed |
| **OpsGraph** | tracks execution state; Force Generation designs the executing force |
| **Sentinel** | independence is part of force design — builder ≠ acceptor where required. Verification bandwidth is a resource; plan it before the end of the mission |
| **Green** | recovery capability may be organic, attached, or reserve. Do not discover its absence during catastrophic failure |
| **Purple** | learns successful templates, persistent gaps, unnecessary specialists, routine substitutions |

**Allocation is hybrid.** Force Generation creates the cell and its capability envelope; OpsGraph exposes READY tasks; members pull locally. Explicit push assignment is for main effort, critical path, scarce specialists, independence requirements, and high consequence. Force Generation governs formation and critical routing — **not every micro-allocation**.

**Templates are hypotheses, not laws.** Use one when the mission shape strongly resembles a known pattern, then adapt to current terrain, supply, risk, and resources. Never blindly replay history. Where evidence is weak, small formation variations may be tested on suitable missions — never on high-consequence ones without reason.

**Formation memory** (mission shape, formation, outcome, coordination cost, rework, cycle time) lets the federation increasingly answer *which organization historically works best for this class of mission?*

## 15. Bottleneck reading

- **Color bottleneck** — many Blue tasks waiting on Red: add a Red provider, *automate the verification*, or *remove the unnecessary Red dependency*. Do not reflexively add an agent; the answer is often a process change.
- **Coordination bottleneck** — performance declining as agents increase: reduce force, merge roles, stabilize interfaces, or split the mission. More force is not always force multiplication.

## 16. Anti-patterns

| Anti-pattern | Why it fails |
|---|---|
| **Maximum swarm** — "use every Grok" | Duplication, coordination, context fragmentation |
| **One agent per skill** | Skills are capability doctrine, not job requisitions |
| **One agent per color** | A three-agent cell can cover all five colors |
| **Permanent teams** | Preserve learning, pairing evidence, and capability — not structure |
| **Expert everywhere** | Q5 capability on Q1 tasks wastes strategic capacity |
| **Cheapest always** | Cost optimization below acceptable mission probability |
| **Best individuals = best team** | Poor complementarity, high coordination, redundant strengths, missing shared fundamentals |
| **Formation by title** — "need coding, call Forge" | Titles are hints; Registry evidence, readiness, context, load, and tool access decide |
| **Zero reserve** | A package consuming every useful capability is fragile under uncertainty |
| **Unused reserve during failure** | Reserve exists to be committed at decisive moments |
| **Recomposition mania** | Changing formation over a 2% fitness estimate; transitions cost real time |
| **Hidden capability gap** | Claiming readiness when a critical capability has no qualified provider |
| **Force Generation as management** | Once the cell is formed, ODA autonomy and OpsGraph govern execution; return on topology changes |

## 17. Metrics

Average cell size, capability coverage, underqualified assignment rate, coordination cost, recomposition rate, formation thrashing, reserve utilization, capability gap rate, main-effort staffing latency, single-point exposure, cycle time by formation, color-signature success, routine substitution, human attention per formation.

Do not optimize "smaller always" — monitor **mission success relative to cell size**; ideal size varies with terrain.

`ForceEfficiency = VerifiedMissionEffect ÷ (AgentTime + Compute + Coordination + HumanAttention)` — this should improve over time.

`MarginalAgentValue = Effect(with) − Effect(without) − AddedCoordinationCost`. Add only when positive with sufficient confidence.

**The real success signal is not many well-assigned agents.** It is: *the mission repeatedly receives exactly enough capability, at the right moment, with minimal idle force and minimal coordination overhead.*

## 18. Sequence and checks

```
LOAD command + recon → mission shape → main effort → required capabilities
 → compile chromatic signature → classify critical/high/optional → independence requirements
 → query Registry → filter by readiness/authority/tools → identify routine substitutions
 → generate minimum viable candidate → test coverage, coordination, fragility, reserve impact,
   assurance independence → compare alternatives if material → select
 → write formation to OpsGraph → issue ODA mission packet → register reserve and conditional
   enablers → monitor recomposition triggers
```

**Before activating:** Do we cover every critical capability? Is the supported element clear? Do supporting elements know what effect they support? Is independent assurance preserved? Can the cell act within its authority? Do members have the tools? Is anyone unreasonably overloaded? Are we consuming a critical reserve unnecessarily? Can the cell degrade gracefully? Is it smaller — or larger — than it needs to be? **What specific value does each member add?** What event should cause recomposition?

If any member has no clear answer: **remove or rejustify.**

**Before recomposing:** What changed? What capability is now missing or excess? What is the expected gain and the transition cost? **Can local ODA adapt without recomposition?** Will this create a new gap elsewhere?

## 19. Worked examples

**Exploratory build** — high uncertainty, medium decomposability, `🔴🔵→🔴`: Scout-1 supports uncertainty reduction; Forge-2 is supported and owns the prototype; Sentinel-1 attaches **only at the verification gate**. Lean, phased, independence-preserving.

**Incident** — 🟢 dominant, 🔴 supporting, 🟡 conditional, 🟣 after: Green-1 supported for recovery, Scout-2 for diagnosis, Yellow attaches only if cross-cell impact emerges; then Red verification and a Purple routine candidate.

**Solo** — small reversible utility, Forge-1 at 🔵 Q4 with high current context and low load, assurance A1: **Forge-1 only.** No Scout, no Yellow, no dedicated Sentinel, no Purple. Healthy minimalism.

**High consequence** — persistent state migration needing 🔴 recon, 🔵 implementation, 🟢 rollback, independent 🔴 A4 assurance, 🟡 coordination: five providers are justified here because consequence and coupling are both high.

## 20. Constitution

1. Organization follows mission topology; define capabilities before selecting providers.
2. Color describes functional need, not headcount — one agent may cover several, one color may need several.
3. Use the smallest force that safely covers the mission; independence stays independent where commanded.
4. Select on demonstrated evidence — and tool access, authority, load, readiness, and context affinity count as much as competence.
5. The strongest individual is not automatically the best assignment; the strongest collection is not automatically the best team.
6. Complementarity and coordination cost matter; interdependence decides whether parallelism helps.
7. Supported/supporting relationships stay explicit.
8. Every added provider must remove a constraint, add capability, unlock parallelism, or reduce meaningful risk.
9. Main effort gets preferential capability; secondary efforts get minimum sufficient capability.
10. Scarce expertise carries opportunity cost; reserve preserves maneuver and is capability-specific; commit it when decisive value justifies it.
11. Temporary enablers detach when their purpose ends; prevent specialist hoarding.
12. Cross-trained agents enable smaller cells; avoid overloaded omni-agents, one-agent-per-skill, and one-agent-per-color.
13. A routine may be a better provider than an agent; deterministic work migrates toward deterministic infrastructure.
14. Capability gaps are explicit. Never invent competence to make a formation look complete.
15. Formations are temporary; recomposition is expected — but it has cost, so do not thrash.
16. Split when independence rises, merge when coupling rises, replace only when gain exceeds transition cost.
17. Preserve state and artifacts through provider failure; design for graceful degradation.
18. Force Generation designs the cell; ODA governs its behavior; OpsGraph controls execution; Mission Command sets priority; Recon defines terrain; the Registry describes competence.
19. Templates are hypotheses; phases may require force changes; capability is never retained merely because it was useful earlier.
20. Human attention is a strategic capability, not generic labor.
21. The goal is not maximum utilization. **The goal is maximum verified mission effect from minimum necessary organized force.**

## Done when

The federation receives an ambiguous mission and answers almost immediately:

> This is a 🔴🔵 mission with independent 🔴 acceptance. It needs Q3 repository archaeology, Q4 implementation, and Q3 concurrency assurance. Forge-2 and Scout-1 are the smallest viable execution cell. Sentinel-1 attaches at the verification gate. Green-1 stays in reserve because committing it would remove the federation's only high-confidence recovery capability.

At that point the federation is not assigning agents. It is **generating the organization the problem requires** — capability concentrating around the decisive constraint, producing effect, dispersing, and reforming around the next one.

The persistent assets are doctrine, capability, memory, tools, routines, and evidence. Teams are temporary expressions of those.
