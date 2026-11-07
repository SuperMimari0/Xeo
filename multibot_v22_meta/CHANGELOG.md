# Changelog

## 2.2.0

- Added loopback-only Provider SDK with `ProviderBackendBase`, `ProviderSdkServer` and simulator reference backend.
- Added backward-compatible protocol negotiation: provider protocol v1 and v2 are both accepted, with highest-common-version selection for v2.2 SDK servers.
- Added read-only provider conformance suite by default, with opt-in action/idempotency checks only when explicitly advertised.
- Added provider diagnostics snapshot showing negotiated protocol, supported versions and SDK compatibility.
- Added `provider-conformance` and `provider-sdk-contract` CLI commands and Provider SDK GUI controls.
- Added `examples/sdk_provider_server.py` and `docs/PROVIDER_SDK.md`.
- Upgraded profile schema to v22 while retaining v2→v21 migration compatibility.
- External provider boundary remains generic and contains no official-client attachment, memory access, injection, packet manipulation or anti-cheat bypass implementation.

## 2.1.0

- Added bounded transient provider retry/backoff and temporary circuit breaker.
- Added provider heartbeat/probe manager and resilience telemetry.
- Added optional idempotent action request IDs; demo bridge deduplicates repeated actions.
- Added capability fallback for optional reads and health-unsupported providers.
- Added stricter provider schema validation and configurable entity limits.
- Added provider-probe CLI command and v2.1 provider resilience GUI metrics.
- Profile schema upgraded to v21 with v2→v20 migration compatibility.

## 2.0.0

- Added generic External Provider Architecture with startup-selectable simulator/external backends.
- Added loopback-only newline-delimited JSON provider transport with timeout and response-size limits.
- Added protocol capability negotiation, provider health reporting, and cached client discovery.
- Added external state provider and action adapter while preserving Action Queue → State Verifier verification.
- Added secret-safe provider configuration: token values stay in environment variables and are not persisted.
- Added simulator-backed in-memory mock bridge and real loopback TCP demo server for integration development.
- Added Provider v2.0 GUI workspace and provider-status/provider-contract CLI commands.
- Added provider configuration semantic audit and startup self-test coverage.
- Upgraded profile schema to v20 with v2→v19 migration compatibility.
- Expanded regression suite to 232 tests with 89.04% measured coverage.
- No official-client attachment, memory access, injection, packet manipulation or anti-cheat bypass is implemented.

## 1.9.0

- Added Windows Build Doctor and explicit native toolchain/source diagnostics.
- Added structural portable EXE and installer verification with PE magic, bundle version and SHA-256 facts.
- Added silent clean-install → installed-smoke → uninstall validation script.
- Added reinstall / optional real previous-version upgrade smoke validation.
- Added a one-command `windows_release.ps1` native release lane and release JSON verifier.
- Added Windows Release Pipeline status separating 100% source automation from native artifact completion.
- Added frozen `--installed-smoke` writable-state validation under per-user runtime storage.
- Expanded GitHub Windows workflow to perform build, install, upgrade/reinstall, uninstall and report upload.
- Expanded Packaging v1.9 GUI and headless commands: build-doctor, artifact-verify, install-lifecycle and windows-release-status.
- Upgraded profile schema to v19 with v2→v18 migration compatibility.
- Expanded regression suite to 220 tests with 89.07% measured coverage.
- Native Windows artifacts are intentionally reported as pending in this Linux-built source release.

## 1.7.0

- Added persisted deterministic scenario corpus with schema validation and SHA-256 fingerprinting.
- Added normalized failure-signature clustering for regression blockers.
- Added persisted deterministic named seed registry with stable child-seed derivation.
- Added bounded snapshot-retention policy for replay, scenario snapshots, benchmark history and timeline events.
- Added benchmark p50/p90/p95/p99 distribution analysis.
- Added release delta reporting against the retained v1.6 immutable manifest.
- Expanded strict regression/release gates with corpus, seed and retention checks.
- Added Corpus v1.7 GUI workspace and new headless commands.
- Upgraded profile schema to v17 with v2→v16 migration compatibility.
- Expanded regression suite to 197 tests and measured 89.57% coverage.

## 1.6.0

