---
name: grokcell-command-and-control
description: >-
  Use when establishing or repairing how the federation is governed — authority
  grants and conflicts, what to centralize vs delegate, control-plane coherence,
  escalation routing, command continuity and succession, disconnected operation,
  degraded C2, and return to normal after emergency authority.
---
# GrokCell Command & Control

⚪ White. Constitutional command-and-control substrate. Version 1.0.0.

**How does the federation remain one coherent organization while many autonomous cells act independently?**

| Centralize | Decentralize |
|---|---|
| purpose, authority semantics, strategic priorities, shared truth, critical resource arbitration | method, local sequencing, implementation, routine adaptation, low-risk decisions |

`maximize: Unity of Purpose + Local Freedom of Action + Shared State − Coordination Burden`

**C2 succeeds when command becomes quieter as the federation becomes more coherent.**

## Fast path

1. **Intent is clear, authority is sufficient, state is coherent** → act locally. **Command stays silent. Silence is the healthy state.**
2. **Routine local judgment** → decide at the lowest competent level. Do not escalate.
3. **Cross-cell externality, high consequence, irreversibility, values, or authority gap** → escalate — **decision-ready**, with a default if no response.
4. **Command changed** → issue a *delta* and replan only the affected region. Never reissue the whole mission order.
5. **Control state is degraded or conflicting** → declare the C2 health state explicitly, bound local authority, reconcile.
6. **Normal C2 has become unsafe** → C4, and cue ⚫ Black Protocol if activation conditions hold.

## 1. Command ≠ control

| **Command** — judgment | **Control** — information processing |
|---|---|
| purpose, end state, priority, risk posture, authority, main effort, resource concentration, termination | task state, ownership, dependencies, leases, events, resources, artifacts, readiness, synchronization |

**Command decides what should matter. Control keeps reality legible enough for those decisions to work.**

**White ≠ Yellow.** White defines *how command exists, how authority flows, how state becomes common, how control stays coherent, and what happens when C2 degrades.* Yellow executes command functions inside that architecture.

> Yellow asks *what matters now?* White asks *by what rules can anyone legitimately answer that question?*

## 2. Authority

All authority delegates downward from human intent:

```
HUMAN → FEDERATION COMMAND → MISSION COMMAND → CELL AUTHORITY → TASK AUTHORITY
```

**No lower layer may silently create authority beyond its delegation.**

**Authority is explicit, never implied.** A grant names grantor, grantee, scope, what it *may* do, what requires notify-after, what requires approval, what is prohibited, expiry, revocability.

Uniform semantics across the federation: **AUTONOMOUS / EXECUTE_AND_NOTIFY / APPROVAL_REQUIRED / PROHIBITED**.

`EffectiveAuthority = min(ConstitutionalCeiling, MissionGrant, ProviderCeiling, CurrentEmergencyState)`

**Capability does not imply permission. Urgency does not imply permission. Color does not imply permission.**

**Least authority, still sufficient.** Grant the least authority that accomplishes the delegated objective — but not so restrictive that routine execution constantly escalates.

`Autonomy = f(Competence, IntentClarity, Reversibility, Consequence, Interdependence)` — and it is **capability- and mission-specific**: an agent may hold high autonomy for one capability and approval-required for another.

**Temporary grants expire** (incident authority, deployment authority, external-write authority). This is what prevents privilege accumulation. **Revocation propagates rapidly** for consequential scopes, naming grantee, scope, reason, effective time, affected tasks.

### Conflicts

Higher legitimate authority beats lower. At the same level, resolve by scope specificity, then the newer valid command, then mission intent. **Remaining ambiguity escalates.** Authority conflicts are resolved structurally, never conversationally.

**Priority arbitration order:** mission end state → main effort → strategic priority → critical path → supporting work. **Local urgency never automatically outranks mission importance.**

## 3. Intent

Every mission exposes purpose, end state, key effects, priorities, **must**, **must not**, authority, risk posture.

**Intent must survive changing methods.** If it has to be rewritten every time local method changes, **the intent was written procedurally** and is wrong.

**Two-level purpose:** every executing element understands its objective *and why it matters to the parent objective* — ideally why the parent matters to the mission. **This is what makes disciplined initiative possible when instructions go obsolete.**

