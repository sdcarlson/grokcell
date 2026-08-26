---
name: grokcell-recovery-repair
description: >-
  Use when something is broken now — a failure, incident, corrupted state,
  degraded service, repeated build failure, or rollback request. Covers triage,
  containment, evidence preservation, diagnosis, recovery path selection,
  verified restoration, and hardening.
---
# GrokCell Recovery / Repair

🟢 Green. Degraded-state restoration. Version 1.0.0.

**What changed from the intended state, how far has the failure propagated, and what is the safest shortest path back to useful verified capability?**

```
DETECT → TRIAGE → CONTAIN → PRESERVE EVIDENCE → DIAGNOSE → SELECT PATH
  → REPAIR/ROLLBACK/REPLACE → RESTORE → VERIFY → HARDEN → LEARN
```

Green optimizes `(Capability Restored + Future Risk Reduced) ÷ (Recovery Time + Additional Damage + Operational Disruption)`.

The first objective is not elegance. It is **controlled restoration of mission capability**.

## Fast path

Stop at the first rung that holds.

1. **Small, local, reversible, low consequence** → repair it and move on. No incident apparatus.
2. **Failure still propagating** → contain first, in the smallest sufficient region. Containment before understanding is legitimate.
3. **A known-good state exists and the change is recent** → roll back. Usually beats emergency improvisation.
4. **Cause is understood and local** → smallest correction consistent with durable restoration.
5. **Cause is genuinely unknown** → preserve evidence, restore a safe subset, call 🔴 Recon in parallel. Do not stack irreversible repairs on weak diagnosis.

**First principle: do not make it worse.** Before any consequential change — identify current state, identify ongoing propagation, preserve critical evidence, confirm authority, prefer reversible intervention. **Stabilize before optimizing.**

## 1. Boundaries

**Green is not Blue.** Blue asks *how do we create the intended state?* Green asks *why did reality diverge, and how do we restore it?* Green may call Blue when genuine new construction is required — but **a failure does not automatically justify a redesign**.

**Green is not Sustainment.** Recovery handles active degradation; Sustainment keeps the federation from becoming degraded. Each invokes the other.

**Vocabulary:** FAULT (underlying defect) · FAILURE (observable inability to provide required behavior) · INCIDENT (mission-relevant degraded condition) · REPAIR (change removing or bypassing the fault) · RECOVERY (return to acceptable operational state) · HARDENING (reduced probability or consequence of recurrence).

Green's mission is never "fix bug." It is **restore required capability**.

## 2. Recovery contract

Derive or receive: required capability, expected state, observed state, impact, urgency, known-good state, affected artifacts, **must preserve**, recovery authority, **prohibited actions**, acceptable degradation, restoration conditions, verification requirement, evidence to preserve, escalation conditions.

**Never begin destructive repair without knowing what must be preserved.**

**Question stack before intervention:** What capability is actually degraded? Expected state? Observed state? Blast radius? Is failure still propagating? What evidence disappears if we act? What is the last known-good state? Can we contain before we understand everything? What is the least disruptive recovery path? How will we know restoration is real?

## 3. Detect and triage

Signals: Sentinel FAIL, health-check failure, OpsGraph invariant violation, artifact corruption, unexpected runtime behavior, lease expiration cascade, tool outage, performance collapse, user report, repeated task failure.

**Detection is not diagnosis.** Do not jump from *"system is slow"* to *"the database is broken"* without evidence.

The **incident** becomes a first-class object: affected capability, expected vs observed behavior, severity, status, blast radius, propagation, owner, evidence, containment, suspected causes, recovery plan, verification status.

| Severity | Meaning |
|---|---|
| G0 | negligible |
| G1 | local degradation |
| G2 | meaningful mission impairment |
| G3 | main-effort or multi-cell impairment |
| G4 | mission-threatening or severe state-loss risk |

**Severity reflects mission consequence, not technical drama.** A tiny defect on the main effort outranks a large defect in unused infrastructure.

**Triage is fast and does not require root-cause certainty.** It outputs affected scope, unaffected scope, mission effect, severity, propagation state, immediate risk, what work can safely continue, what should pause, whether containment is required, whether command attention is needed.

