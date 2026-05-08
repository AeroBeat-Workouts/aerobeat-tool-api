# AeroBeat Tool - AeroBeat Identity, Access, and Entitlements API

This repo is the official **AeroBeat-facing online service layer** for game clients and related product surfaces.

It should be treated as the reusable Tool that exposes AeroBeat-shaped capabilities for:

- athlete session and account state
- linked-account status
- free vs premium workout access
- trusted discovery and library sync
- install/download policy for approved content
- future-safe seams for creator/review integrations without making them the current v1 source of truth

A **Tool** is a reusable service or singleton manager (for example an API client, analytics manager, or integration layer) designed to be modular and plugged into an **Assembly**.

## What this repo is for

`aerobeat-tool-api` is **not** meant to be a generic REST wrapper or a thin mod.io SDK clone.

Its job is to provide the **AeroBeat-owned client contract** that product repos consume while provider-specific mechanics stay behind adapter seams.

That means:

- product repos should depend on `aerobeat-tool-api`
- `aerobeat-tool-api` should speak in **AeroBeat terms**
- provider DTOs, transport quirks, and account-linking details should stay in vendor repos such as `aerobeat-vendor-modio`

## Current strategic framing

The current docs/architecture direction is:

- **AeroBeat is free-to-play**
- the product supports **free workouts** and **premium workouts**
- workout packages are currently governed as **one difficulty per package**
- coaching is **optional**, but when present it is a package-level feature rather than a partial/inconsistent add-on
- **all public UGC, free and premium, must pass review before release**
- **mod.io Full Curation is the current v1 public review/distribution gate**
- premium purchases must flow through **official platform/store paths**
- provider-side ownership sync should rely only on **official, non-deprecated surfaces** we can legitimately support
- AeroBeat still needs an **AeroBeat-owned account architecture** as a first-class concern for progression, retention, and long-term portability

This repo should therefore become the Godot-imported manager for **identity, access, entitlements, discovery, library sync, and downloads for approved/public content**, while leaving room for future creator/review integration seams if later product phases actually need them.

For v1 specifically, this repo should **not** imply that AeroBeat already owns the authoritative submission/review/status workflow. The locked policy says the public gate lives in **mod.io Full Curation** right now. If this package later exposes creator or reviewer helpers, those should be framed as adapters or future-facing seams layered around the current gate rather than a second competing product truth.

## Repository details

- **Type:** Tool (service/module)
- **License:** **MPL 2.0** (weak copyleft / library)
- **Dependencies:**
  - `aerobeat-tool-core` (canonical shared tool/workflow contract)
  - `aerobeat-vendor-*` (allowed provider seams)

## Recommended boundary

### Own here

- `AeroToolManager` singleton/autoload entrypoint
- AeroBeat session/bootstrap helpers
- account/access/entitlement service interfaces
- discovery/library/download orchestration for approved/public content
- AeroBeat-shaped DTOs or resource models
- provider composition and selection behind internal interfaces
- resilience behavior such as retry/backoff and rate-limit handling
- carefully scoped seams for future creator/review workflows, without treating them as the current v1 approval authority

### Do not own here

- raw mod.io DTOs as public contract
- direct product-repo mod.io integration
- a separate AeroBeat-owned review/status workflow presented as the v1 release authority
- provider wallet/purchase semantics as the long-term public vocabulary
- gameplay logic or feature-specific UI flows
- vendor-specific account-link transport as the public API shape

## GodotEnv development flow

This repo uses the AeroBeat GodotEnv package convention.

- Canonical dev/test manifest: `.testbed/addons.jsonc`
- Installed dev/test addons: `.testbed/addons/`
- GodotEnv cache: `.testbed/.addons/`
- Hidden workbench project: `.testbed/project.godot`
- Repo-local unit tests: `.testbed/tests/`

The repo root remains the package/published boundary for downstream consumers. Day-to-day development, debugging, and validation happen from the hidden `.testbed/` workbench using the pinned OpenClaw toolchain: Godot `4.6.2 stable standard`.

### Restore dev/test dependencies

From the repo root:

```bash
cd .testbed
godotenv addons install
```

That restores this repo's current dev/test manifest into `.testbed/addons/`.

### Open the workbench

From the repo root:

```bash
godot --editor --path .testbed
```

### Import smoke check

From the repo root:

```bash
godot --headless --path .testbed --import
```

### Run unit tests

From the repo root:

```bash
godot --headless --path .testbed --script addons/gut/gut_cmdln.gd \
  -gdir=res://tests \
  -ginclude_subdirs \
  -gexit
```

## Validation notes

- `.testbed/addons.jsonc` is the committed dev/test dependency contract.
- The current package shape is consumed from the repo root (`subfolder: "/"`) for downstream installs.
- Until the service surface is implemented, this repo remains mostly skeleton/package scaffolding; the important point is that the public framing should already reflect the intended AeroBeat-owned identity/access/entitlement role plus approved-content access scope, without overstating v1 creator/review ownership.