**Intent conflict:** if a local action serves the task but harms mission purpose, **mission purpose wins** — change or abandon the task.

**Task obsolescence:** a task can stay valid in OpsGraph while becoming strategically irrelevant. Issue `SUPERSEDE` rather than leaving stale work active.

## 4. Control modes

| Mode | Shape | Use when |
|---|---|---|
| **MISSION** | outcome centralized, method decentralized | decomposable work, rich local information, variable methods, reversible actions |
| **HYBRID** | local initiative + explicit synchronization | shared interfaces, moderate consequence, cross-cell dependencies |
| **DETAILED** | method constrained | tight synchronization, compliance, high irreversibility, exact reproducibility |

**Default: MISSION where possible, HYBRID where necessary, DETAILED only when justified.**

**Control must not become micromanagement.** Control mechanisms handle leases, dependencies, state, readiness, events. Agents handle reasoning, implementation, adaptation. **Never use humans or Yellow agents as manual state machines.**

## 5. The control plane

Canonical plane: **OpsGraph + Capability Registry + Force State + COP + Command State**. **Chat is never authoritative state.**

| Source of truth | Owns |
|---|---|
| Mission Command | intent, priorities, authority |
| OpsGraph | work, ownership, dependency state |
| Capability Registry | competence, readiness |
| Force Generation | current formation |
| Sentinel | verification records |
| COP | fused operational picture |

**White ensures these stay mutually coherent — and never duplicates their functionality.**

### Invariants — true at all times

- One accountable owner per task.
- No task executes without valid authority.
- No critical task exists outside durable state.
- No force package relies on a knowingly unavailable provider.
- No mission has two conflicting authoritative main efforts.
- No stale verification is represented as current.
- No lower authority silently overrides higher intent.

**Shared state ≠ shared everything.** Agents receive the *minimum sufficient* state. White governs common truth, role-specific views, and relevant deltas; COP implements distribution.

## 6. Command by exception

Normal execution should require no command attention. Surface only: priority conflict, authority conflict, main-effort threat, resource contention, critical risk, irreversible decision.

**A quiet command channel is a healthy outcome.**

**Escalation classes:** VALUE · AUTHORITY · RISK · INTENT · PRIORITY · RESOURCE · TERMINATION. Every escalation names its class.

**Escalations are processed, not raw.** Never *"something is wrong."* Send: what happened, why it matters, what options exist, recommended action, **default if no response**, decision deadline.

**Default-if-no-response** prevents paralysis:

| Situation | Default |
|---|---|
| Reversible low-risk work | continue |
| Research | continue |
| High-cost commitment | pause |
| Irreversible action | **do not execute** |
| State preservation | preserve |

**Human attention is a strategic command resource** — reserve it for values, high-consequence irreversible choices, strategic priorities, unclear intent, and external authority. **C2 actively compresses machine-manageable issues before escalation.**

## 7. Main effort and support

Every active mission normally has one main effort: objective, supported element, decisive constraint, resource priority, **reconsider when**. It marks where marginal capability currently produces the greatest mission value.

**Main effort is dynamic** — 🔴 unknown → 🔵 construction → 🟢 recovery → 🔴 verification. C2 keeps force, priority, and shared state aligned with each shift.

**Supported** owns the decisive effect; **supporting** increases the supported element's effectiveness. Support relationships may cut across authority topology.

**Communication topology ≠ command topology.** Blue speaks directly to Red — never Blue → Yellow → Red. Hierarchy exists for **authority**; communication follows **information value**.

## 8. Command events and versioning

Material command actions are explicit: type, issuer, **authority basis**, scope, previous state, new state, reason, affected elements, effective time.

`MISSION_CREATED` · `MISSION_CHANGED` · `MAIN_EFFORT_CHANGED` · `PRIORITY_CHANGED` · `AUTHORITY_GRANTED` · `AUTHORITY_REVOKED` · `RESOURCE_PRIORITY_CHANGED` · `FORCE_REVIEW_ORDERED` · `MISSION_SUSPENDED` · `MISSION_RESUMED` · `MISSION_TERMINATED` · `C2_DEGRADED` · `C2_RESTORED`.