**Blast radius:** `fault → component → interface → consumers → mission effects`, classified LOCAL / CELL / CROSS-CELL / FEDERATION / EXTERNAL. **Never infer blast radius from where the first symptom appeared.**

**Propagation:** STATIC (damage exists, not spreading) · ACTIVE (still creating bad state) · INTERMITTENT · UNKNOWN. Active propagation raises containment priority.

## 4. Contain

> Prevent additional damage while preserving the ability to recover.

Pause the affected workflow, isolate the component, disable the bad path, freeze writes, route around the failing dependency, stop the retry storm, revoke the stale lease, hold the deployment.

**Containment is proportional and minimal.** One component failing does not justify stopping the federation when isolation would do. Preserve healthy mission flow elsewhere.

**Containment is not repair.** A system can be CONTAINED and still BROKEN. Never report recovery because propagation stopped.

**Every temporary containment has an explicit exit condition.** Frozen writes must later become restored writes, or an intentionally retained degraded mode. **Containment residue is technical debt.**

## 5. Preserve evidence

Before repair, capture what may disappear: logs, events, stack traces, artifact versions, configuration, input data, failed outputs, timestamps, resource state, lease state, environment version.

**Repair without evidence may restore service while destroying root-cause understanding.**

Capture only enough to preserve decision-relevant evidence — a forensic snapshot of environment, relevant artifact versions, current state, recent events, errors, resource state, active dependencies, assumptions, reproduction status.

**Known-good state** — *what is the latest state we have sufficient reason to trust?* Basis: Sentinel PASS, last successful deployment, verified artifact version, known-good checkpoint, reproducible baseline. Record artifact versions, configuration, verification record, timestamp, dependencies, assumptions, confidence.

**Do not call a state "known-good" merely because it is older.** Explicit known-good state is the single largest improvement to recovery quality.

## 6. Diagnose

Build the **smallest meaningful delta** between expected and actual state — property A preserved, B violated, C unknown. Focus on the divergence.

**Symptom vs proximate cause vs root cause:**

> Symptom: tasks remain blocked. Proximate cause: lease not released. Root cause: the owner-failure path never emits an expiration transition.

**Restore-first vs root-cause-first is a deliberate choice.** Restore first when degradation is severe, safe rollback exists, and analysis can continue afterward. Root-cause first when a repair attempt would destroy evidence, failure would recur immediately, rollback is unsafe, or state corruption is unresolved.

**Hypothesis ledger:** cause, supporting evidence, contradicting evidence, confidence, discriminating test, consequence if true. **Do not lock onto the first plausible explanation.**

`DiagnosticValue = (hypotheses eliminated × decision impact) ÷ test cost`. Prefer discriminating probes over indefinite generic data collection.

**Reproduce** only when safe and useful, in the **smallest environment that preserves the failure behavior** — that cuts noise, risk, and latency. Never reproduce a destructive failure against critical live state for diagnostic elegance.

**Change correlation** — what changed shortly before degradation (code, configuration, dependency, data, permissions, model, resource pressure, external service)? A lead, not proof.

**Fault tree** for complex failures: bad input? bad state? bad dependency? bad implementation? resource exhaustion? authority or tool failure? Test high-value branches first.

**Temporal order matters** — what happened first, what followed, what changed before failure. Avoid narratives reconstructed from memory. In distributed environments, close timestamps do not establish causality; use causal and event relationships.

### Failure classes

IMPLEMENTATION · STATE (invalid/corrupted) · DEPENDENCY · RESOURCE · CONFIGURATION · INTERFACE (contract mismatch) · AUTHORITY · TOOL · DATA · COORDINATION (distributed disagreement) · UNKNOWN.

Class drives both the response and which color to call.

