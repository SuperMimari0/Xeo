# MultiBot Safe v2.2

Multi-client automation architecture for **authorized simulator/test integrations**. v2.2 hardens the generic External Provider boundary introduced in v2.0 with bounded retries, heartbeat monitoring, circuit breaking, schema limits, capability fallback and idempotent action request IDs.

The project does **not** contain official Gameforge-client attachment, memory scanning/writing, code/DLL injection, packet manipulation, anti-cheat bypass, or Cheat Engine integration.

## v2.2 focus: Provider SDK & Compatibility

```text
MultiBot Safe v2.2
├─ GUI / Headless CLI
├─ Decision Engine / Action Queue / State Verifier
├─ Provider Runtime
│  ├─ SimulatorProvider
│  └─ ExternalProvider
│     ├─ loopback JSON transport
│     ├─ protocol v1/v2 negotiation
│     ├─ bounded retry / circuit / heartbeat
│     └─ idempotent action IDs
├─ Provider SDK
│  ├─ ProviderBackendBase
│  ├─ ProviderSdkServer
│  ├─ SimulatorBackend reference
│  └─ read-only conformance suite
├─ Provider diagnostics / compatibility score
└─ Windows EXE / installer automation
```

MultiBot still does not know how an external provider obtains data. It only consumes normalized state/action data through the documented local contract.

## Added in v2.2

- Loopback-only Provider SDK for authorized simulator/test integrations.
- `ProviderBackendBase` implementation surface and `ProviderSdkServer`.
- Reference `SimulatorBackend` plus `examples/sdk_provider_server.py`.
- Provider protocol v2 with **backward compatibility for v1 providers**.
- Highest-common-version negotiation using `supported_protocol_versions`.
- Read-only provider conformance checks by default.
- Optional action/idempotency conformance only when `conformance_actions` is advertised.
- Provider diagnostics with negotiated version and SDK/legacy visibility.
- `provider-conformance` and `provider-sdk-contract` CLI commands.
- Provider SDK v2.2 GUI controls.
- Profile schema upgraded to **v22**, retaining v2→v21 migration support.

## Current quality status

- Tests: **248 / 248 passing**
- Coverage: **88.38%** (5669 / 6414 statements, app/tests omitted by the release coverage lane)
- Provider SDK real loopback TCP roundtrip: PASS
- Read-only provider conformance: **100/100** on the SDK reference backend
- Protocol negotiation: v1 legacy + v2 current PASS
- Provider retry/circuit and action idempotency tests: PASS
- Simulator and external-SDK runtimes share the same Action Queue / State Verifier pipeline.
- Windows source automation is installer-ready; native v2.2 artifacts are produced and lifecycle-tested on a Windows runner.

## Run from source

```bash
pip install -r requirements.txt
python main.py
```

The GUI requires PySide6. Headless provider/quality commands do not require the GUI.

## Safe provider demo

Terminal 1:

```bash
python examples/sdk_provider_server.py --port 8765 --clients 2
```

Terminal 2:

```bash
python -m multibot --provider external --provider-port 8765 provider-status
python -m multibot --provider external --provider-port 8765 provider-probe --checks 5
python -m multibot --provider external --provider-port 8765 provider-conformance
```

The demo provider is backed **only** by the bundled local simulator.

See `docs/PROVIDER_PROTOCOL.md` for the wire contract and `docs/PROVIDER_SDK.md` for the SDK.

## Provider resilience configuration

CLI flags:

```bash
python -m multibot \
  --provider external \
  --provider-host 127.0.0.1 \
  --provider-port 8765 \
  --provider-timeout-ms 1500 \
  --provider-retries 1 \
  --provider-backoff-ms 100 \
  --provider-failure-threshold 3 \
  --provider-circuit-cooldown-ms 2000 \
  --provider-max-entities 512 \
  provider-status
```

Equivalent environment settings include:

```text
MULTIBOT_PROVIDER_MODE
MULTIBOT_PROVIDER_HOST
MULTIBOT_PROVIDER_PORT
MULTIBOT_PROVIDER_TIMEOUT_MS
MULTIBOT_PROVIDER_MAX_RETRIES
MULTIBOT_PROVIDER_BACKOFF_MS
MULTIBOT_PROVIDER_MAX_BACKOFF_MS
MULTIBOT_PROVIDER_FAILURE_THRESHOLD
MULTIBOT_PROVIDER_CIRCUIT_COOLDOWN_MS
MULTIBOT_PROVIDER_HEARTBEAT_INTERVAL_MS
MULTIBOT_PROVIDER_MAX_ENTITIES
MULTIBOT_PROVIDER_TOKEN_ENV
```

The token **value** is read from the environment variable named by `token_env` and is never persisted in the profile.

## Windows EXE / installer

On Windows x64 with the build dependencies installed:

```powershell
powershell -ExecutionPolicy Bypass -File packaging\windows_release.ps1
```

The release lane performs Build Doctor, tests, PyInstaller build, portable smoke, Inno Setup build, silent installation, installed smoke, upgrade/reinstall validation and uninstall.

See `packaging/README_WINDOWS_BUILD.md` for details.

## Quality gates

```bash
python -m multibot self-test --skip-integrity
python -m multibot config-audit
python -m multibot provider-probe --checks 3
python -m multibot release-gate --minimum-coverage 80 --deep --strict
```

## Safety boundary

v2.2 provides a **generic provider interface and SDK only**. It does not implement or document methods for bypassing protections or attaching to the official Gameforge client. `live_provider_stub.py` remains disabled.

## Release files

- `reports/coverage_summary_v2.2.json`
- `reports/release_provenance_v2.2.json`
- `reports/release_attestation_v2.2.json`
- `reports/release_delta_v2.2.json`
- `reports/package_manifest_v2.2.json`
- `reports/release_summary_v2.2.json`
- `reports/smoke_summary_v2.2.json`
- `reports/windows_release_source_v2.2.json`
- v2.0 release reports retained as comparison/history
- `integrity_manifest.json`

Mutable runtime data (`runtime/`, `backups/`, `exports/`, caches) is excluded from the immutable SHA-256 release manifest.