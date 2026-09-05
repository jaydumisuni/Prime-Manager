# Prime Manager — Roadmap

**Repository:** `jaydumisuni/Prime-Manager`
**Product:** Prime Manager
**Authority:** THETECHGUY DIGITAL SOLUTIONS / Prime OS architecture
**Roadmap baseline:** 2026-09-05
**Status:** AUTHORITATIVE INITIAL ROADMAP

## Purpose

Prime Manager is Prime OS's first-party system-management application. Its purpose is not merely to display graphs: it is the operator surface for understanding and controlling the local Prime Host.

Prime Manager must make it possible to answer, from one native application:

- what hardware is this Host running on;
- what is consuming CPU, memory, storage, I/O, GPU and network resources;
- which processes and services are running and why;
- which workloads are Prime-managed and which are ordinary Host processes;
- what can be terminated, suspended, restarted, reprioritized or constrained;
- what state the current Prime generation, recovery path and Host capabilities are in;
- what action Prime Core accepted, rejected or failed, with evidence rather than optimistic UI state.

## Permanent architecture boundary

Prime Manager is **not** a second operating-system authority.

- `Prime-OS` / `primed` owns Host identity, hardware graph, process/service authority, Workload Policy, resource enforcement, power/update/recovery authority, capability negotiation and privileged mutations.
- Prime Manager consumes versioned Prime capabilities and submits typed requests to Prime Core.
- Prime Manager must not bypass Core by directly mutating `/proc`, `/sys`, cgroups, systemd, device nodes or privileged kernel interfaces.
- Read-only local rendering/cache state may live in Prime Manager; Host truth remains owned by Prime Core.
- Every privileged action must resolve to explicit evidence: accepted, rejected, failed, timed out or unavailable.
- Critical Prime authorities are protected by policy and cannot be casually terminated from the UI.

## Product shape

The target application has these primary surfaces:

1. **Overview** — current Host health and the highest-value live signals.
2. **Processes** — process tree, resource use and process controls.
3. **Performance** — CPU, memory, GPU, storage, network and historical telemetry.
4. **Hardware** — Prime hardware graph rendered as an understandable system report.
5. **Storage** — devices, mounts, pressure, generation/recovery reserve and I/O.
6. **Network** — links, throughput and later bounded network controls.
7. **Thermals** — temperatures, power/thermal limits and trends.
8. **Services** — lifecycle, dependencies, restart history and logs.
9. **Drivers** — driver binding, trust tier, health and device relationship.
10. **Prime** — Host ID, generation state, `KNOWN_GOOD`, Prime Exec workloads, Application Profiles, capability health, update/recovery state and policy ownership.

Prime Settings remains a separate, simpler configuration product surface. Prime Manager is the deep inspection and control surface.

---

# PM0 — Authority & Contracts

**Goal:** freeze the interfaces Prime Manager depends on before UI implementation outruns OS authority.

## Deliverables

- Prime Process Inventory v1.
- Prime Process Control v1.
- Prime Service Inventory v1.
- Prime Service Control v1.
- Prime Resource Control v1.
- Prime Manager Telemetry v1.
- Prime Hardware projection compatibility contract using the existing Prime hardware graph.
- Action Evidence v1 for all mutations.
- protected-authority classification for Prime Core, compositor, Shell, recovery/update authorities and other boot-critical services.
- authorization rules for normal-user, elevated-owner and policy-denied mutations.
- stable identifiers for processes, process trees, services and Prime-managed workloads that do not rely on display names.
- explicit stale-data and race semantics: a process or service disappearing between observation and mutation is a truthful result, not an invented success.

## Required mutation vocabulary

At minimum the contracts must represent:

- terminate process;
- force-kill process;
- terminate process tree;
- suspend/resume process or workload;
- change priority / CPU weight;
- change CPU affinity where supported;
- apply bounded CPU, memory and I/O limits where authority exists;
- start service;
- stop service;
- restart service;
- enable/disable service where Prime policy permits it.

## Exit gate

PM0 exits only when Prime OS and Prime Manager agree on versioned request/response shapes, protection semantics, authorization behavior, evidence semantics and compatibility/version negotiation. No UI button may be specified without a corresponding truthful capability state.

---

# PM1 — Operator First Light

**Goal:** deliver the first genuinely useful Prime Manager and include it in the first daily-usable Prime image.