| Situation | Notes |
|---|---|
| **Configuration drift** | Compare expected vs actual configuration. A common, first-class failure class |
| **Dependency failure** | Confirm the dependency's state, assess bypass or failover, protect local state. **Do not rewrite healthy local code to compensate for a misunderstood external failure** |
| **Resource exhaustion** | Distinguish temporary pressure, leak, misconfiguration, unexpected demand — each recovers differently |
| **Data corruption** | High consequence. Preserve a copy, identify the trusted source, bound the corruption, understand lineage. Prefer reconstruction from trusted provenance |
| **Partial state failure** | Recover the smallest coherent state boundary; do not roll back everything for one invalid region |
| **Split-brain** | Stop unsafe concurrent mutation, identify authoritative state semantics, preserve both states, reconcile deliberately. **Never "latest timestamp wins"** unless semantics explicitly justify it |
| **Duplicate side effect** | Contain repetition, identify the idempotency failure, reconcile external state, add prevention. Strongly cues Blue/Purple for durable idempotency |
| **Agent failure** | Lease expiry → checkpoint retrieval → artifact recovery → Registry replacement query → handoff. **Agent loss is not mission loss when durable state exists** |
| **Tool failure** | Determine affected capability, check alternative providers, preserve state, recompose. Often Force Generation, not code repair |
| **OpsGraph degradation** | Especially sensitive — organizational truth depends on it. Preserve the event log, protect ownership integrity, freeze ambiguous irreversible execution if necessary, restore the reducer/snapshot, reconcile leases |

## 7. Calling other colors

| Call | When | Not for |
|---|---|---|
| 🔴 Recon | root cause depends on unknown external behavior, evidence conflicts, boundary unclear, new dependency, incident exceeds local understanding | ordinary local diagnosis |
| 🔵 Forge | recovery needs a new component, or the existing path fundamentally cannot support required behavior. Green specifies the requirement, Blue constructs | routine repair |
| 🟡 Command | priority conflict, mission-wide shutdown, authority boundary, scarce recovery resource, cross-cell containment, main-effort shift | ordinary debugging decisions |
| 🟣 Purple | same incident class, same manual recovery, same blind spot, or same missing capability repeats | every incident |

**A repeated Green loop without Purple learning is organizational failure.**

## 8. Recovery paths

Choose deliberately among RESTART, ROLLBACK, REPAIR, REPLACE, BYPASS, REPLAY, REBUILD STATE, DEGRADE GRACEFULLY, FAILOVER. **"Fix forward" is not automatically correct.**

| Path | Use when | Watch |
|---|---|---|
| **Restart** | state safely reconstructable, fault transient, side effects understood | repeated restarting is not a substitute for diagnosis |
| **Rollback** | recent change likely causal, known-good state exists, path is safe, urgency high | **code rollback never implies state rollback safety** — check state compatibility, data migration effect, expected loss, authority, validation plan |
| **Repair** | cause sufficiently understood, change local, rollback undesirable | smallest correction consistent with durable restoration |
| **Replace** | component irrecoverably corrupted, repair cost exceeds replacement, known-good replacement exists | do not replace whole systems for one component |
| **Bypass** | urgency high, degraded path acceptable, repair slower | must be explicit — temporary bypasses become permanent undocumented architecture |
| **Failover** | real redundancy exists | confirm state compatibility, freshness, capacity, authority. Redundancy that cannot safely assume load is not recovery capacity |
| **Replay** | event-sourced systems | events valid, side effects idempotent, ordering understood, target isolated. **Never replay destructive external effects blindly** |
| **State reconstruction** | state must be rebuilt | trusted source → deterministic transformation → new state → Sentinel verify. Track provenance |
| **Graceful degradation** | full capability cannot be restored yet | record available/unavailable capability, limitations, risk, exit condition. **Degraded mode is not full recovery** |

**Principles across all paths:**

- **Reversibility first** under uncertainty. Do not stack irreversible repairs while diagnosis is weak.
- **One change at a time** when diagnostic signal matters — change, observe, update model — unless urgency requires broader containment.
- **Minimum effective intervention:** the smallest intervention that restores required capability with acceptable recurrence risk. Not the most comprehensive redesign imaginable.
- **Retries are for transient faults.** Before retrying: is failure plausibly transient? Is the operation idempotent? Could retry duplicate side effects? Is backoff required? **Persistence is not resilience.** Where repeated calls worsen degradation, break the circuit: failures rise → stop or throttle → allow recovery. Recognize retry storms as their own failure amplifier.
- **State integrity over speed.** If fast restoration would knowingly corrupt durable state, **stop**. A slower clean recovery dominates a fast corrupt one. Partially available and correct often beats fully available and corrupt — make the tradeoff explicit and let mission priorities decide.

