# Prime Manager — Roadmap

**Repository:** `jaydumisuni/Prime-Manager`  
**Product:** Prime Manager  
**Authority:** THETECHGUY DIGITAL SOLUTIONS / Prime OS architecture  
**Reviewed baseline:** `main` at `375ca5475d97d9378e5ecfd86ff2c24b5137c103`  
**Status:** **AUTHORITATIVE SATURATED PRE-PM0 ROADMAP**  
**Review state:** architecture saturation review complete; PM0 implementation not started

---

# 1. Purpose

Prime Manager is Prime OS's first-party deep system-management and operator application.

It is not merely a process table, graph dashboard, Linux administration frontend or clone of another operating-system task manager. Its purpose is to give an authorized operator a mechanically defensible view of one Prime Host and to request bounded machine actions through Prime-owned authority.

Prime Manager should make it possible to answer:

- what Prime Host is this;
- which Prime generation, kernel and Core build are running;
- what hardware is present and how it is currently assigned/bound;
- which Prime capabilities and Providers are supported, active, dormant, degraded, unavailable or incompatible;
- which workloads are running and why;
- who or what initiated each workload;
- which Application Profile and Workload Policy admitted it;
- which runtime/backend/provider executes it and where;
- which processes implement it;
- which processes are unmanaged, shared or unattributed;
- which services exist and which activation instances are active;
- what CPU, memory, GPU, storage, I/O, network, thermal and power resources are consumed;
- what each metric actually means and whether values are summable;
- what resource constraints were declared and what is mechanically enforced;
- what stronger constraints come from providers, system clamps or future external leases;
- what can be terminated, suspended, resumed, restarted, constrained or diagnosed;
- which actions are unavailable and why;
- what exact target was authorized;
- whether that target changed before commit;
- what Prime Core accepted, denied, failed, committed or could not determine;
- what authority performed the effect;
- what was mechanically observed afterward;
- whether reboot/update/rollback/recovery is safe;
- what workloads or in-flight actions block that transition;
- what happened around an incident;
- what evidence supports each conclusion.

Prime Manager should become the best local operator surface for understanding Prime.

---

# 2. Permanent product rules

## 2.1 Workload-first, process-deep

> **Prime Manager is workload-first and process-deep.**

A logical Prime workload is the preferred managed unit where Prime owns workload identity. Processes remain available for low-level inspection. Prime Manager must not reduce Prime to a flat table of Linux PIDs.

## 2.2 Prime owns machine truth

> **Prime Manager observes, explains and requests control through Prime Core and approved Prime Providers. It never becomes Host authority.**

## 2.3 Unknown remains unknown

> **When Prime does not know, Manager reports UNKNOWN.**

No fake zeroes, ownership, compatibility, completion, ordering, precision or resource attribution.

## 2.4 Support broadly, activate narrowly

Opening Manager must not unnecessarily:

- wake a discrete GPU;
- spin sleeping media;
- launch a VM;
- activate a dormant runtime;
- start a remote Provider;
- unlock encrypted foreign storage;
- bring up a disabled interface;
- enable expensive tracing;
- retain high-cost telemetry after the relevant surface closes.

## 2.5 Distress usefulness

Manager should remain useful under CPU, memory and I/O pressure while the minimum Prime Core, input/compositor and application-admission substrate remains operational.

This does not make Manager:

- a replacement for Prime Recovery;
- immune to security revocation;
- more important than Core, Recovery, compositor or essential input authorities;
- guaranteed to cold-start if Core/application admission itself is unavailable.

Terminal and Recovery remain fallback operator paths.

## 2.6 Observation is not mutation

Opening a view or running preflight must not silently perform the requested target mutation. Any observation that activates hardware/providers or materially perturbs the target must declare that effect.

---

# 3. Permanent authority boundary

## Prime OS / Prime Core owns

- Prime Host identity and lineage;
- generation identity;
- boot and Core epochs;
- hardware graph and device identity;
- capability/Provider registry;
- Prime Exec;
- application admission;
- Application Profiles;
- Workload Policy;
- live workload authority;
- process authority;
- service authority;
- resource accounting and enforcement;
- workload quiescence;
- update/rollback/recovery authority;
- power and thermal coordination;
- device/network/filesystem/secret policy;
- machine-action admission;
- Host action evidence and audit;
- mechanical event authority;
- persistent Host history where provided.

## Prime Manager owns

- presentation;
- navigation;
- search/filter/sort;
- tables, trees and graphs;
- local UI preferences;
- bounded session-local display history;
- disposable non-authoritative cache;
- selection/follow state;
- action-request UX;
- evidence/diagnostic UX;
- report assembly from already-authorized Prime facts.

## Prime Manager must never

- directly mutate `/proc` or `/sys`;
- directly manipulate cgroups or systemd;
- directly manipulate privileged device nodes;
- silently invoke `sudo`;
- expose arbitrary root shell execution;
- expose one generic privileged `execute(action, payload)` API;
- independently scan Host internals and override Core truth;
- create a competing process/workload/service/storage/update/recovery authority;
- parse logs to manufacture structured state.

---

# 4. Ecosystem boundaries

## AgentOps

AgentOps owns semantic Operation lifecycle. Prime owns typed machine actions. A Prime Host action may be correlated with an AgentOps Operation but is not a competing AgentOps operation model.

## Ptah

Ptah owns higher-level Workspace, Activity, Attempt, Environment, Node, Provider, Grant, Lease, Fence, Receipt and Evidence semantics. Prime may later expose stricter constraints imposed by Ptah but does not duplicate Ptah concepts.

## Origins

Origins may aggregate Prime Hosts into Nodes/missions. Origins discovery is not authorization to control a Host.

## Hunter

Hunter may explain Manager evidence. Manager correctness does not depend on Hunter.

## Oracle

Oracle remains an optional AI eyes-and-hands/workstation-control layer. It is not PM5's canonical human fleet-management transport.

## Grid-Knight

Grid-Knight owns cybersecurity interpretation. Manager presents Prime mechanical events/enforcement evidence without becoming a malware judgment engine.

## Prime Terminal

Terminal owns PTY sessions, command parsing and interactive shell/runtime behavior. Manager and Terminal consume the same relevant Prime process/service/resource capabilities. Manager does not become a generic launcher or terminal.

## Prime Shell / Settings

Shell and Settings own everyday quick controls/configuration. Manager owns deep operator inspection and bounded advanced control.

## Prime Recovery

Recovery remains independently usable when normal Prime application/Core operation is unavailable. Manager is not the offline recovery environment.

---

# 5. Prime OS delivery boundary

Prime OS P1 First Light is already separately frozen/proven. Prime Manager must not silently expand that scope.

Default disposition:

> **Preserve Prime OS P1.**

Manager enters the first later Prime generation that explicitly admits it. Once Prime P2 component/package delivery exists, Manager should normally evolve as an independently delivered signed first-party component.

Manager PM phase numbers do not correspond to Prime OS phase numbers.

---

# 6. Current Prime OS gaps that PM0 must close

Before PM1 can exist, Prime OS must evolve beyond current P1 plumbing. The Manager-capable generation requires at minimum:

