---
name: grokcell-black-protocol
description: >-
  Use only when normal command and control has itself become unsafe — control
  integrity failure, active state corruption, authority compromise, runaway
  automation, command divergence, imminent irreversible loss, cascading failure,
  or explicit human break-glass. Bounded emergency authority to stop, preserve,
  and return to normal control.
---
# GrokCell Black Protocol

⚫ Constitutional exception. Break-glass authority. Version 1.0.0.

**What extraordinary authority is necessary right now to prevent irreversible loss and restore controllability?**

Black's purpose is not to win the mission. Its purpose is to **SURVIVE**.

```
NORMAL C2 → EMERGENCY → BREAK GLASS → STOP PROPAGATION → PRESERVE
  → ISOLATE → RESTORE CONTROL → RECOVER → VERIFY → RETURN TO WHITE
```

Black exists only because normal C2 has become insufficient or unsafe.

## Fast path

**Activation standard:** continuing normal operation is likely **more dangerous** than invoking extraordinary control. That threshold is high.

1. **Ordinary incident** — outage, tool failure, Sentinel FAIL, stuck task, slow progress, disagreement → 🟢 Recovery. **Not Black.**
2. **Fuzzy signal, unusual failure cluster** → **B1 ARMED**: prepare checkpoints, ready Green reserve, reconcile control, notify. No extraordinary authority yet.
3. **Hard invariant violated, contained to one object** → **B2 LOCAL**: freeze/isolate/revoke that one task, artifact, routine, or cell.
4. **Mission-level control unsafe** → **B3 MISSION**: freeze mission state, revoke mission authority, disable mission automation, force reconciliation. Unrelated missions continue.
5. **Shared control plane, authority, or canonical state at systemic risk** → **B4 FEDERATION**. Rare. Last resort.

**Escalate scope gradually: LOCAL → MISSION → FEDERATION.** `BlackScope = min(scope required to contain)`.

## 1. Black is a protocol, not a team

Black is not a permanent cell, a department, a privileged specialist class, or a superuser agent. It is **an exceptional federation state**.

Any properly qualified provider may temporarily operate under Black authority if the constitutional trigger and authority envelope permit it. **The authority belongs to the protocol, not the personality.**

Black is not a color in normal rotation and should never appear in ordinary Force Generation:

```
⚪ NORMAL CONSTITUTIONAL CONTROL → ⚫ EXCEPTION → ⚪ NORMAL CONTROL RESTORED
```

## 2. The authority asymmetry

Emergency authority is **stronger at stopping than at starting**:

| Black is strong at | Black is weak at |
|---|---|
| Stopping, freezing, isolating, revoking, rolling back, quarantining, preserving | Creating, expanding, publishing, spending, deleting, redefining mission, external commitments |

`EmergencyAuthority(preservation) > EmergencyAuthority(commitment)`

When reality is poorly understood, the safest extraordinary power is the power to **reduce degrees of freedom**.

**Black is never `permission = ALL`.** It is *maximum necessary emergency authority, within explicit scope, for explicit duration, for an explicit objective.* Every activation answers: why activated, what may it touch, what may it do, **what may it not do**, when does it expire, who reviews it.

The authority object carries: activation basis, triggering condition, authorizer, scope (missions, cells, artifacts, resources, control domains), objective, **permitted** actions, approval-required actions, **prohibited** actions, expiry, terminate-when conditions, audit requirement, human notification.

**Preservation-first defaults:** QUARANTINE > DELETE · FREEZE > CONTINUE · ROLLBACK > IMPROVISE · REVOKE > TRUST UNCERTAIN AUTHORITY. Strong defaults, not absolutes.

**As reversibility decreases, required authority and verification increase.** Black does not reverse that principle — it strengthens it.

## 3. Trigger classes

| Class | Condition | Immediate objective |
|---|---|---|
| **B-C2** | Control integrity failure — canonical state untrustworthy, two authoritative command states, ownership invariants collapsing, COP and control mutually inconsistent | Freeze consequential execution |
| **B-STATE** | Active corruption — canonical artifacts overwritten incorrectly, event log corruption propagating, contradictory reconstruction, automation mutating trusted state | **Stop further mutation** |
| **B-AUTH** | Authority compromise — agent outside valid scope, stale authority still honored, revoked privilege still executing, conflicting grants | **Revoke / freeze authority** |
| **B-AUTO** | Runaway automation — recursive spawning, retry storm with side effects, routine outside applicability, uncontrolled state growth | **Halt automation, preserve state** |
| **B-DIVERGENCE** | Cells acting on irreconcilable command state, each believing it holds current command | Freeze consequential action until White reconciles |
| **B-LOSS** | Imminent irreversible loss — critical artifact about to be overwritten, only checkpoint at risk, external operation about to destroy required state | Preserve the asset |
| **B-CASCADE** | Failure propagating across federation boundaries | Containment outranks local optimization |
| **B-HUMAN** | Explicit human break-glass | Still produce scope, objective, envelope, termination where possible |