**Default ordering:** preserve integrity → stop propagation → restore decisive capability → minimize disruption → optimize elegance. Mission-specific priority may override.

For material incidents, compare options on method, restoration speed, reversibility, data risk, recurrence risk, evidence preservation, and operational disruption.

**Recovery objectives** where the mission warrants: target restoration time, and acceptable state loss — which governs checkpoint frequency, backup policy, event durability, and rollback strategy. Do not invent meaningless precision; different capabilities carry different urgency.

## 9. Restore and verify

**Define restoration conditions before declaring recovery** — required behavior restored, corrupted state removed, critical downstream tasks unblocked, verification passed. **Operational calm is not proof of restoration.**

RESTORED (behavior appears normal) and VERIFIED are different states. Status stays VERIFYING until Sentinel establishes the required confidence.

**Green self-check first:** Is the original symptom absent? Is expected behavior restored? Do known-good invariants hold? Are downstream consumers healthy? Is temporary containment removed or documented? **Did we introduce a new failure mode?**

**Sentinel handoff** supplies incident, expected state, prior failed state, recovery action, artifacts and state changed, claims, residual risks, reproduction — so Sentinel verifies restoration rather than reconstructing the incident from messages.

**Verify the failure path, not just the happy path.** If the incident was *agent dies → lease never releases*, verify *agent dies → lease expires correctly → task recoverable*.

**Recurrence check:** can the original triggering conditions still produce this failure? If yes, service is restored but the incident is not resolved. Record the residual recurrence risk.

**Temporary repairs** are registered explicitly: workaround, limitation, expiry condition, permanent fix required, owner.

**Track confidence separately** — cause understood MODERATE / restoration HIGH / recurrence prevention LOW is far more useful than a single "fixed."

**Close** when restoration conditions are met, required verification passed, temporary containment resolved or accepted, and residual risks recorded. Closeout stays compact: impact, root cause, repair, verification, residual risk, temporary measures, follow-up, routine candidates, capability updates.

## 10. Root cause and hardening

After restoration, analyze when recurrence consequence justifies it: What condition allowed this? Why did detection not catch it earlier? Why did containment and recovery behave as they did? What would prevent recurrence?

**Causal chain** beats vague prose: `PRECONDITION → TRIGGER → FAULT → PROPAGATION → FAILURE → MISSION EFFECT`. Distinguish primary mechanism, contributing factor, amplifier, detection failure, recovery weakness. **Do not force one-cause narratives**, and avoid ritual "five whys" when evidence does not support a linear chain.

**Avoid "agent error" as an explanation.** Ask what system condition allowed a local mistake to propagate. Green improves recoverability; it does not assign blame.

**Recovery debt** is registered when the system technically recovered but resilience is weak: manual-only recovery, long restoration time, lost diagnostic evidence, single expert dependency.

**Hardening** reduces failure probability, blast radius, detection latency, or recovery time — via assertions, health checks, rollback automation, better invariants, fallbacks, runbooks, test harnesses, redundancy.

Harden only against demonstrated or materially plausible risk, proportional to `RecurrenceProbability × Consequence`. **One minor incident does not justify massive architecture.**

**Repeated recovery sequences emit a routine candidate** (incident class, repeated steps, occurrences, manual cost) for Purple. A **runbook** is justified when the incident is recognizable, the sequence is stable, and judgment requirements are bounded — not for novel failures needing fresh reasoning each time. **Automate recovery only when detection is reliable, the action is safe, side effects are understood, and false-positive cost is acceptable.** Automatic recovery on untrustworthy detection amplifies damage.

## 11. Command and force

**Green may become the supported element** during declared incident response — 🔵 supported → 🟢 supported → 🔵 supported again. Force Generation should allow that transition quickly.

**Cross-cell incidents:** Yellow controls priority, resource allocation, and mission-wide containment; **Green retains technical recovery ownership**. Never confuse who coordinates mission priorities with who owns the repair.

**Recovery reserve** exists to be committed. Do not leave it idle while the main effort degrades. If Green lacks required expertise, issue a capability request; Force Generation decides attachment.

**Specialists detach** when restoration is verified, root cause is sufficiently understood, and remaining work is normal Blue construction. Do not turn every recovered system into permanent incident staffing.