- scoped non-root system-application authorization;
- per-capability read authorization and disclosure mediation;
- Application Profile permission mediation;
- a recoverable live workload registry;
- asynchronous Prime Exec supervision;
- workload lifecycle events;
- effective enforcement readback;
- live hardware graph revision/events;
- live capability/Provider revision/events;
- observation streaming/framing transport;
- Host action evidence/journal;
- purpose-bound operator authorization;
- renderer/broker privilege separation.

Current root/shared-socket-group P1 mechanisms remain implementation history, not the permanent Manager security architecture. Manager must never be made UID 0 merely to bypass missing mediation.

---

# 7. Product shape

Initial primary navigation:

1. **Overview**
2. **Workloads & Processes**
3. **Performance**
4. **Hardware**
5. **Storage**
6. **Network**
7. **Thermals**
8. **Services**
9. **Drivers**
10. **Prime**

Later depth may introduce Startup & Background, richer Power/Energy, Host Login Sessions after Prime defines a real session authority, and diagnostics sub-surfaces. Do not prematurely freeze every possible feature as a top-level tab.

---

# PM0 — Authority & Contracts

## Goal

Freeze all machine semantics required by Prime Manager before UI engineering becomes accidental operating-system architecture.

PM0 is primarily Prime OS/Core contract work. Prime Manager is the first major consumer.

---

# 8. PM0 reusable capability families

Prime OS should define or reconcile reusable capability families for:

- workload inventory/lifecycle/control;
- process inventory/control;
- service inventory/control;
- resource control;
- telemetry;
- mechanical Host events;
- bounded logs;
- Prime Host action evidence;
- Host audit;
- operator/client authorization;
- disclosure policy;
- workload quiescence;
- update/recovery projections;
- public system-status projections required by Manager.

Existing authorities remain canonical for Host identity, generation, capability registry, hardware, storage, Application Profiles, Workload Policy, Prime Exec, driver trust and Host health.

No Manager-specific root capability.

---

# 9. Required vs optional capability dependencies

Manager must have a minimal required capability set sufficient to authenticate the client, identify the Host, negotiate Core compatibility and display basic degraded state.

Telemetry, storage depth, GPU, diagnostics, optional Providers and other advanced capability families remain negotiated/optional where possible. Their absence degrades only affected surfaces.

---

# 10. Trusted application architecture

Preferred shape:

```text
unprivileged renderer
        ↓
typed allow-listed bridge
        ↓
minimal trusted Manager broker/native host
        ↓
Prime Core secure IPC
```

The renderer must not be capable of opening privileged Core IPC directly.

The separation must be mechanically enforced through Prime sandboxing, broker-only handles, separate privilege domains or an equivalent Prime mechanism.

### Renderer rules

The renderer receives:

- presentation data;
- safe action status;
- no reusable authorization grant;
- no preflight/fencing commit token;
- no generic Core request primitive;
- no unrestricted shell primitive;
- no unnecessary direct network authority for local PM1.

External content never retains the bridge-enabled trusted origin.

Production renderer devtools/remote debugging are disabled unless explicitly enabled through Prime Developer Mode.

### Broker responsibilities

The trusted broker:

- is mechanically bound to the admitted Manager workload/client instance;
- opens Core IPC;
- negotiates contracts;
- allocates action IDs before submission;
- retains opaque authorization/preflight material;
- validates schemas and structural bounds;
- converts lossless integer/path representations;
- handles reconnect;
- clears privileged state when the final Manager UI session closes.

The broker is not another Host authority.

---

# 11. Manager instance semantics

PM0 explicitly decides whether one Manager client instance per login/session is enforced or multiple simultaneous instances are supported.

If multiple are supported, each has a distinct client-instance identity. Grants, subscriptions, preflights and action identity are instance-bound.

---

# 12. Common observation envelope

Dynamic projections should carry enough metadata to establish:

- Host ID and lineage context;
- generation;
- boot epoch;
- Core epoch;
- Provider/source identity and epoch where relevant;
- observation timestamp;
- source monotonic sequence/time where relevant;
- local receipt time for remote/provider data;
- opaque revision/precondition token;
- completeness;
- authorization scope;
- limitations.

Different capability families may have independent consistency/revision domains. Manager must not imply that the entire machine was observed atomically unless Prime explicitly guarantees it.

---

# 13. Stable identity model

Freeze semantics for:

- Host;
- generation;
- boot;
- Core;
- Provider instance;
- application;
- Application Profile revision;
- Workload Policy revision;
- workload instance;
- workload launch;
- process instance;
- thread instance later;
- service definition;
- service activation instance;
- device/interface/storage/sensor/driver binding;
- Host action;
- principal/client instance.

---

# 14. Host migration / rebind / clone safety

Moving Prime storage to materially different hardware normally yields a new Host identity.

Manager persistence is split into:

- **global user preferences** — layout, columns and similar UI choices;
- **Host-scoped non-sensitive cache/history** — keyed to exact Host/lineage identity;
- **disclosure-gated detail** — memory-only by default;
- **Host action/audit truth** — never Manager-owned.

Old Host snapshots/actions may remain historical lineage evidence but never become current state on a newly enrolled Host.

If cloned storage produces ambiguous/forked Host identity, fleet mutation fails closed until Prime Host identity authority resolves it.

---

# 15. Single-Core authority and Core epochs

Prime maintains one authoritative Core instance per Host/boot authority domain.

Manager-era Core requires:

- instance locking/fencing;
- explicit Core epoch;
- stale-Core invalidation;
- Provider-side Core-epoch fencing.

A superseded Core must not retain privileged Provider mutation authority.

---

# 16. Execution path and placement

Do not permanently model execution as one flat enum.

Reserve a revisioned execution path, for example:

```text
Prime Host → Provider → VM → guest runtime → guest process
```

or:

```text
Prime Host → VM → container → process
```

Each layer may expose identity, Provider, resources, observation depth, mutation depth, fence and clock domain.

Placement may change during workload lifetime. Actions whose safety depends on placement bind the observed placement revision.

---

# 17. Workload lifecycle and continuity

Use a portable workload lifecycle class such as:

- ADMITTED;
- STARTING;
- RUNNING;
- SUSPENDED;
- STOPPING;
- COMPLETED;
- FAILED;
- INTERRUPTED;
- LOST_OR_UNKNOWN.

Providers may expose richer native detail.

Each backend declares whether a workload instance can survive Core restart, Host reboot or Provider reconnect. Continuity must be mechanically proven. Otherwise Prime creates a new workload instance identity or reports the prior state interrupted/unknown.

Completion should carry a portable class such as SUCCEEDED, FAILED, TERMINATED, CRASHED, INTERRUPTED or UNKNOWN plus optional domain-native status.

---

# 18. Live workload registry

Historical launch evidence is not live workload truth.

Prime requires a recoverable live workload authority containing:

- workload identity;
- current lifecycle;
- current placement;
- active process membership;
- supervisor/provider;
- Application Profile/Policy provenance;
- effective enforcement;
- active runtime overrides;
- quiescence classification;
- protection/action availability.

Core restart reconstructs only what can be mechanically recovered.

---

# 19. Prime Exec launch evolution

Manager requires Prime Exec to evolve from launch-through-completion to:

```text
admit
→ assign workload/launch identity
→ persist admission evidence
→ return live identity immediately
→ supervise asynchronously
→ emit lifecycle events
→ preserve final completion evidence
```

Launch provenance must record initiating principal/client/system authority, exact Profile/Policy revision, generation, runtime/backend/provider, and optional Origins/AgentOps correlation.

---

# 20. Process identity and process domains

PID alone is never mutation identity.

Host-native process safety may use boot epoch + PID + start identity + pidfd/equivalent. After Core restart, a lost process handle must be mechanically reconstructed or the process receives a new Prime process-instance identity.

A process can `exec()` a different image without changing PID, so action-relevant process state must use revision domains/precondition tokens for instance lifecycle, image/security state, ownership/credentials, workload membership and protection.

Telemetry has its own sample sequence.

Processes may expose scoped PID aliases across namespaces. Prime process identity remains canonical.

---

# 21. Portable process state, ownership and containment

Use a portable lifecycle state plus optional backend-native detail. Linux-specific states such as ZOMBIE or UNINTERRUPTIBLE remain native detail rather than universal semantics.

Separate:

- application/component ownership;
- workload owner/admitting principal;
- initiating principal;
- execution credential/account.

DynamicUser/root/Administrator display names are not sufficient ownership authority.

Process parent/child ancestry remains within one process domain. VM/container/runtime containment is a separate execution graph.

Valid classification includes managed workload member, Host service, kernel/system process, unmanaged user process, runtime/provider helper, shared infrastructure and unknown/unattributed.

---

# 22. Workload membership

One process need not belong exclusively to one workload.

Represent primary membership, shared/provider infrastructure, Host-service infrastructure and unattributed relationships.

Shared infrastructure is not arbitrarily charged to whichever workload was observed first.

---

# 23. Service model

Separate:

- stable service definition;
- definition/configuration revision;
- 0..N activation instances;
- Provider/supervisor;
- persistence kind.

Persistence kind distinguishes persistent Prime services, transient workload supervisors, per-session/on-demand instances and Provider/guest services.

Use a portable service lifecycle plus optional backend-native detail.

Canonical activation policy may include BOOT, LOGIN, ON_DEMAND, EVENT, SCHEDULED, MANUAL and DISABLED.

Persistent activation change versions the service-definition/configuration authority. It does not mutate a transient runtime unit in place.

Service control scope distinguishes definition, one activation instance and all matching instances.

---

# 24. Summary/detail, completeness and pagination

Inventory tables use bounded cheap summaries. Rich detail loads on selection.

Detail may include full argv, rich provenance, environment, open files, sockets, policy depth, logs and diagnostics.

All truncation is explicit.

Completeness may be complete-for-authorized-scope, filtered, partially unavailable, truncated or Provider-degraded. Completeness metadata itself obeys disclosure policy and must not reveal hidden-object counts where existence is protected.

Pages of one inventory belong to one snapshot/revision. If the token expires, return `SNAPSHOT_EXPIRED` / `RESYNC_REQUIRED`; never splice different snapshots into one table.

---

# 25. Cross-projection references

Workload/process/service projections may be independently revisioned. Relationships can resolve to live, tombstoned or unresolved/stale targets.

Manager never repairs missing graph relationships by guessing.

---

# 26. Observation stream

Preferred model:

```text
snapshot → cursor → sequenced events
```

Freeze event IDs, sequence, cursor, heartbeat, replay, add/change/remove, tombstones, overflow, resync, subscription lease and cleanup.

Snapshot and stream must connect without an unobservable gap.

Delivery classes:

- telemetry — lossy/bounded with explicit gaps;
- lifecycle/state — stronger replay/reconciliation;
- Host action/audit — durability according to evidence policy.

Older clients may safely ignore allowed additive unknown event classes but must then mark interpretation partial.

---

# 27. Transport/framing

Transport/framing version is distinct from Core envelope, capability semantic version and payload/evidence schema version.

Prime may migrate from bounded HTTP/JSON request/response to a framed stream while preserving workload/process semantics.

Slow/flooding telemetry must never starve control-plane actions.

Freeze queue bounds, subscription quotas, per-client concurrency/rate limits, diagnostics limits, frame/message/cardinality/nesting/string bounds, cancellation and slow-consumer behavior.

Malformed/ambiguous encodings are rejected before expensive processing.

---

# 28. Canonical serialization and version evolution

Cross-component digests use canonical typed serialization, not arbitrary JSON text.

Version axes:

1. Core envelope;
2. transport/framing;
3. capability semantic version;
4. request/response schema;
5. evidence/artifact schema.

Freeze syntax, comparison and range negotiation.

Older clients may ignore explicitly safe unknown response fields. Older Core/Providers must not silently ignore unknown mutation/preflight fields that might contain safety semantics.

Unknown protection/risk/permission/disclosure semantics fail closed.

Capability lifecycle remains INTRODUCE → COEXIST → DEPRECATE → prove migration → RETIRE.

`prime-contracts` should produce machine-readable schemas/fixtures for non-Rust consumers and cross-language conformance tests.

---

# 29. Capability state and Provider lifecycle

Keep separate:

- supported;
- available;
- activation state;
- health;
- compatibility.

A capability may be healthy enough to activate but intentionally DORMANT.

Manager must not wake dormant Providers merely to populate a graph.

A privileged action binds the Provider/preflight environment it was authorized against. Provider replacement normally invalidates the action/preflight unless the contract explicitly declares equivalent safe failover semantics.

---

# 30. Provider-owned mutation

For Provider-owned targets, the Provider contract must define:

- identity/fencing token;
- authoritative commit boundary;
- action-ID propagation;
- idempotency/replay class;
- execution deadline/lease;
- cancellation behavior;
- reconciliation method;
- stable error code;
- evidence strength;
- Provider epoch continuity semantics.

If strong enough target identity/fencing does not exist, mutation remains unavailable.

Nested execution preserves one Host action/correlation ID end-to-end while each layer authenticates the next and contributes its own fence/evidence.

---

# 31. Telemetry semantics

Freeze exact meanings for CPU, memory, swap, pressure, storage/I/O, network, GPU, thermals, power and energy.

Every percentage identifies its denominator, for example Host capacity, one logical CPU, assigned vCPU set, workload quota or memory limit.

Every metric states provenance such as Core-observed, Provider-observed/attested, derived, estimated, shared, unattributed, unsupported or unavailable.

Every metric states accounting domain and whether it is summable with another metric.

Avoid double counting tmpfs, zram, integrated-GPU shared memory, VM/guest memory, Provider overhead or remote storage.

Historical graphs preserve denominator/provider/epoch discontinuities rather than drawing misleading seamless percentages.

---

# 32. Resource enforcement

Each effective control states its enforcement layer and strength, for example Host kernel, cgroup/workload, VM, guest, Provider, system clamp, external stricter lease; HARD, PROVIDER_ENFORCED, BEST_EFFORT, ADVISORY or UNKNOWN.

Manager distinguishes:

- declared Prime Policy;
- effective backend enforcement;
- inherited restriction;
- runtime override;
- Provider/external constraint;
- emergency clamp;
- unsupported declaration;
- out-of-band drift.