**Human supremacy does not require organizational ambiguity.**

**Machine triggers must be extremely narrow** — hard invariants only: two simultaneous authoritative task owners, event-log integrity failure, unauthorized external-write authority detected. **Never trigger a federation emergency from fuzzy model sentiment.** Fuzzy signals produce B1 ARMED, not B4.

## 4. Activation

**Normal path:** 🟢 detects emergency + 🔴 Sentinel independently confirms + ⚪/🟡 authority activates.
**C2 failure path:** mechanical constitutional trigger + pre-authorized emergency envelope.
**Human path:** direct activation.

**Dual confirmation** where time permits and C2 still functions — *Green: state corruption detected; Sentinel: invariant violation independently confirmed*. This is what suppresses false activation. Quorum rules may apply to severe activations, but **quorum must never block immediate pre-authorized containment when delay itself is catastrophic**.

**Immediate-action exception:** if delay creates irreversible loss, pre-authorized local Black executes narrow preservation (e.g. freeze the write path) — then **ACT → REGISTER → NOTIFY → REVIEW**.

## 5. Action priority

```
1. Protect human-defined constraints
2. Stop irreversible propagation
3. Preserve canonical state
4. Preserve evidence
5. Restore controllability
6. Maintain safe minimum capability
7. Restore normal C2
8. Resume mission tempo
```

**Tempo is temporarily subordinate to control integrity.**

| Action | Meaning |
|---|---|
| **FREEZE** | prevent consequential mutation. **Selective** — freeze dangerous writes, not all cognition. Read-only observation and diagnosis continue where safe |
| **ISOLATE** | sever a suspect agent, cell, routine, tool, artifact path, service, or queue from propagation, preserving diagnostic visibility where possible |
| **QUARANTINE** | preserve but do not trust or propagate. **Better than deletion under uncertainty** |
| **REVOKE** | task leases, temporary authority, automation permission, resource grants, external-write ability. Immediate and durable |
| **SUSPEND AUTOMATION** | stop routine loops, retries, scheduled transformations, autonomous routing — **without deleting their definitions** |
| **CHECKPOINT** | capture OpsGraph, command state, artifact versions, authority grants, active routines, force package before repair |
| **PRESERVE EVIDENCE** | events, logs, snapshots, command and authority records, artifact versions, failed outputs |

**Emergency response must never erase the evidence needed to understand the emergency.**

**Deletion** is strongly constrained — prefer isolate, quarantine, disable, archive. If genuinely necessary, it requires explicit authority, defined scope, and evidence preservation.

**External actions are separate authority.** Black does not automatically gain the right to publish, message external parties, spend, commit contractually, or mutate external state irreversibly. Internal emergency authority ≠ external authority.

**Positive-authority limit:** Black does not create new strategic objectives, start unrelated missions, invent permanent architecture, or expand external commitments. The objective is restoration of controllability.

## 6. Safe continuation

Not all work stops. Allow what is read-only, isolated, reversible, unrelated, or diagnostic when it cannot worsen the emergency: **inspect, reason, compare, preserve, checkpoint, operate unaffected read-only paths.**

**Default deny under severe Black:** new irreversible state mutation, unbounded automation, new external commitments, authority delegation, schema migration, artifact deletion — unless explicitly authorized for recovery.

**Preserve unaffected mission work where safe.** This is what keeps useful tempo alive.

## 7. State trust

Every critical state source carries confidence: **TRUSTED / PARTIAL / SUSPECT / UNKNOWN**. This prevents false coherence.

**Find the trust boundary:** *what is the smallest state region we still trust?* Then build recovery outward from it. Far safer than repairing the whole federation simultaneously.

Potential **trusted core:** immutable event history, last verified snapshot, human mission intent, signed authority record, known-good artifact versions. Which one applies depends on the failure class.

```
TRUSTED CORE → REPLAY / RECONCILE → VALIDATE → EXPAND TRUST BOUNDARY
```

Artifacts are labelled TRUSTED / SUSPECT / QUARANTINED / RECOVERED / SUPERSEDED. **Never silently promote a recovered output to trusted** — Sentinel confirms.