- Added isolated bounded fault-injection matrix for simulator recovery boundaries.
- Added read-only safe session checkpoint structural diff.
- Added long-run memory, queue, failure and invariant stability monitoring.
- Added dependency-cycle detection over configuration graph edges.
- Added stable source-tree release reproducibility fingerprints.
- Added automatic severity-ordered regression triage.
- Expanded strict regression gate with v1.6 stability layers.
- Added Stability v1.6 GUI workspace and new headless commands.
- Upgraded profile schema to v16 with v2→v15 migration compatibility.
- Expanded regression suite to 179 tests with 89.00% measured coverage.

## 1.5.0

- Added read-only runtime state invariants for character, inventory, target and queue consistency.
- Added deterministic bounded scenario fuzzing in isolated simulator instances.
- Added bounded soak tests with periodic invariant sampling.
- Added portable configuration dependency graph validation.
- Added secret-free SHA-256 release attestation records.
- Added strict regression gate combining invariants, dependencies, fuzzing and soak validation.
- Added Regression v1.5 GUI workspace and new headless commands.
- Upgraded profile schema to v15 with v2→v14 migration compatibility.
- Expanded diagnostics, startup self-test, release report and release validation for v1.5.
- Expanded regression suite to 167 tests with 89.46% measured coverage.

## 1.4.0

- Added bounded resource budgets for queue/history/timeline/replay/session structures.
- Added isolated local-simulator resilience probes for low HP, target exhaustion, client toggling, and unknown action boundaries.
- Added deterministic replay diff data with path/category summaries.
- Added profile migration compatibility audit from v2 through v14.
- Added reproducible release provenance with SHA-256 source hashes and safety-boundary metadata.
- Added optional deep release gate that includes resilience probes.
- Added Resilience v1.4 GUI workspace and new headless commands.
- Upgraded profile schema to v14; v2→v13 migration remains supported.
- Expanded regression suite to 153 tests and raised coverage to 89.39%.

## 1.3.0
- Upgraded portable profile schema to v13 with v2-v12 migration compatibility.
- Added canonical deterministic simulator state hashing and repeated-run determinism probes.
- Added persisted configuration drift baselines with semantic normalization for empty client-scoped containers.
- Added scenario benchmark baselines and regression comparison thresholds.
- Added aggregated 0-100 runtime health scoring with bounded trend history.
- Added read-only tuning advisor; recommendations never mutate runtime settings.
- Added v1.3 release assurance layer combining config drift, health, determinism and benchmark baseline checks.
- Added Assurance v1.3 GUI controls and headless CLI commands for baselines, drift, determinism, health and tuning advice.
- Extended startup self-test, diagnostics, release report and release gate with v1.3 assurance outputs.
- Increased measured test coverage to 89.27%.
- Expanded regression suite to 131 tests.

## 1.2.0
- Upgraded portable profile schema to v12 with v2-v11 migration compatibility.
- Added configurable performance budgets and baseline regression checks.
- Added semantic configuration audit rules beyond basic schema validation.
- Added read-only safe session restore preview with zero action replay.
- Added dashboard alarm thresholds for runtime, queue and profiler health.
- Added aggregated release quality gate combining startup, schema, audit, coverage, performance and alerts.
- Added Quality v1.2 GUI controls and quality-focused headless CLI commands.
- Expanded diagnostics and release reports with v1.2 quality-gate outputs.
- Increased measured test coverage to 88.03%.
- Expanded regression suite to 115 tests.

## 1.1.0
- Upgraded portable profile schema to v11 with v2-v10 migration compatibility.
- Added phase-level runtime performance profiler.
- Added real coverage.py test coverage reporting and CLI command.
- Added bounded persistent session lifecycle history.
- Added checksum-verified configuration backups with guarded restore.
- Added read-only operations dashboard aggregation.
- Added Operations v1.1 GUI tab and profiler timing in the dashboard.
- Added profile/dashboard/coverage/backup/session-history headless CLI commands.
- Extended diagnostics and release reports with v1.1 operational telemetry.
- Expanded regression suite to 98 tests.

## 1.0.0
- Added profile schema v10 validation and legacy upgrade helper.
- Added atomic crash-aware session checkpoints and clean/unclean shutdown detection.
- Added safe session restore that never replays queued actions.
- Added static extension registry without dynamic filesystem plugin loading.
- Added startup self-test and release readiness report.
- Added headless CLI for self-test, simulation, benchmarks, diagnostics, and release reports.
- Added System v1.0 GUI tab for session/schema/extension controls.
- Added package metadata and console entry point in pyproject.toml.
- Retained v2-v9 profile migration compatibility.
- Expanded regression suite to 86 tests.