## Required surfaces

### Overview

- Host model and Prime Host identity summary.
- current CPU, memory, storage, network and thermal headline values.
- current generation state and health summary.
- degraded/unavailable capabilities shown explicitly.

### Processes

- live process table and process tree.
- PID plus stable Prime workload identity when available.
- executable, command line, owner and parent/children.
- CPU and memory usage.
- I/O usage where available.
- end task.
- force kill.
- terminate tree.
- suspend/resume.
- change priority.
- CPU affinity where the Host backend supports it.
- inspect/open executable location through a safe Prime capability rather than arbitrary privileged filesystem access.

### Performance

- total CPU and per-logical-CPU view.
- memory used/available/pressure.
- storage throughput headline.
- network throughput headline.
- thermal headline.
- bounded refresh rates that do not make Prime Manager itself a material workload.

### Hardware

Consume Prime Core's existing `prime.hardware-graph.v1` / `/v1/hardware` truth and render at minimum:

- system/board/firmware;
- CPU and architecture;
- RAM;
- GPU/display connectors;
- storage devices;
- Ethernet/Wi-Fi;
- USB topology/devices;
- audio devices;
- input devices;
- thermal sensors;
- TPM/Secure Boot where available;
- virtualization/KVM capability;
- bound driver information where the graph supplies it.

Prime Manager does not independently rediscover hardware and then disagree with Prime Core.

### Services

- service name/identity, state and substate.
- start, stop and restart.
- enable/disable where authorized.
- uptime/restart count where available.
- recent bounded logs.
- protected Prime services clearly identified.

### Prime

- Host ID.
- current generation ID and state.
- `HEALTH_PROVING` / `KNOWN_GOOD` truth.
- capability health.
- Prime-managed workloads and their Application Profiles.
- Prime Exec backend/runtime family.
- Workload Policy identity.
- recovery/update reserve and generation storage headline.

## Protection requirements

- Prime Manager itself cannot silently weaken Workload Policy.
- boot-critical Prime authorities require stronger policy than ordinary user processes.
- an action that would destroy Core authority or strand the active system must be blocked or require an explicitly higher authorization path defined by Prime OS.
- UI must never render a protected action as if it succeeded when Core rejected it.

## Exit gate

PM1 exits when all required surfaces are backed by live Prime capabilities, all listed controls return truthful evidence, visual behavior matches Prime's approved material language, and no required card is a static proof placeholder.

---

# PM1.5 — Physical Management Proof

**Goal:** prove PM1 on the real KRATOS proof Host before treating Prime Manager as production baseline.

## KRATOS proof campaign

Prove, with captured evidence:

- Prime Manager launches as an admitted Prime application.
- live hardware view matches Prime Core's hardware graph.
- CPU/memory telemetry changes under a bounded test workload.
- a disposable test process can be terminated normally.
- a disposable test process can be force-killed.
- a test process tree can be terminated without killing unrelated processes.
- a disposable workload can be suspended and resumed.
- priority can be changed and mechanically re-read.
- CPU affinity can be changed and mechanically re-read where the backend supports it.
- a disposable service can be started, stopped and restarted.
- service failure and restart count are reflected truthfully.
- a protected Prime authority cannot be casually killed or disabled.
- stale PID/service races return an explicit non-success result.
- Prime Manager survives a denied mutation and continues refreshing state.
- Prime Manager itself does not materially destabilize idle CPU/memory behavior.

## Exit gate

A signed/hashed evidence bundle must bind the Prime Manager revision, Prime OS generation, capability-interface versions and KRATOS Host evidence. No inferred PASS states.

---

# PM2 — Deep System Control

**Goal:** approach and exceed the useful depth of mature Task Manager / Activity Monitor tools while retaining Prime authority boundaries.

## Performance depth

- per-core CPU history.
- process CPU history.
- memory composition, pressure and reclaimability.
- GPU engine/utilization telemetry where supported.
- disk throughput, queueing and latency.
- process I/O breakdown.
- network interface and process throughput where authority exists.
- thermal history and throttling reason where mechanically available.
- battery/power telemetry on applicable Hosts.

## Control depth