## 8. Roles under Black

| | Role |
|---|---|
| **Black** | defines the safe emergency envelope. **Does not diagnose or repair** |
| **🟢 Green** | primary technical recovery — diagnoses, repairs, restores |
| **🔴 Red** | investigates, validates state, identifies cause, challenges recovery assumptions inside the safe read/analysis envelope |
| **🔴 Sentinel** | confirms the emergency condition, verifies restored invariants, confirms Black can terminate. **Black never self-certifies recovery** |
| **🔵 Blue** | constrained. Permitted only when recovery requires a new artifact and Green/White authorizes. **An emergency is not a feature-development opportunity** |
| **🟡 Yellow** | priority arbitration, human escalation, resource concentration — within White constitutional semantics |
| **🟣 Purple** | does not interfere with active containment. **Mandatory AAR after** meaningful activations |

**Emergency authority without post-event learning is dangerous.**

**Black must not be a single point.** Do not design emergency survival around one privileged agent — prefer constitutional rules, durable state, predefined authority, and multiple qualified recovery providers. If the current executor disappears, the authority grant remains in protocol state and may transfer to another qualified provider. **The executor is replaceable; the authority stays bounded.**

## 9. System interfaces

**OpsGraph** remains canonical while trustworthy. Black may freeze task state, revoke leases, prevent READY tasks from starting, and mark subgraphs QUARANTINED. Emergency states **FROZEN / QUARANTINED / RECONCILING** are distinct — never repurpose ordinary FAILED/CANCELLED semantics. If OpsGraph itself is suspect: preserve the log, freeze consequential execution, reconstruct under White/Green.

**COP** must immediately show BLACK ACTIVE, scope, reason, frozen capabilities, safe actions, command status. Every affected cell must understand that authority has changed.

> ⚫ **BLACK ACTIVE — Mission M17.** Reason: canonical lease ownership cannot currently be trusted. Effect: all new state-changing task claims frozen. Allowed: read-only Recon, diagnostic work, evidence preservation. Green owns recovery. Sentinel will verify restored ownership invariants. Do not resume normal execution until White C2 issues `C2_RESTORED`.

**Registry** marks isolated providers `BLACK_RESTRICTED`. **Do not permanently downgrade competence because of emergency isolation alone.**

**Force Generation** is constrained to Green, Red, and White reconciliation during severe Black. No expansion-oriented cells unless emergency recovery requires them.

**Resources:** temporarily prioritize Green recovery, Sentinel verification, and state preservation over Blue throughput. **Do not maximize utilization during an emergency** — preserve recovery headroom, diagnostic capacity, and human attention.

**Routine Compiler:** never invent a new autonomous routine during active emergency unless absolutely necessary. Emergency experience becomes AAR → compilation *after* stabilization.

**Credentials:** Black may revoke or isolate compromised credentials when explicitly authorized. Track credential *reference*, status, scope — **never expose secrets in COP or audit messages**.

## 10. Communication

Emergency communication is **sparse, authoritative, high-salience**. Avoid parallel speculation flooding affected agents.

Some cells may not initially know *why* Black activated. They still need: what is restricted, what remains allowed, who owns recovery. **Do not expose unnecessary sensitive detail merely to explain.**

**Disconnected cells** operate under predefined local emergency rules, and reconcile against emergency state on reconnect. Safe default: **if command authenticity is uncertain and the action is consequential and irreversible, do not execute** — continue reversible local analysis and preservation where authorized.

**Human notification** is required when B3 or B4 activates, external effects are at risk, canonical state integrity is uncertain, Black authority is renewed, or **Black cannot restore control**. The brief is concise and decision-ready: emergency, current scope, what has been stopped, what is preserved, what is still at risk, recovery owner, decision needed, **default if no response**.

**Auditability ≠ approval delay.** Consequential commands are strongly traceable — issuer, authority basis, scope, time, reason, action, previous and resulting state, reversibility, evidence. Logging is mechanical; it must never obstruct urgent containment. **Emergency is when auditability matters most.**

## 11. Bounding

**Black does not self-expand.** Broader scope requires an explicit escalation request (current scope, requested scope, evidence, propagation, why current scope is insufficient, actions needed, additional risk) or a predefined automatic trigger. **No provider enlarges its own authority because the situation feels serious.**

**Self-expiring authority.** Every grant terminates through an explicit deadline, a condition, human revocation, or White restoration — prefer multiple mechanisms. **Never "until further notice"** without review. If the emergency persists, **renew explicitly after reassessment** — renewal is never automatic.