## 0.9.0
- Added bounded Event Timeline with level/source/client/text filtering and tick association.
- Added side-effect-free Policy Sandbox for module eligibility and priority ordering previews.
- Added Workflow Health Analyzer with scoring, grades, and static issue detection.
- Added isolated Scenario Benchmark Manager and benchmark history.
- Added portable JSON configuration packages with deterministic SHA-256 checksums and import/export.
- Added Release Validation Manager for required files, version consistency, and integrity verification.
- Added Timeline & Sandbox and Bench & Release UI tabs.
- Added v0.9 profile schema with v0.8 migration compatibility.
- Expanded diagnostics export with timeline, workflow health, benchmarks, and release validation.
- Expanded regression suite to 76 tests.

## 0.8.0
- Added explicit workflow revision capture, comparison and rollback.
- Added persistent configuration change history.
- Added side-effect-free rule simulator for metric rules and condition previews.
- Added simulator snapshot capture and state diff engine.
- Added rolling performance trend analysis.
- Added recovery policy validation, backoff preview and editor controls.
- Added SHA-256 project integrity report and verification support.
- Added Versions & Rules and Diff & Integrity UI tabs.
- Added v0.8 profile persistence and v0.7 migration compatibility.
- Expanded diagnostics export with revisions, changes, diffs, trends and integrity summary.
- Expanded regression suite to 66 tests.

## 0.7.0
- Added workflow preset library and preset-to-workflow cloning.
- Added ALL/ANY condition chains for multi-condition automation rules.
- Added group behavior profiles combining roles, modules and formation configuration.
- Added read-only runtime replay frames with action deltas and character snapshots.
- Added character profile comparison/diff engine.
- Added configurable recovery policies with per-source thresholds and bounded cooldown backoff.
- Added extended performance summaries for dashboard/diagnostics.
- Added Presets & Chains, Group Profiles, and Replay & Recovery UI tabs.
- Added v0.7 profile persistence and v0.6 migration compatibility.
- Expanded diagnostics export with v0.7 managers and replay frames.
- Expanded regression suite to 55 tests.

## 0.6.0
- Added editable Workflow Manager with add/remove/reorder node operations.
- Added Workflow Editor UI and workflow-to-task-chain execution bridge.
- Added generic metric/operator Rule Builder and workflow rule actions.
- Added Group Scheduler for named character groups.
- Added leader/follower coordination with line and column formations.
- Added rolling runtime metrics and Dashboard UI.
- Added persisted Saved Scenario Library and Saved Scenarios UI.
- Added Group Control UI for formation coordination and group scheduling.
- Added v0.6 profile persistence and v0.5 migration compatibility.
- Expanded diagnostics export with workflows, group scheduler, coordination, metrics and saved scenarios.
- Expanded regression suite to 45 tests.

## 0.5.0
- Added deterministic one-shot and recurring tick scheduler.
- Added HP, kill-count and inventory-driven conditional rules.
- Added character roles: custom, farmer, collector, survivor and scout.
- Added reusable built-in and user-created profile templates.
- Added advanced loot ordering with priority VNUMs and inventory caps.
- Added runtime warning/error issue registry with acknowledgement controls.
- Added built-in simulator scenario runner.
- Added Scheduler, Conditions, Runtime Issues and Scenarios UI tabs.
- Added v0.5 profile persistence for roles, templates, schedules and conditions.
- Expanded diagnostics export with v0.5 manager state and scenario history.
- Expanded regression suite to 35 tests.

## 0.4.0
- Added task-chain engine with move_to, wait, ensure_hp, and hunt_kills steps.
- Added character groups and group-wide module activation.
- Added character profile copying.
- Added per-character module priority policy.
- Added Auto Loot module and simulator world drops.
- Added loot whitelist, blacklist, distance, and minimum-count rules.
- Added verified pickup_loot action and inventory mutation.
- Added persistent in-memory Action History.
- Added Loot Rules, Task Chains, and Action History UI tabs.
- Added v0.4 profile persistence and migration compatibility.
- Expanded diagnostics export with priorities, groups, rules, chains, loot and action history.
- Expanded regression suite to 23 tests.

## 0.3.0
- Added independent per-character module profiles and settings.
- Added Task State Machine and target strategies.
- Added inventory filters, diagnostics export, and recovery circuit breaker.

## 0.2.0
- Added client/character managers, module manager, priority queue, state verifier, movement and profiles.