- Workload Policy-aware CPU quota/weight changes.
- memory limits.
- I/O priority and bandwidth limits where supported.
- richer affinity/topology controls.
- service dependency graph and failure propagation.
- bounded service logs and event history.
- network mutation once Prime OS earns a bounded network-control backend.
- audio mutation once Prime OS earns a bounded mixer/control backend.

## Storage depth

Integrate Prime Storage Intelligence rather than inventing a competing scanner:

- physical device/mount topology;
- capacity and pressure;
- generation/recovery reserve;
- process/workload I/O ownership where available;
- storage-health facts exposed by Prime capabilities;
- safe foreign-filesystem state.

## Exit gate

All controls are capability-gated and policy-aware; unsupported kernel/driver paths remain explicitly unavailable rather than emulated through distro-specific shortcuts.

---

# PM3 — Prime Intelligence

**Goal:** make Prime Manager the best place to understand Prime itself, not merely Linux processes underneath it.

## Required Prime-native views

- Host identity and hardware-graph revision history.
- current and retained generations.
- `BOOT_TRY`, `HEALTH_PROVING`, `KNOWN_GOOD` and rollback state.
- recovery readiness.
- update controller state.
- capability inventory and health.
- Prime Exec workloads grouped by runtime family and backend.
- Application Profile revision and compatibility state.
- Workload Policy revision and effective resource policy.
- Provider/runtime ownership.
- component/package ownership once P2 exists.
- recovery reserve and update-space preflight state.
- driver trust tier and Developer Mode relationships.

## Exit gate

An operator can explain why a workload is running, which backend owns it, which policy constrains it, which generation launched it, and whether the Host can safely update/rollback without leaving Prime Manager.

---

# PM4 — Advanced Operator

**Goal:** turn Prime Manager into a serious troubleshooting and diagnostics workstation.

Planned capabilities:

- configurable graph/history windows.
- process/service event timeline.
- startup/boot impact analysis.
- process snapshots and before/after comparisons.
- workload/resource comparison.
- diagnostics bundles with redaction policy.
- exportable system report built from Prime-owned sanitized facts.
- dependency and failure-correlation views.
- storage/network/thermal incident correlation.
- evidence links into Prime logs without exposing unrelated secrets.

Advanced diagnostics remain observational unless a separately authorized control capability exists.

## Exit gate

PM4 exits when Prime Manager can capture, correlate and export a bounded troubleshooting record without bypassing redaction policy, and every diagnostic view can identify the Prime capability/evidence source behind its conclusions.

---

# PM5 — Remote / Fleet Management

**Goal:** extend Prime Manager to authorized multi-Host operations without moving Host authority out of each Prime Core.

Potential integrations:

- Origins Host/Node projection.
- Hunter-assisted diagnostics.
- Oracle authorized remote transport.
- fleet health summaries.
- remote process/service actions with explicit target Host and authorization.
- evidence/audit trails for remote mutations.

Each Host remains self-authoritative. A remote manager is a client of that Host's Prime capabilities, never a global root authority.

## Exit gate

PM5 exits only when remote reads and mutations preserve explicit Host targeting, local Prime authorization, audit evidence, disconnect/retry truth and fail-closed behavior. Loss of the remote coordinator must not remove local Host management or authority.

---

# Release and Prime OS integration

## P1

Prime OS may pin an exact reviewed Prime Manager artifact into the immutable P1 image. The image must record the application revision/digest and matching Application Profile revision.

## P2+

Once Prime's component/package mechanism exists, Prime Manager should normally evolve as an independently delivered first-party component while Prime OS continues to define the minimum compatible capability contracts.

A Prime Manager update must not require live mutation of image-owned Prime Core merely to add UI behavior.

# Non-goals

Prime Manager is not:

- a replacement for Prime Core;
- an alternative init/service manager;
- a direct `/proc`/`sysfs` mutation frontend;
- an excuse to bypass Workload Policy;
- a global fleet authority;
- a clone of Windows Task Manager, macOS Activity Monitor or TMOG's visual design.

Those products may inform functional expectations. Prime Manager owns its own Prime-native architecture and visual language.

# Completion definition

Prime Manager reaches its first production baseline only when PM0, PM1 and PM1.5 are complete on an installed Prime generation and the application is bound to reproducible release evidence.

Subsequent phases deepen capability without changing the permanent rule:

> Prime Manager observes and controls the Host through Prime Core; it never becomes the Host authority itself.