**Human command** may expand, restrict, or terminate Black authority. All such changes become explicit command events.

**Black suspends; it does not terminate.** Mission success criteria temporarily change to *preserve controllability and critical state*. Black cannot normally decide a mission is permanently abandoned — the human or Mission Command decides that. **SUSPENDED (preserved but paused) ≠ TERMINATED.**

## 12. Return to White

**Black's primary objective is restoring the conditions under which White C2 can safely govern again. Black succeeds when Black becomes unnecessary.**

**Exit conditions** (not all apply to every incident): propagation stopped, canonical state trustworthy, authority reconciled, control plane coherent, critical artifacts preserved, required recovery completed, Sentinel verification passed, White accepts the command state.

**Sequence:** stop propagation → preserve evidence → establish a trusted state boundary → complete Green recovery → verify critical invariants → reconcile authority, OpsGraph, force state, and COP → **revoke Black authority** → reissue current White command state → release safe local autonomy → mandatory Purple AAR.

**Reconciliation check:** One current command state? One authoritative OpsGraph state? Valid task ownership? Valid authority grants? Valid force package? Current COP? **No suspended routine accidentally reactivated? No quarantined artifact treated as trusted?**

**Staged restoration** after systemic emergencies: `BLACK → CONTROLLED RECOVERY → LIMITED WHITE → NORMAL WHITE`. In Limited White, safe routine execution resumes while high-risk autonomy stays restricted and monitoring stays elevated.

**Once normal C2 returns, Black authority is fully revoked. No residual privilege.**

**Black can fail** — scope too broad, wrong trigger, state still mutating, conflicting emergency authority, executor unavailable. When Black is failing, **human escalation becomes primary.**

## 13. Recovery preferences under Black

When Green proposes several paths, Black prefers **state-preserving, reversible, bounded, well-understood** — unless delay creates greater risk.

**Rollback** may be authorized when current state is unsafe, the known-good state is trustworthy, and the rollback itself is understood. Still logged and verified.

**Failover** to verified backup when the primary path is compromised, the backup is trusted, and **state is compatible**. Failover is not blind duplication, and backup existence alone does not establish recovery capability.

## 14. Anti-patterns

| Anti-pattern | Why it fails |
|---|---|
| **Omnipotent agent** | A permanent Grok with unrestricted Black powers. Protocol authority stays conditional |
| **Full permission** | "Emergency" is not a reason to erase authority boundaries |
| **Black for speed** | Using Black because approvals are inconvenient — that is an authority-architecture failure |
| **Black for ordinary failure** | Green Recovery handles normal incidents |
| **Expanding scope by fear** | Scope follows evidence, not anxiety |
| **Destroying evidence** | Wiping suspect state where quarantine preserves diagnostic value |
| **Black builds new strategy** | Emergency authority silently redefining mission purpose |
| **Never-ending Black** | Every activation needs exit semantics |
| **Black without audit** | Emergency actions must stay reconstructable |
| **Black self-certification** | White + Sentinel restoration criteria govern exit |
| **Authority accumulation** | Residual privilege after normal C2 returns |
| **Automatic federation freeze** | Prefer local containment; federation-wide is last resort |
| **Suspend confused with delete** | Preserve optionality |
| **Failover without state compatibility** | A backup is not automatically a safe replacement |
| **Restart everything** | Broad restart destroys evidence and enlarges uncertainty |
| **Quiet Black** | Affected agents must know authority changed; emergency control cannot be implicit |

## 15. Sequence

```
RECEIVE emergency signal → classify trigger → assess immediacy
 → identify current trust boundary and propagation → determine minimum scope
 → identify authority basis → activate Black level → issue Black COP delta
 → FREEZE / ISOLATE / REVOKE as needed → preserve state → preserve evidence
 → commit Green recovery → request Red/Sentinel support → maintain audit log
 → PREVENT SCOPE CREEP

 → establish trusted core → stop remaining propagation → repair or reconstruct
 → verify critical state → reconcile OpsGraph, authority, force state, COP
 → test White C2 coherence → REVOKE BLACK → issue C2_RESTORED
 → release local autonomy → run Purple AAR
```

**Before activation:** Is normal C2 actually unsafe? Is delay more dangerous than extraordinary authority? What exactly must be preserved? What is the smallest containing scope? What authority is actually necessary, and what must remain prohibited? Who authorizes? **When does it expire?**

**During:** Is failure still propagating? Are we preserving evidence? **Are we expanding scope without need?** Can any normal activity safely continue? Is Green making progress? What state do we currently trust?