Requesting an enforcement property is not proof that it became effective. Core/Provider performs mechanical readback where possible.

---

# 33. Resource mutation

Keep distinct:

- scheduler priority;
- CPU weight/quota;
- CPU affinity/cpuset/topology;
- memory/swap limits;
- process count/runtime duration;
- I/O weight/priority/bandwidth;
- storage quota;
- GPU policy;
- workload network/device policy.

CPU affinity uses scalable sets/ranges, not fixed 32/64-bit masks.

Scheduler priority uses bounded canonical intent plus backend detail; unsafe realtime classes require separate authority/proof.

Process-instance changes, running-workload overrides and persistent future-launch policy changes are distinct.

Persistent policy edits create one coherent new immutable revision using compare-and-swap against a base revision. `Revert` creates/selects a new revision rather than rewriting history.

If one shared Provider helper serves multiple workloads, per-workload control is available only when the Provider can isolate the effect.

---

# 34. Suspension semantics

Suspension can have multiple simultaneous causes.

Expose requested suspension intents, effective suspended state and active constraint sources. Clearing one cause does not imply that the workload resumed if another still holds it suspended.

---

# 35. Quiescence

Prime owns quiescence classes such as SAFE_TO_STOP, CHECKPOINTABLE, DURABLE_EXTERNAL_STATE, NON_RESUMABLE and CRITICAL.

Host transition may be reported safe only when Prime update/recovery authority says coverage is sufficiently complete. Unmanaged activity, unknown Provider state, incomplete checkpoint knowledge or unavailable capability can yield UNKNOWN/BLOCKED/REQUIRES_CONFIRMATION.

Quiescence includes in-flight Host actions and invasive diagnostics. Prime must complete, cancel/fence, carry durably across transition or block on them.

Manager itself should normally be SAFE_TO_STOP/reconstructible; ordinary UI state does not block a generation change.

---

# 36. Prime Host Action model

There is no generic privileged action executor.

Typed capability requests share common Host Action metadata/evidence.

The trusted broker allocates an unguessable action ID before first Core submission. Renderer does not choose action IDs.

Core binds action ID to Host, client instance, principal, target and canonical request digest. Same ID + different request is conflict.

Action descriptors include target scope, availability, stable unavailable reason, required permission, risk class, preflight support, replay/reconciliation class, cancellation, expected postcondition, disconnect scope, evidence durability class, rollback/revert support and limitations.

Prefer absolute desired-state requests (`STOP`, `SUSPEND`, `SET_CPU_WEIGHT=200`) over toggle/increment verbs.

`ALREADY_SATISFIED/NO_CHANGE` is a truthful success class when no transition was needed.

---

# 37. Preflight and authoritative commit

Preflight is read/analysis, not target mutation.

A preflight receipt binds the action/request, target, relevant precondition tokens, Provider/epoch, placement revision, capability version, request digest, expiry and Provider fencing state.

Receipts are action-bound unless explicitly declared reusable.

Precondition tokens are opaque source-owned values; Manager does not assume integer revision arithmetic.

For Core-owned objects, Core validates and commits at its authoritative boundary. For Provider-owned targets, the authenticated Provider validates the fence at its own authoritative commit boundary.

---

# 38. Authorization timing

Preflight never substitutes for authorization.

A valid purpose-bound grant is required when Core admits the action.

After durable admission, ordinary grant expiry does not retroactively unauthorize accepted work. Provider fence/deadline controls eventual commit.

A separately defined security revocation may cancel/fence still-uncommitted work where supported. Committed effects require a new remediation action rather than magical rollback.

---

# 39. Action deadlines, cancellation and concurrency

UI/network timeout is distinct from action execution deadline.

Distributed actions carry an authoritative bounded execution lease/deadline.

Cancellation is not rollback and succeeds only before commit when supported.

Closing Manager does not cancel accepted work.

Conflicting actions are serialized, fenced or rejected with conflict. Multi-phase actions must not interleave nondeterministically.

Composite actions preserve phase evidence and revalidate definition/Provider state between phases.

---

# 40. Host Action Evidence

Evidence includes:

- action ID;
- Host/boot/Core epoch;
- Provider/execution path;
- principal and calling client/system authority;
- upstream correlation;
- target and preconditions/fences;
- request digest;
- authorization class;
- timestamps/sequences;
- phases;
- requested/effective values;
- resulting state/revision;
- evidence strength;
- stable result/error;
- limitations.

Evidence strength distinguishes Core-observed, Provider-attested, postcondition-reconciled, commit-proven, state-matches-without-proven-causality and UNKNOWN.

Non-human actors such as update controller, watchdog, Grid-Knight or remote client are represented explicitly rather than flattened to a user actor.

---

# 41. Durable action journal

For effects not atomically coupled with evidence storage:

```text
persist accepted action
→ durability barrier
→ dispatch effect
→ append dispatch/commit/final evidence
```

Evidence durability classes may include session/reconciliation, Core-restart persistent, Host-reboot persistent and audit-required.

Full evidence retention and idempotency/replay protection are separate. An expired detailed record must not make reuse of an old action ID become a fresh destructive request. Use a replay horizon/lightweight tombstone policy.

Intentional evidence expiry returns `EVIDENCE_EXPIRED`, not `NOT_FOUND`.

Durable evidence has integrity protection. Reconciliation appends state; it does not silently rewrite prior accepted evidence. Corrupt evidence is explicitly untrusted.

Evidence stores minimum proof parameters and avoids secrets/reusable grants/raw protected payloads.

---

# 42. Expected disconnects

Actions may intentionally disconnect:

- MANAGER_CLIENT;
- CORE_CONTROL_CHANNEL;
- GRAPHICAL_SESSION;
- PROVIDER_LINK;
- REMOTE_HOST_LINK;
- HOST_REBOOT;
- HOST_POWER.

Each scope has explicit reconciliation semantics.

Reboot/recovery/Core-replacement evidence passes the durability barrier before destructive handoff and resides in system-persistent, generation-independent storage appropriate to Core/Recovery.

Where a handoff/action ID can be carried across boot, use it. Otherwise Prime may prove that a later boot happened without falsely claiming that this particular action caused it.

A restarted Core examines durable action state and applies the action's declared reconciliation strategy rather than blindly redispatching all accepted actions.

---

# 43. Retry and read-after-write

Unknown final state, timeout or lost response is a retry fence, not permission to repeat a destructive request.

Reconcile first.

Where possible, completed action evidence returns resulting object revision/state and event correlation cursor so Manager can reconcile a lagging observation stream.

---

# 44. Risk and confirmation

Action risk may be ROUTINE, DISRUPTIVE, DESTRUCTIVE, RECOVERY_CRITICAL or PROHIBITED.

Renderer confirmation is UX, not the security boundary.

High-risk authorization comes from a trusted Prime auth surface and binds exact action, target and preflight. The trusted surface resolves target identity/details from Core rather than trusting a renderer label.

Manager self-targeting actions either use expected-client-disconnect semantics with Core-owned evidence or remain unavailable.

---

# 45. Authorization principal and permissions

Authorization considers:

- human/session principal;
- admitted Manager client;
- admitted workload;
- workload owner principal;
- target ownership/class;
- protection state;
- permission scope;
- step-up grant;
- Provider/remote principal.