**Command state is versioned.** An agent acting on v5 while command is at v7 must detect whether the intervening deltas invalidate its work — **use impact analysis, not blanket refresh.** Critical command change requires affected cells to refresh before consequential action.

**Deliver changes as deltas:** what changed, what did not, affected elements, effective now, what it supersedes. Then **replan only the affected graph region** — resetting unaffected work destroys tempo.

**Command security** guards against unauthorized, stale, conflicting, or forged commands and scope leakage. Every consequential command traces to legitimate authority.

## 9. Continuity

**Force recomposition does not reset command.** When members change, mission purpose, authority, task state, and artifact history persist. **Teams are temporary; command state is durable.**

**Command continuity** is defined in advance: primary command, alternate, succession condition, delegated authority, local authority cache, reconnect protocol. **Do not discover continuity rules during command loss.**

**Succession is not a power grab** — a successor receives defined authority for defined scope under a defined trigger, never universal control.

**On command loss:** preserve current intent → preserve authority grants → continue reversible authorized work → **halt new irreversible commitments** → maintain local state → attempt reconnection → invoke succession if conditions hold.

**Disconnected operation** requires a bounded packet: mission purpose, local objective, authority, constraints, known state version, key assumptions, local resources, synchronization conditions, termination conditions.

Disconnected cells keep a **local event log** (decision, artifact, state change, blocker, authority use) — not a chat dump.

**Reconnection:** local history + current federation state → conflict detection → reconciliation → new common state. **Neither side is automatically correct.**

Conflict classes: BENIGN · MERGEABLE · AUTHORITY_CONFLICT · ARTIFACT_CONFLICT · DECISION_CONFLICT · IRREVERSIBLE_CONFLICT. Higher classes need Yellow or human decision.

## 10. C2 health

C2 itself degrades. Dimensions: command availability, state coherence, COP freshness, OpsGraph integrity, authority consistency, force visibility, communication reachability.

| State | Examples | Response |
|---|---|---|
| **C0 NORMAL** | all primary functions available | decentralized execution |
| **C1 LIMITED** | one tool degraded, COP latency elevated, alternate command unavailable | Sustainment handles locally |
| **C2 DEGRADED** | Registry stale, partial control-plane outage, some cells disconnected | continue with bounded local authority |
| **C3 SEVERE** | conflicting task ownership, command unavailable, control state unreliable | freeze consequential ambiguity; reconciliation becomes the main effort |
| **C4 EMERGENCY** | canonical state integrity uncertain, active corruption, runaway authority, cells on contradictory command | normal C2 may be unsafe → cue ⚫ Black |

**Under degraded C2:** local reversible work may continue where authority remains valid. **Irreversible commitments stop when command legitimacy is uncertain.**

Degradation and restoration are **explicit events** — `C2_DEGRADED` names affected functions, safe local authority, restricted actions, recovery owner; `C2_RESTORED` names restored functions, reconciled state, remaining limits, whether normal autonomy resumed.

### Black Protocol boundary

**White governs Black's activation semantics** — who may invoke, what qualifies, what envelope may be granted, how normal C2 is restored. **Black never defines its own constitution, and Black authority is always temporary.**

```
⚪ NORMAL C2 → C4 EMERGENCY → ⚫ BLACK → contain/preserve
  → 🟢 recover → 🔴 verify → ⚪ reconcile → NORMAL C2
```

**Return-to-White:** revoke Black authority → reconstruct canonical state → reconcile task ownership → reconcile artifacts → restore normal command → restore force posture → verify C2 coherence → resume normal autonomy → Purple AAR.

**Reconciliation record:** command state, authority state, OpsGraph state, force state, registry state, artifact state, unresolved conflicts, **verified coherent**, normal operation allowed.

## 11. Centralize / decentralize tests

**Before centralizing a decision:** Does the higher level have better information? Does the decision create a cross-cell externality? Is consequence high? Is the authority strategic? **No → keep it local.**

**Before delegating:** Is intent clear? Is competence sufficient? Are boundaries explicit? Can local failure be contained? Can the result be observed? **Yes → delegate.**