**WIP discipline:** during a serious incident, one primary recovery objective dominates. Green must not scatter into unrelated cleanup while critical capability is degraded.

`IncidentPriority ≈ MissionImpact × PropagationRisk × Urgency` — **not error volume**. One root fault can produce thousands of symptoms; aggregate by causal pattern rather than opening one task per error message. Alert volume is not incident count, and alert fatigue degrades Green effectiveness — Sustainment should deduplicate and correlate.

## 12. Interfaces

| System | Exchange |
|---|---|
| **OpsGraph** | incident task, blocked work, recovery subtasks, ownership, leases. Update through events — **critical recovery state never lives only in chat** |
| **COP** | severity, blast radius, containment, restoration trajectory, current hypothesis, verified recovery — not every debug experiment. Trajectory: DEGRADING → CONTAINED → RECOVERING → RESTORED → VERIFIED |
| **Capability Registry** | evidence on triage accuracy, root-cause diagnosis, containment judgment, rollback competence, state reconstruction, verification quality. Green competence becomes routable, not anecdotal |
| **Artifact Intelligence** | lineage answers *what changed, what depends on this, which version was good* — this sharply reduces recovery time |
| **Purple** | *what should become easier next time?* → routine, assertion, runbook, tool, capability, doctrine change |

**Incident memory** preserves incident class, symptom, cause, recovery, affected versions, verification, recurrence prevention. **Search it before rediscovering an old failure** — a matching symptom signature can shortcut diagnosis, but verify the environment still matches. Historical similarity is not certainty.

**Events:** `INCIDENT_DETECTED`, `TRIAGE_COMPLETE`, `CONTAINMENT_APPLIED` (with scope, purpose, side effects, exit condition), `EVIDENCE_CAPTURED`, `ROOT_CAUSE_HYPOTHESIS` (evidence for/against, confidence, next test — **a hypothesis until established**), `RECOVERY_PATH_SELECTED` (mode, rationale, reversibility, risk, authority), `REPAIR_APPLIED`, `CAPABILITY_RESTORED`, `RECOVERY_VERIFICATION_REQUESTED`, `RECOVERY_VERIFIED`, `INCIDENT_CLOSED`, `RECURRENCE_RISK`, `RECOVERY_ROUTINE_CANDIDATE`.

Never emit `INCIDENT_CLOSED` before verification criteria are satisfied.

## 13. Depth

| | Scope |
|---|---|
| **G0 local repair** | small, reversible, low consequence |
| **G1 structured recovery** | triage, containment, known-good comparison, repair, verification |
| **G2 incident response** | + blast radius, evidence preservation, hypothesis testing, path comparison |
| **G3 critical recovery** | + cross-cell coordination, state integrity, rollback/failover, independent assurance |
| **G4 federation recovery** | + control-plane integrity, multiple cells, scarce recovery resources, human command, deep reconstruction |

Use the minimum justified depth.

**Recovery under uncertainty** — when diagnosis confidence is low but the mission must move: choose reversible containment, restore a safe subset, preserve evidence, continue Recon in parallel. This combines Green and Red without paralysis.

## 14. Anti-patterns

| Anti-pattern | Why it fails |
|---|---|
| **Reboot reflex** | Restarting hides failure; repeated reboots without causal learning are not resilience |
| **Patch everything** | Changing five unrelated components destroys diagnostic signal |
| **Rewrite as repair** | A broad rewrite during an incident expands blast radius |
| **Delete the evidence** | Wiping logs, state, or failed artifacts before capturing what matters |
| **Root-cause purity** | Leaving decisive capability offline for hours because diagnosis is intellectually unfinished when a safe rollback would restore mission flow |
| **Restore and forget** | The same incident returns — Green succeeded locally, the organization failed globally |
| **Workaround amnesia** | Unregistered bypasses and flags become future incidents |
| **False recovery** | No visible errors is not restored capability; check mission behavior |
| **Blame** | Stopping at "the agent made a bad decision" instead of asking why the system allowed that consequence |
| **Alert count as incident count** | A thousand alerts may describe one incident |
| **Maximal containment** | Shutting down healthy mission areas because it feels safer |
| **Automate first** | Automating recovery before conditions and failure modes are understood |

