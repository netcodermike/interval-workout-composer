# Validation

Authoring date: November 6, 2026. Host: Windows. Target: Windows, macOS, Linux desktop.

## Local result

Target-platform source CI is recorded after publication. This host has Python, Node.js, and .NET; other native toolchains are verified through CI. No unobserved GUI/device behavior is claimed.

## Reproducible checks

The GitHub Actions workflow builds/runs the following on `ubuntu-latest`:

```sh
gradle build --no-daemon
gradle run --args="--self-test" --no-daemon
```

## Manual acceptance

Create Work 20s and Rest 10s, save/open, start, observe the phase boundary, stop, and restart. Test a short composition in a development copy. Also test malformed inputs and an unwritable output destination.

A workflow file is not evidence of a passing run. Observed CI run links and source commits are recorded after publication. Native GUI, sound, sleep/resume, and platform permissions require direct target-platform acceptance even when model tests pass.