**When autonomy repeatedly misaligns**, diagnose first — unclear intent? weak capability? authority too broad? stale COP? ambiguous interfaces? **Do not automatically centralize.**

**When detailed control repeatedly slows work**, diagnose first — mechanical control done by humans? over-specified methods? too many gates? poor tool support? **Do not automatically blame agents.**

## 12. Interfaces

| System | White's role |
|---|---|
| **COP** | ensure it references canonical sources, creates no parallel truth, stays role-filtered, exposes material conflicts |
| **OpsGraph** | ensure task state stays authoritative, ownership valid, events auditable, control recovery possible |
| **Capability Registry** | prevent **capability** from being confused with **authority** |
| **Force Generation** | ensure formation serves intent, main effort, authority, reserve — and stays visible in shared state |
| **Sentinel** | define what Sentinel may block, what Mission Command may override, what requires human authority |
| **Green** | define the emergency recovery envelope — e.g. may isolate a local component and roll back reversible local change, notify after containment, approval required for federation-wide shutdown |
| **Purple** | may recommend authority redesign, command rules, control automation, doctrine change. **White changes only on sufficient evidence** |

## 13. Load and friction

`C2Friction = EscalationLatency + StatusOverhead + AuthorityAmbiguity + StateDivergence + CoordinationDelay` — this should fall over time.

**Rising command load** (open strategic decisions, authority exceptions, resource conflicts, termination decisions) suggests **over-centralized authority**.

**Rising control load** (manual state reconciliation, manual lease correction, manual status requests, manual routing) suggests **under-automated mechanical control**.

Good C2 produces fewer status requests, fewer approval requests, fewer conflicting actions, faster local decisions, better main-effort concentration.

**Command noise** — constant reprioritization, repeated clarification, status polling, duplicate approvals — indicates architecture problems, not agent problems.

## 14. Anti-patterns

| Anti-pattern | Why it fails |
|---|---|
| **Central brain** | Every decision routed through one omniscient manager; the federation must survive without constant central cognition |
| **Command by chat** | Commands must become durable state |
| **Control by human** | Humans manually maintaining leases, queues, dependency state, routine routing |
| **Authority by vibe** | Permission inferred from confidence, color, or seniority |
| **Permanent emergency authority** | Exceptional authority must expire |
| **Yellow everywhere** | Not every cell needs a manager; White exists so many cells can operate without one |
| **Command flood** | Constant reprioritization destroys local autonomy |
| **Control flood** | Excess transitions, approvals, gates, notifications create coordination drag |
| **Stale intent** | Agents executing old priorities after context materially changed |
| **Authority accumulation** | Temporary permissions that became permanent because revocation was forgotten |
| **Unknown succession** | Discovering continuity rules during command loss |
| **Duplicate source of truth** | Parallel mutable representations of canonical state |
| **Command without feedback** | Command that cannot observe effect is blind; COP and Sentinel close the loop |
| **Control without purpose** | A perfectly controlled organization can efficiently do the wrong thing |
| **Autonomy without shared state** | Decentralization without coherent information is fragmentation |
| **Shared state without autonomy** | Perfect visibility plus mandatory central approval is bureaucracy |
| **Black as normal C2** | If emergency authority becomes routine, **the C2 architecture has failed** |

## 15. Depth

| | Adds |
|---|---|
| **C2-0 local** | intent, authority, OpsGraph, local COP |
| **C2-1 standard** | + force state, shared COP, exception routing |
| **C2-2 multi-cell** | + resource arbitration, command continuity, cross-cell synchronization |
| **C2-3 persistent federation** | + degraded modes, succession, disconnected operation, reconciliation |
| **C2-4 critical federation** | + Black Protocol readiness, strong audit, control-plane recovery |

Use only the needed depth.

## 16. Sequence

```
LOAD doctrine → establish human authority → load active mission command
 → load OpsGraph, Registry, force state, COP
 → verify command version, authority coherence, task ownership, force readiness,
   control-plane health
 → identify exceptions → establish C2 health state → RELEASE NORMAL AUTONOMY
```

**Live loop:** mission reality → control state updated → COP fused → command-relevant? → no: local action; yes: command judgment → command delta → distributed execution.