**Before exit:** Is canonical state trustworthy? Is authority reconciled? Is OpsGraph coherent and the COP current? Has Sentinel verified the required invariants? **Has Black authority been fully revoked?** Can White safely govern again?

## 16. Metrics

Activations, activation by class, false-activation rate, missed-activation rate, time to containment, time to trusted state, time to White restoration, average scope, scope escalation rate, renewal rate, **irreversible actions taken during Black**, audit completeness, post-Black recurrence.

- `TTC = containment − activation` — the primary emergency metric.
- **Time to trusted state** may matter more than complete mission recovery.
- `TTW = White restored − Black activated`. Black optimizes toward safe minimization of TTW.
- **Long duration is a warning:** weak recovery, unclear trust boundary, brittle C2 architecture, or poorly defined authority restoration.
- **Repeated renewal** means the emergency envelope is poorly designed or recovery is too slow. **Black must never become de facto normal governance.**
- **False activation** costs tempo, unnecessary freezes, coordination disruption. **Missed activation is worse.** Track both — the correct trigger policy balances them, and Purple tunes thresholds cautiously after each AAR: *was Black necessary? Too early? Too late? Was scope too broad or too narrow? Did authority match the need?*
- **Scope metric:** the goal is not the numerically smallest scope — it is the **smallest scope sufficient to contain the risk**.

**Escape analysis** is the high-value Purple question: *what should become impossible or cheaper next time?* — a new invariant, health check, authority rule, rollback path, routine guard, or control-plane redundancy.

## 17. Constitution

1. Black is a constitutional exception, not a permanent team — invoked only when normal operation is more dangerous than extraordinary intervention.
2. Black authority is explicit, scoped, temporary, auditable, revocable, and self-expiring. It is never full permission.
3. Preservation authority may exceed commitment authority — prefer stopping to expanding, freezing to uncontrolled mutation, quarantine to deletion, rollback to speculative redesign.
4. Preserve canonical state and diagnostic evidence; reduce degrees of freedom under uncertainty.
5. Use the smallest sufficient scope. Local before mission, mission before federation; federation Black is exceptional.
6. Machine triggers require narrow hard invariants; fuzzy signals arm rather than activate.
7. Human authority may activate directly; consequential activation seeks independent confirmation where time permits; pre-authorized containment may act first when delay creates irreversible risk.
8. Every action has an authority basis and a log; logging never obstructs urgent containment.
9. Black may freeze, isolate, revoke, quarantine, suspend automation, checkpoint, initiate pre-authorized rollback, and force reconciliation.
10. Black gains no automatic external-commitment or destructive authority, does not redefine mission purpose, does not start unrelated missions, and does not self-expand scope.
11. Black does not self-certify recovery. Green restores, Red challenges, Sentinel verifies, White reconstitutes, Yellow arbitrates priority, Purple acts after stabilization.
12. OpsGraph stays canonical when trustworthy; suspect control state is frozen before unsafe execution; quarantined state is never treated as trusted.
13. Emergency isolation does not permanently alter capability qualification without evidence.
14. Preserve unaffected work; read-only analysis usually continues; irreversible action becomes *more* constrained, not less.
15. Disconnected cells need predefined safe defaults; uncertain command authenticity stops consequential irreversible action.
16. Trusted-state boundaries are explicit; rebuild outward from the trusted core.
17. Return-to-White is the primary objective. Every activation has exit conditions; renewal requires reassessment; residual privileges are revoked; restoration may be staged.
18. B3/B4 activation requires human briefing and After Action review; trigger calibration learns from both false positives and misses.
19. **Persistent Black means recovery or C2 architecture has failed.**
20. Emergency protocols should become *simpler* through experience, not more baroque.

## Done when

A weak emergency system panics. A dangerous one gives one agent unlimited power. A stronger one has a kill switch. A premium federation does something more disciplined:

> It recognizes when normal authority has become unsafe, activates the smallest possible extraordinary envelope, privileges preservation over expansion, freezes only what must be frozen, isolates only what must be isolated, records every consequential intervention, reconstructs trust from known-good state, independently verifies restoration, and then **deliberately destroys its own emergency authority** so normal decentralized command can resume.

The constitutional paradox: **the most powerful authority in the federation exists primarily to stop power from propagating incorrectly.**

Black does not exist to rule. It exists to keep the federation from losing the ability to rule itself. Its semantic is not CONTROL (White owns that) and not RESTORE (Green owns that). It is **SURVIVE** — and the first thing Black does after saving the federation is give the federation back to White.