Unix UID/GID alone is not sufficient permanent authority.

Do not create one `prime.manager` super-permission. Define granular permission families for ordinary inventory, sensitive detail, process/workload/service control, resource mutation, diagnostics, disclosure/export and recovery-class actions.

Target scope matters: permission to control one's own user workload is not Host-wide authority.

---

# 46. Mechanically bound client identity and grants

Core never trusts a request field claiming `client = Prime Manager`.

The admitted client identity is mechanically bound to the IPC peer/workload.

Purpose-bound step-up grants bind Host, boot/Core epoch, principal, Manager client instance, scope, target and expiry.

Renderer never receives reusable grants or preflight commit tokens.

Grant expiry behaves conservatively across wall-clock rollback, suspend, lock, logout and user switch.

If Prime auth authority is unavailable, new high-risk actions/sensitive disclosures fail closed unless an already-issued grant explicitly supports bounded offline verification.

---

# 47. Read/disclosure authorization

Authorization governs reads as well as writes, including inventory visibility, argv, paths, environment, sockets, logs, policy detail, diagnostics and history.

Errors must not become existence oracles. Where policy hides existence, denied/not-found semantics may collapse into a non-disclosing result.

Core loss never extends a disclosure grant.

Disclosure-gated detail is memory-only by default. Manager purges gated views/subscriptions on expiry/revocation/lock/logout according to policy.

---

# 48. Clipboard, notifications and other leakage channels

Copying protected data is a separate disclosure action and uses a disclosure-aware broker path.

Sensitive data must not automatically flow into window titles, lock-screen notifications, recent-item metadata, search indexes, crash/debug logs or external URLs.

Renderer direct external networking is unnecessary for local PM1. Safe resource-open must not become a data-exfiltration proxy.

---

# 49. Logs and history

Structured Prime state/events are authority. Logs are diagnostics.

Log/history queries are bounded, cursor-based and authorized at query/fetch time.

Cursors are opaque and scoped to Host/source/principal/disclosure context and expiry. A cursor obtained under elevation cannot be replayed after authorization ends.

Server-side snapshots/subscriptions have leases and automatic cleanup after client crash.

Persistent Host history is Prime OS-owned; it need not live permanently inside `primed`.

---

# 50. Export disclosure and artifacts

Export redaction belongs to Prime policy, not Manager-local judgment.

Prime owns versioned disclosure/export profiles defining audience, permitted fields, mandatory redactions, prohibited data and artifact sensitivity.

Long-running export generation and external artifact release are separate authorization points. Delivery/fetch rechecks disclosure.

Exports use authorized artifact/temp storage with retention, digest, cleanup and destination authority. Do not leave plaintext temp copies in ordinary Manager cache.

Large dumps/diagnostic captures use artifact references containing ID, size, digest, sensitivity, retention and authorized fetch class rather than inline huge payloads.

---

# 51. Resource locators

Do not model executable location as one Host pathname.

A locator may represent Host file, content-addressed admitted artifact, container file, guest file, remote Provider resource or unavailable locator.

Separate REVEAL, OPEN, READ, FETCH and EXPORT capabilities.

For local files, locator actions revalidate object identity rather than trusting stale pathname strings through replacement/symlink races.

---

# 52. Manager's own Profile/Policy

Manager needs a bounded Profile/Policy proving:

- sufficient responsiveness under pressure;
- bounded OOM/memory posture;
- I/O responsiveness;
- telemetry shedding;
- renderer restartability;
- no arbitrary root;
- no unrestricted filesystem/home access;
- no unnecessary direct network;
- mediated GUI/GPU/device access only as needed.

Do not invent a `SYSTEM_UTILITY` policy class unless evidence proves one is necessary.

Survive pressure does not mean immune to security isolation, update quiescence, Profile revocation or owner-authorized termination.

Manager preferences use an authorized app-state/config facility or scoped exposure. If persistence is unavailable/read-only, Manager falls back to defaults/memory-only and continues basic management.

---

# 53. PM0 deterministic proof assets

PM0 must produce deterministic fixtures for:

- normal Host/workload/process/service states;
- Host-native and Provider-owned identity/fencing;
- weak-identity read-only domains;
- PID reuse and process `exec()`;
- service definition revision change;
- placement migration;
- Core/Provider restart;
- unknown enum/version fields;
- stream replay/gap/overflow;
- hostile strings/non-UTF8;
- >2^53 values;
- evidence store failure/corruption;
- stale/expired authorization;
- Provider forgery/replay/deadline cases.

Provide a deterministic fake/replay Core.

Add property/fuzz testing for malformed frames, nesting/cardinality bounds, canonicalization and schema/version evolution.

---

# 54. Contract amendment protocol

If physical/implementation evidence disproves a frozen PM0 contract:

```text
STOP affected work
→ preserve failing evidence
→ identify exact contract/version
→ do not implement a private Manager workaround
→ reopen Prime authority
→ design correction
→ assign compatible/breaking version
→ review
→ freeze
→ migrate consumers
→ re-prove
→ resume
```

Historical proof remains bound to the exact old schema/version.

---

# 55. PM0 dependency matrix

Every Manager feature maps:

```text
feature
→ Prime capability
→ capability version
→ schema
→ permission
→ evidence class
→ minimum proven Prime OS authority/milestone
→ degraded fallback
→ Manager phase
```

Manager phase depth never authorizes an OS capability Prime has not yet earned.

---

# 56. PM0 exit gate

PM0 closes only when:

1. all machine fields/actions have explicit authority owners;
2. reusable typed Prime capabilities exist;
3. current P1 authorization limitations have a frozen Manager-capable replacement;
4. client/principal/workload binding is mechanically defined;
5. live workload authority is frozen;
6. execution-path/domain semantics are frozen;
7. target identity/revision/fencing semantics are frozen;
8. Provider mutation/reconciliation semantics are frozen;
9. observation transport and stream semantics are frozen;
10. summary/detail, completeness and pagination are frozen;
11. telemetry/accounting/denominator/provenance semantics are frozen;
12. resource enforcement/constraint semantics are frozen;
13. quiescence is frozen;
14. action IDs/preflight/authorization/evidence/idempotency are frozen;
15. action concurrency and expected-disconnect semantics are frozen;
16. evidence durability, privacy and integrity are frozen;
17. disclosure/export semantics are frozen;
18. renderer/broker privilege separation is frozen;
19. version/schema/canonicalization evolution is frozen;
20. rollback-aware evidence schema is frozen;
21. deterministic fixtures and fake/replay Core exist;
22. negative/fuzz fixtures exist;
23. Manager requires no direct privileged Host workaround;
24. relevant capabilities remain reusable by Terminal/Shell;
25. Prime OS delivery boundary is resolved;
26. owner freezes PM0.

---

# PM1 — Operator First Light

## Goal

Deliver the first genuinely useful Prime Manager backed entirely by live Prime capabilities.

No static proof dashboard counts as completion.

---

# 57. Overview

Show at minimum:

- Host identity and lineage/rebind state;
- hardware model and architecture;
- current generation/image digest/channel/source revision;
- kernel identity/version;
- Prime Core build/revision;
- Host uptime and boot/Core epoch;
- capability compatibility, activation and health;
- CPU, memory, GPU, storage, network, thermal and power/energy headlines where supported;
- workload/process counts;
- service health;
- update/recovery summary;
- important action failures.

---

# 58. Workloads — default view

Show:

- workload identity;
- application;
- workload owner/admitting principal;
- initiator;
- runtime/backend;
- workload architecture and Host architecture;
- translation layer where used;
- execution path/placement;
- Provider;
- Profile/Policy revision;
- generation;
- portable lifecycle;
- start/uptime;
- process count;
- CPU/memory/I/O/GPU/network where available;
- metric accounting domain;
- declared/effective limits and constraint provenance;
- quiescence;
- protection;
- action availability.

Remote/guest metrics must remain visibly scoped and non-summable with local Host totals unless Prime explicitly says otherwise.

---

# 59. Processes

Show:

- stable process identity;
- execution domain;
- scoped PID aliases;
- portable lifecycle and native detail;
- executable identity strength;
- observed executable/resource locator;
- safe argv display;
- workload/service relationship;
- Prime owner/initiator where available;
- execution credential;
- parent/children within domain;
- execution containment breadcrumb;
- CPU/memory/I/O/thread count;
- protection/action availability.

Visible process title/argv is not trusted executable identity.

---

# 60. PM1 process/workload controls

Where safe authority exists:

- graceful terminate;
- force-stop;
- terminate process tree;
- terminate workload;
- suspend/resume;
- scheduler priority;
- CPU affinity.

Unsupported execution domains remain explicitly read-only.

UI actions bind stable object identity, never row position. Paused display/history/tombstone views must re-resolve current target and rerun required authorization/preflight before any action.

---

# 61. Performance

Show:

- total CPU and per logical CPU;
- memory and pressure;
- GPU and dedicated/shared memory where available;
- storage throughput;
- network throughput;
- thermal state;
- power/energy where available;
- bounded session-local history;
- denominator/provenance/source continuity.

---

# 62. Hardware

Consume Prime hardware truth:

- system/board/firmware;
- CPU;
- RAM;
- PCI;
- GPU/display;
- storage;
- Ethernet/Wi-Fi/Bluetooth where available;
- USB;
- audio/input;
- thermal sensors;
- TPM/Secure Boot;
- virtualization;
- driver binding;
- device assignment/passthrough where known.

Manager does not reverse-parse presentation strings into quantitative authority or independently decide hardware health from external vendor specs.

---

# 63. Storage

Consume Prime Storage Intelligence:

- device/mount topology;
- total/used/free/available/reserved;
- generation/recovery reserve;
- logical/allocated/shared semantics where available;
- throughput/pressure;
- foreign-filesystem state;
- zram/swap backing truth;
- limitations.

---

# 64. Network

PM1 baseline:

- interface identity;
- link/carrier;
- classification;
- throughput;
- packet/error/drop facts where available;
- driver;
- assignment/context;
- limitations.

Raw MAC/IP configuration and ordinary Wi-Fi/IP configuration remain Settings/Shell or later authorized diagnostic projections.

---

# 65. Thermals / Power

Thermals show sensor, source, temperature, status, throttle and thresholds where mechanically known.

Power/Energy initially lives in Overview/Performance/Hardware and shows only supported facts such as source, battery health/charge, measured power or energy.

---

# 66. Services

Show:

- stable service definition;
- definition revision;
- persistence kind;
- activation instances;
- portable lifecycle/native detail;
- activation policy/reason;
- owning component/Provider;
- workload/process relationship;
- restart count with reset epoch;
- last completion/failure;
- restart policy;
- dependencies;
- protection;
- bounded logs.

Actions include start, stop, restart and persistent activation-policy change where supported.

---

# 67. Drivers

Show device, driver identity/version where known, Provider/component owner, trust tier, current binding, health, Developer Mode relationship and limitations.

Driver mutation is not PM1-required.

---

# 68. Prime surface

Show:

- Host ID/lineage;
- current/retained generation summary;
- Core identity;
- HEALTH_PROVING / KNOWN_GOOD;
- capability/Provider graph;
- activation state/health;
- Application Profiles and compatibility/revocation;
- Workload Policies;
- declared/effective enforcement;
- runtime/backend/provider ownership;
- quiescence blockers;
- recovery reserve;
- update/recovery state.

---

# 69. Action / Evidence drawer

Show current-authorized action evidence with action ID, actor/system authority, target Host/domain, target/preconditions, phases, stable result, evidence strength, resulting state and limitations.

Examples include SUCCESS, FAILED, DENIED, ALREADY_SATISFIED, PARTIAL, COMMITTED_EXPECTED_DISCONNECT and UNKNOWN_FINAL_STATE.

---

# 70. PM1 accessibility / operator mechanics

Require:

- keyboard-complete operation;
- visible focus;
- semantic labels;
- DPI/text scaling;
- reduced motion;
- non-color-only status;
- row virtualization;
- stable sorting;
- configurable columns;
- search/filter;
- safe copy handling;
- display pause;
- persistent selection;
- tombstones.

---

# 71. PM1 exit gate

PM1 exits only when:

- all required surfaces use live Prime truth;
- live workload supervision exists;
- renderer cannot bypass broker;
- scoped non-root Manager authorization exists;
- optional capability loss degrades only affected surfaces;
- listed mutations produce typed evidence;
- unsupported Provider actions remain unavailable;
- remote/guest/local resource values remain correctly scoped;
- no required panel is static proof UI;
- Manager satisfies the distress contract without outranking Core/Recovery;
- accessibility/operator-safety requirements pass.

---

# PM1.5 — Adversarial Physical & Contract Proof

## Goal

Prove PM1 on KRATOS and deterministic provider/runtime fixtures under normal, hostile and failure conditions.

No inferred PASS states.

---

# 72. Normal physical proof

Prove:

- Manager admission/Profile/Policy;
- Host/software identity;
- live workload lifecycle and provenance;
- process membership;
- hardware agreement;
- CPU/memory/GPU/storage/network/thermal response where physically available;
- terminate/force-stop/tree/workload stop;
- suspend/resume;
- priority/affinity;
- service lifecycle;
- protected denial;
- effective enforcement readback.

---

# 73. Client-security proof

Attack:

- compromised renderer direct Core IPC;
- same-UID non-Manager impersonation;
- stolen/replayed grant;
- grant from another Manager instance;
- preflight-token replay;
- action-ID/request-digest mismatch;
- spoofed high-risk confirmation target;
- stale grant after suspend/lock/logout;
- privileged cursor replay.

All must deny mechanically.

---

# 74. Provider fixtures

Prove:

- forged/stale Provider fence;
- wrong Provider epoch;
- Provider replacement;
- duplicate action with changed request;
- execution after deadline;
- unauthenticated Provider result;
- Provider restart without action continuity;
- read-only degradation when safe mutation semantics do not exist.

---

# 75. Action lifecycle fault injection

Inject failure:

1. before admission;
2. after admission before durable journal;
3. after durable journal before dispatch;
4. after dispatch before Provider response;
5. after commit before final evidence;
6. after final evidence before client delivery;
7. after Manager closes;
8. during Core restart;
9. across Host reboot where relevant.