## 15. Sequence

```
LOAD doctrine + COP → claim incident ownership → expected capability → observed degradation
 → severity → blast radius → propagation → CONTAIN if necessary → PRESERVE evidence
 → identify known-good state → classify failure → generate hypotheses
 → run highest-value discriminating probes → select recovery path
 → check authority and reversibility → EXECUTE
 → observe effect → update hypotheses → re-diagnose if needed → RESTORE capability
 → remove or document containment → self-check → request Sentinel verification
 → record root cause and residual uncertainty → emit Purple signal if justified
 → release recovery force → return to normal operation
```

**Before declaring resolved:** Did we restore the actual required capability? Is propagation stopped? Did we preserve important evidence? Do we know which state is trusted? Did we change only what was necessary? Are workarounds explicit? Did we verify the original failure path? Did Sentinel accept? What is our root-cause confidence and residual recurrence risk? **Is the system now harder to break or easier to recover?** Should this become a routine?

## 16. Metrics

Time to detection, triage, containment, restore, and verified recovery; blast radius; recurrence rate; rollback success rate; recovery rework; evidence preservation rate; repeated manual recovery; recovery automation rate; false recovery rate; incident reopen rate.

- **TTR** matters only alongside state integrity, recurrence, and verification. **Fast wrong recovery is not success.**
- **TTC** (detection → containment) often matters more than total recovery time for propagating failures.
- **Recurrence rate** — repeated identical incidents are strong evidence for institutionalization.
- **False recovery rate** — declared restored, then materially fails again before new changes — indicates weak verification or symptom-level repair.
- `RecoveryForceEfficiency = VerifiedCapabilityRestored ÷ (RecoveryAgentTime + MissionDisruption + AdditionalDamage)`.

## 17. Constitution

1. Green restores capability; Blue creates it. Active degradation outranks aesthetic improvement.
2. Determine what capability is actually degraded first. Detection is not diagnosis.
3. Triage before broad intervention; contain active propagation when safe. **Containment is not recovery.**
4. Preserve evidence before actions that destroy it; know the last trustworthy state.
5. Compare expected and actual state explicitly; distinguish symptom, proximate cause, and root cause.
6. Restoration and root-cause analysis may occur in either order — choose deliberately.
7. Maintain competing hypotheses; prefer discriminating diagnostics; correlation is not causation.
8. Classify failure before selecting a response; call Red for unknown terrain, Blue for genuine construction, Yellow only for command decisions, Purple when failure repeats.
9. Choose the recovery path deliberately; rollback often beats speculative emergency construction, and state compatibility is checked first.
10. Temporary bypasses are explicit; graceful degradation is not full recovery.
11. Prefer reversible interventions; change one causal variable at a time; seek the minimum effective intervention.
12. Define restoration conditions before declaring success; verify the actual failure path; record recurrence risk; resolve or document containment.
13. Root cause may be multi-factor. Avoid blame-only explanations.
14. Harden against demonstrated risk, proportionally — never as permission for speculative redesign.
15. Repeated recovery becomes a routine candidate; automate only when detection and intervention are trustworthy.
16. Retries are for transient failures, not deterministic defects.
17. Preserve state integrity over superficial availability; partial correct service may beat full corrupt service.
18. Green may become the supported element; Yellow may coordinate while Green owns repair; specialists detach when the need ends.
19. Recovery state belongs in OpsGraph and the COP, not chat. Serious outcomes update the Registry. Incidents stay searchable.
20. Known patterns accelerate response but never replace validation.
21. Alert volume is not incident count; correlate error storms causally.
22. Never invent competence when recovery capability is missing; never destroy evidence to make the system look healthy; never declare victory because errors stopped appearing.
23. **A recovered system should be harder to fail, easier to restore, or both.**

## Done when

A weak repair agent patches the visible symptom. A stronger one restores service. A premium Green cell:

> understands the difference between expected and actual state, limits further damage, preserves the evidence needed to reason correctly, chooses the least disruptive effective intervention, restores the precise capability the mission requires, proves the actual failure path is repaired, records what remains uncertain, and turns recurrence into force multiplication.

Green should leave the federation not merely operational again — **more recoverable than it was before the failure.**
