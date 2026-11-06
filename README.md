# Interval Workout Composer

Compose named timed intervals and run them in a local desktop sequence timer.

[![Build and verify](https://github.com/netcodermike/interval-workout-composer/actions/workflows/verify.yml/badge.svg)](https://github.com/netcodermike/interval-workout-composer/actions/workflows/verify.yml)

**Language:** Kotlin · **Platform:** Windows, macOS, Linux desktop · **App type:** Desktop interval sequence editor and timer

First-release learning implementation, with explicit scope below. This is one independently runnable app, not a placeholder in a combined repository.

## Features

- 1–100 named steps
- 1–3600 seconds each
- Monotonic elapsed-time playback
- Save/open interval compositions

## Requirements

JDK 17 and Gradle 8.9; first build downloads Kotlin 2.0.21 from Gradle/Maven. No binary wrapper is included.

## Quick start

```sh
git clone https://github.com/netcodermike/interval-workout-composer.git
cd interval-workout-composer
gradle run
```

Commands run from the repository root. Lines marked for a particular operating system apply only there. Language tools are prerequisites, not installed by the app. Close desktop windows normally; terminal/server apps stop with Ctrl+C unless their usage notes say otherwise.

## Example workflow

Create Work 20s and Rest 10s, save/open, start, observe the phase boundary, stop, and restart. Test a short composition in a development copy.

## Architecture, configuration, and data

Main.kt validates steps, serializes Properties, and maps elapsed monotonic seconds to the active interval and remaining whole seconds. Swing Timer refreshes every 100 ms; Start restarts from the beginning, Stop halts, and completion beeps. Model tests exercise exact interval boundaries, completion, and serialization. No medical recommendations or automatic workout intensity decisions are made.

## Verification

Build with the quick-start command where needed, then run:

```sh
gradle run --args="--self-test" --no-daemon
```

Manual acceptance: Create Work 20s and Rest 10s, save/open, start, observe the phase boundary, stop, and restart. Test a short composition in a development copy. Also test malformed inputs and an unwritable output destination.

See [validation record](docs/VALIDATION.md) for observed checks and their limits. CI results verify only what the workflow runs; they do not establish native GUI correctness or production readiness.

## Limitations and next steps

Timer/composer only, no exercise guidance, calorie estimates, heart-rate input, pause/resume, recurring rounds, notifications, audio prompts, autosave, or background service. Editing/opening is blocked while running. System sleep can advance elapsed monotonic time depending on platform. Closing stops the session.

## Troubleshooting

Use the exact platform/toolchain above. Preserve originals and use synthetic fixtures first. Errors are displayed in the UI or stderr. A headless machine can run the model tests but cannot verify native GUI/audio behavior. Output paths are chosen explicitly; keep backups of important data.

## Source map

- `build.gradle.kts`
- `settings.gradle.kts`
- `src/main/kotlin/Main.kt`

## Development and license

Read [contributing](CONTRIBUTING.md) before changing the app, and [security/privacy](SECURITY.md) before supplying private data. Use synthetic fixtures for tests. No telemetry, paid API key, or account is required by the app itself. Dependencies, when present, are stated in Requirements.

[MIT license](LICENSE), copyright 2026 netcodermike.