**Reconciliation loop:** command + OpsGraph + registry + force + Sentinel → consistent? → yes: continue; no: classify conflict → reconcile → shared truth.

**Quality check:** Is mission purpose current and main effort clear? Is authority explicit? Does every active task have valid ownership? Are cells operating from current command? Does force state match real readiness? Is the COP current? Are any commands conflicting? Are local decisions escalating unnecessarily? Is human attention used only where needed? **Can the federation continue if one command node disappears — and what happens if normal C2 becomes unsafe?**

## 17. Metrics

Command decision latency, escalation rate, **unnecessary** escalation rate, authority conflict rate, stale command incidents, state divergence rate, status request rate, manual control actions, command load, control load, C2 degradation events, command recovery time, disconnected reconciliation cost, human attention per mission.

- **Escalation rate too high** → authority too narrow, intent too vague, or competence mismatch. **Too low with frequent failure** → authority too broad or poor escalation judgment.
- **Status request rate** — frequent *"what is happening?"* means the COP/control architecture is underperforming. Goal: decrease.
- **Manual control rate** — if humans or Yellow repeatedly renew leases, reconcile state, or route routine work, **automate the mechanics**.
- **State divergence rate** should approach zero.
- **Command recovery time** — loss of C2 function to coherent command restored. Matters for persistent federations.

## 18. Constitution

1. Human intent is the highest legitimate mission authority; everything below is delegated.
2. White defines how command and control exist; Yellow performs command functions inside it.
3. Command is judgment; control is information processing. Never centralize mechanical control in human or agent managers.
4. Centralize purpose, authority semantics, and strategic priority. Decentralize method and routine execution.
5. Authority is explicit. Capability, color, and urgency do not imply authority.
6. Place decisions at the lowest competent level; every element understands parent purpose; intent survives changes in method.
7. Control mode matches interdependence and consequence — mission preferred, hybrid where interfaces are shared, detailed only when justified.
8. Chat is not authoritative state; canonical source ownership stays explicit and mutually coherent.
9. Every active task has valid accountable ownership; every consequential action has valid authority.
10. Command operates by exception; escalations are decision-ready with predefined defaults.
11. Main effort stays explicit and may shift; supported/supporting relationships stay visible; communication may bypass hierarchy when authority is unaffected.
12. Force recomposition preserves durable mission state; continuity and succession are predefined and bounded.
13. Disconnected operation needs a bounded packet and a local event log; reconnection requires reconciliation, and neither side is automatically correct.
14. C2 has health states; degradation is explicit; reversible authorized work may continue, irreversible commitment stops when legitimacy is uncertain.
15. Severe failure may justify Black — White defines its activation and termination, Black never defines its own authority, and its purpose is restoring normal C2.
16. Authority conflicts resolve structurally; local urgency does not outrank mission priority.
17. High command load suggests over-centralization; high control load suggests under-automation; command silence can be healthy.
18. Supersede tasks when intent changes; prefer partial replans and command deltas.
19. Least authority must still be sufficient authority; diagnose repeated autonomy or control failure before changing the architecture.
20. Command state is versioned, stale command is detectable, temporary authority expires, revocation propagates.
21. C2 preserves continuity through provider loss, state through team changes, and intent through method changes.
22. **The best command system becomes progressively quieter as organizational coherence improves.**

## Done when

A weak multi-agent system coordinates through conversation. A stronger one has shared tasks. A better one adds orchestration. A premium federation:

> separates judgment from control, makes authority explicit, preserves one coherent mission reality across many local actors, pushes decisions to the lowest competent level, automatically maintains the mechanical state autonomy requires, survives loss of individual cells or command nodes, and holds a bounded constitutional mechanism for restoring control when normal governance itself becomes unsafe.

That is what makes a federation an organization rather than a swarm.

The goal is not central control. The goal is **coherent decentralization** — centralize information and constitutional authority; decentralize execution and local judgment.

When the architecture works: intent propagates, authority is understood, state stays durable, cells act, exceptions rise, command intervenes only where judgment is genuinely required — and when the crisis passes, the system returns to quiet autonomy.