Prove no duplicate effect and truthful reconciliation.

---

# 76. Race / concurrency proof

Include:

- PID reuse;
- process `exec()` change;
- credential/ownership change;
- service-definition update;
- placement migration;
- Provider switch;
- fork during tree termination;
- conflicting Manager/Terminal/system-client actions;
- multi-phase restart conflict;
- high reader concurrency.

---

# 77. Stream / parser proof

Include:

- high event rate;
- slow reader;
- duplicate delivery;
- gap/replay/overflow;
- snapshot/cursor expiry;
- leaked subscription cleanup;
- Core/Provider restart;
- unknown event class;
- invalid UTF-8;
- bidi/control strings;
- >2^53 values;
- duplicate keys;
- large nested/cardinality payloads;
- version/enum evolution;
- canonicalization consistency across Rust/native/TS;
- framing/schema fuzzing.

---

# 78. Disclosure proof

Include:

- sensitive fields;
- clipboard;
- stale view;
- grant expiry/revocation;
- lock/logout;
- history/log queries;
- notifications;
- export;
- expired artifacts;
- hidden-object enumeration attempts.

---

# 79. Distress / observer proof

Test:

- CPU saturation;
- memory pressure/OOM competition;
- I/O saturation;
- nearly full/read-only Manager-local storage;
- process churn;
- service crash storm;
- Provider degradation;
- telemetry flood.

Manager sheds optional work before essential inspection/control.

Opening Manager must not unnecessarily wake GPU/VM/runtime/Provider/storage or other dormant optional machinery.

---

# 80. Hotplug / evidence proof

Where physically available, prove USB/network/display/hardware-graph/device-assignment changes live without Manager restart.

Test evidence store full/read-only/corrupt, Host-reboot persistence, rollback reading newer evidence schema, evidence expiry and idempotency tombstone behavior.

---

# 81. Proof classes

Each requirement is one of:

- PHYSICALLY_PROVEN;
- CONTRACT_FIXTURE_PROVEN;
- NOT_APPLICABLE_ON_HOST;
- NOT_YET_PROVEN.

No absence of KRATOS hardware becomes an inferred PASS.

If evidence disproves PM0 semantics, invoke the Contract Amendment Protocol.

---

# PM2 — Deep System Control

## Goal

Reach serious professional system-management depth without weakening Prime boundaries.

---

# 82. Deep process/thread inspection

Where supported:

- process CPU/history;
- thread list and stable thread-instance identity;
- thread CPU;
- open files/deleted-open files;
- memory maps;
- working directory;
- security context;
- sockets/listeners;
- detailed I/O;
- page faults/context switches;
- swap;
- limits;
- OOM history;
- crash/exit reason;
- GPU engines/VRAM;
- process/network attribution.

Sensitive depth remains authorization-gated.

---

# 83. Startup & Background

Add an operational sub-surface for boot/login/event/scheduled/on-demand activation, Workload Policy background permission, startup/resource impact, component owner and change authority.

---

# 84. Deep resource controls

Where Prime has earned the backend:

- CPU weight/quota/cpuset;
- memory/swap;
- process count/runtime duration;
- I/O weight/bandwidth;
- storage quota;
- GPU policy;
- workload network policy.

---

# 85. Deep services/storage/network/hardware

Add service dependency/failure graphs, richer event history and resource attribution.

Use Prime Storage Intelligence for health, SMART/NVMe, wear, ownership and open-deleted storage.

Add network connections/sockets/listeners/policy where authorized; ordinary network configuration stays Settings/Shell.

Add hardware operational facts such as negotiated USB/PCIe link, storage health, firmware, battery cycles, fan state, assignment/passthrough and throttle/constraint where Prime can mechanically support them.

---

# PM3 — Prime Intelligence

## Goal

Make Manager the best local place to understand Prime itself.

---

# 86. Prime-native workload intelligence

Expose application, workload, launch, initiator, Profile, Policy, revocation, effective enforcement, runtime, backend, translation, execution path, Provider, component, generation, compatibility and quiescence.

Profile revocation must identify affected running workloads and resulting enforcement evidence instead of looking like an unexplained crash.

---

# 87. Component ownership

Once Prime P2 exists, distinguish image-owned material from component-owned applications/services/runtimes/Providers/capabilities and show component identity/version/publisher/channel/trust/update authority.

Manager does not become the component transaction engine.

---

# 88. Generation / recovery intelligence

Expose current/retained/STAGED/BOOT_TRY/HEALTH_PROVING/KNOWN_GOOD/rollback/recovery state, update preflight, storage reserve, quiescence blockers and in-flight action blockers.

Generation/recovery mutations become visible only after Prime OS separately earns/proves those capabilities. Manager maturity alone never authorizes an unproven OS action.

Emergency Host recovery outranks Manager-version compatibility.

---

# PM4 — Diagnostics & Incident Analysis

## Goal

Provide serious troubleshooting without giving Manager unrestricted debug/kernel authority.

---

# 89. Host timeline

Combine mechanical events while preserving source, source sequence, Host/Core/Provider epoch, receipt ordering, clock uncertainty and proven causal correlation.

Show explicit discontinuity markers for reboot, Core restart, Provider replacement, generation change, denominator/metric-semantic change.

Distinguish caused-by, mechanically-linked and temporally-correlated.

---

# 90. Diagnostics

Where Prime earns explicit capability:

- process sample;
- thread/stack snapshot;
- wait/blocking analysis;
- scheduler delay;
- process dump;
- bounded Host diagnostic capture;
- hang/crash/performance capture.

Diagnostics declare invasiveness/cost and use preflight for target revision, pause effect, memory/storage and system pressure.

If cleanup fails after a pause/freeze-assisted capture, evidence reports the actual resulting target state.

Raw dumps/memory captures remain sensitive artifacts with explicit authorization/retention/export policy.

---

# 91. Export provenance

Every Manager-built report records Manager revision, Host/generation, source capability/schema/version, observation times, disclosure profile ID/version, withheld fields and relevant artifact digests.

The report is an artifact assembled from Prime truth, not a new machine authority.

---

# PM5 — Remote / Fleet

## Goal

Manage multiple Prime Hosts while preserving local Host sovereignty.

PM5 remains design-only until Prime OS exposes an authenticated remote Host capability interface through the appropriate distributed-host milestone or deliberate amendment.

---

# 92. Remote trust / discovery / principal identity

Each Host remains self-authoritative.

Host ID is identity, not authentication. Remote trust uses approved cryptographic identity with key rotation/revocation/expiry/rebind semantics.

Origins discovery is not authority.

Principal identity is Host-scoped/federated; equal display names across Hosts do not imply one principal.

Target confirmation keeps human label, immutable Host identity/trust state and execution context visible.

---

# 93. Fleet capability and batch semantics

Capability negotiation is per Host.

A fleet action resolves a fixed target-set snapshot/digest before confirmation.

Hosts that are incompatible/offline/denied remain explicit and are not silently removed from the result.

One central confirmation cannot manufacture local authorization on remote Hosts.

Results are per Host and may be PARTIAL.

---

# 94. Remote retry / stale disclosure / time

Remote mutation uses the same action ID/fencing/idempotency/reconciliation rules.

Default offline behavior:

```text
Host unreachable → mutation unavailable
```

No hidden destructive command queue.

Remote stale caches obey the same disclosure expiry/purge rules as local stale mode.

Fleet timelines preserve Host-local ordering and clock-quality metadata rather than inventing one exact global order.

Non-Prime Windows/macOS/cloud/specialist machines remain Providers rather than fake Prime Hosts.

---

# Cross-phase gates

# 95. Authority gate

No Manager feature creates competing Host authority.

# 96. Identity gate

Every mutable target has Core-owned or Core-verified Provider-supplied reuse-safe identity/fencing. Otherwise mutation is unavailable.

# 97. Truth gate

Observed, Provider-attested, derived, estimated, stale, shared, unattributed, unsupported and unavailable remain distinct.

# 98. Disclosure gate

Visible does not automatically mean persistable, copyable, exportable or remotely shareable.

# 99. Resource gate

Measure Manager idle CPU/RAM, broker/renderer cost, baseline/detail telemetry, event processing, history, reconnect and diagnostic overhead.

# 100. Distress gate

Manager satisfies PM0-defined survival properties under pressure without outranking Core/Recovery.

# 101. Observer gate

Manager does not materially activate dormant machinery merely by observing it.

# 102. Compatibility gate

Every release records supported Core envelope, transport, capability and schema ranges.

# 103. Security gate

Manager uses least authority, has no generic root, mechanically binds client identity, keeps grants out of renderer, separates renderer from Core IPC, applies disclosure to live/history/export data and prevents secondary-channel leakage.

# 104. Proof gate

No inferred PASS. Architecture contradiction triggers the Contract Amendment Protocol.

# 105. Host-survival gate

Manager failure may fail Manager product/release quality but does not automatically make Prime unable to boot/recover unless a deliberate generation-health policy explicitly says otherwise.

# 106. Emergency recovery exception

If ordinary Manager evidence storage/auth path is unhealthy, Manager may fail closed for high-impact actions. A separately designed emergency Recovery/power authority remains outside Manager and may use its own minimal emergency semantics. Manager never silently downgrades itself into that authority.

---

# Release model

# 107. First delivery

Preserve already-proven Prime P1 unless deliberately reopened. Manager enters a later explicitly authorized generation.

# 108. Manager release identity

Record exact source revision, artifact digest, Application Profile revision, Workload Policy revision and compatible Core/transport/capability/schema ranges.

# 109. P2+ component delivery

After Prime component/package authority exists, Manager normally evolves as a signed first-party component. A Manager package must not patch image-owned Prime Core merely to obtain a missing capability.

# 110. Cross-roadmap cleanup

Prime Terminal also contains sequencing language around the first daily-usable Prime installation. That wording should be reconciled separately with frozen Prime OS P1 authority. It does not authorize Manager or Terminal to silently expand P1.

---

# First production baseline

Prime Manager reaches its first production baseline only when:

- this roadmap is frozen;
- PM0 contracts are frozen;
- Manager-required Prime OS authority exists;
- scoped non-root authorization exists;
- permission/disclosure mediation exists;
- live workload supervision exists;
- live hardware/capability refresh exists;
- PM1 is complete;
- PM1.5 adversarial physical + contract proof passes;
- any falsified contract has been amended and re-proven;
- exact Manager artifact/Profile/Policy are reproducible;
- compatibility matrix is recorded;
- no listed mutation can falsely report success;
- no Provider without adequate fencing exposes unsafe mutation;
- action/evidence reconciliation survives required failure boundaries;
- stale/sensitive data cannot outlive authorization;
- Manager failure does not threaten Host survival.

---

# Engineering execution sequence

```text
1. Freeze this Prime Manager roadmap.

2. Prime OS / prime-contracts:
   define the reusable PM0 contracts.

3. Add Manager-required Prime authority:
   - scoped non-root system-app authorization
   - permission/disclosure mediation
   - live workload registry
   - asynchronous Prime Exec supervision
   - effective enforcement readback
   - dynamic hardware/capability state
   - observation transport
   - Host action evidence/journal

4. Freeze/version the Prime OS contract amendments.

5. Build deterministic fixtures + fake/replay Core.

6. Prove contract/wire/security/provider semantics.

7. Build minimal trusted Manager broker.

8. Prove renderer cannot bypass broker.

9. Build PM1 renderer/UI.

10. Internal architecture/security review.

11. Run PM1.5 KRATOS physical + contract/adversarial campaign.

12. If evidence disproves a frozen contract:
      STOP
      amend
      review
      freeze
      re-prove.

13. Freeze first production Manager baseline.

14. PM2 → PM5 only as corresponding Prime OS capabilities are earned.
```

---

# Independent review mandate

An independent reviewer should attempt to falsify, not expand by default:

1. Host authority ownership;
2. renderer/broker isolation;
3. client identity binding;
4. principal/target authorization;
5. process/workload/service identity;
6. nested execution identity;
7. Provider fencing;
8. Provider idempotency/reconciliation;
9. Host action lifecycle;
10. evidence durability/integrity/privacy;
11. expected-disconnect behavior;
12. disclosure lifecycle;
13. cursor/subscription security;
14. resource accounting;
15. telemetry provenance/denominators;
16. quiescence completeness;
17. Core/Provider restart semantics;
18. schema/version migration;
19. update/rollback compatibility;
20. fleet authority isolation.

Verdict should be `PASS`, `NEEDS WORK` with exact deficiency/consequence/minimum correction, or `BLOCK` with the exact contradiction and evidence.

---

# Permanent final rules

> **Prime Manager never becomes Host authority.**

> **Prime workloads are the primary managed abstraction; processes remain available as mechanical truth.**

> **Execution can be nested and Provider-owned; mutation guarantees follow the authoritative layer, not Linux assumptions.**

> **No strong target identity/fence means no mutation.**

> **The renderer is not trusted with Core IPC, authorization grants or preflight commit tokens.**

> **Authorization is Prime-owned and exact-target bound; confirmation dialogs are UX, not security.**

> **Every Host action has an identity before first submission.**

> **Unknown action outcome is a reconciliation requirement, not permission to retry.**

> **Required action evidence is durable before destructive dispatch.**

> **Persistent machine evidence is never Manager cache.**

> **Visible sensitive data is not automatically persistent, copyable or exportable.**

> **Remote/guest resource values never silently enter local Host totals.**

> **Percentages always identify their denominator.**

> **Declared policy, effective enforcement and external constraints are different truths.**

> **Persistent Profile/Policy/service-definition changes create/version authority rather than rewriting history.**

> **Manager remains useful under machine pressure without becoming more critical than Prime itself.**

> **A frozen contract disproven by evidence is amended and re-proven; Manager never privately patches around it.**

> **When Prime does not know, Manager reports UNKNOWN.**

---

# Current disposition

**Roadmap architecture review:** SATURATED.  
**PM0 implementation:** NOT STARTED.  
**Next engineering frontier:** Prime OS reusable PM0 contracts and Manager-required authorization/workload/observation foundations.  
**Documentation rule:** update this roadmap when authority changes; do not create competing policy copies elsewhere.
